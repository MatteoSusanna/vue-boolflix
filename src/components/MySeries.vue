<template>
    <div>
        <h2>SERIES</h2>
        <div class="cards" >
                <div class="card" v-for="(serie, indice) in getSeries" :key="indice">
                    
                    <img class="copertina d-block" :src="'https://image.tmdb.org/t/p/w342' + serie.poster_path " />
                    
                    <div class="info d-none">
                        <div class="titolo text_center">{{serie.name}}</div>
                        <div class="titolo-originale text_center">{{serie.original_name}}</div>

                        <div class="wrapperor_language">

                            <div class="lingua" v-if="(serie.original_language == 'en')">
                                <img src="../assets/ing.png">
                            </div>
                            <div class="lingua" v-else-if="(serie.original_language == 'it')">
                                <img src="../assets/ita.png">
                            </div>
                            <div class="lingua" v-else-if="(serie.original_language == 'fr')">
                                <img src="../assets/fra.png">
                            </div>
                            <div class="lingua" v-else-if="(serie.original_language == 'ja')">
                                <img src="../assets/ja.png">
                            </div>
                            <div class="lingua" v-else-if="(serie.original_language == 'es')">
                                <img src="../assets/es.png">
                            </div>
                            <div class="lingua" v-else-if="(serie.original_language == 'ko')">
                                <img src="../assets/ko.png">
                            </div>

                            <div class="lingua text_center" v-else>{{serie.original_language}}</div>

                        </div>

                        <div class="punteggio">
                            <div class="t-center" v-if="calcolaVoto(serie.vote_average) == 1">
                                <i class="fa-solid fa-star"></i>
                                <i class="fa-solid fa-star color_gray"></i>
                                <i class="fa-solid fa-star color_gray"></i>
                                <i class="fa-solid fa-star color_gray"></i>
                                <i class="fa-solid fa-star color_gray"></i>
                            </div>
                            <div class="t-center" v-else-if="calcolaVoto(serie.vote_average) == 2">
                                <i class="fa-solid fa-star"></i>
                                <i class="fa-solid fa-star"></i>
                                <i class="fa-solid fa-star color_gray"></i>
                                <i class="fa-solid fa-star color_gray"></i>
                                <i class="fa-solid fa-star color_gray"></i>
                            </div>
                            <div class="t-center" v-else-if="calcolaVoto(serie.vote_average) == 3">
                                <i class="fa-solid fa-star"></i>
                                <i class="fa-solid fa-star"></i>
                                <i class="fa-solid fa-star"></i>
                                <i class="fa-solid fa-star color_gray"></i>
                                <i class="fa-solid fa-star color_gray"></i>
                            </div>
                            <div class="t-center" v-else-if="calcolaVoto(serie.vote_average) == 4">
                                <i class="fa-solid fa-star"></i>
                                <i class="fa-solid fa-star"></i>
                                <i class="fa-solid fa-star"></i>
                                <i class="fa-solid fa-star"></i>
                                <i class="fa-solid fa-star color_gray"></i>
                            </div>
                            <div class="t-center" v-else-if="calcolaVoto(serie.vote_average) == 5">
                                <i class="fa-solid fa-star"></i>
                                <i class="fa-solid fa-star"></i>
                                <i class="fa-solid fa-star"></i>
                                <i class="fa-solid fa-star"></i>
                                <i class="fa-solid fa-star"></i>
                            </div>
                            <div v-else class="voto text_center">{{calcolaVoto(serie.vote_average)}}</div>
                        </div>
                    </div>
                </div>
        </div>

    </div>
</template>

<script>
export default {
    nome: 'MySeries',
    props:{
        getSeries: Array,
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
    .text_center{
        text-align: center;
    }
    .d-block{
        display: block;
    }
    .d-none{
        display: none;
    }
    .t-center{
        text-align: center;
    }


    .cards{
            display: flex;
            flex-wrap: wrap;
            color: $text_color;
            width: 1700px;
            margin: 0 auto;
            .card{
                background-color: black;
                height: 200px;
                width: 200px;
                flex-basis: 15%;
                border: 1px solid red;

                .copertina{
                    width: 100%;
                    height: 100%;
                    object-fit: contain;
                }
                
                img{
                    width: 100%;
                    object-fit: cover;
                }
                &:hover .copertina{
                        display: none;
                }
                &:hover .info{
                        display: block;
                }
            }
        }

</style>