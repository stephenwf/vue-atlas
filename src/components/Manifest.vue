<script>

export default {
  name: 'Manifest',
  inject: ['vault'],
  props: {
    manifestId: String,
  },
  provide () {
    return {
      manifest: this.context
    };
  },
  data () {
    return {
      context: {
        current:  null
      }
    }
  },
  created() {
    this.vault.loadManifest(this.manifestId).then(manifest => {
      this.context.current = manifest;
    })
  },
  render() {
    return this.$slots.default[0];
  }
}
</script>
