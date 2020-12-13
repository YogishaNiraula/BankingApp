<template>
  <div class="flex justify-center p-6">
    <button
      class="focus:outline-none ring-2 border-2 px-4 py-2 rounded-lg bg-blue-200 text-blue-900 font-medium"
      @click="showModal = true"
    >
      Add Entry
    </button>
    <div class="modal" :class="{ 'is-active': showModal }">
      <div class="modal-background"></div>
      <div class="modal-card">
        <form @submit.prevent="handleSubmit">
          <header class="modal-card-head">
            <p class="modal-card-title">Debit-Credit</p>
            <div>
              <button
                class="delete"
                aria-label="close"
                @click="showModal = false"
              ></button>
            </div>
          </header>
          <section class="modal-card-body">
            <label for="title"
              >Title
              <input
                type="text"
                class="input"
                placeholder="E.g Salary"
                v-model="debitCredit.title"
              />
            </label>
            <label for="remarks"
              >Remarks
              <textarea
                class="input"
                placeholder="E.g. Salary got from.."
                v-model="debitCredit.remarks"
              />
            </label>
            <label for="amount"
              >Amount(Enter numbers only)
              <input
                type="numeric"
                class="input mb-4"
                placeholder="E.g 100"
                v-model.number="debitCredit.amount"
              />
            </label>
          </section>
          <footer class="modal-card-foot">
            <button class="button is-success" type="submit">Submit</button>
          </footer>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
import { transformVNodeArgs } from "vue";
export default {
  name: "creditForm",
  data: function () {
    return {
      showModal: false,
      debitCredit: {
        title: "",
        remarks: "",
        amount: 0,
        type: "",
        date: "",
      },
    };
  },
  methods: {
    handleSubmit: function (event) {
      this.debitCredit.amount = parseFloat(this.debitCredit.amount);
      const type = this.determineType(this.debitCredit.amount);
      this.debitCredit.type = type;

      // Formatted Date
      const today = new Date();
      const year = today.getFullYear();
      const month = today.getMonth() + 1;
      const date = today.getDate();

      this.debitCredit.date = `${year}-${month}-${date}`;

      if (this.debitCredit.title.trim() !== "") {
        this.$emit("handleFormData", {
          data: this.debitCredit,
        });
      }

      event.target.reset();
      this.debitCredit = {
        title: "",
        remarks: "",
        amount: 0,
        type: "",
      };

      this.showModal = false;
    },
    determineType: function (amount) {
      if (amount > 0) {
        return "credit";
      } else {
        return "debit";
      }
    },
  },
  computed: {},
};
</script>
