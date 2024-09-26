<script lang="ts">
import type IReceiras from '@/interfaces/IReceitas';
import type { PropType } from 'vue';
export default {
    props: {
        receitas:{type: Object as PropType<IReceiras>, required: true }

    }
}

</script>
<template>
    <article class="card-receita">
        <img :src="`/public/imagens/receitas/${receitas.imagem}`" >
        <h1><strong>{{ receitas.nome }}</strong></h1>
    </article>

</template>