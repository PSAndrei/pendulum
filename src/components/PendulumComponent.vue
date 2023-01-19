<template>
  <div class="pendulum-canvas">
    <div
      class="pendulum-leg"
      :style="{
        height: L + '%',
        transform: `rotate(${position}deg)`,
        'animation-duration': fluctuations + 's',
      }"
    ></div>
  </div>
</template>

<script>
import { ref, computed } from "vue";

export default {
  name: "PendulumComponent",
  props: ["L"],
  setup(props) {
    const g = 9.8;
    const position = ref(0);
    const isNegative = ref(false);

    const fluctuations = computed(() => {
      let T = 2 * Math.PI * Math.sqrt(props.L / g);
      return T / 4;
    });

    return { g, fluctuations, position, isNegative };
  },
};
</script>

<style scoped>
.pendulum-canvas {
  width: 50%;
  height: 50%;
  background: rgb(216, 175, 231);
  border-top: 2px solid black;
  position: relative;
}

.pendulum-leg {
  border: 1px solid black;
  position: absolute;
  right: 50%;
  animation-name: move;
  animation-iteration-count: infinite;
  transform-origin: 50% 0;
}

.pendulum-leg::after {
  content: "";
  position: absolute;
  height: 30px;
  width: 30px;
  background: yellow;
  top: 100%;
  left: -15px;
  border-radius: 50%;
}

@keyframes move {
  0%,
  100% {
    transform: translate(0, 0) rotate(40deg);
  }
  50% {
    transform: translate(0, 0) rotate(-40deg);
  }
}
</style>
