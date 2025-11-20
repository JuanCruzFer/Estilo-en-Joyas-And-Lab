<script setup>
import Header from './Header.vue'
import Bigcarousel from './Bigcarousel.vue'
import ProductSlider from './ProductSlider.vue'
import Footer from './Footer.vue'


// Datos del Carrusel Grande
const heroSlides = [
  {
    title: "Elegancia que perdura",
    text: "Explora nuestros productos exclusivos y encuentra la joya perfecta.",
    image: "https://images.unsplash.com/photo-1515562141207-7a88fb7ce338?q=80&w=2070&auto=format&fit=crop",
    buttonText: "Ver Colección"
  },
  {
    title: "Brillo de Temporada",
    text: "Nuestra colección hecha para deslumbrar.",
    image: "https://images.unsplash.com/photo-1601121141461-9d6647bca1ed?q=80&w=2070&auto=format&fit=crop",
    buttonText: "Comprar Ahora"
  },
  {
    title: "Minimalismo Puro",
    text: "Detalles sutiles que marcan la diferencia.",
    image: "https://images.unsplash.com/photo-1573408301185-9146fe634ad0?q=80&w=2075&auto=format&fit=crop",
    buttonText: "Descubrir"
  }
];

// Datos de los Productos
const jewelryProducts = [
  {
    id: 1,
    name: "Anillo Solitario",
    price: "$120.00 USD",
    image: "https://images.unsplash.com/photo-1535632066927-ab7c9ab60908?q=80&w=800&auto=format&fit=crop"
  },
  {
    id: 2,
    name: "Collar Minimalista",
    price: "$85.00 USD",
    image: "https://images.unsplash.com/photo-1535632066927-ab7c9ab60908?q=80&w=800&auto=format&fit=crop"
  },
  {
    id: 3,
    name: "Aretes Clásicos",
    price: "$210.00 USD",
    image: "https://images.unsplash.com/photo-1611591437281-460bfbe1220a?q=80&w=800&auto=format&fit=crop"
  },
  {
    id: 4,
    name: "Pulsera Gold",
    price: "$150.00 USD",
    image: "https://images.unsplash.com/photo-1602173574767-37ac01994b2a?q=80&w=800&auto=format&fit=crop"
  }
];
</script>

<template>
  <div class="app-container">
    <Header />
    
    <Bigcarousel :slides="heroSlides" />
    
    <ProductSlider :products="jewelryProducts" title="Algunas de Nuestras Joyas" />
    
    <Footer />
  </div>
</template>

<style scoped>
.app-container {
    width: 100%;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
}
</style>  
