<template>
  <div id="app">
    <!-- <Menu></Menu> -->
    <!-- This is the page navigation -->
    <div class="hidden-xs hidden-sm col-md-2 col-lg-2">
      <Timeline v-for="game in allGames" :game="game"></Timeline>
    </div>
    <!--This is the main content-->
    <div class="col-xs-12 col-sm-12 col-md-10 col-lg-10">
      <!--Page logo and title-->
      <div class="col-xs-12 col-sm-12 col-md-12 col-lg-12">
        <div class="header">
          <img class="olympic-rings" src="../static/imgs/olympic-rings.png">
          <h1 class="header-txt">History of the Olympic Games</h1>
          <div class="hidden-xs hidden-sm">
            <p class="sub-txt">*Click on the year to learn about each Olympic game</p>
          </div>
        </div>
      </div>
      <!--Each game info-->
      <div class="col-xs-12 col-sm-12 col-md-12 col-lg-12">
        <Game v-for="(game, index) in allGames" :game="game"> {{ currentGame(game) }} <Game>
      </div>
    </div><!--Main content closing div-->

  </div><!--App closing div-->
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
/*Logo and Title styles*/
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
