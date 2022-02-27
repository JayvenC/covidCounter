<template>
<img :src="image2" class='w-24 m-auto' alt=""/>
  <main v-if="!loading">
    <DataTitle :text="title" :dateOfData="dateOfData"/>
    <Boxes :stats='stats' />
  </main>
  <main class='flex flex-col align-center justify-center text-center' v-else>
    <div class='text-gray-500 text-3xl mt-10 mb-6'> 
      Grabbing the Data
    </div>
    <img :src="image" class="w-24 m-auto" alt="">
  </main>
</template>

<script>
import DataTitle from '@/components/DataTitle'
import Boxes from '@/components/Boxes'
export default {
  name: 'HomeView',
  components: {
    DataTitle,
    Boxes 
  },
  data() {
    return {
      loading: true,
      title: 'Global',
      dateOfData: '',
      stats: {},
      countries: [],
      image: require('../assets/loading.gif'),
      image2: require('../assets/covid19.png')

    }
  },
  methods: {
   async fetchData() {
     const res = await fetch('https://api.covid19api.com/summary')
     const data = await res.json()
     return data
    }
  },
   async created() {
     const data = await this.fetchData()
     
     this.dateOfData = data.Date
     this.stats = data.Global
     this.countries = data.Countries
     this.loading = false

   }
}
</script>
