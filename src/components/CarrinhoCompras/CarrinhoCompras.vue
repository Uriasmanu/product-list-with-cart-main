<template>
    <div class="container-carrinho-itens" v-if="carrinho.length > 0">

        <h3>Seu Carrinho({{ quantidadeItens }})</h3>
        <div class="infos">
            <ItensCarrinho v-for="(item, index) in carrinho" :key="index" :nomeSobremesa="item.name"
                :quantidade="item.quantidade" :valorInicial="item.price"
                :valorFinal="(item.price * item.quantidade).toFixed(2)" @removerItem="removerItem(item.name)" />

        </div>
        <div class="total">
            <p>Valor Total</p>
            <p>R$ {{ valorTotal }}</p>
        </div>
        <DeliveryComponent />
        <BotaoConfirmaPedido />
    </div>

    <div class="container-carrinho" v-else>

        <h3>Seu Carrinho(0)</h3>
        <div class="infos">
            <img src="../../assets/images/illustration-empty-cart.svg" alt="">
            <p>Seus itens adicionados aparecerão aqui</p>
        </div>
    </div>
</template>

<script>
import { eventBus } from '@/scripts/eventBus';
import ItensCarrinho from '../ItensCarrinho/ItensCarrinho.vue';
import DeliveryComponent from '../Delivery/DeliveryComponent.vue';
import BotaoConfirmaPedido from '../BotaoConfirmaPedido/BotaoConfirmaPedido.vue';


export default {
    name: 'CarrinhoCompras',
    components: {
        ItensCarrinho,
        DeliveryComponent,
        BotaoConfirmaPedido,
    },

    data() {
        return {
            quantidadeItens: 0,
            carrinho: [],
        }
    },
    computed: {
        valorTotal() {
            return this.carrinho.reduce((acc, item) => acc + (item.price * item.quantidade), 0).toFixed(2);
        }
    },
    created() {
        eventBus.on('adicionarItem', this.adicionarItem); // Escuta o evento adicionarItem
        eventBus.on('removerItem', this.removerItem);
    },

    methods: {
        adicionarItem(item) {
            const existingItem = this.carrinho.find(i => i.name === item.name);
            if (existingItem) {
                existingItem.quantidade++; // Aumenta a quantidade se o item já estiver no carrinho
            } else {
                this.carrinho.push({ ...item, quantidade: 1 }); // Adiciona o item ao carrinho
            }
            this.quantidadeItens = this.carrinho.reduce((acc, i) => acc + i.quantidade, 0); // Atualiza a quantidade total
        },

        removerItem(nomeSobremesa) {
            const index = this.carrinho.findIndex(i => i.name === nomeSobremesa);
            if (index !== -1) {
                this.carrinho.splice(index, 1);
            }

            this.quantidadeItens = this.carrinho.reduce((acc, i) => acc + i.quantidade, 0);
        }
    },

    beforeUnmount() {
        eventBus.off('adicionarItem', this.adicionarItem); // Limpa o listener ao destruir o componente
        eventBus.off('removerItem', this.removerItem);
    },

}
</script>

<style lang="scss" scoped>
@import './_CarrinhoCompras'
</style>