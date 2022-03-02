<template>
  <div class="app">
    <NoteCard></NoteCard>
  </div>
</template>
<script setup>
import NoteCard from './components/NoteCard/NoteCard.vue';
</script>
<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Nunito+Sans:wght@300;400;700;900&display=swap");
.app {
  width: 100%;
  height: 100vh;
  background-color: darkcyan;
  font-family: "Nunito Sans", sans-serif;
}
</style>
