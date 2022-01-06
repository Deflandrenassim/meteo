<template>
 <div> 
   <div class="titre">
  {{ hello }} dans notre app Méteo 
   </div>

   <div class="input-search">

   <input type="search" name="search" id="search" placeholder="Recherche..">
   </div>



 </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data (){
    return{
      hello: 'Hello World',
      api_key: 'd4235acc5a46cf24a94dfe20005090ba'
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
