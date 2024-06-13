<script>
import { store } from '../store.js';

export default {
    data() {
        return {
            store,
            selectedArchetype: 'all'
        }
    }
}
</script>

<template>
    <select id="select-archetype" v-model="selectedArchetype" @change="$emit('cardArchetype', selectedArchetype)">
        <option value="all" selected>All</option>
        <option v-for="(item, index) in store.archetypes" :key="index" :value="item.archetype_name">{{ item.archetype_name }}</option>
    </select>
</template>

<style lang="scss" scoped>
select {
    padding: .5rem;
    font-size: 1rem;
}
</style>