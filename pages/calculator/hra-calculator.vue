<template>
  <div>
    <h1 class="mf-calculator__heading">HRA Calculator</h1>
    <div class="mf-calculator__section">
      <div class="mf-calculator__input-section">
        <form @submit.prevent="submit">
          <div class="mf-input__section">
            <label class="mf-input__heading">Basic Salary:</label>
            <input
              class="mf-input__value"
              type="number"
              v-model.number="basicSalary"
            />
          </div>
          <div class="mf-input__section">
            <label class="mf-input__heading">City Type:</label>
            <select class="mf-input__value" v-model="cityType">
              <option value="metro">Metro</option>
              <option value="non-metro">Non-Metro</option>
            </select>
          </div>
          <div>
            <button class="rm-btn__black width" type="submit">Calculate</button>
          </div>
        </form>
        <div v-if="result" class="mf-calculator__display-section">
          <div class="mf-calculator__display-heading">Total Amount</div>
          <div class="mf-calculator__display-value">
            ₹{{ result && formatNumberWithComma(result) }}
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
      basicSalary: 0,
      cityType: 'metro',
      result: null,
    }
  },
  methods: {
    submit() {
      if (this.cityType === 'metro') {
        this.result = (this.basicSalary * 50) / 100
      } else {
        this.result = (this.basicSalary * 40) / 100
      }
    },
    formatNumberWithComma(number) {
      return number.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',')
    },
  },
}
</script>
