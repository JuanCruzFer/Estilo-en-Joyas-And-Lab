<script setup>
import ProductCard from './ProductCard.vue';

defineProps({
    products: { type: Array, required: true },
    title: { type: String, default: "Nuestras Joyas" }
});
</script>

<template>
    <section class="featured-products container">
        <h2 class="section-title">{{ title }}</h2>
        <div class="products-slider">
        <ProductCard 
            v-for="item in products" 
            :key="item.id" 
            :product="item" 
        />
        </div>
    </section>
    </template>

<style scoped>
.container { max-width: 1200px; margin: 0 auto; padding: 0 20px; }
.featured-products { padding: 60px 20px; }
.section-title { text-align: center; font-family: 'Georgia', serif; font-size: 2rem; margin-bottom: 40px; color: #1a1a1a; }

/* CLAVE PARA EVITAR EL ZOOM: Scroll horizontal */
.products-slider {
    display: flex;
    gap: 20px;
    overflow-x: auto;
    padding-bottom: 20px;
    scroll-snap-type: x mandatory;
}
.products-slider::-webkit-scrollbar { height: 8px; }
.products-slider::-webkit-scrollbar-thumb { background: #ccc; border-radius: 4px; }
</style>