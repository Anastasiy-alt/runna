<script setup>
const props = defineProps([
  'date',
  'number',
  'status',
  'value'
])
</script>

<template>
  <div class="pay">
    <div class="pay__header">
      <div class="pay__header-info">
        <p class="pay__number medium-m">{{ number }}</p>
        <p class="pay__date regular-s">от {{ date }}</p>
      </div>
      <p class="pay__status regular-s" :class="status === 'Ожидает оплаты' ? 'pay__status_gray' : 'pay__status_red'">
        {{ status }}</p>
    </div>
    <div class="pay__content">
      <p class="pay__value medium-l">{{ value }}</p>
      <ElementsButton :text="'Оплатить'"/>
    </div>
  </div>
</template>

<style lang="sass">
@use "/const/color"

.pay
  width: 352px
  border-radius: 16px
  padding: 12px
  gap: 15px
  display: flex
  flex-direction: column
  background: color.$white

.pay__date
  color: color.$gray

.pay__header, .pay__content
  display: flex
  flex-direction: row
  justify-content: space-between

.pay__content
  align-items: center

.pay__header-info
  display: flex
  flex-direction: column
  gap: 1px

.pay__status_gray
  color: color.$gray

.pay__status_red
  color: color.$red
</style>