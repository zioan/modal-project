<template>
  <h1>{{title}}</h1>
  <div v-if="showModal">
    <Modal theme="sale" @close="toggleModal">
      <h1>My title</h1>
      <template v-slot:links>
        <a href="">sign up now</a>
        <a href="">more info</a>
      </template>
      <p>Lorem, ipsum dolor.</p>
    </Modal>
  </div>
  
  <teleport to=".modals" v-if="showModalTwo">
    <Modal @close="toggleModalTwo">
      <template v-slot:links>
        <h2>Hello from modal 2</h2>
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Incidunt, harum.</p>
        <p>Lorem, ipsum dolor.</p>
        <a href="">Modal 2 link</a>

      </template>
    </Modal>
  </teleport>

  <p>Welcome...</p>

  <button @click.shift="toggleModal">open modal (shift + click)</button>
  <br>
  <button @click="toggleModalTwo">open modal 2</button>

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
      title: "My first vue app :)",
      showModal: false,
      showModalTwo: false,
    }
  },
  methods: {
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
#app, .modals {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1 {
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}
</style>
