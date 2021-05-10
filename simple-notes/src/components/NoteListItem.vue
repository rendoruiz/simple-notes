<template>
  <div 
    class="note-list-item"
    @click="$emit('open-note', note.id)"
  >
    <h3 class="title">#{{ note.id }}: {{ note.title }}</h3>
    <p class="content">{{ note.content }}</p>
  </div>
</template>

<script>
export default {
  name: 'NoteListItem',
  props: {
    note: Object
  }
}
</script>

<style scoped lang="scss">
.note-list-item {
  background: $theme-yellow-bg;
  border-top: 8px solid $theme-yellow-strip;
  color: $theme-yellow-text;
  border-radius: $note-curvature;
  padding: 15px;

  * {
    margin: 0;
    padding: 0;
    line-height: 1;
    white-space: pre-wrap;
  }

  .title {
    font-size: 1.2rem;
  }

  .content {
    margin-top: 5px;
    font-size: 1rem;
  }
}
</style>