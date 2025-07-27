<script setup>
const props = defineProps([
  'title',
  'description',
])
const statusText = ref('Не просмотрено')
const modalOpen = ref(false)

function handleClickTax(evt) {
  if (!evt.target.closest('.tax').classList.contains('tax-visible')) {
    evt.target.closest('.tax').classList.add('tax-visible')
  }
  statusText.value = 'Просмотрено'
  modalOpen.value = true
}

function closeModal() {
  modalOpen.value = false
}
</script>

<template>
  <Teleport to="body">
    <LkTaxModal v-show="modalOpen" :title="title" :description="description" @close="closeModal"/>
  </Teleport>
  <div class="tax" @click="handleClickTax">
    <div class="tax__status-block">
      <IconStatus class="tax__status-icon" filled/>
      <p class="tax__status-text">{{ statusText }}</p>
    </div>
    <p class="tax__title">
      {{ title }}
    </p>
  </div>
</template>

<style lang="sass">
@use "/const/color"
@use "/const/mixin"
.tax
  border-radius: 16px
  padding: 10px 20px
  box-sizing: border-box
  width: 310px
  cursor: pointer
  @include mixin.transition
  border: 1px solid color.$red

.tax__status-block
  display: flex
  flex-direction: row
  align-items: center
  gap: 6px

.tax__status-icon path
  stroke: color.$red

.tax-visible
  border: 1px solid color.$light-gray
  background-color: color.$light-gray-2

  .tax__status-icon path
    stroke: color.$gray

.tax__title
  -webkit-line-clamp: 2
  display: -webkit-box
  -webkit-box-orient: vertical
  overflow: hidden
  text-overflow: ellipsis
</style>