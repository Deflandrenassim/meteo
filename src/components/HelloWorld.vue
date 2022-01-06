<template>
 <div> 
   <div class="titre">
  {{ hello }} dans notre app Méteo 
   </div>

   <div class="input-search">
   <input type="search" class="input" name="search" v-model="recherche" placeholder="Recherche..">
   </div>
  <div class="container">
   <div class="date"> {{ recherche }} </div>
   <div class="temperature"> date aujourdhui   </div>
   <div class="temperature"> 20 degré  </div>
   <div>  quel temps </div>

  </div>



 </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data (){
    return{
      hello: 'Hello World',
      api_key: 'd4235acc5a46cf24a94dfe20005090ba',
      recherche: ''
    }
  }
  }

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
body{
  background-color: rgb(0, 179, 179);
  font-size: 35px;
}
.titre{
  text-align: center;
}


</style>
