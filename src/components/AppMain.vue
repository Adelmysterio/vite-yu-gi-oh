<script>
import Cards from './Cards.vue';
import Loader from './Loader.vue';
import Counter from './Counter.vue';
import AppSelectSearch from './AppSelectSearch.vue'
import { store } from '../store.js';
import axios from 'axios';

export default {
    components: {
        Cards,
        Loader,
        AppSelectSearch,
        Counter
    },
    data() {
        return {
            store,
            isLoaded: false
        };
    },

    methods: {
        getCards: function () {
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
        },

        getCardsByArchetype: function (archString) {
            axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=100&offset=0', {
                params: {
                    archetype: archString
                }
            })
                .then((response) => {

                    console.log(response.data.data);
                    this.store.cards = response.data.data;
                    this.isLoaded = true
                })
                .catch((error) => {
                    console.error(error);
                });
        },

        filterCards: function (arch) {
            if (arch == 'all') {
                this.getCards()
            }
            else { this.getCardsByArchetype(arch) }
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
        <div class="container">
            <AppSelectSearch @cardArchetype="filterCards" />
            <Counter />
            <section>
                <div>
                    <Cards v-if="isLoaded" />
                    <Loader v-else />
                </div>
            </section>
        </div>
    </main>
</template>

<style lang="scss" scoped>
div.container {
    margin: 0 auto;
    max-width: 1200px;
}

main {
    background-color: orange;
    padding: 5rem 0;
}

section {
    padding: 2rem;
    background-color: white;

    div {
        display: flex;
        flex-wrap: wrap;
        justify-content: space-around;
    }
}
</style>