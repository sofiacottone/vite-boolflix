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
    },
    methods: {
        horizontalScroll(event) {
            event.preventDefault();
            event.currentTarget.scrollLeft += event.deltaY
        },
    }
}
</script>

<template>
    <div class="bg-dark p-3 mt-5">
        <h3 class="fw-bold pt-3 pb-1 ps-1 text-white">Films</h3>
        <div class="ms-card-container d-flex justify-content-start overflow-x-auto bg-dark"
            @wheel="horizontalScroll($event)">
            <SingleCard v-for="movie in store.movies" :movieInfo="movie" :key="movie.id">
            </SingleCard>
        </div>

        <h3 class="fw-bold pt-4 pb-1 ps-1 text-white">TV Series</h3>
        <div class="ms-card-container d-flex justify-content-start overflow-x-auto bg-dark"
            @wheel="horizontalScroll($event)">
            <SingleCard v-for="series in store.series" :movieInfo="series" :key="series.id">
            </SingleCard>
        </div>


    </div>
</template>

<style scoped lang="scss">
.ms-card-container {
    /* Hide scrollbar for IE, Edge and Firefox */
    /* IE and Edge */
    -ms-overflow-style: none;
    /* Firefox */
    scrollbar-width: none;

    /* Hide scrollbar for Chrome, Safari and Opera */
    &::-webkit-scrollbar {
        display: none;
    }
}
</style>