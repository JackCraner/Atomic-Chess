<template>
  <div>
    <button class="button" v-on:click="generateFEN"></button>
  </div>
</template>

<script>
export default {
  name: "ChessButton",
  methods: {
    generateFEN() {
      console.log("yo")
    }
  }
}
</script>

<style scoped>
  .button{
    height:100px;
    width:100px;
  }
</style>