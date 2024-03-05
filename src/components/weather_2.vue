<template>
  <div class="header">
    <div class="form">
      <h2 class="we-1">Weather City Information</h2>

      <!-- NAV BAR -->
      <div class="nav">
        <b-navbar type="" variant="">
          <b-nav-form>
            <b-form-input
              class="mr-sm-2"
              placeholder="Type City"
            ></b-form-input>
            <b-button
              variant="outline-success"
              class="my-2 my-sm-0"
              type="submit"
              @click="alterarcity"
            >
              >Search</b-button
            >
          </b-nav-form>
        </b-navbar>
      </div>
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

export default {
  data() {
    return {
      weatherData: null,
      apiKey: "06dc7c3527952552932328eb2812350d",
      v: " CAMPINAS", // You can change the city
    };
  },

  methods: {
    alterarcity() {
      this.weatherData.name = "london";
    },
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
  mounted() {
    this.getWeatherData();
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
.nav {
  display: flex;
  margin-left: 100px;
  margin-top: 100px;
}

/* Add your styles here */
</style>
