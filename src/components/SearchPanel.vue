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
        apiKey: { required: true, type: String }
    },
    methods: {
        handleInput(e) {
            this.keyword = e.target.value;
            this.search();
        },
        clear() {
            this.keyword = '';
            this.results = [];
        },
        search: async function () {
            try {console.log(this.apiKey)
                const link = this.url + '' + this.keyword;
                const res = await axios.get(link, { 'X-Api-Key': this.apiKey })
                console.log(res.data);
            } catch (error) {
                console.log(error);
            }
        }
    }
}
</script>

<template>
    <form>
        <input @input="handleInput" class="bg-gray-300" type="text" :value="this.keyword" />
        <input type="button" value="Clear" @click="clear" />
    </form>
    <div>
        <SearchItem />
    </div>
</template>