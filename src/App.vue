<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <CounterComponent :start="15"></CounterComponent>
  <hr />
  <CounterComponent></CounterComponent>
</template>
<script lang="ts">
import { defineComponent } from "vue";
import CounterComponent from "./components/CounterComponent.vue";

export default defineComponent({
  name: "App",
  components: {
    CounterComponent,
  },
});
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
