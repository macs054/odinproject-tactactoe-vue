<template>
  <div>
    <div class="game-board">
      <Tile
        v-for="tile in boardArray"
        :key="tile.id"
        :id="tile.id"
        @tileClicked="hasWinner ? null : writeInBoard($event)"
        :content="tile.content"
      />
    </div>
    <TextPanel :content="textPanelContent" />
    <ControlPanel @reset="resetGame" :btnLabel="resetBtnLabel" />
  </div>
</template>

<script>
import Tile from "./Tile.vue";
import TextPanel from "./TextPanel";
import ControlPanel from "./ControlPanel";

export default {
  name: "GameBoard",
  components: {
    Tile,
    TextPanel,
    ControlPanel,
  },
  data() {
    return {
      boardArray: [],
      resetBtnLabel: "Reset",
      players: [
        { name: "Player 1", input: "X" },
        { name: "Player 2", input: "O" },
      ],
      currentlyPlaying: "",
      winner: "",
      textPanelContent: "",
    };
  },
  computed: {
    hasWinner() {
      return this.winner !== "";
    },
  },
  methods: {
    writeInBoard(id) {
      this.boardArray[id].content = this.currentlyPlaying.input;
      this.checkWinCondition();
      this.switchPlayer();
    },
    resetGame(resetBtnString) {
      this.clearBoardArray();
      this.winner = "";
      this.currentlyPlaying = this.players[0];
      this.resetBtnLabel = resetBtnString;
      this.setTextPanelContent();
    },
    clearBoardArray() {
      this.boardArray.map((tile) => {
        tile.content = "";
      });
    },
    switchPlayer() {
      this.currentlyPlaying === this.players[0]
        ? (this.currentlyPlaying = this.players[1])
        : (this.currentlyPlaying = this.players[0]);
      this.setTextPanelContent();
    },
    checkThreeInARow(a, b, c) {
      if (!!a || !!b || !!c) {
        return a == b && a == c;
      }
    },
    checkWinCondition() {
      if (
        this.checkThreeInARow(
          this.boardArray[0].content,
          this.boardArray[1].content,
          this.boardArray[2].content
        ) ||
        this.checkThreeInARow(
          this.boardArray[0].content,
          this.boardArray[4].content,
          this.boardArray[8].content
        ) ||
        this.checkThreeInARow(
          this.boardArray[0].content,
          this.boardArray[3].content,
          this.boardArray[6].content
        ) ||
        this.checkThreeInARow(
          this.boardArray[3].content,
          this.boardArray[4].content,
          this.boardArray[5].content
        ) ||
        this.checkThreeInARow(
          this.boardArray[6].content,
          this.boardArray[7].content,
          this.boardArray[8].content
        ) ||
        this.checkThreeInARow(
          this.boardArray[6].content,
          this.boardArray[4].content,
          this.boardArray[2].content
        ) ||
        this.checkThreeInARow(
          this.boardArray[1].content,
          this.boardArray[4].content,
          this.boardArray[7].content
        ) ||
        this.checkThreeInARow(
          this.boardArray[2].content,
          this.boardArray[5].content,
          this.boardArray[8].content
        )
      ) {
        this.winner = this.currentlyPlaying;
      } else if (this.checkIfFullBoard()) {
        this.winner = "None";
      }
    },
    checkIfFullBoard() {
      return this.boardArray.every((tile) => tile.content !== "");
    },
    setTextPanelContent() {
      if (this.winner !== "") {
        this.resetBtnLabel = "New Game";
        this.winner === "None"
          ? (this.textPanelContent = "Draw!")
          : (this.textPanelContent = `${this.winner.name} Wins!`);
      } else {
        this.textPanelContent = `${this.currentlyPlaying.name}'s (${this.currentlyPlaying.input}) turn.`;
      }
    },
  },
  created() {
    // Initialize 3x3 board by creating the array
    for (let i = 0; i < 9; i++) {
      this.boardArray.push({ id: i, content: "" });
    }
    // Player 1 is first player
    this.currentlyPlaying = this.players[0];
    this.setTextPanelContent();
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