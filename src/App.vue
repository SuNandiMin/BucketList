<template>
 <div class="">
  <h1 class="text-white bg-primary text-center p-2 fw-bolder">{{ title }}</h1>
  <div class="container-lg">
        <div class="input-group justify-content-center m-3">
            <input class="" type="text" v-model="newTask" v-on:keyup.enter="addTask()">
            <button class="input-group-text btn btn-secondary" @click="addTask()" type="submit">Add</button>
        </div>
        <div class="row">
            <div class="col-5 offset-2 fs-4 mb-2 fw-bold">TASKS</div>
            <div class="col-2 fs-4 mb-2 fw-bold">Done</div>
        </div>
        <div class="row" v-for="(task,index) in filterTasks" :key="index">
            <div class="col-5 offset-2" :class="task.done ? 'delete-text' : ''">{{ task.action }}</div>
            <div class="col-2 ">
                <input type="checkbox" v-model="task.done">
            </div>
        </div>
        <hr>
        <div class="row">
            <div class="col-3 offset-3 fw-bold fs-5" >Hide Completed Tasks</div>
            <div class="col-2 ">
                <input type="checkbox" v-model="hideCompleted">
            </div>
        </div>
  </div>
 </div>
</template>

<script>
export default {
    name: "App",
    data: () => ({
        title: "Bucket List",
        hideCompleted: false,
        newTask:'',
        tasks: [
            { action : "Trip to Amsterdam", done: false },
            { action : "Learning Vue", done: false },
            { action : "See Taehyung", done: false },
            { action :"Work as a developer" , done:true}
        ]
    }),
    computed: {
        filterTasks() {
            return this.hideCompleted ? this.tasks.filter((v) => !v.done) : this.tasks ;
        }
    },
    methods: {
        addTask() {
            if (this.newTask === '' ) {
               return alert("new task field is required")
            }
            this.tasks.push({
                action: this.newTask,
                done: false,
                time: 'During next year',
            });
            this.newTask = '';
        }
    }
    }
</script>

<style>
.delete-text{
    text-decoration: line-through;
}
</style>

