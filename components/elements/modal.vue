<script setup>

</script>

<template>
  <div style="position: absolute;top: 0;left: 0;bottom: 0;">
    <div class="overlay-el-modal"></div>
    <div class="el-modal">
      <IconCross class="el-modal__close-button" filled @click="$emit('close')"/>
      <slot></slot>
    </div>
  </div>
</template>

<style lang="sass">
@use "/const/color"
@use "/const/mixin"

.el-modal__close-button
  width: 24px
  height: 24px
  min-width: 24px
  min-height: 24px
  cursor: pointer
  @include mixin.transition

.el-modal
  width: 522px
  max-height: 80vh
  border-radius: 32px
  position: fixed
  top: 50%
  left: 50%
  transform: translate(-50%, -50%)
  z-index: 10
  background-color: color.$white
  padding: 20px 15px
  display: flex
  flex-direction: column
  gap: 15px
  box-sizing: border-box

.overlay-el-modal
  width: 100vw
  height: 100vh
  opacity: 0.5
  background-color: color.$gray
  position: fixed
  top: 0
  left: 0
  z-index: 9

.el-modal__close-button:hover
  transform: rotate(180deg)
</style>