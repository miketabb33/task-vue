<template>
  <div>
    <h2 class="taskColumn__header">{{ header }}</h2>
    <div class="taskColumn__container">
      <div v-for="item in items" :key="item.id">
        <TaskCard :hideLeft="hideLeft" :hideRight="hideRight" v-bind="item" @card-move-action="cardMoveAction"/>
      </div>
    </div>
  </div>
</template>

<script>
import TaskCard from './TaskCard.vue';

export default {
  name: 'TaskColumn',
  props: {
    header: String,
    items: Array,
    hideLeft: Boolean,
    hideRight: Boolean
  },
  components: {
    TaskCard
  },
  setup(props, context) {
    const cardMoveAction = (payload) => {
      context.emit('card-move-action', payload)
    }
    return {
      cardMoveAction
    };
  },
}
</script>

<style scoped>
  .taskColumn__container {
    background-color: #ECECEC;
    border: #d4d4d4 solid 1px;
    border-radius: 4px;
    width: 20rem;
    padding: 0.5rem;
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
  }

  .taskColumn__header {
    text-align: center;
    font-family: sans-serif;
  }

</style>