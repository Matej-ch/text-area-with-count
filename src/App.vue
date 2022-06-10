<template>
  <div id="app">
    <text-input
      label="Info"
      text="value in textarea"
      :maxlength="1000"
      text-name="area-name"
      cols="60"
      rows="4"
    />
  </div>
</template>

<script setup>
import TextInput from './components/TextInput.vue'

</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin: 60px auto 0 auto;
    max-width: 300px;
}
</style>
