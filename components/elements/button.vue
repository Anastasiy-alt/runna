<script setup>
const props = defineProps([
  'text'
])
</script>

<template>
  <button class="btn medium-m">
    {{ text }}
  </button>
</template>

<style lang="sass">
@use "/const/color"
@use "/const/mixin"

.btn
  margin: 0
  width: fit-content
  padding: 10px
  box-sizing: border-box
  border: 0
  color: color.$white
  border-radius: 8px
  background-color: color.$red
  @include mixin.transition
  cursor: pointer

.btn:hover
  background-color: color.$red-hover
</style>