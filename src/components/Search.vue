<template>
  <div class="search">
    <div class="top">
      <h1>Welcome.</h1>
      <p>Search for a city</p>
      <div class="input">
        <input type="text" v-model="title" @keypress.enter="search"> 
        <button v-on:click="search">Search</button>
      </div>
    </div>
  </div>
  <app-card :info="info" :image="image"></app-card>
</template>

<script>
import appCard from './Card.vue'
export default {
  data() {
    return {
      title: '',
      info: null,
      image: null
    }
  },
  components: {
    appCard
  },
  methods: {
    search() {
      fetch(`https://api.openweathermap.org/data/2.5/weather?q=${this.title}&appid=4a093959bdf30b3fd316c0c1900b94f5`)
    .then(response => response.json())
    .then(data => {
       this.info = data
       this.image =` http://openweathermap.org/img/wn/${data.weather[0].icon}@2x.png`
    })
    .catch(() => {
      alert('Not a valid city!')
    })
    }
  }
}
</script>


<style scoped>

.search  {
  display: flex;
  justify-content: center;
  width: 64.7%;
  height: 285px;
  background: url('https://www.metoffice.gov.uk/binaries/content/gallery/metofficegovuk/hero-images/science/weather-forecast-background.jpg');
  background-position-y: 80%;
  ;
  padding-top: 60px;

  
}

.top {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  width: 90%;
  height: 100%;
  font-size: 25px;
}

.top p {
  margin-bottom: 0
}

h1 {
  margin-top: 0;
}

.input {
  height: 40px;
  width: 100%;
  margin-top: 20px;
  display: flex;
  justify-self: flex-end;
  align-items: center;
  
}

input {
  width: 70%;
  height: 40px;
  border: none;
  border-radius: 20px;
  outline: none;
  display: inline;
  padding-left: 15px;
  font-size: 20px;
}
button{
  height: 42px;
  width: 100px;
  position: absolute;
  justify-self: flex-end;
  right: 36%;
  z-index: 1;
  cursor: pointer;
  border-radius: 20px;
  outline: none;
  border: none;
  color: white;
  font-size: 20px;
  transition: all 0.2s ease;
  background: #1488CC;  /* fallback for old browsers */
  background: -webkit-linear-gradient(to right, #2B32B2, #1488CC);  /* Chrome 10-25, Safari 5.1-6 */
  background: linear-gradient(to right, #2B32B2, #1488CC); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */


}
</style>
