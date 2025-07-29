<script setup>
const dataFirst = [
  'Главная',
  'Новый платёж',
  'Выписка',
  'Сервисы'
]

const dataSecond = [
  'Кредитные продукты',
  'Депозиты',
  'Бухгалтерия',
  'Риски'
]

const dataThird = [
  'Письма',
  'Тариф',
  'ВЭД',
  'Благотворительность'
]
</script>

<template>
  <div class="sidebar">
    <div>
    <p class="sidebar__title">Альфа-Банк</p>
    <ul class="sidebar__list">
      <li class="regular-l sidebar__list-item" v-for="i in dataFirst">{{ i }}</li>
    </ul>
    <ul class="sidebar__list sidebar__list_second">
      <li class="regular-l sidebar__list-item" v-for="i in dataSecond">{{ i }}</li>
      <a href="/analytics" class="regular-l sidebar__list-item">Аналитика</a>
    </ul>
    <ul class="sidebar__list">
      <li class="regular-l sidebar__list-item" v-for="i in dataThird">{{ i }}</li>
    </ul>
    </div>
    <div>
    <hr class="sidebar__hr">
    <ul class="sidebar__list sidebar__list_bottom">
      <li class="regular-l sidebar__list-item">Приведи друга</li>
      <li class="regular-l sidebar__list-item">Клуб клиентов</li>
    </ul>
    <IconSettings class="sidebar__icon" filled />
    </div>
  </div>
</template>

<style lang="sass">
@use "/const/color"

.sidebar
  width: 290px
  background-color: #C9C9C9
  position: relative
  box-sizing: border-box
  padding: 40px 10px
  font-family: Inter, serif
  height: auto
  display: flex
  flex-direction: column
  justify-content: space-between

.sidebar__title
  font-family: Inter, serif
  font-weight: 500
  font-style: normal
  font-size: 24px
  color: #FFF
  text-align: center
  margin-bottom: 30px

.sidebar__list
  list-style: none
  margin: 0
  padding: 0
  display: flex
  flex-direction: column
  gap: 10px

.sidebar__list_second
  margin-left: 30px

.sidebar__list-item
  padding: 6px 10px
  color: #161616
  text-align: left
  cursor: pointer

.sidebar__hr
  border: 1px solid #969696
  margin: 100px 0 30px
.sidebar__list_bottom
  margin-bottom: 25px
.sidebar__icon
  width: 24px
  height: 24px
  min-width: 24px
  min-height: 24px
  padding-left: 6px

</style>