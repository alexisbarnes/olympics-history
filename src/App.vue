<template>
  <div id="app">
    <!-- <Menu></Menu> -->
    <!-- This is the page navigation -->
    <div class="hidden-xs hidden-sm col-md-2 col-lg-2">
      <!-- https://webdesign.tutsplus.com/tutorials/building-a-vertical-timeline-with-css-and-a-touch-of-javascript--cms-26528-->
      <!--DESKTOP NAV-->
      <div class="timeline">
            <ul>
              <li v-for="game in allGames" @click="show(game)" :class="[game.active ? activeClass: '']">
                <div>
                </div>
                  <p class="menu-year"> {{ game.Year }} </p>
              </li>
            </ul>
      </div>
    </div>

    <!--MOBILE NAV-->
    <nav class="navbar navbar-default hidden-md hidden-lg hidden-xl">
      <div class="container-fluid">
        <!-- Brand and toggle get grouped for better mobile display -->
        <div class="navbar-header">
          <button type="button" class="navbar-toggle collapsed" data-toggle="collapse" data-target="#bs-example-navbar-collapse-1" aria-expanded="false">
            <span class="sr-only">Toggle navigation</span>
            <span class="icon-bar"></span>
            <span class="icon-bar"></span>
            <span class="icon-bar"></span>
          </button>
          <a class="navbar-brand" @click="backHome"><img src="../static/imgs/olympic-rings.png" class="rings-mobile"></a>
        </div>

        <!-- Collect the nav links, forms, and other content for toggling -->
        <div class="collapse navbar-collapse" id="bs-example-navbar-collapse-1">
          <ul class="nav navbar-nav">
            <li class="mobile-list" v-for="game in allGames" @click="show(game)"> {{ game.Year }} </li>
          </ul>
        </div><!-- /.navbar-collapse -->
      </div><!-- /.container-fluid -->
    </nav>
    <!--This is the main content-->
    <div class="col-xs-12 col-sm-12 col-md-10 col-lg-10">
      <div v-if="showIntro">
        <Intro></Intro>
      </div>
      <div v-else>
        <div class="col-xs-12 col-sm-12 col-md-12 col-lg-12">
          <div @click="backHome"><img src="../static/imgs/olympic-rings.png" class="rings-home"></div>
        </div>
        <!--Thank you to Alma and Kate for helping me figure out how to loop through my json correctly!-->
        <Game :game="currentGame"></Game>
        <Vidphoto :game="currentGame"></Vidphoto>
        <Events :game="currentGame"></Events>
        <Medals :game="currentGame"></Medals>
      </div>
    </div>

    <div class="col-xs-12 col-sm-12 col-md-12 col-lg-12 no-padding">
      <footer>
        <p class="footer-txt">&copy; Alexis Barnes<br>Sources: Wikipedia &amp; Youtube</p>
      </footer>
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
      currentGame: '',
      visual: null,
      activeClass: 'activated'
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
    // Looping through JSON & setting active to false, so only one game.active is true
    show: function (game) {
      for (var i in this.allGames) {
        this.allGames[i].active = false
      }
      this.currentGame = game
      this.showIntro = false
      game.active = true
    },
    backHome () {
      this.showIntro = true
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
  height: 100%;
  font: 'Lato', sans-serif;
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
  background: #0089C4;
  cursor: pointer;
}

/*Activated link on timeline*/
.activated {
  background: #000 !important;
}

.timeline ul li:hover {
  background: #000;
}
/*.timeline ul .menu-year:hover {
  color: #D5002B;
}*/
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

/*Olympic Logo on page for each game*/
.rings-home {
  height: 150px;
  float: right;
  cursor: pointer;
}

/*Mobile nav logo*/
.navbar-brand img {
  height: 30px;
}

/*Mobile nav dropdown*/
.mobile-list {
  text-align: center;
}

/*Footer styles*/
footer {
  border-top: 1px solid #0089C4;
  background-color: #fff;
  height: 50px;
  width: 100%;
  margin-top: 20px;
}

.footer-txt {
  font-family: 'Lato', sans-serif;
  text-align: center;
}

.no-padding {
  padding: 0;

}

</style>
