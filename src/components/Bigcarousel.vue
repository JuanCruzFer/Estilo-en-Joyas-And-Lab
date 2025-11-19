<script setup>
import {ref , onMounted, onUnmounted} from 'vue'

const props = defineProps({
    slides: {
        type: Array,
        required: true
    }
});

const currentSlideIndex = ref(0);
let intervalId = null;

const nextSlide = () => {
    currentSlideIndex.value = (currentSlideIndex.value + 1) % props.slides.length;
};

onMounted(() => {
    intervalId = setInterval(nextSlide, 5000);
});

onUnmounted(() => {
    clearInterval(intervalId);
});
</script>

<template>
    <section class="hero-carousel">
        <div 
            v-for="(slide, index) in slides" 
            :key="index"
            class="hero-slide"
            :class="{ active: index === currentSlideIndex }"
            :style="{ backgroundImage: `url(${slide.image})` }"
        >
            <div class="hero-overlay">
                <div class="hero-content">
                    <h2>{{ slide.title }}</h2>
                    <p class="hero-text">{{ slide.text }}</p>
                    <button class="btn-primary">{{ slide.buttonText }}</button>
                </div>
            </div>  
        </div>

        <div class="carousel-indicators">
            <span 
                v-for="(slide, index) in slides" 
                :key="'dot-'+index" 
                class="dot" 
                :class="{ active: index === currentSlideIndex }"
                @click="currentSlideIndex = index"
            ></span>
        </div>
    </section>
</template>

<style scoped>
/* Estilos específicos del Carrusel */
.hero-carousel {
    height: 80vh;
    width: 100%;
    position: relative;
    overflow: hidden;
}

.hero-slide {
    width: 100%;
    height: 100%;
    background-size: cover;
    background-position: center;
    position: absolute; /* Importante para superponerlos */
    top: 0;
    left: 0;
    opacity: 0;
    transition: opacity 1s ease-in-out;
    display: flex;
    justify-content: center;
    align-items: center;
}

.hero-slide.active {
    opacity: 1;
    z-index: 1;
}

.hero-overlay {
    background: rgba(0, 0, 0, 0.4);
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
}

.hero-content {
    color: white;
    max-width: 600px;
    padding: 20px;
}

.hero-content h2 {
    font-size: 3rem;
    margin-bottom: 10px;
    font-family: 'Georgia', serif;
}

.btn-primary {
  background-color: #d4af37; /* Tu color dorado */
    color: white;
    padding: 12px 30px;
    border: none;
    cursor: pointer;
    font-weight: bold;
    text-transform: uppercase;
    margin-top: 20px;
}

/* Estilo para los puntitos de navegación */
.carousel-indicators {
    position: absolute;
    bottom: 20px;
    left: 50%;
    transform: translateX(-50%);
    z-index: 2;
    display: flex;
    gap: 10px;
}

.dot {
    width: 12px;
    height: 12px;
    background-color: rgba(255,255,255,0.5);
    border-radius: 50%;
    cursor: pointer;
}

.dot.active {
    background-color: #d4af37;
}
</style>