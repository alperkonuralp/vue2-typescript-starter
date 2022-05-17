<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" style="height: 10%" />
    <h1>Ülkeler:</h1>
    <table align="center">
      <thead>
        <tr>
          <th>Alpha Kod 2</th>
          <th>Alpha Kod 3</th>
          <th>İsim</th>
          <th>Başkent</th>
          <th>Bölge</th>
          <th>Nüfus</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="country of countries" :key="country.alpha3Code">
          <td>{{ country.alpha2Code }}</td>
          <td>{{ country.alpha3Code }}</td>
          <td>{{ country.name }}</td>
          <td>{{ country.capital }}</td>
          <td>{{ country.region }} / {{ country.subregion }}</td>
          <td align="right">{{ country.population }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import axios from "axios";
import { Country } from "./types";

@Component
export default class App extends Vue {
  private countries: Country[] = [];

  created() {
    axios
      .get("https://restcountries.com/v2/all")
      .then((x) => (this.countries = x.data));
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
