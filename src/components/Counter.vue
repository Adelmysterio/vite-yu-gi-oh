<script>
import { store } from '../store.js';

export default {
    data() {
        return {
            store,
        }
    }
}
</script>

<template>
    <div>
        <p>Found {{ store.cards.length }} cards</p>
    </div>
</template>

<style lang="scss" scoped>
div {
    background-color: black;
    color: white;
    padding: 2rem;
    font-size: 2rem;
    font-weight: bold;

}
</style>