<template>
    <div class="w-full bg-violet-700 p-4 text-white">
        <h2 class="md:text-3xl text-center font-bold">Galería de Videos</h2>
        <div class="grid grid-cols sm:grid-cols-2 md:grid-cols-4 gap-4 mt-4">
            <div v-for="video in videos" :key="video.id"
                class="overflow-hidden w-full m-auto rounded-lg bg-violet-800 p-3 animate-fade-in transition transform duration-300 hover:scale-105 hover:shadow-lg animate-on-visible"
                :ref="setObserver">

                <!-- Facebook video embed with aspect ratio container -->
                <div class="relative w-full" style="padding-top: 56.25%;"> <!-- 16:9 Aspect Ratio -->
                    <div @click="toggleFullScreen(video.id)" class="absolute inset-0 cursor-pointer z-10"></div> <!-- Div que captura el clic -->
                    <iframe :ref="el => videoRefs[video.id] = el"
                        :src="`https://www.facebook.com/plugins/video.php?href=${encodeURIComponent(video.src)}&show_text=0&width=500&height=315&controls=1`"
                        style="border:none; overflow:hidden; position: absolute; top: 0; left: 0; width: 100%; height: 100%;"
                        scrolling="no" frameborder="0" allowfullscreen
                        allow="autoplay; clipboard-write; encrypted-media; picture-in-picture; web-share"></iframe>
                </div>
                <div class="flex flex-col bg-violet-500 p-2 rounded-b-2xl">
                    <strong>Descripción</strong>
                    <p>{{ video.descripcion }}</p>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
import { onMounted, ref } from 'vue';
const videoRefs = ref({});  // para almacenar referencias a los iframes de cada video
const videos = [
    {
        id: 'video-1',
        src: 'https://www.facebook.com/100064220524675/videos/1579846919123471/',
        descripcion: 'test'
    },
    {
        id: 'video-2',
        src: 'https://scontent-mia3-2.xx.fbcdn.net/v/t39.30808-6/290120095_1637531889952443_5729962084350761701_n.jpg?stp=dst-jpg_s600x600&_nc_cat=107&ccb=1-7&_nc_sid=833d8c&_nc_ohc=XRmHWkS1OB0Q7kNvgHFbtFi&_nc_zt=23&_nc_ht=scontent-mia3-2.xx&_nc_gid=ABset6ObY9boRLyPvBHsWI9&oh=00_AYAApTYQdcZk9G10H50xJ7vt-Fq7enjznfVtWcr5NP5ECg&oe=6725ECDC',
        descripcion: 'test'
    }, {
        id: 'video-3',
        src: 'https://scontent-mia3-2.xx.fbcdn.net/v/t39.30808-6/289795040_1637531239952508_8590658022412379484_n.jpg?stp=dst-jpg_p235x350&_nc_cat=110&ccb=1-7&_nc_sid=833d8c&_nc_ohc=xYTLYxfYrOgQ7kNvgE2Ftft&_nc_zt=23&_nc_ht=scontent-mia3-2.xx&_nc_gid=ABset6ObY9boRLyPvBHsWI9&oh=00_AYBr1ziNfS7guoY-8i_TCmNmdnETMInfPbpw-SrEc28QQQ&oe=6725EB94',
        descripcion: 'test'
    }, {
        id: 'video-4',
        src: 'https://scontent-mia3-2.xx.fbcdn.net/v/t39.30808-6/289795040_1637531239952508_8590658022412379484_n.jpg?stp=dst-jpg_p235x350&_nc_cat=110&ccb=1-7&_nc_sid=833d8c&_nc_ohc=xYTLYxfYrOgQ7kNvgE2Ftft&_nc_zt=23&_nc_ht=scontent-mia3-2.xx&_nc_gid=ABset6ObY9boRLyPvBHsWI9&oh=00_AYBr1ziNfS7guoY-8i_TCmNmdnETMInfPbpw-SrEc28QQQ&oe=6725EB94',
        descripcion: 'test'
    },
    {
        id: 'video-5',
        src: 'https://scontent-mia3-2.xx.fbcdn.net/v/t39.30808-6/289795040_1637531239952508_8590658022412379484_n.jpg?stp=dst-jpg_p235x350&_nc_cat=110&ccb=1-7&_nc_sid=833d8c&_nc_ohc=xYTLYxfYrOgQ7kNvgE2Ftft&_nc_zt=23&_nc_ht=scontent-mia3-2.xx&_nc_gid=ABset6ObY9boRLyPvBHsWI9&oh=00_AYBr1ziNfS7guoY-8i_TCmNmdnETMInfPbpw-SrEc28QQQ&oe=6725EB94',
        descripcion: 'test'
    },
    {
        id: 'video-6',
        src: 'https://scontent-mia3-2.xx.fbcdn.net/v/t39.30808-6/289795040_1637531239952508_8590658022412379484_n.jpg?stp=dst-jpg_p235x350&_nc_cat=110&ccb=1-7&_nc_sid=833d8c&_nc_ohc=xYTLYxfYrOgQ7kNvgE2Ftft&_nc_zt=23&_nc_ht=scontent-mia3-2.xx&_nc_gid=ABset6ObY9boRLyPvBHsWI9&oh=00_AYBr1ziNfS7guoY-8i_TCmNmdnETMInfPbpw-SrEc28QQQ&oe=6725EB94',
        descripcion: 'test'
    }, {
        id: 'video-7',
        src: 'https://scontent-mia3-2.xx.fbcdn.net/v/t39.30808-6/289795040_1637531239952508_8590658022412379484_n.jpg?stp=dst-jpg_p235x350&_nc_cat=110&ccb=1-7&_nc_sid=833d8c&_nc_ohc=xYTLYxfYrOgQ7kNvgE2Ftft&_nc_zt=23&_nc_ht=scontent-mia3-2.xx&_nc_gid=ABset6ObY9boRLyPvBHsWI9&oh=00_AYBr1ziNfS7guoY-8i_TCmNmdnETMInfPbpw-SrEc28QQQ&oe=6725EB94',
        descripcion: 'test'
    }, {
        id: 'video-8',
        src: 'https://scontent-mia3-2.xx.fbcdn.net/v/t39.30808-6/289795040_1637531239952508_8590658022412379484_n.jpg?stp=dst-jpg_p235x350&_nc_cat=110&ccb=1-7&_nc_sid=833d8c&_nc_ohc=xYTLYxfYrOgQ7kNvgE2Ftft&_nc_zt=23&_nc_ht=scontent-mia3-2.xx&_nc_gid=ABset6ObY9boRLyPvBHsWI9&oh=00_AYBr1ziNfS7guoY-8i_TCmNmdnETMInfPbpw-SrEc28QQQ&oe=6725EB94',
        descripcion: 'test'
    }
];


// Función para expandir a pantalla completa
const toggleFullScreen = (videoId) => {
    const videoElement = videoRefs.value[videoId];   
        // Si no está en pantalla completa, entrar
        if (videoElement.requestFullscreen) {
            videoElement.requestFullscreen();
        } else if (videoElement.mozRequestFullScreen) { // Firefox
            videoElement.mozRequestFullScreen();
        } else if (videoElement.webkitRequestFullscreen) { // Chrome, Safari y Opera
            videoElement.webkitRequestFullscreen();
        } else if (videoElement.msRequestFullscreen) { // IE/Edge
            videoElement.msRequestFullscreen();
        }
};

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

/* TailwindCSS aspect-ratio utility for fixed ratio */
.aspect-w-16 {
    width: 100%;
}

.aspect-h-9 {
    padding-top: 56.25%;
    /* 16:9 aspect ratio */
    position: relative;
}

.aspect-w-16>iframe {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
}

/* Estilos para pantalla completa */
:fullscreen iframe {
    width: 100vw;
    /* 100% del ancho de la ventana */
    height: 100vh;
    /* 100% de la altura de la ventana */
    position: fixed;
    /* Fijo en la pantalla */
    top: 0;
    left: 0;
    z-index: 9999;
    /* Asegúrate de que esté por encima de otros elementos */
}
</style>