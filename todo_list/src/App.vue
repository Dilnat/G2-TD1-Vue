<script setup lang="ts">
let texte =  "un texte qui s'affiche";
</script>


<template>
  <div id="wrapper">
    <h1>TODO liste</h1>
    <p>{{texte}}</p>
    <a v-bind:href="texte">Test</a>
  </div>
</template>

<style scoped>
</style>