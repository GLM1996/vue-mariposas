<template>
  <div :style="{ height: bannerHeight + 'px' }" class="flex flex-between flex-wrap w-100 bg-violet-700 p-4 text-white">
    <div class="w-full sm:w-1/2 flex flex-col justify-center items-center">
      <h1 class="text-4xl sm:text-4xl font-bold text-center mb-1">Quienes somos?</h1>
      <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Consequuntur repellat quos, ipsam fugiat ea quasi sed
        voluptatem repellendus possimus debitis quaerat nam est reiciendis consequatur corporis soluta cum atque
        dignissimos.</p>
    </div>
    <div class="w-full sm:w-1/2 flex justify-center items-center">
      <img src="/src/assets/logo.png" alt="Descripción de la imagen" class="w-1/2 h-auto object-cover">
    </div>
  </div>
</template>

<script setup>

import { ref, onMounted, onBeforeUnmount } from 'vue';

const bannerHeight = ref(0); // Ref para la altura del banner

const updateBannerHeight = () => {
  const navbar = document.querySelector('nav'); // Selecciona el navbar

  if (navbar) {
    bannerHeight.value = window.innerHeight - navbar.offsetHeight; // Calcula la altura del banner
  }
};

onMounted(() => {
  updateBannerHeight(); // Calcula la altura al montar el componente
  window.addEventListener('resize', updateBannerHeight); // Escucha el evento de resize
});

onBeforeUnmount(() => {
  window.removeEventListener('resize', updateBannerHeight); // Limpia el listener de resize
});
</script>

<style scoped></style>