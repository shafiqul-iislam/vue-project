<script>
export default {
    data() {
        return {
            message: 'Hello In Jobs World',
            status: 'active',
            tasks: ['Task One', 'Task Two', 'Task Three'],
            link: 'https://www.google.com',
        }
    },

    methods: {
        toggleStatus() {
            // this.status = this.status == 'active' ? 'deactive' : 'active';

            if (this.status == 'active') {
                this.status = 'pending';
            } else if (this.status == 'pending') {
                this.status = 'deactive';
            } else {
                this.status = 'active';
            }
        }
    }
};

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
        <li v-for="task in tasks">{{ task }}</li>
    </ul>
    <br>

    <a v-bind:href="link">Click Here</a>

    <!-- link is veriable -->
    <a :href="link">Click Here</a>

    <br>

    <!-- <button v-on:click="toggleStatus">Change Status</button> -->
    <button @click="toggleStatus">Change Status</button>
</template>
