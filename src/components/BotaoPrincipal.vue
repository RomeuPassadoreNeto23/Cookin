<script lang="ts">
export default {
    props: {
        texto: { type: String, required: true }

    },

}
</script>
<template>
    <button class="botao">{{ texto }}</button>
</template>
<style scoped>
.botao {

    width: 312px;
    height: 56px;
    padding: 8px 16px 8px 16px;
    border-radius: 32px;
    background: #F0633C;
    color: #FEF7EC;
    cursor: pointer;
    font-weight: 700;
    font-size: 22px;
    box-shadow: 4px 4px 15px 0px #FF734C40;



}

.botao:hover {
    filter: brightness(90%);
}
</style>