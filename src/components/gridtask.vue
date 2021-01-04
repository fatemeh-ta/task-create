<template>
  <div class="font">
    <app-task v-for="(item,key) in tasks" :key="item.id">
      <button  @click="checkcomplete(key)">
        <span v-if ="item.id=='complete'" style="backgroundColor:lightgreen; textDecoration : line-through">
          {{item.subject}} | {{item.id}}
        </span>
        <span v-else>
          {{item.subject}} | {{item.id}}
        </span>
      </button>
      <button @click="deletetask(key)">
        <i class="fa fa-trash" aria-hidden="true"></i>
      </button>
    </app-task>
  </div>
</template>

<script>
import task from './task.vue'
export default {
  data() {
    return {
    }
  },
  components : {
    appTask : task
  },
  props : {
    tasks : {
      type : Array
    },
  },
  methods : {
    deletetask(key) {
      this.$emit('deleted' , key )
    },
    checkcomplete(key) {
      this.$emit ('completed' , key)
    },
  },
}
</script>

<style scoped>
  i {
    font-family: 'FontAwesome';
  }

  .style {
    background-color: green;
  }
  .font {
    font-family: "vazir";
  }

</style>
