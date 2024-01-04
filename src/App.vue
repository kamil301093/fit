<script>
import axios from 'axios'
import CalcTarget from './components/CalcTarget.vue'
import CalStats from './components/CalStats.vue'
import SearchPanel from './components/SearchPanel'
import ListOf from './components/ListOf.vue'
import SiteFooter from './components/SiteFooter.vue'

export default {
  name: 'App',
  components: {
    CalcTarget,
    CalStats,
    SearchPanel,
    ListOf,
    SiteFooter
  },
  data() {
    return {
      myTrainings: [],
      myMeals: []
    }
  },
  mounted: function () {
    this.getMyTrainings(),
      this.getMyMeals()
  },
  methods: {
    getMyTrainings: async function () {
      try {
        const res = await axios.get(`http://localhost:3000/trainings`);
        this.myTrainings = res.data;
      } catch (error) {
        console.log(error);
      }
    },
    getMyMeals: async function () {
      try {
        const res = await axios.get(`http://localhost:3000/meal`);
        this.myMeals = res.data;
      } catch (error) {
        console.log(error);
      }
    }
  }
}
</script>

<template>
  <div class="text-center">
    <div class="m-auto w-[500px]">
      <CalcTarget />
      <CalStats />
      <SearchPanel url="https://api.api-ninjas.com/v1/caloriesburned?activity='"
        apiKey="/vYeXNNdQRDghe2/yU8qYw==trRLtfdZRF06dfSk" />
      <ListOf listName="Trainings" :listData="myTrainings" />
      <SearchPanel />
      <ListOf listName="Meals" :listData="myMeals" />
      <SiteFooter />
    </div>
  </div>
</template>

