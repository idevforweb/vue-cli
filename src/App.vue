// Handling Components with Modal Component.

<template>
  <!-- button created to use the toggleModel method -->
  <!-- used .alt event modifier option: alt has to be pressd in order to show modal -->
  <button @click.alt="toggleModal">Show Modal</button>
  <button @click="toggleModalTwo">Show Modal Two</button>
  <h1> {{ title }} </h1>
  <!-- using v-if to set true or false boolean for modal visibility -->
  <div v-if="showModal">
    <!-- Slots are useful for passing custom templates into components -->
    <!-- slots are writting with defualt closing tag, inline closing tag <modal></modal>-->
    <Modal :theme="vSales" @close="toggleModal">
      <!-- name slots dont automitcally render unless called  -->
      <template v-slot:links>
        <a href="#">Sign up now</a>
        <a href="#">More info</a>
      </template>
      <!-- defualt slot content  -->
      <h1>{{ header }}</h1>
      <p>{{ text }}</p>
  
    </Modal>
  </div>

  <!-- Using teleport we can send different components to different roots in index.html -->
  <!-- This will be sent to the .modal element -->
  <teleport to=".modals" v-if="showModalTwo">
    <Modal @close="toggleModalTwo">
      <!-- named slots dont automitcally render unless called  -->
      <template v-slot:links>
        <a href="#">Sign up now</a>
        <a href="#">More info</a>
      </template>
      <!-- defualt slot content  -->
      <h1>{{ headerTwo }}</h1>
      <p>{{ textTwo }}</p>
  
    </Modal>
  </teleport>
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
      headerTwo: 'Modal Two Header',
      text:   'Dynamic content for modal text prop',
      textTwo:   'Text for Modal Two',
      vSales: 'sale',
      showModal: false,
      showModalTwo: false,
    }
  }, 
  methods: {
    toggleModal() {
      this.showModal = !this.showModal;
    },
        toggleModalTwo() {
      this.showModalTwo = !this.showModalTwo;
    }
  }
}
</script>

<style>
#app, .modals {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
