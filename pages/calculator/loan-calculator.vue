<template>
  <div>
    <h1>Loan Calcultor</h1>
    <div class="">
      <label>Loan Amount</label>
      <input v-model="loanAmount" type="number" />
    </div>
    <div class="">
      <label>Interest rate</label>
      <input v-model="interestRate" type="number" />
    </div>
    <div class="">
      <label>Loan Tenure</label>
      <input v-model="term" type="number" />
    </div>
    <button @click="submit">calculator</button>
    <div class="">Monthly Payment:- {{ Amount && Amount.toFixed(2) }}</div>
    <div class="">Total Interest:- {{ totalInterest }}</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      loanAmount: null,
      interestRate: null,
      term: null,
      Amount: null,
      totalInterest: null,
    }
  },
  methods: {
    submit() {
      const monthlyRate = this.interestRate / 100 / 12
      const payments = this.term * 12
      const x = Math.pow(1 + monthlyRate, payments)
      const monthlyPayment = (this.loanAmount * monthlyRate) / (1 - 1 / x)
      this.Amount = monthlyPayment
      this.totalInterest = monthlyPayment * payments - this.loanAmount
    },
  },
}
</script>

<style lang="scss" scoped></style>
