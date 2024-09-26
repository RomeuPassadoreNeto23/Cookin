<script lang="ts">

import SelecionarIngredientes from './SelecionarIngredientes.vue';
import SuaLista from './SuaLista.vue';
import Tag from './Tag.vue';
import MostrarRrceitas from './MostrarReceitas.vue'


type Pagina = 'SelecionarIngredientes' | 'MostrarReceitas';

export default {
    data() {
        return {
            ingredientes: [] as string[],
            conteudo: 'SelecionarIngredientes' as Pagina

        };
    },
    components: { SelecionarIngredientes, Tag, SuaLista, MostrarRrceitas },
    methods: {
        adicionarIngrediente(incrediente: string) {
            this.ingredientes.push(incrediente)

        },
        removerIgrediente(incrediente: string) {
            console.log("ingrediente", incrediente)
            this.ingredientes = this.ingredientes.filter(ingredientes => incrediente != ingredientes)


        },
        nevegar(pagina: Pagina) {
            this.conteudo = pagina
        }

    },
    emits: ['removerIgrediente', 'adicionarIngrediente', 'buscarReceitas']

}

</script>
<template>

    <main class="conteudo-principal">
        <SuaLista :ingredientes="ingredientes" />
        <SelecionarIngredientes v-if="conteudo === 'SelecionarIngredientes'"
            @adicionar-ingrediente="adicionarIngrediente"
            @remover-ingrediente="removerIgrediente"
            @buscar-receitas="nevegar('MostrarReceitas')" />
        <MostrarRrceitas v-else=" conteudo ===  'MostrarReceitas'" />

    </main>

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