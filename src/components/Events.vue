<template>
  <div class="Events">
    <ul>
      <li class="key-events"> {{ game.Fact1 }} </p>
      <li class="key-events"> {{ game.Fact2 }} </p>
      <li class="key-events"> {{ game.Fact3 }} </p>
      <li class="key-events"> {{ game.Fact4 }} </p>
    </ul>
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
