<script setup>
import { ref } from 'vue'
const isMenuOpen = ref(false)
const isDropdownOpen = ref(false)
const toggleMenu = () => {
    isMenuOpen.value = !isMenuOpen.value
}
const scrollToContact = () => {
    const contactSection = document.getElementById('contact')
    if (contactSection) {
        contactSection.scrollIntoView({ behavior: 'smooth' , block: 'start'})
        isMenuOpen.value = false;
    }
}
</script>

<template>
    <header class="main-header">
        <div class="container header-content">
            <div class="brand">
                <i class="fa-regular fa-gem logo-icon"></i>
                <div class="brand-name">Estilo en Joyas</div>
            </div>

            <nav :class="{ 'open': isMenuOpen }">
                <ul class="nav-links">
                    <li><a href="#">Inicio</a></li> 
                    <li class="dropdown-wrapper"
                        @mouseenter = "isDropdownOpen = true"
                        @mouseleave = "isDropdownOpen = false">

                        <a href="#" class="dropdown-trigger">Productos
                            <i class="fa-solid fa-chevron-down arrow-icon"></i>
                        </a>
                        <transition name="fade">
                            <ul v-if="isDropdownOpen" class="dropdown-menu">
                                <li><a href="#">Ver Todos</a></li>
                                <li class="separator"></li> <li><a href="#">Anillos</a></li>
                                <li><a href="#">Pulseras</a></li>
                                <li><a href="#">Tobilleras</a></li>
                                <li><a href="#">Cadenas</a></li>
                                <li><a href="#">Aritos</a></li>
                                <li><a href="#">Dijes</a></li>
                            </ul>
                        </transition>
                    </li>
                    <li><a href="#" @click.prevent="scrollToContact">Contacto</a></li>
                </ul>
            </nav>

            <div class="user-actions">
                <div class="auth-links">
                    <a href="#" class="login-link">Ingresar</a>
                    <span class="divider">|</span>
                    <a href="#" class="register-link">Crear cuenta</a>
                </div>
                
                <div class="cart-wrapper">
                    <a href="#" class="cart-btn">
                        <i class="fa-solid fa-cart-shopping"></i>
                        <span class="cart-count">0</span>
                    </a>
                </div>
            </div>
            
            <button class="menu-toggle" @click="toggleMenu">
                <i class="fa-solid fa-bars"></i>
            </button>
        </div>
    </header>
</template>

<style scoped>
/* 1. FONDO OSCURO Y LUJOSO */
.main-header {
    background-color: #151515; /* Color Onyx (Casi negro) */
    color: #ffffff;
    padding: 0; /* Quitamos padding extra para que se vea compacto y fino */
    position: sticky;
    top: 0;
    z-index: 1000;
    border-bottom: 1px solid #333; /* Una línea sutil abajo */
}

.container {
    max-width: 1400px; /* Un poco más ancho para pantallas grandes */
    margin: 0 auto;
    padding: 0 30px;
}

.header-content {
    display: flex;
    justify-content: space-between;
    align-items: center;
    height: 80px; /* Altura fija elegante */
}

/* 2. TIPOGRAFÍA DEL LOGO */
.brand {
    display: flex;
    align-items: center;
    gap: 12px;
    cursor: pointer;
}

.logo-icon {
    font-size: 1.8rem;
    color: #d4af37; /* Icono Dorado */
}

.brand-name {
    font-family: 'Playfair Display', serif; /* Fuente elegante */
    font-size: 1.8rem;
    font-weight: 700; /* Negrita */
    letter-spacing: 1px;
    color: #ffffff;
}

/* 3. MENÚ DE NAVEGACIÓN */
.nav-links {
    display: flex;
    gap: 40px;
    list-style: none;
    margin: 0;
}

.nav-links a {
    font-family: 'Montserrat', sans-serif; /* Fuente limpia */
    font-size: 0.95rem;
    text-transform: uppercase; /* Mayúsculas se ven más premium */
    letter-spacing: 1px;
    color: #cccccc; /* Gris claro */
    transition: all 0.3s ease;
    font-weight: 400;
}

.nav-links a:hover {
    color: #d4af37; /* Dorado al pasar el mouse */
}

/* 4. ACCIONES DE USUARIO (SOLUCIÓN A TU PROBLEMA DE ESPACIO) */
.user-actions {
    display: flex;
    align-items: center;
    gap: 25px; /* Espacio entre login y carrito */
}

.auth-links {
    display: flex;
    align-items: center;
    gap: 10px;
    font-family: 'Montserrat', sans-serif;
    font-size: 0.85rem;
}

.divider { color: #555; }

.auth-links a {
    color: white;
    text-decoration: none;
    transition: color 0.3s;
}

.auth-links a:hover { color: #d4af37; }

.register-link {
    border: 1px solid #d4af37;
    padding: 6px 15px;
    border-radius: 20px; /* Botón redondeado */
    color: #d4af37 !important;
}

.register-link:hover {
    background-color: #d4af37;
    color: #000 !important;
}

.cart-btn {
    font-size: 1.2rem;
    color: white;
    position: relative;
}

.cart-count {
    position: absolute;
    top: -8px;
    right: -10px;
    background-color: #d4af37;
    color: #000;
    font-size: 0.7rem;
    width: 18px;
    height: 18px;
    border-radius: 50%;
    display: flex;
    justify-content: center;
    align-items: center;
    font-weight: bold;
}

.menu-toggle { display: none; } /* Oculto en escritorio */

/* RESPONSIVE (MÓVIL) */
@media (max-width: 768px) {
    .menu-toggle {
        display: block;
        background: none;
        border: none;
        color: white;
        font-size: 1.5rem;
        cursor: pointer;
    }

    .nav-links {
        display: none; /* Aquí deberías agregar lógica para abrir el menú lateral */
    }
    
    .auth-links { display: none; } /* Ocultamos login en móvil para simplificar */
}
.dropdown-wrapper {
    position: relative; /* Vital: Para que el menú hijo se posicione respecto a este padre */
    height: 100%;
    display: flex;
    align-items: center;
}

.dropdown-trigger {
    display: flex;
    align-items: center;
    gap: 8px; /* Espacio entre texto y flechita */
}

.arrow-icon {
    font-size: 0.7rem; /* Flechita pequeña y elegante */
    transition: transform 0.3s;
}

/* Girar la flecha cuando el menú está abierto */
.dropdown-wrapper:hover .arrow-icon {
    transform: rotate(180deg);
}

/* El Menú Flotante en sí */
.dropdown-menu {
    position: absolute;
    top: 40px; /* Ajusta para que aparezca justo debajo del texto */
    left: -20px; /* Un poco a la izquierda para centrar visualmente */
    background-color: #151515; /* Mismo negro Onyx del header */
    min-width: 200px;
    box-shadow: 0 10px 30px rgba(0,0,0,0.5); /* Sombra fuerte para destacar */
    border: 1px solid #333;
    border-top: 3px solid #d4af37; /* Detalle dorado arriba */
    padding: 15px 0;
    list-style: none;
    z-index: 1001;
    border-radius: 0 0 4px 4px;
}

/* Los items dentro del menú desplegable */
.dropdown-menu li {
    display: block;
}

.dropdown-menu a {
    display: block;
    padding: 10px 25px;
    color: #ccc;
    font-family: 'Montserrat', sans-serif;
    font-size: 0.9rem;
    text-transform: capitalize; /* Primera letra mayúscula */
    transition: all 0.2s;
}

.dropdown-menu a:hover {
    background-color: #222;
    color: #d4af37;
    padding-left: 30px; /* Efecto de desplazamiento a la derecha */
}

.separator {
    height: 1px;
    background-color: #333;
    margin: 5px 20px;
}

/* Animación Suave (Fade) */
.fade-enter-active,
.fade-leave-active {
    transition: opacity 0.3s ease, transform 0.3s ease;
}

.fade-enter-from,
.fade-leave-to {
    opacity: 0;
    transform: translateY(10px); /* Sube un poquito al aparecer */
}

/* --- REGLAS PREVIAS (RESUMIDAS PARA CONTEXTO) --- */
.main-header { background-color: #151515; color: white; /* ... */ }
</style>