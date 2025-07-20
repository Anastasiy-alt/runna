<script setup>
const props = defineProps([
  'cost',
  'title',
  'graph'
])
</script>

<template>
  <div class="right">
    <div class="right__title">
      <p class="regular-xxl">{{ title }}</p>
      <ElementsSwitch :tabs="['день', 'неделя', 'месяц', 'год']"/>
    </div>
    <div class="right__title">
      <p class="right__cost medium-xl">{{ cost }}</p>
      <p class="right__cost right__cost_cal regular-m">Календарь</p>
    </div>
    <ElementsGraph :graph="graph" class="right__graph"/>
  </div>
</template>

<style lang="sass">
@use "/const/color"


.right
  width: 100%
  display: flex
  flex-direction: column
  gap: 8px

.right__title
  display: flex
  flex-direction: row
  justify-content: space-between

.right__cost
  padding: 2px 8px
  border: 1px solid color.$light-gray
  border-radius: 6px

.right__graph
  margin-top: 6px

.right__cost_cal
  padding: 4px 8px
  color: color.$gray
  display: flex
  flex-direction: row
  align-items: center
</style>