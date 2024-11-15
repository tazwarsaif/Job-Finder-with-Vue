
<script setup>
import { ref,onMounted } from 'vue';

    const name = ref('Tazwar Saif')
    const status = ref('active')
    const tasks = ref(["Task1", "Task2" , "Task3"]);
    const toggleStatus = () =>  {
        if(status.value === 'active'){
            status.value = 'pending'
        }else if(status.value=== 'pending'){
            status.value = 'inactive'
        }else{
            status.value = "active"
        }
    }
    const newTask = ref('');
    const addTask = () => {
        if(newTask.value.trim !== ''){
            tasks.value.push(newTask.value)
            newTask.value = ''
        }
    }
    const deleteTask = (index) =>{
        tasks.value.splice(index,1);
    }
    onMounted(async () =>{
        try{
            const response =  await fetch('https://jsonplaceholder.typicode.com/todos');
            const data = await response.json();
            data.forEach(element => {
                tasks.value.push(element.title)
            });
        }catch(error){
                console.log(error)
            }
    })

</script>

<template>
  <h1>{{ name }}</h1>
  <p v-if="status==='active'">User is active</p>
  <p v-else-if="status==='pending'">Pending</p>
  <p v-else>Inactive</p>

  <form action="" @submit.prevent="addTask">
    <label for="newTask">Add Task</label>
    <input type="text" id="newTask" name="newTask" v-model="newTask">
    <button type="submit">Submit</button>
  </form>
  <h3>Tasks:</h3>
  <ul>
    <li v-for="(task,index) in tasks" :key="task">
        <span>
            {{ task }}
        </span>
        <button @click="deleteTask(index)">Delete Task</button>
    </li>
  </ul>
  <button @click="toggleStatus">Change Status</button>
</template>


