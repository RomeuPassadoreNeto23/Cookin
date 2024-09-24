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
    emits: ['adicionarIngrediente', 'removerIngrediente']
    ,
    methods: {
        aoClicar() {
            this.selecionado = !this.selecionado
            if (this.selecionado) {
                this.$emit('adicionarIngrediente', this.ingredientes);
            } else {
                this.$emit('removerIngrediente', this.ingredientes);

            }


        }
    },
    
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
