<template>
  <button @click.prevent="reset">reset</button>
</template>

<script>
import store from '../store'
export default {
  methods: {
    reset () {
      store.reset()
    }
  }
}
</script>

<style>
</style>
