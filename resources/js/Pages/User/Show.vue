<script setup>
import { Head, Link, useForm } from '@inertiajs/vue3';
import AppLayout from '@/Layouts/AppLayout.vue';
import InputLabel from '@/Components/InputLabel.vue';
import PrimaryButton from '@/Components/PrimaryButton.vue';

// Definimos las props si es necesario recibir datos desde el padre
const props = defineProps(['user']);

</script>

<template>
    <AppLayout title="Usuarios">
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">
                Mostrar Usuario
            </h2>
        </template>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="bg-white overflow-hidden shadow-xl sm:rounded-lg">
                    <div class="p-6 lg:p-8 bg-white border-b border-gray-200">
                        <form @submit.prevent="submit">
                            <InputLabel for="name" :value="'Nombre : '+user.name" />
                            <InputLabel for="email" :value="'E-mail '+user.email" />
                            <InputLabel for="password" :value="'Password : '+user.password" />
                            <Link :href="route('user.index')">Volver</Link>
                        </form>
                    </div>
                </div>
            </div>
        </div>
    </AppLayout>
</template>

