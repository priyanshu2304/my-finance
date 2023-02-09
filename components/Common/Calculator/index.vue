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
          description:
            'CAGR stands for Compound Annual Growth Rate, which is a measure of the average yearly growth rate of an investment over a specific time period. It takes into account the compound effect of any gains or losses and assumes a constant rate of growth. It is used to determine the average return on an investment over a number of years.',
        },
        {
          id: 3,
          name: 'Loan Calculator',
          path: '/calculator/loan-calculator',
          imageUrl: require('@/assets/images/dummy.png'),
          backgroundClr: '#F2A0FF',
          description:
            'These calculators help determine the monthly payment and total interest of a loan, given the loan amount, interest rate, and term.',
        },
        {
          id: 4,
          name: 'Retirement Calculator',
          path: '/calculator/retirement-calculator',
          imageUrl: require('@/assets/images/dummy.png'),
          backgroundClr: '#FAD85D',
          description:
            'These calculators help individuals plan and evaluate their retirement savings, including calculating the amount of savings needed to reach a certain retirement goal and determining the estimated monthly retirement income.',
        },
        {
          id: 5,
          name: 'Investment Calculator',
          path: '/calculator/investment-calculator',
          imageUrl: require('@/assets/images/dummy.png'),
          backgroundClr: '#FAD85D',
          description:
            'These calculators help individuals determine the future value of their investments, including stocks, bonds, and mutual funds.',
        },
        {
          id: 6,
          name: 'Saving Calculator',
          path: '/calculator/saving-calculator',
          imageUrl: require('@/assets/images/dummy.png'),
          backgroundClr: '#FAD85D',
          description:
            'These calculators help individuals determine the future value of their savings and the amount of savings needed to reach a certain goal, given the current savings and interest rate.',
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
