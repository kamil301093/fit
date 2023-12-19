<script>
import SingleItem from './SingleItem'
export default {
    components: {
        SingleItem
    },
    props: {
        listName: { type: String },
        listData: { type: Object }
    }
}
</script>

<template>
    <div>
        <h2 class="text-left">{{ listName }}</h2>
        <SingleItem v-for="item of listData" :key="item.id" :itemName="item.name" :itemCal="item.cal" />
    </div>
</template>