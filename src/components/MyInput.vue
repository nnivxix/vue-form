<template>
  <div class="row">
    <div class="input-field col s12">
      <label :for="name.toLowerCase()">{{name}}</label> <br>
      <div class="error">{{ error }}</div><br>
      <input :id="name.toLowerCase()" :type="typeInput"
      class="validate" :value="value" @input="input">

    </div>
  </div>
</template>

<script>
export default {
  props:{
    name: {
      type: String,
    },
    value: {
      type: String,
    },
    typeInput: {
      type: String,
    },
    rules: {
      type: Object,
      default: {},
    },
    error: {
      type: String,
    }
  },
  created() {
    this.$emit('update', {
        name: this.name.toLowerCase(),
        value: this.value,
        err: this.validate(this.value),
      })
  },
  methods: {
    input ($event) {
      this.$emit('update', {
        name: this.name.toLowerCase(),
        value: $event.target.value,
        error: this.validate($event.target.value),
      })
    },
    validate(value) {
      if (this.rules.required && value.length === 0) {
        return 'Value is required';
      }

      if (this.rules.min && value.length < this.rules.min) {
          return `This min length is ${this.rules.min}`;
      }
    }
  }
}
</script>

<style>
.error {
  color: red;
  padding-top: 10px;

}
</style>