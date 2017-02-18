<template>
  <div class="Game">
    <div class="col-xs-12 col-sm-12 col-md-12 col-lg-12">
      <h1 class="game-title"> {{ game.Game }} </h1>
    </div>
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
  },
  methods: {
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
/*Game title styles*/
  h1 {
    text-align: center;
  }

  .game-title {
    color: #0089C4;
    font-family: 'Lato', sans-serif;
    font-size: 50px;
  }

</style>
