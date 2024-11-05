<script setup>
import AppLayout from '@/Layouts/AppLayout.vue'
import bgImage from '@/../../public/images/image-from-rawpixel-id-5923662-jpeg.jpg';

</script>

<template>
    <AppLayout>
        <template #content>
            <div class="flex items-center justify-center h-screen bg-cover" :style="{ backgroundImage: `url(${bgImage})` }">
                <h1 class="fs-1 text-center align-item-center justify-content-center text-6xl text-white"> The best calculator you
                    have ever met</h1>
            </div>
        </template>
    </AppLayout>
</template>
