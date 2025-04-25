<script setup>
import { useRoute } from 'vue-router';
import { reactive } from 'vue';
import axios from 'axios';
import JobData from '@/jobs2.json';

const route = useRoute();
const jobId = route.params.id;
const job = JobData.find(job => job.id == jobId);

const updateForm = reactive({
    jobTitle: job.title,
    company: {
        name: job.company.name,
        description: job.company.description,
        location: job.company.location
    },
    jobType: job.type,
    description: job.description,
    salary: job.salary,
    responsibilities: job.responsibilities,
    requirements: job.requirements
});


const handleUpdateSubmit = () => {

    console.log(form);

    // // in this way i can put the data in the database using laravel
    // try {
    //     const response = axios.put('http://localhost:3001/jobs/' + jobId, updateForm);
    //     console.log(response);
    // } catch (error) {
    //     console.log('Error Fetching in Job', error);
    // }
}

</script>

<template>
    <div class="container p-5">
        <div class="card shadow-lg">
            <div class="card-header bg-success text-white text-center">
                <h4 class="mb-0">Update Job</h4>
            </div>
            <div class="card-body">

                <form @submit.prevent="handleUpdateSubmit">
                    <div class="mb-3">
                        <label for="jobTitle" class="form-label">Job Title</label>
                        <input type="text" v-model="updateForm.jobTitle" class="form-control" id="jobTitle"
                            placeholder="Enter job title">
                    </div>

                    <div class="mb-3">
                        <label for="companyName" class="form-label">Company Name</label>
                        <input type="text" v-model="updateForm.company.name" class="form-control" id="companyName"
                            placeholder="Enter company name">
                    </div>

                    <div class="mb-3">
                        <label for="location" class="form-label">Location</label>
                        <input type="text" v-model="updateForm.company.location" class="form-control" id="location"
                            placeholder="Enter location">
                    </div>

                    <div class="mb-3">
                        <label for="jobType" class="form-label">Job Type</label>
                        <select class="form-select" v-model="updateForm.jobType" id="jobType">
                            <option value="">Choose job type</option>
                            <option value="Full-Time">Full-Time</option>
                            <option value="Part-Time">Part-Time</option>
                            <option value="Remote">Remote</option>
                            <option value="Contract">Contract</option>
                        </select>
                    </div>

                    <div class="mb-3">
                        <label for="description" class="form-label">Job Description</label>
                        <textarea class="form-control" v-model="updateForm.description" id="description" rows="2"
                            placeholder="Write job description..."></textarea>
                    </div>

                    <div class="mb-3">
                        <label for="salary" class="form-label">Salary</label>
                        <input type="text" v-model="updateForm.salary" class="form-control" id="salary"
                            placeholder="Enter Salary">
                    </div>

                    <div class="mb-3">
                        <label for="responsibilities" class="form-label">Responsibilities</label>
                        <textarea class="form-control" v-model="updateForm.responsibilities" id="responsibilities"
                            rows="2" placeholder="List responsibilities..."></textarea>
                    </div>

                    <div class="mb-3">
                        <label for="requirements" class="form-label">Requirements</label>
                        <textarea class="form-control" v-model="updateForm.requirements" id="requirements" rows="2"
                            placeholder="List requirements..."></textarea>
                    </div>

                    <div class="d-flex justify-content-between">
                        <button type="submit" class="btn btn-success">Submit Job</button>
                        <RouterLink to="/" class="btn btn-outline-secondary">Cancel</RouterLink>
                    </div>
                </form>
            </div>
        </div>
    </div>
</template>