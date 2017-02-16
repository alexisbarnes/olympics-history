<template>
  <div id="app">
    <!-- <Menu></Menu> -->
    <!-- This is the page navigation -->
    <div class="hidden-xs hidden-sm col-md-2 col-lg-2">
      <!-- https://webdesign.tutsplus.com/tutorials/building-a-vertical-timeline-with-css-and-a-touch-of-javascript--cms-26528-->
      <div class="timeline">
            <ul>
              <li v-for="game in allGames" @click="show(game)">
                <div>
                </div>
                  <p class="menu-year"> {{ game.Year }} </p>
              </li>
            </ul>
      </div>
    </div>
    <!--This is the main content-->
    <div class="col-xs-12 col-sm-12 col-md-10 col-lg-10">
      <div v-if="showIntro">
        <Intro></Intro>
      </div>
      <div else>
        <Game :game="currentGame"></Game>
        <Vidphoto :game="currentGame"></Vidphoto>
        <Events :game="currentGame"></Events>
        <Medals :game="currentGame"></Medals>
      </div>
    </div>

  </div><!--App closing div-->
</template>

<script>
import axios from 'axios'
import Intro from './components/Intro'
import Vidphoto from './components/Vidphoto'
import Game from './components/Game'
import Events from './components/Events'
import Medals from './components/Medals'
export default {
  name: 'app',
  components: {
    Intro,
    Vidphoto,
    Game,
    Events,
    Medals
  },
  data () {
    return {
      allGames: [],
      showIntro: true,
      currentGame: ''
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
    show: function (game) {
      this.currentGame = game
    }
  }
}
</script>

<style>
#app {
}
/*Nav Styles*/
*,
*::before,
*::after {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body {
  font: normal 16px/1.5 "Helvetica Neue", sans-serif;
  background: #fff;
  color: #000000;
  overflow-x: hidden;
  padding-bottom: 50px;
}
/* TIMELINE */
.timeline ul li {
  list-style-type: none;
  position: relative;
  width: 6px;
  margin: 0 auto;
  padding-top: 40px;
  background: #00A53C;
}
.timeline ul li:hover {
  background: #D5002B;
}
.timeline ul .menu-year:hover {
  color: #D5002B;
}
.timeline ul li::after {
  content: '';
  position: absolute;
  left: 50%;
  bottom: 0;
  transform: translateX(-50%);
  width: 30px;
  height: 30px;
  border-radius: 50%;
  background: inherit;
}
.menu-year {
    margin: -25px 0 0px 20px;
    float: left;
}

</style>
