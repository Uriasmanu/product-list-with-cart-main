<template>
    <div class="ItensDoPedidoFinal">
        <img :src="require(`@/assets/images/${img}-thumbnail`)" :alt="name">
        <div>
            <p class="nome">{{ nomeSobremesa }}</p>
            <div class="valor">
                <p>{{ quantidade }}x</p>
                <p>@ {{ valorInicial.toFixed(2) }}</p>
                <p>{{ valorFinal }}</p>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'ItensDoPedidoFinal'
    }
</script>

<style lang="scss" scoped>
    @import './ItensDoPedidoFinal'
</style>
 
