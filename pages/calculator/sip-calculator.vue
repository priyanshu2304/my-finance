<template>
  <div>
    <h1 class="mf-calculator__heading">SIP</h1>
    <div class="mf-calculator__section">
      <div class="mf-calculator__input-section">
        <div class="mf-input__section">
          <label class="mf-input__heading">Monthly Sip</label>
          <input
            class="mf-input__value"
            v-model="monthlyAmount"
            type="number"
          />
        </div>
        <div class="mf-input__section">
          <label class="mf-input__heading">No Of Years Invested</label>
          <input class="mf-input__value" v-model="noOfYear" type="number" />
        </div>
        <div class="mf-input__section">
          <label class="mf-input__heading">Annual rate Of Interest</label>
          <input
            class="mf-input__value"
            v-model="rateOfInterest"
            type="number"
          />
        </div>
        <button class="rm-btn__black width" @click="submit">Calculator</button>
        <div class="mf-calculator__display-section">
          <div class="mf-calculator__display-heading">Total Amount</div>
          <div class="mf-calculator__display-value">
            ₹{{ Amount && Amount.toFixed(2) }}
          </div>
        </div>
      </div>
      <div class="mf-calculator__chart-section">hy</div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      monthlyAmount: null,
      noOfYear: null,
      rateOfInterest: null,
      Amount: null,
    }
  },
  methods: {
    submit() {
      this.Amount =
        (this.monthlyAmount *
          (Math.pow(1 + this.rateOfInterest / 100 / 12, 12 * this.noOfYear) -
            1)) /
        (this.rateOfInterest / 100 / 12)
    },
  },
}
</script>

<style lang="scss" scoped></style>
