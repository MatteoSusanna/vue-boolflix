<template>
  <header>
    <h1>BOOLFLIX</h1>
    <div class="wrapper-serch">

        <input type="text" 
        v-model="inputSerch"
        @keyup="$emit('inputSerch', inputSerch)">

        <button>Cerca</button>
    </div>
  </header>
</template>

<script>
export default {
    nome: 'MyHeader',
    data(){
        return{
            inputSerch: ''
        }
    }
}
</script>

<style lang="scss">
@import '../styles/general.scss';

    header{
        height: 100px;
        background-color: $header_color;
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding: 0 50px;
        h1{
            color: red;
            font-weight: 500;
        }
    }

</style>