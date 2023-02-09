<template>
  <div>
    <h1 class="mf-calculator__heading">Savings Calculator</h1>
    <div class="mf-calculator__section">
      <div class="mf-calculator__input-section">
        <form @submit.prevent="submit">
          <div class="mf-input__section">
            <label class="mf-input__heading">Monthly Savings</label>
            <input
              class="mf-input__value"
              v-model="monthlySavings"
              type="number"
            />
          </div>
          <div class="mf-input__section">
            <label class="mf-input__heading">Annual Interest Rate</label>
            <input
              class="mf-input__value"
              v-model="annualInterestRate"
              type="number"
            />
          </div>
          <div class="mf-input__section">
            <label class="mf-input__heading">Years</label>
            <input class="mf-input__value" v-model="years" type="number" />
          </div>
          <button class="rm-btn__black width" type="submit">Calculator</button>
        </form>
        <div v-if="totalSavings" class="mf-calculator__display-section">
          <div class="mf-calculator__display-heading">
            Total saving after {{ years }} years
          </div>
          <div class="mf-calculator__display-value">
            ₹{{ totalSavings && formatNumberWithComma(totalSavings) }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      monthlySavings: null,
      annualInterestRate: null,
      years: null,
      totalSavings: 0,
    }
  },
  methods: {
    submit() {
      const monthlyInterestRate = this.annualInterestRate / 12 / 100
      let totalSavings = 0

      for (let i = 0; i < this.years * 12; i++) {
        totalSavings =
          (totalSavings + this.monthlySavings) * (1 + monthlyInterestRate)
      }

      this.totalSavings = totalSavings.toFixed(2)
    },
    formatNumberWithComma(number) {
      return number.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',')
    },
  },
}
</script>

<style lang="scss" scoped></style>
