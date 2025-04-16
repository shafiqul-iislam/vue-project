<script setup>
import { RouterLink } from 'vue-router';
</script>

<template>
    <div class="container">
        <div class="card shadow-lg mt-3">
            <div class="card-body">
                <h2 class="card-title text-success mb-3">Senior Laravel Developer</h2>

                <p class="text-muted mb-1"><strong>Company:</strong> CodeWorks Ltd.</p>
                <p class="text-muted mb-1"><strong>Location:</strong> Dhaka, Bangladesh</p>
                <p class="text-muted mb-3"><strong>Job Type:</strong> Full-Time</p>

                <h5 class="text-dark">Job Description</h5>
                <p>
                    We are looking for an experienced Laravel developer to join our growing team. The ideal candidate
                    should have a strong understanding of backend development, RESTful APIs, and MySQL.
                </p>

                <h5 class="text-dark">Responsibilities</h5>
                <ul>
                    <li>Develop and maintain web applications using Laravel</li>
                    <li>Collaborate with front-end developers and designers</li>
                    <li>Write clean, reusable, and efficient code</li>
                    <li>Participate in code reviews</li>
                </ul>

                <h5 class="text-dark">Requirements</h5>
                <ul>
                    <li>3+ years of experience with Laravel</li>
                    <li>Strong knowledge of PHP, MySQL, and Git</li>
                    <li>Familiar with RESTful APIs and modern design patterns</li>
                    <li>Good communication and teamwork skills</li>
                </ul>

                <div class="mt-4">
                    <RouterLink to="/apply" class="btn btn-success me-2">Apply Now</RouterLink>
                    <RouterLink to="/jobs" class="btn btn-outline-secondary">Back to Jobs</RouterLink>
                </div>
            </div>
        </div>
    </div>
</template>