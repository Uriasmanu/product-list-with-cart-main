<template>
    <div v-if="ativo" class="container-botao-adicionar" @click="ativarBotao">
        <img src="../../assets/images/icon-add-to-cart.svg" alt="icone de carrinho">
        <p>Adicionar</p>
    </div>
    <div v-else class="container-botao-adicionar-ativo">
        <button @click="remover"><img src="../../assets/images/icon-decrement-quantity.svg"
                alt="icone remover"></button>
        <p>{{ valor }}</p>
        <button @click="adicionar"><img src="../../assets/images/icon-increment-quantity.svg"
                alt="icone adicionar"></button>

    </div>
</template>

<script>
import { eventBus } from '@/scripts/eventBus';

export default {
    nome: 'BotaoAdicionar',
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
            ativo: true
        }
    },

    methods: {
        ativarBotao() {
            this.ativo = false

            // Exibe os dados no console
            console.log('Item Adicionado:', {
                name: this.name,
                price: this.price,
                quantity: this.valor
            });
            eventBus.emit('adicionarItem', {
                name: this.name,
                price: this.price,
                quantity: this.valor
            }

            )
        },

        adicionar() {
            this.valor++;

            // Exibe os dados no console
            console.log('Item Adicionado:', {
                name: this.name,
                price: this.price,
                quantity: this.valor
            });
            eventBus.emit('adicionarItem', {
                name: this.name,
                price: this.price,
                quantity: this.valor
            }

            )

        },

        remover() {
            if (this.valor > 1) {
                this.valor--;

            } else {
                this.ativo = true;
            }
        },

    }
}



</script>

<style lang="scss" scoped>
@import './_BotaoAdicionar'
</style>