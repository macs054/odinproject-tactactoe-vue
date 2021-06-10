<template>
  <div :id="id" class="btn" @click="tileClicked">{{ content }}</div>
</template>

<script>
export default {
  name: "Tile",
  props: {
    id: Number,
    content: String,
  },
  methods: {
    tileClicked() {
      if (this.content === "") {
        this.$emit("tileClicked", this.id);
      }
    },
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