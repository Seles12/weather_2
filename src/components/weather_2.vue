<template>
  <div class="header">
    <div class="form">
      <h2 class="we-1">Weather City Information</h2>
      <nav_form></nav_form>
      <div class="let-1" v-if="weatherData">
        <p><strong>City:</strong> {{ weatherData.name }}</p>
        <p><strong>Temperature:</strong> {{ weatherData.main.temp }}°C</p>
        <p>
          <strong>Description:</strong> {{ weatherData.weather[0].description }}
        </p>
      </div>
      <div v-else>
        <p>Loading...</p>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

import nav_form from "./nav-form.vue";

export default {
  components: {
    nav_form,
  },
  data() {
    return {
      weatherData: null,
      apiKey: "06dc7c3527952552932328eb2812350d",
      city: "bicester", // You can change the city
    };
  },
  mounted() {
    this.getWeatherData();
  },
  methods: {
    async getWeatherData() {
      try {
        const response = await axios.get(
          `https://api.openweathermap.org/data/2.5/weather?q=${this.city}&appid=${this.apiKey}&units=metric`
        );
        this.weatherData = response.data;
      } catch (error) {
        console.error("Error fetching weather data:", error);
      }
    },
  },
};
</script>

<style scoped>
.header {
  display: flex;
  justify-content: center;
  margin-top: 90px;
}
.form {
  display: flex;
  flex-direction: column;
  width: 670px;
  height: 700px;
  gap: 10px;
  padding-bottom: 0.4em;
  background-color: #cccccc;
  border-radius: 25px;
  transition: 0.4s ease-in-out;
}

.form:hover {
  transform: scale(1.05);
  border: 1px solid rgb(215, 228, 227) s;
}
.we-1 {
  display: flex;
  justify-content: center;
  font-size: 3.2em;
  border: 700px;
  margin-top: 40px;
}
.let-1 {
  display: flex;
  flex-direction: column;
  gap: 50px;
  font-size: 2.2em;
  margin-top: 120px;
  margin-left: 10px;
}
.nav_form {
  margin-bottom: 10px;
}

/* Add your styles here */
</style>
