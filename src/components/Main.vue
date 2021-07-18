<template>
    <div class="main-container">
        <h1>ORIGINALI NETFLIX</h1>
        <div class="row">
                <Movies class="movies-section" v-for="results in results" :key= 'results.id'
                :poster_path="results.poster_path"
                :title="results.title"
                :original_title="results.original_title"
                :original_language="results.original_language"
                :vote_average="results.vote_average"
                :inputSearch="inputSearch"/>
        </div>
    </div>
    
</template>

<script>
import Movies from './Movies.vue'; //importo il mio componente 

export default {
    name: 'Main',

    components: {
        Movies   //qui lo dichiari
    }, 
    props: {
        results: Array,
        inputSearch: String
    } 
}
</script>

<style lang="scss" scoped>
    .main-container{
        padding: 30px ;
        h1{
            font-weight:500;
            font-size: 30px;
        }
      .row{
          .movies-section{
              width: calc(100% / 6);
              padding: 10px;
          }
      }
    }
</style>