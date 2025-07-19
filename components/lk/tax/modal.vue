<script setup>
const props = defineProps([
  'title',
  'description',
  'open'
])
const closeModal = ref(true)
</script>

<template>
  <div style="position: absolute;top: 0;left: 0;bottom: 0;">
    <div class="overlay-tax-modal"></div>
    <div class="tax-modal">
      <IconCross class="tax-modal__close-button" filled @click="$emit('close')"/>
      <p class="tax-modal__title bold-xxxl">{{ title }}</p>
      <p class="tax-modal__description regular-m">{{ description }}</p>
    </div>
  </div>
</template>

<style lang="sass">
@use "/const/color"
@use "/const/mixin"
.tax-modal__close-button
  width: 24px
  height: 24px
  min-width: 24px
  min-height: 24px
  cursor: pointer
  @include mixin.transition

.tax-modal
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

.overlay-tax-modal
  width: 100vw
  height: 100vh
  opacity: 0.5
  background-color: color.$gray
  position: fixed
  top: 0
  left: 0
  z-index: 9

.tax-modal__description
  height: 100%
  overflow: auto
  padding-right: 20px

  &::-webkit-scrollbar
    width: 4px

  &::-webkit-scrollbar-track
    background: color.$hr-gray

  &::-webkit-scrollbar-thumb
    background: color.$scroll-gray
    border-radius: 6px

.tax-modal__close-button:hover
  transform: rotate(180deg)
</style>