<template>
    <div id="ending-screen" :class="darkMode ? 'dark-mode' : 'light-mode'">
        <div>
            <div class="title">תוצאת ההתנגדות היא: {{ result }} </div>
            <div class="button " @click="goBack">בחזרה למחשבון</div>
        </div>

    </div>
</template>

<script>
export default {
  name: "ending-screen",
  props: ["darkMode", "result"],
  data() {
    return {
    
    };
  },
  methods: {
    goBack() {
        this.$emit("goBack");
    }
  },
};
</script>

<style scoped>
/* General Styles */
#ending-screen {
    width: 100%;
    height: 100%;
    font-family: "OpenSansHebrew";
    text-align: center;
    overflow: hidden;
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

/* Buttons */
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

.button {
    padding: 0.75rem;
    border-radius: 20px;
    font-size: 1.6rem;
    transition: transform 0.8s, background-color 0.8s;
}

.button:active {
    transform: scale(0.9);
}


.dark-mode .button {
    border: 2px solid  rgb(250, 182, 57);
    color:  rgb(250, 182, 57);;
}

.light-mode .button {
    border: 2px solid rgb(228, 118, 137);
    color: rgb(192, 113, 126);
}


/* Dark and Light Modes */
.dark-mode {
    background: black;
    color: white;
}

.light-mode {
    background: white;
    color: black;
}

.dark-mode .title {
    color: rgb(250, 182, 57);
}

.light-mode .title {
    color: rgb(62, 112, 108);
}



.text {
    /* position: absolute; */
    /* top: 2rem; */
    margin: 2rem;
    padding: 1rem;
    border-radius: 20px;
    font-size: 1.2rem;
}

.light-mode .text {
    background-color: rgba(255, 192, 203, 0.173);
}

</style>
