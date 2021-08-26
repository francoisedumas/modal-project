<template>
  <h1> {{ title }}</h1>
  <input type="text" ref="name">
  <p>Nothing here!</p>
  <button @click="handleClick">Click me</button>
  <div v-if="showModal">
    <Modal :header="header" :text="text" theme="sale" @close="toggleModal">
      <!-- here is a named slot -->
      <template v-slot:links>
        <a href="#">Sign in</a>
      </template>
      <!-- here is a slot -->
      <h1>Ninja in a slot</h1>
      <p>Cool slot</p>
    </Modal>
  </div>
  <div v-if="showModalTwo">
    <Modal @close="toggleModalTwo">
      <h1>This is my second modal</h1>
      <p>Oh yeahhh</p>
    </Modal>
  </div>
  <p>Welcome...</p>
  <button @click.shift="toggleModal">Open modal (shift)</button>
  <p>You like modals...</p>
  <button @click="toggleModalTwo">Open the second modal</button>

</template>

<script>
import Modal from './components/Modal.vue'

export default {
  name: 'App',
  components: {
    Modal
  },
  data() {
    return {
      title: 'My first Vue App',
      header: 'Sign up for discount',
      text: 'Grab your swag',
      showModal: false,
      showModalTwo: false,
    }
  },
  methods: {
    handleClick() {
      console.log(this.$refs.name)
      this.$refs.name.classList.add('active')
      this.$refs.name.focus()
    },
    toggleModal() {
      this.showModal = !this.showModal
    },
    toggleModalTwo() {
      this.showModalTwo = !this.showModalTwo
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
h1 {
  border-bottom: 1px solid #2c3e50;
  display: inline-block;
  padding-bottom: 10px;
}
</style>
