<template>
  <div class="lg-steps">
    <div class="lg-steps-line"></div>
    <div class="lg-step" :style="{ color: active >= item ? activeColor : defaultColor}" v-for="item in count" :key="item">{{ item }}</div>
  </div>
</template>

<script>
import './steps.css'
export default {
  props: {
    count: {
      type: Number,
      default: 4
    },
    active: {
      type: Number,
      default: 0
    },
    activeColor: {
      type: String,
      default: 'red'
    },
    defaultColor: {
      type: String,
      default: 'green'
    }
  }
}
</script>

<style>

</style>