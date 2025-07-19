<script setup>
const props = defineProps([
  'title',
  'value',
  'all'
])
</script>

<template>
  <div class="bills">
    <div class="bills__title-block">
      <i v-if="!all" class="bills__deco"></i>
      <i v-if="all" class="bills__deco-all"><i class="bills__deco-all-inner"></i><i
          class="bills__deco-all-inner"></i></i>
      <p class="bills__title regular-m">{{ title }}</p>
    </div>
    <p class="bills__value medium-xl">{{ value }}</p>
  </div>
</template>

<style lang="sass">
@use "/const/color"
.bills
  min-width: 173px
  max-width: fit-content
  height: 94px
  border-radius: 16px
  display: flex
  flex-direction: column
  justify-content: space-between
  padding: 10px 20px
  box-sizing: border-box
  background: color.$light-gray-2

.bills__deco
  width: 19px
  height: 9px
  border-radius: 2px
  background: color.$light-gray

.bills__deco-all
  display: flex
  flex-direction: row
  gap: 1px

.bills__deco-all-inner
  width: 9px
  height: 9px
  border-radius: 2px
  background: color.$light-gray

.bills__title-block
  display: flex
  flex-direction: row
  gap: 6px
  align-items: center
</style>