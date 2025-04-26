<script setup>
import axios from 'axios';
import { ref, reactive, onMounted, computed } from 'vue';
import { useRoute, RouterLink } from 'vue-router';
import JobData from '@/jobs2.json';
import { useToast } from 'vue-toastification';

const route = useRoute();

const toast = useToast();

const deleteJob = async (id) => {

    console.log(id);

    toast.success('Job deleted successfully');


    // try {
    //     const response = await axios.delete(`http://localhost:3001/jobs/${id}`);
    //     if (response.status == 200) {

    //         toast.success('Job deleted successfully');

    //         // alert('Job deleted successfully');
    //         // window.location.href = '/jobs';
    //     }
    // } catch (error) {
    //     console.log('Error deleting job', error);
    // }
};

const job = computed(() => {
    const id = Number(route.params.id);
    return JobData.find(job => job.id == id);
});

</script>

<template>
    <div class="container">
        <div class="card shadow-lg mt-3" v-if="job">
            <div class="card-body">
                <h2 class="card-title text-success mb-3">{{ job.title }}</h2>

                <p class="text-muted mb-1"><strong>Company:</strong> {{ job.company.name }}</p>
                <p class="text-muted mb-1"><strong>Location:</strong> Dhaka, Bangladesh</p>
                <p class="text-muted mb-3"><strong>Job Type:</strong> {{ job.type }}</p>

                <h5 class="text-dark">Job Description</h5>
                <p>{{ job.description }}</p>

                <h5 class="text-dark">Responsibilities</h5>
                <p>{{ job.responsibilities }}</p>

                <h5 class="text-dark">Requirements</h5>
                <p>{{ job.requirements }}</p>

                <p class="text-muted mb-1"><strong>Salary:</strong> {{ job.salary }}</p>

                <div class="mt-4 d-flex justify-content-between">
                    <div class="">
                        <RouterLink to="/apply" class="btn btn-success me-2">Apply Now</RouterLink>
                        <RouterLink to="/jobs" class="btn btn-outline-secondary">Back to Jobs</RouterLink>
                    </div>
                    <div class="">
                        <RouterLink :to="'/job/edit/' + job.id" class="btn btn-success me-2">Edit</RouterLink>
                        <button @click="deleteJob(job.id)" class="btn btn-danger">Delete</button>
                    </div>
                </div>
            </div>
        </div>
        <div v-else class="alert alert-warning mt-3">Job not found.</div>
    </div>
</template>
