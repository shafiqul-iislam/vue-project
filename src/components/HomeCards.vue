<script setup>
import Card from '@/components/Card.vue';
import { RouterLink } from 'vue-router';

</script>

<template>
    <!-- Job Cards -->
    <div class="container mt-5">
        <div class="row g-4">
            <div class="col-md-6">
                <Card>
                    <div class="card-body d-flex justify-content-between align-items-center">
                        <div>
                            <h5 class="card-title mb-1">From Frontend Developer</h5>
                            <p class="text-muted mb-0">Company XYZ - Remote</p>
                        </div>
                        <RouterLink to="/jobs" class="btn btn-success">Browse Jobs</RouterLink>
                    </div>
                </Card>
            </div>
            <div class="col-md-6">
                <Card bg="bg-white">
                    <div class="card-body d-flex justify-content-between align-items-center">
                        <div>
                            <h5 class="card-title mb-1">For Backend Developer</h5>
                            <p class="text-muted mb-0">Company ABC - New York, USA</p>
                        </div>
                        <RouterLink to="/jobs" class="btn btn-success">Browse Jobs</RouterLink>
                    </div>
                </Card>
            </div>
        </div>
    </div>
</template>