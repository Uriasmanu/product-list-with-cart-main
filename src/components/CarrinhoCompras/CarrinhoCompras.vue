<template>
    <div class="container-carrinho">
        <h3>Seu Carrinho(0)</h3>
        <div class="infos">
            <img src="../../assets/images/illustration-empty-cart.svg" alt="">
            <p>Seus itens adicionados aparecerão aqui</p>
        </div>
    </div>

    <div class="container-carrinho-itens">
        <h3>Seu Carrinho({{ quantidadeItens }})</h3>
        <div class="infos">
            <ItensCarrinho />
        </div>
    </div>
</template>

<script>
import ItensCarrinho from '../ItensCarrinho/ItensCarrinho.vue';

export default {
    name: 'CarrinhoCompras',
    components: {
        ItensCarrinho
    },

    data(){
        return {
            quantidadeItens: 0
        }
    }
}
</script>

<style lang="scss" scoped>
@import './_CarrinhoCompras'
</style>