<template>
    <div class="container-ordem">
        <div class="cabecalho">
            <img src="../../assets/images/icon-order-confirmed.svg" alt="">
            <h4>Pedido Confirmado</h4>
            <p>Esperamos que você aproveite sua comida!</p>
        </div>
        <div class="container-itens">
            <ItensDoPedidoFinal v-for="(item, index) in carrinhoConfirmado" :key="index" :nomeSobremesa="item.name"
                :quantidade="item.quantidade" :valorInicial="item.price"
                :valorFinal="(item.price * item.quantidade).toFixed(2)" />

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
import ItensDoPedidoFinal from '../ItensDoPedidoFinal/ItensDoPedidoFinal.vue';

export default {
    name: 'CardOrdenConfirmada',

    components: {
        BotaoFinalizar,
        ItensDoPedidoFinal,
    },

    data() {
        return {
            carrinhoConfirmado: [], // Inicializa vazio
        }
    },

    computed: {
        valorTotal() {
            return this.carrinhoConfirmado.reduce((acc, item) => acc + (item.price * item.quantidade), 0).toFixed(2);
        }
    },

    created() {
        // Verifica se há dados no localStorage ao criar o componente
        const carrinho = localStorage.getItem('carrinhoConfirmado');
        if (carrinho) {
            this.carrinhoConfirmado = JSON.parse(carrinho);
        }
    },
}
</script>

<style lang="scss" scoped>
@import './CardOrdenConfirmada';
</style>
