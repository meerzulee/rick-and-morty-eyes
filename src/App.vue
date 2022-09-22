<script >


const angle = (cx, cy, ex, ey) => {
  const dy = ey - cy;
  const dx = ex - cx;
  const rad = Math.atan2(dy, dx);
  const deg = rad * 180 / Math.PI;
  return deg
}

import { ref } from 'vue'
export default {
  setup() {

    const degr = ref(0)
   
    document.addEventListener('mousemove', (e) => {
      // console.log(e);
      const rect = document.getElementById('anchor').getBoundingClientRect();
      const anchorX = rect.left + rect.width / 2;
      const anchorY = rect.top + rect.height / 2;
      const mouseX = e.clientX;
      const mouseY = e.clientY;


      degr.value = angle(mouseX, mouseY, anchorX, anchorY)
      
     

    })
    return { degr }
  }
}
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
</script>

<template>
  <div>
    <main>
      <img src="./assets/morty.png" id="anchor" :style="{filter: `hue-rotate(${degr+90}deg)`}">
      
      <div id="eyes">
        <img src="./assets/eye.png" class="eyes" :style="{top: '130px', right: '34px', transform: `rotate(${degr+90}deg)`}">
        <img src="./assets/eye.png" class="eyes" :style="{top: '-167px', right: '-167px', transform: `rotate(${degr+90}deg)` }">
        <img src="./assets/eye.png" class="eyes" :style="{top: '-173px', right: '-265px', transform: `rotate(${degr+90}deg)` }">
        <img src="./assets/eye.png" class="eyes" :style="{top: '150px',right: '174px', transform: `rotate(${degr+90}deg)`}">

      </div>
    </main>
  </div>
</template>

<style >
body {
  background-color: black;
  color: white;
  padding: 0;
  margin: 0;
}

main {
  display: grid;
  place-items: center;
  min-height: 100vh;
  position: relative;
}

#eyes,
#eyes img {
  position: absolute;
}
</style>
