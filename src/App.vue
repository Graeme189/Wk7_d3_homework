<template lang="html">
  <div class="">
    <h1>Countries</h1>
    <div class="container">
      <countries-list :countries='countries'></countries-list>
    </div>
  </div>
</template>

<script>
import CountriesList from './components/CountriesList.vue'
import CountryDetail from './components/CountryDetail.vue'

export default {
  name: 'app',
  data(){
    return {
      countries: []
    };
  },
  mounted(){
    const response = fetch('https://restcountries.eu/rest/v2/all')
    .then(response => response.json())
    // console.log(response); //check this returns to the console
    .then(countries => this.countries = countries)
  },
  components: {
    "countries-list": CountriesList,
    "country-detail": CountryDetail
  }
}
</script>

<style lang="css" scoped>
</style>
