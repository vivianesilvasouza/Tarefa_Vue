<template>
  <div class="box formulario">
    <div class="columns">
      <div
        class="column is-8"
        role="form"
        aria-label="Formulário para criação de uma nova tarefa"
      >
        <input
          type="text"
          class="input"
          placeholder="Qual tarefa você deseja iniciar?"
          v-model="descricao"
        />
      </div>
      <div class="column">
        <TempoTarefa @aoTemporizadorFinalizado="finalizaraTarefa" />
      </div>
    </div>
  </div>
</template>

<script lang="ts" >
import { defineComponent } from "vue";
import TempoTarefa from "./TempoTarefa.vue";

export default defineComponent({
  name: "FormularioTarefa",
  emits: ["aoSalvarTarefa"],
  components: {
    TempoTarefa,
  },
  data() {
    return {
      descricao: "",
    };
  },
  methods: {
    finalizaraTarefa(tempoDecorrido: number): void {
      this.$emit("aoSalvarTarefa", {
        duracaoEmSegundos: tempoDecorrido,
        descricao: this.descricao,
      });
      this.descricao = "";
    },
  },
});
</script>

<style>
.formulario {
  color: var(--bg-texto-primario);
  background-color: var(--bg-primario);
}
</style>
