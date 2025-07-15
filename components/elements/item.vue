<script setup>
function toggleDescription(evt) {
  evt.target.closest('.item').classList.toggle('active')
}
</script>

<template>
  <div class="item">
    <div class="item__title" @click="toggleDescription">
      <p class="regular-m">Увеличить цветовую палитру термосов</p>
      <IconArrow class="item__icon"/>
    </div>
    <div class="item__description">
      <div class="item__description-block">
        <i></i>
        <ElementsTag/>
        <p class="item__description-text regular-m">Увеличение ... на , ... на n% m%</p>
      </div>
    </div>
  </div>
</template>

<style lang="sass">
@use "/const/color"
@use "/const/mixin"
.item__description-block
  overflow: hidden
  max-height: 0
  @include mixin.transition

.item
  z-index: 10
  padding: 10px
  box-sizing: border-box
  width: 200px
  border-radius: 8px
  position: relative
  cursor: pointer

.item__description::before
  content: ''
  position: absolute
  top: -56px
  left: 0
  width: 100%
  height: calc(100% + 56px)
  border-radius: 8px
  box-shadow: 0 3px 8px 0 #0000001F
  background-color: color.$white
  z-index: -1

.item__title
  cursor: pointer
  display: flex
  align-items: center
  justify-content: space-between

.item__icon
  width: 24px
  height: 24px
  min-width: 24px
  min-height: 24px
  @include mixin.transition

.item__description
  position: absolute
  top: calc(100%)
  left: 0
  max-height: 0
  z-index: -1
  @include mixin.transition

  i
    width: 180px
    display: block
    height: 1px
    background: color.$hr-gray
    margin: 0 auto
    box-sizing: border-box

  .item__description-text
    padding: 10px
    box-sizing: border-box

.item.active .item__description, .item.active .item__description-block
  max-height: 100px

.item.active .item__icon
  transform: rotate(180deg)

</style>