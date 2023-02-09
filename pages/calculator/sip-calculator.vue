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
        <form @submit.prevent="submit">
          <div class="mf-input__section">
            <label class="mf-input__heading">Number Of Years Invested</label>
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
          <button class="rm-btn__black width" type="submit">Calculator</button>
        </form>
        <div v-if="amount" class="mf-calculator__display-section">
          <div class="mf-calculator__display-heading">Total Amount</div>
          <div class="mf-calculator__display-value">
            ₹{{ amount && formatNumberWithComma(amount) }}
          </div>
        </div>
        <div v-if="investedAmount" class="mf-calculator__display-section">
          <div class="mf-calculator__display-heading">
            Total Invested Amount
          </div>
          <div class="mf-calculator__display-value">
            ₹{{ investedAmount && formatNumberWithComma(investedAmount) }}
          </div>
        </div>
        <div v-if="earnedMoney" class="mf-calculator__display-section">
          <div class="mf-calculator__display-heading">Total Earned Amount</div>
          <div class="mf-calculator__display-value">
            ₹{{ earnedMoney && formatNumberWithComma(earnedMoney) }}
          </div>
        </div>
      </div>
      <div
        v-if="investedAmount && earnedMoney && amount"
        class="mf-calculator__chart-section"
      >
        <chart-component
          :key="amount"
          chartId="pie-chart"
          title="Sip Calculator"
          :seriesData="[
            {
              name: 'Invested Money',
              y: Number(investedAmount),
            },
            {
              name: 'Earned Money',
              y: Number(earnedMoney),
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
      monthlyAmount: null,
      noOfYear: null,
      rateOfInterest: null,
      amount: null,
      investedAmount: null,
      earnedMoney: null,
    }
  },
  components: {
    ChartComponent,
  },
  methods: {
    submit() {
      this.amount = (
        (this.monthlyAmount *
          (Math.pow(1 + this.rateOfInterest / 100 / 12, 12 * this.noOfYear) -
            1)) /
        (this.rateOfInterest / 100 / 12)
      ).toFixed(2)
      this.investedAmount = (this.monthlyAmount * 12 * this.noOfYear).toFixed(2)
      this.earnedMoney = (this.amount - this.investedAmount).toFixed(2)
    },
    formatNumberWithComma(number) {
      return number.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',')
    },
  },
}
</script>

<style lang="scss" scoped></style>
