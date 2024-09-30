<script setup>
import {Head, Link, useForm} from '@inertiajs/vue3'
import { ref } from 'vue'
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue'
import Card from 'primevue/card'
import InputText from 'primevue/inputtext'
import InputGroup from 'primevue/inputgroup'
import InputGroupAddon from 'primevue/inputgroupaddon'
import Button from 'primevue/button'
import PrimaryButton from '@/Components/PrimaryButton.vue'
import InputError from '@/Components/InputError.vue'
import InputLabel from '@/Components/InputLabel.vue'
import TextInput from '@/Components/TextInput.vue'


const form = useForm({
    code: '',
    name: '',
    url: '',
});

const submit = () => {
    form.post(route('course.store'), {
        onFinish: () => form.reset('code', 'name', 'url'),
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
                        <InputLabel for="code" value="Code" />

                        <TextInput
                            id="code"
                            type="text"
                            class="mt-1 block w-full"
                            v-model="form.code"
                            required
                            autofocus
                        />

                        <InputError class="mt-2" :message="form.errors.code" />
                    </div>

                    <div class="mt-4">
                        <InputLabel for="name" value="Name" />

                        <TextInput
                            id="name"
                            type="text"
                            class="mt-1 block w-full"
                            v-model="form.name"
                            required
                        />

                        <InputError class="mt-2" :message="form.errors.name" />
                    </div>

                    <div class="mt-4">
                        <InputLabel for="url" value="Url" />

                        <TextInput
                            id="url"
                            type="url"
                            class="mt-1 block w-full"
                            v-model="form.url"
                            required
                        />

                        <InputError class="mt-2" :message="form.errors.password" />
                    </div>

                    <div class="mt-4 flex items-center justify-end">

                        <Button
                            @click="submit"
                            label="Create"
                            icon="pi pi-plus"
                            outlined
                        />
                    </div>
                </form>
            </template>
        </Card>
    </AuthenticatedLayout>
</template>
