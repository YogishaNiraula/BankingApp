<template>
  <dash @handle="listThings()" />
  <dc />
  <blah />
</template>

<script>
import dash from "./components/dashboard.vue";
import dc from "./components/dcbutton.vue";
import blah from "./components/blah.vue";

export default {
  name: "App",
  props: { showModal: false },
  components: {
    dash,
    dc,
    blah,
  },
  data: function () {
    return {
      list: {
        amount: "",
      },
    };
  },
  methods: {
    listThings: function (amount) {
      this.list.amount = amount;
      console.log(this.amount);
    },
  },
};
</script>
