<template>
    <div id="calculating-container">
        <div class="charStyle" v-show="!clickedBtn">
            {{ chosenFormula }}
        </div>
        <!-- Use clickedBtn prop directly for v-show -->
        <div class="formula-container" v-show="clickedBtn">
            <div 
                class="formula-options" 
                v-for="(formula, index) in formulasArr" 
                :key="index" 
                @click="chooseFormula(formula.name)">
                {{ formula.name }}
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "calculating-container",
    props: ['chosenBtn', 'clickedBtn'], // clickedBtn used directly
    data() {
      return {
        MKnumber: null,
        MTSnumber: null,
        degreeNum: null,
        safetyFactor: 1.25,
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
        chosenFormula: '',
      };
    },
    methods: {
        chooseFormula(formulaName) {
            setTimeout(() => {
                this.chosenFormula = formulaName;
            this.$emit("clickedBtn", !this.clickedBtn);
            },500)}
    },

};
</script>

<style scoped>
#calculating-container {
    width: 90%;
    height: 20%;
    position: absolute;
    top: 3rem;
    right: 50%;
    transform: translateX(50%);
    border-radius: 2rem;
    /* border: 0.5px solid  rgb(182, 152, 32); */
}
.charStyle {
    /* color: #004f51; */
    position: absolute;
    left: 50%;
    transform: translateX(-50%);
    width: 100%;
    text-align: center;
    font-size: calc(10px + 3.8vw);
    font-weight: 500;
    z-index: 3;
    }

.formula-options {
    padding: 0.25rem;
    background-color: rgba(244, 223, 179, 0.937);
    border-radius: 15px;
    margin-top: 0.25rem;
    z-index: 23;
    color: black;
}

.formula-options:hover {
    background-color: rgba(255, 228, 192, 0.841);
    scale: 1.05;
}
.formula-container {
    text-align: center;
    /* background-color: rgba(244, 223, 179, 0.669); */
    border-radius: 15px;
}
</style>