<template>
    <div class="container-botao-adicionar">
        <img src="../../assets/images/icon-add-to-cart.svg" alt="">
        <p>Adicionar</p>
    </div>
    <div class="container-botao-adicionar-ativo">
        <img src="../../assets/images/icon-decrement-quantity.svg" alt="">
        <p>1</p>
        <img src="../../assets/images/icon-increment-quantity.svg" alt="">
    </div>
</template>

<script>
    export default{
        nome: 'BotaoAdicionar',
        components: {

        }
    }
</script>

<style lang="scss" scoped>
@import './_BotaoAdicionar'
</style>