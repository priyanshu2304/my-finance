<template>
  <div>
    <h1>Investment</h1>
    <div class="">
      <label>Investment Amount</label>
      <input v-model="investmentAmount" type="number" />
    </div>
    <div class="">
      <label>No Of Years Invested</label>
      <input v-model="noOfYear" type="number" />
    </div>
    <div class="">
      <label>Invested on Investment</label>
      <input v-model="interest" type="number" />
    </div>
    <button @click="submit">calculate</button>

    <div class="">
      Future Value:- {{ futureValue && futureValue.toFixed(2) }}
    </div>
    <div class="">
      Total Interest:- {{ totalInterest && totalInterest.toFixed(2) }}
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      investmentAmount: null,
      noOfYear: null,
      interest: null,
      futureValue: null,
      totalInterest: null,
    }
  },
  methods: {
    submit() {
      const monthlyRate = this.interest / 100 / 12
      const payments = this.noOfYear * 12
      const x = Math.pow(1 + monthlyRate, payments)
      const futureValue = this.investmentAmount * x
      const totalInterest = futureValue - this.investmentAmount
      this.futureValue = futureValue
      this.totalInterest = totalInterest
    },
  },
}
</script>

<style lang="scss" scoped></style>
