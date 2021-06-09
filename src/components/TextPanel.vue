<template>
  <div class="text-panel">{{ content }}</div>
</template>

<script>
export default {
  name: "TextPanel",
  data() {
    return {
      content: "Player Turn",
    };
  },
};
</script>

<style scoped>
.text-panel {
  text-align: center;
  margin: 1.5em;
}
</style>