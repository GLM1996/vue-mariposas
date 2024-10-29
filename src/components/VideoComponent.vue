<template>
  <div class="video-container">
    <h1>Video de Facebook</h1>
    <div class="fb-video" data-href="https://www.facebook.com/100064220524675/videos/1579846919123471/" data-width="600"
      data-height="400" data-allowfullscreen="true">
    </div>
  </div>
</template>

<script>
export default {
  name: 'FacebookVideoComponent',
  mounted() {
    // Cargar el SDK de Facebook para incrustar videos
    if (typeof FB !== 'undefined') {
      FB.XFBML.parse();
    } else {
      const script = document.createElement('script');
      script.src = 'https://connect.facebook.net/en_US/sdk.js#xfbml=1&version=v10.0';
      script.async = true;
      script.onload = () => {
        if (typeof FB !== 'undefined') {
          FB.XFBML.parse();
        }
      };
      document.body.appendChild(script);
    }
  }
};
</script>

<style scoped>
.video-container {
  text-align: center;
  /* Centrar el contenido */
}

/* Opcional: estilos para mejorar el diseño de los videos */
.video-container {
    position: relative;
    overflow: hidden;
    padding-top: 56.25%;
}

.video-container iframe {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
}
</style>