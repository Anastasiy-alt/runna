<script setup>
const props = defineProps([
    'corr'
])
const data = {
  title: 'Анализ сезонности'
}
</script>

<template>
  <article class="left">
    <p class="medium-xl">{{ data.title }}</p>
    <div class="left__analyze">
      <p class="left__analyze-text regular-s">Общий спрос по рынку на товары категории «Спорт и отдых» вырос в апреле на 36% по
        сравнению с прошлым месяцем. Наибольшую прибыль вам приносят товары: «Палатка» и «Термос», количество продаж
        выросло на 48% по сравнению с прошлым месяцем.</p>
    </div>
    <div class="corr" v-if="corr">
      <p class="corr__value medium-m">{{corr}}</p>
      <p class="corr__text regular-s">Корреляция между финансовой ситуацией и сезонностью</p>
    </div>
    <div class="season">
      <p class="medium-m">Предложения</p>
      <div class="season__block">
        <ElementsItem style="z-index: 15" />
        <ElementsItem style="z-index: 14"  />
        <ElementsItem style="z-index: 13"  />
        <ElementsItem style="z-index: 12"  />
      </div>
    </div>
    <ElementsButton text="Консультация со специалистом" />
  </article>
</template>

<style lang="sass">
@use "/const/color"
@use "/const/mixin"


.left
  width: 450px
  display: flex
  flex-direction: column
  gap: 16px
  background: color.$bg-gray
  border-radius: 8px
  padding: 20px
  box-sizing: border-box

.left__analyze
  position: relative
  overflow: hidden
  border-radius: 4px 8px 8px 4px
  background-color: color.$white

.left__analyze::before
  content: ""
  position: absolute
  top: 0
  left: 0
  width: 2px
  height: 100%
  background-color: color.$red

.left__analyze-text
  padding: 10px 15px

.corr
  display: flex
  flex-direction: row
  gap: 10px
  align-items: center

.corr__value
  padding: 8px 12px
  box-sizing: border-box
  background: #AAEE39
  border-radius: 8px
  border: 1px solid color.$black

.corr__text
  max-width: 205px

.season
  display: flex
  flex-direction: column
  gap: 10px

.season__block
  display: grid
  grid-template-columns: repeat(2, 200px)
  gap: 10px
</style>