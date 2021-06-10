<template>
  <div class="text-panel">{{ content }}</div>
</template>

<script>
export default {
  name: "TextPanel",
  props: {
    content: String,
  },
};
</script>

<style scoped>
.text-panel {
  text-align: center;
  margin: 1.5em;
}
</style>