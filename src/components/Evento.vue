<template>
    <v-app>
        <!-- Barra de navegación -->
        <v-app-bar app color="primary" dark>
            <v-toolbar-title class="headline">
                <v-icon large left>mdi-home-automation</v-icon>
                Conexión Inteligente
            </v-toolbar-title>

            <v-spacer></v-spacer>

            <v-toolbar-items class="hidden-sm-and-down">
                <v-btn text to="#inicio">Inicio</v-btn>
                <v-btn text to="#acerca">Acerca</v-btn>
                <v-btn text to="#productos">Productos</v-btn>
                <v-btn text to="#entradas">Entradas</v-btn>
                <v-btn text to="#contacto">Contacto</v-btn>
            </v-toolbar-items>

            <v-app-bar-nav-icon class="hidden-md-and-up" @click="drawer = !drawer"></v-app-bar-nav-icon>
        </v-app-bar>

        <!-- Menú para móviles -->
        <v-navigation-drawer v-model="drawer" absolute temporary right>
            <v-list nav dense>
                <v-list-item-group>
                    <v-list-item to="#inicio">
                        <v-list-item-title>Inicio</v-list-item-title>
                    </v-list-item>
                    <v-list-item to="#acerca">
                        <v-list-item-title>Acerca</v-list-item-title>
                    </v-list-item>
                    <v-list-item to="#productos">
                        <v-list-item-title>Productos</v-list-item-title>
                    </v-list-item>
                    <v-list-item to="#entradas">
                        <v-list-item-title>Entradas</v-list-item-title>
                    </v-list-item>
                    <v-list-item to="#contacto">
                        <v-list-item-title>Contacto</v-list-item-title>
                    </v-list-item>
                </v-list-item-group>
            </v-list>
        </v-navigation-drawer>

        <!-- Contenido principal -->
        <v-main>
            <!-- Sección Hero -->
            <section id="inicio" class="hero-section">
                <v-parallax src="https://cdn.vuetifyjs.com/images/parallax/material2.jpg" height="600">
                    <v-row align="center" justify="center">
                        <v-col class="text-center" cols="12">
                            <h1 class="display-2 font-weight-bold mb-4">Conexión Inteligente</h1>
                            <h2 class="headline mb-6">Domótica y Hogares del Futuro</h2>
                            <v-btn large color="accent" class="mt-6" to="#entradas">
                                Comprar Entradas
                                <v-icon right>mdi-arrow-right</v-icon>
                            </v-btn>
                        </v-col>
                    </v-row>
                </v-parallax>
            </section>

            <!-- Sección de información -->
            <section id="acerca" class="py-12">
                <v-container>
                    <v-row>
                        <v-col cols="12" class="text-center">
                            <h2 class="display-1 mb-6">Acerca del Evento</h2>
                            <p class="subtitle-1 mb-8">
                                Un evento único donde explorarás las últimas tendencias en domótica y automatización del
                                hogar.
                                Conoce productos innovadores, asiste a charlas técnicas y establece conexiones valiosas.
                            </p>
                        </v-col>
                    </v-row>

                    <v-row>
                        <v-col v-for="(feature, i) in features" :key="i" cols="12" md="4">
                            <v-card class="pa-6 text-center" height="100%">
                                <v-icon x-large color="primary" class="mb-4">{{ feature.icon }}</v-icon>
                                <h3 class="headline mb-3">{{ feature.title }}</h3>
                                <p>{{ feature.text }}</p>
                            </v-card>
                        </v-col>
                    </v-row>
                </v-container>
            </section>

            <!-- Sección de productos -->
            <section id="productos" class="py-12 grey lighten-4">
                <v-container>
                    <v-row>
                        <v-col cols="12" class="text-center">
                            <h2 class="display-1 mb-6">Productos Destacados</h2>
                            <p class="subtitle-1 mb-8">Descubre los productos innovadores que estarán presentes en el
                                evento</p>
                        </v-col>
                    </v-row>

                    <v-row>
                        <v-col v-for="(product, i) in products" :key="i" cols="12" sm="6" md="4">
                            <v-card class="mx-auto" max-width="350">
                                <v-img :src="product.image" height="200"></v-img>
                                <v-card-title>{{ product.name }}</v-card-title>
                                <v-card-text>
                                    <p>{{ product.description }}</p>
                                    <div class="d-flex align-center mt-4">
                                        <v-rating :value="product.rating" color="amber" dense half-increments readonly
                                            size="14"></v-rating>
                                        <span class="grey--text ml-2">({{ product.reviews }})</span>
                                    </div>
                                </v-card-text>
                                <v-card-actions>
                                    <v-btn color="primary" text>Más información</v-btn>
                                    <v-spacer></v-spacer>
                                    <span class="title font-weight-bold primary--text">{{ product.price }}</span>
                                </v-card-actions>
                            </v-card>
                        </v-col>
                    </v-row>
                </v-container>
            </section>

            <!-- Sección de entradas -->
            <section id="entradas" class="py-12">
                <v-container>
                    <v-row>
                        <v-col cols="12" class="text-center">
                            <h2 class="display-1 mb-6">Adquiere tus Entradas</h2>
                            <p class="subtitle-1 mb-8">Selecciona el tipo de entrada que mejor se adapte a tus
                                necesidades</p>
                        </v-col>
                    </v-row>

                    <v-row>
                        <v-col v-for="(ticket, i) in tickets" :key="i" cols="12" md="4">
                            <v-card :class="['pa-4', 'text-center', { 'recommended': ticket.recommended }]"
                                height="100%">
                                <v-card-title class="justify-center headline">{{ ticket.type }}</v-card-title>
                                <v-card-text>
                                    <div class="display-1 font-weight-black primary--text my-4">{{ ticket.price }}</div>
                                    <v-list dense>
                                        <v-list-item v-for="(feature, j) in ticket.features" :key="j">
                                            <v-list-item-icon>
                                                <v-icon color="primary">mdi-check</v-icon>
                                            </v-list-item-icon>
                                            <v-list-item-content>
                                                <v-list-item-title>{{ feature }}</v-list-item-title>
                                            </v-list-item-content>
                                        </v-list-item>
                                    </v-list>
                                </v-card-text>
                                <v-card-actions class="justify-center">
                                    <v-btn color="primary" large>Seleccionar</v-btn>
                                </v-card-actions>
                            </v-card>
                        </v-col>
                    </v-row>
                </v-container>
            </section>

            <!-- Sección de contacto -->
            <section id="contacto" class="py-12 grey lighten-4">
                <v-container>
                    <v-row>
                        <v-col cols="12" class="text-center">
                            <h2 class="display-1 mb-6">Contacto</h2>
                            <p class="subtitle-1 mb-8">¿Tienes preguntas? Estamos aquí para ayudarte</p>
                        </v-col>
                    </v-row>

                    <v-row>
                        <v-col cols="12" md="6">
                            <v-card class="pa-6">
                                <h3 class="headline mb-4">Envíanos un mensaje</h3>
                                <v-form>
                                    <v-text-field label="Nombre" outlined></v-text-field>
                                    <v-text-field label="Email" outlined></v-text-field>
                                    <v-textarea label="Mensaje" outlined></v-textarea>
                                    <v-btn color="primary" large>Enviar</v-btn>
                                </v-form>
                            </v-card>
                        </v-col>
                        <v-col cols="12" md="6">
                            <v-card class="pa-6" height="100%">
                                <h3 class="headline mb-4">Información del evento</h3>
                                <v-list>
                                    <v-list-item>
                                        <v-list-item-icon>
                                            <v-icon color="primary">mdi-calendar</v-icon>
                                        </v-list-item-icon>
                                        <v-list-item-content>
                                            <v-list-item-title>15 de Noviembre, 2025</v-list-item-title>
                                        </v-list-item-content>
                                    </v-list-item>
                                    <v-list-item>
                                        <v-list-item-icon>
                                            <v-icon color="primary">mdi-map-marker</v-icon>
                                        </v-list-item-icon>
                                        <v-list-item-content>
                                            <v-list-item-title>Centro de Convenciones Casa Inteligente,
                                                Yopal</v-list-item-title>
                                        </v-list-item-content>
                                    </v-list-item>
                                    <v-list-item>
                                        <v-list-item-icon>
                                            <v-icon color="primary">mdi-clock</v-icon>
                                        </v-list-item-icon>
                                        <v-list-item-content>
                                            <v-list-item-title>8:00 AM - 5:00 PM</v-list-item-title>
                                        </v-list-item-content>
                                    </v-list-item>
                                </v-list>

                                <div class="mt-8">
                                    <h4 class="title mb-3">Síguenos en redes sociales</h4>
                                    <div>
                                        <v-btn icon large class="mr-2">
                                            <v-icon color="#3b5998">mdi-facebook</v-icon>
                                        </v-btn>
                                        <v-btn icon large class="mr-2">
                                            <v-icon color="#1da1f2">mdi-twitter</v-icon>
                                        </v-btn>
                                        <v-btn icon large class="mr-2">
                                            <v-icon color="#0077b5">mdi-linkedin</v-icon>
                                        </v-btn>
                                        <v-btn icon large>
                                            <v-icon color="#e4405f">mdi-instagram</v-icon>
                                        </v-btn>
                                    </div>
                                </div>
                            </v-card>
                        </v-col>
                    </v-row>
                </v-container>
            </section>
        </v-main>

        <!-- Pie de página -->
        <v-footer color="primary" dark>
            <v-container>
                <v-row>
                    <v-col cols="12" md="6" class="text-center text-md-left">
                        <h3 class="headline mb-4">Conexión Inteligente</h3>
                        <p>Domótica y Hogares del Futuro</p>
                        <p>Organizado por ELECTRICOM INGENIERÍA S.A.S</p>
                    </v-col>
                    <v-col cols="12" md="6" class="text-center text-md-right">
                        <v-btn icon large class="mr-2">
                            <v-icon>mdi-facebook</v-icon>
                        </v-btn>
                        <v-btn icon large class="mr-2">
                            <v-icon>mdi-twitter</v-icon>
                        </v-btn>
                        <v-btn icon large class="mr-2">
                            <v-icon>mdi-linkedin</v-icon>
                        </v-btn>
                        <v-btn icon large>
                            <v-icon>mdi-instagram</v-icon>
                        </v-btn>
                    </v-col>
                </v-row>
                <v-divider class="my-4"></v-divider>
                <div class="text-center">
                    &copy; 2025 ELECTRICOM INGENIERÍA S.A.S - Todos los derechos reservados
                </div>
            </v-container>
        </v-footer>
    </v-app>
</template>

<script>
export default {
    name: 'App',
    data: () => ({
        drawer: false,
        features: [
            {
                icon: 'mdi-microphone',
                title: 'Charlas Técnicas',
                text: 'Expertos del sector compartirán sus conocimientos sobre las últimas tendencias en domótica.'
            },
            {
                icon: 'mdi-handshake',
                title: 'Networking',
                text: 'Conecta con profesionales y empresas líderes en el sector de automatización del hogar.'
            },
            {
                icon: 'mdi-eye',
                title: 'Demostraciones',
                text: 'Prueba en vivo los dispositivos más innovadores del mercado de la domótica.'
            }
        ],
        products: [
            {
                name: 'Interruptores WiFi',
                description: 'Controla las luces de tu hogar desde cualquier lugar a través de tu smartphone.',
                price: '$89.900',
                rating: 4.5,
                reviews: 128,
                image: 'https://cdn.vuetifyjs.com/images/cards/house.jpg'
            },
            {
                name: 'Termostatos Inteligentes',
                description: 'Regula la temperatura de tu hogar automáticamente y ahorra energía.',
                price: '$219.900',
                rating: 4.7,
                reviews: 95,
                image: 'https://cdn.vuetifyjs.com/images/cards/office.jpg'
            },
            {
                name: 'Cámaras de Seguridad',
                description: 'Vigila tu hogar en tiempo real con visión nocturna y detección de movimiento.',
                price: '$159.900',
                rating: 4.3,
                reviews: 204,
                image: 'https://cdn.vuetifyjs.com/images/cards/road.jpg'
            }
        ],
        tickets: [
            {
                type: 'Entrada General',
                price: '$120.000',
                recommended: false,
                features: [
                    'Acceso a todas las charlas técnicas',
                    'Zona de demostraciones',
                    'Material informativo',
                    'Coffee break'
                ]
            },
            {
                type: 'Entrada Premium',
                price: '$200.000',
                recommended: true,
                features: [
                    'Todos los beneficios de Entrada General',
                    'Acceso a zona VIP de networking',
                    'Kit de bienvenida premium',
                    'Almuerzo incluido',
                    'Estacionamiento gratuito'
                ]
            },
            {
                type: 'Entrada Estudiantil',
                price: '$80.000',
                recommended: false,
                features: [
                    'Acceso a todas las charlas técnicas',
                    'Zona de demostraciones',
                    'Material informativo',
                    'Descuento especial para estudiantes'
                ]
            }
        ]
    })
};
</script>

<style>
.hero-section {
    position: relative;
    scroll-margin-top: 80px; /* Ajusta este valor según la altura de tu barra de navegación */
}

.recommended {
    position: relative;
    overflow: hidden;
    border: 2px solid #1976d2 !important;
}

.recommended::before {
    content: 'RECOMENDADO';
    position: absolute;
    top: 15px;
    right: -30px;
    background: #ff5252;
    color: white;
    padding: 5px 30px;
    font-size: 12px;
    font-weight: bold;
    transform: rotate(45deg);
    z-index: 1;
}
</style>