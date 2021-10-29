<script>

export default {
  name: 'IIIFCanvas',
  inject: ['vault', 'manifest'],
  props: {
    index: Number,
  },
  provide () {
    return {
      canvas: this.context
    };
  },
  beforeMount() {
    this.setCanvasFromManifest(this.manifest.current);
  },
  data () {
    return {
      context: {
        current:  null
      }
    }
  },

  methods: {
    setCanvasFromManifest() {
      if (!this.manifest.current) {
        return undefined;
      }
      const canvas = this.manifest.current.items[this.index];
      if (canvas) {
        this.context.current = this.vault.fromRef(canvas);
      }
    },
  },

  watch: {
    'index': {
      handler() {
        this.setCanvasFromManifest();
      }
    },
    'manifest.current': {
      handler() {
        this.setCanvasFromManifest();
      }
    }
  },

  render() {
    return this.$slots.default;
  }
}
</script>
