<template>
  <div class="flex justify-around">
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
div > div {
  justify-content: space-around;
  padding: 4px;
}
</style>
