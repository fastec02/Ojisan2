<template>
  <div class="example-modal-window">
    <p>ガチャを回しておじさんを手に入れよう</p>
    <button @click="openModal">回す</button>
    <p>現在{{ count }}おじさん</p>
    <!-- コンポーネント MyModal -->
    <MyModal @close="closeModal" v-if="modal">
      <!-- default スロットコンテンツ -->
      <p>新たなおじさんを手に入れた</p>
      <div>
        <div v-bind:is="getRandom()"></div>
      </div>
      <!-- /default -->
      <!-- footer スロットコンテンツ -->
      <template slot="footer">
        <button @click="doSend">閉じる</button>
      </template>
      <!-- /footer -->
    </MyModal>
  </div>
</template>

<script>
import MyModal from "./MyModal.vue";
import OjiA from "./ojisan/ojisan_a.vue";
import OjiB from "./ojisan/ojisan_b.vue";
import OjiC from "./ojisan/ojisan_c.vue";
import OjiD from "./ojisan/ojisan_d.vue";
import OjiE from "./ojisan/ojisan_e.vue";
import OjiF from "./ojisan/ojisan_f.vue";

export default {
  components: {
    MyModal,
    ojisan_a: OjiA,
    ojisan_b: OjiB,
    ojisan_c: OjiC,
    ojisan_d: OjiD,
    ojisan_e: OjiE,
    ojisan_f: OjiF
  },
  data() {
    return {
      ojisan_components: [
        "ojisan_a",
        "ojisan_b",
        "ojisan_c",
        "ojisan_d",
        "ojisan_e",
        "ojisan_f"
      ],
      modal: false,
      count: 0
    };
  },
  methods: {
    openModal() {
      this.count += 1;
      this.getRandom();
      this.modal = true;
    },
    closeModal() {
      this.modal = false;
    },
    doSend() {
      this.closeModal();
    },
    getRandom() {
      const rnd = Math.floor(Math.random() * this.ojisan_components.length);
      return this.ojisan_components[rnd];
    }
  }
};
</script>