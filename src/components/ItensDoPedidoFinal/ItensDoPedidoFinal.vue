<template>
    <div class="ItensDoPedidoFinal">
        <div class="container-pedido">
            <img :src="require(`@/assets/images/${img}-thumbnail.jpg`)" :alt="nameSobrenesa">
            <div class="infos">
                <p class="nome">{{ nomeSobremesa }}</p>
                <div class="valor">
                    <p>{{ quantidade }}x</p>
                    <p>@ {{ valorInicial.toFixed(2) }}</p>

                </div>

            </div>
        </div>
        <p>R$ {{ valorFinal }}</p>
    </div>
</template>

<script>
import sobremesasJson from '@/Json/sobremesas.json';

export default {
    name: 'ItensDoPedidoFinal',
    props: {
        nomeSobremesa: String,
        quantidade: Number,
        valorInicial: Number,
        valorFinal: String,
    },

    data() {
        return {
            img: '', // armazenará o nome da imagem correspondente
        };
    },

    created() {
        this.setarImagem();
    },

    methods: {
        setarImagem() {
            // Busca a sobremesa no JSON com base no nome
            const sobremesa = sobremesasJson.find(item => item.name === this.nomeSobremesa);
            if (sobremesa) {
                // Se encontrar a sobremesa, define o nome da imagem
                this.img = sobremesa.img;
            } else {
                // Se não encontrar, pode definir uma imagem padrão ou exibir um erro
                this.img = 'default-image'; // Defina a imagem padrão se necessário
            }
        },
    },
}
</script>

<style lang="scss" scoped>
@import './ItensDoPedidoFinal'
</style>
