<template>
  <div class="task">
    <div class="checkbox"></div>
    <div :class="`content ${doneClass}`">任务描述</div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const props = defineProps({
  done: {
    type: Boolean,
    default: () => {
      return false;
    },
  },
});

const doneClass = ref(props.done ? "done" : "");
</script>

<style lang="scss" scoped>
.task {
  height: 40px;
  display: flex;
  align-items: center;
  font-size: 18px;
  .checkbox {
    width: 15px;
    height: 15px;
    border: solid black 1px;
    border-radius: 3px;
    margin-right: 8px;
  }
  .content {
    margin-right: 8px;
    &.done {
      text-decoration: line-through;
    }
  }
}
</style>
