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
    <select  id="select-archetype">
        <option v-for="(item, index) in store.archetypes" :key="index" value="item">{{ item.archetype_name }}</option>
    </select>
</template>

<style scoped></style>