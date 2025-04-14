<script setup>
import { ref, defineProps, computed } from 'vue';

const props = defineProps({
    jobs: Object
});

const showFullDescription = ref(false);

const toggleFullDescription = () => {
    showFullDescription.value = !showFullDescription.value
}

const truncatedDescription = computed(() => {
    let description = props.jobs.description;

    if (!showFullDescription.value) {
        description = description.substring(0, 90) + '...';
    }

    return description
});

</script>

<template>
    <div class="">
        <div class="">
            {{ truncatedDescription }}
        </div>
        <button @click="toggleFullDescription()" class="btn btn-sm btn-success mt-2">
            {{ showFullDescription ? 'Less' : 'More' }}
        </button>
    </div>
</template>