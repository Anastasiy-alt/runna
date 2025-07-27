<script setup>
// const props = defineProps([
//   'title',
//   'description',
// ])

</script>

<template>
  <ElementsModal>
    <p class="tax-modal__title bold-xxxl">Что будет в случае неуплаты налога на прибыль?</p>
    <p class="tax-modal__description regular-m">Неуплата или неполная уплата сумм налога (сбора, страховых взносов) влечет взыскание штрафа в размере 20 процентов от неуплаченной суммы налога (сбора, страховых взносов).</p>
    <ElementsButton class="tax-modal__button" :text="'Понятно'"/>
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