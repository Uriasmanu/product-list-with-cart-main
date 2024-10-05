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

export default {
  name: 'InicialPage',
  components: {
    CarrinhoCompras,
    CardAlimento,
    CardOrdenConfirmada,
  },
  data() {
    return {
      sobremesas: sobremesasData,
      showOverlay: true,

    }
  },

}
</script>

<style lang="scss" scoped>
@import './_InicialPage';
@import './_InicialPageMobile';
</style>
