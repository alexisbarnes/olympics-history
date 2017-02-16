<template>
  <div class="Game">
    <!--Title for each game-->
    <div class="col-xs-12 col-sm-12 col-md-12 col-lg-12">
      <h1 class="game-title"> {{ game.Game }} </h1>
    </div>

    <!--Photo/Video for each game-->
    <div class="col-xs-12 col-sm-12 col-md-12 col-lg-12">
      <div class="visual" v-if="game.Video === null"> {{ game.Photo }} </div>
      <div v-else> {{ game.Video }} </div>
    </div>

    <!--Key Events for each game-->
    <div class="col-xs-12 col-sm-12 col-md-6 col-lg-6">
      <h2 class="events-txt">Key Events</h2>
      <ul>
        <li class="key-events"> {{ game.Fact1 }} </li>
        <li class="key-events"> {{ game.Fact2 }} </li>
        <li class="key-events"> {{ game.Fact3 }} </li>
        <li class="key-events"> {{ game.Fact4 }} </li>
      </ul>
    </div>

    <!--Medal Count for each game-->
    <div class="col-xs-12 col-sm-12 col-md-6 col-lg-6">
      <h2 class="medals-txt">Medal Count</h2>
      <div class="medals-img"> {{ game.Medals }} </div>
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
  }

/*Main photo/vid styles*/
  .visual {
    text-align: center;
    margin: 20px;
  }

/*Key Events styles*/
  .events-txt {
    text-align: center;
    font-family: 'Lato', sans-serif;
    color: #0089C4;
  }

  li {
    font-family: 'Lato', sans-serif;
    font-size: 15px;
  }

/*Medal count styles*/
  .medals-txt {
    text-align: center;
    font-family: 'Lato', sans-serif;
    color: #0089C4;
  }

  .medals-img {
    text-align: center;
    margin: 20px;
  }

</style>
