<script lang="ts">
import { obterReceitas } from '@/http';
import type { PropType } from 'vue';
import type IReceiras from '@/interfaces/IReceitas';
import CardReceita from './CardReceita.vue';
import BotaoPrincipal from './BotaoPrincipal.vue';
import { itensDeLista1EstaoEmLista2 } from '@/operacoes/listas';



export default {
    props: {
        ingrediente: { type: Array as PropType<string[]>, required: true }
    },
    data() {
        return {
            receitasEncontradas : [] as IReceiras[],

        };
    },
    
    watch: {
        ingrediente: {
            async handler(novaListaIngredientes) {
                const receitas = await obterReceitas();
                this.receitasEncontradas = receitas.filter((receita) => {
                    const possoFazerReceita = itensDeLista1EstaoEmLista2(receita.ingredientes,
                        novaListaIngredientes);
                    return possoFazerReceita;
                });
            },
            immediate: true
        }, 
    },

    components: { CardReceita, BotaoPrincipal },
    emits: ['editarReceita']
}


</script>
<template>

    <section class="mostrar-receita">

        <h1 class="cabecalho titulo-receita">Receitas</h1>
        <p class="resultado paragrafo-lg">Resultados encontrados: {{ receitasEncontradas.length }}</p>
        <p v-if="receitasEncontradas.length" class=" paragrafo-lg descricao">Veja as opções de receitas que encontramos
            com os ingredientes que você tem
            por aí!</p>
        <p v-else class=" paragrafo-lg descricao">Ops, não encontramos resultados para sua combinação. Vamos tentar de
            novo?</p>

        <ul class="receita" v-if="receitasEncontradas.length">
            <li v-for="receita in receitasEncontradas" :key="receita.nome">
                <CardReceita :receitas="receita" />
            </li>
        </ul>
        <img v-else src="../assets/imagens/sem-receitas.png" />

        <BotaoPrincipal texto="Editar lista" @click="$emit('editarReceita')" />

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
    width: 1200px;
}
</style>
