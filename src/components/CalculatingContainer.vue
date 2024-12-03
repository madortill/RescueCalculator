<template>
    <div id="calculating-container" >
        <div :class="darkMode ? 'dark-mode' : 'light-mode'">
            <div v-if="!MKnumber && !clickedStates.ground && !afterDelete" class='guidance'>בחרו סוג קרקע</div>
            <div v-else-if="showGuidance && !chosenFormula && !clickedStates.formula && !clickedStates.ground && !afterDelete" class='guidance'>בחרו נוסחא</div>
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
        <div class="calc" ref="formulaContainer" v-show="!clickedStates.formula && !clickedStates.ground" @click="handlePlaceholderClick">
            <div v-show="!errorMessage" v-html="renderFormula()"></div>
            <div v-show="errorMessage" class="error-message">{{ errorMessage }}</div>
        </div>
    </div>
</template>

<script>

export default {
    name: "calculating-container",
    props: ['chosenValueString', 'clickedStates', 'darkMode', 'stringBtn'], 
    data() {
      return {
        showGuidance: false,
        MKnumber: null,
        MTSnumber: null,
        degreeNum: null,
        afterDelete: false,
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
                formula: 'safetyFactor x ((MKnumber x MTSnumber) + (MTSnumber x degreeNum / 60))'
            },
            {
                name: 'התנגדות לחילוץ מעל 45 מעלות',
                formula: 'safetyFactor x ((MKnumber x MTSnumber) + MTSnumber)'
            },
            {
                name: 'התנגדות לחילוץ במישור',
                formula: 'safetyFactor x (MKnumber x MTSnumber)'
            },
            {
                name: 'התנגדות להיפוך - חוק היפוך הרכב',
                formula: '(MTSnumber x 2 / 3)'
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
        chosenCalc: null,
        localChosenBtn: this.chosenValueString,
        newInput: false,
        insertedValues: {}, // Store the inserted values for each variable
        placeholders: {} ,// Store the placeholders so we can update them simultaneously
        errorMessage: '',
      };
    },
    watch: {
        chosenValueString(newVal) {
            // Extract the most left digit
            this.localChosenBtn = newVal.charAt(0);
            this.alertUpdate();
        }
    },
    computed: {
        updatedChosenBtn() {
            return this.localChosenBtn;
        },
        updateStringBtn() {
            return this.stringBtn;
        }
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
                return ' '; // Return blank if no formula is chosen
            }

            // Handle delete button: Reset inputs but keep safetyFactor
            if (this.updateStringBtn === 'מחק') {
                this.resetFormulaInputs(); // Reset inputs
                return this.renderPlaceholderFormula(); // Re-render formula with placeholders
            }

            // Replace placeholders with current variable values or leave placeholders if null
            let formula = this.chosenFormula.formula;
            const variableLabels = {
                MKnumber: 'מקדם קרקע',
                MTSnumber: 'משקל ציוד',
                degreeNum: 'זוית השיפוע',
                safetyFactor: '1.25' // Default value for safetyFactor
            };

            const variables = {
                MKnumber: this.MKnumber,
                MTSnumber: this.MTSnumber,
                degreeNum: this.degreeNum,
                safetyFactor: this.safetyFactor
            };

            const modeClass = this.darkMode ? 'dark-mode' : 'light-mode';

            Object.keys(variables).forEach((key) => {
                let value;
                if (key === 'safetyFactor') {
                    value = variableLabels[key]; // Always use default value for safetyFactor
                } else {
                    value =
                        variables[key] !== null
                            ? variables[key]
                            : `<span class="placeholder ${modeClass}" data-var="${key}">${variableLabels[key]}</span>`;
                }
                formula = formula.split(key).join(value);
            });

            return formula;
        },
        renderPlaceholderFormula() {
            let formula = this.chosenFormula.formula;
            const variableLabels = {
                MKnumber: `${this.MKnumber}`,
                MTSnumber: 'משקל ציוד',
                degreeNum: 'זוית השיפוע',
                safetyFactor: '1.25' // Default value for safetyFactor
            };
            const modeClass = this.darkMode ? 'dark-mode' : 'light-mode';

            Object.keys(variableLabels).forEach((key) => {
                if (key === 'safetyFactor' || key === 'MKnumber') {
                    formula = formula.split(key).join(variableLabels[key]); // Use default value for safetyFactor
                } else {
                    const placeholder = `<span class="placeholder ${modeClass}" data-var="${key}">${variableLabels[key]}</span>`;
                    formula = formula.split(key).join(placeholder);
                }
            });

            return formula;
        },
        resetFormulaInputs() {
            // Reset only the input variables to null, leave safetyFactor unchanged
            this.MTSnumber = null;
            this.degreeNum = null;
            this.localChosenBtn = ''; 
            this.afterDelete = true;
        },
        alertUpdate() {
            this.newInput = true;
        },
        validateDegreeNum(value) {
        if (value > 45) {
            this.degreeNum = null; // Clear the input
            this.errorMessage = 'שימו לב, הזוית צריכה להיות קטנה יותר מ-45 מעלות, אנא הכניסו ערך תקין';
            setTimeout(() => {
            this.errorMessage = ''; // Clear the error message after a short delay
            }, 4500);
        } else {
            this.degreeNum = value;
        }
        },
        handlePlaceholderClick(event) {
        if (event.target.classList.contains("placeholder")) {
            const variable = event.target.getAttribute('data-var');
            if (!variable || variable === 'safetyFactor') return; // Do not allow editing safetyFactor

            if (this.selectedPlaceholder && this.selectedPlaceholder !== event.target) {
            clearInterval(this.intervalId); // Stop the interval
            if (this.currentInput) {
                if (variable === 'degreeNum') {
                this.validateDegreeNum(parseFloat(this.currentInput)); // Validate degreeNum
                } else {
                this[variable] = parseFloat(this.currentInput); // Save the previous value
                }
            }
            }
            this.selectedPlaceholder = event.target;
            this.currentInput = ''; // Reset input for the new placeholder

            if (this.intervalId) {
            clearInterval(this.intervalId);
            }

            this.intervalId = setInterval(() => {
            if (this.updatedChosenBtn !== null && this.newInput) {
                // Add the button value and reset flag
                this.currentInput += this.updatedChosenBtn;
                this.newInput = false;
            }
            this.selectedPlaceholder.textContent = this.currentInput;

            if (this.currentInput.length === 7) {
                clearInterval(this.intervalId);
                if (variable === 'degreeNum') {
                this.validateDegreeNum(parseFloat(this.currentInput)); // Validate degreeNum
                } else {
                this[variable] = parseFloat(this.currentInput); // Save the final value
                }
            }
            }, 250); // Adjust speed if needed
        } else {
            // User clicked outside a placeholder
            if (this.selectedPlaceholder) {
            const variable = this.selectedPlaceholder.getAttribute('data-var');
            clearInterval(this.intervalId); // Stop the interval
            if (this.currentInput) {
                if (variable === 'degreeNum') {
                this.validateDegreeNum(parseFloat(this.currentInput)); // Validate degreeNum
                } else {
                this[variable] = parseFloat(this.currentInput); // Save the value
                }
            }
            this.selectedPlaceholder = null; // Reset the placeholder
            }
        }
    },
    mounted() {
        const calcContainer = this.$refs.formulaContainer;
        
        calcContainer.addEventListener('touchstart', this.handlePlaceholderClick, false);
        calcContainer.addEventListener('touchend', this.handlePlaceholderClick, false);
    },
    beforeDestroy() {
        const calcContainer = this.$refs.formulaContainer;
        calcContainer.removeEventListener('touchstart', this.handlePlaceholderClick, false);
        calcContainer.removeEventListener('touchend', this.handlePlaceholderClick, false);

        if (this.intervalId) {
        clearInterval(this.intervalId);
        }
    }
}
};
</script>

<style scoped>
@font-face {
  font-family: 'Heebo';
  src: url(/src/assets/fonts/Heebo/Heebo-Regular.ttf);
} 

#calculating-container {
    width: 92%;
    height: 23%;
    position: absolute;
    top: 1.75rem;
    right: 50%;
    transform: translateX(50%);
    border-radius: 2rem;
    font-size: 1.1rem;
    font-weight: 550;
    font-family: 'OpenSansHebrew';
}

.charStyle {
    position: absolute;
    left: 50%;
    transform: translateX(-50%);
    width: 100vw;
    text-align: center;
    font-size: 1.65rem;
    color: white;
    font-weight: 600;
}

.light {
    color: #a43b49 !important;
}

.formula-container {
    position: absolute;
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    justify-content: center;
    text-align: center;
    border-radius: 15px;
    width: 100%;
    height: 100%;

}

.formula-options {
    padding: 0.25rem;
    width: 75%;
    border-radius: 15px;
    margin: 0.1rem;
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



.ground-container {
    position: absolute;
    top: 1.5rem;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-evenly;
    text-align: center;
    border-radius: 15px;
    width: 100%;
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
    font-family: 'Heebo';
}

.error-message {
  color: rgb(222, 67, 53);
  margin-top: 0.2rem;
  text-align: center;
}

</style>

<style>
.placeholder {
    display: inline-block;
    background-color: transparent; /* No background color to blend with the input area */
    color: #666; /* Default text color */
    padding: 0.4rem;
    border-bottom: 2px solid #aaa; /* Underline for better emphasis */
    font-style: italic; /* To indicate it's a placeholder */
    text-align: center;
    cursor: pointer; /* Indicate that it is clickable */
    transition: all 0.3s ease-in-out;
}

/* Dark mode styling */
.dark-mode .placeholder {
    color: #ddd; /* Light text color for dark mode */
    border-bottom: 2px solid #bbb; /* Lighter border for contrast */
}

/* Light mode styling */
.light-mode .placeholder {
    color: #333; /* Darker text color for light mode */
    border-bottom: 2px solid #888; /* Darker border for better contrast */
}

.placeholder:hover {
    color: #0056b3; /* Change color on hover */
    border-bottom-color: #0056b3; /* Highlight the underline on hover */
}

@keyframes clickme {
    0% {
        transform: scale(1);
    }
    50% {
        transform: scale(1.05);
    }
    100% {
        transform: scale(1);
    }
}
</style>