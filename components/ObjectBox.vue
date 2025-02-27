
<script setup lang="ts">
const props = defineProps({
  // You can add props here if needed
})
</script>

<template>
  <div 
    bg="orange-400" 
    shadow="sm" 
    rounded="lg" 
    p="4"
    text="white"
  >
    <slot></slot>
  </div>
</template>