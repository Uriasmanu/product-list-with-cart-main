<template>
  <div class="inicial-page">
    <div class="alimentos">
      <h1>Sobremesas</h1>
      <div class="pratos">
        <CardAlimento v-for="(item, index) in sobremesas" :key="index" :name="item.name" :category="item.category"
          :preco="item.price" :img="item.img" />
      </div>
    </div>
    <div class="carrinho">
      <CarrinhoCompras />
    </div>
    <div v-if="showOverlay" class="overlay">
      <CardOrdenConfirmada />
    </div>
  </div>
</template>

<script>
import CardAlimento from '@/components/CardAlimento/CardAlimento.vue';
import CardOrdenConfirmada from '@/components/CardOrdenConfirmada/CardOrdenConfirmada.vue';
import CarrinhoCompras from '@/components/CarrinhoCompras/CarrinhoCompras.vue';
import sobremesasData from '@/Json/sobremesas.json'
import { eventBus } from '@/scripts/eventBus';

export default {
  name: 'InicialPage',
  components: {
    CarrinhoCompras,
    CardAlimento,
    CardOrdenConfirmada,
  },
  created() {
    // Escutando o evento 'pedidoConfirmado'
    eventBus.on('pedidoConfirmado', this.exibirOverlay);
  },
  data() {
    return {
      sobremesas: sobremesasData,
      showOverlay: false,

    }
  },
  methods: {
    exibirOverlay() {
      this.showOverlay = true; // Atualiza o estado para mostrar a overlay
    },
  },
  beforeUnmount() {
    eventBus.off('pedidoConfirmado', this.exibirOverlay); // Limpa o listener ao destruir o componente
  },

}
</script>

<style lang="scss" scoped>
@import './_InicialPage';
@import './_InicialPageMobile';
</style>
