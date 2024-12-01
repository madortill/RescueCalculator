<template>
  <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 451.62 754" :class="isDark ? 'dark-mode' : 'light-mode'">
    <g id="Layer_1" data-name="Layer 1">
      <rect class="background" width="450" height="600" />
    </g>
    <g id="Layer_3" data-name="Layer 3">
      <g class="button">
          <ellipse class="cls-1" cx="165" cy="570" rx="40" ry="40" />
          <text  :class="['cls-4', { 'light-text': !isDark }]"  transform="translate(150 600) scale(.999)">
              <tspan x="25" y="-15">2</tspan>
          </text>
      </g>
      <g class="button">
          <ellipse class="cls-1" cx="165" cy="460" rx="40" ry="40" />
          <text  :class="['cls-4', { 'light-text': !isDark }]"  transform="translate(150 495) scale(.999)">
           <tspan x="25" y="-17">5</tspan>
          </text>
      </g>
      <g class="button">
          <ellipse class="cls-1" cx="165" cy="350" rx="40" ry="40" />
          <text  :class="['cls-4', { 'light-text': !isDark }]"  transform="translate(150 390) scale(.999)">
              <tspan x="26" y="-24">8</tspan>
          </text>
      </g>
      <g class="button">    
      <ellipse class="cls-1" cx="55" cy="570" rx="40" ry="40" />
          <text :class="['cls-4', { 'light-text': !isDark }]"  transform="translate(45 600) scale(.999)">
              <tspan x="22" y="-15">1</tspan>
          </text>
      </g>
      <g class="button">
          <ellipse class="cls-1" cx="55" cy="460" rx="40" ry="40" />
          <text  :class="['cls-4', { 'light-text': !isDark }]"  transform="translate(45 495) scale(.999)">
              <tspan x="20" y="-18">4</tspan>
          </text>
      </g>
      <g class="button">
          <ellipse class="cls-1" cx="55" cy="350" rx="40" ry="40" />
          <text  :class="['cls-4', { 'light-text': !isDark }]" transform="translate(45 390) scale(.999)">
              <tspan x="22" y="-22">7</tspan>
          </text>
      </g>
      <g class="button">
          <rect class="cls-1" x="17" y="635" width="296" height="75" rx="28.45" ry="28.45" />
          <text  :class="['cls-4', { 'light-text': !isDark }]"  transform="translate(45 710) scale(.999)">
              <tspan x="21" y="-20">0</tspan>
          </text>
      </g>
      <g class="button">
          <ellipse class="cls-1" cx="275" cy="570" rx="40" ry="40" />
          <text  :class="['cls-4', { 'light-text': !isDark }]"  transform="translate(260 600) scale(.999)">
              <tspan x="26" y="-15">3</tspan>
          </text>
      </g>
      <g class="button">
          <ellipse class="cls-1" cx="275" cy="460" rx="40" ry="40" />
          <text  :class="['cls-4', { 'light-text': !isDark }]"  transform="translate(260 495) scale(.999)">
              <tspan x="25" y="-20">6</tspan>
          </text>
      </g>
      <g class="button">
          <ellipse class="cls-1" cx="275" cy="350" rx="40" ry="40" />
          <text :class="['cls-4', { 'light-text': !isDark }]"  transform="translate(260 390) scale(.999)">
              <tspan x="26" y="-24">9</tspan>
          </text>
      </g>
      <g class="button">
          <ellipse class="cls-5" cx="385" cy="460" rx="40" ry="40" />
          <text  class="cls-4 differentSize" transform="translate(355 495) scale(.999)">
              <tspan x="57.5" y="-25">מחק</tspan>
          </text>
      </g>
      <g class="button">
          <ellipse class="cls-5" cx="385" cy="350" rx="40" ry="40" />
          <text class="cls-3" transform="translate(365 395) scale(.999)">
              <tspan x="35" y="-25">=</tspan>
          </text>
      </g>
      <g class="button" v-if="!MKfound" @click=" this.$emit('clickedBtn', 'ground');">
          <rect class="cls-6" x="95" y="180" width="70" height="135" rx="17.78" ry="17.78" transform="translate(-150 390) rotate(-90)" />
          <text class="cls-2" transform="translate(55 280) scale(0.999)">
              <tspan x="90" y="-10"  :style="{ fontSize: 'calc(15px + 3vw)' }">סוג קרקע</tspan>
          </text>
      </g>
      <g v-else>
          <g class="button">
      `    <rect  x="94" y="166" width="70" height="90" rx="17.78" ry="17.78" transform="translate(-150 390) rotate(-90)" :class="isDark ? 'dark-button' : 'light-button'" />
          <text class="cls-2" :transform="'translate(65 265) scale(0.999)'" text-anchor="middle" alignment-baseline="middle" :class="isDark ? 'dark-text' : 'light-text'">
              <tspan :x="-5" :y="0" :style="{ fontSize: 'calc(13px + 4vw)'}">{{ MKinfo.factor }}</tspan>
              <tspan :x="-5" :y="22" :style="{ fontSize: 'calc(9px + 2vw)'}">{{ MKinfo.name }}</tspan>
          </text>
          </g>`
          <g class="button" @click=" this.$emit('clickedBtn', 'ground');">
              <rect class="cls-6" x="94" y="285" width="70" height="130" rx="17.78" ry="17.78" transform="translate(-150 390) rotate(-90)" />
              <text class="cls-2" transform="translate(55 280) scale(0.999)">
                  <tspan x="190" y="-11" :style="{ fontSize: 'calc(15px + 3vw)' }">סוג קרקע</tspan>
              </text>
          </g>
      </g>
      
      <g class="button" @click="this.$emit('clickedBtn', 'degree');">
          <rect class="cls-5" x="322.5" y="600.5" width="175" height="90" rx="29.2" ry="29.2" transform="translate(-260 1030) rotate(-90)" />
          <g transform="translate(0, 0)">
              <text class="cls-2" text-anchor="middle" x="385" y="605">שינוי</text>
              <text class="cls-2" text-anchor="middle" x="385" y="640">זוית</text>
          </g>
      </g>
      <g id="formula-btn" class="button">
          <rect class="cls-6" x="310" y="235" width="70" height="125" rx="17.78" ry="17.78" transform="translate(60 605) rotate(-90)" />
          <text class="cls-2" transform="translate(280 280) scale(0.999)">
              <tspan x="120" y="-11"  :style="{ fontSize: 'calc(15px + 3vw)'}">נוסחאות</tspan>
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