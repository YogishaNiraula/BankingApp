<template>
  <div class="flex justify-between p-2 bg-red-900 text-orange-200">
    <div>Dashboard</div>
    <div>Total : {{ total }}</div>
  </div>
</template>

<script>
export default {
  name: "dash",
  data: function () {
    return { total: 0 };
  },
};
</script>
