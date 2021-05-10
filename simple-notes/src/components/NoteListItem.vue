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

  box-shadow: 0 1px 2px rgba(0,0,0,0.08), 0 3px 8px rgba(0,0,0,0.1);
  transition-property: box-shadow;
  transition-duration: 0.3s, 0.3s;
  transition-timing-function: ease, ease;
  transition-delay: 0s, 0s;

  &:hover {
    box-shadow: 0 6.4px 14.4px rgba(0,0,0,0.13),0 1.2px 3.6px rgba(0,0,0,0.1);
  }

  * {
    margin: 0;
    padding: 0;
    line-height: 1;
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