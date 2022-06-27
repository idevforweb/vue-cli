// Handling Components with Modal Component.

<template>
  <!-- button created to use the toggleModel method -->
  <!-- used .alt event modifier option: alt has to be pressd in order to show modal -->
  <button @click.alt="toggleModal">Show Modal</button>
  <h1> {{ title }} </h1>
  <!-- using v-if to set true or false boolean for modal visibility -->
  <div v-if="showModal">
    <!-- Add modal as HTML tag -->
    <!-- Passing header, text, theme props to modal -->
    <!-- use bind method eg. :header is equal to v-bind:header for props -->
    <!-- theme is linked to the dynamic :class="{ sales: 'expression' }" set up in Modal.vue -->
    <!-- @close is the $emit method created in App.vue that selects the toggleModal method to inherit -->
    <Modal 
      :header="header"
      :text="text"
      :theme="vSales"
      @close="toggleModal"
    />
  </div>
</template>

<script>
// Import Modal
import Modal from './components/Modal.vue'

export default {
  name: 'App',
  // Add Modal component to exports
  components: { Modal },
  data() {
    return {
      title:  'My first Real Vue App :)',
      // Dynamic content for modal prop attributes 'header' and 'text'
      header: 'Dynamic content for header prop',
      text:   'Dynamic content for modal text prop',
      vSales: 'sale',
      showModal: false,
    }
  }, 
  methods: {
    toggleModal() {
      this.showModal = !this.showModal;
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
