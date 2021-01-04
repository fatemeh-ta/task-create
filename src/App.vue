<template>
  <div class="body wrapper container">
    <app-header></app-header>
    <app-new-task @creatTask="creatTask"></app-new-task>
    <p class="message">{{message}}</p>
    <app-grid-task :tasks="tasks" @deleted="deletedTask" @completed="completetask"></app-grid-task>
    <button @click="deleatComplete" class="delete"> مشاهده لیست های تکمیل نشده </button>
  </div>
</template>

<script>
import gridtask from './components/gridtask.vue'
import newtask from './components/newtask.vue'
import header from './components/header.vue'
export default {
  data () {
    return {
      tasks :[{
        subject : 'salam' , id : 'incomplete'
      }],
      message : '',

    }
  },
  methods : {
    creatTask (title , status) {
      if (title == '') {
        this.message = 'لطفا عنوان تسک را وارد نمایید'
      } else {
        //this.tasks.push(title)
          this.tasks.push ({
          subject : title,
          id :  status
        });
        this.message = ''
      }
    },
    deletedTask(key) {
      this.tasks.splice(key, 1)
    },
    completetask(key) {
      this.$set( this.tasks, key, {id: 'complete'})
    },
    deleatComplete() {
      //alert('ddddd')
      this.tasks = this.tasks.filter((arry) => arry.id === 'incomplete')
    }
  },
  components : {
    appGridTask : gridtask,
    appNewTask : newtask,
    appHeader : header
  }
}
</script>

<style lang="scss">
  .wrapper {
    max-width: 1200px;
    margin: 0 auto;
  }
  .body {
    border: 1px solid #000;
    padding: 8px;
    direction: rtl;
    font-family: "vazir";
  }
  .container {
    max-width: 1200px;
    margin-left: auto;
    margin-right: auto;
    &::after {
      clear: both;
      content: '';
      display: table;
    }
  }
  .message {
    color : rgb(151, 16, 16);
    text-align: center;
  }
  .delete {
    padding: 8px;
    border: 1px solid rgb(151, 16, 16);
    margin: 0 auto;
    display: block;
    cursor: pointer;
    font-family: "vazir";
    &:hover {
      background-color: rgb(151, 16, 16);
      color: #fff;
    }
  }
</style>
