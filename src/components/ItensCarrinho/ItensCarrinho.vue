<template>
    <div class="container-itens">
        <div class="row">
            <p class="nome">{{ nomeSobremesa }}</p>
            <div class="valor">
                <p>{{ quantidade }}x</p>
                <p>@ {{ valorInicial.toFixed(2) }}</p>
                <p>{{ valorFinal }}</p>
            </div>
        </div>
        <button>
            <img src="../../assets/images/icon-remove-item.svg" alt="icone remover">
        </button>
    </div>
</template>

<script>
export default {
    nome: "ItensCarrinho",
    props: {
        nomeSobremesa: {
            type: String,
            required: true,
        },
        quantidade: {
            type: Number,
            required: true,
        },
        valorInicial: {
            type: String,
            required: true,
        },
        valorFinal: {
            type: String,
            required: true,
        },
    }
}

</script>

<style lang="scss" scoped>
@import './_ItensCarrinho';
</style>