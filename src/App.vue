<template>
  <div id="app">
    <Vault>
      <manifest manifest-id="https://media.getty.edu/iiif/manifest/ae8c3376-f8d6-447b-90a9-9c67b4cbe4d1">
        <div>
          <manifest-label />
          <IIIFCanvas :index="canvasIndex">
            <div>
              <canvas-label />
              <canvas-thumbnail width="200" height="200"/>
            </div>
          </IIIFCanvas>

          <button v-on:click="prev">prev</button>
          <button v-on:click="next">next</button>
        </div>
      </manifest>
    </Vault>
  </div>
</template>

<script>
import Vault from './components/Vault';
import Manifest from './components/Manifest';
import ManifestLabel from './components/ManifestLabel';
import IIIFCanvas from './components/IIIFCanvas';
import CanvasLabel from '@/components/CanvasLabel';
import CanvasThumbnail from "@/components/CanvasThumbnail";

export default {
  name: 'App',
  components: {
    CanvasThumbnail,
    CanvasLabel,
    Vault,
    Manifest,
    ManifestLabel,
    IIIFCanvas,
  },
  data() {
    return {
      canvasIndex: 1
    }
  },
  methods: {
    next() {
      this.canvasIndex += 1;
    },
    prev() {
      this.canvasIndex -= 1;
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
