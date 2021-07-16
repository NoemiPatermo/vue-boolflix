<template>
<div class="container-fluid">
   <div class="header-container row">
       <div class="logo-container col-6">
            <div class="logo-content">
                <img src="../assets/Netflix-logo.png" alt="logo-Netflix">   
            </div>
              <div class="finta-nav">
                    <ul>
                        <li>Home</li>
                        <li>Serie Tv</li>
                        <li>Film</li>
                        <li>Originali</li>
                        <li>Aggiunti di recente</li>
                        <li>La mia lista</li>
                    </ul>
                </div>
       </div>

       <div class="icon-container col-6">
            <div class="icon-content">
               <li><i class="fas fa-search"></i></li>
                <li>BAMBINI</li>
                <li><i class="fas fa-bell"></i></li>
            </div>
       </div> 
    </div>   
</div>                
</template>

<script>
export default {
    name: 'Header',
}
</script>


<style lang="scss" scoped>
.header-container {
    color: #fff;
    background-color: black;
     .logo-container{
         display: flex;
         text-align: center;
         margin-top: 10px;
         .logo-content{
             width: 10%;
             img{
                 width: 100%;
             }
         }
         .finta-nav{
             li{
                 list-style: none;
                 display: inline-block;
                 padding: 10px;
             }
         }
    
    }
    .icon-container{
        display: flex;
        align-items: center;
        justify-content: flex-end;
        .icon-content{
            
            li{
                padding: 15px;
                list-style: none;
                display: inline-block;

            }
        }
    }
     
        
   
}
</style>