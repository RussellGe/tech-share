<script setup lang="ts">
import { ref, effect } from "vue";
const count = ref(0);
const countAdd = () => {
    for(let i = 0; i < 100; i++) {
        count.value ++
    }
    runner()
}
const relatedValue = ref(0)
const runner = effect(() => {
    relatedValue.value += count.value
    console.log(count.value)
}, {
    scheduler: () => {
        console.log(1)
    }
})
</script>

<template>
  <div class="flex space-x-10 items-center">
    <div>{{count}}, {{relatedValue}}</div>
    <div class="border rounded w-10 h-5" @click="countAdd">Add</div>
  </div>
</template>
