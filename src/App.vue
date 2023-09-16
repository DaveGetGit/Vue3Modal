<template>
  <h1>{{ title }}</h1>
  <input type="text" ref="name" />
  <button @click="handleClick">Click Me</button>

  <div v-if="showModal">
    <ModalComponent theme="sale" @close="toggleModal">
      <h1>Ninja GiveAway</h1>
      <p>Grab your Ninja swag for half a price</p>
    </ModalComponent>
  </div>
  <button @click="toggleModal">Toggle Modal</button>
</template>

<script>
import ModalComponent from "./components/ModalComponent.vue";

export default {
  name: "App",
  components: { ModalComponent },
  data() {
    return {
      title: "My first vue3 app",
      header: "Sign up for the GiveAway",
      text: "Grab your Ninja Swag for half a Price",
      showModal: false,
    };
  },
  methods: {
    handleClick() {
      console.log(this.$refs.name);
      this.$refs.name.classList.add("active");
      this.$refs.name.focus();
    },
    toggleModal() {
      this.showModal = !this.showModal;
    },
  },
};
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
