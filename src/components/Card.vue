<template>
    <div class="card-container ">
        <div class="inner-card" @mouseover="hover=true" 
            @mouseleave="hover=false">

                <img :src="imgMovie" /> 

                <div v-if="hover">
                    <div class="hover-section">
                            <h4>{{title}}{{name}}</h4>  
                            <div class="line"/>
                            <h6>Original title: {{original_title}}{{original_name}}</h6>
                            <h6> Language: <img class="flag" :src="littleFlag" :alt="`image of ${{title}}`"></h6>
                      <span><i v-for="n in 5" :key="n" class="fa-star" :class="n <= voteRounded ? 'fas' : 'far' "></i></span>       
                    </div> 
                </div>
        </div>
    </div>
</template>



<script>

export default {
    name: 'Card',
    data(){
        return{
           hover: false, 
           voteRounded: Math.round(this.vote_average / 2),
        };
    },
    props:{  // dati che invia il componente padre (main)
        poster_path: String,
        title: String,
        original_title: String,
        original_language: String,
        vote_average: Number,
        original_name: String,
        name: String
        
    },
    computed: {
        imgMovie(){     //completa la parte mancante della foto, indicando il percorso da seguire,
            if(this.poster_path) {
                return 'https://image.tmdb.org/t/p/w500/' + this.poster_path;
            } else {
                return require('../assets/error.jpg') // nel caso manchi img di un film
            } //il require permette di riscrivere la stringa in modo dinamico
        },
        littleFlag(){ //  funzione per le bandierine
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
                      box-shadow: 3px 3px 3px 3px  #fff;
                      opacity: 0.2;
                      cursor: pointer;
               }
            
           }
       
        .hover-section{
            position: absolute;
            transform: translate(-20%, -50%);
            left: 30%;
            top: 80%;   
            font-weight: bold;
            font-style: oblique;
            margin: 5px;
            padding: 5px;
            line-height: 30px;
            font-size: 50px;
            font-style: oblique;
            h6{
                font-size: 15px;
            }
            .line{
            width: 30%;
            height: 4px;
            margin: 15px auto;
            background: #fff
            }
        }  
        span{
            color: yellow;
        } 
        .flag{
           width: 35px;
           border-radius: 50%;
        }
       }
    }
</style>