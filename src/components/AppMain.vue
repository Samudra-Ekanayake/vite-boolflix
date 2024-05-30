<script>


import axios from 'axios'


export default {

    name: 'AppMain',


    data() {
        return {

            movies: [],
            flagLanguage: {
                "en" : require("../assets/Flag_of_the_United_Kingdom_(1-2).svg.png"),
                "it" : require("../assets/Flag_of_Italy.svg.png")         
            }


        }

    },
    methods: {

        getMovies() {
            const options = {
                method: 'GET',
                url: 'https://api.themoviedb.org/3/movie/popular',
                params: { language: 'en-US', page: '1' },
                headers: { accept: 'application/json', Authorization: 'Bearer eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiIxMDk1MjJhMWVjZDljMWIyNmNjZDBjMzEyOWU2YTM0ZCIsInN1YiI6IjY2NTczMzg1ZWYwNWQ5MDUwNTU5OTc5YiIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.5Ms9JOIUtSXGUmtaxu-i83znnXnCT6ekKKp90y5qWeM' }
            };

            axios
                .request(options)
                .then(response => {
                    console.log(response.data.results);
                    this.movies = response.data.results;
                })
                .catch(error => {
                    console.error(error);
                });
        }


    },

    mounted() {

        this.getMovies()

    },

}

</script>

<template>

    <div class="container-fluid st_container bg-black d-flex align-items-center">
        <div class="row d-flex justify-content-between col-12 m-0">
            <div class="col-2 st_boolflix">
                BOOLFLIX
            </div>
            <div class="col-2">
                <input type="text">
            </div>
        </div>

    </div>

    <div class="container-fluid">
        <div class="row">

            <div class="offset-1 col-10 bg-info p-0 d-flex
            ">
                <ul class="d-flex flex-wrap">
                    <li class="m-2" v-for="element in movies">
                        <div>{{ element.title }}</div>
                        <div>{{ element.original_title }}</div>
                        <div>
                            <img :src="flagLanguage[element.original_language]" alt=""
                            v-if="flagLanguage[element.original_language]">
                            <span v-else>{{ element.original_language }}</span>  
                        </div>
                        <div>{{ element.vote_average }}</div>
                    </li>
                </ul>
            </div>
        </div>
    </div>


</template>

<style scoped>
.st_boolflix {
    color: red;
}

.st_container {

    height: 5rem;

}

.st_container2 {
    margin-left: 20rem;
    margin-right: 20rem
}
</style>
