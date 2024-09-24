<script lang="ts">
import { obterReceitas } from '@/http';
import type IReceiras from '@/interfaces/IReceitas';
export default {
    data() {

        return {
            receitas: [] as IReceiras[]
        }


    },
    async created() {
        this.receitas = await obterReceitas();

    },
}


</script>
<template>
    <main class="conteudo-receita">

    </main>
</template>

