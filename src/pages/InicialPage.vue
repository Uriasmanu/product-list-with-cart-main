<template>
  <div class="inicial-page">
    <div class="alimentos">
      <h1>Sobremesas</h1>
      <BotaoAdicionar></BotaoAdicionar>
    </div>
    <div class="carrinho">
      <CarrinhoCompras></CarrinhoCompras>
    </div>
  </div>
</template>

<script>
import BotaoAdicionar from '@/components/BotaoAdicionar/BotaoAdicionar.vue';
import CarrinhoCompras from '@/components/CarrinhoCompras/CarrinhoCompras.vue';

export default {
  name: 'InicialPage',
  components: {
    CarrinhoCompras,
    BotaoAdicionar
  }
}
</script>

<style lang="scss" scoped>
@import './_inicialpage.scss'; // Importando todos os estilos do SCSS</style>

