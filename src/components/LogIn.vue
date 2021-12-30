<template>
<div class="main">
  <div class="wrapper">
    <form class="col s12" @submit.prevent="submit" >     

      <MyInput
      :value="username.value"
      :error="username.error"
      name="Username" typeInput="text"
      :rules="{ required: true, min: 5}"
      @update="update" />

      <MyInput
      :value="password.value"
      :error="password.error"
      name="Password" typeInput="password"
      :rules="{ min: 8 }"
      @update="update"/>

      <MyButton :disabled="!valid" />

    </form>
  </div>
</div>
</template>

<style>
  .main {
    display: flex;
    max-width: 100%;
    justify-content: center;
  }
  .wrapper {
    width: 80%;
  }
</style>
<script>

import MyButton from './MyButton.vue';
import MyInput from './MyInput.vue';

export default {
  components: {
    MyButton, MyInput
  },
  data: () => ({
    username: {
      value: '',
      error: ''
    },
    password: {
      value: '',
      error: ''
    },
  }),
  computed: {
    valid(){
      return (
        !this.username.error &&
        !this.password.error
      )
    }
  },
  methods: {
    update({name, value, error}) {
      this[name].value = value;
      this[name].error = error;
    },
    submit() {
      console.log('Event');
    }
  }
}


</script>