<template>

    <div class="flex flex-col min-h-screen">
        <Navbar />

        <main>
            <slot name="content" />

            <slot name="modal" />
        </main>

        <Footer />
    </div>

</template>

<script setup>
import Navbar from '@/Components/Main/Navbar.vue';
import Footer from '@/Components/Main/Footer.vue';



</script>