<script setup lang="ts">
import { onMounted, ref } from "vue";
import { faceH5 } from "./face-h5";

// 依赖注入
const faceIm = ref<faceH5>();
const faceEl = ref();

onMounted(() => {
  faceIm.value = new faceH5({ videoEl: faceEl.value });
});

function startRecord() {
  faceIm.value
    ?.startRecord()
    .then((res) => {
      console.log("startRecord=============");
      console.log(res);
      console.log("startRecord=============");
    })
    .catch((err) => {
      console.error(err);
    });
}
function stopRecord() {
  faceIm.value
    ?.stopRecord()
    .then((res) => {
      console.log("stopRecord=============");
      console.log(res);
      console.log("stopRecord=============");
    })
    .catch((err) => {
      console.error(err);
    });
}
</script>

<template>
  <div>
    <video
      ref="faceEl"
      src=""
      x5-video-player-type="h5"
      playsinline
      webkit-playsinline
    ></video>
    <button @click="startRecord">开始录制</button>
    <button @click="stopRecord">停止录制</button>
  </div>
</template>

<style scoped>
video {
  width: 240px;
  height: 300px;
}
</style>
