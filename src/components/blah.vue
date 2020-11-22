<template>
  <div class="flex bg-blue-200">
    <div>Date</div>
    <div>Debited/Credited</div>
    <div>Amount</div>
  </div>
</template>

<script>
export default {
  name: "blah",
  data: function () {
    return {};
  },
};
</script>

<style scoped>
div > div {
  justify-content: space-around;
  padding: 4px;
}
</style>