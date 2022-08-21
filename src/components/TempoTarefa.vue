<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <CronometroTarefa :tempoemSegundos="tempoemSegundos" />
    <button class="button" @click="iniciar" :disabled="cronometroRodando">
      <span class="icon">
        <i class="fas fa-play"></i>
      </span>
      <span>play</span>
    </button>
    <button class="button" @click="finalizar" :disabled="!cronometroRodando">
      <span class="icon">
        <i class="fas fa-stop"></i>
      </span>
      <span>stop</span>
    </button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import CronometroTarefa from "./CronometroTarefa.vue";

export default defineComponent({
  name: "TempoTarefa",
  components: {
    CronometroTarefa,
  },
  data() {
    return {
      tempoemSegundos: 0,
      cronometro: 0,
      cronometroRodando: false,
    };
  },

  methods: {
    iniciar() {
      // começar a contagem
      // 1 seg = 100 ms
      this.cronometroRodando = true;
      this.cronometro = setInterval(() => {
        this.tempoemSegundos += 1;
      }, 1000);
      console.log("iniciando");
    },
    finalizar() {
      this.cronometroRodando = false;
      clearInterval(this.cronometro);
    },
  },
});
</script>