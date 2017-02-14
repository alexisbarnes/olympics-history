<template>
    <div class="Game">
        <h1 class="game-title"> {{ game.Game }} </h1>


    </div>
</template>

<script>
export default {
  props: [
    'game'
  ],
  data () {
    return {
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1 {
  text-align: center;
}

</style>
