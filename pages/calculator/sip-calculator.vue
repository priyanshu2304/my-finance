<template>
  <div>
    <h1>SIP</h1>
    <div class="">
      <label>Monthly Sip</label>
      <input v-model="monthlyAmount" type="number" />
    </div>
    <div class="">
      <label>No Of Years Invested</label>
      <input v-model="noOfYear" type="number" />
    </div>
    <div class="">
      <label>Annual rate Of Interest</label>
      <input v-model="rateOfInterest" type="number" />
    </div>
    <button @click="submit">calculator</button>
    <div class="">{{ Amount && Amount.toFixed(2) }}</div>
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
