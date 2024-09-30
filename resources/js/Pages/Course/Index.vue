<script setup>
import { Head } from '@inertiajs/vue3';
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue'
import DataTable from 'primevue/datatable'
import Column from 'primevue/column'
import DataTableButtons from '@/Components/DataTable/DataTableButtons.vue'

defineProps({
    courses: {
        type: Array,
    },
});
</script>

<template>
    <AuthenticatedLayout>
        <Head title="Courses" />

        <DataTable :value="courses" tableStyle="min-width: 50rem">
            <Column field="code" header="Code"></Column>
            <Column field="name" header="Name"></Column>
            <Column field="url" header="Url">
                <template #body="{ data }">
                    <a :href="data.url" target="_blank">{{ data.url }}</a>
                </template>
            </Column>
            <Column class="!text-end">
                <template #body="{ data }">
                    <DataTableButtons :data="data" target='course'/>
                </template>
            </Column>
        </DataTable>

    </AuthenticatedLayout>
</template>
