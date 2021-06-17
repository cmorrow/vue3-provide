<template>
  <img alt="Vue logo" src="./assets/logo.png" />

  <input type="text" v-model="nameInput.firstName" placeholder="first name" />
  <input type="text" v-model="nameInput.lastName" placeholder="last name" />
  <button @click="changeUser">Change User</button>

  <HelloWorld msg="Welcome to Your Vue.js App" />
  <Counter />
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import Counter from "./components/Counter.vue";
import { provide, reactive, readonly } from "vue";

export default {
  name: "App",
  components: {
    HelloWorld,
    Counter
  },
  setup() {
    const user = reactive({
      id: 1,
      firstName: "Chris",
      lastName: "Morrow"
    });
    const nameInput = reactive({
      id: 1,
      firstName: user.firstName,
      lastName: user.lastName
    });

    console.log(nameInput);

    provide("currentUser", readonly(user));

    const changeUser = function() {
      user.firstName = nameInput.firstName;
      user.lastName = nameInput.lastName;
    };

    return {
      user,
      nameInput,
      changeUser
    };
  }
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
