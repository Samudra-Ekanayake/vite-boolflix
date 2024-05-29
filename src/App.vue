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

    }
  },

  methods: {
    getMovies() {

      axios.get('url_dell_api')
        .then(response => {

        })
        .catch(error => {

        })
    }

  },

  mounted() {

  },

}

</script>

<template>

  <AppHeader />
  <AppMain />

</template>

<style></style>
