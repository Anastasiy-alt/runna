<script setup>
const props = defineProps([
  'title',
  'description',
])

</script>

<template>
  <ElementsModal>
    <p class="tax-modal__title bold-xxxl">{{ title }}</p>
    <p class="tax-modal__description regular-m">{{ description }}</p>
    <ElementsButton class="tax-modal__button" :text="'Исправлено'"/>
  </ElementsModal>
</template>

<style lang="sass">
@use "/const/color"
@use "/const/mixin"
.tax-modal__button
  margin: 0 auto

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
</style>