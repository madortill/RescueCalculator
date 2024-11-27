<template>
    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 451.62 754" :class="isDark ? 'dark-mode' : 'light-mode'">
      <g id="Layer_1" data-name="Layer 1">
        <rect class="background" width="451.62" height="754" />
      </g>
      <g id="Layer_3" data-name="Layer 3">
        <g class="button">
            <ellipse class="cls-1" cx="164.37" cy="589.51" rx="41.16" ry="39.8" />
            <text  :class="['cls-4', { 'light-text': !isDark }]"  transform="translate(152.14 601.49) scale(.97 1)">
                <tspan x="24" y="2">2</tspan>
            </text>
        </g>
        <g class="button">
            <ellipse class="cls-1" cx="163.65" cy="480.23" rx="41.16" ry="39.8" />
            <text  :class="['cls-4', { 'light-text': !isDark }]"  transform="translate(151.42 497.16) scale(.97 1)">
             <tspan x="24" y="0">5</tspan>
            </text>
        </g>
        <g class="button">
            <ellipse class="cls-1" cx="166.02" cy="372.21" rx="41.16" ry="39.8" />
            <text  :class="['cls-4', { 'light-text': !isDark }]"  transform="translate(153.79 387.4) scale(.97 1)">
                <tspan x="24" y="0">8</tspan>
            </text>
        </g>
        <g class="button">    
        <ellipse class="cls-1" cx="57.64" cy="589.63" rx="41.16" ry="39.8" />
            <text :class="['cls-4', { 'light-text': !isDark }]"  transform="translate(45.41 602.7) scale(.97 1)">
                <tspan x="24" y="2">1</tspan>
            </text>
        </g>
        <g class="button">
            <ellipse class="cls-1" cx="57.38" cy="480.83" rx="41.16" ry="39.8" />
            <text  :class="['cls-4', { 'light-text': !isDark }]"  transform="translate(45.15 495.63) scale(.97 1)">
                <tspan x="24" y="0">4</tspan>
            </text>
        </g>
        <g class="button">
            <ellipse class="cls-1" cx="57.51" cy="370.38" rx="41.16" ry="39.8" />
            <text  :class="['cls-4', { 'light-text': !isDark }]" transform="translate(45.28 387.26) scale(.97 1)">
                <tspan x="24" y="0">7</tspan>
            </text>
        </g>
        <g class="button">
            <rect class="cls-1" x="17.62" y="658.76" width="296" height="74.43" rx="28.45" ry="28.45" />
            <text  :class="['cls-4', { 'light-text': !isDark }]"  transform="translate(45.57 712.34) scale(.98 1)">
                <tspan x="24" y="0">0</tspan>
            </text>
        </g>
        <g class="button">
            <ellipse class="cls-1" cx="270.76" cy="587.73" rx="41.16" ry="39.8" />
            <text  :class="['cls-4', { 'light-text': !isDark }]"  transform="translate(258.53 602.21) scale(.97 1)">
                <tspan x="24" y="2">3</tspan>
            </text>
        </g>
        <g class="button">
            <ellipse class="cls-1" cx="271.34" cy="481.08" rx="41.16" ry="39.8" />
            <text  :class="['cls-4', { 'light-text': !isDark }]"  transform="translate(259.11 495.87) scale(.97 1)">
                <tspan x="24" y="0">6</tspan>
            </text>
        </g>
        <g class="button">
            <ellipse class="cls-1" cx="273.57" cy="372.42" rx="41.16" ry="39.8" />
            <text :class="['cls-4', { 'light-text': !isDark }]"  transform="translate(261.34 387.53) scale(.97 1)">
                <tspan x="24" y="0">9</tspan>
            </text>
        </g>
        <g class="button">
            <ellipse class="cls-5" cx="382.97" cy="481.83" rx="42.58" ry="40.72" />
            <text  class="cls-4 differentSize" transform="translate(356.1 493.85) scale(.98 1)">
                <tspan x="57" y="-3">מחק</tspan>
            </text>
        </g>
        <g class="button">
            <ellipse class="cls-5" cx="382.17" cy="376.34" rx="42.58" ry="40.72" />
            <text class="cls-3" transform="translate(367.73 393.04) scale(.98 1)">
                <tspan x="29" y="2">=</tspan>
            </text>
        </g>
        <g class="button" v-if="!MKfound" @click=" this.$emit('clickedBtn', 'ground');">
            <rect class="cls-6" x="82.42" y="197.43" width="69.41" height="151.42" rx="17.78" ry="17.78" transform="translate(-156.02 390.26) rotate(-90)" />
            <text class="cls-2" transform="translate(56.51 281.72) scale(1.06 1)">
                <tspan x="104" y="0"  :style="{ fontSize: 'calc(15px + 3vw)' }">סוג קרקע</tspan>
            </text>
        </g>

        <g v-else>
            <g class="button">
        `    <rect  x="82.42" y="177.43" width="69.41" height="87.42" rx="17.78" ry="17.78" transform="translate(-156.02 390.26) rotate(-90)" :class="isDark ? 'dark-button' : 'light-button'" />
            <text class="cls-2" :transform="'translate(' + (82.42 + 69.41 / -4.2) + ',' + (177.43 + 87.42 / 0.9) + ') scale(1.06 1)'" text-anchor="middle" alignment-baseline="middle" :class="isDark ? 'dark-text' : 'light-text'">
                <tspan :x="0" :y="0" :style="{ fontSize: 'calc(13px + 4vw)'}">{{ MKinfo.factor }}</tspan>
                <tspan :x="0" :y="20" :style="{ fontSize: 'calc(13px + 1vw)'}">{{ MKinfo.name }}</tspan>
            </text>
            </g>`


            <g class="button" @click=" this.$emit('clickedBtn', 'ground');">
                <rect class="cls-6" x="82.42" y="287.43" width="69.41" height="127.42" rx="17.78" ry="17.78" transform="translate(-156.02 390.26) rotate(-90)" />
                <text class="cls-2" transform="translate(56.51 281.72) scale(1.06 1)">
                    <tspan x="179" y="0" :style="{ fontSize: 'calc(15px + 3vw)' }">סוג קרקע</tspan>
                </text>
            </g>
            
        </g>
        
        <g class="button" @click="this.$emit('clickedBtn', 'degree');">
            <rect class="cls-5" x="298.22" y="599.02" width="170.8" height="96" rx="29.2" ry="29.2" transform="translate(-263.4 1030.64) rotate(-90)" />
            <g transform="translate(0, 0)">
                <text class="cls-2" text-anchor="middle" x="380" y="635">שינוי</text>
                <text class="cls-2" text-anchor="middle" x="380" y="675">זוית</text>
            </g>
        </g>
        <g id="formula-btn" class="button">
            <rect class="cls-6" x="299.8" y="214.75" width="69.41" height="141.42" rx="17.78" ry="17.78" transform="translate(61.05 607.96) rotate(-90)" />
            <text class="cls-2" transform="translate(281.08 282.75) scale(1.06 1)">
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
  