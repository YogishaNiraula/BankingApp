<template>
  <div
    class="w-full grid grid-cols-3 text-center px-12 py-4 font-bold"
    :class="{
      'bg-green-100 text-green-900': type === 'credit',
      'bg-red-100 text-red-900': type === 'debit',
    }"
  >
    <div>{{ date }}</div>
    <div>{{ title }}</div>
    <div>{{ amount }}</div>
  </div>
</template>

<script>
export default {
  name: "expenseList",
  props: ["title", "amount", "date", "type"],
};
</script>

<style scoped>
</style>
