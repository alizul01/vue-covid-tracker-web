<template>
  <main v-if="!loading">
    <div class="container">
      {{ data }}
    </div>
  </main>

  <main class="flex justify-center items-center flex-col text-center" v-else>
    <div class="text-gray-500 text-3xl mt-10 mb-6">
      Fetching Data
    </div>

    <img :src="loadingImage" alt="loading" class="w-64">
  </main>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'HomeView',
  components: {
  },
  data() {
    return {
      loading: true,
      title: 'Global',
      dataDate: '',
      status: {},
      countries: [],
      loadingImage: require('../assets/loading.gif')
    }
  },
  methods: {
    async fetchData() {
      const res = await fetch('https://api.covid19api.com/summary');
      const data = await res.json();

      return data;
    }
  },
  async created() {
    const data = await this.fetchData();

    this.dataDate = data.Date;
    this.stats = data.Global;
    this.countries = data.Countries;
    this.loading = false;
  },
}
</script>
