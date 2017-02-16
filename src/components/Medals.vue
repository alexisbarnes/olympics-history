<template>
  <div class="Medals">
    <div class="col-xs-12 col-sm-12 col-md-6 col-lg-6">
      <div class="col-xs-12 col-sm-12 col-md-12 col-lg-12">
        <h2>Medal Count</h2>
        <p>*Ranked by number of gold medals</p>
      </div>
      <img :src="game.Medals" class="medals-img">
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
img {
  height: 400px;
}

h2 {
  text-align: center;
  color: #0089C4;
}

p {
  text-align: center;
  font-style: italic;
}
</style>
