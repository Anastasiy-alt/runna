<script setup>

</script>

<template>
  <div class="tag">
    <IconStar class="tag__icon" filled/>
    <p class="medium-m">Прогноз</p>
  </div>

</template>

<style lang="sass">
@use "/const/color"
@use "/const/mixin"

.tag
  padding: 2px 8px
  box-sizing: border-box
  display: flex
  flex-direction: row
  gap: 10px
  border-radius: 8px
  border: 1px solid color.$hr-gray
  align-items: center
  width: fit-content
  margin: 10px 10px 0

.tag__icon
  width: 10px
  min-width: 10px
  height: 10px
  min-height: 10px
</style>