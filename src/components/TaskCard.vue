<template>
  <div class="taskCard__container">
    <button 
      class="taskCard__arrow taskCard__arrow--left" 
      @click="clickLeft"
      v-if="!hideLeft">
      &larr;
    </button>
    {{ title }}
    <button 
      class="taskCard__arrow taskCard__arrow--right"
      @click="clickRight"
      v-if="!hideRight">
      &rarr;
    </button>
  </div>
</template>

<script>



export default {
  name: 'TaskCard',
  props: {
    id: String,
    title: String,
    hideLeft: Boolean,
    hideRight: Boolean
  }, 
  setup(props, context) {
    const clickLeft = () => {
      context.emit('card-move-action', 'test');
    }

    const clickRight = () => {
      context.emit('card-move-action', 'test');
    }
    return {
      clickLeft,
      clickRight,
    };
  },
}
</script>

<style scoped>
  .taskCard__container {
    background-color: white;
    padding: 1.5rem;
    border-radius: 4px;
    box-shadow: 1px 1px 8px lightgray;
    position: relative;
  }

  .taskCard__arrow {
    background-color: transparent;
    border: none;
    cursor: pointer;
    transition: all 0.2s;
    position: absolute;

    &:hover {
      background-color: #d4d4d4;
      border-radius: 2px;
    }
  }

  .taskCard__arrow--left {
    left: 0px;
  }

  .taskCard__arrow--right {
    right: 0px;
  }

</style>