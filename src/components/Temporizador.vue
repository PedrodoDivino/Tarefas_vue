<template>
        <div
          class="is-flex is-align-itens-center is-justify-content-space-bettween"
        >
          <Cronometro :tempoEmSegundo="tempoEmSegundo" />

          <button class="button" @click="iniciarContagem" :disabled="CronometroRodando">
            <span class="icon">
              <i class="fas fa-play"></i>
            </span>
            <span>play</span>
          </button>
          <button class="button" @click="finalizarContagem" :disabled="!CronometroRodando">
            <span class="icon">
              <i class="fas fa-stop"></i>
            </span>
            <span>stop</span>
          </button>
        </div>
 
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Cronometro from "./Cronometro.vue";

export default defineComponent({
  name: "Temporizador",
  emits:['aoTemporizadorFinalizado'],
  components: {
    Cronometro,
  },
  data() {
    return {
      tempoEmSegundo: 0,
      cronometro: 0,
      CronometroRodando: false,
    };
  },
  methods: {
    iniciarContagem() {
      this.CronometroRodando = true;
      this.cronometro = setInterval(() => {
        this.tempoEmSegundo += 1;
      }, 1000);
    },
    finalizarContagem() {
      this.CronometroRodando = false;
      clearInterval(this.cronometro);
      this.$emit('aoTemporizadorFinalizado',this.tempoEmSegundo)
      this.tempoEmSegundo= 0
    },
  },
});
</script>
