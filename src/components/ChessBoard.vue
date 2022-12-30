<template>
  <div class="chess-board">


    <ChessSquare v-for="(row,rowIndex) in rows" :key="rowIndex" class="row">
      <ChessSquare v-for="(cell, cellIndex) in row" :key="cellIndex"
           :class="'cell'.concat(' ', cellColour(rowIndex,cellIndex))"
            v-bind:id="'cell ' + rowIndex +  '' +  cellIndex">
        <ChessPiece v-if="cell !== ''" draggable="true" v-bind:type="cell[0]" v-bind:color="cell[1]" v-bind:id="cell[1] + cell[0] + ' ' + rowIndex + cellIndex"></ChessPiece>
      </ChessSquare>
    </ChessSquare>
    <button class="submit button" v-on:click="generateFEN"></button>

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
          [[PieceType.Rook, PieceColor.Black], [PieceType.Knight, PieceColor.Black], [PieceType.Bishop, PieceColor.Black], [PieceType.Queen, PieceColor.Black], [PieceType.King, PieceColor.Black], [PieceType.Bishop, PieceColor.Black], [PieceType.Knight, PieceColor.Black], [PieceType.Rook, PieceColor.Black]],
          [[PieceType.Pawn, PieceColor.Black], [PieceType.Pawn, PieceColor.Black], [PieceType.Pawn, PieceColor.Black], [PieceType.Pawn, PieceColor.Black], [PieceType.Pawn, PieceColor.Black], [PieceType.Pawn, PieceColor.Black], [PieceType.Pawn, PieceColor.Black], [PieceType.Pawn, PieceColor.Black]],
          ['', '', '', '', '', '', '', ''],
          ['', '', '', '', '', '', '', ''],
          ['', '', '', '', '', '', '', ''],
          ['', '', '', '', '', '', '', ''],
         [[PieceType.Pawn, PieceColor.White], [PieceType.Pawn, PieceColor.White], [PieceType.Pawn, PieceColor.White], [PieceType.Pawn, PieceColor.White], [PieceType.Pawn, PieceColor.White], [PieceType.Pawn, PieceColor.White], [PieceType.Pawn, PieceColor.White], [PieceType.Pawn, PieceColor.White]],
          [[PieceType.Rook, PieceColor.White], [PieceType.Knight, PieceColor.White], [PieceType.Bishop, PieceColor.White], [PieceType.Queen, PieceColor.White], [PieceType.King, PieceColor.White], [PieceType.Bishop, PieceColor.White], [PieceType.Knight, PieceColor.White], [PieceType.Rook, PieceColor.White]],
        ]

      }
      },
  methods:{
    cellColour(rowIndex, columnIndex){

      return (rowIndex + columnIndex) % 2 ===0 ? 'light' : 'dark';
    },
    dragend(pieceID)
    {
      console.log(pieceID + ' : ' )
    },

    generateFEN()
    {
      for (let component of this.$children)
      {
        console.log(component)
      }

      console.log(this.rows)

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
  height: 50px;

}
.button {
  width: 100px;
  height: 200px;
}



</style>