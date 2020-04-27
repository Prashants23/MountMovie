<template>
<div class="mainContainer">
  <Header/>
  <div id="app">
    <!-- <p @click="consol">Text</p> -->
  <UpcomingMovies v-bind:UpcomingMovies="UpcomingMoviesArray"/>

  <TopRatedMovies v-bind:TopRated="TopRatedMoviesArray"/>
    </div>

</div>
</template>

<script>
import UpcomingMovies from './components/UpcomingMovies.vue'
import Header from './components/Header.vue'
import TopRatedMovies from './components/topRatedMovies.vue'
import axios from 'axios';

export default {
  name: 'App',
  components: {
    UpcomingMovies,
    TopRatedMovies,
    Header
  },
  data(){
      return {
        UpcomingMoviesarray:[],

        TopRatedMoviesArray:[]
      }},
      async created() {
    try {
      const upcomingMovieRes = await axios.get(`https://api.themoviedb.org/3/movie/upcoming?api_key=3a304b40bd8364f3d94fbafac1e9a63a&language=en-US&page=1`);
      const TopRatedRes = await axios.get(`https://api.themoviedb.org/3/movie/top_rated?api_key=3a304b40bd8364f3d94fbafac1e9a63a&language=en-US&page=1`)
       
      this.UpcomingMoviesArray = upcomingMovieRes.data.results;
      this.TopRatedMoviesArray = TopRatedRes.data.results;
       console.log("movies",this.UpcomingMoviesArray);
    } catch(e) {
      console.error(e)
    }

 
  },
  method:{
    consol(){
      console.log("test");
    }
  }
}
</script>

<style scoped>
*{
    margin-top:0;
    margin-left: 0;
    margin-right: 0;
    padding-left: 0;
    padding-right: 0;
    padding-top: 0;
    /* padding:0; */
    box-sizing: border-box
};
body{
  background: rgb(53, 52, 52);
}
</style>>

