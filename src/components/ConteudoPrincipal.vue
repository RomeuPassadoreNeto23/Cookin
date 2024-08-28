<script lang="ts">

import SelecionarIngredientes from './SelecionarIngredientes.vue';
import SuaLista from './SuaLista.vue';
import Tag from './Tag.vue';
import BuscarReceitas  from './BuscarReceitas.vue';
import Rodape from './Rodape.vue';

export default {
    data() {
        return {
            ingredientes: [] as string[]

        };
    },
    components: { SelecionarIngredientes, Tag, SuaLista,BuscarReceitas,Rodape },
    methods: {
        adicionarIngrediente(incrediente: string) {
            this.ingredientes.push(incrediente)

        },
        removerIgrediente(incrediente: number) {
            console.log("ingrediente", incrediente)
            this.ingredientes.splice(incrediente, 1)


        }

    }

}

</script>
<template>

    <main class="conteudo-principal">
        <SuaLista :ingredientes="ingredientes" />
        <SelecionarIngredientes @adicionar-ingrediente="adicionarIngrediente"
            @remover-ingrediente="removerIgrediente" />
        <BuscarReceitas />  
    </main>
    <Rodape />
</template>
<style scoped>
.conteudo-principal {
    padding: 6.5rem 7.5rem;
    border-radius: 3.75rem 3.75rem 0rem 0rem;
    background: var(--creme, #FFFAF3);
    color: var(--cinza, #444);

    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 5rem;
}

@media only screen and (max-width: 1300px) {
    .conteudo-principal {
        padding: 5rem 3.75rem;
        gap: 3.5rem;
    }
}

@media only screen and (max-width: 767px) {
    .conteudo-principal {
        padding: 4rem 1.5rem;
        gap: 4rem;
    }
}
</style>