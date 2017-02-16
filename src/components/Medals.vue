<template>
  <div class="Medals">
    <div class="col-xs-12 col-sm-12 col-md-6 col-lg-6">
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
  height: 260px;
}
</style>
