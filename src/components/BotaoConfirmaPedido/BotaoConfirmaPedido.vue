<template>
    <button @click="confirmarPedido" class="conteiner-BotaoConfirmaPedido">
        Confirma Pedido
    </button>
</template>

<script>
import { eventBus } from '@/scripts/eventBus';



export default {
    name: 'BotaoConfirmaPedido',
    methods: {
        confirmarPedido() {
            eventBus.emit('pedidoConfirmado');
        }
    }
}
</script>

<style lang="scss" scoped>
@import "./_BotaoConfirmaPedido.scss"
</style>