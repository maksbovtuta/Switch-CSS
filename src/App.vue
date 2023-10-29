<template>
  <header>
    <div class="wrapper">
      <fieldset>
        <legend>Select theme:</legend>

        <div>
          <input
            @change="changeTheme"
            type="radio"
            name="drone"
            value="light"
            v-model="selectedTheme"
          />
          <label>light</label>
        </div>

        <div>
          <input
            @change="changeTheme"
            type="radio"
            name="drone"
            value="dark"
            v-model="selectedTheme"
          />
          <label>dark</label>
        </div>
      </fieldset>
      <br />
      <div :class="styleSwitcher">
        <h2>Hello, World!</h2>
      </div>
    </div>
  </header>
</template>

<script setup>
import { computed, ref } from "vue";
import { useStore } from "vuex";

const store = useStore();
const selectedTheme = ref("dark");

const changeTheme = () => {
  store.commit("setStyle", selectedTheme.value);
};

const styleSwitcher = computed(() => {
  return store.getters.getStyle;
});
</script>

<style scoped>
html,
body {
  background-color: aliceblue;
}
header {
  line-height: 1.5;
}
.light {
  background-color: #ffffff;
  color: #000000;
}
.dark {
  background-color: #333333;
  color: #ffffff;
}
h2 {
  color: black;
}
.logo {
  display: block;
  margin: 0 auto 2rem;
}
p,
label {
  font: 1rem "Fira Sans", sans-serif;
}

input {
  margin: 0.4rem;
}
</style>
