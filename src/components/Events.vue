<template>
  <div class="Events">
    <div class="col-xs-12 col-sm-12 col-md-6 col-lg-6">
      <!-- <div class="col-xs-12 col-sm-12 col-md-12 col-lg-12"> -->
        <h2 class="sub-header">Key Events</h2>
     <!-- </div> -->
        <ul>
          <li class="keyEvents"> {{ game.Fact1 }} </p>
          <li class="keyEvents"> {{ game.Fact2 }} </p>
          <li class="keyEvents"> {{ game.Fact3 }} </p>
          <li class="keyEvents"> {{ game.Fact4 }} </p>
        </ul>
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
h2 {
  text-align: center;
  font-family: 'Lato', sans-serif;
  color: #0089C4;
}

li {
  font-family: 'Lato', sans-serif;
  font-size: 20px;
}

/*Text is smaller on phone*/
@media screen and (max-width: 400px) {
  li {
    font-size: 15px;
  }
}

</style>
