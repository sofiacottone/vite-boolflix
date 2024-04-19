<script>


export default {
    name: 'SingleCard',
    props: ['movieInfo'],
    data() {
        return {
            stars: []
        }
    },
    methods: {
        getFlag() {
            let flag = `/src/assets/img/flags/${this.movieInfo.original_language}.png`;
            return flag;
        },
        getCardImage(movieInfo) {
            let cardImage = `https://image.tmdb.org/t/p/w342${movieInfo.poster_path}`;
            return cardImage;
        },
        getRatingStars() {
            let voteAverage = Math.floor(this.movieInfo.vote_average / 2);
            for (let i = 0; i < 5; i++) {
                if (i < voteAverage) {
                    this.stars.push('fa-solid')
                } else {
                    this.stars.push('fa-regular')
                }
            }
        }
    },
    mounted() {
        this.getRatingStars();
    }
}
</script>

<template>

    <!-- single card  -->
    <div class="ms-flip-card col-xxl-2 col-xl-3 col-lg-4 col-md-6 col-sm-12 bg-dark border mb-4">

        <div class="ms-flip-card-inner">

            <div class="ms-flip-card-front">
                <img :src="getCardImage(movieInfo)" :alt="movieInfo.title || movieInfo.name">
            </div>

            <div class="ms-flip-card-back p-3">
                <div><span class="text-danger">Title: </span>{{ movieInfo.title || movieInfo.name }}</div>
                <div><span class="text-danger">Original Title: </span>{{ movieInfo.original_title ||
                    movieInfo.original_name }}</div>
                <div>
                    <span class="text-danger">Original Language: </span>

                    <div class="d-flex align-items-center gap-2">
                        {{ movieInfo.original_language }}
                        <div class="ms-flag-wrapper">
                            <img :src="getFlag()" onerror='this.style.display = "none"'>
                        </div>
                    </div>
                </div>
                <div>
                    <span class="text-danger">Rating: </span>
                    <i v-for="star in stars" :class="star" class="fa-star"></i>
                    ({{ Math.floor(movieInfo.vote_average / 2) }})
                </div>
            </div>

        </div>
    </div>

</template>

<style scoped lang="scss">
.ms-flip-card {
    // width: calc(100% / 3 - 20px);
    min-height: 310px;

    .ms-flip-card-front {
        img {
            width: 100%;
            max-height: 100%;
            min-height: 440px;
            object-fit: cover;
            object-position: center;
            aspect-ratio: 2/3;
        }

    }

    .ms-flag-wrapper {
        width: 30px;
        height: 30px;

        img {
            width: 100%;
            max-height: 100%;
        }
    }

    i {
        &.fa-solid {
            color: #dc3444;
        }
    }
}
</style>