<template>
  <div 
    class="note-list-item"
    @click="$emit('open-note', note.id)"
  >
    <span class="date">{{ shortDateFormat(note.id) }}</span>
    <h3 class="title">{{ note.title }}</h3>
    <p class="content">{{ note.content }}</p>
    <span 
      class="delete-button"
      @click="$emit('delete-note', note.id)"
    >
      ❌
    </span>
  </div>
</template>

<script>
import moment from 'moment'

export default {
  name: 'NoteListItem',
  props: {
    note: Object
  },
  methods: {
    shortDateFormat(unixTime) {
      return moment(unixTime).fromNow()
    }
  }
}
</script>

<style scoped lang="scss">
.note-list-item {
  @extend %theme-yellow;
  @extend %depth-shadow;

  display: flex;
  flex-direction: column;
  padding: $card-item-padding;
  max-height: 200px;
  overflow: hidden;
  position: relative;

  &:hover {
    .delete-button {
      display: inline-block;
    }
    .date {
      visibility: hidden;
    }
  }

  .delete-button {
    display: none;
    position: absolute;
    top: $card-item-padding;
    right: $card-item-padding;
    cursor: pointer;
    &:active {
      transform: scale(0.90);
    }
  }

  * {
    margin: 0;
    padding: 0;
    line-height: 1;
  }

  .date {
    text-align: right;
    font-size: 0.7rem;
  }

  .title {
    font-size: 1.2rem;
  }

  .content {
    margin-top: 5px;
    font-size: 1rem;
  }

  -webkit-user-select: none;  
  -moz-user-select: none;    
  -ms-user-select: none;      
  user-select: none;
}
</style>