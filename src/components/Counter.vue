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

<style scoped></style>