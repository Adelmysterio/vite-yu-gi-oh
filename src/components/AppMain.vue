<script>
import Cards from './Cards.vue';
import Loader from './Loader.vue';
import AppSelectSearch from './AppSelectSearch.vue'
import { store } from '../store.js';
import axios from 'axios';

export default {
    components: {
        Cards,
        Loader,
        AppSelectSearch
    },
    data() {
        return {
            store,
            isLoaded: false
        };
    },

    methods: {
        getCards: function(){
            axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=100&offset=0')
            .then((response) => {
                console.log(response.data.data);
                this.store.cards = response.data.data;
                this.isLoaded = true
            })
            .catch((error) => {
                console.error(error);
            });
        },

        getArchetypes: function () {
            axios.get('https://db.ygoprodeck.com/api/v7/archetypes.php')
            .then((response) => {
                console.log(response.data);
                this.store.archetypes = response.data;
                this.isLoaded = true
            })
            .catch((error) => {
                console.error(error);
            });
        }


    },
    created() {
     this.getCards(),
     this.getArchetypes()
    }
}
</script>

<template>
    <main>
        <AppSelectSearch />
        <div>
            <Cards v-if="isLoaded" />
            <Loader v-else />
        </div>
    </main>
</template>

<style scoped>
main {
    background-color: orange;
    padding: 5rem 0;
}

div {
    margin: 0 auto;
    padding: 2rem;
    max-width: 1200px;
    background-color: white;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
}
</style>