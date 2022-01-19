<template>
  <div id="allcountries">
    <H2 class="text-center">All Countries</H2>
    
    <div class="container my-3">
      <div class="row">
        <div class="col-md-3 my-3" v-for="(country,index) in countries" :key="index">
          <div class="card shadow">
            <img :src="country.flags.png" class="card-img-top" alt="...">
            <div class="card-body">
              <h5 class="card-title"><h4>{{country.name.common}}</h4></h5>
              <router-link :to="{ name: 'Country', params: { name: country.name.common }}" class="btn btn-primary">Detail</router-link>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
const axios = require('axios');
export default {
  data(){
    return {
      countries: null
    }
  },
  mounted(){
    axios.get('https://restcountries.com/v3.1/all')
          .then(response => {
            this.countries = response.data
          })
  }
}
</script>

<style scoped>

</style>