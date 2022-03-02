<template>
  <transition name="card-list-transition">
    <div v-show="props.noteList.length > 0" class="card-list">
      <div
        v-for="(card, index) in props.noteList"
        :key="index"
        :style="cardBackgroundColor(card.color)"
        class="card-list-item"
      >
        <h3 class="card-list-item-title">{{ card.title }}</h3>
        <p class="card-list-item-desc">{{ card.desc }}</p>
        <span class="card-list-item-time">{{ card.time }}</span>
        <span @click="$emit('deleteCard', card)" class="card-list-item-close-icon">
          <i class="fa-solid fa-xmark"></i>
        </span>
      </div>
    </div>
  </transition>
  <div v-show="!(props.noteList.length > 0)" class="none-card-list">
    <p class="none-card-list-message">No notes yet</p>
  </div>
</template>
<script setup>
import { defineProps } from 'vue';

const props = defineProps(['noteList']);

const cardBackgroundColor = (color) => {
  return `background-color: ${color};`
}

</script>
<style src="./NoteList.scss" lang="scss">
</style>