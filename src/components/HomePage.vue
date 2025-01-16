<template>
  <div class="board">
    <TaskColumn header="To Do" :hideLeft=true :items="toDoItems" @card-move-action="cardMoveAction"/>
    <TaskColumn header="Doing" :items="doingItems" @card-move-action="cardMoveAction"/>
    <TaskColumn header="Done" :hideRight=true :items="doneItems" @card-move-action="cardMoveAction"/>
  </div>
</template>

<script>
import { doingItems, doneItems, toDoItems } from '@/Items';
import TaskColumn from './TaskColumn.vue';
import { uuid } from '@/uuid';

const cardMoveAction = () => {
  doingItems.push({id: uuid(), title: "nice"})
}

export default {
  name: 'HomePage',
  components: {
    TaskColumn
  },
  data() {
    return {
      toDoItems,
      doingItems,
      doneItems
    }
  },
  setup() {
    return {
      cardMoveAction
    };
  }
}
</script>

<style scoped>
  .board {
    display: flex;
    gap: 1rem;
  }
</style>