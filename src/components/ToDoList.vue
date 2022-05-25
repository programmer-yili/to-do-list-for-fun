<template>
  <div class="main">
    <task-list-card
      v-for="(taskList, index) in taskLists"
      :key="index"
      :active="index === activeTaskListIndex"
      :data="taskList"
      :style="cardStyle(index, index === activeTaskListIndex)"
      @click="onCardClick(index)"
    />
  </div>
</template>

<script setup>
import TaskListCard from "./TaskListCard.vue";
import { reactive, ref } from "vue";

const taskLists = reactive([
  {
    id: 1,
    title: "工作",
    tasks: [
      { id: 11, content: "任务描述1", isDone: false },
      { id: 12, content: "任务描述2", isDone: true },
      { id: 13, content: "任务描述3", isDone: false },
    ],
  },
  {
    id: 2,
    title: "学习",
    tasks: [{ id: 21, content: "任务描述1", isDone: true }],
  },
  {
    id: 3,
    title: "收集箱",
    tasks: [
      { id: 22, content: "任务描述2", isDone: false },
      { id: 23, content: "任务描述3", isDone: false },
    ],
  },
  {
    id: 4,
    title: "随便",
    tasks: [
      { id: 42, content: "任务描述2" },
      { id: 43, content: "任务描述3" },
    ],
  },
]);

const activeTaskListIndex = ref(0);
const cardColors = ["#f7ea96", "#a0cafd", "#9fffab"];
const cardStyle = (index, active) => {
  const colorCount = cardColors.length;
  let style = `background-color: ${
    cardColors[(index + colorCount) % colorCount]
  };`;
  style += active
    ? "top: 0;z-index: 0;"
    : `top: calc(80% + ${index * 50}px);z-index: ${index + 1};`;
  return style;
};

const onCardClick = (index) => {
  activeTaskListIndex.value = index;
};
</script>

<style lang="scss">
.main {
  position: relative;
  width: 100vw;
  height: 100vh;
  overflow: hidden;
}
</style>
