<template>
  <div class="flex bg-gray-100 h-screen">
    <div class="flex-1 text-gray-700 bg-gray-200 px-4 m-2">
      <Card />
    </div>
    <div class="flex-1 text-gray-700 bg-gray-200 px-4 m-2">
      <div class="bg-blue-200">1</div>
    </div>
    <div class="flex-1 text-gray-700 bg-gray-200 px-4 m-2">
      <div class="bg-blue-200">1</div>
    </div>
  </div>
</template>

<script>
import Card from "../Card/index.vue";

export default {
  name: "Canvas",
  components: {
    Card,
  },
};
</script>
