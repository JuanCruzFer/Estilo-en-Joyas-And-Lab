<script setup>
import ProductCard from './ProductCard.vue';

defineProps({
    products: { type: Array, required: true },
    title: { type: String, default: "Colección Exclusiva" } // Cambié el título a algo más fancy
});
</script>

<template>
    <section class="featured-products texture-bg">
        <div class="container">
        <h2 class="section-title">{{ title }}</h2>
        <p class="section-subtitle">Piezas seleccionadas para resaltar tu esencia</p>

        <div class="products-slider">
            <ProductCard 
            v-for="item in products" 
            :key="item.id" 
            :product="item"
            />
        </div>
        </div>
    </section>
</template>

<style scoped>
/* FONDO CON TEXTURA DE MÁRMOL */
.texture-bg {
    /* Esta imagen es una textura de mármol blanco elegante */
    background-image: url('https://images.unsplash.com/photo-1569083372416-1347cc820394?q=80&w=2070&auto=format&fit=crop');
    background-size: cover;
    background-position: center;
    padding: 80px 0; /* Más espacio arriba y abajo */
    position: relative;
}

/* Una capa sutil blanca encima para que el texto se lea bien */
.texture-bg::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(255, 255, 255, 0.5); /* Transparencia blanca */
    z-index: 0;
}

.container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 20px;
    position: relative;
    z-index: 1; /* Para estar encima del fondo */
}

.section-title {
    text-align: center;
    font-family: 'Playfair Display', serif; /* Usamos la fuente nueva */
    font-size: 2.5rem;
    margin-bottom: 10px;
    color: #151515;
}

.section-subtitle {
    text-align: center;
    font-family: 'Montserrat', sans-serif;
    color: #666;
    margin-bottom: 50px;
    font-weight: 300;
    letter-spacing: 1px;
}

/* Slider Horizontal */
.products-slider {
    display: flex;
    gap: 25px; /* Un poco más de espacio entre tarjetas */
    overflow-x: auto;
    padding: 20px 10px; /* Padding interno para que la sombra no se corte */
    scroll-snap-type: x mandatory;
}

.products-slider::-webkit-scrollbar { height: 6px; }
.products-slider::-webkit-scrollbar-thumb { background: #d4af37; border-radius: 10px; }
</style>