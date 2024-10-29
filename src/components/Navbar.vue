<template>
    <nav class="bg-violet-500 p-4 sticky top-0 z-50">
        <div class="container mx-auto flex justify-between items-center">
            <a href="#" class="text-white text-lg font-semibold">Mi Portafolio</a>
            <div class="hidden md:flex space-x-4">
                <a href="#about" class="text-white hover:bg-violet-700 px-3 py-2 rounded">Sobre mí</a>
                <a href="#skills" class="text-white hover:bg-violet-700 px-3 py-2 rounded">Skills</a>
                <a href="#projects" class="text-white hover:bg-violet-700 px-3 py-2 rounded">Proyectos</a>
                <a href="#contact" class="text-white hover:bg-violet-700 px-3 py-2 rounded">Contacto</a>
            </div>
            <div class="hidden md:flex">
                <button class="text-white bg-violet-700 p-2 mr-2 rounded-md">Face</button>
                <button class="text-white bg-violet-700 p-2 mr-2 rounded-md">Youtube</button>
            </div>
            <button class="md:hidden text-white" @click="toggleMenu">
                <svg v-if="isMenuOpen" xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none"
                    viewBox="0 0 24 24" stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
                </svg>
                <svg v-else xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24"
                    stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16m-7 6h7" />
                </svg>
            </button>
        </div>
        <div v-if="isMenuOpen" class="md:hidden  p-4">
            <a href="#about" class="block text-white hover:bg-violet-700 px-3 py-2 rounded w-max">Sobre mí</a>
            <a href="#skills" class="block text-white hover:bg-violet-700 px-3 py-2 rounded w-max">Skills</a>
            <a href="#projects" class="block text-white hover:bg-violet-700 px-3 py-2 rounded w-max">Proyectos</a>
            <a href="#contact" class="block text-white hover:bg-violet-700 px-3 py-2 rounded w-max">Contacto</a>
            <div class="flex mt-4">
                <button class="text-white bg-violet-700 p-2 mr-2 rounded-md">Face</button>
                <button class="text-white bg-violet-700 p-2 mr-2 rounded-md">Youtube</button>
            </div>
        </div>
    </nav>
</template>

<script setup>
import { ref } from 'vue';

const isMenuOpen = ref(false);

const toggleMenu = () => {
    isMenuOpen.value = !isMenuOpen.value;
};
</script>

<style>
/* Estilos opcionales */
</style>