<template>
  <main class="columns is-gapless is-multiline" :class="{ 'dark-mode' : darkThemeActive }" >
    <div class="column is-one-quarter">
      <BarraLateral @aoChangedTheme="changeTheme" />
    </div>
    <div class="column is-three-quarter content">
      <Formulario @aoSalvarTarefa="salvarTarefa" />
      <div class="lista">
        <Tarefa
          v-for="(tarefa, index) in tarefas"
          :key="index"
          :tarefa="tarefa"
        />
      </div>

      <Box v-if="listaEstaVazia"> Você não está muito produtivo hoje :() </Box>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import BarraLateral from "./components/BarraLateral.vue";
import Formulario from "./components/Formulario.vue";
import ITarefa from "./components/interface/ITarefa";
import Tarefa from "./components/Tarefa.vue";
import Box from "./components/Box.vue";

export default defineComponent({
  name: "App",
  components: {
    BarraLateral,
    Formulario,
    Tarefa,
    Box,
  },
  data() {
    return {
      tarefas: [] as ITarefa[],
      darkThemeActive: false,
    };
  },
  computed: {
    listaEstaVazia(): boolean {
      return this.tarefas.length === 0;
    },
  },
  methods: {
    salvarTarefa(tarefa: ITarefa) {
      this.tarefas.push(tarefa);
    },
    changeTheme (darkThemeActive :boolean){
      this.darkThemeActive = darkThemeActive;
    },
  },
});
</script>
<style>
main {
  --bg-primary: #fff;
  --text-primary: #000;
}

main.dark-mode {
  --bg-primary: rgb(12, 3, 49);
  --text-primary: #fff;
}
.lista {
  padding: 1.25rem;
}
.content{
  background-color: var(--bg-primary)

}
.is-flex {
  display: flex;
  justify-content: space-between;
}
</style>
