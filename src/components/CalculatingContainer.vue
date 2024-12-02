<template>
    <div id="calculating-container" >
        <div :class="darkMode ? 'dark-mode' : 'light-mode'">
            <div v-if="!MKnumber && !clickedStates.ground" class='guidance'>בחרו סוג קרקע</div>
            <div v-else-if="showGuidance && !chosenFormula && !clickedStates.formula && !clickedStates.ground" class='guidance'>בחרו נוסחא</div>
        </div>
        
        <div class="ground-container" v-show="clickedStates.ground" :class="darkMode ? 'dark-mode' : 'light-mode'">
            <div
                class="item"
                v-for="(ground, index) in groundTypesArr" 
                :key="index" 
                @click="chooseGround(ground)">
                {{ ground.name }}
            </div>
        </div>

        <div class="formula-container" v-show="clickedStates.formula" :class="darkMode ? 'dark-mode' : 'light-mode'">
            <div 
                class="formula-options" 
                v-for="(formula, index) in formulasArr" 
                :key="index" 
                @click="chooseFormula(formula)">
                {{ formula.name }}
            </div>
        </div>
        
        <div class="charStyle" :class="darkMode ? 'dark' : 'light'" v-show="!clickedStates.formula && !clickedStates.ground">
            {{ chosenFormula.name }}
        </div>
        <div class="calc" ref="formulaContainer" v-show="!clickedStates.formula && !clickedStates.ground">
            <div v-html="renderFormula()"></div>
        </div>
    </div>
</template>

<script>

export default {
    name: "calculating-container",
    props: ['chosenBtn', 'clickedStates', 'darkMode',], 
    data() {
      return {
        showGuidance: false,
        MKnumber: null,
        MTSnumber: null,
        degreeNum: null,
        safetyFactor: 1.25,
        formulasArrOriginal: [
            {name: 'התנגדות לחילוץ עד 45 מעלות',
            formula: this.safetyFactor * ((this.MKnumber * this.MTSnumber) + (this.MTSnumber * this.degreeNum / 60))},
            {name: 'התנגדות לחילוץ מעל 45 מעלות',
            formula: this.safetyFactor * ((this.MKnumber * this.MTSnumber) + this.MTSnumber)},
            {name: 'התנגדות לחילוץ במישור',
            formula: this.safetyFactor * ((this.MKnumber * this.MTSnumber))},
            {name: 'התנגדות להיפוך - חוק היפוך הרכב',
            formula: (this.MTSnumber * 2 / 3)}
        ],
        formulasArr: [
            {
                name: 'התנגדות לחילוץ עד 45 מעלות',
                formula: 'safetyFactor * ((MKnumber * MTSnumber) + (MTSnumber * degreeNum / 60))'
            },
            {
                name: 'התנגדות לחילוץ מעל 45 מעלות',
                formula: 'safetyFactor * ((MKnumber * MTSnumber) + MTSnumber)'
            },
            {
                name: 'התנגדות לחילוץ במישור',
                formula: 'safetyFactor * (MKnumber * MTSnumber)'
            },
            {
                name: 'התנגדות להיפוך - חוק היפוך הרכב',
                formula: '(MTSnumber * 2 / 3)'
            }
        ],
        groundTypesArr: [
            {name: 'כביש', factor: 0.04},
            {name: 'אדמה קשה', factor: 0.1},
            {name: 'חצץ', factor: 0.2},
            {name: 'חול', factor: 0.25},
            {name: 'בוץ קל', factor: 0.333},
            {name: 'בוץ כבד', factor: 0.5},
            {name: 'בוץ דביק', factor: 0.66}
        ],
        degreeFactorsArr: [
            {degree: 180, factor: 1},
            {degree: 120, factor: 1},
            {degree: 90, factor: 1.4},
            {degree: 60, factor: 1.7},
            {degree: 30, factor: 2},
        ],
        chosenFormula: '',
        chosenCalc: null
      };
    },
    methods: {
        chooseFormula(formula) {
            setTimeout(() => {
                this.chosenFormula = formula;
                this.$emit("clickedBtn", "formula");
                // this.$emit("resetButtonState")
            },750)
            
        },
        chooseGround(ground) {
            setTimeout(() => {
                this.MKnumber = ground.factor;
                this.showGuidance = true;
                this.$emit("MKinfo", ground);
                this.$emit("clickedBtn", "ground");
                // this.$emit("resetButtonState");
            },750)  
        },
        renderFormula() {
            if (!this.chosenFormula || typeof this.chosenFormula.formula !== 'string') {
                return ' '; // "Select a formula" in Hebrew
            }

            let formula = this.chosenFormula.formula;

            const variableLabels = {
                MKnumber: 'מקדם קרקע',
                MTSnumber: 'משקל ציוד',
                degreeNum: 'מקדם הזווית',
                safetyFactor: 'מקדם בטיחות'
            };

            const variables = {
                MKnumber: this.MKnumber,
                MTSnumber: this.MTSnumber,
                degreeNum: this.degreeNum,
                safetyFactor: this.safetyFactor
            };

            Object.keys(variables).forEach((key) => {
                const value =
                    variables[key] !== null
                        ? variables[key]
                        : `<span class="placeholder" data-var="${key}">${variableLabels[key]}</span>`;
                formula = formula.split(key).join(value);
            });

            return formula;
        },

        handlePlaceholderClick(event) {
            const variable = event.target.getAttribute('data-var');
            if (!variable) return;

            const value = prompt(`הכנס ערך עבור ${variable}`);
            if (!isNaN(value)) {
                this[variable] = parseFloat(value);
            }
        }
    },
    mounted() {
        const container = this.$refs.formulaContainer;
        if (container) {
        container.addEventListener('click', (event) => {
            if (event.target.classList.contains('placeholder')) {
                this.handlePlaceholderClick(event);
            }
        });
        }
    }
};
</script>

<style scoped>

#calculating-container {
    width: 83%;
    height: 20%;
    position: absolute;
    top: 2.5rem;
    right: 50%;
    transform: translateX(50%);
    border-radius: 2rem;
    font-size: calc(10px + 2.4vw);
    font-weight: 550;
    font-family: 'OpenSansHebrew';
}

.charStyle {
    position: absolute;
    left: 50%;
    transform: translateX(-50%);
    width: 100vw;
    text-align: center;
    font-size: calc(10px + 4vw);
    color: white;
    font-weight: 600;
}

.light {
    color: #a43b49 !important;
}

.formula-options {
    padding: 0.25rem;
    border-radius: 15px;
    margin-top: 0.15rem;
    z-index: 23;
    color: black;
}

.light-mode .formula-options {
    background-color: rgba(246, 153, 102, 0.358);
    color:  #591b10c7;
}

.dark-mode .formula-options {
    background-color: rgba(123, 114, 114, 0.498);
    color:  #ffffff;
}

.formula-container {
    text-align: center;
    border-radius: 15px;
}

.ground-container {
    position: absolute;
    top: 1.5rem;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-evenly;
    text-align: center;
    border-radius: 15px;
}

.item {
    padding: 0.7rem;
    margin: 0.3rem;
    border-radius: 15px;
    margin-top: 0.25rem;
    z-index: 23;
    color: black;
}

.formula-options,
.item {
    transition: transform 0.3s ease-in, background-color 0.3s ease-in;
}

.formula-options:hover {
    background-color: rgba(255, 228, 192, 0.841);
    transform: scale(1.05); 
}

.light-mode .item:hover{
    background-color: rgba(255, 228, 192, 0.841);
    transform: scale(1.05); 
}

.dark-mode .item:hover {
    background-color: rgba(166, 149, 128, 0.841);
    transform: scale(1.05); 
}
.light-mode .item {
    background-color: rgba(246, 153, 102, 0.358);
    color:  #591b10c7;
}

.dark-mode .item {
    background-color: rgba(123, 114, 114, 0.498);
    color:  #ffffff;
}

.placeholder {
    display: inline-block;
    padding: 0.2rem 0.4rem;
    margin: 0 0.1rem;
    background-color: rgba(255, 255, 0, 0.5);
    border-radius: 4px;
    cursor: pointer;
    text-align: center;
}

.guidance {
    text-align: center;
    margin-top: 2rem;
    font-size: 2rem;
    font-weight: 600;
}

.dark-mode .guidance {
    color: white;
}
.light-mode .guidance {
    color: #406767db;
}

.calc {
    color: rgb(201, 176, 87);
    direction: ltr;
    text-align: left;
    margin-top: 5rem;
}

</style>