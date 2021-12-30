<template>
  <div class="row">
    <button :disabled="disabled"
    class="amber darken-4 waves-effect waves-light btn">
    Masuk
    </button>
  </div>
</template>

<script>
export default {
  props: {
    disabled: {
      type: Boolean,
    }
  },
}
</script>

<style>
button:disabled {
  background-color: #ffb300;
}
</style>