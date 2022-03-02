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
          <label class="note-card-content-footer-colors-label red">
            <input type="radio" class="note-card-content-footer-colors-label-input" />
          </label>
          <label class="note-card-content-footer-colors-label blue">
            <input type="radio" class="note-card-content-footer-colors-label-input" />
          </label>
          <label class="note-card-content-footer-colors-label yellow">
            <input type="radio" class="note-card-content-footer-colors-label-input" />
          </label>
          <label class="note-card-content-footer-colors-label black">
            <input type="radio" class="note-card-content-footer-colors-label-input" />
          </label>
        </div>
        <button type="button" class="note-card-content-footer-button">Add Note</button>
      </div>
    </div>
  </div>
</template>
<script setup>
</script>
<style src="./NoteCard.scss" lang="scss">
</style>