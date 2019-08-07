<template lang="html">
  <div class="">
    <h1>Countries</h1>
    <div class="container">
      <countries-list :countries='countries'></countries-list>
      <country-detail :country='selectedCountry'></country-detail>
    </div>
  </div>
</template>

<script>
import {eventBus} from './main.js';
import CountriesList from './components/CountriesList.vue';
import CountryDetail from './components/CountryDetail.vue';

export default {
  name: 'app',
  data(){
    return {
      countries: [],
      selectedCountry: null
    };
  },
  mounted(){
    const response = fetch('https://restcountries.eu/rest/v2/all')
    .then(response => response.json())
    .then(countries => this.countries = countries)

    eventBus.$on('country-selected', (country) => {
      this.selectedCountry = country;
    })
  },
  components: {
    "countries-list": CountriesList,
    "country-detail": CountryDetail
  }
}
</script>

<style lang="css" scoped>
</style>
