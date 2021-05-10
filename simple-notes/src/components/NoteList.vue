<template>
  <div class="note-list">
    <header class="header">
      <h2>Notes List</h2>
      <button 
        @click="$emit('new-note')"
        class="add-button"
      >
        new note
      </button>
    </header>

    <div
      class="note-list-items"
      v-if="notes"
    >
      <NoteListItem 
        v-for="note in notes"
        :key="note.id"
        :note="note" 
        @open-note="$emit('open-note', note.id)"
        @delete-note="$emit('delete-note', note.id)"
      />
    </div>
    
    <div v-else>
      <span>No content.</span>
    </div>
  </div>
</template>

<script>
import NoteListItem from './NoteListItem'

export default {

  name: 'NoteList',
  components: {
    NoteListItem,
  },
  props: {
    notes: Array,
  },
}
</script>

<style scoped lang="scss">
.note-list {

  .header {
    display: flex;
    justify-content: space-between;
    align-items: center;

    .add-button {
      @extend %depth-shadow;
      background: $theme-light-text;
      color: #fff;
      padding: 8px 15px;
      border: none;
      border-radius: $curve-radius;
      cursor: pointer;
      text-decoration: none;
      font-size: 15px;
      font-family: inherit;
      &:focus {
        outline: none;
      }
      &:active {
        transform: scale(0.98);
      }
    }
  }

  .note-list-items {
    display: flex;
    flex-direction: column;
    gap: 10px
  }
}
</style>
