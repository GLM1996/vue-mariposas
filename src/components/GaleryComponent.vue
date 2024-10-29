<template>
    <div class="w-full bg-violet-600 px-4 py-12 text-white" >
        <h2 class="md:text-3xl text-center font-bold">Galería de Imágenes</h2>
        <div class="grid sm:grid-cols-2 md:grid-cols-4 gap-4 mt-4 ">
            <div v-for="imagen in imágenes" :key="imagen.id" 
            class="overflow-hidden rounded-lg card w-full m-auto bg-violet-800 p-3 animate-fade-in transition transform duration-300 hover:scale-105 hover:shadow-lg animate-on-visible"
            :ref="setObserver">
                <img 
                :src="imagen.src" 
                alt="Imagen"
                class="w-full h-max-72 sm:h-48 object-cover rounded-t-2xl" />
                <div class="flex flex-col bg-violet-500 p-2 rounded-b-2xl">
                    <strong>Descripcion</strong>
                    <p>{{ imagen.descripcion }}</p>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
import { onMounted, ref } from 'vue';
const imágenes = [
    {
        id: 'imagen-1',
        src: 'https://scontent-mia3-2.xx.fbcdn.net/v/t39.30808-6/289795040_1637531239952508_8590658022412379484_n.jpg?stp=dst-jpg_p235x350&_nc_cat=110&ccb=1-7&_nc_sid=833d8c&_nc_ohc=xYTLYxfYrOgQ7kNvgE2Ftft&_nc_zt=23&_nc_ht=scontent-mia3-2.xx&_nc_gid=ABset6ObY9boRLyPvBHsWI9&oh=00_AYBr1ziNfS7guoY-8i_TCmNmdnETMInfPbpw-SrEc28QQQ&oe=6725EB94',
        descripcion: 'test'
    },
    {
        id: 'imagen-2',
        src: 'https://scontent-mia3-2.xx.fbcdn.net/v/t39.30808-6/290120095_1637531889952443_5729962084350761701_n.jpg?stp=dst-jpg_s600x600&_nc_cat=107&ccb=1-7&_nc_sid=833d8c&_nc_ohc=XRmHWkS1OB0Q7kNvgHFbtFi&_nc_zt=23&_nc_ht=scontent-mia3-2.xx&_nc_gid=ABset6ObY9boRLyPvBHsWI9&oh=00_AYAApTYQdcZk9G10H50xJ7vt-Fq7enjznfVtWcr5NP5ECg&oe=6725ECDC',
        descripcion: 'test'
    }, {
        id: 'imagen-3',
        src: 'https://scontent-mia3-2.xx.fbcdn.net/v/t39.30808-6/290585434_1637531839952448_1951835526741824837_n.jpg?stp=dst-jpg_s600x600&_nc_cat=105&ccb=1-7&_nc_sid=833d8c&_nc_ohc=MPuKlaRnvl8Q7kNvgElkMvU&_nc_zt=23&_nc_ht=scontent-mia3-2.xx&_nc_gid=ABset6ObY9boRLyPvBHsWI9&oh=00_AYDaZbOJYpUdz6okmPRTyPtsKDnIL_NMSGT3xnj_tGGVFw&oe=6726054E',
        descripcion: 'test'
    }, {
        id: 'imagen-4',
        src: 'https://scontent-mia3-2.xx.fbcdn.net/v/t39.30808-6/289795040_1637531239952508_8590658022412379484_n.jpg?stp=dst-jpg_p235x350&_nc_cat=110&ccb=1-7&_nc_sid=833d8c&_nc_ohc=xYTLYxfYrOgQ7kNvgE2Ftft&_nc_zt=23&_nc_ht=scontent-mia3-2.xx&_nc_gid=ABset6ObY9boRLyPvBHsWI9&oh=00_AYBr1ziNfS7guoY-8i_TCmNmdnETMInfPbpw-SrEc28QQQ&oe=6725EB94',
        descripcion: 'test'
    },
    {
        id: 'imagen-5',
        src: 'https://scontent-mia3-2.xx.fbcdn.net/v/t39.30808-6/289795040_1637531239952508_8590658022412379484_n.jpg?stp=dst-jpg_p235x350&_nc_cat=110&ccb=1-7&_nc_sid=833d8c&_nc_ohc=xYTLYxfYrOgQ7kNvgE2Ftft&_nc_zt=23&_nc_ht=scontent-mia3-2.xx&_nc_gid=ABset6ObY9boRLyPvBHsWI9&oh=00_AYBr1ziNfS7guoY-8i_TCmNmdnETMInfPbpw-SrEc28QQQ&oe=6725EB94',
        descripcion: 'test'
    },
    {
        id: 'imagen-6',
        src: 'https://scontent-mia3-2.xx.fbcdn.net/v/t39.30808-6/289795040_1637531239952508_8590658022412379484_n.jpg?stp=dst-jpg_p235x350&_nc_cat=110&ccb=1-7&_nc_sid=833d8c&_nc_ohc=xYTLYxfYrOgQ7kNvgE2Ftft&_nc_zt=23&_nc_ht=scontent-mia3-2.xx&_nc_gid=ABset6ObY9boRLyPvBHsWI9&oh=00_AYBr1ziNfS7guoY-8i_TCmNmdnETMInfPbpw-SrEc28QQQ&oe=6725EB94',
        descripcion: 'test'
    }, {
        id: 'imagen-7',
        src: 'https://scontent-mia3-2.xx.fbcdn.net/v/t39.30808-6/289795040_1637531239952508_8590658022412379484_n.jpg?stp=dst-jpg_p235x350&_nc_cat=110&ccb=1-7&_nc_sid=833d8c&_nc_ohc=xYTLYxfYrOgQ7kNvgE2Ftft&_nc_zt=23&_nc_ht=scontent-mia3-2.xx&_nc_gid=ABset6ObY9boRLyPvBHsWI9&oh=00_AYBr1ziNfS7guoY-8i_TCmNmdnETMInfPbpw-SrEc28QQQ&oe=6725EB94',
        descripcion: 'test'
    }, {
        id: 'imagen-8',
        src: 'https://scontent-mia3-2.xx.fbcdn.net/v/t39.30808-6/289795040_1637531239952508_8590658022412379484_n.jpg?stp=dst-jpg_p235x350&_nc_cat=110&ccb=1-7&_nc_sid=833d8c&_nc_ohc=xYTLYxfYrOgQ7kNvgE2Ftft&_nc_zt=23&_nc_ht=scontent-mia3-2.xx&_nc_gid=ABset6ObY9boRLyPvBHsWI9&oh=00_AYBr1ziNfS7guoY-8i_TCmNmdnETMInfPbpw-SrEc28QQQ&oe=6725EB94',
        descripcion: 'test'
    }
];
const setObserver = (el) => {
    if (!el) return;

    const observer = new IntersectionObserver((entries) => {
        entries.forEach((entry) => {
            if (entry.isIntersecting) {
                entry.target.classList.add('fade-in');
                observer.unobserve(entry.target);
            }
        });
    });

    observer.observe(el);
};
</script>

<style scoped>
@keyframes fadeIn {
    from {
        opacity: 0;
        transform: translateY(25px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

.fade-in {
    opacity: 1 !important;
    animation: fadeIn 0.9s ease-in-out;
}

.animate-on-visible {
    opacity: 0;
}
</style>