<template>
  <div class="container">
    <h2>Notes List</h2>
    <div 
      class="note-list"
      v-if="notes"
    >
      <div 
        class="note-list-item"
        v-for="note in notes"
        :key="note.id"
      >
        <span>{{ note.id }}</span>
        <h3>{{ note.title }}</h3>
        <p>{{ note.content }}</p>
      </div>
    </div>
    
    <div v-else>
      no content
    </div>
  </div>
</template>

<script>
export default {
  name: 'NoteList',
  props: {
    notes: Array
  }
}
</script>

<style scoped lang="scss">
.note-list {
  display: flex;
  flex-direction: column;
  gap: 10px
}
.note-list-item {
  background: rgb(255, 247, 209);
  border-radius: 6px;
  padding: 20px;
}
</style>
