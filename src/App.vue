<template>
  <div id="container"></div>
  <canvas class="webgl"></canvas>
</template>
<script setup>
import { RouterLink, RouterView } from 'vue-router'
import { onMounted } from 'vue'
import * as THREE from 'three'

onMounted(() => {
  const scene = new THREE.Scene()

  //   console.log('container', container)
  //   container.appendChild(renderer.domElement)

  const sizes = {
    width: 800,
    height: 600,
  }

  const camera = new THREE.PerspectiveCamera(75, sizes.width / sizes.height)
  camera.position.z = 3

  const geometry = new THREE.BoxGeometry(1, 1, 1)
  const material = new THREE.MeshBasicMaterial({
    color: '#ff0000',
  })
  const mesh = new THREE.Mesh(geometry, material)

  let canvas = document.querySelector('.webgl')

  const renderer = new THREE.WebGLRenderer({
    canvas: canvas,
  })
  renderer.setSize(sizes.width, sizes.height)

  scene.add(mesh)
  scene.add(camera)

  renderer.render(scene, camera)
})
</script>

<style scoped lang="less"></style>
