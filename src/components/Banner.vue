<template>
  <div class="chess-board">
    <div v-for="(row, rowIndex) in board" :key="rowIndex" class="row">
      <div v-for="(piece, colIndex) in row" :key="colIndex" class="square" :class="getSquareClass(rowIndex, colIndex)" @click="handleSquareClick(rowIndex, colIndex)">
        <img v-if="piece" :src="'src/assets/white_king.png'" alt="Piece" />
      </div>
    </div>
    <button @click="generateFEN">Generate FEN</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      board: [
        ['R', 'N', 'B', 'Q', 'K', 'B', 'N', 'R'],
        ['P', 'P', 'P', 'P', 'P', 'P', 'P', 'P'],
        [null, null, null, null, null, null, null, null],
        [null, null, null, null, null, null, null, null],
        [null, null, null, null, null, null, null, null],
        [null, null, null, null, null, null, null, null],
        ['p', 'p', 'p', 'p', 'p', 'p', 'p', 'p'],
        ['r', 'n', 'b', 'q', 'k', 'b', 'n', 'r'],
      ],
    }
  },
  methods: {
    getSquareClass(rowIndex, colIndex) {
      // Determine the CSS class for the square based on its position
      const isDark = (rowIndex + colIndex) % 2 === 1;
      return isDark ? 'dark' : 'light';
    },
    handleSquareClick(rowIndex, colIndex) {
      // Handle a click on a square by moving the selected piece to the square
      if (this.selectedPiece) {
        this.board[rowIndex][colIndex] = this.selectedPiece;
        this.board[this.selectedPieceRow][this.selectedPieceCol] = null;
        this.selectedPiece = null;
      } else {
        this.selectedPiece = this.board[rowIndex][colIndex];
        this.selectedPieceRow = rowIndex;
        this.selectedPieceCol = colIndex;
      }
    },
    generateFEN() {
      // Generate the FEN code for the current board position
      console.log(this.board)
    }
  }
}
</script>
<style>
.chess-board {
  display: flex;
  flex-wrap: wrap;
  width: 400px;
  height:400px
}
  .square{
    width: 50px;
    height: 50px;
  }
</style>