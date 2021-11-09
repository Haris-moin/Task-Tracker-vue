<template>
 <div  class="container">
   <Header title="Task Tracker"/>
   <AddTask @add-task="addTask"/>
   <Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks" />
 </div>
</template>

<script>

import Header from './components/Header.vue'
import Tasks from './components/tasks.vue'
import AddTask from './components/AddTask.vue'
export default {
  name: 'App',
  components: {
    Header,
    Tasks,
    AddTask,
  },
  methods:{
    addTask(task){
      this.tasks= [...this.tasks,task]
    },
    deleteTask(id){
     this.tasks = this.tasks.filter(task=>task.id!=id);
    },
    toggleReminder(id){
      this.tasks =this.tasks.map((task)=>
      task.id===id ? {...task,reminder:!task.reminder}: task)
    }
  },
  data(){
    return {
      tasks : []
    }
  },
  created() {
    this.tasks = [
      {
        id:1,
        text:'Doctore Appoinment',
        day:'March 1',
        reminder:true,
      },
       {
        id:2,
        text:'Go to mall',
        day:'March 2',
        reminder:true,
      },
       {
        id:3,
        text:'School Appoinment',
        day:'March 4',
        reminder:false,
      },
    ]
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');
*{
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  }
  body{
    font-family: 'Poppins', sans-serif;
  }
  .container{
    max-width: 500px;
    margin: 30px auto;
    overflow: auto;
    min-height: 300px;
    border: 1px solid steelblue;
    padding: 30px;
    border-radius: 5px;
  }
  .btn{
    display: inline-block;
    background: #000;
    color: #fff;
    border: none;
    padding: 10px 20px;
    margin: 5px;
    border-radius: 5px;
    cursor: pointer;
    text-decoration: none;
    font-size: 15px;
    font-family: inherit;
  }
  btn:focus{
    outline: none;
  }
  .btn:active{
    transform: scale(0.98);
  }
  .btn-block{
    display: block;
    width: 100%;
  }
   .Heading{
        display: flex;
        justify-content: center;
        align-items: center;
        margin-bottom: 20px;
    }
</style>
