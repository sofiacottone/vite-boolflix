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
        getCardImage() {
            let cardImage = `https://image.tmdb.org/t/p/w342${this.movieInfo.poster_path}`;
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
    <div class="ms-flip-card col-xxl-2 col-xl-3 col-lg-4 col-md-6 col-sm-9 mb-4 mx-auto">

        <div class="ms-flip-card-inner border">

            <div class="ms-flip-card-front">
                <img v-if="movieInfo.poster_path" :src="getCardImage()" :alt="movieInfo.title || movieInfo.name">
                <div class="ms-img-placeholder d-flex justify-content-center align-items-center text-uppercase text-center fw-bold fs-4"
                    v-else>
                    {{ movieInfo.title
                    ||
                    movieInfo.name
                    }}</div>
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
    max-height: 800px;
    background-color: transparent;
    perspective: 1000px;

    &:hover .ms-flip-card-inner {
        transform: rotateY(180deg);
    }

    .ms-flip-card-inner {
        width: 100%;
        height: 100%;
        position: relative;
        transition: transform 0.8s;
        transform-style: preserve-3d;
        color: #fff;

        .ms-flip-card-front {
            width: 100%;
            height: 100%;
            backface-visibility: hidden;

            img {
                width: 100%;
                max-height: 100%;
                min-height: 440px;
                object-fit: cover;
                object-position: center;
                aspect-ratio: 2/3;
            }

            .ms-img-placeholder {
                background-color: #000;
                color: #dc3444;
                width: 100%;
                height: 100%;
            }
        }

        .ms-flip-card-back {
            width: 100%;
            height: 100%;
            position: absolute;
            top: 0;
            left: 0;
            backface-visibility: hidden;
            transform: rotateY(180deg);
            background-color: #000;

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
    }
}

@media screen and (max-width: 1200px) {
    .ms-flip-card {
        .ms-flip-card-inner {
            .ms-flip-card-back {
                font-size: 26px;

            }
        }
    }
}
</style>