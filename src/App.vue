<template>
  <div id="app">
    <Header title="PROJECT: Tic-Tac-Toe" />
    <GameBoard />
    <TextPanel />
    <ControlPanel />
  </div>
</template>

<script>
import Header from "./components/Header"
import GameBoard from "./components/GameBoard"
import TextPanel from "./components/TextPanel"
import ControlPanel from "./components/ControlPanel"

export default {
  name: 'App',
  components: {
    Header,
    GameBoard,
    TextPanel,
    ControlPanel
  }
}
</script>

<style>
  body {
      font-family: 'Courier New', Courier, monospace;
  }
</style>
