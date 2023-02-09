<template>
  <div>
    <h1 class="mf-calculator__heading">Investment</h1>
    <div class="mf-calculator__section">
      <div class="mf-calculator__input-section">
        <form @submit.prevent="submit">
          <div class="mf-input__section">
            <label class="mf-input__heading">Investment Amount</label>
            <input
              class="mf-input__value"
              v-model="investmentAmount"
              type="number"
            />
          </div>
          <div class="mf-input__section">
            <label class="mf-input__heading">No Of Years Invested</label>
            <input class="mf-input__value" v-model="noOfYear" type="number" />
          </div>
          <div class="mf-input__section">
            <label class="mf-input__heading">Interest on Investment</label>
            <input class="mf-input__value" v-model="interest" type="number" />
          </div>
          <button class="rm-btn__black width" type="submit">calculate</button>
        </form>
        <div v-if="futureValue" class="mf-calculator__display-section">
          <div class="mf-calculator__display-heading">Future Value</div>
          <div class="mf-calculator__display-value">
            ₹{{ futureValue && futureValue }}
          </div>
        </div>
        <div v-if="totalInterest" class="mf-calculator__display-section">
          <div class="mf-calculator__display-heading">Total Interest</div>
          <div class="mf-calculator__display-value">
            ₹{{ totalInterest && totalInterest }}
          </div>
        </div>
        <div v-if="totalInterest" class="mf-calculator__display-section">
          <div class="mf-calculator__display-heading">Total Money Invested</div>
          <div class="mf-calculator__display-value">
            ₹{{ investmentAmount && investmentAmount }}
          </div>
        </div>
      </div>
      <div v-if="futureValue" class="mf-calculator__chart-section">
        <chart-component
          :key="futureValue"
          chartId="pie-chart"
          title="Sip Calculator"
          :seriesData="[
            {
              name: 'Invested Money',
              y: Number(investmentAmount),
            },
            {
              name: 'Interest Recieved',
              y: Number(totalInterest),
              sliced: true,
              selected: true,
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
      investmentAmount: null,
      noOfYear: null,
      interest: null,
      futureValue: null,
      totalInterest: null,
    }
  },
  components: {
    ChartComponent,
  },
  methods: {
    submit() {
      const monthlyRate = this.interest / 100 / 12
      const payments = this.noOfYear * 12
      const x = Math.pow(1 + monthlyRate, payments)
      const futureValue = this.investmentAmount * x
      const totalInterest = futureValue - this.investmentAmount
      this.futureValue = futureValue.toFixed(2)
      this.totalInterest = totalInterest.toFixed(2)
    },
  },
}
</script>

<style lang="scss" scoped></style>
