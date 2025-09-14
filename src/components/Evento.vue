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
                <v-btn text @click="goToSection('#inicio')">Inicio</v-btn>
                <v-btn text @click="goToSection('#acerca')">Acerca</v-btn>
                <v-btn text @click="goToSection('#productos')">Productos</v-btn>
                <v-btn text @click="goToSection('#entradas')">Entradas</v-btn>
                <v-btn text @click="goToSection('#contacto')">Contacto</v-btn>
            </v-toolbar-items>

            <v-app-bar-nav-icon class="hidden-md-and-up" @click="drawer = !drawer"></v-app-bar-nav-icon>
        </v-app-bar>

        <!-- Menú para móviles -->
        <v-navigation-drawer v-model="drawer" absolute temporary right>
            <v-list nav dense>
                <v-list-item-group>
                    <v-list-item @click="goToSection('#inicio'); drawer=false">
                        <v-list-item-title>Inicio</v-list-item-title>
                    </v-list-item>
                    <v-list-item @click="goToSection('#acerca'); drawer=false">
                        <v-list-item-title>Acerca</v-list-item-title>
                    </v-list-item>
                    <v-list-item @click="goToSection('#productos'); drawer=false">
                        <v-list-item-title>Productos</v-list-item-title>
                    </v-list-item>
                    <v-list-item @click="goToSection('#entradas'); drawer=false">
                        <v-list-item-title>Entradas</v-list-item-title>
                    </v-list-item>
                    <v-list-item @click="goToSection('#contacto'); drawer=false">
                        <v-list-item-title>Contacto</v-list-item-title>
                    </v-list-item>
                </v-list-item-group>
            </v-list>
        </v-navigation-drawer>

        <!-- Contenido principal -->
        <v-main>
            <div class="site-container">
            <!-- Sección Hero (Carousel integrado) -->
            <section id="inicio" class="hero-section">
                <v-carousel height="60vh" cycle hide-delimiter-background>
                    <v-carousel-item v-for="(slide, i) in heroSlides" :key="i">
                        <v-img :src="slide.image" gradient="to bottom, rgba(0,0,0,.4), rgba(0,0,0,.6)">
                            <v-container fill-height>
                                <v-row align="center" justify="center">
                                    <v-col cols="12" class="text-center white--text">
                                        <h1 class="display-2 font-weight-bold mb-4">{{ slide.title }}</h1>
                                        <h2 class="headline mb-6">{{ slide.subtitle }}</h2>
                                        <v-btn large-xl color="accent" @click="goToSection(slide.target)">
                                            {{ slide.buttonText }}
                                            <v-icon right>mdi-arrow-right</v-icon>
                                        </v-btn>
                                    </v-col>
                                </v-row>
                            </v-container>
                        </v-img>
                    </v-carousel-item>
                </v-carousel>
            </section>
            <!-- Sección de información (Conócenos en tarjetas) -->
            <section id="acerca" class="py-12">
                <v-container>
                    <v-row class="mb-8">
                        <v-col cols="12" class="text-center">
                            <h2 class="display-1 mb-4">CONÓCENOS</h2>
                            <p class="subtitle-1 mx-auto" style="max-width:760px">ELECTRICOM INGENIERÍA S.A.S. es una empresa casanareña especializada en ingeniería eléctrica, civil y telecomunicaciones. Contamos con un equipo humano idóneo y capacitado, comprometido en ofrecer soluciones completas y confiables para el sector industrial, comercial y de la construcción.</p>
                        </v-col>
                    </v-row>

                    <!-- Brochure preview and actions -->
                    <v-row class="mb-6" justify="center">
                        <v-col cols="12" md="8" class="text-center">
                            <v-img :src="folletoAsset" max-width="720" class="mx-auto mb-4" contain></v-img>
                            <div>
                                <v-btn color="primary" class="mr-3" @click="downloadFolleto">Descargar Folleto</v-btn>
                                <v-btn color="secondary" @click="openFolleto">Ver Folleto</v-btn>
                            </div>
                        </v-col>
                    </v-row>

                    <v-row>
                        <v-col cols="12" md="4">
                            <v-card class="pa-6 text-center about-card" height="100%">
                                <v-icon x-large color="primary" class="mb-4">mdi-target</v-icon>
                                <h3 class="headline mb-3">MISIÓN</h3>
                                <p>Brindar servicios y productos innovadores que integren tecnología, calidad y eficiencia, garantizando el bienestar de nuestros clientes y colaboradores.</p>
                            </v-card>
                        </v-col>

                        <v-col cols="12" md="4">
                            <v-card class="pa-6 text-center about-card" height="100%">
                                <v-icon x-large color="primary" class="mb-4">mdi-eye</v-icon>
                                <h3 class="headline mb-3">VISIÓN</h3>
                                <p>Ser líderes en ingeniería aplicada en la Orinoquia colombiana, con proyección nacional, destacándonos por la innovación, cumplimiento y excelencia.</p>
                            </v-card>
                        </v-col>

                        <v-col cols="12" md="4">
                            <v-card class="pa-6 text-center about-card" height="100%">
                                <v-icon x-large color="primary" class="mb-4">mdi-cog-outline</v-icon>
                                <h3 class="headline mb-3">VALORES</h3>
                                <ul class="text-left" style="display:inline-block; text-align:left;">
                                    <li>Transparencia</li>
                                    <li>Responsabilidad</li>
                                    <li>Respeto</li>
                                    <li>Compromiso</li>
                                    <li>Calidad</li>
                                </ul>
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
                                <v-img :src="product.image" height="200" contain class="product-img"></v-img>
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
                                    <v-btn color="accent" large dark elevation="6" class="buy-btn" @click="openPurchase(ticket)">Comprar</v-btn>
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
                                            <v-list-item-title>30 de Noviembre, 2025</v-list-item-title>
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
                                        <v-btn icon large class="mr-2" href="https://www.facebook.com/wilson.nossagranados" target="_blank" rel="noopener">
                                            <v-icon color="#3b5998">mdi-facebook</v-icon>
                                        </v-btn>
                                        <v-btn icon large class="mr-2" href="https://x.com/Electricom" target="_blank" rel="noopener">
                                            <v-icon color="#1da1f2">mdi-twitter</v-icon>
                                        </v-btn>
                                    </div>
                                </div>
                            </v-card>
                        </v-col>
                    </v-row>
                </v-container>
            </section>
            </div>
        </v-main>

        <!-- Dialog de compra -->
        <v-dialog v-model="purchaseDialog" max-width="500">
            <v-card>
                <v-card-title class="headline">Comprar: {{ selectedTicket.type || '' }}</v-card-title>
                <v-card-text>
                    <v-form ref="purchaseForm">
                        <v-text-field v-model="purchaseForm.name" label="Nombre" required></v-text-field>
                        <v-text-field v-model="purchaseForm.email" label="Email" required></v-text-field>
                        <p>Precio: <strong>{{ selectedTicket.price }}</strong></p>
                    </v-form>
                </v-card-text>
                <v-card-actions>
                    <v-spacer></v-spacer>
                    <v-btn text @click="purchaseDialog = false">Cancelar</v-btn>
                    <v-btn color="primary" @click="confirmPurchase">Confirmar Compra</v-btn>
                </v-card-actions>
            </v-card>
        </v-dialog>

        <!-- Snackbar de confirmación -->
        <v-snackbar v-model="snackbar.show" :timeout="3000">
            {{ snackbar.text }}
            <v-btn text @click="snackbar.show = false">Cerrar</v-btn>
        </v-snackbar>

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
                        <v-btn icon large class="mr-2" href="https://www.facebook.com/wilson.nossagranados" target="_blank" rel="noopener">
                            <v-icon>mdi-facebook</v-icon>
                        </v-btn>
                        <v-btn icon large class="mr-2" href="https://x.com/Electricom" target="_blank" rel="noopener">
                            <v-icon>mdi-twitter</v-icon>
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
import termostatoImg from '@/assets/termostato.jpeg'
// import camarasIMG from '@/assets/camaras.jpeg'
import camaras2IMG from '@/assets/camaras 2.png'
// import cerraduraIMG from '@/assets/cerradura.jpeg'
// import folletoIMG from '@/assets/folleto.jpeg'
// import imterruptoIMG from '@/assets/interruptor.jpeg'
// import termostatoIMG from '@/assets/termostato.jpeg'
import entradas from '@/assets/entradas.png'
import folletoAsset from '@/assets/folleto.jpg'
import conocenos from '@/assets/conocenos.png'


export default {
    name: 'App',
    data: () => ({
        drawer: false,
        purchaseDialog: false,
        selectedTicket: {},
        purchaseForm: {
            name: '',
            email: ''
        },
        snackbar: {
            show: false,
            text: ''
        },
        heroSlides: [
            {
                title: '',
                subtitle: 'Descubre los productos innovadores del evento',
                buttonText: 'Ver Productos',
                target: '#productos',
                image: camaras2IMG
            },
            {
                title: '',
                subtitle: '',
                buttonText: 'Comprar Entradas',
                target: '#entradas',
                image: entradas
            },
            {
                title: '',
                subtitle: '',
                buttonText: 'CONOCENOS',
                target: '#acerca',
                image: conocenos
            }
        ],
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
                image: termostatoImg
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
    ,
    methods: {
        goToSection(selector) {
            const el = document.querySelector(selector);
            if (el) el.scrollIntoView({ behavior: 'smooth' });
        },
        openPurchase(ticket) {
            this.selectedTicket = ticket || {};
            this.purchaseForm = { name: '', email: '' };
            this.purchaseDialog = true;
        },
        openFolleto() {
            // Open the imported asset in a new tab
            const w = window.open(folletoAsset, '_blank');
            if (w) w.focus();
        },
        async downloadFolleto() {
            try {
                const resp = await fetch(folletoAsset);
                const blob = await resp.blob();
                const url = window.URL.createObjectURL(blob);
                const a = document.createElement('a');
                a.href = url;
                a.download = 'folleto.jpg';
                document.body.appendChild(a);
                a.click();
                a.remove();
                window.URL.revokeObjectURL(url);
            } catch (err) {
                console.error('Error descargando folleto', err);
                this.snackbar.text = 'No se pudo descargar el folleto.';
                this.snackbar.show = true;
            }
        },
        confirmPurchase() {
            if (!this.purchaseForm.name || !this.purchaseForm.email) {
                this.snackbar.text = 'Por favor complete nombre y email.';
                this.snackbar.show = true;
                return;
            }

            // Simular compra
            this.purchaseDialog = false;
            this.snackbar.text = `Compra simulada: ${this.selectedTicket.type} - ${this.selectedTicket.price}`;
            this.snackbar.show = true;

            // Aquí podríamos resetear el formulario o enviar datos a un API
            this.purchaseForm = { name: '', email: '' };
            this.selectedTicket = {};
        }
    }
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

.buy-btn {
    padding-left: 28px !important;
    padding-right: 28px !important;
    font-weight: 700 !important;
    letter-spacing: 0.5px;
    background-color: #4caf50 !important; /* verde */
    color: white !important;
    transition: transform 120ms ease, box-shadow 120ms ease;
    box-shadow: 0 6px 18px rgba(76,175,80,0.24);
}

.buy-btn:active,
.buy-btn.v-btn--active {
    transform: translateY(2px) scale(0.995);
    box-shadow: 0 4px 12px rgba(76,175,80,0.18);
}

.buy-btn:hover {
    transform: translateY(-2px) scale(1.01);
}

/* Product image styling to hide transparent backgrounds and center the image */
.product-img {
    background: white;
    padding: 12px;
    object-fit: contain;
}

.about-card {
    border-radius: 8px;
    box-shadow: 0 6px 18px rgba(16,24,40,0.06);
}

.about-card h3 {
    color: #013a63;
}

</style>

<style scoped>
.site-container {
    max-width: 1100px;
    margin: 0 auto;
    padding: 0 16px;
}

.hero-section .v-carousel {
    max-height: 60vh;
}
</style>