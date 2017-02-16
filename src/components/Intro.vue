<template>
  <div class="Intro">
    <div class="col-xs-12 col-sm-12 col-md-12 col-lg-12">
      <div class="header">
        <img class="olympic-rings" src="../../static/imgs/olympic-rings.png">
        <h1 class="header-txt">History of the Olympic Games</h1>
        <div class="hidden-xs hidden-sm">
          <p class="sub-txt">*Click on the year to learn about each Olympic game</p>
        </div>
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
