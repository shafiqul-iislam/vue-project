<script setup>
import { RouterLink } from 'vue-router';
import { reactive } from 'vue';
import axios from 'axios';
import router from '@/router';


const form = reactive({
    jobTitle: '',
    company: {
        name: ''
    },
    location: '',
    jobType: '',
    description: '',
    salary: '',
    responsibilities: '',
    requirements: ''
});

const handleSubmit = async () => {

    const newJob = {
        title: form.jobTitle,
        company: {
            name: form.company.name
        },
        location: form.location,
        type: form.jobType,
        description: form.description,
        salary: form.salary,
        responsibilities: form.responsibilities,
        requirements: form.requirements
    }


    console.log(newJob);

    // in this way i can put the data in the database using laravel
    // try {
    //     const response = await axios.post('http://localhost:3001/jobs', newJob);
    //     router.push(`/jobs/${response.data.id}`);
    // } catch (error) {
    //     console.log('Error Fetching in Job', error);
    // }

};
</script>

<template>
    <div class="container p-5">
        <div class="card shadow-lg">
            <div class="card-header bg-success text-white text-center">
                <h4 class="mb-0">Add New Job</h4>
            </div>
            <div class="card-body">

                <form @submit.prevent="handleSubmit">
                    <div class="mb-3">
                        <label for="jobTitle" class="form-label">Job Title</label>
                        <input type="text" v-model="form.jobTitle" class="form-control" id="jobTitle"
                            placeholder="Enter job title">
                    </div>

                    <div class="mb-3">
                        <label for="companyName" class="form-label">Company Name</label>
                        <input type="text" v-model="form.company.name" class="form-control" id="companyName"
                            placeholder="Enter company name">
                    </div>

                    <div class="mb-3">
                        <label for="location" class="form-label">Location</label>
                        <input type="text" v-model="form.location" class="form-control" id="location"
                            placeholder="Enter location">
                    </div>

                    <div class="mb-3">
                        <label for="jobType" class="form-label">Job Type</label>
                        <select class="form-select" v-model="form.jobType" id="jobType">
                            <option value="">Choose job type</option>
                            <option value="full-time">Full-Time</option>
                            <option value="part-time">Part-Time</option>
                            <option value="remote">Remote</option>
                            <option value="contract">Contract</option>
                        </select>
                    </div>

                    <div class="mb-3">
                        <label for="description" class="form-label">Job Description</label>
                        <textarea class="form-control" v-model="form.description" id="description" rows="1"
                            placeholder="Write job description..."></textarea>
                    </div>

                    <div class="mb-3">
                        <label for="salary" class="form-label">Salary</label>
                        <input type="text" v-model="form.salary" class="form-control" id="salary"
                            placeholder="Enter Salary">
                    </div>

                    <div class="mb-3">
                        <label for="responsibilities" class="form-label">Responsibilities</label>
                        <textarea class="form-control" v-model="form.responsibilities" id="responsibilities" rows="1"
                            placeholder="List responsibilities..."></textarea>
                    </div>

                    <div class="mb-3">
                        <label for="requirements" class="form-label">Requirements</label>
                        <textarea class="form-control" v-model="form.requirements" id="requirements" rows="1"
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