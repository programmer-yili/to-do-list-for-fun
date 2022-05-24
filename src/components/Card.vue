<template>
  <div class="card">
    <div class="header">
      <div class="title">工作</div>
      <div class="count">30</div>
    </div>
    <div class="task-list">
      <task :done="true" />
      <task />
      <task />
    </div>
  </div>
</template>

<script setup>
import Task from "./Task.vue";
</script>

<style lang="scss" scoped>
.card {
  box-sizing: border-box;
  width: 100vw;
  height: 100vh;
  background-color: #f7ea96;
  border: black 4px solid;
  border-radius: 30px;
  overflow: hidden;
  padding: 20px;
  .header {
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
    height: 32px;
    border-bottom: 4px black solid;
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
