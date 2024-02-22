<template>
  <div>
    <body>
      <button class="btn-start" @click="popupActive">Начать</button>

      <popup
        v-if="popupVisiable"
        @hiddenPopup="popupActive"
        @sendInputs="sendInputs"
      />
      <p>{{ jsonData }}</p>
    </body>
  </div>
</template>
<script>
import popup from "./components/popup.vue";
export default {
  data() {
    return {
      popupVisiable: false,
      jsonData: "",
    };
  },
  components: { popup },
  methods: {
    popupActive() {
      this.popupVisiable = !this.popupVisiable;
    },
    sendInputs(inputs) {
      let nonEmptyInputs = [];
      for (let i = 0; i < inputs.length; i++) {
        if (inputs[i].trim() !== "") {
          nonEmptyInputs.push(inputs[i]);
        }
      }
      this.jsonData = JSON.stringify(nonEmptyInputs);
      this.popupVisiable = !this.popupVisiable;
    },
  },
};
</script>

<style>
.btn-start {
  padding: 10px 50px;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
</style>
