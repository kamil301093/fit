<script>
export default {
    data () {
        return {
            toAdd: 1
        }
    },
    props: {
        name: { required: true, type: String },
        qty: { required: true, type: Number },
        addFunction: { required: true },
    }
}
</script>

<template>
    <div class="bg-white flex justify-around">
        <span>{{ this.name }}</span>
        <span>{{ this.qty }}</span>
        <form @submit.prevent="this.addFunction">
            <input type="number" :value="this.toAdd" min="1" max="1000" step="1" />
            <input type="submit" value="+" />
        </form>
    </div>
</template>