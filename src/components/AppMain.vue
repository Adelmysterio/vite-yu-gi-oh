<script>
import Cards from './Cards.vue';
import { store } from '../store.js';
import axios from 'axios';
import Loader from './Loader.vue'

export default {
    components: {
        Cards,
        Loader
    },
    data() {
        return {
            store,
            isLoaded: false
        };
    },
    created() {
        axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0')
            .then((response) => {
                console.log(response.data.data);
                this.store.cards = response.data.data;
                this.isLoaded = true
            })
            .catch((error) => {
                console.error(error);
            });
    }
}
</script>

<template>
    <main>
        <div>
            <Cards v-if="isLoaded"/>
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