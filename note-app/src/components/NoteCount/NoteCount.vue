<template>
  <div class="note-count">
    <button
      @click="emit('filterCardList', null)"
      class="note-count-button"
    >All {{ totalColorCount }}</button>
    <button
      @click="emit('filterCardList', 'red')"
      class="note-count-button red"
    >{{ props.colorCount.redCount }}</button>
    <button
      @click="emit('filterCardList', 'blue')"
      class="note-count-button blue"
    >{{ props.colorCount.blueCount }}</button>
    <button
      @click="emit('filterCardList', 'yellow')"
      class="note-count-button yellow"
    >{{ props.colorCount.yellowCount }}</button>
    <button
      @click="emit('filterCardList', 'grey')"
      class="note-count-button grey"
    >{{ props.colorCount.greyCount }}</button>
  </div>
</template>
<script setup>
import { defineProps, computed, defineEmits } from 'vue';

const props = defineProps(['colorCount']);
const emit = defineEmits(['filterCardList']);

const totalColorCount = computed(() => {
  let totalCount = props.colorCount.redCount + props.colorCount.blueCount + props.colorCount.yellowCount + props.colorCount.greyCount;
  return totalCount;
})
</script>
<style src="./NoteCount.scss" lang="scss">
</style>