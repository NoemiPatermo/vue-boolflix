<template>
    <div class="main-container">
        <h1>ORIGINALI NETFLIX</h1>
        <div class="row">
                <Movies class="movies-section" v-for="populars in populars" :key= 'populars.id'
                :poster_path="populars.poster_path"
                :title="populars.title"
                :original_title="populars.original_title"
                :original_language="populars.original_language"
                :vote_average="populars.vote_average"
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
        populars: Array,
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