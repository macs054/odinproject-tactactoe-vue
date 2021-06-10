<template>
  <div class="controls">
    <button class="reset" @click="reset()">{{ btnLabel }}</button>
  </div>
</template>

<script>
export default {
  name: "ControlPanel",
  methods: {
    reset() {
      this.$emit("reset", "Reset");
    },
  },
  props: {
    btnLabel: String,
  },
};
</script>

<style scoped>
.controls {
  display: flex;
  justify-content: center;
}

.reset {
  text-align: center;
}
</style>