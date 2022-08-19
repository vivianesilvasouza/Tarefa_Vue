<template>
  <header>
    <h1>
      <img src="../assets/logo_tarefa.png" alt="logo da taefa" />
    </h1>
  </header>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "BarraLateral",
});
</script>

<style >
header {
  padding: 1rem;
  background: #0d3b66;
  width: 100%;
  height: 100vh;
}

img {
  width: 400px;
  height: 200px;
}
@media only screen and (max-width: 768px) {
  header {
    padding: 2.5rem;
    height: auto;
  }
}
</style>