<script setup lang="ts">

const props = defineProps({
  buttonText: {
    type: Number,
    required: true
  },
  onClick: {
    type: Function,
    required: true,
    default: () => {}
  }
});
  function handleClick(page: number) {
  props.onClick(page);
}
</script>

<template>
<button type="button" @click="handleClick(buttonText)">{{buttonText}}</button>
</template>

<style scoped>
button {
  width: 3rem;
  font-size: larger;
  font-weight: 600;
  font-family: "Times New Roman", Times, serif;
}
</style>
