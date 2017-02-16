<template>
  <div class="Events">
    <div class="col-xs-12 col-sm-12 col-md-6 col-lg-6">
      <ul>
        <li class="key-events"> {{ game.Fact1 }} </p>
        <li class="key-events"> {{ game.Fact2 }} </p>
        <li class="key-events"> {{ game.Fact3 }} </p>
        <li class="key-events"> {{ game.Fact4 }} </p>
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


</style>
