<script>
export default {
    props: {
        name: { required: true, type: String },
        qty: { required: true, type: Number }
    },
}
</script>

<template>
    <div>
        <h3 class="">{{this.qty}}</h3>
        <h4 class="">{{this.name}}</h4>
    </div>
</template>