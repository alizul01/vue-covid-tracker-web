<template>
  <main v-if="!loading" class="mb-24 md:mb-0">
    <div class="container">
      <DataTitle :text="title" :dataDate="timestamp" />
      <DataBoxes :stats="stats" />
    </div>
    <CountrySelect :countries="countries" @get-country="getCountryData" />

    <button
      v-if="stats.Country"
      class="
        mt-4
        bg-red-500
        hover:bg-red-700
        text-white
        font-medium
        py-2
        px-4
        rounded
        focus:outline-none focus:shadow-outline
      "
      @click="clearCountryData"
    >
      Refresh
    </button>
  </main>

  <main class="flex justify-center items-center flex-col text-center" v-else>
    <div class="text-gray-500 text-3xl mt-10 mb-6">Fetching Data</div>

    <img :src="loadingImage" alt="loading" class="w-64" />
  </main>
</template>

<script>
// @ is an alias to /src
import DataTitle from "@/components/DataTitle.vue";
import moment from "moment";
import DataBoxes from "@/components/DataBoxes.vue";
import CountrySelect from "@/components/CountrySelect.vue";

export default {
  name: "HomeView",
  components: {
    DataTitle,
    DataTitle,
    DataBoxes,
    CountrySelect,
  },
  data() {
    return {
      loading: true,
      title: "Global",
      dataDate: "",
      status: {},
      countries: [],
      loadingImage: require("../assets/loading.gif"),
    };
  },
  computed: {
    timestamp: function () {
      return moment(this.dataDate).format("MMMM Do YYYY, h:mm:ss a");
    },
  },
  methods: {
    async fetchData() {
      const res = await fetch("https://api.covid19api.com/summary");
      const data = await res.json();

      return data;
    },
    getCountryData(country) {
      this.stats = country;
      this.title = country.Country;
    },
    async clearCountryData() {
      this.loading = true;
      const data = await this.fetchData();
      this.stats = data.Global;
      this.title = "Global";
      this.loading = false;
    },
  },
  async created() {
    const data = await this.fetchData();

    this.dataDate = data.Date;
    this.stats = data.Global;
    this.countries = data.Countries;
    this.loading = false;
  },
};
</script>
