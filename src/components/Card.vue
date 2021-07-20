<template>
    <div class="card-container ">
        <div class="inner-card" @mouseover="hover=true" 
            @mouseleave="hover=false">

                <img :src="imgMovie" /> 

                <span v-if="hover">
                    <div class="hover-text">
                            <h5>Name: {{title}}</h5>  
                            <h6>Original title: {{original_title}}</h6>
                            <h6> Language: <img class="flag" :src="littleFlag" :alt="`image of ${{title}}`"></h6>
                             <h6> Vote: {{vote_average}}</h6>
                    </div> 
                </span>
        </div>
    </div>
    
</template>



<script>

export default {
    name: 'Card',
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
        imgMovie(){     //completa la parte mancante della foto, indicando il percorso da seguire,
            if(this.poster_path) {
                return 'https://image.tmdb.org/t/p/w342/' + this.poster_path;
            } else {
                return require('../assets/error.jpg') // nel caso manchi img di un film
            }
        },
        littleFlag(){
            return require ('../assets/' + this.original_language + '.jpg');
        }
  },

  
}
</script>



<style lang="scss" scoped>
    .card-container{
        text-align: center;
        margin-top: 5px;
     
       .inner-card{
           color: #fff;
           position: relative;
           line-height: 20px;
           
           img{
               width: 90%;
            .error{
                img{
                    width: 90%;
                    
                }
            }
               &:hover{
                      box-shadow: 2px 2px 2px 2px  #fff;
                      opacity: 0.2;
                      cursor: pointer;
               }
            
           }
       
        .hover-text{
            position: absolute;
            transform: translate(-20%, -50%);
            left: 30%;
            top: 60%;
            font-size: 28px;
            font-weight: bold;
            font-style: oblique;
            margin: 5px;
            padding: 5px;
            line-height: 30px;
            font-size: 40px;
            font-style: oblique;
        }   
        .flag{
           width: 35px;
           border-radius: 50%;
        }
       }
    }
</style>