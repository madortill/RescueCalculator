<template>
  <div div id="main-screen" :style="{ backgroundColor: darkMode ? 'black' : 'white' }">
    <ThemeSwitcher @click="changeMode">לחצו עליי!</ThemeSwitcher>
    <!-- <button @click="changeMode">לחצו עליי!</button> -->
     <div class="charStyle">
      {{ this.chosenValue }}
     </div>
    <Calculator2SVG class="container" :darkMode="darkMode" @chosen-btn="handleChosenBtn" @toggle-theme="changeMode"></Calculator2SVG>
      <!-- <CalculatorLightSVG class="container" v-else></CalculatorLightSVG> -->
  </div>
</template>

<script>
import Calculator2SVG from './Calculator2SVG.vue';
import CalculatorLightSVG from './CalculatorLightSVG.vue';
import ThemeSwitcher from './ThemeSwitcher.vue'


export default {
  name: "main-screen",
  components: {
    Calculator2SVG,
    CalculatorLightSVG,
    ThemeSwitcher
  },
  data() {
    return {
      darkMode: true,
      chosenValue: ''
    }
  },
  computed: {
  },
  methods: {
    changeMode() {
      this.darkMode = !this.darkMode;
    },
    handleChosenBtn(chosenBtn) { // This will log the chosen button value
    this.chosenValue = chosenBtn;
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

.charStyle {
  color: rgb(182, 152, 32);
  position: absolute;
  left: 3rem;
  top: 7rem;
  font-size: calc(14px + 6vw)
}
</style>