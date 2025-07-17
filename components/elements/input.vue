<script setup>
const props = defineProps([
  "placeholder",
  "type", // Тип инпута
  "error", // Отображение ошибки в инпуте, True/False
  "errorText", // Текст ошибки
  "label", // Текст под инпутом
  "disabled",
  "required", // required свойство в инпут, True/False
]);
const emits = defineEmits(['input'])
const visibleClear = ref(false);
const focusInput = ref(false)

const ClearInput = () => {
  const inputField = document.querySelector(".input__field");
  inputField.value = "";
  visibleClear.value = false;
};

const CheckInput = () => {
  const inputField = document.querySelector(".input__field");
  if(!props.error){
    if (inputField.value !== "") {
      visibleClear.value = true;
    } else {
      visibleClear.value = false;
    }
  }
  emits('input', inputField.value)
};

const UnfocusInput = () => {
  focusInput.value = !focusInput.value
};

const OnClickInput = () => {
  const inputField = document.querySelector(".input__field");
  if (inputField.value !== "") {
    if(!props.error){
      visibleClear.value = true;
    }
    focusInput.value = false
  }
};
</script>
<!--id="input-email"-->
<template>
  <div class="input">
    <input
        :class="{ input__field_error: error }"
        class="input__field font-text_small"
        :type="type"
        :placeholder="placeholder"
        :disabled="disabled"
        :required="required"
        ref="inputField"
        @input="CheckInput"
        @click="OnClickInput"
        @blur="UnfocusInput"
    />
<!--    <IconError v-if="error" class="input__error" filled />-->
<!--    <IconCloseSmall-->
<!--        @click="ClearInput"-->
<!--        class="input__clear"-->
<!--        :class="{ input__clear_visible: visibleClear, input__clear_unfocus: focusInput }"-->
<!--        filled-->
<!--    />-->
    <label
        :class="{ input__label_error: error }"
        class="input__label font-input-label"
        for="input-email"
    >
      {{ errorText ? errorText : label }}
    </label>
  </div>
</template>

<style lang="sass">
@use "/const/color"
@use "/const/mixin"

.input
  position: relative
  box-sizing: border-box
  display: flex
  flex-direction: column
  gap: 4px
.input__field
  box-sizing: border-box
  max-height: 51px
  padding: 15px 48px 15px 12px
  border-radius: 16px
  background-color: color.$white
  color: color.$gray
  outline: none
.input__field::placeholder
  color: color.$gray
.input__label
  color: color.$gray
.input__error
  position: absolute
  z-index: 5
  top: 26px
  right: 12px
  transform: translateY(-50%)
.input__error path
  stroke: color.$red
.input__clear
  display: none
  cursor: pointer
  position: absolute
  z-index: 3
  top: 26px
  right: 12px
  transform: translateY(-50%)
  width: 20px
  height: 20px
  @include mixin.transition
.input__clear path
  stroke: black

.input__clear_visible
  display: block
.input__clear_unfocus
  opacity: 0

.input__field_error
  color: color.$red
  border: 1px solid color.$red
.input__label_error
  color: color.$red

.input__field:disabled::placeholder, .input__field:disabled ~ .input__label
  color: color.$gray
</style>
