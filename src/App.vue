<script setup>
import GlyphTab from './GlyphTab.vue';
</script>

<template>
  <main>  
  <div>
    <h1 class="scl-font-variant-heading-1">UniKeyTab</h1>
    <p>A table to help entering Unicode characters. This table lists only characters specified in DIN 91379.</p>
    <scale-card>
      <GlyphTab />
    </scale-card>    
  </div>
  </main>  
</template>

<style>

main {
  display: grid;
  place-items: center;
  height: 100vh;
  font-family: sans-serif;
}

</style>
