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
      currentTitle: '',
      currentYear: '',
      currentPhoto: '',
      currentVideo: '',
      currentFact1: '',
      currentFact2: '',
      currentFact3: '',
      currentFact4: '',
      currentMedal: ''
    }
  },
  methods: {
    this.game.push({
      currentTitle: this.Game
    })
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  h1 {
    text-align: center;
  }

  .game-title {
    color: #0089C4;
  }

</style>
