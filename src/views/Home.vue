<template>
  <div v-if="!loading">
    <DataTitle :text="title" :dataDate="dataDate"/>
    <DataBoxes :stats="stats"/>
    <SelectCountry @updateCountry="updateCountryData" :countries="countries"/>
    <button
      v-if="stats.Country"
      class="inline-block align-middle bg-green-700 text-white rounded p-3 mt-10 focus:outline-none hover:bg-green-600 m-auto"
      @click="clearCountryData"
    >
      Clear Country
    </button>
  </div>
  <div class="flex flex-col align-center justify-center text-center" v-else>
    <img :src="loadingImage" class="w-24 m-auto" alt="loading">
    <div class="text-gray-500 text-3xl mt-10 mb-6">Fetching Data</div>
    </div>
</template>

<script>
import DataTitle from '@/components/DataTitle'
import DataBoxes from '@/components/DataBoxes'
import SelectCountry from '@/components/SelectCountry'
export default {
  name: 'Home',
  data() {
    return {
      loading: true,
      title: 'Global',
      stats: {},
      dataDate: '',
      countries: [],
      loadingImage: require('../assets/loading.gif')
    }
  },
  components: {
    DataTitle,
    DataBoxes,
    SelectCountry
  },
  methods: {
    async getStats() {
      const result =  await fetch('https://api.covid19api.com/summary')
      const stats = await result.json()
      return stats
    },
    updateCountryData(country) {
      this.stats = country
      this.title = country.Country
    },
    async clearCountryData() {
      const data = await this.getStats()
      this.title = 'Global'
      this.stats = data.Global
    }
  },
  async created() {
    const data = await this.getStats()
    this.countries = data.Countries
    this.stats = data.Global
    this.dataDate = data.date
    this.loading = false
  }
}
</script>
