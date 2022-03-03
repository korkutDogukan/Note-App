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
    <NoteCount @filterCardList="filterCardList" :colorCount="colorCount"></NoteCount>
    <NoteList
      @deleteCard="deleteCard"
      :noteList="filteredList.length > 0 ? filteredList : noteList"
    ></NoteList>
  </div>
</template>
<script setup>
import NoteList from "../NoteList/NoteList.vue";
import { ref } from "vue";
import NoteCount from "../NoteCount/NoteCount.vue";

const selectedColor = ref(null);
const noteTitle = ref(null);
const noteDescription = ref(null);
const noteList = ref([]);
const filteredList = ref([]);
const colorCount = ref({
  redCount: 0,
  blueCount: 0,
  yellowCount: 0,
  greyCount: 0
})

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
  filteredList.value = filteredList.value.filter(c => c != card);
  if (card.color == 'red') {
    colorCount.value.redCount--;
  } else if (card.color == 'blue') {
    colorCount.value.blueCount--;
  } else if (card.color == 'yellow') {
    colorCount.value.yellowCount--;
  } else {
    colorCount.value.greyCount--;
  }
}

const filterCardList = (color) => {
  filteredList.value = noteList.value.filter(c => c.color == color);
  console.log("selam", color);
}

const addNote = () => {
  if (noteTitle.value != null && noteDescription.value != null && selectedColor.value != null) {
    if (selectedColor.value == 'red') {
      colorCount.value.redCount++;
    } else if (selectedColor.value == 'blue') {
      colorCount.value.blueCount++;
    } else if (selectedColor.value == 'yellow') {
      colorCount.value.yellowCount++;
    } else {
      colorCount.value.greyCount++;
    }
    let dateObj = new Date();
    let month = dateObj.getUTCMonth() + 1;
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