<template>
  <div>
    <h1 v-if="canvas.current">{{ canvas.current.label.none[0] }}</h1>
  </div>
</template>
<script>

import CanvasMixin from '@/components/CanvasMixin';

export default {
  name: 'CanvasLabel',
  mixins: [CanvasMixin],
}
</script>
