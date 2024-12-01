<template>
  <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 451.62 754" :class="isDark ? 'dark-mode' : 'light-mode'">
    <g id="Layer_1" data-name="Layer 1">
      <rect class="background" width="450" height="600" />
    </g>
    <g id="Layer_3" data-name="Layer 3">
      <g class="button">
          <ellipse class="cls-1" cx="165" cy="570" rx="40" ry="40" />
          <text  :class="['cls-4', { 'light-text': !isDark }]"  transform="translate(150 600) scale(.999)">
              <tspan x="24" y="2">2</tspan>
          </text>
      </g>
      <g class="button">
          <ellipse class="cls-1" cx="165" cy="460" rx="40" ry="40" />
          <text  :class="['cls-4', { 'light-text': !isDark }]"  transform="translate(150 495) scale(.999)">
           <tspan x="24" y="0">5</tspan>
          </text>
      </g>
      <g class="button">
          <ellipse class="cls-1" cx="165" cy="350" rx="40" ry="40" />
          <text  :class="['cls-4', { 'light-text': !isDark }]"  transform="translate(150 390) scale(.999)">
              <tspan x="24" y="0">8</tspan>
          </text>
      </g>
      <g class="button">    
      <ellipse class="cls-1" cx="55" cy="570" rx="40" ry="40" />
          <text :class="['cls-4', { 'light-text': !isDark }]"  transform="translate(45 600) scale(.999)">
              <tspan x="24" y="2">1</tspan>
          </text>
      </g>
      <g class="button">
          <ellipse class="cls-1" cx="55" cy="460" rx="40" ry="40" />
          <text  :class="['cls-4', { 'light-text': !isDark }]"  transform="translate(45 495) scale(.999)">
              <tspan x="24" y="0">4</tspan>
          </text>
      </g>
      <g class="button">
          <ellipse class="cls-1" cx="55" cy="350" rx="40" ry="40" />
          <text  :class="['cls-4', { 'light-text': !isDark }]" transform="translate(45 390) scale(.999)">
              <tspan x="24" y="0">7</tspan>
          </text>
      </g>
      <g class="button">
          <rect class="cls-1" x="15" y="640" width="296" height="75" rx="28.45" ry="28.45" />
          <text  :class="['cls-4', { 'light-text': !isDark }]"  transform="translate(45 710) scale(.999)">
              <tspan x="24" y="0">0</tspan>
          </text>
      </g>
      <g class="button">
          <ellipse class="cls-1" cx="270" cy="570" rx="40" ry="40" />
          <text  :class="['cls-4', { 'light-text': !isDark }]"  transform="translate(260 600) scale(.999)">
              <tspan x="24" y="2">3</tspan>
          </text>
      </g>
      <g class="button">
          <ellipse class="cls-1" cx="270" cy="460" rx="40" ry="40" />
          <text  :class="['cls-4', { 'light-text': !isDark }]"  transform="translate(260 495) scale(.999)">
              <tspan x="24" y="0">6</tspan>
          </text>
      </g>
      <g class="button">
          <ellipse class="cls-1" cx="270" cy="350" rx="40" ry="40" />
          <text :class="['cls-4', { 'light-text': !isDark }]"  transform="translate(260 390) scale(.999)">
              <tspan x="24" y="0">9</tspan>
          </text>
      </g>
      <g class="button">
          <ellipse class="cls-5" cx="380" cy="460" rx="40" ry="40" />
          <text  class="cls-4 differentSize" transform="translate(355 495) scale(.999)">
              <tspan x="57" y="-3">מחק</tspan>
          </text>
      </g>
      <g class="button">
          <ellipse class="cls-5" cx="380" cy="350" rx="40" ry="40" />
          <text class="cls-3" transform="translate(365 395) scale(.999)">
              <tspan x="29" y="2">=</tspan>
          </text>
      </g>
      <g class="button" v-if="!MKfound" @click=" this.$emit('clickedBtn', 'ground');">
          <rect class="cls-6" x="80" y="200" width="70" height="150" rx="17.78" ry="17.78" transform="translate(-150 390) rotate(-90)" />
          <text class="cls-2" transform="translate(55 280) scale(0.999)">
              <tspan x="104" y="0"  :style="{ fontSize: 'calc(15px + 3vw)' }">סוג קרקע</tspan>
          </text>
      </g>
      <g v-else>
          <g class="button">
      `    <rect  x="80" y="180" width="70" height="90" rx="17.78" ry="17.78" transform="translate(-150 390) rotate(-90)" :class="isDark ? 'dark-button' : 'light-button'" />
          <text class="cls-2" :transform="'translate(65 265) scale(0.999)'" text-anchor="middle" alignment-baseline="middle" :class="isDark ? 'dark-text' : 'light-text'">
              <tspan :x="-2" :y="26" :style="{ fontSize: 'calc(13px + 4vw)'}">{{ MKinfo.factor }}</tspan>
              <tspan :x="-6" :y="2" :style="{ fontSize: 'calc(9px + 2vw)'}">{{ MKinfo.name }}</tspan>
          </text>
          </g>`
          <g class="button" @click=" this.$emit('clickedBtn', 'ground');">
              <rect class="cls-6" x="80" y="290" width="70" height="130" rx="17.78" ry="17.78" transform="translate(-150 390) rotate(-90)" />
              <text class="cls-2" transform="translate(55 280) scale(0.999)">
                  <tspan x="179" y="0" :style="{ fontSize: 'calc(15px + 3vw)' }">סוג קרקע</tspan>
              </text>
          </g>
      </g>
      
      <g class="button" @click="this.$emit('clickedBtn', 'degree');">
          <rect class="cls-5" x="300" y="580" width="170.8" height="96" rx="29.2" ry="29.2" transform="translate(-260 1030) rotate(-90)" />
          <g transform="translate(0, 0)">
              <text class="cls-2" text-anchor="middle" x="380" y="635">שינוי</text>
              <text class="cls-2" text-anchor="middle" x="380" y="675">זוית</text>
          </g>
      </g>
      <g id="formula-btn" class="button">
          <rect class="cls-6" x="300" y="214.75" width="70" height="140" rx="17.78" ry="17.78" transform="translate(60 605) rotate(-90)" />
          <text class="cls-2" transform="translate(280 280) scale(0.999)">
              <tspan x="106" y="0"  :style="{ fontSize: 'calc(15px + 3vw)'}">נוסחאות</tspan>
          </text>
      </g> 
    </g>
  </svg>
</template>

<script>
  export default {
  name: "calculator-svg",
  props: ['darkMode','MKinfo'],
  data() {
      return {
          childrenArr: [],
          chosenBtn: '',
      }
  },
  computed: {
      isDark() {
      return this.darkMode;
      },
      MKfound() {
          return this.MKinfo;
      }
  },
  methods: {
      handleFormulaSelection() {
          const buttonGroups = document.querySelectorAll(".button");
          const formulaBtn = document.getElementById("formula-btn");
          // formulaBtn.classList.add("pulsing");
          // // Initially disable all buttons except "formula-btn"
          // buttonGroups.forEach((button) => {
          //     if (button !== formulaBtn) {
          //     button.classList.add("disabled");
          //     }
          // });
          // Enable all buttons when "formula-btn" is clicked
          formulaBtn.addEventListener("click", () => {
              this.$emit('clickedBtn', 'formula');
              buttonGroups.forEach((button) => {
              button.addEventListener("click", this.getInfo);
              });
          });
      },
      getInfo(event) {
          if (this.childrenArr.length === 0) {
              this.childrenArr = event.currentTarget.children;
          }
          for (let i = 0; i < this.childrenArr.length; i++) {
              if ((this.childrenArr[i].children).length > 1) {
                  this.childrenArr = this.childrenArr[i].children;
                  this.getInfo(this.childrenArr);
              } else if (this.childrenArr[i].tagName === 'text' ) {
                  this.chosenBtn = this.childrenArr[i].textContent;
                  this.childrenArr = [];
                  this.$emit('chosen-btn', this.chosenBtn);
          }
      }
  },
  },
  mounted() {
       this.handleFormulaSelection();
  },
  };
</script>

<style scoped>
/* Dark mode styles */
.dark-mode .cls-1 {
  fill: #4d4d4d;
}

.dark-mode .cls-2 {
  font-family: 'OpenSansHebrew';
  font-size: calc(15px + 4vw);
}

.dark-mode .cls-2,
.dark-mode .cls-3,
.dark-mode .cls-4 {
  fill: #fff;
}

.dark-mode .cls-5 {
  fill: #b3b3b3;
}

.dark-mode .cls-3 {
  font-size: calc(15px + 10vw);
}

.dark-mode .cls-3,
.dark-mode .cls-4 {
  font-family: 'Heebo';
}

.dark-mode .cls-4 {
  font-size: calc(15px + 7vw);
}

.dark-mode .cls-6 {
  fill: #fbb03b;
}
.dark-mode .background {
fill: #000; /* Change to white or any color you want for dark mode */
}
/* Light mode styles */
.light-mode .cls-1 {
  /* fill: #dae6e6; */
  fill: #2e4a4a61;
}

.light-mode .cls-2 {
  font-family: 'OpenSansHebrew';
  font-size: calc(15px + 4vw);
}

.light-mode .cls-2,
.light-mode .cls-3,
.light-mode .cls-4 {
  fill: #b33e4e;
  opacity: 0.75;
}

.light-mode .cls-5 {
  fill: #e6e6e6;
}

.light-mode .cls-3 {
  font-size: calc(15px + 10vw);
}

.light-mode .cls-3,
.light-mode .cls-4 {
  font-family: 'Heebo';
}

.light-mode .cls-4 {
  font-size: calc(15px + 7vw);
}

.light-mode .cls-6 {
  fill: #e6e6e6;
}
.light-mode  .light-text {
  /* fill: #004f51; */
  fill: #ffffff;
  font-size: calc(15px + 7vw);
  opacity: 1;
}

.light-mode  .differentSize,
.dark-mode  .differentSize {
  font-size: calc(15px + 4vw) !important;
  font-family: 'OpenSansHebrew';
}
.light-mode .background {
fill: #fff; /*                                           to black or any color you want for light mode */
}
.disabled {
  pointer-events: none; /* Makes the button non-clickable */
  filter: grayscale(100%);
  opacity: 0.5;
}
.pulsing {
position: relative; /* Ensures the button is positioned within its container */
animation: pulse 2s infinite;
}
@keyframes pulse {
0%, 100% {
  transform: scale(0.995);
}
50% {
  transform: scale(1.005);
}
}
/* Light Mode Button */
.light-button {
  fill: rgba(171, 53, 53, 0.651);
 /* Fill color for the button in light mode */
}
/* Dark Mode Button */
.dark-button {
fill: rgb(196, 154, 122); /* Fill color for the button in dark mode */
}
</style>


















<!-- <template>
    <svg xmlns="http://www.w3.org/2000/svg" :viewBox="viewBox" :width="width" :height="height">
      <g id="Layer_1" data-name="Layer 1">
        <rect width="528" height="754" rx="49.97" ry="49.97" />
      </g>
      <g id="Layer_3" data-name="Layer 3">
        <ellipse class="cls-6" cx="203.38" cy="580.21" rx="40.29" ry="37.21" />
        <ellipse class="cls-6" cx="203.49" cy="473.57" rx="40.29" ry="37.21" />
        <ellipse class="cls-6" cx="203.64" cy="369.21" rx="40.29" ry="37.21" />
        <g>
          <ellipse class="cls-6" cx="317.71" cy="369.27" rx="40.29" ry="37.21" />
          <ellipse class="cls-6" cx="317.71" cy="473.57" rx="40.29" ry="37.21" />
          <ellipse class="cls-6" cx="317.71" cy="577.87" rx="40.29" ry="37.21" />
        </g>
        <ellipse class="cls-6" cx="88.29" cy="580.21" rx="40.29" ry="37.21" />
        <ellipse class="cls-6" cx="89.29" cy="473.57" rx="40.29" ry="37.21" />
        <ellipse class="cls-6" cx="89.29" cy="369.33" rx="40.29" ry="37.21" />
        <rect class="cls-6" x="49" y="643" width="178" height="68" rx="28.45" ry="28.45" />
        <ellipse class="cls-6" cx="439.52" cy="677.39" rx="40.29" ry="37.21" />
        <ellipse class="cls-6" cx="317.52" cy="677.39" rx="40.29" ry="37.21" />
        <rect class="cls-5" x="405.21" y="311.79" width="69.57" height="134" rx="28.45" ry="28.45" transform="translate(61.21 818.79) rotate(-90)" />
        <rect class="cls-5" x="405.21" y="513.21" width="69.57" height="134" rx="28.45" ry="28.45" transform="translate(-140.21 1020.21) rotate(-90)" />
        <rect class="cls-5" x="405.21" y="409" width="69.57" height="134" rx="28.45" ry="28.45" transform="translate(-36 916) rotate(-90)" />
      </g>
      <g id="Layer_2" data-name="Layer 2">
        <rect class="cls-1" x="33" y="-33" width="466" height="274" rx="27.62" ry="27.62" />
        <text class="cls-2" transform="translate(100 595)">1</text>
        <text class="cls-2" transform="translate(215 595)">2</text>
        <text class="cls-2" transform="translate(100 490)">4</text>
        <text class="cls-2" transform="translate(330 595)">3</text>
        <text class="cls-2" transform="translate(215 490)">5</text>
        <text class="cls-2" transform="translate(330 490)">6</text>
        <text class="cls-2" transform="translate(100 385)">7</text>
        <text class="cls-2" transform="translate(215 385)">8</text>
        <text class="cls-2" transform="translate(330 385)">9</text>
        <text class="cls-2" transform="translate(100 695)">0</text>
        <text class="cls-4" transform="translate(347 687)">מחק</text>
        <text class="cls-2" transform="translate(450 695)">=</text>
        <text class="cls-3" transform="translate(487 385)">נוסחאות</text>
        <text class="cls-3" transform="translate(495 485)">סוג קרקע</text>
        <text class="cls-3" transform="translate(495 587)">שינוי זוית</text>
      </g>
    </svg>
  </template>
  
  <script>
  export default {
    // name: "SvgComponent",
    props: {
      width: {
        type: String,
        default: "528px",
      },
      height: {
        type: String,
        default: "754px",
      },
      viewBox: {
        type: String,
        default: "0 0 528 754",
      },
    },
  };
  </script>
  
  <style>
  .cls-1 {
    fill: #000000c6;
    opacity: 0.63;
  }
  .cls-2 {
    font-size: 48px;
  }
  .cls-2, .cls-3, .cls-4 {
    fill: #fff;
  }
  .cls-2, .cls-4 {
    font-family: Heebo-Thin, Heebo;
    font-weight: 200;
  }
  .cls-3 {
    font-family: Heebo-Regular, Heebo;
    font-size: 28px;
  }
  .cls-5 {
    fill: #f7931e;
  }
  .cls-4 {
    font-size: 34px;
  }
  .cls-6 {
    fill: #c4c3c2;
  }
</style> -->