<template>
    <div id="app">
      <opening-screen 
          v-if="page === 0" 
          @nextScreen="goToNext"
           @toggle-theme="changeMode"
          :darkMode="darkMode">
      </opening-screen>

      <main-screen 
          v-else-if="page === 1"  
          @nextScreen="goToNext"
           @toggle-theme="changeMode"
          :darkMode="darkMode">
      </main-screen>

      <ThemeSwitcher
        @click="changeMode">
    </ThemeSwitcher>
    </div>
</template>

<script>
import MainScreen from './components/MainScreen.vue'
import OpeningScreen from './components/OpeningScreen.vue'
import ThemeSwitcher from './components/ThemeSwitcher.vue'

export default {
  name: "app",
  components: {
  MainScreen,
  OpeningScreen,
  ThemeSwitcher
  },
  data() {
    return {
      page: 0,
      // page: 1,
      darkMode: true,

    }
  },
  methods: {
    goToNext() {
      this.page++;
    },
    changeMode() {
      this.darkMode = !this.darkMode;
    },
  }
}
</script>

<style scoped>
@font-face {
  font-family: 'Heebo';
  src: url(/src/assets/fonts/Heebo/Heebo-Regular.ttf);
}

@font-face {
  font-family: 'OpenSansHebrew';
  src: url(/src/assets/fonts/OpenSansHebrew/OpenSansHebrew-Italic.ttf);
}
html {
  font-size: calc(14px + 0.4vw);
}

#app {
  direction: rtl;
  width: 100vw;
	height: 100vh;
  overflow: hidden;
  font-family: 'Heebo';
}
</style>
