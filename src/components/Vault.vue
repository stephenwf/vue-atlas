<script>
import { Vault } from '@hyperion-framework/vault';

export default {
  name: 'Vault',
  provide() {
    return { vault: this.vault };
  },
  data () {
    let vault = this.vault
    if (!vault) {
      vault = new Vault()
    }

    return { vault: vault };
  },
  mounted () {
    this.vault = new Vault();
  },
  render() {
    return this.$slots.default[0];
  }
}
</script>
