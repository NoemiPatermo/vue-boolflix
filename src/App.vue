<template>
  <div id="app">
    <Header @search="searchArrayMovies"/>  <!--si è messo in ascolto (listener)-->
    <Main  :inputSearch="inputSearch"   :results="filterFilms" /> <!--inviamo i dati al main (filtrati)-->
    <Movies />
  </div>
</template>

<script>

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
    
      results: [ 
       {
           "adult": false,
           "backdrop_path": "/3lbTiIN8cVonMUQwaeh5nvn61lr.jpg",
           "genre_ids": [
               12,
               35,
               878,
               10751
           ],
           "id": 105,
           "original_language": "en",
           "original_title": "Back to the Future",
           "overview": "Eighties teenager Marty McFly is accidentally sent back in time to 1955, inadvertently disrupting his parents' first meeting and attracting his mother's romantic interest. Marty must repair the damage to history by rekindling his parents' romance and - with the help of his eccentric inventor friend Doc Brown - return to 1985.",
           "popularity": 38.464,
           "poster_path": "/7lyBcpYB0Qt8gYhXYaEZUNlNQAv.jpg",
           "release_date": "1985-07-03",
           "title": "Back to the Future",
           "video": false,
           "vote_average": 8.3,
           "vote_count": 15222
       },
       {
           "adult": false,
           "backdrop_path": "/a4qvbI9x3nqu3hKQyDRVVBpMklx.jpg",
           "genre_ids": [
               12,
               35,
               10751,
               878
           ],
           "id": 165,
           "original_language": "en",
           "original_title": "Back to the Future Part II",
           "overview": "Marty and Doc are at it again in this wacky sequel to the 1985 blockbuster as the time-traveling duo head to 2015 to nip some McFly family woes in the bud. But things go awry thanks to bully Biff Tannen and a pesky sports almanac. In a last-ditch attempt to set things straight, Marty finds himself bound for 1955 and face to face with his teenage parents -- again.",
           "popularity": 21.527,
           "poster_path":"/hQq8xZe5uLjFzSBt4LanNP7SQjl.jpg" ,
           "release_date": "1989-11-22",
           "title": "Back to the Future Part II",
           "video": false,
           "vote_average": 7.7,
           "vote_count": 9744
       },
       {
           "adult": false,
           "backdrop_path": "/igaRMweCynEGoS6w4Rsim7JPnKu.jpg",
           "genre_ids": [
               12,
               35,
               878
           ],
           "id": 196,
           "original_language": "en",
           "original_title": "Back to the Future Part III",
           "overview": "The final installment of the Back to the Future trilogy finds Marty digging the trusty DeLorean out of a mineshaft and looking for Doc in the Wild West of 1885. But when their time machine breaks down, the travelers are stranded in a land of spurs. More problems arise when Doc falls for pretty schoolteacher Clara Clayton, and Marty tangles with Buford Tannen.",
           "popularity": 17.89,
           "poster_path":"/crzoVQnMzIrRfHtQw0tLBirNfVg.jpg" ,
           "release_date": "1990-05-25",
           "title": "Back to the Future Part III",
           "video": false,
           "vote_average": 7.4,
           "vote_count": 7863
       },
       {
           "adult": false,
           "backdrop_path": "/3lbTiIN8cVonMUQwaeh5nvn61lr.jpg",
           "genre_ids": [
               12,
               35,
               878,
               10751
           ],
           "id": 104,
           "original_language": "en",
           "original_title": "Back to the Future",
           "overview": "Eighties teenager Marty McFly is accidentally sent back in time to 1955, inadvertently disrupting his parents' first meeting and attracting his mother's romantic interest. Marty must repair the damage to history by rekindling his parents' romance and - with the help of his eccentric inventor friend Doc Brown - return to 1985.",
           "popularity": 38.464,
           "poster_path": "/7lyBcpYB0Qt8gYhXYaEZUNlNQAv.jpg",
           "release_date": "1985-07-03",
           "title": "Il Miglio Verde",
           "video": false,
           "vote_average": 4.3,
           "vote_count": 15222
       },
       {
           "adult": false,
           "backdrop_path": "/a4qvbI9x3nqu3hKQyDRVVBpMklx.jpg",
           "genre_ids": [
               12,
               35,
               10751,
               878
           ],
           "id": 163,
           "original_language": "en",
           "original_title": "Back to the Future Part II",
           "overview": "Marty and Doc are at it again in this wacky sequel to the 1985 blockbuster as the time-traveling duo head to 2015 to nip some McFly family woes in the bud. But things go awry thanks to bully Biff Tannen and a pesky sports almanac. In a last-ditch attempt to set things straight, Marty finds himself bound for 1955 and face to face with his teenage parents -- again.",
           "popularity": 21.527,
           "poster_path": "/hQq8xZe5uLjFzSBt4LanNP7SQjl.jpg",
           "release_date": "1989-11-22",
           "title": "The Great Gatsby",
           "video": false,
           "vote_average": 5.7,
           "vote_count": 9744
       },
       {
           "adult": false,
           "backdrop_path": "/igaRMweCynEGoS6w4Rsim7JPnKu.jpg",
           "genre_ids": [
               12,
               35,
               878
           ],
           "id": 197,
           "original_language": "en",
           "original_title": "Back to the Future Part III",
           "overview": "The final installment of the Back to the Future trilogy finds Marty digging the trusty DeLorean out of a mineshaft and looking for Doc in the Wild West of 1885. But when their time machine breaks down, the travelers are stranded in a land of spurs. More problems arise when Doc falls for pretty schoolteacher Clara Clayton, and Marty tangles with Buford Tannen.",
           "popularity": 17.89,
           "poster_path": "/crzoVQnMzIrRfHtQw0tLBirNfVg.jpg",
           "release_date": "1990-05-25",
           "title": "Man in Black",
           "video": false,
           "vote_average": 3.4,
           "vote_count": 7863
       }
    
   ],
   inputSearch: '',//qui metto ciò che l'utente digita
    
   }
   
  }, 
    created() {
        this.searchArrayMovies('')
    },
    computed: { //eseguito e lanciato ogni volta che uno dei dati interni cambia
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
                return this.results
            }
            return this.results.filter((element) => { //array originale filtrato
                return searchIn(this.inputSearch, [element.title])
            })
        }
    },
    methods:{ //questa funzione raccoglie ciò che l'utente digita
        searchArrayMovies(searchFilm){
            this.inputSearch = searchFilm.trim() //hai ciò che l'utente digita e ciò che ti arriva dall'header  
                                                 // no whitespace -> trim
        }
    }
   
    
}
</script>

<style lang="scss">
@import "./style/app.scss"
</style>