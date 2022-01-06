<template>
  <div id="app">
    <div class="titre"> {{ hello }} dans notre app Méteo</div>
    <main>

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
  <div class="geo">
    {{ weather.name }}, {{ weather.sys.country}}
    <div class="temp">
    {{ Math.round(weather.main.temp)}}
    </div>

   
  </div>
 <div class="temp">
 </div>
</div>

    </main>
    </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      api_key: "d4235acc5a46cf24a94dfe20005090ba",
      base_url: "https://api.openweathermap.org/data/2.5/",
      hello: "Hello World", // ma Data du titre
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
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
#app {
  display: flex;
  flex-direction: column;
  justify-content: center;
  justify-items: center;
}
body {
  background-color: rgb(0, 179, 179);
  font-size: 35px;
}
.titre {
  text-align: center;
}
</style>
