<script setup>
import { reactive, onMounted } from 'vue';
import { useRoute, RouterLink } from 'vue-router';
import axios from 'axios';

const route = useRoute();
const jobId = route.params.id;

const state = reactive({
    job: {},
});


onMounted(async () => {
    try {
        const response = await axios.get(`http://localhost:3001/jobs/${jobId}`);
        state.job = response.data;
    } catch (error) {
        console.log('Error Fetching in Job', error);
    }
});

</script>

<template>
    <div class="container">
        <div class="card shadow-lg mt-3">
            <div class="card-body">
                <h2 class="card-title text-success mb-3">{{ state.job.title }}</h2>

                <p class="text-muted mb-1"><strong>Company:</strong> Yellow Tech</p>
                <p class="text-muted mb-1"><strong>Location:</strong> Dhaka, Bangladesh</p>
                <p class="text-muted mb-3"><strong>Job Type:</strong> {{ state.job.type }}</p>

                <h5 class="text-dark">Job Description</h5>
                <p>
                    {{ state.job.description }}
                </p>

                <h5 class="text-dark">Responsibilities</h5>
                <p>
                    {{ state.job.responsibilities }}
                </p>

                <h5 class="text-dark">Requirements</h5>
                <p>
                    {{ state.job.requirements }}
                </p>

                <p class="text-muted mb-1"><strong>Salary:</strong> {{ state.job.salary }}</p>

                <div class="mt-4">
                    <RouterLink to="/apply" class="btn btn-success me-2">Apply Now</RouterLink>
                    <RouterLink to="/jobs" class="btn btn-outline-secondary">Back to Jobs</RouterLink>
                </div>
            </div>
        </div>
    </div>
</template>