<template>
  <div class="mf-option__container">
    <div v-for="items in options" class="mf-option__section" :key="items.id">
      <NuxtLink class="mf-options__link" :to="items.path">
        <div class="mf-options__title">{{ items.name }}</div>
        <div class="mf-options__description">{{ items.description }}</div>
        <div class="mf-image">
          <!-- <img class="mf-image__container" :src="items.imageUrl" /> -->
        </div>
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
          backgroundClr: '#0BF4C8',
          description:
            'These calculators help individuals determine the future value of their Systematic Investment Plan (SIP) investment, given the current SIP amount, interest rate, and investment period.',
        },
        {
          id: 2,
          name: 'CAGR Calculator',
          path: '/calculator/CAGR-calculator',
          imageUrl: require('@/assets/images/dummy.png'),
          backgroundClr: '#FAD85D',
          description: '',
        },
        {
          id: 3,
          name: 'Loan Calculator',
          path: '/calculator/loan-calculator',
          imageUrl: require('@/assets/images/dummy.png'),
          backgroundClr: '#F2A0FF',
          description: '',
        },
        {
          id: 4,
          name: 'Retirement Calculator',
          path: '/calculator/retirement-calculator',
          imageUrl: require('@/assets/images/dummy.png'),
          backgroundClr: '#FAD85D',
          description: '',
        },
        {
          id: 5,
          name: 'Investment Calculator',
          path: '/calculator/investment-calculator',
          imageUrl: require('@/assets/images/dummy.png'),
          backgroundClr: '#FAD85D',
          description: '',
        },
        {
          id: 6,
          name: 'Goal Calculator',
          path: '',
          imageUrl: require('@/assets/images/dummy.png'),
          backgroundClr: '#FAD85D',
          description: '',
        },
        {
          id: 7,
          name: 'Lump-Sum Calculator',
          path: '',
          imageUrl: require('@/assets/images/dummy.png'),
          backgroundClr: '#FAD85D',
          description: '',
        },
      ],
    }
  },
}
</script>

<style lang="scss" scoped>
.mf-option__container {
  display: flex;
  flex-wrap: wrap;
  gap: 15px;
}

.mf-option__section {
  border: 1px solid black;
  padding: $t-marg__pad * 1.5;
  width: 250px;
  box-shadow: 10px 10px 20px 0px rgba(0, 0, 0, 0.3);
  border: 2px solid rgba(0, 0, 0, 0.15);
  border-radius: 15px;
  transition: 0.3s;
  background-color: $white;
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
  font-weight: $font-ebold-weight;
  font-size: $font-size-xlarge;
}

.mf-options__description {
  font-size: $font-size-base;
  padding-top: $t-marg__pad * 2;
}
.mf-options__link {
  text-decoration: none;
  color: $black;
}

.mf-option__section:hover {
  transform: scale(1.08);
}
</style>
