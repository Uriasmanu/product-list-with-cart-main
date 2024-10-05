<template>
    <div class="container-carrinho-itens" v-if="carrinho.length > 0">

        <h3>Seu Carrinho({{ quantidadeItens }})</h3>
        <div class="infos">
            <ItensCarrinho v-for="(item, index) in carrinho" :key="index" :nomeSobremesa="item.name"
                :quantidade="item.quantidade" :valorInicial="item.price"
                :valorFinal="(item.price * item.quantidade).toFixed(2)" @removerItem="removerItem(item.name)"
                @subtrairItem="subtrairItem(item.name)" />
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
            const total = this.carrinho.reduce((acc, item) => acc + (item.price * item.quantidade), 0).toFixed(2);
            return total;
        }
    },
    created() {
        eventBus.on('adicionarItem', this.adicionarItem); // Escuta o evento adicionarItem
        eventBus.on('removerItem', this.removerItem);
        eventBus.on('subtrairItem', this.subtrairItem);
        eventBus.on('pedidoConfirmado', this.confirmarPedido);
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
                const itemRemovido = this.carrinho[index]; // Guarde o item para log
                this.carrinho.splice(index, 1);
                this.quantidadeItens = this.carrinho.reduce((acc, i) => acc + i.quantidade, 0);

                // Emitir evento para notificar que um item foi removido
                eventBus.emit('itemRemovido', itemRemovido.name); // Notifica o item removido
            }
        },

        subtrairItem(nomeSobremesa) {
            const existingItem = this.carrinho.find(i => i.name === nomeSobremesa); // Busca pelo nome da sobremesa
            if (existingItem) {
                existingItem.quantidade--; // Diminui a quantidade do item


                if (existingItem.quantidade <= 0) {
                    this.carrinho = this.carrinho.filter(i => i.name !== existingItem.name); // Remove o item do carrinho
                }
            }

            this.atualizarQuantidadeTotal(); // Atualiza a quantidade total após subtração
        },

        atualizarQuantidadeTotal() {
            this.quantidadeItens = this.carrinho.reduce((acc, i) => acc + i.quantidade, 0); // Atualiza a quantidade total
        },
        confirmarPedido() {
            // Armazena o conteúdo atual do carrinho no localStorage
            localStorage.setItem('carrinhoConfirmado', JSON.stringify(this.carrinho));
            // Emite para o componente pai que o pedido foi confirmado
            this.$emit('pedidoConfirmado');
        },



    },

    beforeUnmount() {
        eventBus.off('adicionarItem', this.adicionarItem); // Limpa o listener ao destruir o componente
        eventBus.off('removerItem', this.removerItem);
        eventBus.off('subtrairItem', this.subtrairItem);
        eventBus.off('pedidoConfirmado', this.confirmarPedido);
    },

}
</script>

<style lang="scss" scoped>
@import './_CarrinhoCompras'
</style>
