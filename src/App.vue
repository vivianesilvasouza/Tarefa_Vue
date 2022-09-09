<template>
  <main
    class="columns is-gapless is-multiline"
    :class="{ 'modo-escuro': modoEscuroAtivo }"
  >
    <div class="column is-one-quarter">
      <BarraLateral @aoTemaAlterado="trocarTema" />
    </div>
    <div class="column is-three-quarter conteudo">
      <FormularioTarefa @aoSalvarTarefa="salvarTarefa" />
      <div class="lista">
        <TarefaDaTarefa
          v-for="(tarefa, index) in tarefas"
          :key="index"
          :tarefa="tarefa"
        />
        <BoxDaTarefa v-if="listaEstaVazia"
          >Você não possui nem uma tarefa registrada!<br />
          Vamos fazer?</BoxDaTarefa
        >
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import BarraLateral from "./components/BarraLateral.vue";
import BoxDaTarefa from "./components/BoxDaTarefa.vue";
import FormularioTarefa from "./components/FormularioTarefa.vue";
import TarefaDaTarefa from "./components/TarefaDaTarefa.vue";
import ITarefa from "./interfaces/ITarefa";

export default defineComponent({
  name: "App",
  components: {
    BarraLateral,
    FormularioTarefa,
    TarefaDaTarefa,
    BoxDaTarefa,
  },

  data() {
    return {
      tarefas: [] as ITarefa[],
      modoEscuroAtivo: false,
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
    trocarTema(modoEscuroAtivo: boolean) {
      this.modoEscuroAtivo = modoEscuroAtivo;
    },
  },
});
</script>

<style>
.lista {
  padding: 1.25rem;
}

main {
  --bg-primario: #fff;
  --bg-texto-primario: #000;
}
main.modo-escuro {
  --bg-primario: #3e3042;
  --bg-texto-primario: #fd0094;
}
.conteudo {
  background-color: var(--bg-primario);
}
</style>
