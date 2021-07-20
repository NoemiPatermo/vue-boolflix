<template>
  <div id="app">
    <Header @search="searchMovie"/>  <!--si è messo in ascolto (listener)-->
    <Main    :popularSeries="filteredArraySeries"  :populars="filteredArray" /> <!--inviamo i dati al main (filtrati)-->
  </div>
</template>

<script>
import axios from 'axios';
import Header from './components/Header.vue';
import Main from './components/Main.vue';

export default {
  name: 'App',
  components: {
    Header,
    Main
  },
  data(){
       
    return {
      populars: [],
      popularSeries:[],
      filteredArray: [],
      filteredArraySeries:[]

   }
   
  }, 
    created() {  //parte la chiamata api (movie popular [like hompege] )
        axios.get('https://api.themoviedb.org/3/movie/popular?api_key=c2bd2f899fd21dab83976c0c8ef6993a').then((results) =>{
            this.populars = results.data.results;
            this.filteredArray = results.data.results;
        });
        axios.get('https://api.themoviedb.org/3/tv/popular?api_key=c2bd2f899fd21dab83976c0c8ef6993a').then((results) =>{
            this.popularSeries = results.data.results;
            this.filteredArraySeries = results.data.results;
        });
    },
    
   methods:{ 
       searchMovie(searchFilm){ 
           if (searchFilm.length == 0) { //check se la stringa è vuota la chiamata non deve partire -> la blocchi col return
               this.filteredArray = this.populars;
               return;
            }                           // con questa chiamata tu ricerchi e colleghi cosa ha digitato il tuo utente
           axios.get(`https://api.themoviedb.org/3/search/movie?api_key=c2bd2f899fd21dab83976c0c8ef6993a&query=${searchFilm}`).then((results) =>{
               this.filteredArray = results.data.results;   
           });
           axios.get(`https://api.themoviedb.org/3/search/tv?api_key=c2bd2f899fd21dab83976c0c8ef6993a&query=${searchFilm}`).then((results) =>{
             this.filteredArraySeries = results.data.results; 
           })
       
   }
    
 }
   
    
}
</script>

<style lang="scss">
@import "./style/app.scss"
</style>