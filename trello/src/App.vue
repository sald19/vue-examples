<template>
  <div class="lg:container mx-auto">
    <Canvas />
  </div>
</template>

<script>
import Canvas from "./components/Canvas/index.vue";

export default {
  name: "App",
  components: {
    Canvas,
  },
};
</script>
