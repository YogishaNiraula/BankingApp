<template>
  <div class="flex justify-between p-2 bg-red-900 text-orange-200">
    <div>Dashboard</div>
    <div>Total : {{ total }}</div>
  </div>
  <credit-form @handleFormData="handleValue" />
  <div class="flex justify-around p-3 bg-blue-200">
    <div>Date</div>
    <div>Expenditure</div>
    <div>Amount</div>
  </div>

  <div>
    <ul>
      <li v-for="dc in debitcreditList" :key="dc.title">
        <expense-list
          :date="dc.date"
          :title="dc.title"
          :amount="dc.amount"
          :type="dc.type"
        />
      </li>
    </ul>
  </div>
</template>

<script>
import creditForm from "./creditForm.vue";
import ExpenseList from "./expenseList.vue";

export default {
  name: "dashboard",
  components: {
    creditForm,
    ExpenseList,
  },
  methods: {
    handleValue: function (data) {
      const { amount } = data.data;
      this.total += amount;

      this.debitcreditList.push(data.data);
    },
  },

  data: function () {
    return { total: 0, debitcreditList: [] };
  },
};
</script>
