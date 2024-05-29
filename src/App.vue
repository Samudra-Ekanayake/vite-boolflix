<script>

import AppHeader from "./components/AppHeader.vue";
import AppMain from "./components/AppMain.vue";
import axios from 'axios'



export default {

  components: {
    AppHeader, AppMain,
  },

  data() {
    return {

      movies: [],

    }
  },

  methods: {

    getMovies() {
      const options = {
        method: 'GET',
        url: 'https://api.themoviedb.org/3/movie/popular',
        params: { language: 'en-US', page: '1' },
        headers: { accept: 'application/json', Authorization: 'Bearer 109522a1ecd9c1b26ccd0c3129e6a34d' }
      };

      axios
        .request(options)
        .then(response => {
          console.log(response.data);
          this.movies=response.data.results;
        })
        .catch(error => {
          console.error(error);
        });
    }

  },

  mounted() {

  },

}

</script>

<template>

  <AppHeader />
  <AppMain :movies="movies" />

</template>

<style></style>
