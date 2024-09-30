<script setup>
import { ref } from 'vue';
import PrimaryNavigationMenu from '@/Components/PrimaryNavigationMenu.vue'
import Card from 'primevue/card';

const showingNavigationDropdown = ref(false);
</script>

<template>
    <div class="min-h-screen bg-gray-100">
        <PrimaryNavigationMenu />

        <main>
            <slot />
        </main>
    </div>
</template>
