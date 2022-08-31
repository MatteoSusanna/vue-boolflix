<template>
    <div class="wrapper">
        <h1 class="mtb">FILM</h1>
        <div class="cards">
            <div class="card" v-for="(film, indice) in getFilm" :key="indice">

                <img class="copertina d-block" :src="'https://image.tmdb.org/t/p/w342' + film.poster_path " />

                <div  class="info d-none">
                    <div class="titolo text_center">{{film.title}}</div>
                    <div class="titolo-originale text_center">{{film.original_title}}</div>

                    <div class="wrapper_language">

                            <div class="lingua" v-if="(film.original_language == 'en')">
                                <img class="bandiera" src="../assets/ing.png">
                            </div>
                            <div class="lingua" v-else-if="(film.original_language == 'it')">
                                <img class="bandiera" src="../assets/ita.png">
                            </div>
                            <div class="lingua" v-else-if="(film.original_language == 'fr')">
                                <img class="bandiera" src="../assets/fra.png">
                            </div>
                            <div class="lingua" v-else-if="(film.original_language == 'ja')">
                                <img class="bandiera" src="../assets/ja.png">
                            </div>
                            <div class="lingua" v-else-if="(film.original_language == 'es')">
                                <img class="bandiera" src="../assets/es.png">
                            </div>
                            <div class="lingua" v-else-if="(film.original_language == 'ko')">
                                <img class="bandiera" src="../assets/ko.png">
                            </div>
                            <div class="lingua text_center" v-else>{{film.original_language}}</div>
                    </div>

                    <div class="punteggio">
                        <div class="t-center" v-if="calcolaVoto(film.vote_average) == 1">
                            <i class="fa-solid fa-star"></i>
                            <i class="fa-solid fa-star color_gray"></i>
                            <i class="fa-solid fa-star color_gray"></i>
                            <i class="fa-solid fa-star color_gray"></i>
                            <i class="fa-solid fa-star color_gray"></i>
                        </div>
                        <div class="t-center" v-else-if="calcolaVoto(film.vote_average) == 2">
                            <i class="fa-solid fa-star"></i>
                            <i class="fa-solid fa-star"></i>
                            <i class="fa-solid fa-star color_gray"></i>
                            <i class="fa-solid fa-star color_gray"></i>
                            <i class="fa-solid fa-star color_gray"></i>
                        </div>
                        <div class="t-center" v-else-if="calcolaVoto(film.vote_average) == 3">
                            <i class="fa-solid fa-star"></i>
                            <i class="fa-solid fa-star"></i>
                            <i class="fa-solid fa-star"></i>
                            <i class="fa-solid fa-star color_gray"></i>
                            <i class="fa-solid fa-star color_gray"></i>
                        </div>
                        <div class="t-center" v-else-if="calcolaVoto(film.vote_average) == 4">
                            <i class="fa-solid fa-star"></i>
                            <i class="fa-solid fa-star"></i>
                            <i class="fa-solid fa-star"></i>
                            <i class="fa-solid fa-star"></i>
                            <i class="fa-solid fa-star color_gray"></i>
                        </div>
                        <div class="t-center" v-else-if="calcolaVoto(film.vote_average) == 5">
                            <i class="fa-solid fa-star"></i>
                            <i class="fa-solid fa-star"></i>
                            <i class="fa-solid fa-star"></i>
                            <i class="fa-solid fa-star"></i>
                            <i class="fa-solid fa-star"></i>
                        </div>
                        <div v-else class="voto text_center">{{calcolaVoto(film.vote_average)}}</div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    nome: 'MyCard',
    props:{
        getFilm: Array,
    },
    methods:{
        calcolaVoto(voto){
            return Math.floor(voto / 2);
        }
    }
}
</script>

<style lang="scss">
@import '../styles/general.scss';
    .mtb{
        margin: 50px 0;
    }
    .color_gray{
        color: gray;
    }
    .text_center{
        text-align: center;
    }
    .d-block{
        display: block;
    }
    .d-none{
        display: none;
    }

    .cards{
            display: flex;
            flex-wrap: wrap;
            color: $text_color;
            width: 1400px;
            margin: 0 auto;
            .card{
                background-color: black;
                height: 400px;
                width: 200px;
                flex-basis: 15%;
                border: 1px solid white;
                padding: 15px 2px;

                .copertina{
                    width: 100%;
                    height: 100%;
                    object-fit: cover;
                }
                
                &:hover .copertina{
                        display: none;
                }
                &:hover .info{
                        display: block;
                }
            }
            .lingua{
                height: 40px;
                width: 40px;
                margin: 40px auto;

                .bandiera{
                    width: 100%;
                    object-fit: cover;
                }
            }
        }

</style>