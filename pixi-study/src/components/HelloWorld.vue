<script setup lang="ts">
import { ref, onMounted } from 'vue'
import * as PIXI from 'pixi.js'

const pixiContainer = ref<HTMLElement | null>(null)

const app = new PIXI.Application({ width: window.innerWidth, height: window.innerHeight })
const sprite = PIXI.Sprite.from('pixi.png')
// Setup the position of the sprite
sprite.x = app.renderer.width / 2
sprite.y = app.renderer.height / 2

// Rotate around the center
sprite.anchor.x = 0.5
sprite.anchor.y = 0.5
app.stage.addChild(sprite)

onMounted(() => {
  pixiContainer.value?.appendChild(app.view)
})
</script>

<template>
  <div class="pixi" ref="pixiContainer" />
</template>

<style scoped>
.pixi {
  width: 100vw;
  height: 100vh;
  overflow: hidden;
}
</style>
