<template>
    <div id="opening-screen" :class="darkMode ? 'dark-mode' : 'light-mode'">
        <img class= "madortill" src="/src/assets/media/madortill.png" alt="icon"/>

        <div  v-if="page===0" class="open-page" :class="darkMode ? 'dark-mode' : 'light-mode'">
            <div class="title">ברוכים הבאים למחשבון חישוב התנגדות לחילוץ!</div>
            <div class="button upper" @click="goNext">יאללה נתחיל!</div>  
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
                 לאחר שבדקתם את כל אלו, תוכלו להשתמש במחשבון! <br><br>
                 עליכם להשתמש בכפתורים שנמצאים במחשבון על מנת להכניס את הערכים הרצויים לנוסחא שבחרתם. <br><br>
                 לאחר מכן תוכלו לחשב את תוצאת ההתנגדות שיש להפעיל, בהתאם לנוסחאות החילוץ. 
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
    position: absolute;
    top: 9rem;
    font-size: 2.2rem;
    font-weight: bold;
    text-align: center;
    margin: 0.85rem;
    padding-top: 2.5rem;
    padding-bottom: 2.5rem;
    padding-right: 0.5rem;
    padding-left: 0.5rem;
    border-radius: 1rem;
    animation: float 3s ease-in-out infinite;
}


/* Keyframes for the floating effect */
@keyframes float {
    0% {
        transform: translateY(0);
    }
    50% {
        transform: translateY(-15px);
    }
    100% {
        transform: translateY(0);
    }
}

.button-container {
    position: absolute;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    top: 17rem;
    width: 87%;
    height: 50%;
    margin: 0.85rem;
    border-radius: 1rem;
    border: 2px solid rgb(255, 255, 255);
}


.dark-mode .title  {
    color:rgb(250, 182, 57);
    /* background-color: orange; */
    /* border: 2px solid rgb(250, 154, 71); */
}
.light-mode .title  {
    color:rgb(62, 112, 108);
    /* background-color: pink; */
    /* border: 2px solid rgb(157, 195, 189); */
}

.button {
    position: absolute;
    bottom: 5rem;
    margin-top: 5rem;
    padding: 0.75rem;
    border-radius: 20px; 
    font-size: 1.6rem;
}

.upper {
    bottom: 10rem;
}


 .dark-mode {
    background-color: black;
    color: rgb(255, 255, 255);
}

.dark-mode .button {
    border: 2px solid  rgb(250, 182, 57);
    color:  rgb(250, 182, 57);;
}

.light-mode .button {
    border: 2px solid rgb(228, 118, 137);
    color: rgb(192, 113, 126);
}

.light-mode {
    background-color: white;
    color: black;
}

.text {
    position: absolute;
    top: 2rem;
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
    margin: 0.4rem;
    padding: 0.7rem;
    border-radius: 1rem;
    font-size: 1.23rem;
    color: white;
}

.dark-mode .item {
    color: rgb(245, 154, 63);
    border: 2px solid 
}

.light-mode .item {
    background-color: #6f9a9ac2;
}

.container-checklist {
   margin-top: 1rem;
}

.madortill, .mifkada {
    width: 4rem;
    position: absolute;
    bottom: 1.25rem;
    right: 1.25rem;
}


.dark-mode .madortill {
    filter: invert(1) brightness(2);
}

</style>