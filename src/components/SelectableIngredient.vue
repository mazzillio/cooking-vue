<script lang="ts">
import { inject, type Ref } from 'vue';
import Tag from './Tag.vue';
export default {
  components:{
    Tag
  },
  props:{
    ingrediente:{ type: String, required: true}
  },
  data(){
    return {
      isSelect: false,
      ingredientes: inject('ingredientes') as Ref<string[]>
    }
  },
  methods:{
    handleIsSelect(){
      this.isSelect = !this.isSelect
      if(this.isSelect) {
        this.ingredientes.push(this.ingrediente)
      } else {
       this.ingredientes = this.ingredientes.filter((i) => i !== this.ingrediente)
      }
    }
  },
  //emits:['adicionarIngrediente','removerIngrediente']
}

</script>
<template>
  <button 
    class="ingrediente" 
    @click="handleIsSelect" 
    :aria-pressed="isSelect"
  >
    <Tag :text="ingrediente" :ativa="isSelect"/>
  </button>
</template>
<style scoped>
  .ingrediente{
    cursor: pointer;
  }
</style>