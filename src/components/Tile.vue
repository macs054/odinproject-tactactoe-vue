<template>
  <div :id="id" class="btn"></div>
</template>

<script>
export default {
  name: "Tile",
  props: {
    id: Number,
  },
};
</script>

<style scoped>
div {
  border: 1px solid #ddd;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>