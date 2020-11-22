<template>
  <dash />
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
};
</script>
