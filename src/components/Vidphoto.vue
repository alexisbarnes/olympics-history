<template>
  <div class="Visual">
    <div class="col-xs-12 col-sm-12 col-md-12 col-lg-12">
      <div class="visual" v-if="game.Video === null">
        <img :src="game.Photo" class="visuals">
      </div>
      <!--vue youtube embed component used https://github.com/kaorun343/vue-youtube-embed -->
      <div v-else>
        <div class="visual">
          <youtube :video-id="game.Video" @ready="ready" @playing="playing"></youtube>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
'use strict'
import Vue from 'vue'
import VueYouTubeEmbed from 'vue-youtube-embed'
Vue.use(VueYouTubeEmbed)
export default {
  props: [
    'game'
  ],

  data () {
    return {
      videoID: ''
    }
  },
  methods: {
    ready (player) {
      this.player = player
    },
    playing (player) {
      // The player is playing a video.
    },
    change () {
      // when you change the value, the player will also change.
      // If you would like to change `playerVars`, please change it before you change `videoId`.
      // If `playerVars.autoplay` is 1, `loadVideoById` will be called.
      // If `playerVars.autoplay` is 0, `cueVideoById` will be called.
      this.videoId = 'another video id'
    },
    stop () {
      this.player.stopVideo()
    },
    pause () {
      this.player.pauseVideo()
    }
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.visual {
 text-align: center;
 margin: 20px;
}

img {
  height: 300px;
}

/*Photo is responsive for mobile*/
@media screen and (max-width: 400px) {
  .visuals {
    height: 250px;
  }
}

</style>
