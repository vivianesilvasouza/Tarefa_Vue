<template>
  <div class="box has-text-weight-bold"><slot></slot></div>
</template>

<script lang="ts">
import { defineComponent, PropType } from "vue";

export default defineComponent({
  name: "BoxDaTarefa",
});
</script>

<style scoped>
.box {
  background: rgb(236, 235, 235);
}
</style>