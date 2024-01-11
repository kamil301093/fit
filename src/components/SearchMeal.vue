<script>
import axios from 'axios'
import SearchItem from './SearchItem.vue'


export default {
    components: {
        SearchItem
    },
    data() {
        return {
            searchUrl: 'https://api.api-ninjas.com/v1/nutrition?query=',
            apiKey: '/vYeXNNdQRDghe2/yU8qYw==trRLtfdZRF06dfSk',
            keyword: '',
            results: [],
            dataToAdd: {},
            pushUrl: 'http://localhost:3000/meal'
        }
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
            try {
                const link = this.searchUrl + '' + this.keyword;
                const res = await axios(link, {
                    headers: {
                        'X-Api-Key': this.apiKey
                    }
                })
                this.results = res.data;
            } catch (error) {
                console.log(error);
            }
        },
        handleItem(meal, cal) {
            const handledItem = { name: meal, cal: cal };
            this.dataToAdd = handledItem;
            this.addItem();
        },
        addItem: async function () {
            try {
                const link = this.pushUrl;
                const data = this.dataToAdd;
                const res = await axios.post(link, data);
                console.log(res);
            } catch (error) {
                console.log(error)
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
    <div class="fixed">
        <SearchItem v-for="result of results" :key="result.name" :name="result.name" :qty="result.calories"
            :addFunction="handleItem(result.name, result.calories)" />
    </div>
</template>