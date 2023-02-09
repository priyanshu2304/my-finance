<template>
  <div>
    <h1 class="mf-calculator__heading">CAGR</h1>
    <div class="mf-calculator__section">
      <div class="mf-calculator__input-section">
        <form @submit.prevent="submit">
          <div class="mf-input__section">
            <label class="mf-input__heading">First Value</label>
            <input
              class="mf-input__value"
              v-model="firstAmount"
              type="number"
            />
          </div>
          <div class="mf-input__section">
            <label class="mf-input__heading">Second Value</label>
            <input
              class="mf-input__value"
              v-model="secondAmount"
              type="number"
            />
          </div>
          <div class="mf-input__section">
            <label class="mf-input__heading">No Of Year</label>
            <input class="mf-input__value" v-model="noOfYears" type="number" />
          </div>
          <button class="rm-btn__black width" type="submit">calculator</button>
        </form>
        <div v-if="amount" class="mf-calculator__display-section">
          <div class="mf-calculator__display-heading">Total Amount</div>
          <div class="mf-calculator__display-value">
            {{ amount && formatNumberWithComma(amount) * 100 }}%
          </div>
        </div>
      </div>
      <div v-if="amount" class="mf-calculator__chart-section">
        {{ amount }}
        <chart-component
          :key="amount"
          chartId="pie-chart"
          title="Sip Calculator"
          :seriesData="[
            {
              name: 'Percentage',
              y: Number(amount),
            },
          ]"
        />
      </div>
    </div>
  </div>
</template>

<script>
import ChartComponent from '@/components/Common/Charts.vue'
export default {
  data() {
    return {
      firstAmount: null,
      secondAmount: null,
      noOfYears: null,
      amount: null,
    }
  },
  components: {
    ChartComponent,
  },
  methods: {
    submit() {
      this.amount =
        Math.pow(this.secondAmount / this.firstAmount, 1 / this.noOfYears) - 1
    },
    formatNumberWithComma(number) {
      return number.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',')
    },
  },
}
</script>

<style lang="scss" scoped></style>
