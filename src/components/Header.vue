<template>
<div class="container-fluid">
   <div class="header-container row">
       <div class="logo-container col-6">
            <div class="logo-content">
                <img src="../assets/Netflix-logo.png" alt="logo-Netflix">   
            </div>
              <div class="nav">
                    <ul>
                        <li><a href="#">Home</a></li>
                        <li><a href="#">Serie Tv</a></li>
                        <li><a href="#">Film</a></li>
                        <li><a href="#">Originali</a></li>
                        <li><a href="#">Aggiunti di recente</a></li>
                        <li><a href="#">La mia lista</a></li>
                    </ul>
                </div>
       </div>

       <div class="icon-container col-6">
            <div class="icon-content">
                <input type="text" placeholder="Search" v-model="searchFilm">  <!--trigger evento search-->
               <button @click="$emit('search', searchFilm)">Choose   <i class="fas fa-search"></i></button>
                <li><a href="#">BAMBINI</a></li>
                <li><i class="fas fa-bell"></i></li>
            </div>
       </div> 
    </div>   
</div>                
</template>

<script>
export default {
    name: 'Header',
    data(){
        return {
            searchFilm: ''
        }
    }
}
</script>


<style lang="scss" scoped>
.header-container {
    
     .logo-container{
         display: flex;
         align-items: center;
         
         .logo-content{
             width: 20%;
             img{
                 width: 100%;
             }
         }   
    }
    .icon-container{
        display: flex;
        align-items: center;
        justify-content: flex-end;
        
    }
     
        
   
}
</style>