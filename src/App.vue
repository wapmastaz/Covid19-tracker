<template>
  <div>
    <Header />
    <div class="container sm:container p-4">
      <main v-if="!isLoading" class="flex flex-col justify-center align-center">
        <data-title :title="title" :dataDate="dataDate" />

        <data-boxes :stats="stats"/>

        <country-select @get-country="getCountryStats" :countries="countries" />

        <button @click="clearCountryData()" v-if="stats.Country" class="bg-green-700 rounded p-3 text-white shadow:md mt-10">
          Clear Country
        </button>
      </main>

      <main v-else>
        <div class="w-24 mx-auto flex flex-col justify-center">
          <img :src="loadingImage" alt="Loading Image" />
        </div>
      </main>
    </div>
  </div>
</template>

<script>
import Header from "./components/Header";
import DataTitle from "./components/DataTitle.vue"
import DataBoxes from "./components/DataBoxes.vue";
import CountrySelect from "./components/CountrySelect.vue";
import axios from "axios";
export default {
  name: "App",
  components: {
    Header,
    DataTitle,
    DataBoxes,
    CountrySelect
  },
  data() {
    return {
      title: "Global",
      dataDate: "",
      isLoading: true,
      loadingImage: require("../src/assets/loader.gif"),
      stats: {},
      countries: [],
    };
  },
  methods: {
    getCovidData() {
      axios({
        method: "get",
        url: "https://api.covid19api.com/summary",
      })
        .then((res) => {
          console.log(res);
          (this.dataDate = res.data.Date),
            (this.stats = res.data.Global),
            (this.countries = res.data.Countries);
          this.isLoading = false;
          // console.log(this.stats)
        })
        .catch((err) => {
          console.log(err);
        });
    },
    getCountryStats(country) {
      this.title = country.Country
      this.stats = country
    },
    clearCountryData() {
      this.isLoading = true;
      this.title = "Global"
      const data = this.getCovidData();
      this.stats = data
      this.isLoading = false
      
    }
  },
  created() {
    this.getCovidData();
  },
};
</script>

<style></style>
