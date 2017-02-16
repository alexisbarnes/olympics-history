<template>
  <div class="Game">
    <div class="col-xs-12 col-sm-12 col-md-12 col-lg-12">
      <h1 class="game-title"> {{ game.Game }} </h1>
    </div>
  </div>

</template>

<script>
export default {

  props: [

    'game'

  ],

  data () {
    return {
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
