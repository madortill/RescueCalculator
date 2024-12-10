<template>
  <div div id="main-screen" :style="{ backgroundColor: darkMode ? 'black' : 'white' }">

    <div class="loader" v-if="showLoader" :class="darkMode ? 'dark-mode' : 'light-mode'">
        <img class="gif" src="/public/media/blackonwhite-ezgif.com-gif-maker.gif" alt="Loading..."/>
        <!-- מיד מתחילים... -->
        <p class="loader-text"> מיד מתחילים... </p>
    </div> 

    <div v-else>
        <Calculator2SVG 
          class="container"
          :key="containerKey" 
          :darkMode="darkMode" 
          :MKinfo = "MKinfo"
          :degreeInfo = "degreeInfo"
          :clickedStates="clickedStates"
          @chosen-btn="handleChosenBtn" 
          @clickedBtn="handleClicked">
      </Calculator2SVG>
    

      <CalculatingContainer 
        class="container"
        :key="containerKey"
        :darkMode="darkMode"
        :chosenValueString="chosenValueString"
        :stringBtn="stringBtn"
        :clickedStates="clickedStates" 
        @clickedBtn="handleClicked"
        @reset="reset"
        @MKinfo="foundMK"
        @DegreeInfo="foundDegree"
        >
       </CalculatingContainer>
    </div>

   
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
      degreeInfo: null,
      counter: 0,
      showLoader: true,
      containerKey: 0,
   };
  },
  computed: {
  },
  methods: {
    foundMK(ground) {
      this.MKinfo = ground;
    },
    foundDegree(degree) {
      this.degreeInfo = degree;
    },
    handleClicked(btn) {
      const currentState = this.clickedStates[btn];
      Object.keys(this.clickedStates).forEach(name => {
        this.clickedStates[name] = false;
      });
      this.clickedStates[btn] = !currentState;
    },

    handleChosenBtn(chosenBtn) { 
      this.counter++;
      // console.log(chosenBtn);
      if (Number(chosenBtn) || Number(chosenBtn) === 0) {
          this.chosenValueString = String(chosenBtn)+String(this.counter);
      } else {
        this.stringBtn = String(chosenBtn)+String(this.counter);
        // console.log(this.stringBtn);
       }
    },
    reset() {
      this.resetCalc = true;
      this.chosenValueString = null;
      this.stringBtn = '';
      this.clickedStates = {
        formula: false,
        ground: false,
        degree: false,
      };
      this.MKinfo = null;
      this.degreeInfo = null;
      this.containerKey++;

      setTimeout( () => {
        this.resetCalc = false;
      }, 100);
    }
  },
  mounted() {
    setTimeout(() => {
            this.showLoader = false;
        }, 4500);
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

/* טוען */
.loader {
    position: fixed;
    z-index: 99;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    font-size: 2em;
    font-weight: 800;
}

.dark-mode .loader {
  background-color: black;
}

.gif {
  width: 100%;
  z-index: 1000000;
}

.loader-text {
  font-size: 2rem;
}

.dark-mode .loader-text {
  color: white;
}

.light-mode .loader-text {
  color: #005051b3;
}

.dark-mode .gif {
  filter: brightness(1.9) contrast(1.2) sepia(1) saturate(400%) hue-rotate(-10deg); /* Makes it orange */
}

.light-mode .gif {
  filter: brightness(1.2) contrast(1.2) sepia(1) saturate(300%) hue-rotate(-60deg); /* Makes it pink */
}

</style>