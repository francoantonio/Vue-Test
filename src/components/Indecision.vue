<template>
  <img v-if="img" :src="img" />
  <div class="bg-dark"></div>

  <div class="indecision-container">
    <input v-model="question" type="text" placeholder="Hazme una pregunta" />
    <p>Recuerda terminar con un signo de interrogacion</p>
    <div v-if="isValidQuestion">
      <h2>{{ question }}</h2>
      <h1>{{ answer }}</h1>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "Indecision",
  data() {
    return {
      question: "",
      answer: "",
      img: "",
      isValidQuestion: false,
    };
  },
  watch: {
    question(value: string) {
      this.isValidQuestion = false;
      if (!value.includes("?")) return;

      this.isValidQuestion = true;
      this.getAnswer();
    },
  },
  methods: {
    async getAnswer() {
      this.answer = "Pensando...";
      const { image, answer } = await fetch("https://yesno.wtf/api").then((r) => r.json());
      this.img = image;
      this.answer = answer == "yes" ? "Si!" : "No!";
    },
  },
});
</script>

<style scoped>
img,
.bg-dark {
  height: 100vh;
  left: 0px;
  max-height: 100%;
  max-width: 100%;
  position: fixed;
  top: 0px;
  width: 100vw;
}

.bg-dark {
  background-color: rgba(0, 0, 0, 0.4);
}

.indecision-container {
  position: relative;
  z-index: 99;
}

input {
  width: 250px;
  padding: 10px 15px;
  border-radius: 5px;
  border: none;
}
input:focus {
  outline: none;
}

p {
  margin-top: 1rem;

  color: white;
  font-size: 20px;
  margin-top: 0px;
}

h1,
h2 {
  color: white;
}

h2 {
  margin-top: 150px;
}
</style>
