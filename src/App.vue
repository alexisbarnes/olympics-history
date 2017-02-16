<template>
  <div id="app">
    <!-- <Menu></Menu> -->
    <!-- This is the page navigation -->
    <div class="col-md-2">
      <Timeline v-for="game in allGames" :game="game"></Timeline>
    </div>

    <div class="col-md-10"> <!--contains all info-->
      <div class="col-md-12">
        <div class="header">
          <img class="olympic-rings" src="../static/imgs/olympic-rings.png">
          <h1 class="header-txt">History of the Olympic Games</h1>
          <p class="sub-txt">*Click on the year to learn about each Olympic game</p>
        </div>
      </div>
      <div class="col-md-12">
        <Game v-for="(game, index) in allGames" :game="game"> {{ currentGame(game) }} <Game>
      </div>


    </div>

  </div>
</template>

<script>
import axios from 'axios'
import Game from './components/Game'
import Timeline from './components/Timeline'
import Events from './components/Events'
export default {
  name: 'app',
  components: {
    Game,
    Timeline,
    Events
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
        // console.log(this.allGames[0].Year)
      })
  },
  methods: {
    currentGame (game) {
      return `${game.Game}`
    }
  }
}
</script>

<style>
#app {
}

.header {
  text-align: center;
}

.header-txt {
  font-size: 60px;
  font-family: 'Lato', sans-serif;
  font-style: normal;
}

.sub-txt {
  font-family: 'Lato', sans-serif;
  font-style: italic;
}

img {
  height: 250px;
  width: auto;
}

</style>
