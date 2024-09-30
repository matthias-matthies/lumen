<script setup>
import { Head } from '@inertiajs/vue3';
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue'

defineProps({
    courses: {
        type: Array,
    },
});
</script>

<template>
    <AuthenticatedLayout>
        <Head title="Edit Course" />

    </AuthenticatedLayout>
</template>
