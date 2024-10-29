<template>
    <div class="w-full  bg-violet-600 p-4 text-white">
        <div class="grid w-full md:w-10/12 m-auto gap-2 mt-4">
            <div v-for="(imagen, index) in imágenes" :key="imagen.id"
                :class="index % 2 === 0 ? 'flex-col md:flex-row' : 'flex-col md:flex-row-reverse'"
                class="flex items-center  overflow-hidden rounded-lg  py-2 px-8 animate-fade-in">

                <div class="relative w-full md:w-1/2 p-2">
                    <img :src="imagen.src" alt="Imagen" class="w-max-full h-max-64 object-cover rounded-2xl" />
                </div>
                <div class="flex flex-col w-full md:w-1/2  items-center justify-around h-full p-2">
                    <strong class="md:text-4xl">Descripción</strong>
                    <p>{{ imagen.descripcion }}</p>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>

const imágenes = [
    {
        id: 'imagen-1',
        src: 'https://scontent-mia3-2.xx.fbcdn.net/v/t39.30808-6/289795040_1637531239952508_8590658022412379484_n.jpg?stp=dst-jpg_p235x350&_nc_cat=110&ccb=1-7&_nc_sid=833d8c&_nc_ohc=xYTLYxfYrOgQ7kNvgE2Ftft&_nc_zt=23&_nc_ht=scontent-mia3-2.xx&_nc_gid=ABset6ObY9boRLyPvBHsWI9&oh=00_AYBr1ziNfS7guoY-8i_TCmNmdnETMInfPbpw-SrEc28QQQ&oe=6725EB94',
        descripcion: 'loremi aopsdfopsdo sdjfas dfkjsdf sdljfsd fklsdjflas dfsjdklf sldfsl fs dfkls klfjasdklf asdklj f'
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
];


</script>

<style scoped>
.animate-fade-in {
    opacity: 0;
    animation: fadeIn 0.9s forwards;
}

@keyframes fadeIn {
    from {
        opacity: 0;
        transform: translateY(10px);
    }

    to {
        opacity: 1;
        transform: translateY(0);
    }
}
</style>
