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
          <form @submit.prevent="handleSubmit">
            <label for="title"
              >Title
              <input
                type="text"
                class="input"
                placeholder="E.g Salary"
                v-model="title"
              />
            </label>
            <label for="remarks"
              >Remarks
              <textarea
                class="input"
                placeholder="E.g. Salary got from.."
                v-model="remarks"
              />
            </label>
            <label for="amount"
              >Amount
              <input
                type="numeric"
                class="input mb-4"
                placeholder="E.g 100"
                v-model="amount"
              />
            </label>
            <button class="button is-success" type="submit">Submit</button>
          </form>
        </section>
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
        amount: "",
        type: "",
        date: new Date(),
      },
    };
  },
  methods: {
    handleSubmit: function (event) {
      console.log(this.debitCredit);
    },
    determineType: function () {
      if (amount >= 0) {
        return (type = "credit");
      } else {
        return (type = "debit");
      }
    },
  },
};
</script>