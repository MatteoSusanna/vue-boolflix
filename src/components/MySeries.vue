<template>
    <div>
        <h2>SERIES</h2>
        <div class="cards" >
                <div class="card" v-for="(serie, indice) in getSeries" :key="indice">
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

                    <div class="voto text_center">{{serie.vote_average}}</div>
                </div>
        </div>

    </div>
</template>

<script>
export default {
    nome: 'MySeries',
    props:{
        getSeries: Array
    }
}
</script>

<style>

</style>