<template>
  <div div id="main-screen" :style="{ backgroundColor: darkMode ? 'black' : 'white' }">
    
    <Calculator2SVG 
        class="container" 
        :darkMode="darkMode" 
        :MKinfo = "MKinfo"
        :clickedStates="clickedStates"
        @chosen-btn="handleChosenBtn" 
        @clickedBtn="handleClicked">
    </Calculator2SVG>
    
    <!-- <ThemeSwitcher
        @click="changeMode">
    </ThemeSwitcher> -->

    <CalculatingContainer 
      class="container"
      :darkMode="darkMode"
      :chosenValueString="chosenValueString"
      :stringBtn="stringBtn"
      :clickedStates="clickedStates" 
      @clickedBtn="handleClicked"
      @MKinfo="foundMK"
      >
  </CalculatingContainer>
  
  </div>
</template>

<script>
import Calculator2SVG from './Calculator2SVG.vue';
import CalculatorLightSVG from './CalculatorLightSVG.vue';
import ThemeSwitcher from './ThemeSwitcher.vue'
import CalculatingContainer from './CalculatingContainer.vue';


export default {
  name: "main-screen",
  props: ['darkMode'], 
  components: {
    Calculator2SVG,
    CalculatorLightSVG,
    ThemeSwitcher,
    CalculatingContainer
  },
  data() {
    return {
      // darkMode: true,
      chosenValueString: null,
      stringBtn: '',
      clickedStates: {
        formula: false,
        ground: false,
        degree: false,
      },
      MKinfo: null,
      counter: 0,
   };
  },
  computed: {
  },
  methods: {
    foundMK(ground) {
      this.MKinfo = ground;
    },
    handleClicked(btn) {
      const currentState = this.clickedStates[btn];
      Object.keys(this.clickedStates).forEach(name => {
        this.clickedStates[name] = false;
      });
      this.clickedStates[btn] = !currentState;
    },

    // changeMode() {
    //   this.darkMode = !this.darkMode;
    // },
    handleChosenBtn(chosenBtn) { 
      this.counter++;
      // console.log(chosenBtn);
      if (Number(chosenBtn) || Number(chosenBtn) === 0) {
          this.chosenValueString = String(chosenBtn)+String(this.counter);
      } else {
        this.stringBtn = chosenBtn;
        // console.log(this.stringBtn);
       }
    },
  }
}
</script>

<style scoped>
#main-screen {
    width: 100%;
    height: 100%;
    background-size: 110% 110%;
}

.container {
  width: 100vw;
  height: 100vh;
  position: absolute;
  top: 0;
}
</style>