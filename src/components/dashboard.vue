<template>
  <div
    class="flex justify-between px-12 py-4 bg-indigo-900 font-bold text-indigo-100 text-xl"
  >
    <div>Dashboard</div>
    <div>Total : {{ total }}</div>
  </div>
  <credit-form @handleFormData="handleValue" />
  <div
    class="grid grid-cols-3 text-center px-12 py-4 bg-purple-100 text-purple-900 font-semibold text-lg"
  >
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

      console.log("Adding to List");

      this.debitcreditList.push(data.data);

      this.updateLocalStorageDebitCredtiList(this.debitcreditList);
    },
    updateLocalStorageDebitCredtiList(newValue) {
      window.localStorage.setItem("__list__", JSON.stringify(newValue));
    },
  },

  data: function () {
    // get data from localstorage

    const total = window.localStorage.getItem("__total__") ?? 0;
    const debitcreditList = window.localStorage.getItem("__list__") ?? "[]";

    return {
      total: parseFloat(total),
      debitcreditList: JSON.parse(debitcreditList),
    };
  },

  watch: {
    total(newValue) {
      window.localStorage.setItem("__total__", newValue);
    },
  },
};
</script>

