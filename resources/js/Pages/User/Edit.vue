<script setup>
import AppLayout from '@/Layouts/AppLayout.vue';
import { Head, Link, useForm } from '@inertiajs/vue3';
import InputError from '@/Components/InputError.vue';
import InputLabel from '@/Components/InputLabel.vue';
import TextInput from '@/Components/TextInput.vue';
import PrimaryButton from '@/Components/PrimaryButton.vue';

// Definimos las props si es necesario recibir datos desde el padre
const props = defineProps(['user','errors']);

// Inicializamos el formulario con los datos predefinidos
const form = useForm({
    name: props.user?.name || '',
    email: props.user?.email || '',
    password: props.user?.password ||'',
});

// Función para manejar el envío del formulario
const submit = () => {
    form.put(route('user.update', props.user.id));
};
</script>

<template>
    <AppLayout title="Usuarios">
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">
                Editar Usuario
            </h2>
        </template>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="bg-white overflow-hidden shadow-xl sm:rounded-lg">
                    <div class="p-6 lg:p-8 bg-white border-b border-gray-200">
                        
                        <form @submit.prevent="submit">
                            <InputLabel for="name" value="Nombre"/>
                            <InputError :message="errors.name"/>
                            <TextInput type="text" v-model="form.name" id="name" class="mt-1 block w-full" required />

                            <InputLabel for="email" value="Email"/>
                            <InputError :message="errors.email"/>
                            <TextInput type="email" v-model="form.email" id="email" class="mt-1 block w-full" required />

                            <InputLabel for="password" value="Contraseña"/>
                            <InputError :message="errors.password"/>
                            <TextInput type="password" v-model="form.password" id="password" class="mt-1 block w-full" required />

                            <PrimaryButton class="mt-4" :class="{ 'opacity-25': form.processing }" :disabled="form.processing">
                                Actualizar
                            </PrimaryButton>
                        </form>
                    </div>
                </div>
            </div>
        </div>
    </AppLayout>
</template>

