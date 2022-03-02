<template>
  <div class="note-card">
    <div class="note-card-title">Note App</div>
    <div class="note-card-content">
      <form class="note-card-content-form">
        <input placeholder="Title" type="text" class="note-card-content-form-input" />
        <textarea placeholder="Description" class="note-card-content-form-textarea"></textarea>
      </form>
      <div class="note-card-content-footer">
        <div class="note-card-content-footer-colors">
          <label
            @click="selectRed"
            :class="selectedColor == 'red' ? 'selected-color' : null"
            class="note-card-content-footer-colors-label red"
          >
            <input type="radio" class="note-card-content-footer-colors-label-input" />
          </label>
          <label
            :class="selectedColor == 'blue' ? 'selected-color' : null"
            @click="selectBlue"
            class="note-card-content-footer-colors-label blue"
          >
            <input type="radio" class="note-card-content-footer-colors-label-input" />
          </label>
          <label
            :class="selectedColor == 'yellow' ? 'selected-color' : null"
            @click="selectYellow"
            class="note-card-content-footer-colors-label yellow"
          >
            <input type="radio" class="note-card-content-footer-colors-label-input" />
          </label>
          <label
            :class="selectedColor == 'grey' ? 'selected-color' : null"
            @click="selectGrey"
            class="note-card-content-footer-colors-label grey"
          >
            <input type="radio" class="note-card-content-footer-colors-label-input" />
          </label>
        </div>
        <button type="button" class="note-card-content-footer-button">Add Note</button>
      </div>
    </div>
  </div>
</template>
<script setup>
import { ref } from "vue";

const selectedColor = ref(null);

const selectRed = () => {
  selectedColor.value = "red";
}
const selectBlue = () => {
  selectedColor.value = "blue";
}
const selectYellow = () => {
  selectedColor.value = "yellow";
}
const selectGrey = () => {
  selectedColor.value = "grey";
}
</script>
<style src="./NoteCard.scss" lang="scss">
</style>