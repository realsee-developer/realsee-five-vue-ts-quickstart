<script setup lang="ts">
import { Five } from '@realsee/five';
import { useFiveCurrentState } from '@realsee/five/vue';
import { computed } from 'vue';

const [currentState, setState] = useFiveCurrentState();

const text = computed(() =>
  currentState.value.mode === Five.Mode.Floorplan
    ? '切换到全景态'
    : '切换到模型态'
);

const onClick = () => {
  if (currentState.value.mode === Five.Mode.Panorama) {
    setState({ mode: Five.Mode.Floorplan });
    return;
  }

  if (currentState.value.mode === Five.Mode.Floorplan) {
    setState({ mode: Five.Mode.Panorama });
    return;
  }
};
</script>

<template>
  <button @click="onClick" class="btn">{{ text }}</button>
</template>

<style scoped>
.btn {
  position: absolute;
  top: 20px;
  left: 50%;
  transform: translateX(-50%);
  z-index: 10001;
  padding: 0 10px;
  height: 30px;
}
</style>
