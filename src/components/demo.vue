<template>
  <canvas id="demo"></canvas>
</template>

<script lang="ts" setup>
import * as BABYLON from '@babylonjs/core/Legacy/legacy'; // 全部引入
import { Engine, Scene } from '@babylonjs/core'; // 只引入使用到的类
// import '@babylonjs/materials/legacy/legacy'; // 引入其他模块中的所有类，例如materials
import { onMounted } from 'vue';
class BabylonScene {
  scene: Scene;
  engine: Engine;
  constructor(private canvas: HTMLCanvasElement) {
    this.engine = new BABYLON.Engine(this.canvas, true);
    this.scene = this.CreateScene();
    this.engine.runRenderLoop(() => {
      this.scene.render();
    });
  }

  CreateScene(): Scene {
    const scene = new BABYLON.Scene(this.engine);
    return scene;
  }
}
onMounted(() => {
  const canvas = document.getElementById('demo') as HTMLCanvasElement;
  // const canvas = document.querySelector("canvas");
  const demo = new BabylonScene(canvas);
});

</script>