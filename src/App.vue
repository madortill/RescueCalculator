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
#app {
  direction: rtl;
  width: 100vw;
	height: 100vh;
  overflow: hidden;
}
</style>
