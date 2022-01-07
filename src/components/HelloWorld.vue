<template>
  <div id="app">
  
    <div class="titre">{{ hello }} dans notre app Méteo</div>

    <div class="input-search">
      <input
        type="search"
        class="input"
        name="search"
        v-model="recherche"
        placeholder="Recherche.."
        @keypress="fetchWeather"
      />
    </div>

    <div class="container" v-if="typeof weather.main != 'undefined'">

       <div class="date"> 
        {{ dateBuilder() }}
       </div>

      <div class="geo">
        {{ weather.name }}, {{ weather.sys.country }}
        </div>
        
        <div class="temp">
          {{ Math.round(weather.main.temp) }} ° 
        </div>

    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      api_key: "d4235acc5a46cf24a94dfe20005090ba",
      base_url: "https://api.openweathermap.org/data/2.5/",
      hello: "Hello World Welcome ", // ma Data du titre
      recherche: "",
      weather: {},
    };
  },
  methods: {
    fetchWeather(evement) {
      if (evement.key == "Enter") {
        fetch(
          `${this.base_url}weather?q=${this.recherche}&units=metric&APPID=${this.api_key}`
        )
          .then((res) => {
            return res.json();
          })
          .then(this.setResults);
      }
    },
    setResults(results) {
      this.weather = results;
    },
    dateBuilder() {
      let d = new Date();
      let months = ["Janvier", "Février", "Mars", "Avril", "Mai",
      "Juin", "Juillet", "Aout", "Septembre", "Octobre", "Novembre", "Decembre"];
      let days = ["Lundi", "Mardi", "Mercredi", "Jeudi", "Vendredi", "Samedi", "Dimanche"];
       
      let day = days[d.getDay()];
      let date = d.getDate();
      let month = months[d.getMonth()];
      let year = d.getFullYear();

      return `${day} ${date} ${month} ${year}`;
    }
  },
};
</script>


<style>
#app{
  display: flex;
  text-align: center;
  flex-direction: column;
  font-size: 40px;
}
body{
  background-color: rgb(0, 179, 179);
}
.container{
  margin-top: 5rem;
}
.titre{
 display: flex;
 justify-content: center;
}
.input-search{
  margin-top: 3rem;
  display: flex;
  justify-content: center;
}

.input{
  border-radius: 10px;
  height: 50px;
  width: 200px;
  box-shadow: 10px 5px 5px rgb(255, 234, 234);
}
.btn{
  border-radius: 50%;
}
</style>
