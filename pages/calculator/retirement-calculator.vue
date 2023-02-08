<template>
  <div>
    <h1>Retirement Calcultor</h1>
    <div class="">
      <label>Current Age</label>
      <input v-model="currentAge" type="number" />
    </div>
    <div class="">
      <label>Retirement Age</label>
      <input v-model="retirementAge" type="number" />
    </div>
    <div class="">
      <label>Annual Income</label>
      <input v-model="annualIncome" type="number" />
    </div>
    <div class="">
      <label>Saving Rate</label>
      <input v-model="savingsRate" type="number" />
    </div>
    <div class="">
      <label>Inflation Rate</label>
      <input v-model="inflationRate" type="number" />
    </div>
    <div class="">
      <label>Return Rate</label>
      <input v-model="returnRate" type="number" />
    </div>
    <button @click="submit">calculator</button>
    <div class="">{{ amount && Math.abs(amount.toFixed(2)) }}</div>
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
