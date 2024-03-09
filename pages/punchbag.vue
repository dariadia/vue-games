<template>
  <v-file-input prepend-icon="mdi-camera" label="File input" accept="image/*" v-model="image" variant="solo-filled"></v-file-input>
  <div id="bag" :class="{ burst: isGameOn }"></div>
  <div id="bag-health">
    <div :style="{ width: health + '%' }"></div>
  </div>
  <div id="controls">
    <button @click="punch" v-show="!ended">Punch</button>
    <button @click="restart">Restart</button>
  </div>
</template>

<script setup>
const health = ref(100)
const image = ref("")

const isGameOn = computed(() => Boolean(image))
console.log(image)

const punch = () => {
  health -= 10
  if (health <= 0) isGameOn = false
}
const restart = () => {
  health = 100
  image = ""
}
</script>
