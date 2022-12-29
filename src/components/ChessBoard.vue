<template>
  <div class="chess-board">


    <ChessSquare v-for="(row,rowIndex) in rows" :key="rowIndex" class="row">
      <ChessSquare v-for="(cell, cellIndex) in row" :key="cellIndex"
           :classs="'cell'.concat(' ', cellColour(rowIndex,cellIndex))">
        <ChessPiece v-if="cell !== ''" draggable="true" v-bind:type="cell[0]" v-bind:color="cell[1]"></ChessPiece>
      </ChessSquare>
    </ChessSquare>

  </div>
</template>

<script>
import ChessPiece from "@/components/ChessPiece.vue";
import PieceType from  "@/components/enums/PieceType";
import draggable from "vuedraggable";
import ChessSquare from "@/components/ChessSquare.vue";
import PieceColor from "@/components/enums/PieceColor";

export default {
    name: "ChessBoard",

  components: {
    ChessSquare,
      ChessPiece,
  },
    directives:
    {

      draggable
    },

    data(){
      return {
        rows: [
          ['', '', '', '', '', '', '', ''],
          ['', '', '', [PieceType.King, PieceColor.Black], '', '', '', ''],
          ['', '', '', '', '', '', '', ''],
          ['', '', '', '', '', '', '', ''],
          ['', '', '', '', [PieceType.King,PieceColor.White], '', '', ''],
          ['', '', '', '', '', '', '', ''],
          ['', '', '', '', '', '', '', ''],
          ['', '', '', '', '', '', '', '']
        ]
      }
      },
  methods:{
    cellColour(rowIndex, columnIndex){

      return (rowIndex + columnIndex) % 2 ===0 ? 'light' : 'dark';
    },

  },

  }
</script>

<style scoped>
.row {
  display: flex;
}
.chess-board {
  display: flex;
  flex-wrap: wrap;
  width: 400px;
  height:400px
}
.light {
  background-color: #f0d9b5;
}

.dark {
  background-color: #b58863;
}

.cell {
  width: 50px;
  height: 50px

}
</style>