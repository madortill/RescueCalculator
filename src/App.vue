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
      darkMode: false,

    }
  },
  methods: {
    goToNext() {
      this.page++;
    },
    changeMode() {
      this.darkMode = !this.darkMode;
    },
    updateMetaTags() {
      // Update theme color for Android browsers
      const themeMetaTag = document.querySelector('meta[name="theme-color"]');
      if (themeMetaTag) {
        themeMetaTag.setAttribute("content", this.darkMode ? "#000000" : "#ffffff");
      } else {
        const newThemeMetaTag = document.createElement("meta");
        newThemeMetaTag.name = "theme-color";
        newThemeMetaTag.content = this.darkMode ? "#000000" : "#ffffff";
        document.head.appendChild(newThemeMetaTag);
      }

      // Update status bar style for iOS Safari
      const statusBarMetaTag = document.querySelector('meta[name="apple-mobile-web-app-status-bar-style"]');
      if (statusBarMetaTag) {
        statusBarMetaTag.setAttribute("content", this.darkMode ? "black-translucent" : "default");
      } else {
        const newStatusBarMetaTag = document.createElement("meta");
        newStatusBarMetaTag.name = "apple-mobile-web-app-status-bar-style";
        newStatusBarMetaTag.content = this.darkMode ? "black-translucent" : "default";
        document.head.appendChild(newStatusBarMetaTag);
      }
    }
  },
  watch: {
    darkMode: {
      handler: "updateMetaTags",
    },
  },
  mounted() {
    // Ensure the initial theme color is set when the app is loaded
    this.updateMetaTags();
  },
};
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
