<template>
  <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 451.62 754" :class="isDark ? 'dark-mode' : 'light-mode'">
    <g id="Layer_1" data-name="Layer 1">
      <rect class="background" width="450" height="600" />
    </g>
    <g id="Layer_3" data-name="Layer 3">
      <!-- Row 1 -->
    <g class="button" :class="{'disabled': currState.formula || currState.degree || currState.ground}">
        <ellipse class="cls-1" cx="60" cy="555" rx="37" ry="37" />
        <text :class="['cls-4', { 'light-text': !isDark }]" transform="translate(75 200) scale(.999)">
            <tspan x="-5" y="370">1</tspan>
        </text>
    </g>
    <g class="button" :class="{'disabled': currState.formula || currState.degree || currState.ground}">
        <ellipse class="cls-1" cx="150" cy="555" rx="37" ry="37" />
        <text :class="['cls-4', { 'light-text': !isDark }]" transform="translate(157.5 200) scale(.999)">
            <tspan x="2.5" y="370">2</tspan>
        </text>
    </g>
    <g class="button" :class="{'disabled': currState.formula || currState.degree || currState.ground}">
        <ellipse class="cls-1" cx="245" cy="555" rx="37" ry="37" />
        <text :class="['cls-4', { 'light-text': !isDark }]" transform="translate(240 200) scale(.999)">
            <tspan x="15.5" y="370">3</tspan>
        </text>
    </g>

    <!-- Row 2 -->
    <g class="button" :class="{'disabled': currState.formula || currState.degree || currState.ground}">
        <ellipse class="cls-1" cx="60" cy="460" rx="37" ry="37" />
        <text :class="['cls-4', { 'light-text': !isDark }]" transform="translate(75 300) scale(.999)">
            <tspan x="-5" y="175">4</tspan>
        </text>
    </g>
    <g class="button" :class="{'disabled': currState.formula || currState.degree || currState.ground}">
        <ellipse class="cls-1" cx="150" cy="460" rx="37" ry="37" />
        <text :class="['cls-4', { 'light-text': !isDark }]" transform="translate(157.5 300) scale(.999)">
            <tspan x="2.5" y="175">5</tspan>
        </text>
    </g>
    <g class="button" :class="{'disabled': currState.formula || currState.degree || currState.ground}">
        <ellipse class="cls-1" cx="245" cy="460" rx="37" ry="37" />
        <text :class="['cls-4', { 'light-text': !isDark }]" transform="translate(240 300) scale(.999)">
            <tspan x="15.5" y="175">6</tspan>
        </text>
    </g>

    <!-- Row 3 -->
    <g class="button" :class="{'disabled': currState.formula || currState.degree || currState.ground}">
        <ellipse class="cls-1" cx="60" cy="362.5" rx="37" ry="37" />
        <text :class="['cls-4', { 'light-text': !isDark }]" transform="translate(75 400) scale(.999)">
            <tspan x="-5" y="-22.5">7</tspan>
        </text>
    </g>
    <g class="button" :class="{'disabled': currState.formula || currState.degree || currState.ground}">
        <ellipse class="cls-1" cx="150" cy="362.5" rx="37" ry="37" />
        <text :class="['cls-4', { 'light-text': !isDark }]" transform="translate(157.5 400) scale(.999)">
            <tspan x="2.5" y="-22.5">8</tspan>
        </text>
    </g>
    <g class="button" :class="{'disabled': currState.formula || currState.degree || currState.ground}">
        <ellipse class="cls-1" cx="245" cy="362.5" rx="37" ry="37" />
        <text :class="['cls-4', { 'light-text': !isDark }]" transform="translate(240 400) scale(.999)">
            <tspan x="15.5" y="-22.5">9</tspan>
        </text>
    </g>

    <!-- 0 Button -->
    <g class="button" :class="{'disabled': currState.formula || currState.degree || currState.ground}">
        <rect class="cls-1" x="25" y="610" width="255" height="75" rx="28.45" ry="28.45" />
        <text :class="['cls-4', { 'light-text': !isDark }]" transform="translate(160 490) scale(.999)">
            <tspan x="-90" y="175">0</tspan>
        </text>
    </g>


      <g class="button" :class="{'disabled': currState.formula || currState.degree || currState.ground}">
          <ellipse class="cls-5" cx="60" cy="267.5" rx="37" ry="37" />
          <text  class="cls-4 differentSize" :style="{ fontSize: '1.65rem  !important'}"  transform="translate(355 495) scale(.999)">
              <tspan x="-265" y="-217.5">איפוס</tspan>
          </text>
      </g>
      <g class="button" :class="{'disabled': currState.formula || currState.degree || currState.ground}">
          <ellipse class="cls-5 equal" cx="382" cy="276" rx="47" ry="47" />
          <text class="cls-3" :style="{ fontSize: '4.5rem'}" transform="translate(365 395) scale(.999)">
              <tspan x="36" y="-93">=</tspan>
          </text>
      </g>
      
      <g id="ground-btn" class="button"  @click="handleGround" :class="{'disabled': currState.ground || currState.formula}">
          <rect class="cls-5" x="477.5" y="578.5" width="100" height="110" rx="29.2" ry="29.2" transform="translate(-260 1030) rotate(-90)" />
          <g transform="translate(0, 0)">
              <text class="cls-2" text-anchor="middle" x="370" y="495">סוג</text>
              <text class="cls-2" text-anchor="middle" x="370" y="527">קרקע</text>
          </g>
      </g>

      <!-- <g id="ground-btn" class="button"  @click="handleGround" :class="{'disabled': currState.formula || currState.degree}">
          <rect class="cls-6" x="-45" y="470" width="70" height="110" rx="17.78" ry="17.78" transform="translate(-150 390) rotate(-90)" />
          <text class="cls-2" transform="translate(55 280) scale(0.999)">
              <tspan x="380" y="130">סוג קרקע</tspan>
          </text>
      </g> -->
      <g>
          <g class="button" :class="{'disabled': currState.formula || currState.degree || currState.ground}">
          <rect  x="95.5" y="375.5" width="60" height="90" rx="17.78" ry="17.78" transform="translate(-150 390) rotate(-90)" :class="isDark ? 'dark-button' : 'light-button'" />
          <text class="cls-2" :transform="'translate(65 265) scale(0.999)'" text-anchor="middle" alignment-baseline="middle"  :class="['center-text', isDark ? 'dark-text' : 'light-text']">
              <tspan v-if="MKfound" :x="205" :y="5" :style="{ fontSize: '2rem'}">{{ MKinfo.factor }}</tspan>
          </text>
          <text v-if="MKfound" class="cls-2" :transform="'translate(65 265) scale(0.999)'" text-anchor="middle" alignment-baseline="middle"  :class="['center-text', isDark ? 'dark-text' : 'light-text']">
              <tspan  :x="205" :y="25" :style="{ fontSize: '1rem'}">{{ MKinfo.name }}</tspan>
          </text>
           <text v-else class="cls-2" :transform="'translate(65 265) scale(0.999)'" text-anchor="middle" alignment-baseline="middle"  :class="['center-text', isDark ? 'dark-text' : 'light-text']">
              <tspan :x="200" :y="-5" :style="{ fontSize: '1rem'}">לא נבחר</tspan>
              <tspan :x="205" :y="15" :style="{ fontSize: '1rem'}">סוג קרקע</tspan>
           </text>
          </g>
      </g>
      
      <g id="degree-btn" class="button" :class="{'disabled': currState.ground || currState.formula}">
          <rect class="cls-5" x="342.5" y="578.5" width="110" height="110" rx="29.2" ry="29.2" transform="translate(-260 1030) rotate(-90)" />
          <g transform="translate(0, 0)">
              <text class="cls-2" text-anchor="middle" x="370" y="628">שינוי</text>
              <text class="cls-2" text-anchor="middle" x="370" y="660">זוית</text>
          </g>
      </g>

      <g>
          <g class="button" :class="{'disabled': currState.formula || currState.degree || currState.ground}">
          <rect  x="95.5" y="265.5" width="60" height="90" rx="17.78" ry="17.78" transform="translate(-150 390) rotate(-90)" :class="isDark ? 'dark-button' : 'light-button'" />
          <text class="cls-2" :transform="'translate(65 265) scale(0.999)'" text-anchor="middle" alignment-baseline="middle"  :class="['center-text', isDark ? 'dark-text' : 'light-text']">
              <tspan v-if="degreeFound" :x="95" :y="5" :style="{ fontSize: '2rem'}">{{ degreeInfo.factor }}</tspan>
          </text>
          <text v-if="degreeFound" class="cls-2" :transform="'translate(65 265) scale(0.999)'" text-anchor="middle" alignment-baseline="middle"  :class="['center-text', isDark ? 'dark-text' : 'light-text']">
            <tspan :x="95" :y="25" :style="{ fontSize: '1rem'}"> {{ degreeInfo.degree }} מעלות</tspan>     
          </text>
          <text v-else class="cls-2" :transform="'translate(65 265) scale(0.999)'" text-anchor="middle" alignment-baseline="middle"  :class="['center-text', isDark ? 'dark-text' : 'light-text']">
            <tspan :x="90" :y="-5" :style="{ fontSize: '1rem'}">לא נבחר</tspan>
            <tspan :x="100" :y="15" :style="{ fontSize: '1rem'}">שינוי זוית</tspan>
          </text>
          </g>
      </g>

      <g id="formula-btn" class="button" :class="{'disabled': currState.ground || currState.degree}">
          <rect class="cls-5" x="177.5" y="258.5" width="75" height="110" rx="17.78" ry="17.78" transform="translate(60 605) rotate(-90)" />
          <text class="cls-2" transform="translate(280 280) scale(0.999)">
              <tspan x="141" y="120">נוסחאות</tspan>
          </text>
      </g> 
    </g>
  </svg>
</template>

<script>
  export default {
  name: "calculator-svg",
  props: ['darkMode','MKinfo', 'degreeInfo', 'clickedStates'],
  data() {
      return {
          childrenArr: [],
          chosenBtn: '',
          currClickedStates: {
            formula: undefined,
            ground: undefined,
            degree: undefined
          }
      }
  },
  computed: {
      isDark() {
      return this.darkMode;
      },
      MKfound() {
      return this.MKinfo;
      },
      degreeFound() {
      return this.degreeInfo;
      },
      currState() {
        this.currClickedStates.formula = this.clickedStates.formula;
        this.currClickedStates.ground = this.clickedStates.ground;
        this.currClickedStates.degree = this.clickedStates.degree;
        return this.currClickedStates;
      }
  },
  methods: {
    handleGround() {
      this.$emit('clickedBtn', 'ground');
        this.addListeners();
    },
    handleFormula() {
      this.$emit('clickedBtn', 'formula');
    },
    addListeners() {
      const buttonGroups = document.querySelectorAll(".button");
      const formulaBtn = document.getElementById("formula-btn");
      const degreeBtn = document.getElementById("degree-btn");
      degreeBtn.addEventListener("click", () => {
        this.$emit('clickedBtn', 'degree')});
      formulaBtn.addEventListener("click", () => {
        this.handleFormula();
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
  };
</script>

<style scoped>
.dark-mode .cls-1 {
  fill: #4d4d4d;
}

.dark-mode .cls-2 {
  font-family: 'OpenSansHebrew';
  font-size: 1.78rem;
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
  font-size: 3.5rem;
}

.dark-mode .cls-3,
.dark-mode .cls-4 {
  font-family: 'Heebo';
}

.dark-mode .cls-4 {
  font-size: 2.4rem;
}

.dark-mode .cls-6 {
  fill: #fbb03b;
}
.dark-mode .background {
fill: #000; 
}

.dark-mode .equal {
  fill: #ba996b;
}


.light-mode .cls-1 {
  fill: #2e4a4a61;
}

.light-mode .cls-2 {
  font-family: 'OpenSansHebrew';
  font-size: 1.78rem;
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
  font-size: 3.5rem;
}

.light-mode .cls-3,
.light-mode .cls-4 {
  font-family: 'Heebo';
}

.light-mode .cls-6 {
  fill: #e6e6e6;
}
.light-mode  .light-text {
  fill: #ffffff;
  font-size: 2.4rem;
  opacity: 1;
}

.light-mode  .differentSize,
.dark-mode  .differentSize {
  font-size: 1.9rem !important;
  font-family: 'OpenSansHebrew';
}
.light-mode .background {
fill: #fff; 
}


.light-button {
  fill: rgba(171, 53, 53, 0.651);
}

.dark-button {
  fill: #d9911c;
}

.button.disabled {
  opacity: 0.5;
  pointer-events: none;
}



</style>