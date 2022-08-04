<template>
<Box/>
    <div class="collumns">
      <div class="column is-7">{{tarefa.descricao || 'Tarefa sem Descrição'}}</div>
      <div class="collumn">
        <Cronometro :tempoEmSegundo="tarefa.dururacaoEmSegundos" />
      </div>
    </div>
<Box/>
</template>
<script lang="ts">
import { defineComponent, PropType } from "vue";
import Cronometro from "./Cronometro.vue";
import Itarefa from "./interface/ITarefa";
import Box from "../components/Box.vue";


export default defineComponent({
  name: "Tarefa",
  components: {
    Cronometro,
    Box
},
  props: {
    tarefa:{
      type: Object as  PropType<Itarefa>,
      required: true,
  },
}});
</script>

<style scoped> 

</style>

