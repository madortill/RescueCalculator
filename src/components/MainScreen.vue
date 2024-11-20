<template>
  <div div id="main-screen" :style="{ backgroundColor: darkMode ? 'black' : 'white' }">
    <Calculator2SVG class="container" :darkMode="darkMode" @chosen-btn="handleChosenBtn" @toggle-theme="changeMode"></Calculator2SVG>
    <ThemeSwitcher @click="changeMode">לחצו עליי!</ThemeSwitcher>
    <CalculatingContainer class="container" :chosenBtn="chosenValue"></CalculatingContainer>
      <!-- <CalculatorLightSVG class="container" v-else></CalculatorLightSVG> -->
  </div>
</template>

<script>
import Calculator2SVG from './Calculator2SVG.vue';
import CalculatorLightSVG from './CalculatorLightSVG.vue';
import ThemeSwitcher from './ThemeSwitcher.vue'
import CalculatingContainer from './CalculatingContainer.vue';


export default {
  name: "main-screen",
  components: {
    Calculator2SVG,
    CalculatorLightSVG,
    ThemeSwitcher,
    CalculatingContainer
  },
  data() {
    return {
      darkMode: true,
      chosenValue: null,
      stringBtn: ''
    }
  },
  computed: {
  },
  methods: {
    changeMode() {
      this.darkMode = !this.darkMode;
    },
    handleChosenBtn(chosenBtn) { // This will log the chosen button value
      if (Number(chosenBtn)) {
          this.chosenValue = Number(chosenBtn);
      }
       else {
        this.stringBtn = chosenBtn;
        console.log(this.stringBtn);
       }
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
  position: absolute;
  top: 0;
}


</style>