<template>
    <div id="opening-screen">
        <div  v-if="page===0" class="open-page" :class="darkMode ? 'dark-mode' : 'light-mode'">
            <div class="title">ברוכים הבאים למחשבון חישוב התנגדות לחילוץ!</div>
            <div class="button" @click="goNext">המשך</div>
        </div>
        <div  v-else-if="page===1" class="continue-page" :class="darkMode ? 'dark-mode' : 'light-mode'">
            <div class="text">
                נהג חילוץ יקר, בעת הגעה לאירוע חילוץ מסוג משיכה יש לזכור כי ישנם כמה פרמטרים חשובים אותם יש לבדוק טרם החילוץ:
            </div>
            <div class="container-checklist">
                <div class="item" v-for="item in checklist" :key="item">{{ item }}</div>
            </div>
            <div class="button" @click="goNext">המשך</div>
        </div>
        <div v-else class="continue-page" :class="darkMode ? 'dark-mode' : 'light-mode'">
            <div class="text">    
                לאחר שבדקת את כל אלו, תוכל להתשמש במחשבון אשר יחשב עבורך את ההתנגדות אותה תצטרך להפעיל בהתאם לנוסחאות חילוץ.
            </div>
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
        page: 0,
        checklist: [
                'משקל הרכב אותו נדרש לחלץ',
                'סוג הקרקע',
                'זווית המשיכה (שיפוע הקרקע)',
                'האם נדרש שינוי זווית',
            ]
    }
  },
  methods: {
    goNext() {
        this.page++;
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
    font-family: 'OpenSansHebrew';
    text-align: center;
}

.open-page,
.continue-page {
    width: 100%;
    height: 100%;
    display: flex;
    /* margin-top: 3rem; */
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
    margin: 0.85rem;
    padding-top: 1rem;
    padding-bottom: 1rem;
    padding-right: 0.5rem;
    padding-left: 0.5rem;
    border-radius: 1rem;
}
.dark-mode .title  {
    background-color: orange;
}
.light-mode .title  {
    background-color: pink;
}
.button {
    margin-top: 5rem;
    padding: 0.75rem;
    border-radius: 20px; 
    font-size: 1rem;
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

.text {
    margin: 2rem;
    padding: 1rem;
    border-radius: 20px;
    font-size: 1.2rem;
}


.dark-mode .text {
    /* background-color: orange; */
}

.light-mode .text {
    /* background-color: pink; */
}

.item {
    margin: 0.1rem;
    padding: 0.7rem;
    border-radius: 1rem;
    font-size: 1.23rem;
    color: white;
}

.dark-mode .item {
    background-color: gray;
}

.light-mode .item {
    background-color: #6f9a9ac2;
}

</style>