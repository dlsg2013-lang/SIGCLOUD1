<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Infografía: OpenLayers en Web GIS</title>
    
    <!-- Carga de Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    
    <!-- Importación de la fuente 'Inter' (similar a la de Apple) -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;700;900&display=swap" rel="stylesheet">
    
    <style>
        /* Aplicar la fuente base y el fondo oscuro */
        body {
            font-family: 'Inter', sans-serif;
            background-color: #0A0A10; /* Fondo oscuro estilo programación */
            color: #E0E0E0;
            overflow-x: hidden; /* Evitar scroll horizontal */
        }

        /* Contenedor principal de cada sección "scrollytelling" */
        .section-container {
            width: 100%;
            min-height: 100vh; /* Cada sección principal ocupa al menos toda la pantalla */
            padding: 8rem 2rem; /* Espaciado generoso */
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            border-bottom: 1px solid #2a2a3a; /* Separador sutil */
        }

        /* Estilo de los "cuadros de texto" */
        .info-card {
            background-color: #11111a; /* Un poco más claro que el fondo */
            border: 1px solid #303040;
            border-radius: 1.5rem; /* Bordes muy redondeados */
            padding: 2rem;
            box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1), 0 10px 10px -5px rgba(0, 0, 0, 0.04);
            transition: all 0.3s ease;
        }

        .info-card:hover {
            border-color: #4a4a6a;
        }

        /* Clases para la animación de scroll */
        .scroll-animate {
            opacity: 0;
            transform: translateY(40px);
            transition: opacity 0.7s ease-out, transform 0.7s ease-out;
        }

        .scroll-animate.delay-1 { transition-delay: 0.1s; }
        .scroll-animate.delay-2 { transition-delay: 0.2s; }
        .scroll-animate.delay-3 { transition-delay: 0.3s; }

        .scroll-animate.is-visible {
            opacity: 1;
            transform: translateY(0);
        }

        /* Títulos estilo Apple/Programación */
        .section-title {
            font-size: 3rem; /* 48px */
            font-weight: 900;
            line-height: 1.1;
            text-align: center;
            margin-bottom: 3rem;
            color: #FFFFFF;
        }

        @media (min-width: 768px) {
            .section-title {
                font-size: 5rem; /* 80px */
            }
        }
        
        /* Acordeón para OGC */
        .accordion-content {
            max-height: 0;
            overflow: hidden;
            transition: max-height 0.5s ease-out;
        }
        
        .accordion-toggle.active .accordion-icon {
            transform: rotate(45deg);
        }
        
        /* Estilo para keywords de programación */
        .code-keyword {
            font-family: monospace;
            color: #60A5FA; /* Azul brillante */
            font-weight: 700;
        }
        
        .code-keyword-green {
            font-family: monospace;
            color: #34D399; /* Verde brillante */
            font-weight: 700;
        }

    </style>
</head>
<body class="antialiased">

    <!-- 1. SECCIÓN HERO (TÍTULO PRINCIPAL) -->
    <section class="section-container h-screen !justify-center text-center px-4">
        <h1 class="text-4xl md:text-7xl font-black text-white leading-tight">
            Aplicación de 
            <span class="bg-clip-text text-transparent bg-gradient-to-r from-blue-400 to-purple-500">
                OpenLayers
            </span>
            <br>
            en Web GIS
        </h1>
        <p class="text-xl md:text-2xl text-gray-400 mt-6 max-w-3xl mx-auto">
            Publicación de datos espaciotemporales en la web.
            <span class="block text-lg mt-4 text-gray-500">
                Capitulo 2 del libro de Tiwari, A., y Jain, K. (2017). <i>Concepts and Applications of Web GIS</i>. Nova Science Publishers, Inc.
            </span>
        </p>
        <div class="mt-16 animate-bounce">
            <svg class="w-8 h-8 text-gray-500" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 14l-7 7m0 0l-7-7m7 7V3"></path></svg>
        </div>
    </section>

    <!-- 2. RESUMEN EJECUTIVO -->
    <section class="section-container">
        <div class="max-w-4xl w-full">
            <h2 class="section-title scroll-animate">
                Resumen
            </h2>
            <p class="text-xl text-gray-400 text-center max-w-3xl mx-auto -mt-8 mb-16 scroll-animate delay-1">
                Un vistazo al flujo de conceptos que se tratarán en esta infografía.
            </p>
            
            <div class="flex flex-col items-center w-full max-w-2xl mx-auto">
                        
                <!-- Paso 1 -->
                <div class="info-card scroll-animate delay-1 w-full text-center">
                    <span class="block text-2xl font-bold text-purple-300">Punto de Partida</span>
                    <h4 class="text-xl font-bold text-white mt-2">Web GIS + <span class="code-keyword">OpenLayers</span></h4>
                    <p class="text-gray-400">Plataformas potentes para publicar, analizar y visualizar datos espaciotemporales.</p>
                </div>
                
                <svg class="w-8 h-8 text-gray-600 my-4 scroll-animate delay-1" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 14l-7 7m0 0l-7-7m7 7V3"></path></svg>
                
                <!-- Paso 2 -->
                <div class="info-card scroll-animate delay-2 w-full text-center">
                    <span class="block text-2xl font-bold text-purple-300">Conceptos Clave</span>
                    <h4 class="text-xl font-bold text-white mt-2">Arquitectura y Estándares OGC</h4>
                    <p class="text-gray-400">Se explorará la arquitectura (cliente ligero/pesado) y la interoperabilidad (<span class="code-keyword-green">WMS</span>, <span class="code-keyword-green">WFS</span>, <span class="code-keyword-green">WCS</span>).</p>
                </div>
                
                <svg class="w-8 h-8 text-gray-600 my-4 scroll-animate delay-2" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 14l-7 7m0 0l-7-7m7 7V3"></path></svg>
                
                <!-- Paso 3 -->
                <div class="info-card scroll-animate delay-3 w-full text-center">
                    <span class="block text-2xl font-bold text-purple-300">Aplicación Práctica</span>
                    <h4 class="text-xl font-bold text-white mt-2">Caso de Estudio: Himalaya (NMSHE)</h4>
                    <p class="text-gray-400">Se analizará un portal real que integra <span class="code-keyword">ArcGIS</span>, <span class="code-keyword">GeoServer</span> y <span class="code-keyword">OpenLayers</span>.</p>
                </div>

            </div>
        </div>
    </section>
    
    <!-- 3. FUNDAMENTOS DE LOS SIG -->
    <section class="section-container">
        <div class="max-w-6xl w-full">
            <h2 class="section-title scroll-animate">
                1. Fundamentos
                <span class="bg-clip-text text-transparent bg-gradient-to-r from-green-400 to-blue-400">
                    de SIG
                </span>
            </h2>
            
            <p class="text-xl text-gray-400 text-center max-w-3xl mx-auto mb-16 scroll-animate delay-1">
                Un SIG (GIS) es una aplicación informática diseñada para recopilar, almacenar, manipular, analizar y visualizar datos georreferenciados, facilitando la identificación de patrones y la toma de decisiones.
            </p>

            <!-- Principios Clave -->
            <h3 class="text-3xl md:text-4xl font-bold text-white text-center mb-10 scroll-animate">Principios Clave del SIG</h3>
            <div class="grid md:grid-cols-2 gap-8 mb-16">
                
                <div class="info-card scroll-animate delay-1">
                    <h4 class="text-2xl font-bold text-green-400 mb-4">Captura de Datos</h4>
                    <p class="text-gray-300 mb-4">Convertir datos del mundo real a formato digital. Se organizan en capas y provienen de diversas fuentes.</p>
                    <div class="grid grid-cols-2 gap-4">
                        <div class="bg-gray-950 p-4 rounded-lg border border-gray-700">
                            <b class="text-white">Datos Raster:</b>
                            <p class="text-sm text-gray-400">Cuadrícula de píxeles (temperatura, elevación).</p>
                        </div>
                        <div class="bg-gray-950 p-4 rounded-lg border border-gray-700">
                            <b class="text-white">Datos Vectoriales:</b>
                            <p class="text-sm text-gray-400">Puntos, líneas y polígonos (carreteras, edificios).</p>
                        </div>
                    </div>
                </div>
                
                <div class="info-card scroll-animate delay-2">
                    <h4 class="text-2xl font-bold text-green-400 mb-4">Gestión y Actualización</h4>
                    <p class="text-gray-300">El SGBD (DBMS) es crucial para almacenar, manipular y recuperar datos. El diseño relacional es dominante. La actualización es vital para reflejar cambios físicos (ej. un incendio).</p>
                </div>
                
                <div class="info-card scroll-animate delay-3">
                    <h4 class="text-2xl font-bold text-green-400 mb-4">Análisis Geográfico</h4>
                    <p class="text-gray-300">Abarca desde operaciones lógicas simples hasta modelos complejos para responder preguntas, analizar cambios a lo largo del tiempo o predecir tendencias futuras.</p>
                </div>

                <div class="info-card scroll-animate delay-1 md:delay-4">
                    <h4 class="text-2xl font-bold text-green-400 mb-4">Preparación de Resultados</h4>
                    <p class="text-gray-300">Presentar la información derivada en formatos comprensibles, principalmente mapas y informes tabulares. Un mapa eficaz incluye título, leyenda, flecha de norte y escala.</p>
                </div>
            </div>

            <!-- Componentes Esenciales -->
            <h3 class="text-3xl md:text-4xl font-bold text-white text-center mb-10 scroll-animate">Componentes Esenciales</h3>
            <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-5 gap-6 text-center">
                
                <div class="info-card p-6 scroll-animate delay-1">
                    <svg class="w-16 h-16 mx-auto text-blue-400" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9.75 17L9 20l-1 1h8l-1-1-.75-3M3 13h18M5 17h14a2 2 0 002-2V5a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"></path></svg>
                    <h4 class="text-xl font-bold text-white mt-4">Hardware</h4>
                    <p class="text-gray-400 text-sm">Servidores, PCs, plotters, escáneres.</p>
                </div>

                <div class="info-card p-6 scroll-animate delay-2">
                    <svg class="w-16 h-16 mx-auto text-blue-400" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 20l4-16m4 4l4 4-4 4M6 16l-4-4 4-4"></path></svg>
                    <h4 class="text-xl font-bold text-white mt-4">Software</h4>
                    <p class="text-gray-400 text-sm">Funciones para almacenar, analizar y mostrar.</p>
                </div>

                <div class="info-card p-6 scroll-animate delay-3">
                    <svg class="w-16 h-16 mx-auto text-blue-400" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 7v10c0 2.21 3.582 4 8 4s8-1.79 8-4V7M4 7c0-2.21 3.582-4 8-4s8 1.79 8 4M4 7c0 2.21 3.582 4 8 4s8-1.79 8-4"></path></svg>
                    <h4 class="text-xl font-bold text-white mt-4">Datos</h4>
                    <p class="text-gray-400 text-sm">Componente más importante; integra datos espaciales.</p>
                </div>

                <div class="info-card p-6 scroll-animate delay-1 md:delay-4">
                    <svg class="w-16 h-16 mx-auto text-blue-400" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 20h5v-2a3 3 0 00-5.356-1.857M17 20H7m10 0v-2c0-.653-.084-1.284-.24-1.857M7 20v-2c0-.653.084-1.284.24-1.857M7 20H2v-2a3 3 0 015.356-1.857M12 12a3 3 0 100-6 3 3 0 000 6z"></path></svg>
                    <h4 class="text-xl font-bold text-white mt-4">Personas</h4>
                    <p class="text-gray-400 text-sm">Gestores, especialistas y usuarios finales.</p>
                </div>
                
                <div class="info-card p-6 scroll-animate delay-2 md:delay-5 col-span-2 md:col-span-1">
                    <svg class="w-16 h-16 mx-auto text-blue-400" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5H7a2 2 0 00-2 2v12a2 2 0 002 2h10a2 2 0 002-2V7a2 2 0 00-2-2h-2M9 5a2 2 0 002-2h2a2 2 0 002 2M9 5a2 2 0 012-2h2a2 2 0 012 2m-3 7h3m-3 4h3m-6-4h.01M9 16h.01"></path></svg>
                    <h4 class="text-xl font-bold text-white mt-4">Métodos</h4>
                    <p class="text-gray-400 text-sm">Plan de implementación y reglas de negocio.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- 4. ARQUITECTURA WEB GIS -->
    <section class="section-container">
        <div class="max-w-6xl w-full">
            <h2 class="section-title scroll-animate">
                2. Arquitectura
                <span class="text-purple-400">Web GIS</span>
            </h2>
            
            <p class="text-xl text-gray-400 text-center max-w-3xl mx-auto mb-16 scroll-animate delay-1">
                Un Web GIS es un sistema de información distribuido que utiliza tecnologías web. Permite a múltiples usuarios acceder y procesar información geoespacial a través de internet sin software local costoso.
            </p>

            <!-- Arquitectura General (3 Niveles) -->
            <h3 class="text-3xl md:text-4xl font-bold text-white text-center mb-10 scroll-animate">Arquitectura General (3 Niveles)</h3>
            <div class="flex flex-col md:flex-row justify-between items-center w-full max-w-5xl mx-auto space-y-8 md:space-y-0 md:space-x-8 mb-20">
                
                <div class="text-center p-6 info-card w-full md:w-1/3 scroll-animate delay-1">
                    <svg class="w-16 h-16 mx-auto text-purple-400 mb-4" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9.75 17L9 20l-1 1h8l-1-1-.75-3M3 13h18M5 17h14a2 2 0 002-2V5a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"></path></svg>
                    <h4 class="text-2xl font-bold text-white">Nivel de Presentación</h4>
                    <p class="text-gray-400">(Cliente: Navegador, App)</p>
                </div>
                
                <svg class="w-12 h-12 text-gray-600 hidden md:block scroll-animate delay-2" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3"></path></svg>
                <svg class="w-12 h-12 text-gray-600 md:hidden scroll-animate delay-2" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M16 17l-4 4m0 0l-4-4m4 4V3"></path></svg>

                <div class="text-center p-6 info-card w-full md:w-1/3 scroll-animate delay-3">
                    <svg class="w-16 h-16 mx-auto text-purple-400 mb-4" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 12h14M5 12a2 2 0 01-2-2V6a2 2 0 012-2h14a2 2 0 012 2v4a2 2 0 01-2 2M5 12a2 2 0 00-2 2v4a2 2 0 002 2h14a2 2 0 002-2v-4a2 2 0 00-2-2"></path></svg>
                    <h4 class="text-2xl font-bold text-white">Nivel de Lógica</h4>
                    <p class="text-gray-400">(Servidor Web, Servidor GIS)</p>
                </div>
                
                <svg class="w-12 h-12 text-gray-600 hidden md:block scroll-animate delay-2" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3"></path></svg>
                <svg class="w-12 h-12 text-gray-600 md:hidden scroll-animate delay-2" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M16 17l-4 4m0 0l-4-4m4 4V3"></path></svg>

                <div class="text-center p-6 info-card w-full md:w-1/3 scroll-animate delay-1 md:delay-4">
                     <svg class="w-16 h-16 mx-auto text-purple-400 mb-4" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 7v10c0 2.21 3.582 4 8 4s8-1.79 8-4V7M4 7c0-2.21 3.582-4 8-4s8 1.79 8 4M4 7c0 2.21 3.582 4 8 4s8-1.79 8-4"></path></svg>
                    <h4 class="text-2xl font-bold text-white">Nivel de Datos</h4>
                    <p class="text-gray-400">(Base de Datos GIS)</p>
                </div>
            </div>

            <!-- Cliente Ligero vs. Pesado -->
            <h3 class="text-3xl md:text-4xl font-bold text-white text-center mb-10 scroll-animate">Cliente Ligero vs. Cliente Pesado</h3>
            <div class="info-card overflow-x-auto scroll-animate delay-1">
                <div class="grid grid-cols-3 gap-x-4 min-w-[700px] md:min-w-full">
                    <!-- Header -->
                    <div class="font-bold text-xl text-white pb-4 border-b border-gray-700">Característica</div>
                    <div class="font-bold text-xl text-blue-300 pb-4 border-b border-gray-700">Cliente Ligero (Servidor Pesado)</div>
                    <div class="font-bold text-xl text-green-300 pb-4 border-b border-gray-700">Cliente Pesado</div>

                    <!-- Fila 1 -->
                    <div class="font-semibold text-gray-300 py-4 border-b border-gray-800">Lugar del Procesamiento</div>
                    <div class="text-gray-400 py-4 border-b border-gray-800">En el servidor</div>
                    <div class="text-gray-400 py-4 border-b border-gray-800">En el cliente</div>
                    
                    <!-- Fila 2 -->
                    <div class="font-semibold text-gray-300 py-4 border-b border-gray-800">Software del Cliente</div>
                    <div class="text-gray-400 py-4 border-b border-gray-800">Navegador web estándar</div>
                    <div class="text-gray-400 py-4 border-b border-gray-800">Plug-ins, applets de Java, etc.</div>

                    <!-- Fila 3 -->
                    <div class="font-semibold text-gray-300 py-4 border-b border-gray-800">Interacción del Usuario</div>
                    <div class="text-gray-400 py-4 border-b border-gray-800">Limitada (requiere recarga)</div>
                    <div class="text-gray-400 py-4 border-b border-gray-800">Rápida e interactiva (local)</div>

                    <!-- Fila 4 -->
                    <div class="font-semibold text-gray-300 py-4 border-b border-gray-800">Datos Transferidos</div>
                    <div class="text-gray-400 py-4 border-b border-gray-800">Imágenes procesadas (raster)</div>
                    <div class="text-gray-400 py-4 border-b border-gray-800">Datos brutos (vectoriales)</div>

                    <!-- Fila 5 -->
                    <div class="font-semibold text-gray-300 py-4 border-b border-gray-800">Ancho de Banda</div>
                    <div class="text-gray-400 py-4 border-b border-gray-800">Menor presión</div>
                    <div class="text-gray-400 py-4 border-b border-gray-800">Mayor presión (datos grandes)</div>
                    
                    <!-- Fila 6 -->
                    <div class="font-semibold text-gray-300 py-4 border-b border-gray-800">Facilidad de Actualización</div>
                    <div class="text-gray-400 py-4 border-b border-gray-800">Fácil (solo en servidor)</div>
                    <div class="text-gray-400 py-4 border-b border-gray-800">Difícil (actualizar cada cliente)</div>
                </div>
            </div>
        </div>
    </section>

    <!-- 5. ESTÁNDARES OGC -->
    <section class="section-container">
        <div class="max-w-4xl w-full">
            <h2 class="section-title scroll-animate">
                3. Estándares
                <span class="bg-clip-text text-transparent bg-gradient-to-r from-orange-400 to-yellow-400">
                    OGC
                </span>
            </h2>
            
            <div class="info-card text-center mb-16 scroll-animate delay-1">
                <h3 class="text-3xl font-bold text-white mb-4">Open Geospatial Consortium</h3>
                <p class="text-xl text-gray-400">
                    Consorcio internacional que desarrolla especificaciones públicas para la interoperabilidad de SIG. Sus Servicios Web (OWS) usan <span class="code-keyword">XML</span> y <span class="code-keyword">HTTP</span> para integrar múltiples fuentes de datos.
                </p>
            </div>

            <!-- Acordeón de Servicios OGC -->
            <div class="space-y-4" id="ogc-accordion">
                
                <!-- WMS -->
                <div class="info-card scroll-animate delay-1">
                    <button class="accordion-toggle w-full flex justify-between items-center text-left">
                        <h4 class="text-2xl font-bold text-orange-400">Web Map Service (WMS)</h4>
                        <div class="accordion-icon transition-transform transform">
                            <svg class="w-8 h-8 text-gray-500" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 4v16m8-8H4"></path></svg>
                        </div>
                    </button>
                    <div class="accordion-content">
                        <p class="text-gray-300 mt-4 pt-4 border-t border-gray-700">
                            Produce mapas como imágenes (JPEG, PNG). El cliente solicita un mapa de un área específica, sistema de coordenadas y capas.
                        </p>
                        <ul class="list-disc list-inside text-gray-400 mt-4 space-y-2">
                            <li><b class="text-gray-200">GetCapabilities:</b> Devuelve XML describiendo el servicio (capas, formatos).</li>
                            <li><b class="text-gray-200">GetMap:</b> Retorna la imagen del mapa con los parámetros definidos.</li>
                            <li><b class="text-gray-200">GetFeatureInfo (Opcional):</b> Obtiene información de un punto específico.</li>
                        </ul>
                    </div>
                </div>

                <!-- WFS -->
                <div class="info-card scroll-animate delay-2">
                    <button class="accordion-toggle w-full flex justify-between items-center text-left">
                        <h4 class="text-2xl font-bold text-orange-400">Web Feature Service (WFS)</h4>
                        <div class="accordion-icon transition-transform transform">
                            <svg class="w-8 h-8 text-gray-500" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 4v16m8-8H4"></path></svg>
                        </div>
                    </button>
                    <div class="accordion-content">
                        <p class="text-gray-300 mt-4 pt-4 border-t border-gray-700">
                            A diferencia de WMS, intercambia información geográfica en formato <b class="text-white">vectorial</b> (puntos, líneas, polígonos).
                        </p>
                        <ul class="list-disc list-inside text-gray-400 mt-4 space-y-2">
                            <li>Codifica y transfiere datos en <span class="code-keyword-green">GML</span> (un subconjunto de XML).</li>
                            <li>Permite consultas espaciales y no espaciales.</li>
                            <li>Soporta la creación, actualización y eliminación de entidades geográficas.</li>
                        </ul>
                    </div>
                </div>

                <!-- WCS -->
                <div class="info-card scroll-animate delay-3">
                    <button class="accordion-toggle w-full flex justify-between items-center text-left">
                        <h4 class="text-2xl font-bold text-orange-400">Web Coverage Service (WCS)</h4>
                        <div class="accordion-icon transition-transform transform">
                            <svg class="w-8 h-8 text-gray-500" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 4v16m8-8H4"></path></svg>
                        </div>
                    </button>
                    <div class="accordion-content">
                        <p class="text-gray-300 mt-4 pt-4 border-t border-gray-700">
                            Soporta el intercambio de datos como "coberturas" (típicamente datos <b class="text-white">raster</b> o de cuadrícula).
                        </p>
                        <ul class="list-disc list-inside text-gray-400 mt-4 space-y-2">
                            <li>Mientras WMS devuelve una imagen, WCS proporciona los <b class="text-white">datos brutos</b> subyacentes.</li>
                            <li>Permite un análisis más complejo y su uso en modelos científicos.</li>
                        </ul>
                    </div>
                </div>

            </div>
        </div>
    </section>

    <!-- 6. CASO DE ESTUDIO NMSHE -->
    <section class="section-container">
        <div class="max-w-6xl w-full">
            <h2 class="section-title scroll-animate">
                4. Caso de Estudio
                <span class="bg-clip-text text-transparent bg-gradient-to-r from-teal-400 to-blue-400">
                    Portal NMSHE
                </span>
            </h2>
            
            <div class="grid md:grid-cols-2 gap-8 mb-16">
                <div class="info-card scroll-animate delay-1">
                    <h3 class="text-3xl font-bold text-white mb-4">Contexto del Proyecto</h3>
                    <p class="text-gray-300 leading-relaxed">
                        La Misión Nacional para el Mantenimiento del Ecosistema del Himalaya (<b class="text-white">NMSHE</b>) estudia la vulnerabilidad de esta región al cambio climático. El Instituto Nacional de Hidrología (NIH) evalúa el impacto sobre el agua, la nieve y el hielo. El Himalaya es susceptible, con un aumento de temperatura superior al promedio mundial, provocando el retroceso de glaciares.
                    </p>
                    <p class="text-gray-300 leading-relaxed mt-4">
                        El proyecto busca desarrollar un portal web interactivo para representar mapas (drenaje, cobertura de nieve) y mejorar su calidad mediante análisis geoespacial.
                    </p>
                </div>
                
                <div class="info-card scroll-animate delay-2">
                    <h3 class="text-3xl font-bold text-white mb-4">Flujo de Trabajo</h3>
                    <div class="flex flex-col space-y-4">
                        <div class="flex items-center space-x-4">
                            <span class="flex-shrink-0 w-10 h-10 flex items-center justify-center bg-teal-800 text-teal-200 rounded-full font-bold">1</span>
                            <p class="text-gray-300">Datos geoespaciales (mapas de drenaje, nieve) preprocesados en <span class="code-keyword">ArcMap 10.3</span>.</p>
                        </div>
                        
                        <svg class="w-6 h-6 text-gray-600 ml-2" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 14l-7 7m0 0l-7-7m7 7V3"></path></svg>
                        
                        <div class="flex items-center space-x-4">
                            <span class="flex-shrink-0 w-10 h-10 flex items-center justify-center bg-teal-800 text-teal-200 rounded-full font-bold">2</span>
                            <p class="text-gray-300">Mapas publicados en <span class="code-keyword">GeoServer</span> (servidor GIS de código abierto).</p>
                        </div>
                        
                        <svg class="w-6 h-6 text-gray-600 ml-2" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 14l-7 7m0 0l-7-7m7 7V3"></path></svg>
                        
                        <div class="flex items-center space-x-4">
                            <span class="flex-shrink-0 w-10 h-10 flex items-center justify-center bg-teal-800 text-teal-200 rounded-full font-bold">3</span>
                            <p class="text-gray-300">Mapas servidos en el sitio web de NMSHE en formato interactivo usando <span class="code-keyword-green">OpenLayers</span> y <span class="code-keyword-green">GeoExt</span> sobre <span class="code-keyword-green">OpenStreetMap</span>.</p>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Pila Tecnológica -->
            <h3 class="text-3xl md:text-4xl font-bold text-white text-center mb-10 scroll-animate">Pila Tecnológica (Software Stack)</h3>
            <div class="grid grid-cols-2 md:grid-cols-3 gap-6">
                
                <div class="info-card p-6 scroll-animate delay-1">
                    <h4 class="text-xl font-bold text-white">ArcGIS Desktop 10.3</h4>
                    <p class="text-gray-400 text-sm">Preparación y preprocesamiento de datos.</p>
                </div>
                <div class="info-card p-6 scroll-animate delay-2">
                    <h4 class="text-xl font-bold text-white">Apache Tomcat 9.0.0</h4>
                    <p class="text-gray-400 text-sm">Servidor web de código abierto (Java).</p>
                </div>
                <div class="info-card p-6 scroll-animate delay-3">
                    <h4 class="text-xl font-bold text-white">GeoServer 2.10.0</h4>
                    <p class="text-gray-400 text-sm">Servidor GIS que publica datos usando estándares OGC.</p>
                </div>
                <div class="info-card p-6 scroll-animate delay-1">
                    <h4 class="text-xl font-bold text-white text-blue-400">OpenLayers 2.13.1</h4>
                    <p class="text-gray-400 text-sm">Biblioteca JavaScript para mostrar mapas interactivos.</p>
                </div>
                <div class="info-card p-6 scroll-animate delay-2">
                    <h4 class="text-xl font-bold text-white">GeoExt 2.1.0</h4>
                    <p class="text-gray-400 text-sm">Framework JS que combina OpenLayers con ExtJS (UI).</p>
                </div>
                <div class="info-card p-6 scroll-animate delay-3">
                    <h4 class="text-xl font-bold text-white">HTML y CSS</h4>
                    <p class="text-gray-400 text-sm">Estructuración y estilo de las páginas web.</p>
                </div>
            </div>
        </div>
    </section>
    
    <!-- 7. CONCLUSIONES -->
    <section class="section-container">
        <div class="max-w-4xl w-full">
            <h2 class="section-title scroll-animate">
                5. Conclusiones y
                <span class="bg-clip-text text-transparent bg-gradient-to-r from-rose-500 to-orange-400">
                    Consideraciones
                </span>
            </h2>
            
            <p class="text-xl text-gray-400 text-center max-w-3xl mx-auto mb-16 scroll-animate delay-1">
                El desarrollo de un Web GIS es un proceso complejo que enfrenta desafíos como las innovaciones tecnológicas, la transferencia de grandes volúmenes de datos y la necesidad de atender a usuarios no especializados.
            </p>

            <div class="space-y-6">
                
                <div class="info-card p-8 scroll-animate delay-1">
                    <div class="flex items-start">
                        <svg class="flex-shrink-0 w-8 h-8 text-rose-400 mt-1 mr-4" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 10V3L4 14h7v7l9-11h-7z"></path></svg>
                        <div>
                            <h4 class="text-2xl font-bold text-white mb-2">El desarrollo es un Proceso, no un Paso</h4>
                            <p class="text-gray-300 text-lg">
                                El éxito depende de un proceso continuo, desde el análisis de requisitos hasta el mantenimiento, no solo de comprar software y hardware.
                            </p>
                        </div>
                    </div>
                </div>

                <div class="info-card p-8 scroll-animate delay-2">
                    <div class="flex items-start">
                        <svg class="flex-shrink-0 w-8 h-8 text-rose-400 mt-1 mr-4" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m5.618-4.016A11.955 11.955 0 0112 2.011A11.955 11.955 0 012.382 7.984A11.955 11.955 0 0112 21.99a11.955 11.955 0 019.618-14.006z"></path></svg>
                        <div>
                            <h4 class="text-2xl font-bold text-white mb-2">La Arquitectura depende de los Requisitos</h4>
                            <p class="text-gray-300 text-lg">
                                El análisis inicial es fundamental para definir las funciones y la arquitectura adecuada (para NMSHE, fue una arquitectura de cliente medio).
                            </p>
                        </div>
                    </div>
                </div>

                <div class="info-card p-8 scroll-animate delay-3">
                    <div class="flex items-start">
                        <svg class="flex-shrink-0 w-8 h-8 text-rose-400 mt-1 mr-4" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 7h12m0 0l-4-4m4 4l-4 4m0 6H4m0 0l4 4m-4-4l4-4"></path></svg>
                        <div>
                            <h4 class="text-2xl font-bold text-white mb-2">Requisitos Técnicos</h4>
                            <p class="text-gray-300 text-lg">
                                Es crucial seleccionar un <b class="text-white">ancho de banda de Internet elevado</b> debido a la alta tasa de transferencia de datos. El volumen de datos exige procesadores de alta capacidad en el servidor y, a veces, en el cliente.
                            </p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- FOOTER -->
    <footer class="text-center p-16 text-gray-500 leading-relaxed">
        <p class="font-semibold text-gray-400">Elaborado por</p>
        <p class="text-lg text-gray-300">David Leonardo Sanabria Garcia</p>
        <p>Maestría en Geionformacion del Territorio</p>
        <p>Escuela de Ciencias Agrícolas, Pecuarias y del Medio Ambiente</p>
    </footer>


    <script>
        // --- SCRIPT PARA ANIMACIÓN EN SCROLL ---
        document.addEventListener("DOMContentLoaded", () => {
            const animatedElements = document.querySelectorAll(".scroll-animate");

            if ("IntersectionObserver" in window) {
                const observer = new IntersectionObserver((entries, observer) => {
                    entries.forEach(entry => {
                        if (entry.isIntersecting) {
                            entry.target.classList.add("is-visible");
                            observer.unobserve(entry.target);
                        }
                    });
                }, {
                    threshold: 0.1 // Activar cuando el 10% del elemento esté visible
                });

                animatedElements.forEach(el => {
                    observer.observe(el);
                });
            } else {
                // Fallback para navegadores antiguos
                animatedElements.forEach(el => {
                    el.classList.add("is-visible");
                });
            }

            // --- SCRIPT PARA ACORDEÓN OGC ---
            const accordionToggles = document.querySelectorAll(".accordion-toggle");

            accordionToggles.forEach(button => {
                button.addEventListener("click", () => {
                    const content = button.nextElementSibling;
                    button.classList.toggle("active");

                    if (content.style.maxHeight) {
                        content.style.maxHeight = null;
                    } else {
                        content.style.maxHeight = content.scrollHeight + "px";
                    }
                });
            });
        });
    </script>

</body>
</html>
