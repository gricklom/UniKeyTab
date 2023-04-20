<script setup>
import { ref } from 'vue'
import GlyphTab from './GlyphTab.vue';

var selectedElements = ref('')

function glyphClicked(glyph) {
    selectedElements.value += glyph
}

function copyElements() {
  navigator.clipboard.writeText(selectedElements.value)
  console.log(selectedElements.value)
}
</script>

<template>
  <main>
      <h1 class="scl-font-variant-heading-1">UniKeyTab</h1>
      <p>A table to help entering Unicode characters. This table lists only characters specified in DIN 91379.</p>
      <scale-card>        
        <p>Clicking the buttons in the table below will add to the selected text elements. A click on <em>Copy</em> copies these elements to your clipboard.</p>
        <div class="container-2-col">
          <scale-text-field id="unikeys" 
              v-model="selectedElements"
              label="Selected text elements"
              readonly>
          </scale-text-field>
          <scale-button @click="() => copyElements()">Copy</scale-button>
        </div>      
        <GlyphTab @glyph="(g) => glyphClicked(g)"/>
      </scale-card>    
  </main>  
</template>

<style>

main {
  display: grid;
  text-align: left;
  font-family: sans-serif;
}
.container-2-col {
  display: grid;
  grid-template-columns: auto min-content;
  column-gap: 1em;
  text-align: right;
  margin-top: 1em;
  margin-bottom: 1em;
}
</style>
