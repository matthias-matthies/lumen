<script setup>
import Button from 'primevue/button'
import {Link} from '@inertiajs/vue3'

const props = defineProps({
    data: {
        type: Object,
        required: true,
    },
    target: {
        type: String,
        required: true,
    }
})
</script>

<template>
    <Link method="GET" :href="route(`${props.target}.show`, props.data)">
        <Button
            :style="{ 'border-top-right-radius': '0px', 'border-bottom-right-radius': '0px'}"
            label="Show"
            icon="pi pi-search"
            severity="info"
            outlined
        />
    </Link>
    <Link method="GET" :href="route(`${props.target}.edit`, props.data)">
        <Button
            :style="{ 'border-radius': '0px', 'border-left': '0px', 'border-right': '0px' }"
            label="Edit"
            icon="pi pi-pencil"
            severity="secondary"
            outlined
        />
    </Link>
    <Link method="DELETE" :href="route(`${props.target}.destroy`, props.data)">
        <Button
            :style="{ 'border-top-left-radius': '0px', 'border-bottom-left-radius': '0px' }"
            label="Delete"
            icon="pi pi-delete-left"
            severity="danger"
        />
    </Link>
</template>
