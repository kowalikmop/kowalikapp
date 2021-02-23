<template>
  <div class="home">
  <input v-model="appTitle" />
  <h1>Liczba pomnożona przez 2 to:</h1>
   <transition name="fade">
  <span v-if="appTitle > 0">{{ appTitle * 2}}</span>
  </transition>
  <button @click="appTitle += 1"> + </button>
  <button @click="appTitle -= 1"> - </button>
  </div>
</template>
<script>
export default {
  data() {
    return {
      appTitle: null,
    };
  },
};
</script>
<style scoped>
.fade-enter-active, .fade-leave-active {
  transition: all .3s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
font-size: 40px;
}
</style>
