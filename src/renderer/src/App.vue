<script setup>
import Versions from './components/Versions.vue'
import businessComponent from './components/business-component.vue';
import { ref, onMounted } from 'vue'
const ipcHandle = () => window.electron.ipcRenderer.send('ping')
</script>

<template>
  <div class="home viewer">
    <vc-viewer @ready="onViewerReady" :style="{ width: '100%', height: '100vh'}">
      <vc-entity
        ref="entity"
        :billboard="billboard"
        :position="{ lng: 108, lat: 32 }"
        :point="point"
        :label="label"
        @click="onEntityEvt"
        @mouseover="onEntityEvt"
        @mouseout="onEntityEvt"
      >
        <!-- <vc-graphics-rectangle
          :coordinates="[130, 20, 80, 25]"
          material="green"
        ></vc-graphics-rectangle> -->
      </vc-entity>
      <!-- <vc-layer-imagery>
        <vc-imagery-provider-osm></vc-imagery-provider-osm>
      </vc-layer-imagery> -->
      <vc-navigation></vc-navigation>
      <vc-measurements :offset="[0, 40]" :mainFabOpts="mainFabOpts"></vc-measurements>
      <business-component></business-component>
    </vc-viewer>
  </div>
</template>