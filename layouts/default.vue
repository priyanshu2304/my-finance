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
  padding: $t-marg__pad * 4;
}
</style>
