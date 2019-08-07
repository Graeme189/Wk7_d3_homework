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
    fetch('https://restcountries.eu/rest/v2/all')
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

<style>
body {
  background: #F09819;  /* fallback for old browsers */
  background: -webkit-linear-gradient(to bottom, #EDDE5D, #F09819);  /* Chrome 10-25, Safari 5.1-6 */
  background: linear-gradient(to bottom, #EDDE5D, #F09819); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
  font-family: cursive;
}
.container {
  display: flex;
  justify-content: center;
}
h1 {
 text-align: center;
}
</style>
