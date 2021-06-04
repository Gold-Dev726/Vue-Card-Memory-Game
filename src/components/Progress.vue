<template>
  <transition name="fade">
    <progress class="progress  is-small is-success" :value="value" max="100"
      >{{ value }} %</progress
    >
  </transition>
</template>

<script>
export default {
  props: {
    cols: Number,
    done: Array,
  },
  computed: {
    value: function() {
      return (this.done.length / (Math.pow(this.cols, 2) / 2)) * 100;
    },
  },
};
</script>

<style scoped>
progress::-webkit-progress-value {
  transition: width 1s ease;
}
</style>
