<script>
import Cards from './Cards.vue';
import { store } from '../store.js'
import axios from 'axios';

axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0')
    .then((response) => {
        console.log(response.data);
        response.data = this.store.cards
    })
    .catch(function (error) {
        console.log(error);
    })
    .finally(function () {
    });

export default {
    components: {
        Cards
    },

    data() {
        return {
            store,
        }
    }
}
</script>

<template>
    <main>
        <div>
            <Cards />
        </div>
    </main>
</template>

<style scoped>
main {
    background-color: orangered;
}
</style>