<script>
    import SearchInput from './SearchInput'
    import SearchItem from './SearchItem.vue'

    export default {
        components: {
            SearchInput,
            SearchItem
        },
        props: {
            url: { required: true, type: String }
        }
    }
</script>

<template>
    <SearchInput />
    <SearchItem />
    <SearchItem />
    <SearchItem />
</template>