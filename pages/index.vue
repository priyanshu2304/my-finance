<template>
  <div></div>
</template>

<script>
export default {
  name: 'IndexPage',
  mounted() {
    this.$router.push({
      path: '/calculator',
    })
  },
}
</script>
