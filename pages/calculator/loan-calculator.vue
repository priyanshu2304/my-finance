<template>
  <div>
    <h1 class="mf-calculator__heading">Loan Calcultor</h1>
    <div class="mf-calculator__section">
      <div class="mf-calculator__input-section">
        <form @submit.prevent="submit">
          <div class="mf-input__section">
            <label class="mf-input__heading">Loan Amount</label>
            <input class="mf-input__value" v-model="loanAmount" type="number" />
          </div>
          <div class="mf-input__section">
            <label class="mf-input__heading">Interest rate</label>
            <input
              class="mf-input__value"
              v-model="interestRate"
              type="number"
            />
          </div>
          <div class="mf-input__section">
            <label class="mf-input__heading">Loan Tenure</label>
            <input class="mf-input__value" v-model="term" type="number" />
          </div>
          <button class="rm-btn__black width" type="submit">calculator</button>
        </form>
        <div v-if="totalPayable" class="mf-calculator__display-section">
          <div class="mf-calculator__display-heading">Total Payable Amount</div>
          <div class="mf-calculator__display-value">
            ₹{{ formatNumberWithComma(totalPayable) }}
          </div>
        </div>
        <div v-if="totalInterest" class="mf-calculator__display-section">
          <div class="mf-calculator__display-heading">Total Interest</div>
          <div class="mf-calculator__display-value">
            ₹{{ formatNumberWithComma(totalInterest) }}
          </div>
        </div>
        <div v-if="totalInterest" class="mf-calculator__display-section">
          <div class="mf-calculator__display-heading">Loan Amount</div>
          <div class="mf-calculator__display-value">
            ₹{{ formatNumberWithComma(loanAmount) }}
          </div>
        </div>
        <div v-if="Amount" class="mf-calculator__display-section">
          <div class="mf-calculator__display-heading">Monthly Payment</div>
          <div class="mf-calculator__display-value">
            ₹{{ Amount && formatNumberWithComma(Amount) }}
          </div>
        </div>
      </div>
      <div v-if="Amount && totalInterest" class="mf-calculator__chart-section">
        <chart-component
          :key="Amount"
          chartId="pie-chart"
          title="Sip Calculator"
          :seriesData="[
            {
              name: 'Loan Amount',
              y: Number(loanAmount),
            },
            {
              name: 'Interest Amount',
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
      loanAmount: null,
      interestRate: null,
      term: null,
      Amount: null,
      totalInterest: null,
      totalPayable: null,
    }
  },
  components: {
    ChartComponent,
  },
  methods: {
    submit() {
      const monthlyRate = this.interestRate / 100 / 12
      const payments = this.term * 12
      const x = Math.pow(1 + monthlyRate, payments)
      const monthlyPayment = (this.loanAmount * monthlyRate) / (1 - 1 / x)
      this.Amount = monthlyPayment.toFixed(2)
      this.totalInterest = (
        monthlyPayment * payments -
        this.loanAmount
      ).toFixed(2)
      this.totalPayable = (monthlyPayment * payments).toFixed(2)
    },
    formatNumberWithComma(number) {
      return number.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',')
    },
  },
}
</script>

<style lang="scss" scoped></style>
