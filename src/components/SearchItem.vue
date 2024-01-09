<script>
export default {
    props: {
        name: { required: true, type: String },
        qty: { required: true, type: Number },
        addFunction: { required: true, type: Function },
    }
}
</script>

<template>
    <div class="flex justify-around">
        <span>{{this.name}}</span>
        <span>{{this.qty}}</span>
        <span @click="this.addFunction">+</span>
    </div>
</template>