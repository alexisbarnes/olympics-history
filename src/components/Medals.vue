<template>
  <div class="Medals">
    <div class="col-xs-12 col-sm-12 col-md-6 col-lg-6">
      <div class="col-xs-12 col-sm-12 col-md-12 col-lg-12">
        <h2>Medal Count</h2>
        <p>*Ranked by number of gold medals</p>
      </div>
      <div class="medals">
        <img :src="game.Medals" class="medals-img">
      </div>
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
.medals {
  text-align: center;
}

img {
  height: 400px;
}

h2 {
  text-align: center;
  color: #0089C4;
  font-family: 'Lato', sans-serif;

}

p {
  text-align: center;
  font-family: 'Lato', sans-serif;
  font-style: italic;
}

@media screen and (max-width: 400px) {
  img {
    height: 350px;
  }
}
</style>
