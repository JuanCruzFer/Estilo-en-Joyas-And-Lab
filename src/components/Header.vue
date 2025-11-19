<script setup>
import { ref } from 'vue'

const isMenuOpen = ref(false)

const toggleMenu = () => {
    isMenuOpen.value = !isMenuOpen.value
}
</script>

<template>
    <header class="main-header">
    <div class="container header-content">
        <div class="brand">
            <div class="logo-placeholder"></div>
            <div class="brand-name">Estilo en Joyas</div>
        </div>
        <nav>
            <ul class="nav-links">
                <li><a href="#">Inicio</a></li>
                <li><a href="#">Productos</a></li>
                <li><a href="#">Sobre Nosotros</a></li>
                <li><a href="#">Contacto</a></li>
            </ul>
        </nav>
        <div class="user-actions">
            <a href="#" class="auth-link">Iniciar Sesión</a>
            <a href="#" class="auth-link">Registrarse</a>
            <div class="cart-btn">
                <i class="fas fa-shopping-cart"></i>
                <span class="cart-count">0</span>
            </div>
        </div>
    </div>
    </header>
    
</template>

<style scoped>
.main-header {
    background-color: white;
    box-shadow: 0 2px 10px rgba(0,0,0,0.05);
    padding: 1rem 0; /* Un poco más de aire arriba y abajo */
}

.header-content {
    display: flex;
    justify-content: space-between;
    align-items: center; /* ESTO ALINEA VERTICALMENTE TODO */
    padding: 0 20px;     /* Margen a los costados */
    max-width: 1200px;
    margin: 0 auto;
}

/* El resto de tus estilos... */
.nav-links {
    display: flex;
    gap: 30px;
    margin: 0; /* Asegura que no haya margen extra */
}

/* RESPONSIVE MEDIA QUERY para el header */
@media (max-width: 768px) {
    .header-content {
        flex-direction: column;
        gap: 15px;
    }
    
    .nav-links {
        gap: 15px;
        font-size: 0.9rem;
    }

    .user-actions {
        width: 100%;
        justify-content: center;
    }
}
</style>