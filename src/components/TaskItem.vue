<template>
  <div class="task">
    <div :class="`iconfont icon-${done ? 'checked' : 'uncheck'}`"></div>
    <div :class="`content ${done ? 'done' : ''}`">任务描述</div>
  </div>
</template>

<script setup>
defineProps({
  done: {
    type: Boolean,
    default: () => {
      return false;
    },
  },
});
</script>

<style lang="scss">
.task {
  height: 40px;
  display: flex;
  align-items: center;
  font-size: 18px;
  .iconfont {
    font-size: 26px;
    margin-right: 8px;
  }
  .content {
    margin-right: 8px;
    font-size: 1em;
    &.done {
      text-decoration: line-through;
    }
  }
}
</style>
