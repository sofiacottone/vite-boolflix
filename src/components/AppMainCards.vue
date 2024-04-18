<script>
import { store } from '../store.js'
import SingleCard from './SingleCard.vue'

export default {
    name: 'AppMainCards',
    components: {
        SingleCard,
    },
    data() {
        return {
            store
        }
    }
}
</script>

<template>
    <div class="text-bg-secondary p-3 mt-5">
        <h3 class="fw-bold pt-3 pb-1 ps-1">Films</h3>
        <div class="d-flex flex-wrap justify-content-start gap-4 text-bg-secondary">
            <SingleCard v-for="movie in store.movies" :movieInfo="movie" :key="movie.id">
            </SingleCard>
        </div>

        <h3 class="fw-bold pt-4 pb-1 ps-1">TV Series</h3>
        <div class="d-flex flex-wrap justify-content-start gap-4 text-bg-secondary">
            <SingleCard v-for="series in store.series" :movieInfo="series" :key="series.id">
            </SingleCard>
        </div>


    </div>
</template>

<style scoped lang="scss"></style>