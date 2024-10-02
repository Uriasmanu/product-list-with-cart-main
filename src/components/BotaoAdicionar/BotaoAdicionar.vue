<template>
    <div v-if="ativo" class="container-botao-adicionar" @click="ativarBotao">
        <img src="../../assets/images/icon-add-to-cart.svg" alt="icone de carrinho">
        <p>Adicionar</p>
    </div>
    <div v-else class="container-botao-adicionar-ativo">
        <button @click="remover">
            <img src="../../assets/images/icon-decrement-quantity.svg" alt="icone remover">
        </button>
        <p>{{ valor }}</p>
        <button @click="adicionar">
            <img src="../../assets/images/icon-increment-quantity.svg" alt="icone adicionar">
        </button>
    </div>
</template>

<script>
import { eventBus } from '@/scripts/eventBus';

export default {
    name: 'BotaoAdicionar', // Corrigi de "nome" para "name"
    props: {
        name: {
            type: String,
            required: true,
        },
        price: {
            type: Number,
            required: true,
        },
    },

    data() {
        return {
            valor: 1,
            ativo: true,
        };
    },

    methods: {
        ativarBotao() {
            this.ativo = false;
            this.emitirEventoAdicionar();
        },

        adicionar() {
            this.valor++;
            this.emitirEventoAdicionar(); // Emitir evento para adicionar
        },

        remover() {
            if (this.valor > 1) {
                this.valor--;
            }
        },

        emitirEventoAdicionar() {
            eventBus.emit('adicionarItem', {
                name: this.name,
                price: this.price,
                quantity: this.valor, // Sempre passa a quantidade atual
            });
        },

        emitirEventoRemover() {
            eventBus.emit('removerItem', this.name);
        },
    },
};
</script>

<style lang="scss" scoped>
@import './_BotaoAdicionar';
</style>
