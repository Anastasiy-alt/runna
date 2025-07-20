<script setup>
const fileInput = ref(null);
const uploaded = ref(false);
const fileName = ref('');

const selectFile = () => {
  fileInput.value.click();
};

const handleFileUpload = (event) => {
  const file = event.target.files[0];
  if (file) {
    fileName.value = file.name;
    uploaded.value = true;
  }
};
</script>

<template>
  <input type="file" ref="fileInput" @change="handleFileUpload" style="display: none;" />
  <button class="upload-button" :class="{'upload-button__uploaded' : uploaded}" @click="selectFile">
    {{ uploaded ? fileName + ' загружен' : 'Загрузить финансовую отчётность' }}
    <IconUpload filled v-show="!uploaded" />
  </button>
</template>

<style lang="sass">
@use "/const/color"
@use "/const/mixin"
.upload-button
  @include mixin.transition
  border-radius: 8px
  cursor: pointer
  padding: 10px
  border: 1px solid color.$light-gray
  background-color: color.$light-gray-2
  color: color.$input-gray
  width: fit-content
  svg
    margin-left: 10px
.upload-button:hover
  border: 1px solid color.$gray
.upload-button__uploaded
  background-color: color.$white
</style>