<script>
import axios from 'axios'
import SearchItem from './SearchItem.vue'

export default {
    components: {
        SearchItem
    },
    data() {
        return {
            keyword: '',
            results: []
        }
    },
    props: {
        url: { required: true, type: String },
        apiKey: { required: true, type: String },
    },
    methods: {
        handleInput(e) {
            this.keyword = e.target.value; console.log(this.keyword)
        },
        clear() {
            this.keyword = '';
            this.results = [];
        },
        search: async function () {
            try {
                const link = this.url + '' + this.keyword; console.log(link);
                const res = await axios.get(link, {
                    headers: {
                        'x-rapidapi-host': this.url,
                        'x-rapidapi-key': this.apiKey
                    }
                }
                );
                console.log(res.data);
            } catch (error) {
                console.log(error);
            }
        }
    }
}
</script>

<template>
    <form @submit.prevent="search">
        <input @input="handleInput" class="bg-gray-300" type="text" :value="this.keyword" />
        <input type="submit" value="Search" />
        <input type="button" value="Clear" @click="clear" />
    </form>
    <div>
        <SearchItem />
    </div>
</template>