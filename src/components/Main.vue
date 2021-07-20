<template>
    <div class="main-container">
        <h1>ORIGINALI NETFLIX</h1>
        <div class="row">
                <Card class="card-section" v-for="populars in populars" :key= 'populars.id'
                :poster_path="populars.poster_path"
                :title="populars.title"
                :original_title="populars.original_title"
                :original_language="populars.original_language"
                :vote_average="populars.vote_average"/>
        </div>
        <div class="row">
            <h1>Serie Tv</h1>       <!--riuso del componente-->
            <Card class="card-section" v-for="series in popularSeries" :key= 'series.id'
                :poster_path="series.poster_path"
                :name="series.name"
                :original_name="series.original_name"
                :original_language="series.original_language"
                :vote_average="series.vote_average"/>
        </div>

    </div>
    
</template>

<script>
import Card from './Card.vue'; //importo il mio componente Card

export default {
    name: 'Main',

    components: {
        Card,   //qui lo dichiari
    }, 
    props: {
        populars: Array,
        popularSeries: Array
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
          .card-section{
              width: calc(100% / 4);
              padding: 5px;
          }
      }
    }
</style>