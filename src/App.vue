<script setup lang="ts">

</script>

<template>
  <h1 id="ravi">Ravi Chalahko</h1>
  <svg width="100" height="600">
    <defs>
      <linearGradient id="grad" gradientUnits="userSpaceOnUse" x1="50" x2="50" y1="50" y2="550">
        <stop offset="5%" stop-color="#547E96" />
        <stop offset="95%" stop-color="#373052" />
      </linearGradient>
    </defs>

    <path id="path" d="M 50 50 v 500" />
  </svg>
</template>

<style scoped>
#path {
  stroke: url(#grad);
  stroke-width: 3px;
}

#ravi {
  background-image: linear-gradient(180deg, #547E96 0%, #373052 100%);
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
  -webkit-text-stroke: 0.01em rgba(143,143,143,0.541);
  font-weight: 400;
}
</style>
