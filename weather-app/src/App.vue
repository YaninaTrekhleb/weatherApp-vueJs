<template>
  <div id="app" :class="typeof weather.main != 'undefined' && weather.main.temp > 16 ? 'warm' : ''">
    <main>
      <div class="search-box">
        <input 
          type="text" 
          class="search-bar" 
          placeholder="Search..."
          v-model="query"
          @keypress="fetchWeather"
        />
      </div>
      <div class="weather-wrap" v-if="typeof weather.main != 'undefined'">
        <div class="location-box">
          <div class="location">{{ weather.name }}, {{ weather.sys.country }}</div>
          <div class="date">{{ dateBuilder() }}</div>
        </div>
        <div class="weather-box">
          <div class="temperature">{{ Math.round(weather.main.temp)}}°c</div>
          <div class="weather">{{ weather.weather[0].main }}</div>
        </div>
      </div>
    </main>
  </div>
</template>

<script>

export default {
  name: 'app',
  data () {
    return {
      api_key: '666286886c5d52f0bb028c1a10401486',
      url_base: 'https://api.openweathermap.org/data/2.5/',
      query: '',
      weather: {}
    }
  },
  methods: {
    fetchWeather (e) {
      if (e.key == "Enter") {
        fetch(`${this.url_base}weather?q=${this.query}&units=metric&APPID=${this.api_key}`)
          .then(res => {
            return res.json();
          }).then(this.setResults);
      }
    },
    setResults (results) {
      this.weather = results;
    },
    dateBuilder () {
      let d = new Date();
      let months = ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"];
      let days = ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"];

      let day = days[d.getDay()];
      let date = d.getDate();
      let month = months[d.getMonth()];
      let year = d.getFullYear();
      return `${day} ${date} ${month} ${year}`;
    }
  }
}

</script>

<style>
  * {
    margin: 0 auto;
    padding: 0;
  }

  body {
    font-family: 'montserrat', sans-serif;
  }

  #app {
    background-image: url('./assets/cold-bg.jpeg');
    background-position: center;
    background-size: cover;
    background-repeat: no-repeat;
    transition: 0.4s;
  }

  #app.warm {
    background-image: url('./assets/warm-bg.jpeg');
  }

  main {
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    min-height: 100vh;
    padding: 25px;
    background-image: linear-gradient(to bottom, rgba(0, 0, 0, 0.25), rgba(0, 0, 0, 0.4));
  }

  .search-box {
    width: 100%;
    margin-bottom: 30px;
  }

  .search-box .search-bar {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 50%;
    padding: 15px;

    color: #313131;
    font-size: 20px;

    appearance: none;
    border: none;
    outline: none;
    background: none;

    background-color: rgba(255, 255, 255, 0.7);
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.25);
    border-radius: 10px;
    transition: 0.4s;
  }

  .search-box .search-bar:focus {
    box-shadow: 0 0 12px rgba(0, 0, 0, 0.25);
    background-color: rgba(255, 255, 255, 0.9);
    transition: 0.4s;
  }

  .location-box .location {
    color: white;
    font-size: 35px;
    font-weight: 500;
    text-align: center;
    text-shadow: 1px 3px rgba(0, 0, 0, 0.25);
  }

  .location-box .date {
    color: white;
    font-size: 20px;
    font-weight: 300;
    text-align: center;
    font-style: italic;
    margin-top: 10px;
  }

  .weather-box {
    text-align: center;
  }

  .weather-box .temperature {
    display: inline-block;
    padding: 10px 25px;
    color: white;
    font-size: 100px;
    font-weight: 900;

    text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
    background-color: rgba(255, 255, 255, 0.25);
    border-radius: 16px;
    margin: 30px 0;

    box-shadow: 3px 6px rgba(0, 0, 0, 0.25);
  }

  .weather-box .weather {
    color: white;
    font-size: 45px;
    font-weight: 700;
    font-style: italic;
    text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
  }
</style>
