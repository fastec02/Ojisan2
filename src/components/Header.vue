<template>
  <nav class="navbar navbar-expand-lg navbar-light bg-light sticky-top">
    <a class="navbar-brand" href="#">日本おじさん連合</a>
    <button
      class="navbar-toggler"
      type="button"
      data-toggle="collapse"
      data-target="#navbarSupportedContent"
      aria-controls="navbarSupportedContent"
      aria-expanded="false"
      aria-label="Toggle navigation"
    >
      <span class="navbar-toggler-icon"></span>
    </button>

    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav mr-auto"></ul>
      <span class="navbar-text">現在 {{ val}}おじさん</span>
    </div>
  </nav>
</template>

<script>
import App from "../App.vue";
export default {
  name: "Header",
  data() {
    return {
      count: 0
    };
  },
  props: ["val"],
  mounted: function() {
    App.bus.$on("bus-event", this.changeMethod);
  },
  methods: {
    changeMethod(count) {
      this.count = count;
    }
  }
};
</script>

<style scoped>
</style>