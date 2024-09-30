<script setup>
import { Head } from '@inertiajs/vue3';
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue'
import DataTable from 'primevue/datatable'
import Column from 'primevue/column'
import DataTableButtons from '@/Components/DataTable/DataTableButtons.vue'
import Card from 'primevue/card'
import Button from 'primevue/button'
import {Link} from '@inertiajs/vue3'

defineProps({
    courses: {
        type: Array,
    },
});
</script>

<template>
    <AuthenticatedLayout>
        <Head title="Courses" />
        <Card class="mx-4">
            <template #title>
                <h1>Courses</h1>
            </template>
            <template #subtitle>
                <div class="flex justify-between items-center">
                    <p>Liste aller aktiven Kurse.</p>
                    <Link method="GET" :href="route(`course.create`)">
                        <Button
                            label="Create"
                            icon="pi pi-plus"
                            outlined
                        />
                    </Link>
                </div>
            </template>
            <template #content>
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
            </template>
        </Card>
    </AuthenticatedLayout>
</template>
