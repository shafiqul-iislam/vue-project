<script setup>

import { ref, onMounted } from 'vue';

const message = ref('Hello World');
const status = ref('active');
const tasks = ref(['Task One', 'Task Two', 'Task Three']);
const link = ref('https://www.google.com');
const newTask = ref('');

const toggleStatus = () => {
    // status.value = status.value == 'active' ? 'deactive' : 'active';

    if (status.value == 'active') {
        status.value = 'pending';
    } else if (status.value == 'pending') {
        status.value = 'deactive';
    } else {
        status.value = 'active';
    }
};


const addTask = () => {
    if (newTask.value.trim() != '') {
        tasks.value.push(newTask.value);
        newTask.value = '';
    }
};

const deleteTask = (index) => {
    tasks.value.splice(index, 1);
};

onMounted(async () => {
    try {

        const response = await fetch('https://jsonplaceholder.typicode.com/todos');

        const data = await response.json();

        tasks.value = data.map((todo) => todo.title);

    } catch (error) {
        console.log(error);
    }
});

</script>

<template>
    <h1>{{ message }}</h1>

    <br>
    <p v-if="status == 'active'">Jobs Is Active</p>
    <p v-else-if="status == 'pending'">Jobs Is Pending</p>
    <p v-else>Jobs Is Not Active</p>

    <br>
    <h3>Tasks:</h3>
    <ul>
        <li v-for="(task, index) in tasks">
            <span>{{ task }}</span>
            <button @click="deleteTask(index)">Delete</button>
        </li>
    </ul>
    <br>
    <form @submit.prevent="addTask">
        <label for="newTask">Add Task</label>
        <input type="text" name="new_task" v-model="newTask">
        <button type="submit">Submit</button>
    </form>
    <br>

    <!-- <a v-bind:href="link">Click Here</a> -->
    <!-- link is veriable -->
    <a :href="link">Click Here</a>

    <br>

    <!-- <button v-on:click="toggleStatus">Change Status</button> -->
    <button @click="toggleStatus">Change Status</button>
</template>
