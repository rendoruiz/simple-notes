<template>
  <div class="home">
    <NoteList :notes="notes" />
    <NoteEditor />
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
      notes: [
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
          id: 1,
          title: '3rd Title',
          content: '3rd Content',
        },
      ]
    }
  }
}
</script>

<style scoped>
.home {
  display: grid;
  grid-template-columns: minmax(auto, 300px) minmax(70%, max-content);
  gap: 10px;
  padding: 10px;
  height: 100vh;
}
</style>
