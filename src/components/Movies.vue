<template>
    <div class="movies-container">
        <div class="inner-movies ">
            <img :src="poster_path" alt= />
            <div class="title">{{title}}</div>  
        </div>
    </div>
</template>



<script>
export default {
    name: 'Movies',
    props:{
        poster_path: String,
        title: String,
    
    }
}
</script>



<style lang="scss" scoped>
    .movies-container{
        text-align: center;
        margin-top: 5px;
       .inner-movies{
           position: relative;
           line-height: 20px;
           height: 200px;
           img{
               
               box-shadow: 1px 1px 1px 1px  #fff;
           }
        .title{
            position: absolute;
            left: 60%;
            transform: translate(-60%, -100%);
            font-size: 20px;
            padding: 5px;
        }
           
       }
    }
</style>