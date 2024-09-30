<template>
    <div class="container-alimento">
        <div>
            <img src="" alt="">
            <BotaoAdicionar></BotaoAdicionar>
        </div>
        <p></p>
        <h4></h4>
        <p></p>
    </div>
</template>

<script>
import BotaoAdicionar from '../BotaoAdicionar/BotaoAdicionar.vue';


export default {
    name: 'CardAlimento',
    components: {
        BotaoAdicionar
    }

}
</script>

<style lang="scss" scoped>
@import './_CardAlimento'
</style>