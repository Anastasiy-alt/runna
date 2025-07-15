<script setup>

</script>

<template>
<div class="right">
  <div class="right__title">
    <p class="regular-xxl">Затраты</p>
    <ElementsSwitch :tabs="['день', 'неделя', 'месяц', 'год']"/>
  </div>
  <ElementsGraph />
</div>
</template>

<style lang="sass">
.right
  width: 100%
.right__title
  display: flex
  flex-direction: row
  justify-content: space-between
</style>