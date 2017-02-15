<template>
  <div id="app">
    <!-- <Menu></Menu> -->
    <!-- This is the page navigation -->
    <div class="col-md-2">
      <Timeline v-for="game in allGames" :game="game"></Timeline>
    </div>

    <div class="col-md-10">
      <Game v-for="game in allGames" :game="game"><Game>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import Game from './components/Game'
import Timeline from './components/Timeline'
export default {
  name: 'app',
  components: {
    Game,
    Timeline
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
        // console.log(this.allGames)
      })
  }
}
</script>

<style>
#app {
}

</style>
