<template>
  <div id="app">
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

    <!-- MAIN CONTENT -->
    <div class="col-xs-12 col-sm-12 col-md-10 col-lg-10">
      <div v-if="showIntro">
        <Intro></Intro>
      </div>
      <div v-else>
        <!--Logo shows for each game-->
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

    <!--FOOTER-->
    <div class="col-xs-12 col-sm-12 col-md-12 col-lg-12 no-padding">
      <footer>
        <p class="footer-txt">&copy; <a href="https://github.com/alexisbarnes" target="_blank">Alexis Barnes</a><br>Sources: <a href="https://en.wikipedia.org/wiki/1972_Summer_Olympics_medal_table" target="_blank">Wikipedia</a> &amp; <a href="https://www.youtube.com" target="_blank">YouTube</a></p>
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
    //  Shows intro when click on Olympics logo
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
  background: #B82420 !important;
}

.timeline ul li:hover {
  background: #B82420;
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
  color: #000;
  font-family: 'Lato', sans-serif;
  font-size: 20px;
  background: #E6E6E6;
  border-bottom: 1px solid #000;
}

/*Shows hamburger menu for iPad*/
@media (max-width: 1200px) {
    .navbar-header {
        float: none;
    }
    .navbar-left,.navbar-right {
        float: none !important;
    }
    .navbar-toggle {
        display: block;
    }
    .navbar-collapse {
        border-top: 1px solid transparent;
        box-shadow: inset 0 1px 0 rgba(255,255,255,0.1);
    }
    .navbar-fixed-top {
        top: 0;
        border-width: 0 0 1px;
    }
    .navbar-collapse.collapse {
        display: none!important;
    }
    .navbar-nav {
        float: none!important;
        margin-top: 7.5px;
    }
    .navbar-nav>li {
        float: none;
    }
    .navbar-nav>li>a {
        padding-top: 10px;
        padding-bottom: 10px;
    }
    .collapse.in{
        display:block !important;
    }
}

/*Footer styles*/
footer {
  background-color: #e6e6e6;
  padding: 10px 0 0 0;
  height: 60px;
  width: 100%;
  margin-top: 20px;
}

.footer-txt {
  font-family: 'Lato', sans-serif;
  text-align: center;
}

footer a {
  color: #B82420;
}

footer a:hover {
  color: #0089C4;
  text-decoration: none;
}

.no-padding {
  padding: 0;

}

</style>
