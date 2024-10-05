<template>
    <button @click="finaliazarPedido" class="BotaoFinalizar">iniciar novo pedido</button>
</template>

<script>
import { eventBus } from '@/scripts/eventBus';

    export default{
        name: 'BotaoFinalizar',
        methods: {
            finaliazarPedido(){
                eventBus.emit('finaliazarPedido');
                localStorage.removeItem('carrinhoConfirmado');

            }
        }
    }
</script>

<style lang="scss" scoped>
@import './BotaoFinalizar'
</style>
