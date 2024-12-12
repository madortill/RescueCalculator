<template>
    <div id="app">
      <opening-screen 
          v-show="page === 0" 
          @nextScreen="goToNext"
           @toggle-theme="changeMode"
          :darkMode="darkMode">
      </opening-screen>

      <main-screen 
           v-show="page === 1"  
          @nextScreen="goToNext"
          @calculatedResult="saveResult"
          @toggle-theme="changeMode"
          :darkMode="darkMode">
      </main-screen>

      <ending-screen
         v-show="page === 2" 
         @goBack="goBack" 
         :darkMode="darkMode"
         :result="result">
      </ending-screen>

      <ThemeSwitcher
        @click="changeMode">
    </ThemeSwitcher>
    </div>
</template>

<script>
import MainScreen from './components/MainScreen.vue'
import OpeningScreen from './components/OpeningScreen.vue'
import EndingScreen from './components/EndScreen.vue'
import ThemeSwitcher from './components/ThemeSwitcher.vue'

export default {
  name: "app",
  components: {
  MainScreen,
  OpeningScreen,
  ThemeSwitcher,
  EndingScreen
  },
  data() {
    return {
      page: 0,
      // page: 2,
      darkMode: false,
      result: null,

    }
  },
  methods: {
    goToNext(pageSent) {
      if (pageSent === null || pageSent === undefined) {
        this.page++;
      } else {
        this.page = pageSent;
      }
      console.log(this.page);
    },
    goBack() {
      this.page--;
    },
    saveResult(unsavedResult) {
      this.result = unsavedResult;
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
/* html {
  font-size: calc(14px + 0.4vw);
}

#app {
  direction: rtl;
  width: 100vw;
	height: 100vh;
  overflow: hidden;
  font-family: 'Heebo';
} */

html, body {
  margin: 0;
  padding: 0;
  width: 100%;
  height: 100%;
  background-color: black; /* Matches dark mode */
  color: white; /* Adjust text color for dark mode */
}

#app {
  direction: rtl;
  width: 100vw;
  height: 100vh;
  overflow: hidden;
  font-family: 'Heebo';
  padding-top: env(safe-area-inset-top); /* Ensures the app accounts for the notch */
  background-color: var(--app-bg-color); /* Dynamic background */
}

/* Add a dynamic background color for light/dark mode */
:root {
  --app-bg-color: white;
}
.dark-mode {
  --app-bg-color: black;
}

</style>
