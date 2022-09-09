<template>
  <section>
    <strong class="display"> {{ tempoDecorrido }}</strong>
  </section>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "CronometroTarefa",
  props: {
    tempoemSegundos: {
      type: Number,
      default: 0,
    },
  },
  computed: {
    tempoDecorrido(): string {
      return new Date(this.tempoemSegundos * 1000).toISOString().substr(11, 8);
    },
  },
});
</script>

<style scoped>
.display {
  color: var(--bg-texto-primario);
}
</style>
