<template>
  <!-- Counter -->
  <div>
    <button @click="subtract">-</button>
    <button @click="add">+</button>
    <div class="counter">{{ counter }}</div>
    <h2>Current User:</h2>
    <p>{{ currentUser.firstName }} {{ currentUser.lastName }}</p>
  </div>
</template>

<script>
import { ref, inject } from "vue";

export default {
  name: "Counter",
  setup() {
    const counter = ref(0);

    const currentUser = inject("currentUser");
    currentUser.firstName = "Bob";

    const add = function() {
      counter.value = counter.value + 1;
    };

    const subtract = function() {
      counter.value = counter.value - 1;
    };

    return {
      currentUser,
      add,
      subtract,
      counter
    };
  }
};
</script>

<style scoped>
button {
  margin-left: 5px;
}
</style>
