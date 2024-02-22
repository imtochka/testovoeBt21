<template>
  <div @click.self="hiddenPopup" class="popup">
    <div class="popup-wrapper">
      <h1>Заголовок</h1>
      <div class="popup-input-box">
        <input
          v-for="(input, index) in inputs"
          :key="index"
          v-model.trim="inputs[index]"
        />
      </div>

      <div class="button-wrapper">
        <button @click.self="sendInputs" class="send-btn">Отправить</button>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      inputs: ["", "", "", "", ""],
    };
  },
  methods: {
    hiddenPopup() {
      this.$emit("hiddenPopup");
    },
    sendInputs() {
      // if (this.input) {

      //   this.$emit('formSubmitted');
      // }
      console.log(this.inputs);
      this.$emit("sendInputs", this.inputs);
    },
  },
};
</script>

<style scoped>
.button-wrapper {
  margin-top: 20px;
  display: flex;
  justify-content: center;
}
.send-btn {
  display: flex;
  text-align: center;
  margin-bottom: 15px;
  padding: 10px 15px;
}
input {
  border: 1px solid black;
  border-radius: 5px;
  outline: none;
  padding: 2px;
}
.popup {
  z-index: 5;
  position: absolute;
  min-width: 100%;

  height: 100vh;

  background-color: rgba(0, 0, 0, 0.5);
}
.popup-wrapper {
  background-color: #fff;

  position: absolute;
  max-width: 500px;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
.popup-wrapper h1 {
  display: flex;
  justify-content: center;
  margin-bottom: 15px;
}

.popup-input-box {
  display: flex;

  flex-wrap: wrap;
  justify-content: space-around;
  gap: 30px;
  background-color: white;
}
</style>
