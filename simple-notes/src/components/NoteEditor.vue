<template>
  <div class="note-editor">
    <div 
      ref="title"
      class="title" 
      contenteditable="true"
      @input="note.title = $event.target.innerText"
    >
      {{ titleText }}
    </div>
    <div 
      class="content" 
      contenteditable="true"
      @input="note.content = $event.target.innerText"
    >
      {{ contentText }}
    </div>
  </div>
</template>

<script>
export default {
  name: 'NoteEditor',
  props: {
    note: Object,
  },
  data() {
    return {
      titleText: null,
      contentText: null,
    }
  },
  mounted() {
    this.titleText = this.note.title
    this.contentText = this.note.content
    this.$refs.title.focus()
  },
  updated() {
    this.titleText = this.note.title
    this.contentText = this.note.content
    this.$refs.title.focus()
  },
}
</script>

<style scoped lang="scss">
.note-editor {
  @extend %theme-yellow;

  align-self: start;
  padding: 20px;

  display: grid;
  grid-template-rows: auto 1fr;

  .title,
  .content {
    white-space: pre-wrap;
  }

  .title {
    font-size: 2rem;
  }

  .content {
    margin-top: 10px;
    font-size: 1.2rem;
  }

  .placeholder {
    font-style: italic;
  }
}
</style>
