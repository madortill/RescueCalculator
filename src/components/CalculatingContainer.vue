<template>
    <div id="calculating-container" >
        <div class="charStyle" :class="darkMode ? 'dark' : 'light'" v-show="!clickedStates.formula && !clickedStates.ground">
            {{ chosenFormula }}
        </div>
        <div class="calc">
            <!-- <input type="text" v-model="inputValue" @mousedown="updateInput"/> -->
        </div>

        <div class="formula-container" v-show="clickedStates.formula" :class="darkMode ? 'dark-mode' : 'light-mode'">
            <div 
                class="formula-options" 
                v-for="(formula, index) in formulasArr" 
                :key="index" 
                @click="chooseFormula(formula.name)">
                {{ formula.name }}
            </div>
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
    </div>
</template>

<script>
import { computed } from 'vue';

export default {
    name: "calculating-container",
    props: ['chosenBtn', 'clickedStates', 'darkMode',], 
    data() {
      return {
        MKnumber: null,
        MTSnumber: null,
        degreeNum: null,
        safetyFactor: 1.25,
        inputValue: '',
        formulasArr: [
            {
                name: 'התנגדות לחילוץ עד 45 מעלות',
                formula: this.safetyFactor * ((this.MKnumber * this.MTSnumber) + (this.MTSnumber * this.degreeNum / 60))
            },
            {
                name: 'התנגדות לחילוץ מעל 45 מעלות',
                formula: this.safetyFactor * ((this.MKnumber * this.MTSnumber) + this.MTSnumber)
            },
            {
                name: 'התנגדות לחילוץ במישור',
                formula: this.safetyFactor * ((this.MKnumber * this.MTSnumber))
            },
            {
                name: 'התנגדות להיפוך - חוק היפוך הרכב',
                formula: (this.MTSnumber * 2 / 3)
            }
        ],
        groundTypesArr: [
            {
                name: 'כביש',
                factor: 0.04
            },
            {
                name: 'אדמה קשה',
                factor: 0.1
            },
            {
                name: 'חצץ',
                factor: 0.2
            },
            {
                name: 'חול',
                factor: 0.25
            },
            {
                name: 'בוץ קל',
                factor: 0.333
            },
            {
                name: 'בוץ כבד',
                factor: 0.5
            },
            {
                name: 'בוץ דביק',
                factor: 0.66
            }
        ],
        degreeFactorsArr: [
            {
                degree: 180,
                factor: 1
            },
            {
                degree: 120,
                factor: 1
            },
            {
                degree: 90,
                factor: 1.4
            },
            {
                degree: 60,
                factor: 1.7
            },
            {
                degree: 30,
                factor: 2
            },
        ],
        chosenFormula: '',
      };
    },
    methods: {
        chooseFormula(formulaName) {
            setTimeout(() => {
                this.chosenFormula = formulaName;
                this.$emit("clickedBtn", "formula");
            },750)
            
        },
        chooseGround(ground) {
            setTimeout(() => {
                this.MKnumber = ground.factor;
                this.$emit("MKinfo", ground);
                // console.log(groundFormula);
                this.$emit("clickedBtn", "ground");
            },750)  
        },
    },
    computed : {
        updateInput() {
            this.inputValue = this.chosenBtn
            return this.inputValue;
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
    margin-top: 0.25rem;
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
/* .formula-options:hover {
    background-color: rgba(255, 228, 192, 0.841);
    scale: 1.05;
} */
.formula-container {
    text-align: center;
    /* background-color: rgba(244, 223, 179, 0.669); */
    border-radius: 15px;
}

.ground-container {
    position: absolute;
    top: 1.5rem;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-evenly;
    text-align: center;
    /* background-color: rgba(244, 223, 179, 0.669); */
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

/* Correct the scale property with transform */
.formula-options:hover {
    background-color: rgba(255, 228, 192, 0.841);
    transform: scale(1.05); /* Corrected scale with transform */
}

.item:hover {
    background-color: rgba(4, 4, 4, 0.841);
    transform: scale(1.15); /* Corrected scale with transform */
}

/* .item:hover {
    background-color: rgba(4, 4, 4, 0.841);
    scale: 1.15;
} */

.light-mode .item {
    background-color: rgba(246, 153, 102, 0.358);
    color:  #591b10c7;
}
.dark-mode .item {
    background-color: rgba(123, 114, 114, 0.498);
    color:  #ffffff;
}
</style>