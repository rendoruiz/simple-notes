<template>
  <div class="note-list">
    <h2>Notes List</h2>
    <div 
      class="note-list-items"
      v-if="notes"
    >
      <NoteListItem 
        v-for="note in notes"
        :key="note.id"
        :note="note" 
        @open-note="$emit('open-note', note.id)"
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

  .note-list-items {
    display: flex;
    flex-direction: column;
    gap: 10px
  }
}
</style>
