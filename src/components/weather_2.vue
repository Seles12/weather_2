<template>
  <div class="header">
    <div class="form">
      <h2 class="cab_2">Weather City Information</h2>

      <!-- NAV BAR -->
      <div class="nav">
        <b-navbar type="" variant="">
          <b-nav-form>
            <b-form-input
              class="mr-sm-2"
              v-model="city"
              placeholder="Type City"
            />
            <b-button
              v-b-modal.modal-1
              variant="outline-success"
              class="my-2 my-sm-0"
              @click="setCity"
              >Search</b-button
            >
          </b-nav-form>
        </b-navbar>
        <!--modal -->
        <div>
          <b-modal id="modal-1" title="Weather City Information">
            <p class="my-4"><p><strong>City:</strong> {{ weatherData.name }}</p>
        <p><strong>Temperature:</strong> {{ weatherData.main.temp }}°C</p>
        <p>
          <strong>Description:</strong> {{ weatherData.weather[0].description }}
        </p></p>
          </b-modal>
        </div>
      </div>
      <div class="let-1" v-if="weatherData">
        
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
      city: "LONDON", // You can change the city
    };
  },
  methods: {
    async setCity() {
      // this.weatherData.name = "london";

      // Add Validation here:
      // IF city is empty, return an error
      // Else, call getWeatherData()

      await this.getWeatherData();
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
  async mounted() {
    await this.getWeatherData();
  },
};
</script>

<style>
.header {
  display: flex;
  justify-content: center;
  /* margin-top: 90px; */
}
.form {
  display: flex;
  flex-direction: column;
  width: 670px;
  height: 200px;
  gap: 10px;
  padding-bottom: 0.4em;
  background-color: #d9f8cb;
  border-radius: 25px;
}

/* .form:hover {
  transform: scale(1.05);
  border: 1px solid rgb(215, 228, 227) s;
} */
.cab_2 {
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
