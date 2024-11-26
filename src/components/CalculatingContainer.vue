<template>
    <div id="calculating-container">
        <div class="charStyle">
            {{ chosenBtn }}
        </div>
    </div>
</template>

<script>
export default {
    name: "calculating-container",
    props: ['chosenBtn'],
    data() {
      return {
      }
    },
    methods: {
    }
  }
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
    color: rgb(182, 152, 32);
    position: absolute;
    left: 3rem;
    top: 5rem;
    font-size: calc(14px + 6vw)
    }
</style>