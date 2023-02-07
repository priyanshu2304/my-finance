<template>
  <div class="mf-header__container">
    <div class="rm-header__title">Finance calculator</div>
  </div>
</template>

<script>
export default {
  name: 'Heading-component',
}
</script>

<style lang="scss" scoped>
.mf-header__container {
  display: flex;
  justify-content: center;
  padding: $t-marg__pad * 2 0;
  border-bottom: 2px solid $light-teal;
  border-bottom-left-radius: 15px;
  border-bottom-right-radius: 15px;
  background: $light-teal;

  .rm-header__title {
    font-size: $font-size-h3-p;
    font-weight: $font-ebold-weight;
  }
}
</style>
