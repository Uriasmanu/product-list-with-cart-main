<template>
  <div class="inicial-page">
    <div class="alimentos">
      <h1>Sobremesas</h1>
      <div class="pratos">
        <CardAlimento
          v-for="(item, index) in sobremesas"
          :key="index"
          :name="item.name"
          :category="item.category"
          :preco="item.price"
          :img="item.img"
        />
    </div>
    </div>
    <div class="carrinho">
      <CarrinhoCompras/>
    </div>
  </div>
</template>

<script>
import CardAlimento from '@/components/CardAlimento/CardAlimento.vue';
import CarrinhoCompras from '@/components/CarrinhoCompras/CarrinhoCompras.vue';
import sobremesasData from '@/Json/sobremesas.json'

export default {
  name: 'InicialPage',
  components: {
    CarrinhoCompras,
    CardAlimento
  },
  data(){
    return {
      sobremesas: sobremesasData
    }
  }

}
</script>

<style lang="scss" scoped>
@import './_inicialpage.scss'; // Importando todos os estilos do SCSS</style>

