<template>
    <div class="container-ordem">
        <div class="cabecalho">
            <img src="../../assets//images/icon-order-confirmed.svg" alt="">
            <h4>Pedido Confirmado</h4>
            <p>Esperamos que você aproveite sua comida!</p>
        </div>
        <div class="container-itens">

            <div class="total">
            <p>Valor Total</p>
            <p>R$ {{ valorTotal }}</p>
        </div>
        </div>
        
        <BotaoFinalizar />
    </div>
</template>

<script>
import BotaoFinalizar from '../BotaoFinalizar/BotaoFinalizar.vue';

export default {
    name: 'CardOrdenConfirmada',

    components: {
        BotaoFinalizar,
    },
}
</script>

<style lang="scss" scoped>
@import './CardOrdenConfirmada'
</style>
