<script>
import axios from 'axios'
import CalcTarget from './components/CalcTarget.vue'
import CalStats from './components/CalStats.vue'
import SearchTrainings from './components/SearchTrainings'
import SearchMeal from './components/SearchMeal'
import ListOf from './components/ListOf.vue'
import SiteFooter from './components/SiteFooter.vue'

export default {
  name: 'App',
  components: {
    CalcTarget,
    CalStats,
    SearchTrainings,
    SearchMeal,
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
      <SearchTrainings />
      <ListOf listName="Activity" :listData="myTrainings" />
      <SearchMeal />
      <ListOf listName="Meals" :listData="myMeals" />
      <SiteFooter />
    </div>
  </div>
</template>

