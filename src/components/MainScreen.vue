<template>
    <div id="main-screen">
      <!-- <CalculatorSVG class="container"></CalculatorSVG> -->
       <Calculator2SVG class="container"></Calculator2SVG>
    </div>
</template>

<script>
import Calculator2SVG from './Calculator2SVG.vue';
import CalculatorSVG from './CalculatorSVG.vue';


export default {
  name: "main-screen",
  components: {
    CalculatorSVG,
    Calculator2SVG
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