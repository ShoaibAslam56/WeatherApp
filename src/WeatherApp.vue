<template>
    <div class="weather-app">
      <div class="input-container">
        <input type="text" v-model="city" placeholder="Enter the city name" class="city-input">
        <button @click="fetchdata" class="search-button">Search</button>
      </div>
      <div v-if="weather" class="weather-details">
        <div>
            <img :src="weatherIcon" width="150px" class="colored-icon" alt="">
            <p>{{ weather.weather[0].description }}</p>
        </div>
        <h2 class="weather-title">Weather in {{ weather.name }}</h2>
        <div class="weather-info">
          <p><i class="fas fa-tint"></i> <strong>Humidity</strong> <br> {{ weather.main.humidity }}%</p>
        <p><i class="fas fa-thermometer-three-quarters"></i> <strong>Temperature</strong> <br> {{ convertTemp(weather.main.temp) }} °C</p>
        <p><i class="fas fa-wind"></i> <strong>Windspeed</strong> <br> {{ convertWindSpeed(weather.wind.speed) }} km/h</p>
        </div>
      </div>
      <div v-else class="placeholder">
        <h1>Enter city name to get weather details</h1>
      </div>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    name: "WeatherApp",
    data() {
      return {
        city: '',
        weather: null,
      };
    },
    computed:{
        weatherIcon(){
            return this.weather ? `https://openweathermap.org/img/wn/${this.weather.weather[0].icon}@2x.png` : ""
        }
    },
    methods: {
      async fetchdata() {
        let api_key = "857587bb2fb29bf20b2b529fe40617ee";
        try {
          const response = await axios.get(`https://api.openweathermap.org/data/2.5/weather?q=${this.city}&appid=${api_key}`);
          this.weather = response.data;
        } catch (error) {
          console.warn("Error occurred in your app", error);
        }
      },
      convertTemp(tempK) {
      return (tempK - 273.15).toFixed(2);
    },
    convertWindSpeed(speedMps) {
      return (speedMps * 3.6).toFixed(2);
    }
    },
  };
  </script>
  
  <style scoped>
  .weather-app {
    font-family: 'Arial', sans-serif;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100vh;
    background: linear-gradient(to right, #1cb5d4, #17c5e4);
    color: #fff;
  }

  .input-container {
    display: flex;
    align-items: center;
    margin-bottom: 20px;
  }
  
  .city-input {
    padding: 10px;
    font-size: 16px;
    border: none;
    border-radius: 50px;
    margin-right: 10px;
    width: 250px;
  }
  
  .search-button {
    padding: 10px 20px;
    background-color: #fff;
    color: #0099FF;
    border: none;
    border-radius: 50px;
    cursor: pointer;
    font-size: 16px;
  }
  
  .search-button:hover {
    background-color: #66CCFF;
    color: white;
  }
  
  .weather-details {
    text-align: center;
  }
  
  .weather-title {
    font-size: 24px;
    margin-bottom: 15px;
  }
  
  .weather-info {
    font-size: 18px;
    display: flex;
    justify-content: space-between;
    width: 400px;
    /* border: 2px solid black; */
  }

  .placeholder h1 {
    font-size: 20px;
    color: #ddd;
  }
  
  @media (max-width: 600px) {
    .city-input {
      width: 200px;
    }
  
    .search-button {
      padding: 8px 16px;
    }
  
    .weather-title {
      font-size: 20px;
    }
  
    .weather-info {
      font-size: 16px;
    }
  }
  .weather-info {
  font-size: 18px;
}

.weather-info i {
  margin-right: 10px; 
  color: #ffcc00; 
  font-size: 24px; 
}


.weather-info .fa-tint {
  color: #4db8ff; 
  font-size: 50px; 
}

.weather-info .fa-thermometer-three-quarters {
  color: #ff5733; 
  font-size: 50px; 
}

.weather-info .fa-wind {
  color: #00b894; 
  font-size: 50px; 
}
.colored-icon {
  fill: red; /* Changes the color of the SVG */
  width: 150px; /* Adjust the size */
}
  </style>
  