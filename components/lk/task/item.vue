<script setup>
const props = defineProps([
  'title',
  'status',
  'value',
  'date'
])

const display = ref(true)
const showAll = ref(false)
const statusRef = ref(props.status)

function close() {
  display.value = false
}

function show(evt) {
  showAll.value = !showAll.value
  if (statusRef.value === 'Не просмотрено') {
    statusRef.value = 'В процессе'
  }
}

const modalOpen = ref(false)

function handleClickTask(evt) {
  modalOpen.value = true
}

function closeModal() {
  modalOpen.value = false
}

const modalData = {
  title: 'Что будет в случае неуплаты налога на прибыль?',
  detail: 'Неуплата или неполная уплата сумм налога (сбора, страховых взносов) влечет взыскание штрафа в размере 20 процентов от неуплаченной суммы налога (сбора, страховых взносов).',
}
</script>

<template>
  <Teleport to="body">
    <LkTaskModal v-show="modalOpen" :close="closeModal" @close="closeModal"/>
  </Teleport>
  <div class="task" v-if="display" @click="show">
    <p class="medium-l task__title">{{ title }}
      <IconCross class="task__close" @click="close" v-if="status === 'Выполнено'"/>
    </p>
    <div class="task__status-block">
      <IconDone filled v-if="statusRef === 'Выполнено'" class="task__status-icon"/>
      <IconEye filled v-if="statusRef === 'Не просмотрено'" class="task__status-icon"/>
      <IconErorr filled v-if="statusRef === 'Не выполнено'" class="task__status-icon"/>
      <IconUimProcess filled v-if="statusRef === 'Обработка платежа'" class="task__status-icon"/>
      <IconProcess filled v-if="statusRef === 'В процессе'" class="task__status-icon"/>
      <p class="task__status regular-s">{{ statusRef }}</p>
    </div>
    <p class="bold-l" v-if="!showAll">{{ value }} ₽</p>
    <div class="task__block" :class="showAll ? 'show' : ''">
      <p class="medium-l" v-if="showAll">Сумма к оплате: {{ value }} ₽</p>
      <p class="regular-m task__date-block" v-if="showAll">
        <IconStatus class="task__date-icon" filled/>
        Срок оплаты: {{ date }}
      </p>
      <ElementsButton v-if="showAll" text="Сформировать новый счёт для уплаты налога"/>
    </div>
    <p class="regular-s task__question" v-if="showAll" @click="handleClickTask">
      <IconQuestion class="task__question-icon" filled/>
      Что будет в случае неуплаты налога?
    </p>
  </div>
</template>

<style lang="sass">
@use "/const/color"
@use "/const/mixin"
.task
  cursor: pointer
  width: 310px
  min-height: 96px
  top: 719px
  left: 667px
  border-radius: 16px
  border: 1px solid color.$light-gray
  padding: 10px 20px
  background-color: color.$light-gray-2
  box-sizing: border-box
  display: flex
  flex-direction: column
  gap: 6px

.task__title
  display: flex
  flex-direction: row
  justify-content: space-between

.task__close
  cursor: pointer
  @include mixin.transition

.task__close:hover
  transform: rotate(180deg)

.task__status, .task__question
  color: color.$gray

.task__status-icon
  width: 16px
  height: 16px
  min-width: 16px
  min-height: 16px

.task__status-block
  display: flex
  flex-direction: row
  gap: 5px
  align-items: center

.task__date-block
  display: flex
  flex-direction: row
  align-items: center
  gap: 5px

.task__date-icon
  width: 18px
  height: 18px
  min-width: 18px
  min-height: 18px

  path
    stroke: color.$red

.task__block
  display: flex
  flex-direction: column
  gap: 10px

.task__block.show
  padding: 16px 0

.task__question
  display: flex
  flex-direction: row
  align-items: center
  gap: 5px

.task__question-icon
  width: 16px
  height: 16px
  min-width: 16px
  min-height: 16px
</style>