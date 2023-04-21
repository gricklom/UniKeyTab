<script setup>
import { ref, computed } from 'vue'
import glyphsJson from './assets/glyphs.json'

const emit = defineEmits(['glyph'])

const filterChar = ref('')
const glyphs = ref(glyphsJson)

const filteredGrlyphs = computed(() => {
    if (filterChar.value == '') {
        return glyphs.value
    } else {
        return glyphs.value.filter((g) => g.baseChar === filterChar.value.toLowerCase())
    }
})

function glyphClick(glyph) {
    emit('glyph', glyph.glyph)
}
</script>

<template>
    <p>Type a character to show only characters based on it.</p>
    <scale-text-field id="filterField" 
        v-model="filterChar"
        label="Base char"
        max-length="1">
    </scale-text-field>
    <scale-table striped>
        <table>
            <caption v-if="filterChar">
                Text elements based on character <strong>{{ filterChar }}</strong>.
            </caption>
            <thead>
                <tr>
                    <th aria-disabled="true">Text element</th>
                    <th aria-disabled="true">Name</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="g in filteredGrlyphs">
                    <td>
                        <scale-button size="small" @click="() => glyphClick(g)">
                            {{ g.glyph }}
                        </scale-button>
                    </td>
                    <td>{{ g.name }}</td>
                </tr>
            </tbody>
        </table>
    </scale-table>
</template>

<style>
#filterField {
    margin: 5em;
}
td {
    text-align: left;
}
</style>