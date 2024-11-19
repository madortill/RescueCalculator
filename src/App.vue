<template>
    <div id="app">
      <main-screen></main-screen>
    </div>

</template>

<script>
import MainScreen from './components/MainScreen.vue'
export default {
  name: "app",
  components: {
  MainScreen
  },
  data() {
    return {
    }
  },
  methods: {
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

#app {
  direction: rtl;
  width: 100vw;
	height: 100vh;
  overflow: hidden;
  font-family: 'Heebo';
}
</style>
