<script lang="ts">
import type IReceiras from '@/interfaces/IReceitas';
import type { PropType } from 'vue';
export default {
    props: {
        receitas: { type: Object as PropType<IReceiras>, required: true }

    }
}

</script>
<template>
    <article class="card-receita">
        <img :src="`/public/imagens/receitas/${receitas.imagem}`">
        <h1>{{ receitas.nome }}</h1>
    </article>

</template>
<style scoped>
.card-receita {
    display: flex;
    justify-content:flex-start;
    align-items:center;
    flex-direction: column;
    width:282px;
    min-height:246px; 
    max-width: 312px;
    border-radius: 16px;
    box-shadow: 4px 4px 12px 0px rgba(68, 68, 68, 0.08);
    background-color: rgba(255, 255, 255, 1);
}
.card-receita img {
    width: 282px;
    height: 150px;
    border-radius: 16px 16px 0px 0px;
    margin-bottom: 30px;
 
    

}
.card-receita h1{
    width:282px;
    height:22px;
    font-size: 18px;
    font-weight: 700;
    font-family:Paragraph Bold, sans-serif ;
    text-align: center;

}
</style>