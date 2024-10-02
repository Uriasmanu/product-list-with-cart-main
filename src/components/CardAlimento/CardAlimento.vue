<template>
    <div class="container-alimento">
        <div>
            <img :src="require(`@/assets/images/${img}.jpg`)" :alt="name">
            <div class="adicionar">
                <BotaoAdicionar :name="name" :price="preco" />
            </div>

        </div>
        <p class="categoria">{{ category }}</p>
        <h4>{{ name }}</h4>
        <p class="preco">R$ {{ preco.toFixed(2) }}</p>
    </div>
</template>

<script>
import BotaoAdicionar from '../BotaoAdicionar/BotaoAdicionar.vue';


export default {
    name: 'CardAlimento',
    components: {
        BotaoAdicionar
    },

    props: {
        name: {
            type: String,
            required: true,
        },
        category: {
            type: String,
            required: true,
        },
        preco: {
            type: Number,
            required: true,
        },
        img: {
            type: String,
            required: true,
        },
    }
}
</script>

<style lang="scss" scoped>
@import './_CardAlimento';
@import './_CardAlimentoMobile'
</style>