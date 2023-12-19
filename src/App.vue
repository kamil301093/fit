<script>
import axios from 'axios'
import CalStats from './components/CalStats.vue'
import SearchPanel from './components/SearchPanel'
import ListOf from './components/ListOf.vue'
import SiteFooter from './components/SiteFooter.vue'

export default {
  name: 'App',
  components: {
    CalStats,
    SearchPanel,
    ListOf,
    SiteFooter
  },
  data() {
    return {
      trainings: []
    }
  },
  async created() {
    try {
      const res = await axios.get(`http://localhost:3000/trainings`);
      this.trainings = res.data;
    } catch (error) {
      console.log(error);
    }
  }
}
</script>

<template>
  <div class="text-center">
    <div class="m-auto w-[500px]">
      <CalStats />
      <SearchPanel />
      <ListOf name="Trainings" :listData="trainings" />
      <SearchPanel />
      <ListOf name="Meals" />
      <SiteFooter />
    </div>
  </div>
</template>

