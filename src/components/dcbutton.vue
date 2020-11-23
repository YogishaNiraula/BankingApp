<template>
  <div class="flex justify-center p-6">
    <button
      class="bg-indigo-500 p-2 border-solid border border-black"
      @click="showModal = true"
    >
      Debit/Credit
    </button>
    <div class="modal" :class="{ 'is-active': showModal }">
      <div class="modal-background"></div>
      <div class="modal-card">
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
          <form>
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
          </form>
        </section>
        <footer class="modal-card-foot">
          <button
            class="button is-success"
            @click="handleSubmit()"
            type="submit"
          >
            Submit
          </button>
        </footer>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "dc",
  data: function () {
    return {
      showModal: false,
      debitCredit: {
        title: "",
        remarks: "",
        amount: 0,
        type: "",
        date: new Date(),
      },
      clearForm: {
        title: "",
        remarks: "",
        amount: 0,
        type: "",
        date: new Date(),
      },
    };
  },
  props: ["title", "remarks", "amount", "type"],
  methods: {
    handleSubmit: function (event) {
      this.$emit("handle", this.$data.amount);
    },
  },
  computed: {
    determineType: function (amount) {
      let type = "";
      if (amount > 0) {
        return (data[this.debitCredit].type = "credit");
      } else {
        return (this.type = "debit");
      }
    },
  },
};
</script>