<template>
  <div class="box form">
    <div class="columns">
      <div
        class="column is-8"
        role="form"
        aria-label="formulário para criação de cada nova tarefa"
      >
        <input type="text" placeholder="qual tarefa voce deseja iniciar?"
        v-model="descricao"
        />

      </div>
      <div class="column">
        <Temporizador @aoTemporizadorFinalizado="finalizarTarefa"/>
   </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Temporizador from  '@/components/Temporizador.vue';

export default defineComponent({
  name: "Formulário",
  emits: ['aoSalvarTarefa'],
  components: {
   Temporizador
},data () {
return{
  descricao: ''
}
},
 methods: {
  finalizarTarefa(tempoDecorrido: number): void{
    this.$emit('aoSalvarTarefa',{
      dururacaoEmSegundos: tempoDecorrido,
      descricao: this.descricao
    })
   this.descricao=''
  }
}
});
</script>
<style>
.form{
  color: var(--text-primary);
  background-color:var(--bg-primary);
}
</style>
