<template>
  <div>
    <input
        class="activation__input"
        type="text"
        placeholder="Pass phrase"
        :maxlength="passPhrase.length"
        @change="onChange"
    />
    <div
        class="activation__error"
        v-if="isShowError">
      Error, try again!!!
    </div>
  </div>
</template>

<script>
export default {
  name: 'Activation',
  props: {
    passPhrase: String
  },
  data() {
    return {
      isShowError: false
    };
  },
  methods: {
    onChange(event) {
      const userPassphrase = event.target.value;
      if (userPassphrase === this.passPhrase) {
        this.$emit('complete');
      } else if (userPassphrase.length === this.passPhrase.length) {
        this.showError();
      }
    },
    showError() {
      this.isShowError = true;
      setTimeout(() => this.isShowError = false, 5000);
    }
  }
};
</script>

<style scoped>
.activation__input {
  width: 40vw;
  height: 10vw;
  font-size: 10vw;
  border-radius: 10px;
  border: 2px solid #ad17cd;
}

.activation__error {
  color: red;
  font-size: 10vw;
}
</style>