<template>
    <div class="movies-container ">
        <div class="inner-movies">
            <span @mouseover="hover=true" @mouseleave="hover=false">
                    <img :src="newImg" alt="img film"/>
            </span>
                <span v-if="hover">
                    <div class="text">
                         <div class="title">{{title}}</div>
                        <div class="original_title">{{original_title}}</div>  
                        <div class="original_language">{{original_language}}</div>
                        <div class="vote_average">{{vote_average}}</div>
                    </div> 
                </span>
        </div>
    </div>
    
</template>



<script>
export default {
    name: 'Movies',
    data(){
        return{
           hover: false, 
        };
    },
    props:{
        poster_path: String,
        title: String,
        original_title: String,
        original_language: String,
        vote_average: Number,
    },
    computed: {
        newImg(){
            return 'https://image.tmdb.org/t/p/w342/' + this.poster_path    
        }
    }
}
</script>



<style lang="scss" scoped>
    .movies-container{
        text-align: center;
        margin-top: 5px;
     
       .inner-movies{
           color: #fff;
           position: relative;
           line-height: 20px;
           
           img{
               width: 70%;
               &:hover{
                      box-shadow: 1px 1px 1px 1px  #fff;
                      opacity: 0.4;
                      cursor: pointer;
               }
            
           }
       
        .text{
            position: absolute;
            transform: translate(-20%, -50%);
            left: 30%;
            top: 60%;
            font-size: 28px;
            font-weight: 600;
            font-style: oblique;
            margin: 5px;
            padding: 5px;
            line-height: 30px;
        }   
       }
    }
</style>