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
    <span v-if="note.date">{{ formattedDate(note.date) }}</span>
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
import moment from 'moment'

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
  methods: {
    syncData() {
      this.titleText = this.note.title
      this.contentText = this.note.content
      this.$refs.title.focus()
    },
    formattedDate(rawDate) {
      return moment(rawDate).format('LLLL')
    }
  },
  mounted() {
    this.syncData()
  },
  updated() {
    this.syncData()
  },
}
</script>

<style scoped lang="scss">
.note-editor {
  @extend %theme-yellow;

  align-self: start;
  padding: 20px;

  display: grid;
  grid-template-rows: auto auto 1fr;

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
