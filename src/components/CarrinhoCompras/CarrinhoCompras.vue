<template>
    <div class="container-carrinho-itens"  v-if="carrinho.length > 0">

        <h3>Seu Carrinho({{ quantidadeItens }})</h3>
        <div class="infos">
            <ItensCarrinho 
                v-for="(item, index) in itensCarrinho"
                :key="index"
                :nomeSobremesa = "item.name"
                :quantidade = "item.quantidade"
                :valorInicial = "item.price"
                :valorFinal = "(item.price * item.quantidade).toFixed(2)"
            />
        </div>
    </div>

    <div class="container-carrinho"  v-else>

        <h3>Seu Carrinho(0)</h3>
        <div class="infos">
            <img src="../../assets/images/illustration-empty-cart.svg" alt="">
            <p>Seus itens adicionados aparecerão aqui</p>
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

    data() {
        return {
            quantidadeItens: 0,
            carrinho: [],
        }
    },

    methods: {
        adicionarAoCarrinho(item){
            const itemExiste = this.itensCarrinho.find(i => i.name === item.name);
            if(itemExiste){
                itemExiste.quantidade ++;
            }else{
                this.itensCarrinho.push({...item, quantidade: 1});
            }
            this.quantidadeItens++;
        }

    },

}
</script>

<style lang="scss" scoped>
@import './_CarrinhoCompras'
</style>