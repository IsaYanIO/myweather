<template>
  <h1>Сайт с погодой</h1>
  <h3>Выберите город</h3>
  <h2 v-if="!weather">Загрузка...</h2>
  <div v-else>
    <p>Температура {{ weather.main.temp }}</p>
    <p>{{ weather.weather[0].description}}</p> 
    <img :src="`https://openweathermap.org/img/wn/${weather.weather[0].icon}.png`" alt=""> 
    <p>Влажность воздуха</p>
    <p>{{ weather.main.humidity}}</p>    
    <p>{{ weather.main.pressure}}</p>    
    <p>{{ weather.wind.speed}}</p>    
    <p>{{ weather.wind.deg}}</p>   
  </div>
</template>

<script>

export default {
  name: 'App',
  data(){
    return{
      weather:null
    }
  },
  mounted(){
    fetch('https://api.openweathermap.org/data/2.5/weather?lat=59.231&lon=57.123&appid=0b48dc9464e4dd154dc21fd44f9f39b1&units=metric&lang=ru')
      .then(resp => resp.json())
      .then(json => {
        this.weather = json
    });
  },
  components: {
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
