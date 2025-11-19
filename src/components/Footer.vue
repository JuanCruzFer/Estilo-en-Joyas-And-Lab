<script setup>
// Podrías tener props para los enlaces de redes sociales, etc.
</script>

<template>
    <footer class="main-footer">
        <div class="container footer-content">
        <div class="footer-section about">
            <h3>Sobre Nosotros</h3>
            <p>En Estilo en Joyas, nos dedicamos a resaltar tu belleza con piezas únicas y atemporales. Calidad y diseño en cada detalle.</p>
        </div>

        <div class="footer-section contact">
            <h3>Contáctanos</h3>
            <p>¿Tienes dudas? Escríbenos:</p>
            <div class="social-icons">
            <a href="#" class="social-link instagram">
                <i class="fa-brands fa-instagram"></i>
            </a>
            <a href="#" class="social-link whatsapp">
                <i class="fa-brands fa-whatsapp"></i>
            </a>
            </div>
        </div>
        </div>
        <div class="footer-bottom">
        <p>&copy; 2023 Estilo en Joyas. Todos los derechos reservados.</p>
        </div>
    </footer>
</template>

<style scoped>
/* Contenedor principal */
.container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 20px;
}

/* FOOTER */
.main-footer {
    background-color: var(--primary-color);
    color: #ccc;
    padding: 50px 0 20px;
}

.footer-content {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    gap: 40px;
    margin-bottom: 40px;
}

.footer-section {
    flex: 1;
    min-width: 300px; /* Asegura que no se achique demasiado */
}

.footer-section h3 {
    color: var(--white);
    font-family: var(--font-serif);
    margin-bottom: 15px;
    border-bottom: 1px solid var(--accent-color);
    display: inline-block;
    padding-bottom: 5px;
}

.social-icons {
    margin-top: 15px;
    display: flex;
    gap: 15px;
}

.social-link {
    font-size: 1.8rem;
    color: var(--white);
    transition: color 0.3s;
}

.social-link.instagram:hover { color: #E1306C; } /* Color de Instagram */
.social-link.whatsapp:hover { color: #25D366; } /* Color de WhatsApp */

.footer-bottom {
    text-align: center;
    border-top: 1px solid #333;
    padding-top: 20px;
    font-size: 0.9rem;
}

/* RESPONSIVE MEDIA QUERY para el footer */
@media (max-width: 768px) {
    .footer-content {
        flex-direction: column;
        align-items: center; /* Centra los bloques en mobile */
        text-align: center;
    }
    .footer-section {
        min-width: unset; /* Quita el min-width para mobile */
        width: 100%;
    }
    .footer-section h3 {
        display: block; /* Para centrar el borde inferior si es un solo texto */
        margin: 0 auto 15px auto;
    }
    .social-icons {
        justify-content: center; /* Centra los iconos */
    }
}
</style>