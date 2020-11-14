<template>
    <div class="card" v-if="info">
    <h1>{{ info.name }}, {{ info.sys.country }}</h1>
        <div class="row">
            <div class="top">
                <div>
                    <img :src="image">
                    <p id="desc">{{ info.weather[0].main }}</p>
                </div>
                <div>
                    <p>Max Temperature: {{ Math.round(info.main.temp_max - 273.15) }} °C <i class="fas fa-thermometer-half"></i></p>
                    <p>Min Temperature: {{ Math.round(info.main.temp_min - 273.15) }} °C  <i class="fas fa-thermometer-half"></i></p>
                </div>
            </div>
        </div>
        <div class="row bottom">
            <p>Pressure: {{ info.main.pressure }} mbar <i class="fab fa-cloudscale"></i> </p>
            <p>Wind speed: {{ info.wind.speed }} m/s <i class="fas fa-tachometer-alt"></i></p>
            <p>Humidity: {{ info.main.humidity }} <i class="fas fa-percentage"></i></p>
        </div>
        <p id="temp">{{ Math.round(info.main.temp - 273.15) }} °C</p>
  </div>
</template>

<script>
export default {
    props: ['info', 'image']
}
</script>

<style scoped>

.card {
  margin-top: 20px;
  height: 550px;
  width: 40%;
  display: flex;
  flex-direction: column;
  align-items: center;
  border-radius: 10px;
  box-shadow: 1px 0px 31px 0px #000000;
  margin-bottom: 20px;
  color: lightblue;
}

.row {
  width: 90%;
  display: flex;
  justify-content: space-between;
  padding: 10px;
}

.top {
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.top img {
  height: 150px
}

#desc {
  text-align: center;
  margin-top: 0;
}

.bottom {
    text-align: left;
}

p {
  font-size: 20px;
  text-align: left;
}

#temp {
  margin: 30px 0;
  font-size: 75px;
}
</style>