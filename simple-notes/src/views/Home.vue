<template>
  <div class="home">
    <NoteList 
      :notes="notes" 
      @open-note="openNote"
      @new-note="newNote"
      @delete-note="deleteNote"
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
  watch: {
    notes: {
      deep: true,
      handler(updatedNotes) {
        localStorage.notes = JSON.stringify(updatedNotes)
      }
    }
  },
  methods: {
    openNote(noteId) {
      this.selectedNote = this.notes.find(note => note.id === noteId)
    },
    newNote() {
      const newNote = {
        id: Date.now(),
      }
      this.notes.push(newNote)
      this.openNote(newNote.id)
    },
    deleteNote(noteId) {
      console.log(noteId)
      if (confirm('confirm deletion')) {
        this.notes = this.notes.filter(note => note.id !== noteId)
      }
    }
  },
  created() {
    if (!localStorage.notes) {
      this.notes = [
        {
          id: 1620571057387,
          title: '1st Title',
          content: '1st Content',
        },
        {
          id: 1620572057387,
          title: '2nd Title',
          content: '2nd Content',
        },
        {
          id: 1620573057387,
          title: '3rd Title',
          content: '3rd Content',
        },
      ]
    }
  },
  mounted() {
    if (localStorage.notes) {
      this.notes = JSON.parse(localStorage.notes)
      const latestNote = this.notes.slice(0, 1).shift()
      this.openNote(latestNote.id)
    }
  },
}
</script>

<style scoped>
.home {
  display: grid;
  grid-template-columns: minmax(50px, 300px) minmax(300px, 600px);
  gap: 20px;
  justify-content: center;
  padding: 10px;
}
</style>
