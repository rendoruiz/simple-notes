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
  @extend %theme-yellow;
  
  padding: 15px;
  max-height: 200px;
  overflow: hidden;

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