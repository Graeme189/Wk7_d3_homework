<template lang="html">
  <div class="">
    <h1>Countries</h1>
    <div class="container">
      <li v-for="country in countries">{{ country.name }}</li>
    </div>
  </div>
</template>

<script>
export default {
  name: 'app',
  data(){
    return {
      countries: []
    }
  },
  mounted(){
    const response = fetch('https://restcountries.eu/rest/v2/all')
    .then(response => response.json())
    // console.log(response); //check this returns to the console
    .then(countries => this.countries = countries)
  }
}
</script>

<style lang="css" scoped>
</style>
