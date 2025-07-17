<template>
<!--  <Modal />-->

  <div class="block">
    <BlockRight cost="1 000 000, 00 ₽" />
    <BlockLeft :corr="'0,86'" />
  </div>
</template>

<style lang="sass">
@import url('https://fonts.googleapis.com/css2?family=Inter:ital,opsz,wght@0,14..32,100..900;1,14..32,100..900&display=swap')
p
  margin: 0
  padding: 0

.regular-s
  font-family: Inter, serif
  font-weight: 400
  font-size: 12px
  line-height: 16px
  letter-spacing: 0
.regular-m
  font-family: Inter, serif
  font-weight: 400
  font-size: 14px
  line-height: 18px
  letter-spacing: 0
.regular-xxl
  font-family: Inter, serif
  font-weight: 400
  font-size: 20px
  line-height: 30px
  letter-spacing: 0
.medium-m
  font-family: Inter, serif
  font-weight: 500
  font-size: 14px
  line-height: 18px
  letter-spacing: 0
.medium-xl
  font-family: Inter, serif
  font-weight: 500
  font-size: 18px
  line-height: 28px
  letter-spacing: 0

.block
  display: flex
  flex-direction: row
  gap: 10px
</style>
