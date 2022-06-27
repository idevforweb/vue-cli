<template>
  <h1> {{ title }} </h1>
  <!-- How to use template refs -->
  <input type="text" ref="name">
  <button @click="handleClick">Click me here!</button>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      title: 'My first Real Vue App :)'
    }
  },
  // How to use template refs
  methods: {
    handleClick() {
      console.log(this.$refs.name);
      // Using regular js to add a class to ref.name
      this.$refs.name.classList.add('active');
      // Using regular js to focus input field on button click 
      this.$refs.name.focus();
    }
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
  margin-top: 60px;
}
</style>
