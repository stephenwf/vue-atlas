<template>
  <div>
    <img v-if="thumbnail" :src="thumbnail.id" />
  </div>
</template>
<script>

export default {
  name: 'CanvasThumbnail',
  // We need the vault, and the current canvas.
  inject: ['vault', 'canvas'],

  // Our props we'll pass to the vaults getThumbnail()
  props: ['width', 'height'],

  data () {
    return {
      thumbnail: null
    };
  },

  methods: {
    // Called when the canvas changes.
    setCanvasThumbnail() {
      if (this.canvas.current) {
        // Request the thumbnail.
        this.vault.getThumbnail(this.canvas.current, {height: this.height || 200, width: this.width || 200}).then(res => {
          this.thumbnail = res.best;
        })
      }
    },
  },

  watch: {
    // When the injected canvas changes
    'canvas.current': {
      handler() {
        this.setCanvasThumbnail();
      }
    }
  }
}
</script>
