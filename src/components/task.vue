<template>
  <div class="task">
    <slot></slot>
  </div>
</template>

<script>
export default {

}
</script>

<style scoped>
.task {
    background-color: #ccc;
    color: rgb(151, 16, 16);
    padding: 16px 24px;
    box-shadow: 0 0 3px rgb(32,16,16);
    box-sizing: border-box;
    float: right;
    width: 100%;
    margin-bottom: 16px;
  }
</style>
