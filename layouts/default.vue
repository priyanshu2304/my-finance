<template>
  <div>
    <heading-Component />
    <div class="mf-main-page"><Nuxt /></div>
  </div>
</template>

<script>
import Heading from '~/components/Common/Header.vue'
export default {
  components: {
    headingComponent: Heading,
  },
}
</script>

<style lang="scss" scoped>
.mf-main-page {
  max-width: 1110px;
  margin: 50px auto;
  width: 100%;
}
</style>
