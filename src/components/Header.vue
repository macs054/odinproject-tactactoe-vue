<template>
  <div>
    <header>{{ title }}</header>
  </div>
</template>

<script>
export default {
  name: "Header",
  props: {
    title: String,
  },
};
</script>

<style scoped>
header {
  text-align: center;
  color: #ce973e;
  font-weight: bold;
  font-size: 35px;
  padding: 40px 0px 40px 0px;
  border-bottom: 2px solid silver;
  background-color: white;
  margin-bottom: 2em;
}
</style>