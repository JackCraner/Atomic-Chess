<template>
  <div
    :id="id"
    class="chessSquare"
    @dragover.prevent
    @drop.prevent="drop">
    <slot></slot>
  </div>
</template>

<script>

import {useSlots} from "vue";


export default {
  props: {
    id:String,
  },



  name: "ChessSquare",
  methods: {
    drop: e => {

      const pieceID = e.dataTransfer.getData('ChessPiece_id');

      const piece = document.getElementById(pieceID);
      piece.style.display = "block";


      e.target.appendChild(piece);



    }
  }
}
</script>

<style scoped>
  .chessSquare {
    max-width: 100%;
    max-height: 100%;

}
</style>