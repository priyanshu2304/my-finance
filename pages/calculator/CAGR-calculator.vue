<template>
  <div>
    <h1>CAGR</h1>
    <div class="">
      <label>First Value</label>
      <input v-model="firstAmount" type="number" />
    </div>
    <div class="">
      <label>Second Value</label>
      <input v-model="secondAmount" type="number" />
    </div>
    <div class="">
      <label>No Of Year</label>
      <input v-model="noOfYears" type="number" />
    </div>
    <button @click="submit">calculator</button>
    <div class="">{{ Amount && Amount.toFixed(2) }}</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      firstAmount: null,
      secondAmount: null,
      noOfYears: null,
      Amount: null,
    }
  },
  methods: {
    submit() {
      this.Amount =
        Math.pow(this.secondAmount / this.firstAmount, 1 / this.noOfYears) - 1
    },
  },
}
</script>

<style lang="scss" scoped></style>
