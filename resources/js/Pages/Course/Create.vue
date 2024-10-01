<script setup>
import {Head, Link, useForm} from '@inertiajs/vue3'
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue'
import Card from 'primevue/card'
import InputText from 'primevue/inputtext'
import Button from 'primevue/button'
import Message from 'primevue/message'

const form = useForm({
    code: '',
    name: '',
    url: '',
});

const submit = () => {
    form.post(route('course.store'), {
        //onFinish: () => form.reset('code', 'name', 'url'),
    });
};
</script>

<template>
    <AuthenticatedLayout>
        <Head title="Create Course" />

        <Card class="mx-4">
            <template #title>
                <div class="flex justify-between">
                    <h1>Create Course</h1>
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
                        <Button
                            :style="{ 'border-top-left-radius': '0px', 'border-bottom-left-radius': '0px', 'border-left': '0px' }"
                            @click="submit"
                            label="Create"
                            icon="pi pi-plus"
                            outlined
                        />
                    </div>
                </div>
            </template>

            <template #content>
                <form @submit.prevent="submit">
                    <div>
                        <label for="code" class="block">Code*</label>
                        <InputText
                            id="code"
                            type="text"
                            class="mt-1 block w-full"
                            v-model="form.code"
                            autofocus
                        />
                        <Message v-if="form.errors.code" severity="error" class="mt-2">{{ form.errors.code }}</Message>
                    </div>

                    <div class="mt-4">
                        <label for="name" class="block">Name*</label>
                        <InputText
                            id="name"
                            type="text"
                            class="mt-1 block w-full"
                            v-model="form.name"
                        />
                        <Message v-if="form.errors.name" severity="error" class="mt-2">{{ form.errors.name }}</Message>
                    </div>

                    <div class="mt-4">
                        <label for="url" class="block">Url</label>
                        <InputText
                            id="url"
                            type="url"
                            class="mt-1 block w-full"
                            v-model="form.url"
                        />
                        <Message v-if="form.errors.url" severity="error" class="mt-2">{{ form.errors.url }}</Message>
                    </div>

                    <div class="mt-4 flex items-center justify-end">
                        <Button
                            @click="submit"
                            label="Create"
                            icon="pi pi-plus"
                            class="p-button-outlined"
                        />
                    </div>
                </form>
            </template>

        </Card>
    </AuthenticatedLayout>
</template>
