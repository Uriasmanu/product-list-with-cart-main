<template>
  <div class="inicial-page">
    <div class="alimentos">
      <h1>Desserts</h1>
    </div>
    <div class="carrinho">
      <CarrinhoCompras></CarrinhoCompras>
    </div>
  </div>
</template>

<script>
import CarrinhoCompras from '@/components/CarrinhoCompras/CarrinhoCompras.vue';

export default {
  name: 'InicialPage',
  components: {
    CarrinhoCompras
  }
}
</script>

<style lang="scss" scoped>
@import './_inicialpage.scss'; // Importando todos os estilos do SCSS</style>

