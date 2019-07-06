<template>
  <div id="app">
    <Header v-bind:val="count"/>
    <div class="container-fluid">
      <div class="row">
        <div class="col-sm-6">
          <p>ガチャを回しておじさんを手に入れよう</p>
          <img width="60%" src="./assets/gachagacha.png">
          <Dashboard v-on:child-event="parentMethod"/>
        </div>
        <div class="col-sm-6">
          <div class="border-left">
            <Pop/>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Dashboard from "./components/index.vue";
import Mymodal from "./components/MyModal.vue";
import Pop from "./components/Pop.vue";
import Header from "./components/Header";

export default {
  name: "App",
  data() {
    return {
      count: 0
    };
  },
  components: {
    Dashboard,
    Mymodal,
    Pop,
    Header
  },
  methods: {
    parentMethod(count) {
      this.count = count;
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 0px;
}
</style>
