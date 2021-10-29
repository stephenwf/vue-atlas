<script>
export default {
  name: 'ManifestMixin',
  inject: ['manifest'],
  data() {
    return {
      manifest: this.manifest
    }
  }
}
</script>
