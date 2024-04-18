<script>
import axios from 'axios';
import { store } from './store.js'
import AppHeader from './components/AppHeader.vue';
import AppMainCards from './components/AppMainCards.vue';

export default {
    components: {
        AppHeader,
        AppMainCards
    },
    data() {
        return {
            store,
            queryParams: {
                query: 'a',
                media_type: ''
            }
        }
    },
    methods: {
        getMoviesFromApi() {
            // movies 
            let apiUrl = 'https://api.themoviedb.org/3/search/movie?api_key=f016167b7ad1b63b57570a64d8de7087';

            if (store.searchedMovie !== '') {
                this.queryParams.query = store.searchedMovie;
                store.searchedMovie = ''
            }

            axios.get(apiUrl, {
                params: this.queryParams
            })
                .then((response) => {
                    store.movies = response.data.results
                })

            // tv series 
            let seriesApiUrl = 'https://api.themoviedb.org/3/search/tv?api_key=f016167b7ad1b63b57570a64d8de7087';
            axios.get(seriesApiUrl, {
                params: this.queryParams
            })
                .then((response) => {
                    store.series = response.data.results
                })
        }
    },
    mounted() {
        this.getMoviesFromApi();
        // this.getSeriesFromApi();
    }
}
</script>

<template>
    <AppHeader @searchPerformed="getMoviesFromApi"></AppHeader>

    <main>
        <AppMainCards></AppMainCards>
    </main>
</template>

<style lang="scss">
@use './style/generic.scss' as *;
</style>