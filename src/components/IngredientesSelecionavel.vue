<script lang="ts">
import Tag from './Tag.vue';

export default {
    components: { Tag },
    props: {
        ingredientes: { type: String, required: true }

    },
    data() {
        return {
            selecionado: false
        }

    },
    methods: {
        aoClicar() {
            this.selecionado = !this.selecionado
            if( this.selecionado){
                this.$emit('adicionarIngrediente', this.ingredientes);
            }


        }
    },
    emits:['adicionarIngrediente']
}

</script>
<template>
    <button class="ingrediente" @:click="aoClicar" :aria-pressed="selecionado">
        <Tag :texto="ingredientes" :ativa="selecionado" />
    </button>
</template>
<style scoped>
.ingrediente {
    cursor: pointer;
}
</style>
