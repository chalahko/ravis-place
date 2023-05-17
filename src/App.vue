<script setup lang="ts">
  import Mode from './components/Mode.vue'
  import { onMounted } from 'vue';

  onMounted(() => {
    window.addEventListener('scroll', debounce(scrollUpdate, 250))
  })

  function scrollUpdate() {
    const timeline = document.getElementById('timeline')

    const scroll = document.documentElement.scrollTop

    if(timeline) {
      timeline.style.height = `calc(${scroll}px + 85vh)`
      console.log('setting height to ' + scroll)
    }
  }

  function debounce (method: Function, wait: number) {
    let timeout: number
    return () => {
      if (timeout) {
        clearTimeout(timeout)
      }
      timeout = setTimeout(method, wait)
    }
  }
</script>

<template>
  <Mode></Mode>
  <section style="background-color: #666699;">
    <p>
      shroud: campfire<br>
      torches: stars<br>
      carteneau: glyph
    </p>
  </section>
  <section style="background-color: #52527a;"></section>
  <section style="background-color: #3d3d5c;"></section>
  <div id="timeline"></div>
  <div id="dot"></div>
</template>

<style scoped>
#dot {
  position: absolute;
  top: 50px;
  right: 22vw;
  transform: translateX(50%) translateY(-50%);
  height: 10px;
  width: 10px;
  background-color: #e1e1e1;
  border-radius: 10px;
  border: 4px solid rgb(74, 57, 100);
  z-index: 15;
}

section {
  display: block;
  box-sizing: border-box;
  height: 100vh;
  width: 60vw;
  scroll-snap-align: start;
  padding: 20px;
}

#timeline {
  position: absolute;
  transform: translateX(50%);
  top: 50px;
  right: 22vw;
  width: 6px;
  height: 85vh;
  background-color: rgb(74, 57, 100);
  z-index: 10;
  transition: height .5s;
  transition-delay: .2s;
  border-radius: 6px;
}

path {
  stroke: #b33e36;
  stroke-linecap: round;
  stroke-width: 3px;
  fill: none;
}

#ravi {
  background-image: linear-gradient(0deg, #b33e36 0%, #BF9630 100%);
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
  -webkit-text-stroke: 0.01em rgba(33,33,33,0.541);
  font-weight: 400;
}

circle {
  fill: #d9d9d9;
  stroke: #b33e36;
  stroke-width: 3px;
}
</style>
