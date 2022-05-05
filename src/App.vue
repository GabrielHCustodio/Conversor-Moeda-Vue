<template>
  <div id="center">
    <HeaderConversor />
    <BodyConversor />
  </div>
</template>

<script>
import HeaderConversor from "./components/Header.vue"
import BodyConversor from "./components/Body.vue"

export default {
  components: {
    HeaderConversor,
    BodyConversor
  }
}
</script>

<style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: Helvetica;
  }

  #center {
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    margin: 30px 0;
  }

</style>
