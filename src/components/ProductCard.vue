<script setup>
    defineProps({
        product: {
            type: Object,
            required: true
        }
    })
</script>

<template>
    <article class="product-card">
        <div class="product-img">
            <img :src="product.image" :alt="product.name">
        </div>
        <div class="product-info">
            <h3>{{ product.name }}</h3>
            <p class="price">{{ product.price }}</p>
            <button class="btn-secondary" @click="$emit('add-to-cart', product)">Agregar al carrito</button>
        </div>
    </article>
</template>

<style scoped>
.product-card {
    min-width: 250px; /* Ancho fijo para el carrusel */
    background: white;
    border: 1px solid #eee;
    scroll-snap-align: start;
    transition: transform 0.3s;
}

.product-card:hover {
    transform: translateY(-5px);
    box-shadow: 0 5px 15px rgba(0,0,0,0.1);
}

.product-img {
    height: 250px;
    width: 100%;
    overflow: hidden;
}

.product-img img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: transform 0.3s;
}

.product-card:hover .product-img img {
    transform: scale(1.05);
}

.product-info {
    padding: 15px;
    text-align: center;
}

.price {
    color: #d4af37;
    font-weight: bold;
    margin: 10px 0;
}

.btn-secondary {
    border: 1px solid #1a1a1a;
    background: transparent;
    padding: 8px 20px;
    cursor: pointer;
    transition: 0.3s;
}

.btn-secondary:hover {
    background: #1a1a1a;
    color: white;
}
</style>