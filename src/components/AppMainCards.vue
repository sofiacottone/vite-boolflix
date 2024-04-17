<script>
import { store } from '../store.js'
import SingleCard from './SingleCard.vue'

export default {
    name: 'AppMainCards',
    components: {
        SingleCard
    },
    data() {
        return {
            store
        }
    }
}
</script>

<template>
    <div class="d-flex flex-wrap justify-content-start gap-4 text-bg-secondary p-3">
        <SingleCard v-for="movie in store.movies" :movieInfo="movie" :key="movie.id"></SingleCard>
    </div>
</template>

<style scoped lang="scss"></style>