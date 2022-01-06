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
      <div class="geo">
        {{ weather.name }}, {{ weather.sys.country }}
        <div class="temp">
          {{ Math.round(weather.main.temp) }}
        </div>
      </div>
      <div class="temp"></div>
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
  },
};
</script>


<style>
#app{
  display: flex;
  justify-content: center;
  flex-direction: column;
  font-size: 50px;
}
body{
  background-color: rgb(0, 179, 179);
}
.titre{
  text-align: center;
}
.input{
  border-radius:  10px;
  height: 100%;
}


</style>
