<template>
  <div>
    <div class="status">{{ status }}</div>
    <div class="board-row" v-for="row in 3" :key="row">
      <Square
        v-for="col in 3"
        :key="(row - 1) * 3 + col"
        :value="squares[(row - 1) * 3 + col - 1]"
        @click="handleClick((row - 1) * 3 + col - 1)"
      />
    </div>
    <button @click="resetGame" class="btn">Reset Game</button>
  </div>
</template>

<script>
import Square from "./Square.vue";

export default {
  components: {
    Square,
  },
  data() {
    return {
      squares: Array(9).fill(null),
      xIsNext: true,
    };
  },
  computed: {
    status() {
      const winner = this.calculateWinner();
      if (winner) {
        return `Winner: ${winner}`;
      } else {
        return `Next player: ${this.xIsNext ? "X" : "O"}`;
      }
    },
  },
  methods: {
    handleClick(i) {
      if (this.calculateWinner() || this.squares[i]) {
        return;
      }
      const squares = this.squares.slice();
      squares[i] = this.xIsNext ? "X" : "O";
      this.squares = squares;
      this.xIsNext = !this.xIsNext;
    },
    calculateWinner() {
      const lines = [
        [0, 1, 2],
        [3, 4, 5],
        [6, 7, 8],
        [0, 3, 6],
        [1, 4, 7],
        [2, 5, 8],
        [0, 4, 8],
        [2, 4, 6],
      ];
      for (let i = 0; i < lines.length; i++) {
        const [a, b, c] = lines[i];
        if (
          this.squares[a] &&
          this.squares[a] === this.squares[b] &&
          this.squares[a] === this.squares[c]
        ) {
          return this.squares[a];
        }
      }
      return null;
    },
    resetGame() {
      this.squares = Array(9).fill(null);
    },
  },
};
</script>

<style scoped>
/* CSS styles for the board */
.status {
  margin-bottom: 20px;
  margin-top: 10px;
}

.board-row::after {
  clear: both;
  content: "";
  display: table;
}

.btn {
  outline: none;
  border: none;
  margin-top: 20px;
  font-size: 15px;
  background-color: #ffffff;
  padding: 10px 10px;
  border: 1px solid rgb(126, 126, 126);
  cursor: pointer;
}
</style>
