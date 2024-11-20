<template>
  <div div id="main-screen" :style="{ backgroundColor: darkMode ? 'black' : 'white' }">
      <button @click="changeMode">לחצו עליי!</button>
      <Calculator2SVG class="container" v-if="darkMode"></Calculator2SVG>
      <CalculatorLightSVG class="container" v-else></CalculatorLightSVG>
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
      darkMode: true,
    }
  },
  computed: {
  },
  methods: {
    changeMode() {
      this.darkMode = !this.darkMode;
    }
  }
}
</script>

<style scoped>
#main-screen {
    width: 100%;
    height: 100%;
    /* background-color: black; */
    /* background-color: white; */
    background-size: 110% 110%;
}

.container {
  width: 100vw;
  height: 100vh;
}
</style>