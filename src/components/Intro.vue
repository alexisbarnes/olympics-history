<template>
  <div class="Intro">
    <div class="col-xs-12 col-sm-12 col-md-12 col-lg-12">
      <div class="header">
        <img class="olympic-rings" src="../../static/imgs/olympic-rings.png">
        <h1 class="header-txt">History of the Modern Olympic Games</h1>
          <p class="sub-txt">*Click on a year to learn about each Olympic game</p>
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
  }

}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
/*Logo and Title styles*/
.header {
  text-align: center;
  position: fixed;
  margin: 120px;
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

/*Olympic Rings responsive*/
@media screen and (max-width: 400px) {
  .header-txt {
    font-size: 30px;
  }
}

@media screen and (max-width: 550px) {
  img {
    height: 150px;
  }
}

@media screen and (max-width: 991px) {
  .header {
    position: static;
    margin: 0;
    padding: 10px;
  }
}

</style>
