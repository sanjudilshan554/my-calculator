<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { Head } from '@inertiajs/vue3';
import { ref } from 'vue';

const isModalOpen = ref(false);
const value1 = ref(null);
const value2 = ref(null);
const result = ref(null);

function openModal() {
    isModalOpen.value = true;
}

function closeModal() {
    isModalOpen.value = false;
    result.value = null; // Reset the result when closing
}

function calculate() {
    result.value = (value1.value || 0) + (value2.value || 0);
}

const calcButtonClasses = "w-full text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800";
const actionButtonClasses = "w-full text-white bg-green-700 hover:bg-green-800 focus:ring-4 focus:outline-none focus:ring-green-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center dark:bg-green-600 dark:hover:bg-green-700 dark:focus:ring-green-800";
</script>

<template>

    <Head title="Dashboard" />

    <AuthenticatedLayout>
        <template #header>
            <h2 class="text-xl font-semibold leading-tight text-gray-800">
                Dashboard
            </h2>
        </template>

        <div class="py-12">
            <div class="mx-auto max-w-7xl sm:px-6 lg:px-8">
                <div class="overflow-hidden bg-white shadow-sm sm:rounded-lg">
                    <div class="p-6 text-gray-900">
                        You're logged in!
                    </div>
                </div>


                <div>

                    <!-- Button to open modal -->
                    <button @click="openModal"
                        class="block text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800">
                        Basic calculator
                    </button>

                    <!-- Modal -->
                    <div v-if="isModalOpen"
                        class="fixed inset-0 flex items-center justify-center bg-black bg-opacity-50">
                        <div class="relative bg-white rounded-lg shadow dark:bg-gray-700 p-6 w-full max-w-md">
                            <!-- Close button -->
                            <button @click="closeModal"
                                class="absolute top-3 right-3 text-gray-400 hover:text-gray-900 dark:hover:text-white">
                                <span class="sr-only">Close</span>
                                ✕
                            </button>

                            <!-- Modal content -->
                            <h3 class="text-xl font-bold text-gray-900 dark:text-white mb-4">Basic Calculator</h3>

                            <!-- Input fields for the values -->
                            <div class="mb-4">
                                <input type="number" v-model.number="value1"
                                    class="mt-1 block w-full p-2 border rounded-lg bg-gray-50 dark:bg-gray-800 dark:border-gray-600 text-gray-900 dark:text-white" />
                            </div>

                            <!-- Display result -->
                            <div v-if="result !== null" class="mb-4 text-gray-900 dark:text-white">
                                Result: {{ result }}
                            </div>

                            <!-- Calculator buttons -->
                            <div class="grid grid-cols-4 gap-4">
                                <!-- Numbers and operators -->
                                <button v-for="num in ['7', '8', '9']" :key="num" @click="handleInput(num)"
                                    :class="calcButtonClasses">
                                    {{ num }}
                                </button>
                                <div>
                                    <Button :class="actionButtonClasses">/</Button>
                                </div>
                                <button v-for="num in ['4', '5', '6']" :key="num" @click="handleInput(num)"
                                    :class="calcButtonClasses">
                                    {{ num }}
                                </button>
                                <div>
                                    <Button :class="actionButtonClasses">x</Button>
                                </div>
                                <button v-for="num in ['1', '2', '3']" :key="num" @click="handleInput(num)"
                                    :class="calcButtonClasses">
                                    {{ num }}
                                </button>
                                <div>
                                    <Button :class="actionButtonClasses">-</Button>
                                </div>
                                <button v-for="num in ['0', '.', '%']" :key="num" @click="handleInput(num)"
                                    :class="calcButtonClasses">
                                    {{ num }}
                                </button>
                                <div>
                                    <Button :class="actionButtonClasses">+</Button>
                                </div>
                            </div>

                            <!-- Calculate button -->
                            <button @click="calculate"
                                class="w-full mt-4 text-white bg-green-700 hover:bg-green-800 focus:ring-4 focus:outline-none focus:ring-green-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center dark:bg-green-600 dark:hover:bg-green-700 dark:focus:ring-green-800">
                                Calculate
                            </button>
                        </div>
                    </div>
                </div>
            </div>
        </div>

    </AuthenticatedLayout>
</template>


<style></style>