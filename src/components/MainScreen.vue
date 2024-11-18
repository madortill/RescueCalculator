<template>
    <div id="main-screen">
      <CalculatorSVG class="container"></CalculatorSVG>
    </div>
</template>

<script>
import CalculatorSVG from './CalculatorSVG.vue';


export default {
  name: "main-screen",
  components: {
    CalculatorSVG
  },
  data() {
    return {
    }
  },
  computed: {
  },
  methods: {
  }
}
</script>

<style scoped>
#main-screen {
    width: 100%;
    height: 100%;
    background-color: black;
    background-size: 110% 110%;
}

.container {
  width: 100vw;
  height: 100vh;
}
</style>