<template>
  <div class="container" id="country">
    <h2>Country Name - {{ $route.params.name }}</h2>

    <p>{{country}}</p>
  </div>
</template>

<script>
const axios = require('axios');
export default {
  data(){
    return {
      country: null
    }
  },
  mounted(){
    let name = this.$route.params.name
    axios.get('https://restcountries.com/v3.1/name/'+name)
        .then(response => {
          this.country = response.data
        })
  }
}
</script>

<style scoped>

</style>