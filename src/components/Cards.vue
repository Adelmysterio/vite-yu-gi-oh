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
    <article v-for="item in cards">
        <img src="" alt="">
    </article>
</template>

<style scoped></style>