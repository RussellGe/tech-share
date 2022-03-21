<script setup lang="ts">
import { ref, effect } from 'vue'
const app = ref(null)
const count = ref(0)

const renderer = (domString, container) => {
    if(container.value) {
      container.value.innerHTML = domString
    }
}
const countAdd = () => count.value++;

effect(() => {
    renderer(`<h1>count: ${count.value}</h1>`, app)
})

</script>

<template>
 <div class="flex space-x-10 items-center">
     <span class="flex items-center" ref='app'></span>
     <div class="border rounded w-10 h-5" @click='countAdd'>Add</div> 
 </div>
</template>
