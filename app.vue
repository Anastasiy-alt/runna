<template>
  <div class="page">
    <img class="lk-button" src="/assets/user.png" @click="() => navigateTo('/')" alt="">
    <div class="sidebar">
      <img src="/assets/sidebar.png" alt="">
      <div class="analytics-button" @click="() => navigateTo('analytics')"></div>
    </div>
    <NuxtPage class="page-nuxt"/>
  </div>

</template>

<style lang="sass">
@import url('https://fonts.googleapis.com/css2?family=Inter:ital,opsz,wght@0,14..32,100..900;1,14..32,100..900&display=swap')
p
  font-family: Inter, serif
  margin: 0
  padding: 0
  letter-spacing: 0
.nuxt-icon
  margin: 0 !important
.page
  display: flex
  flex-direction: row
  gap: 20px

.sidebar
  position: relative

.analytics-button
  position: absolute
  top: 510px
  left: 40px
  height: 50px
  width: 250px
  cursor: pointer

.lk-button
  position: absolute
  top: -2px
  right: 0
  height: 80px
  object-fit: contain
  cursor: pointer

.page-nuxt
  margin-top: 100px

.regular-s
  font-weight: 400
  font-size: 12px
  line-height: 16px

.regular-m
  font-weight: 400
  font-size: 14px
  line-height: 18px

.regular-xxl
  font-weight: 400
  font-size: 20px
  line-height: 30px

.medium-m
  font-weight: 500
  font-size: 14px
  line-height: 18px

.medium-l
  font-weight: 500
  font-size: 16px
  line-height: 24px

.medium-xl
  font-weight: 500
  font-size: 18px
  line-height: 28px

.medium-value
  font-weight: 500
  font-size: 40px
  line-height: 40px

.bold-l
  font-weight: 700
  font-size: 16px
  line-height: 24px

.bold-xxxl
  font-weight: 700
  font-size: 24px
  line-height: 30px

.bold-xxl
  font-weight: 700
  font-size: 20px
  line-height: 30px

.block
  display: flex
  flex-direction: row
  gap: 10px
</style>
<script setup lang="ts">
</script>