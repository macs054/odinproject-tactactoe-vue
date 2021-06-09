<template>
  <div class="game-board">
    <Tile id="0" />
    <Tile id="1" />
    <Tile id="2" />
    <Tile id="3" />
    <Tile id="4" />
    <Tile id="5" />
    <Tile id="6" />
    <Tile id="7" />
    <Tile id="8" />
  </div>
</template>

<script>
import Tile from "./Tile.vue";

export default {
  name: "GameBoard",
  components: {
    Tile,
  },
};
</script>

<style scoped>
.game-board {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-auto-rows: minmax(50px, auto);
  width: 300px;
  height: 300px;
  font-size: 40px;
  margin: 0 auto;
}
</style>