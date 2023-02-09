<template>
  <div>
    <h1 class="mf-calculator__heading">Retirement Calcultor</h1>
    <div class="mf-calculator__section">
      <div class="mf-calculator__input-section">
        <form @submit.prevent="submit">
          <div class="mf-input__section">
            <label class="mf-input__heading">Current Age</label>
            <input class="mf-input__value" v-model="currentAge" type="number" />
          </div>
          <div class="mf-input__section">
            <label class="mf-input__heading">Retirement Age</label>
            <input
              class="mf-input__value"
              v-model="retirementAge"
              type="number"
            />
          </div>
          <div class="mf-input__section">
            <label class="mf-input__heading">Annual Income</label>
            <input
              class="mf-input__value"
              v-model="annualIncome"
              type="number"
            />
          </div>
          <div class="mf-input__section">
            <label class="mf-input__heading">Saving Rate</label>
            <input
              class="mf-input__value"
              v-model="savingsRate"
              type="number"
            />
          </div>
          <div class="mf-input__section">
            <label class="mf-input__heading">Inflation Rate</label>
            <input
              class="mf-input__value"
              v-model="inflationRate"
              type="number"
            />
          </div>
          <div class="mf-input__section">
            <label class="mf-input__heading">Return Rate</label>
            <input class="mf-input__value" v-model="returnRate" type="number" />
          </div>
          <button class="rm-btn__black width" type="submit">Calculator</button>
        </form>
        <div v-if="amount" class="mf-calculator__display-section">
          <div class="mf-calculator__display-heading">Amount</div>
          <div class="mf-calculator__display-value">
            {{ amount && formatNumberWithComma(Math.abs(amount.toFixed(2))) }}
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
      currentAge: null,
      retirementAge: null,
      annualIncome: null,
      savingsRate: null,
      inflationRate: null,
      returnRate: null,
      amount: null,
    }
  },
  methods: {
    submit() {
      const yearsUntilRetirement = this.retirementAge - this.currentAge
      const savingsGoal =
        this.annualIncome *
        (1 + this.inflationRate) *
        (1 / (1 + this.returnRate) -
          1 / Math.pow(1 + this.inflationRate, yearsUntilRetirement))
      this.amount = (savingsGoal * this.savingsRate) / 12
    },
    formatNumberWithComma(number) {
      return number.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',')
    },
  },
}
</script>

<style lang="scss" scoped></style>

<!-- function calculateRetirement(currentAge, retirementAge, annualIncome, currentSavings, monthlySavings, inflationRate, expectedReturn) {
    var yearsToRetirement = retirementAge - currentAge;
    var monthlyIncome = annualIncome / 12;
    var monthlyExpenses = monthlyIncome - monthlySavings;
    var futureMonthlyExpenses = monthlyExpenses * Math.pow(1 + inflationRate / 100, yearsToRetirement);
    var futureValue = currentSavings * Math.pow(1 + expectedReturn / 100 / 12, yearsToRetirement * 12);
    var monthlyShortfall = futureMonthlyExpenses - futureValue / yearsToRetirement / 12;
    return {
      yearsToRetirement: yearsToRetirement,
      futureMonthlyExpenses: futureMonthlyExpenses,
      futureValue: futureValue,
      monthlyShortfall: monthlyShortfall
    };
  }
  
  var currentAge = 35;
  var retirementAge = 65;
  var annualIncome = 75000;
  var currentSavings = 100000;
  var monthlySavings = 1000;
  var inflationRate = 3;
  var expectedReturn = 7;
  
  var retirement = calculateRetirement(currentAge, retirementAge, annualIncome, currentSavings, monthlySavings, inflationRate, expectedReturn);
  console.log("Years to Retirement: " + retirement.yearsToRetirement);
  console.log("Future Monthly Expenses: " + retirement.futureMonthlyExpenses);
  console.log("Future Value: " + retirement.futureValue);
  console.log("Monthly Shortfall: " + retirement.monthlyShortfall); -->
