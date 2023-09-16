<template>
  <h1>{{ title }}</h1>
  <input type="text" ref="name" />
  <button @click="handleClick">Click Me</button>

  <teleport to=".modals" v-if="showModal">
    <ModalComponent theme="sale" @close="toggleModal">
      <h1>Ninja GiveAway</h1>
      <p>Grab your Ninja swag for half a price</p>
      <template v-slot:links>
        <div class="actions">
          <a href="#">Sign up now</a>
          <a href="#">Login</a>
        </div></template
      >
    </ModalComponent>
  </teleport>
  <teleport to=".modals" v-if="showModalTwo">
    <ModalComponent @close="toggleModalTwo">
      <h1>Sign up to the newsletter</h1>
      <p>For update and promo code</p>
    </ModalComponent>
  </teleport>
  <button @clickteleport="toggleModal">Toggle Modal</button>
  <button @click="toggleModalTwo">Toggle Modal Two</button>
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
      showModalTwo: false,
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
    toggleModalTwo() {
      this.showModalTwo = !this.showModalTwo;
    },
  },
};
</script>

<style>
#app,
.modals {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
