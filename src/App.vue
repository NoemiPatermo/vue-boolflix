<template>
  <div id="app">
    <Header @search="searchMovie"/>  <!--si è messo in ascolto (listener)-->
    <Main  :inputSearch="inputSearch"   :populars="filteredArray" /> <!--inviamo i dati al main (filtrati)-->
    <Movies />
  </div>
</template>

<script>
import axios from 'axios';
import Header from './components/Header.vue';
import Main from './components/Main.vue';
import Movies from './components/Movies.vue';
export default {
  name: 'App',
  components: {
    Header,
    Main,
    Movies
  },
  data(){
       
    return {
      populars: [],
      filteredArray: [],
      inputSearch: '',//qui metto ciò che l'utente digita
   }
   
  }, // chiude il data
    created() {  //parte la chiamata api (movie popular [like hompege] )
        axios.get('https://api.themoviedb.org/3/movie/popular?api_key=c2bd2f899fd21dab83976c0c8ef6993a').then((results) =>{
            this.populars = results.data.results;
            this.filteredArray = results.data.results;
        })
      this.searchMovie('')
    },
    computed: {      //eseguito e lanciato ogni volta che uno dei dati interni cambia
       filterFilms(){
            function searchIn(search, elements){
                let exists = false;
                elements.forEach((element) => {
                    if(element.toLowerCase().includes(search.toLowerCase())) {
                        exists = true;
                    }
                });
                return exists;
            }
            if(this.inputSearch.length === 0) {
                return this.populars
            }
            return this.populars.filter((element) => { //array originale filtrato
                return searchIn(this.inputSearch, [element.title])
            })
        }
    },
   methods:{ 
       searchMovie(searchFilm){ 
           if (searchFilm.length == 0) {
               this.filteredArray = this.populars;
               return;
            }                           // con quest chiamata tu ricerchi e colleghi cosa ha digitato il tuo utente
           axios.get(`https://api.themoviedb.org/3/search/movie?api_key=c2bd2f899fd21dab83976c0c8ef6993a&query=${searchFilm}`).then((results) =>{
               this.filteredArray = results.data.results;
               this.inputSearch = searchFilm.trim()
           })
       
   }
    
 }
   
    
}
</script>

<style lang="scss">
@import "./style/app.scss"
</style>