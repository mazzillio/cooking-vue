<script lang="ts">
import type { ICategorie } from '@/interfaces/ICategorie';
import type { PropType } from 'vue';
import Tag from './Tag.vue';
import SelectableIngredient from './SelectableIngredient.vue';
  export default {
    props: {
        categorie: {
            type: Object as PropType<ICategorie>,
            required: true
        }
    },
    components: { Tag, SelectableIngredient }
}
</script>
<template>
  <article class="categoria">
    <header class="categoria__cabecalho">
      <img :src="`/imagens/icones/categorias_ingredientes/${categorie.imagem}`" alt="" class="categoria__imagem">
      <h2 class="paragrafo-lg categoria__nome">
        {{ categorie.nome }}
      </h2>
    </header>
    <ul class="categoria__ingredientes">
      <li v-for="ingrediente in categorie.ingredientes" :key="ingrediente">
        <SelectableIngredient 
        :ingrediente="ingrediente" 
        />
      </li>
    </ul>
  </article>
</template>
<style scoped>
.categoria {
  width: 19.5rem;
  padding: 1rem;
  border-radius: 1rem;
  background: var(--branco, #FFF);
  box-shadow: 4px 4px 10px 0px rgba(68, 68, 68, 0.05);
  height: 100%;

  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 2rem;
}

.categoria__cabecalho {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.5rem;
}

.categoria__imagem {
  width: 3.5rem;
}

.categoria__nome {
  text-align: center;
  color: var(--verde-medio, #3D6D4A);
  font-weight: 700;
}

.categoria__ingredientes {
  display: flex;
  justify-content: center;
  gap: 0.5rem;
  flex-wrap: wrap;
}

</style>