<template>
  <div class="card">
    <div :class="`header ${!active || 'border'}`">
      <div class="title">{{ data.title }}</div>
      <div class="count">
        {{ doneCount(data.tasks) }} / {{ data.tasks.length }}
      </div>
    </div>
    <div v-if="active" class="task-list">
      <task-item
        v-for="(task, index) in data.tasks"
        :key="index"
        :done="task.isDone"
        :data="task"
        @click="onTaskClick(index)"
      />
    </div>
  </div>
</template>

<script setup>
import TaskItem from "./TaskItem.vue";

const props = defineProps({
  data: {
    type: Object,
    default: () => {
      return null;
    },
  },
  active: {
    type: Boolean,
    default: () => {
      return false;
    },
  },
});

const doneCount = (tasks) => {
  return tasks.filter((item) => {
    return item.isDone;
  }).length;
};

const emmit = defineEmits(["update:data"]);
const onTaskClick = (index) => {
  let tasks = props.data.tasks.map((item, key) => {
    index !== key || (item.isDone = !item.isDone);
    return item;
  });

  emmit("update:data", tasks);
};
</script>

<style lang="scss">
.card {
  position: absolute;
  box-sizing: border-box;
  width: 100vw;
  height: 100vh;
  background-color: #f7ea96;
  border: black 4px solid;
  border-radius: 30px;
  overflow: hidden;
  padding: 20px;
  transition: all 0.5s;
  z-index: 0;
  .header {
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
    height: 32px;
    &.border {
      border-bottom: 4px black solid;
    }
    font-weight: bold;
  }
  .task-list {
    padding: 22px 0;
    width: 100%;
    display: flex;
    flex-direction: column;
  }
}
</style>
