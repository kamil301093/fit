<script>
export default {
    props: {
        itemName: { type: String },
        itemCal: { type: Number }
    }
}
</script>

<template>
    <div class="flex justify-around">
        <span>{{ itemName }}</span>
        <span>{{ itemCal }}</span>
        <a>remove</a>
    </div>
</template>