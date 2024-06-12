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
        <p>{{ item.name }}</p>
    </article>
</template>

<style scoped></style>