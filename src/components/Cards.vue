<script>
import { store } from '../store.js'
export default {
    data() {
        return {
            store,
        }
    }
}
</script>

<template>
    <article v-for="(item, index) in store.cards" :key="index">
        <img :src="item.card_images[0].image_url" :alt="item.name">
        <section>
            <h4>{{ item.name }}</h4>
            <p>{{ item.archetype }}</p>
        </section>
    </article>
</template>

<style lang="scss" scoped>
article {
    width: calc(100% / 5 - 1rem);
    margin-bottom: 2rem;
    background-color: orange;

    img {
        width: 100%;
    }

    section {
        margin: 1rem;
        text-align: center;

        h4 {
            color: white;
            margin-bottom: .5rem;
        }
    }
}
</style>