<script setup>

const props = defineProps([
  'tabs',
  'onTabChange',
]);
const switchBlock = ref(null);
const tabElements = ref([]);
const activeTab = ref();
const indicatorWidth = ref(0);
const indicatorOffset = ref(0);
const initialRender = ref(true);
const router = useRouter()

const setTab = (index) => {
  activeTab.value = index;

  updateIndicatorPosition();
  if (props.onTabChange) {
    props.onTabChange(activeTab.value);
  }
};
const updateIndicatorPosition = () => {
  if (document.querySelector('.switch')) {
    let activeTabElement = tabElements.value[activeTab.value];
    if (activeTabElement?.offsetWidth === 0) {
      const switchBlockRef = switchBlock.value;
      const switchTabElements = switchBlockRef.querySelectorAll('.switch__tab');
      activeTabElement = switchTabElements[activeTab.value];
    }
    indicatorWidth.value = activeTabElement?.offsetWidth;
    indicatorOffset.value = activeTabElement?.offsetLeft;
  }
}
const handleWindowResize = () => {
  updateIndicatorPosition();
};

const indicatorStyles = computed(() => {
  return {
    width: `${indicatorWidth.value}px`,
    transform: `translateX(${indicatorOffset.value}px)`
  };
});

onMounted(() => {
  const currentQuery = router.currentRoute.value.query;
  if (currentQuery?.type === props.tabs[0].toLowerCase() || currentQuery?.type === props.tabs[1].toLowerCase()) {
    activeTab.value = currentQuery?.type ? (currentQuery?.type === props.tabs[0].toLowerCase() ? 0 : 1) : 0
  } else {
    activeTab.value = 0
  }
  updateIndicatorPosition();
  initialRender.value = false;
  window.addEventListener('resize', handleWindowResize);
});
</script>

<template>
  <div ref="switchBlock" class="switch">
    <p v-for="(tab, index) in tabs" ref="tabElements"
       class="regular-m"
       :class="{ 'switch__tab': true, 'switch__tab_active': index === activeTab}"
       @click="setTab(index)">{{ tab }}</p>
    <span v-if="!initialRender" :style="indicatorStyles" class="switch__tab-indicator"></span>
  </div>
</template>

<style lang="sass">
@use "/const/color"
@use "/const/mixin"

.switch
  display: flex
  width: fit-content
  height: fit-content
  padding: 4px 8px
  justify-content: center
  align-items: center
  align-self: stretch
  border: 1px solid color.$light-gray
  gap: 4px
  position: relative
  border-radius: 6px
  background: color.$white
  z-index: 0

.switch__tab
  text-transform: capitalize
  margin: 0
  display: flex
  padding: 2px 8px
  justify-content: center
  align-items: center
  flex: 1 0 0
  width: 100%
  border-radius: 6px
  color: color.$gray
  cursor: pointer
  white-space: nowrap

.switch__tab_active
  border-radius: 4px
  color: color.$black
  @include mixin.transition
  z-index: 2

.switch__tab-indicator
  position: absolute
  top: 4px
  left: 0
  height: 22px
  border-radius: 4px
  @include mixin.transition
  background: color.$light-gray
</style>
