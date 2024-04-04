<template>
  <h2>Погода</h2>
  <input v-model="city" type="text" placeholder="Введите название города на английском">
  <button @click="getWeather">Поиск {{ city}}</button>
  <div v-if="weather && weather.count">
    Погода в {{ weather.list[0].name }}, {{ Math.ceil(weather.list[0].main.temp - 273)}} Градусов


  </div>
</template>

<script>
export default {
  data() {
    return {
      city: null,
      weather: null,
    }
  },
  methods: {
    getWeather(){
      let url = 'https://openweathermap.org/data/2.5/find?q='+this.city+'&appid=439d4b804bc8187953eb36d2a8c26a02&units=metric';
      fetch(url)
          .then(response => response.json())
          .then(data => this.weather = data)

    }
  }
}
</script>