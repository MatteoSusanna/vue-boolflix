<template>
  <header>
    <h1>BOOLFLIX</h1>
    <div>
        <input type="text">
        <button>Cerca</button>
    </div>
  </header>
</template>

<script>
export default {
    nome: 'MyHeader'
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