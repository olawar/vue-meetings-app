<template>
  <div>
    <label for="email">Zaloguj się e-mailem</label>
    <input v-bind:class="{ errorInput: error }" id="email" type="email" v-model="email">
    <p class="error" v-if="error">Wpisz poprawny adres email</p>
    <button @click="enter()">{{ buttonLabel }}</button>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        email: '',
        error: false,
        buttonLabel: ''
      }
    },
    methods: {
      enter() {
        if(!this.error) {
          this.$emit('login', this.email);
        }
      }
    },
    mounted() {
      if (!this.buttonLabel) {
        this.buttonLabel = 'Zaloguj się';
      }
    },
    watch: {
      email: function() {
        this.email.length > 3 ? (this.error = false) : (this.error=true);
      }
    }
  }
</script>

<style lang="scss">
.error {
  color: red;
}
.errorInput {
  border: 1px solid red !important;
}
</style>
