<template>
<div>
     <div class="header">
            <h1>MountMovies's Top Rated Movies</h1>
        </div>
    <div class="MovieCardsContainer">
         <div v-bind:key="movie.id" v-for="movie in TopRated" class="MovieCard">
           <div class="container">
             <img :src="'https://image.tmdb.org/t/p/w400' + movie.backdrop_path" alt="Avatar" class="image">
               <h3 class="Title">{{movie.original_title}}</h3>
            <div class="overlay">
              <div class="text"> 
                <div class="VotesAverage">{{movie.vote_average}}/10</div>
                <div class="TotalVotes"> Total Votes: {{movie.vote_count}}</div>
                <div class="Title">{{movie.original_title}}</div>
              </div>
          </div>
        </div>
      </div>
  </div>
</div>
</template>

<script>
export default {
    name:'TopRatedMovies',
    props:["TopRated"],
    data(){
        return {hovered:false}
    }
}
</script>

<style scoped>
.container {
 position: relative;
 width: 450px;
}

.image {
  display: block;
  width: 100%;
  border: 5px solid rgb(227, 233, 227);
  /* height: auto; */
}
.overlay {
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  height: 100%;
  width: 100%;
  opacity: 0;
  transition: .5s ease;
  background-color: transparent;
  /* opacity: 0.1; */
}

.container:hover .overlay {
  opacity: 1;
}

.text {
  color: white;
  font-size: 20px;
  position: absolute;
  /* background: red; */
  top: 50%;
  left: 46%;

  -webkit-transform: translate(-50%, -50%);
  -ms-transform: translate(-50%, -50%);
  transform: translate(-50%, -50%);
  text-align: center;
}
.Title{
    color:white;
    font-weight: bold;
    margin-top: 50;
}

.VotesAverage{
    /* padding-left: 50;
    padding-right: 50; */margin-bottom: 20;
    text-align: center;
    font-size: 40;
    font-weight: 700;
      color: rgb(211, 255, 213);
  
}
.TotalVotes{
    margin-bottom: 20px;
    text-align: center;
    font-size: 20px;
    font-weight: 700;
    color: rgb(211, 255, 213);
  
}


.header{
    color: azure;
    text-align: center;

} 
  @media screen and (min-width: 500px) {
.MovieCardsContainer{
   display: grid;
    grid: 1fr 1fr/ 1fr 1fr 1fr;
   grid-gap: 5px;
  padding: 10px;
   
}}
</style>