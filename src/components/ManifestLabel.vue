<template>
  <div>
    <h1 v-if="manifest.current">{{ manifest.current.label.none[0] }}</h1>
  </div>
</template>
<script>

import ManifestMixin from '@/components/ManifestMixin';

export default {
  name: 'ManifestLabel',
  mixins: [ManifestMixin],
}
</script>
