<script>
export default {
    props: {
        name: { required: true, type: String },
        qty: { required: true, type: Number },
    },
}
</script>

<template>
    <div>
        <h3 class="">{{props.qty}}</h3>
        <h4 class="">{{props.name}}</h4>
    </div>
</template>