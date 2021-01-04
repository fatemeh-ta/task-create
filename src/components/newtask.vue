<template>
  <div>
    <form class="create-task">
      <input type="text" v-model="description" placeholder="لطفا عنوان تسک را وارد نمایید"  >
      <button @click.prevent="addtask">ثبت درخواست</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      description : '',
      status : 'incomplete'
    }
  },
  methods : {
    addtask() {
      this.$emit('creatTask' , this.description , this.status)
      this.description = ''
    }
  }
}
</script>

<style lang="scss" scoped>
  .create-task {
    margin: 16px auto;
    text-align: center;
  }
  input {
    border: 1px solid rgb(151, 16, 16);
    padding: 8px;
    margin-bottom: 8px;
    font-family: "vazir";
  }
  button {
    padding: 8px;
    border: 1px solid rgb(151, 16, 16);
    cursor: pointer;
    font-family: "vazir";
    &:hover {
      background-color: rgb(151, 16, 16);
      color: #fff;
    }
  }

</style>
