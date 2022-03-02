<template>
  <div class="note-card">
    <h1 class="note-card-title">Note App</h1>
    <div class="note-card-content">
      <form class="note-card-content-form">
        <input
          placeholder="Title"
          type="text"
          class="note-card-content-form-input"
          v-model="noteTitle"
        />
        <textarea
          placeholder="Description"
          class="note-card-content-form-textarea"
          v-model="noteDescription"
        ></textarea>
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
        <button @click="addNote" type="button" class="note-card-content-footer-button">Add Note</button>
      </div>
    </div>
    <NoteList @deleteCard="deleteCard" :noteList="noteList"></NoteList>
  </div>
</template>
<script setup>
import NoteList from "../NoteList/NoteList.vue";
import { ref } from "vue";

const selectedColor = ref(null);
const noteTitle = ref(null);
const noteDescription = ref(null);
const noteList = ref([]);

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

const deleteCard = (card) => {
  noteList.value = noteList.value.filter(c => c != card);
}

const addNote = () => {
  if (noteTitle.value != null && noteDescription.value != null && selectedColor.value != null) {
    let dateObj = new Date();
    let month = dateObj.getUTCMonth() + 1; //months from 1-12
    let day = dateObj.getUTCDate();
    let year = dateObj.getUTCFullYear();
    const noteContent = ref({
      title: noteTitle.value,
      desc: noteDescription.value,
      color: selectedColor.value,
      time: year + "/" + month + "/" + day
    });
    noteList.value.push(noteContent.value);
    noteTitle.value = null;
    noteDescription.value = null;
    selectedColor.value = null;
    return;
  }
  alert("Bütün verileri giriniz!");
}

</script>
<style src="./NoteCard.scss" lang="scss">
</style>