<template>
  <div div id="main-screen" :style="{ backgroundColor: darkMode ? 'black' : 'white' }">

    <div class="loader" v-if="showLoader" :class="darkMode ? 'dark-mode' : 'light-mode'">
        <img class="gif" src="../assets/media/blackonwhite-ezgif.com-gif-maker.gif" alt="Loading..."/>
        <!-- מיד מתחילים... -->
        <p class="loader-text"> מיד מתחילים... </p>
    </div> 

    <div v-else>
        <Calculator2SVG 
          class="container" 
          :darkMode="darkMode" 
          :MKinfo = "MKinfo"
          :degreeInfo = "degreeInfo"
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

    // changeMode() {
    //   this.darkMode = !this.darkMode;
    // },
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
  },
  mounted() {
    setTimeout(() => {
            this.showLoader = false;
        }, 3000);
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
  width: 110%
}

.loader-text {
  font-size: 2rem;
}

.dark-mode .loader-text {
  color: white;
}
</style>