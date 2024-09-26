<script lang="ts">
import { obterReceitas } from '@/http';
import type IReceiras from '@/interfaces/IReceitas';
import CardReceita from './CardReceita.vue';
export default {
    data() {

        return {
            receitas: [] as IReceiras[]
        }


    },
    async created() {
        this.receitas = await obterReceitas();

    },
    components: { CardReceita }
}


</script>
<template>
    <section class="mostrar-receita">
        <h1 class="cabecalho titulo-receita">Receitas</h1>
        <p class="resultado paragrafo-lg">Resultados encontrados: {{ receitas.length }}</p>
        <p class=" paragrafo-lg descricao">Veja as opções de receitas que encontramos com os ingredientes que você tem
            por aí!</p>
        <ul class="receita">
            <li v-for="receita in receitas" :key="receita.nome">
                <CardReceita :receitas="receita" />
            </li>
        </ul>
    </section>
</template>
<style scoped>
.mostrar-receita {
    display: flex;
    flex-direction: column;
    align-items: center;
}

.titulo-receita {
    color: var(--verde-medio, #3D6D4A);
    display: block;
    margin-bottom: 1.5rem;

}

.resultado {
    color: var(--verde-medio, #3D6D4A);

}

.descricao {
    margin-bottom: 2rem;
}

.receita {
    margin-bottom: 1rem;
    display: flex;
    justify-content: center;
    gap: 1.5rem;
    flex-wrap: wrap;
}
</style>
