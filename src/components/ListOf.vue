<script>
import AddedItem from './AddedItem'
export default {
    components: {
        AddedItem
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
        <AddedItem v-for="item of listData" :key="item.id" :itemName="item.name" :itemCal="item.cal" />
    </div>
</template>