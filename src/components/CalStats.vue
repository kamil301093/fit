<script>
    import SingleStat from './SingleStat.vue'
    export default {
        name: 'CalStats',
        components: {
            SingleStat
        },
        props: {
            eaten: { required: true, type: Number },
            burned: { required: true, type: Number },
            left: { required: true, type: Number }
        }
    }
</script>

<template>
    <div>
        <h2 class="text-left text-xl">daily target: target  +calculate</h2>
        <div class="flex justify-around">
            <SingleStat />
            <SingleStat />
            <SingleStat />
        </div>
    </div>
</template>