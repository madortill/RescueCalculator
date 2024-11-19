<template>
    <div id="main-screen">
       <Calculator2SVG class="container"></Calculator2SVG>
       <!-- <CalculatorLightSVG class="container"></CalculatorLightSVG> -->
    </div>
</template>

<script>
import Calculator2SVG from './Calculator2SVG.vue';
import CalculatorLightSVG from './CalculatorLightSVG.vue'


export default {
  name: "main-screen",
  components: {
    Calculator2SVG,
    CalculatorLightSVG
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
    /* background-color: black; */
    background-color: white;
    background-size: 110% 110%;
}

.container {
  width: 100vw;
  height: 100vh;
}
</style>