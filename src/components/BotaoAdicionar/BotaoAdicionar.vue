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
export default {
    nome: 'BotaoAdicionar',
    data() {
        return {
            valor: 1,
            ativo: true
        }
    },

    methods: {
        ativarBotao() {
            this.ativo = false
        },

        adicionar() {
            this.valor++;
        },

        remover() {
            if (this.valor > 1) {
                this.valor--;

            } else {
                this.ativo = true;
            }
        }

    }
}



</script>

<style lang="scss" scoped>
@import './_BotaoAdicionar'
</style>