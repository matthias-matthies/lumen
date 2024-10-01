<script setup>
import { Head } from '@inertiajs/vue3';
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue'
import Card from 'primevue/card';
import {Link} from '@inertiajs/vue3';
import Button from 'primevue/button';

defineProps({
    course: {
        type: Array,
    },
});
</script>

<template>
    <AuthenticatedLayout>
        <Head title="Course" />

        <Card class="mx-4 mb-4">
            <template #title>
                <div class="flex justify-between">
                    <h1>
                        Course Information
                    </h1>
                    <div class="flex justify-end">
                        <Link
                            method="GET"
                            :href="route('course.index')"
                        >
                            <Button
                                :style="{ 'border-top-right-radius': '0px', 'border-bottom-right-radius': '0px'}"
                                label="Back"
                                icon="pi pi-angle-left"
                                severity="info"
                                outlined
                            />
                        </Link>
                        <Link
                            method="GET"
                            :href="route('course.edit', course)"
                        >
                            <Button
                                :style="{ 'border-top-left-radius': '0px', 'border-bottom-left-radius': '0px', 'border-left': '0px' }"
                                label="Edit"
                                icon="pi pi-pencil"
                                severity="secondary"
                                outlined
                            />
                        </Link>
                    </div>
                </div>
            </template>
            <template #content>
                <p>
                    Code: {{ course.code }}
                </p>
                <p>
                    Name: {{ course.name }}
                </p>
                <p>
                    Url: <a href="{{ course.url }}">{{ course.url }}</a>
                </p>
            </template>
        </Card>

        <div class="grid grid-cols-2 gap-4 mx-4">
            <Card>
                <template #title>
                    Course Lessons
                </template>
                <template #content>
                    TODO: Add lessons here
                </template>
            </Card>

            <Card>
                <template #title>
                    Course Deadlines
                </template>
                <template #content>
                    TODO: Add Deadlines here
                </template>
            </Card>
        </div>

    </AuthenticatedLayout>
</template>
