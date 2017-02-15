<template>
  <div id="app">
    <!-- <Menu></Menu> -->
    <!-- This is the page navigation -->
    <div class="col-md-2">
      <div class="timeline">
        <ul>
            <li v-for="game in allGames" :game="game">
              <div>
              </div>
              <p class="menu-year"> {{ game.Year }} </p>
            </li>
        </ul>
      </div>
    </div>

    <div class="col-md-10">
      <Game v-for="game in allGames" :game="game"><Game>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import Game from './components/Game'
import Menu from './components/Menu'
export default {
  name: 'app',
  components: {
    Game,
    Menu
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
  padding-top: 50px;
  background: #000000;
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
