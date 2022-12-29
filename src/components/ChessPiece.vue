<template>


  <img :id="color + ' ' + type"
       :draggable="draggable"
       @dragstart="dragStart"
       @dragover.stop class="pieceImage" v-bind:src="'src/assets/' +color+ '_' +type + '.png'" alt="name">

</template>

<script>
export default {
  props: {
    color: {
      type: String,
      required: true,
    },
    type: {
      type: String,
      required: true,
    },
    draggable:{
      type:String,
      required:true
    }

  },
  methods: {
    dragStart: e => {
      const target = e.target;
      e.dataTransfer.setData('ChessPiece_id', target.id);

    }
  },
  data()
  {
    return {
      imageURL: ''
    }

  },

  created() {
    this.imageURL = "'src/assets/+color+_king.png'"
  }
}
</script>

<style scoped>
  .pieceImage{
    object-fit: cover;
    max-width: 100%;
    max-height: 100%;

  }

</style>