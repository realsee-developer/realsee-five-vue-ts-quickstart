<script setup lang="ts">
import { FiveProvider } from '@realsee/five/vue';
import work from '@realsee/open-works/virtual/81RojBlJQdVTglNNMr/work.json';
import ResponsiveFiveCanvas from './components/ResponsiveFiveCanvas.vue';
import ToggleFiveModeButton from './components/ToggleFiveModeButton.vue';

// five初始化参数请参考
// https://unpkg.com/@realsee/five@latest/docs/interfaces/five.FiveInitArgs.html
const fiveInitArgs = {
  imageOptions: {
    // 初始512开启动态瓦片加载，可提升点位加载速度
    size: 512,
  },
  textureOptions: {
    // 关闭模型贴图自动缩放，加载高精度模型贴图，
    // 注意，低性能的机器大模型场景容易崩溃
    autoResize: false,
  },
};
</script>

<template>
  <FiveProvider :fiveInitArgs="fiveInitArgs" :initialWork="work">
    <ResponsiveFiveCanvas />
    <ToggleFiveModeButton />
  </FiveProvider>
</template>
