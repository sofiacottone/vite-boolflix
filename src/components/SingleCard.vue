<script>


export default {
    name: 'SingleCard',
    props: ['movieInfo'],
    methods: {
        getFlag() {
            let flag = `/src/assets/img/flags/${this.movieInfo.original_language}.png`;
            return flag;
        }
    },
    mounted() {
    }
}
</script>

<template>

    <!-- single card  -->
    <div class="ms-flip-card bg-dark border">

        <div class="ms-flip-card-inner">

            <div class="ms-flip-card-front">
                <!-- <img src="https://image.tmdb.org/t/p/w342/cNYYPcbcfT90wTyI6hUmJH5Fx8H.jpg" alt=""> -->
            </div>

            <div class="ms-flip-card-back p-3">
                <div><span class="text-danger">Title: </span>{{ movieInfo.title || movieInfo.name }}</div>
                <div><span class="text-danger">Original Title: </span>{{ movieInfo.original_title ||
                    movieInfo.original_name }}</div>
                <div class="ms-flag-wrapper d-flex align-items-center gap-2">
                    <div><span class="text-danger">Original Language: </span> {{ movieInfo.original_language }}</div>
                    <img :src="getFlag()" onerror='this.style.display = "none"'>
                </div>
                <div><span class="text-danger">Rating: </span> {{ Math.floor(movieInfo.vote_average / 2) }}</div>
            </div>

        </div>
    </div>

</template>

<style scoped lang="scss">
.ms-flip-card {
    width: calc(100% / 3 - 20px);
    min-height: 360px;

    img {
        width: 100%;
        max-height: 100%;
        object-fit: contain;
        object-position: top;
    }

    .ms-flag-wrapper {

        img {
            width: 30px;

        }
    }
}
</style>