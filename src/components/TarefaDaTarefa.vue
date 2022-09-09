<template>
  <BoxDaTarefa>
    <div class="columns">
      <div class="column is -7">
        {{ tarefa.descricao || "Tarefa sem descrição" }}
      </div>
      <div class="column">
        <CronometroTarefa :tempoemSegundos="tarefa.duracaoEmSegundos" />
      </div>
    </div>
  </BoxDaTarefa>
</template>

<script lang="ts">
import ITarefa from "@/interfaces/ITarefa";
import { defineComponent, PropType } from "vue";
import CronometroTarefa from "./CronometroTarefa.vue";
import BoxDaTarefa from "./BoxDaTarefa.vue";

export default defineComponent({
  name: "TarefaDaTarefa",
  components: { CronometroTarefa, BoxDaTarefa },
  props: {
    tarefa: {
      type: Object as PropType<ITarefa>,
      required: true,
    },
  },
});
</script>

<style scoped>
</style>


