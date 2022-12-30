<template>
  <div
    :id="id"
    class="chessSquare"
    @dragover.prevent
    @drop.prevent="dropMethod">
    <slot></slot>
  </div>
</template>

<script>




import ChessBoard from "@/components/ChessBoard.vue";

export default {
  props: {
    id:String,
  },




  name: "ChessSquare",
  methods: {
    dropMethod(e){

      const pieceID = e.dataTransfer.getData('ChessPiece_id');
      const piece = document.getElementById(pieceID);
      piece.style.display = "block";

      console.log(this.$parent.$parent.$data)


      e.target.appendChild(piece);



    },



  }
}
</script>

<style scoped>
  .chessSquare {
    max-width: 100%;
    max-height: 100%;

  }



</style>