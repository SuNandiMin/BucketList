<template>
 <div class="">
  <h1 class="text-white bg-primary text-center p-2 fw-bolder">{{ title }}</h1>
  <div class="container-lg">
    <div class="row">
        <div class="col-5 offset-2 fs-4 mb-2 fw-bold">TASKS</div>
        <div class="col-2 fs-4 mb-2 fw-bold">Done</div>
    </div>
        <div class="row" v-for="(task,index) in tasks" :key="index">
        <div class="col-5 offset-2 ">{{ task.action }}</div>
        <div class="col-2 ">{{ task.done }}</div>
    </div>
  </div>
 </div>
</template>

<script>
export default {
    name: "App",
    data: () => ({
        title: "Bucket List",
        tasks: [
            { action : "Trip to Amsterdam", done: false },
            { action : "Learning Vue", done: false },
            { action : "See Taehyung", done: false },
            { action :"Work as a developer" , done:true}
        ]
    }),
    }
</script>

