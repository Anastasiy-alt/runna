<script setup>
const props = defineProps([
  'corr',
  'analysis',
  'season'
])

const modalOpen = ref(false)

function closeModal() {
  modalOpen.value = false
}

function handleOpenModal() {
  modalOpen.value = true
}
</script>

<template>
  <ElementsModal class="request-modal" v-show="modalOpen" @close="closeModal">
    <p class="request-modal__title medium-xl">Запись к специалисту</p>
    <ElementsInput :required="true" :placeholder="'Введите ваше имя'" :type="'text'"/>
    <ElementsInput :required="true" :placeholder="'Введите ваш e-mail. Мы направим ссылку на Zoom'" :type="'email'"/>
    <ElementsTextarea :required="true" :placeholder="'Опишите проблему'" :type="'textarea'"/>
    <ElementsButton type="submit" class="request-modal__button" text="Отправить заявку"/>
  </ElementsModal>
  <article class="left">
    <p class="medium-xl">{{ analysis.title }}</p>
    <div class="left__analyze">
      <p class="left__analyze-text regular-s">{{ analysis.value }}</p>
    </div>
    <div class="corr" v-if="corr">
      <p class="corr__value medium-m">{{ corr.value }}</p>
      <p class="corr__text regular-s">{{ corr.title }}</p>
    </div>
    <div class="season">
      <p class="medium-m">Предложения</p>
      <div class="season__block">
        <ElementsItem v-for="(item, idx) in season"
                      :style="`z-index: ${season.length - idx}`"
                      :title="item.title"
                      :description="item.description"
        />
      </div>
    </div>
    <ElementsButton @click="handleOpenModal" text="Консультация со специалистом"/>
  </article>
</template>

<style lang="sass">
@use "/const/color"
@use "/const/mixin"

.request-modal__title
  text-align: center

.request-modal__button
  margin: 0 auto

.left
  width: 450px
  display: flex
  flex-direction: column
  gap: 16px
  background: color.$bg-gray
  border-radius: 8px
  padding: 20px
  box-sizing: border-box
  height: fit-content

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