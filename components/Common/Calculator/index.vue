<template>
  <div class="mf-option__container">
    <div v-for="items in options" :key="items.id">
      <NuxtLink class="mf-options__link" :to="items.path">
        <div class="mf-image">
          <img class="mf-image__container" :src="items.imageUrl" />
        </div>
        <div class="mf-options__title">{{ items.name }}</div>
      </NuxtLink>
    </div>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  data() {
    return {
      options: [
        {
          id: 1,
          name: 'Sip Calculator',
          path: '/calculator/sip-calculator',
          imageUrl: require('@/assets/images/dummy.png'),
        },
        {
          id: 2,
          name: 'CAGR Calculator',
          path: '/calculator/CAGR-calculator',
          imageUrl: require('@/assets/images/dummy.png'),
        },
        {
          id: 5,
          name: 'Loan Calculator',
          path: '/calculator/loan-calculator',
          imageUrl: require('@/assets/images/dummy.png'),
        },
        {
          id: 6,
          name: 'Retirement Calculator',
          path: '/calculator/retirement-calculator',
          imageUrl: require('@/assets/images/dummy.png'),
        },
        {
          id: 7,
          name: 'Investment Calculator',
          path: '/calculator/investment-calculator',
          imageUrl: require('@/assets/images/dummy.png'),
        },
        {
          id: 3,
          name: 'Goal Calculator',
          path: '',
          imageUrl: require('@/assets/images/dummy.png'),
        },
        {
          id: 4,
          name: 'Lump-Sum Calculator',
          path: '',
          imageUrl: require('@/assets/images/dummy.png'),
        },
      ],
    }
  },
}
</script>

<style lang="scss" scoped>
.mf-option__container {
  display: flex;
  justify-content: space-around;
}
.mf-image {
  display: flex;
  justify-content: center;
  .mf-image__container {
    height: 150px;
    width: 150px;
  }
}

.mf-options__title {
  display: flex;
  justify-content: center;
  transition: transform 0.2s;
}

.mf-options__link {
  text-decoration: none;
  color: $black;
}

.mf-options__title:hover {
  transform: scale(1.5);
}
</style>
