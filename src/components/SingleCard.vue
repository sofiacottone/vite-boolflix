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
    <div class="ms-flip-card bg-dark">
        <div class="ms-flip-card-inner">
            <div class="ms-flip-card-front">
                <img src="https://image.tmdb.org/t/p/w342/cNYYPcbcfT90wTyI6hUmJH5Fx8H.jpg" alt="">
            </div>
            <div class="ms-flip-card-back">
                <div>{{ movieInfo.title }}</div>
                <div>{{ movieInfo.original_title }}</div>
                <div class="ms-flag-wrapper d-flex align-items-center gap-2">
                    <div>{{ movieInfo.original_language }}</div>
                    <img :src="getFlag()" onerror='this.style.display = "none"'>
                </div>
                <div>{{ Math.floor(movieInfo.vote_average / 2) }}</div>
            </div>
        </div>
    </div>

</template>

<style scoped lang="scss">
.ms-flip-card {
    width: calc(100% / 3 - 20px);

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