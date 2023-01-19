<template>
  <pendulum-slider v-model="size" />
  <pendulum-component :L="size" />
</template>

<script>
import PendulumComponent from "./components/PendulumComponent.vue";
import PendulumSlider from "./components/Slider.vue";
import { ref } from "vue";

export default {
  name: "App",
  components: {
    "pendulum-component": PendulumComponent,
    "pendulum-slider": PendulumSlider,
  },
  setup() {
    const size = ref("2");
    return { size };
  },
};
</script>

<style>
#app {
  height: 100vh;
}
* {
  margin: 0;
  padding: 0;
}
</style>
