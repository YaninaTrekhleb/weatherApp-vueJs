<template>
  <div id="app">
    <main>
      <div class="search-box">
        <input type="text" class="search-bar" placeholder="Search..."/>
      </div>
      <div class="weather-wrap">
        <div class="location-box">
          <div class="location">Northhampton, UK</div>
          <div class="date">Monday 10 August 2020</div>
        </div>
        <div class="weather-box">
          <div class="temperature">30°</div>
          <div class="weather">Sun</div>
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
      api_key: '666286886c5d52f0bb028c1a10401486'
    }
  }
}

</script>

<style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  body {
    font-family: 'montserrat', sans-serif;
  }

  #app {
    /* display: flex;
    justify-content: center;
    align-items: center; */
    background-image: url('./assets/cold-bg.jpeg');
    background-position: center;
    background-size: cover;
    background-repeat: no-repeat;
    transition: 0.4s;
  }

  main {
    min-height: 100vh;
    padding: 25px;
    background-image: linear-gradient(to bottom, rgba(0, 0, 0, 0.25), rgba(0, 0, 0, 0.4));
  }

  .search-box {
    width: 100%;
    margin-bottom: 30px;
  }

  .search-box .search-bar {
    display: block;
    width: 100%;
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
