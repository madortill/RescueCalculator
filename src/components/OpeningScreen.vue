<template>
    <div id="opening-screen">
        <div  v-if="!clickedStart" class="open-page" :class="darkMode ? 'dark-mode' : 'light-mode'">
            <div class="title">ברוכים הבאים למחשבון חישוב התנגדות לחילוץ!</div>
            <div class="button" @click="goNext">המשך</div>
        </div>
        <div  v-else class="continue-page" :class="darkMode ? 'dark-mode' : 'light-mode'">
            <div>טקסט</div>
            <div  class="button" @click="startCalc">המשך</div>
        </div>
    </div>
</template>

<script>
export default {
  name: "opening-screen",
  props: ['darkMode'], 
  data() {
    return {
        clickedStart: false,
    }
  },
  methods: {
    goNext() {
        this.clickedStart = true;
        console.log(this.darkMode);
    },
    startCalc() {
        this.$emit('nextScreen');
    }
  }
}
</script>


<style scoped>
#opening-screen {
    width: 100%;
    height: 100%;  
    font-family: 'OpenSansHebrew' 
}

.open-page,
.continue-page {
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
}

.title {
    position: relative;
    bottom: 3rem;
    font-size: 2.2rem;
    font-weight: bold;
    text-align: center;
    margin: 1.5rem;
}

.button {
    margin-top: 2rem;
    padding: 0.75rem;
    border-radius: 20px; 
    font-size: 1.4rem;
}

 .dark-mode {
    background-color: black;
    color: white;
}

.dark-mode .button {
    background-color: orange;
}

.light-mode .button {
    background-color: pink;
}

.light-mode {
    background-color: white;
    color: black;
}

</style>