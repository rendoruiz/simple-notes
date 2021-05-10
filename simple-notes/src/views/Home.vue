<template>
  <div class="home">
    <NoteList 
      :notes="notes" 
      @open-note="openNote"
    />
    <NoteEditor 
      v-if="selectedNote"
      :note="selectedNote"
    />
  </div>
</template>

<script>
import NoteList from '@/components/NoteList.vue'
import NoteEditor from '@/components/NoteEditor.vue'

export default {
  name: 'Home',
  components: {
    NoteList,
    NoteEditor,
  },
  data() {
    return {
      selectedNote: null,
      notes: []
    }
  },
  methods: {
    openNote(noteId) {
      this.selectedNote = this.notes.find(note => note.id === noteId)
    }
  },
  created() {
    this.notes = [
      {
        id: 1,
        title: '1st Title',
        content: '1st Content',
      },
      {
        id: 2,
        title: '2nd Title',
        content: '2nd Content',
      },
      {
        id: 3,
        title: '3rd Title',
        content: '3rd Content',
      },
    ]
  }
}
</script>

<style scoped>
.home {
  display: grid;
  grid-template-columns: minmax(50px, 300px) minmax(300px, 600px);
  gap: 10px;
  justify-content: center;
  padding: 10px;
}
</style>
