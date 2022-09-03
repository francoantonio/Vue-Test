<template>
  <h2>{{ customTitle }}</h2>
  <h3>{{ counter }} <sup>2</sup> = {{ squareCounter }}</h3>
  <hr />
  <div class="flex">
    <button @click.left="decrement">-1</button>
    <button @click.left="increment">+1</button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent<any, any, any, any>({
  name: "CounterComponent",
  props: {
    title: {
      type: String,
      required: false,
    },
    start: {
      type: Number,
      default: 0,
      validator(value: number) {
        return value <= 100;
      },
    },
  },
  data() {
    return {
      counter: this.start,
    };
  },
  methods: {
    getSquareValue() {
      return this.counter * this.counter;
    },
    increment() {
      this.counter++;
    },
    decrement() {
      this.counter--;
    },
  },
  computed: {
    squareCounter() {
      return this.counter * this.counter;
    },
    customTitle() {
      return this.title || "Computed";
    },
  },
});
</script>

<style>
.flex {
  display: flex;
  justify-content: space-evenly;
  align-items: center;
}

button {
  background-color: #64bb87;
  border-radius: 5px;
  border: 1px solid white;
  color: white;
  cursor: pointer;
  margin: 0 5px;
  padding: 5px 15px;
  transition: 0.3s ease-in-out;
}
button:hover {
  background-color: #5aa67b;
  transition: 0.3s ease-in-out;
}
</style>
