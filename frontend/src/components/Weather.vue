<template>
  <h1>London is {{ londonTemp }}°C</h1>    
</template>

<script>
import axios from 'axios';
import cityTemps from '../data/climate.json';

export default {
  name: 'Weather',
  data () {
    return {
      londonTemp: null
    }
  },
  mounted () {
    this.getLondonTemp();
    console.log(cityTemps);
  },
  methods: {
    getLondonTemp() {
      axios
      .get('http://api.weatherstack.com/current?access_key=0f01a0c3824f82eeb73640ed6734f813&query=London')
      .then(response => (this.londonTemp = response.data.current.temperature))
    }
  }
}
</script>