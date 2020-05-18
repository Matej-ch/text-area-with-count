<template>
  <div id="app">
    <text-input
            label="Info"
            text="value in textarea"
            maxlength="1000"
            textName="area-name"
            cols="60" rows="4">
    </text-input>
  </div>
</template>

<script>
import TextInput from './components/TextInput.vue'

export default {
  name: 'App',
  components: {
    TextInput
  }
}
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
