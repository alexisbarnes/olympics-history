<template>
  <div id="app">
    <Game v-for="game in allGames" :game="game"><Game>
  </div>
</template>

<script>
import axios from 'axios'
import Game from './components/Game'

export default {
  name: 'app',
  components: {
    Game
  },
  data () {
    return {
      allGames: []
    }
  },

  mounted () {
    axios.get('/static/games.json')
      .then((response) => {
        this.allGames = response.data
        console.log(this.allGames)
      })
  }
}

</script>

<style>
#app {

}
</style>
