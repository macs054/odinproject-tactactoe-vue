<template>
  <div id="app">
    <Header :title="title" />
    <GameBoard />
  </div>
</template>

<script>
import Header from "./components/Header";
import GameBoard from "./components/GameBoard";

export default {
  name: "App",
  components: {
    Header,
    GameBoard,
  },
  data() {
    return {
      title: "PROJECT: Tic-Tac-Toe",
    };
  },
};
</script>

<style>
body {
  font-family: "Courier New", Courier, monospace;
}
</style>
