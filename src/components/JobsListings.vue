<script setup>
import JobData from '@/jobs2.json';
import JobsListing from './JobsListing.vue';
import { ref, reactive, defineProps, onMounted } from 'vue';
import { RouterLink } from 'vue-router';
import axios from 'axios';

defineProps({
    limit: Number,
    showButton: {
        type: Boolean,
        default: false
    }
});

// const jobs = ref([]);

const jobs = ref(JobData);

// const state = reactive({
//     jobs: [],
//     isLoading: true
// });

onMounted(async () => {

    try {
        const response = await axios.get('http://localhost:3001/jobs');
        jobs.value = response.data;

        // state.jobs = response.data;
    } catch (error) {
        console.log('Error Fetching in Jobs', error);
    }
    // finally {
    //     state.isLoading = false;
    // }

});
</script>

<template>
    <div class="container mt-5 mb-5">
        <h2 class="mb-4 text-center text-success fw-bold">Browse Jobs</h2>

        <div class="row g-4 mb-3">
            <div class="col-lg-6" v-for="job in jobs.slice(0, limit || jobs.length)" :key="job.id">
                <div class="card shadow-sm h-100">
                    <div class="card-body">
                        <h5 class="card-title">{{ job.title }}</h5>
                        <h6 class="card-subtitle mb-2 text-muted">{{ job.type }}</h6>
                        <!-- <p class="card-text">{{ job.description }}</p> -->

                        <p>
                            <JobsListing :jobs="job" />
                        </p>

                        <p class="mb-1"><strong>Salary:</strong> {{ job.salary }}</p>
                        <hr>
                        <h6 class="mb-1">Company: {{ job.company.name }}</h6>
                        <p class="text-muted">{{ job.company.description }}.</p>
                        <RouterLink :to="'/job-details/' + job.id" class="btn btn-sm btn-success">Read More</RouterLink>
                    </div>
                </div>
            </div>
        </div>

        <div v-if="showButton" class="py-3 d-flex justify-content-center">
            <RouterLink to="/jobs" class="btn btn-dark">View All Jobs</RouterLink>
        </div>
    </div>
</template>