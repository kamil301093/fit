<script>
import axios from 'axios';
import SingleStat from './SingleStat.vue'

export default {
    name: 'CalStats',
    components: {
        SingleStat
    },
    data() {
        return {
            calStats: []
        }
    },
    mounted: function () {
        this.getCalStats()
    },
    methods: {
        getCalStats: async function () {
            try {
                const res = await axios.get(`http://localhost:3000/cal`);
                this.calStats = res.data;
            } catch (error) {
                console.log(error);
            }
        }
    }
}
</script>

<template>
    <div>
        <h2 class="text-left text-xl">daily target: {{calStats.target}} +calculate</h2>
        <div class="flex justify-around">
            <SingleStat name="Eaten" :qty="calStats.eaten" />
            <SingleStat name="Burned" :qty="calStats.burned" />
            <SingleStat name="Left" :qty="calStats.left" />
        </div>
    </div>
</template>