<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Infografía sobre la aplicación de OpenLayers en Web GIS y estándares OGC.">
    <meta name="author" content="David Leonardo Sanabria Garcia">
    <title>Infografía: OpenLayers en Web GIS</title>
    
    <script src="https://cdn.tailwindcss.com"></script>
    
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['Inter', 'sans-serif'],
                    },
                    colors: {
                        dark: '#0A0A10',
                        card: '#11111a',
                    }
                }
            }
        }
    </script>

    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;700;900&display=swap" rel="stylesheet">
    
    <style>
        /* Estilos base */
        body {
            font-family: 'Inter', sans-serif;
            background-color: #0A0A10;
            color: #E0E0E0;
            overflow-x: hidden;
            scroll-behavior: smooth;
        }

        /* Contenedor de sección scrollytelling */
        .section-container {
            width: 100%;
            min-height: 100vh;
            padding: 6rem 1.5rem;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            border-bottom: 1px solid #2a2a3a;
        }

        /* Tarjetas de información */
        .info-card {
            background-color: #11111a;
            border: 1px solid #303040;
            border-radius: 1.5rem;
            padding: 2rem;
            box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.3), 0 10px 10px -5px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s ease, border-color 0.3s ease;
        }

        .info-card:hover {
            border-color: #60A5FA;
            transform: translateY(-5px);
        }

        /* Animaciones de Scroll */
        .scroll-animate {
            opacity: 0;
            transform: translateY(40px);
            transition: opacity 0.8s cubic-bezier(0.25, 0.46, 0.45, 0.94), transform 0.8s cubic-bezier(0.25, 0.46, 0.45, 0.94);
        }

        .scroll-animate.delay-1 { transition-delay: 0.1s; }
        .scroll-animate.delay-2 { transition-delay: 0.2s; }
        .scroll-animate.delay-3 { transition-delay: 0.3s; }
        .scroll-animate.delay-4 { transition-delay: 0.4s; }
        .scroll-animate.delay-5 { transition-delay: 0.5s; }

        .scroll-animate.is-visible {
            opacity: 1;
            transform: translateY(0);
        }

        /* Títulos */
        .section-title {
            font-size: 2.5rem;
            font-weight: 900;
            line-height: 1.1;
            text-align: center;
            margin-bottom: 3rem;
            color: #FFFFFF;
        }

        @media (min-width: 768px) {
            .section-title { font-size: 4rem; }
        }
        
        @media (min-width: 1024px) {
            .section-title { font-size: 5rem; }
        }

        /* Acordeón */
        .accordion-content {
            max-height: 0;
            overflow: hidden;
            transition: max-height 0.4s ease-out;
        }
        
        .accordion-toggle.active .accordion-icon {
            transform: rotate(45deg);
        }

        /* Estilos de código */
        .code-keyword { font-family: monospace; color: #60A5FA; font-weight: 700; }
        .code-keyword-green { font-family: monospace; color: #34D399; font-weight: 700; }
        
        /* Barra de scroll personalizada */
        ::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-track {
            background: #0A0A10; 
        }
        ::-webkit-scrollbar-thumb {
            background: #333; 
            border-radius: 4px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #555; 
        }
    </style>
</head>
<body class="antialiased">

    <section class="section-container h-screen !justify-center text-center px-4 relative">
        <div class="absolute inset-0 bg-[url('https://www.transparenttextures.com/patterns/cubes.png')] opacity-5 pointer-events-none"></div>
        
        <h1 class="text-4xl md:text-7xl font-black text-white leading-tight z-10">
            Aplicación de 
            <span class="bg-clip-text text-transparent bg-gradient-to-r from-blue-400 to-purple-500">
                OpenLayers
            </span>
            <br>
            en Web GIS
        </h1>
        <p class="text-xl md:text-2xl text-gray-400 mt-6 max-w-3xl mx-auto z-10">
            Publicación de datos espaciotemporales en la web.
            <span class="block text-base md:text-lg mt-4 text-gray-500 font-light">
                Basado en el Cap. 2 de Tiwari, A., y Jain, K. (2017). <i>Concepts and Applications of Web GIS</i>.
            </span>
        </p>
        <div class="mt-16 animate-bounce z-10 cursor-pointer" onclick="document.getElementById('resumen').scrollIntoView()">
            <svg class="w-8 h-8 text-gray-500 hover:text-white transition-colors" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 14l-7 7m0 0l-7-7m7 7V3"></path></svg>
        </div>
    </section>

    <section id="resumen" class="section-container">
        <div class="max-w-4xl w-full">
            <h2 class="section-title scroll-animate">Resumen</h2>
            <p class="text-xl text-gray-400 text-center max-w-3xl mx-auto -mt-8 mb-16 scroll-animate delay-1">
                Flujo de conceptos tratados en esta infografía.
            </p>
            
            <div class="flex flex-col items-center w-full max-w-2xl mx-auto">
                <div class="info-card scroll-animate delay-1 w-full text-center hover:border-purple-500">
                    <span class="block text-2xl font-bold text-purple-400">Punto de Partida</span>
                    <h4 class="text-xl font-bold text-white mt-2">Web GIS + <span class="code-keyword">OpenLayers</span></h4>
                    <p class="text-gray-400 mt-2">Plataformas potentes para publicar y visualizar datos espaciales.</p>
                </div>
                
                <svg class="w-8 h-8 text-gray-700 my-4 scroll-animate delay-1" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 14l-7 7m0 0l-7-7m7 7V3"></path></svg>
                
                <div class="info-card scroll-animate delay-2 w-full text-center hover:border-green-500">
                    <span class="block text-2xl font-bold text-green-400">Conceptos Clave</span>
                    <h4 class="text-xl font-bold text-white mt-2">Arquitectura y Estándares OGC</h4>
                    <p class="text-gray-400 mt-2">Interoperabilidad mediante <span class="code-keyword-green">WMS</span>, <span class="code-keyword-green">WFS</span> y <span class="code-keyword-green">WCS</span>.</p>
                </div>
                
                <svg class="w-8 h-8 text-gray-700 my-4 scroll-animate delay-2" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 14l-7 7m0 0l-7-7m7 7V3"></path></svg>
                
                <div class="info-card scroll-animate delay-3 w-full text-center hover:border-teal-500">
                    <span class="block text-2xl font-bold text-teal-400">Aplicación Práctica</span>
                    <h4 class="text-xl font-bold text-white mt-2">Caso de Estudio: Himalaya (NMSHE)</h4>
                    <p class="text-gray-400 mt-2">Integración real de <span class="code-keyword">ArcGIS</span>, <span class="code-keyword">GeoServer</span> y <span class="code-keyword">OpenLayers</span>.</p>
                </div>
            </div>
        </div>
    </section>
    
    <section class="section-container">
        <div class="max-w-6xl w-full">
            <h2 class="section-title scroll-animate">
                1. Fundamentos
                <span class="bg-clip-text text-transparent bg-gradient-to-r from-green-400 to-blue-400">de SIG</span>
            </h2>
            
            <p class="text-lg md:text-xl text-gray-400 text-center max-w-3xl mx-auto mb-16 scroll-animate delay-1">
                Recopilación, almacenamiento, análisis y visualización de datos georreferenciados para la toma de decisiones.
            </p>

            <h3 class="text-2xl md:text-4xl font-bold text-white text-center mb-10 scroll-animate">Principios Clave</h3>
            <div class="grid md:grid-cols-2 gap-8 mb-16">
                
                <div class="info-card scroll-animate delay-1 group">
                    <h4 class="text-2xl font-bold text-green-400 mb-4 group-hover:text-green-300">Captura de Datos</h4>
                    <p class="text-gray-300 mb-4">Conversión del mundo real a digital organizado en capas.</p>
                    <div class="grid grid-cols-2 gap-4">
                        <div class="bg-gray-950 p-3 rounded-lg border border-gray-800">
                            <b class="text-white block mb-1">Raster</b>
                            <span class="text-xs text-gray-400">Píxeles (imágenes, elevación).</span>
                        </div>
                        <div class="bg-gray-950 p-3 rounded-lg border border-gray-800">
                            <b class="text-white block mb-1">Vectorial</b>
                            <span class="text-xs text-gray-400">Puntos, líneas, polígonos.</span>
                        </div>
                    </div>
                </div>
                
                <div class="info-card scroll-animate delay-2 group">
                    <h4 class="text-2xl font-bold text-green-400 mb-4 group-hover:text-green-300">Gestión (SGBD)</h4>
                    <p class="text-gray-300">Crucial para manipular y recuperar datos. El diseño relacional es dominante y la actualización constante refleja cambios físicos.</p>
                </div>
                
                <div class="info-card scroll-animate delay-3 group">
                    <h4 class="text-2xl font-bold text-green-400 mb-4 group-hover:text-green-300">Análisis</h4>
                    <p class="text-gray-300">Desde operaciones lógicas hasta modelos complejos para predecir tendencias futuras.</p>
                </div>

                <div class="info-card scroll-animate delay-4 group">
                    <h4 class="text-2xl font-bold text-green-400 mb-4 group-hover:text-green-300">Resultados</h4>
                    <p class="text-gray-300">Mapas e informes. Un mapa eficaz debe incluir: título, leyenda, norte y escala.</p>
                </div>
            </div>

            <h3 class="text-2xl md:text-4xl font-bold text-white text-center mb-10 scroll-animate">5 Componentes</h3>
            <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-5 gap-4 md:gap-6 text-center">
                <div class="info-card p-4 md:p-6 scroll-animate delay-1 hover:bg-blue-900/20">
                    <svg class="w-10 h-10 md:w-12 md:h-12 mx-auto text-blue-400" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9.75 17L9 20l-1 1h8l-1-1-.75-3M3 13h18M5 17h14a2 2 0 002-2V5a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"></path></svg>
                    <h4 class="font-bold text-white mt-3">Hardware</h4>
                </div>
                <div class="info-card p-4 md:p-6 scroll-animate delay-2 hover:bg-blue-900/20">
                    <svg class="w-10 h-10 md:w-12 md:h-12 mx-auto text-blue-400" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 20l4-16m4 4l4 4-4 4M6 16l-4-4 4-4"></path></svg>
                    <h4 class="font-bold text-white mt-3">Software</h4>
                </div>
                <div class="info-card p-4 md:p-6 scroll-animate delay-3 hover:bg-blue-900/20">
                    <svg class="w-10 h-10 md:w-12 md:h-12 mx-auto text-blue-400" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 7v10c0 2.21 3.582 4 8 4s8-1.79 8-4V7M4 7c0-2.21 3.582-4 8-4s8 1.79 8 4M4 7c0 2.21 3.582 4 8 4s8-1.79 8-4"></path></svg>
                    <h4 class="font-bold text-white mt-3">Datos</h4>
                </div>
                <div class="info-card p-4 md:p-6 scroll-animate delay-4 hover:bg-blue-900/20">
                    <svg class="w-10 h-10 md:w-12 md:h-12 mx-auto text-blue-400" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 20h5v-2a3 3 0 00-5.356-1.857M17 20H7m10 0v-2c0-.653-.084-1.284-.24-1.857M7 20v-2c0-.653.084-1.284.24-1.857M7 20H2v-2a3 3 0 015.356-1.857M12 12a3 3 0 100-6 3 3 0 000 6z"></path></svg>
                    <h4 class="font-bold text-white mt-3">Personas</h4>
                </div>
                <div class="info-card p-4 md:p-6 scroll-animate delay-5 hover:bg-blue-900/20 col-span-2 md:col-span-1">
                    <svg class="w-10 h-10 md:w-12 md:h-12 mx-auto text-blue-400" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5H7a2 2 0 00-2 2v12a2 2 0 002 2h10a2 2 0 002-2V7a2 2 0 00-2-2h-2M9 5a2 2 0 002-2h2a2 2 0 002 2M9 5a2 2 0 012-2h2a2 2 0 012 2m-3 7h3m-3 4h3m-6-4h.01M9 16h.01"></path></svg>
                    <h4 class="font-bold text-white mt-3">Métodos</h4>
                </div>
            </div>
        </div>
    </section>

    <section class="section-container">
        <div class="max-w-6xl w-full">
            <h2 class="section-title scroll-animate">
                2. Arquitectura <span class="text-purple-400">Web GIS</span>
            </h2>
            
            <p class="text-lg md:text-xl text-gray-400 text-center max-w-3xl mx-auto mb-16 scroll-animate delay-1">
                Sistema distribuido que permite a múltiples usuarios acceder y procesar geoinformación vía internet sin software local costoso.
            </p>

            <h3 class="text-2xl md:text-4xl font-bold text-white text-center mb-10 scroll-animate">Los 3 Niveles</h3>
            <div class="flex flex-col md:flex-row justify-between items-center w-full max-w-5xl mx-auto space-y-8 md:space-y-0 md:space-x-8 mb-20">
                
                <div class="text-center p-6 info-card w-full md:w-1/3 scroll-animate delay-1">
                    <svg class="w-12 h-12 mx-auto text-purple-400 mb-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9.75 17L9 20l-1 1h8l-1-1-.75-3M3 13h18M5 17h14a2 2 0 002-2V5a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"></path></svg>
                    <h4 class="text-xl font-bold text-white">Presentación</h4>
                    <p class="text-gray-500 text-sm mt-1">Navegador, Apps</p>
                </div>
                
                <div class="text-gray-600 scroll-animate delay-2 rotate-90 md:rotate-0">
                    <svg class="w-8 h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3"></path></svg>
                </div>

                <div class="text-center p-6 info-card w-full md:w-1/3 scroll-animate delay-3">
                    <svg class="w-12 h-12 mx-auto text-purple-400 mb-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 12h14M5 12a2 2 0 01-2-2V6a2 2 0 012-2h14a2 2 0 012 2v4a2 2 0 01-2 2M5 12a2 2 0 00-2 2v4a2 2 0 002 2h14a2 2 0 002-2v-4a2 2 0 00-2-2"></path></svg>
                    <h4 class="text-xl font-bold text-white">Lógica</h4>
                    <p class="text-gray-500 text-sm mt-1">Web Server, GIS Server</p>
                </div>
                
                <div class="text-gray-600 scroll-animate delay-2 rotate-90 md:rotate-0">
                    <svg class="w-8 h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3"></path></svg>
                </div>

                <div class="text-center p-6 info-card w-full md:w-1/3 scroll-animate delay-4">
                     <svg class="w-12 h-12 mx-auto text-purple-400 mb-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 7v10c0 2.21 3.582 4 8 4s8-1.79 8-4V7M4 7c0-2.21 3.582-4 8-4s8 1.79 8 4M4 7c0 2.21 3.582-4 8-4s8 1.79 8 4M4 7c0 2.21 3.582 4 8 4s8-1.79 8-4"></path></svg>
                    <h4 class="text-xl font-bold text-white">Datos</h4>
                    <p class="text-gray-500 text-sm mt-1">GIS Database</p>
                </div>
            </div>

            <h3 class="text-2xl md:text-4xl font-bold text-white text-center mb-10 scroll-animate">Cliente Ligero vs. Pesado</h3>
            <div class="info-card overflow-x-auto scroll-animate delay-1">
                <table class="w-full min-w-[600px] text-left border-collapse">
                    <thead>
                        <tr>
                            <th class="p-4 border-b border-gray-700 text-white font-bold text-lg">Característica</th>
                            <th class="p-4 border-b border-gray-700 text-blue-400 font-bold text-lg">Cliente Ligero</th>
                            <th class="p-4 border-b border-gray-700 text-green-400 font-bold text-lg">Cliente Pesado</th>
                        </tr>
                    </thead>
                    <tbody class="text-gray-400">
                        <tr class="hover:bg-white/5">
                            <td class="p-4 border-b border-gray-800 font-semibold text-gray-300">Procesamiento</td>
                            <td class="p-4 border-b border-gray-800">En el servidor</td>
                            <td class="p-4 border-b border-gray-800">En el cliente</td>
                        </tr>
                        <tr class="hover:bg-white/5">
                            <td class="p-4 border-b border-gray-800 font-semibold text-gray-300">Software</td>
                            <td class="p-4 border-b border-gray-800">Navegador Web</td>
                            <td class="p-4 border-b border-gray-800">Plug-ins / Applets</td>
                        </tr>
                        <tr class="hover:bg-white/5">
                            <td class="p-4 border-b border-gray-800 font-semibold text-gray-300">Interacción</td>
                            <td class="p-4 border-b border-gray-800">Limitada</td>
                            <td class="p-4 border-b border-gray-800">Rápida (Local)</td>
                        </tr>
                        <tr class="hover:bg-white/5">
                            <td class="p-4 border-b border-gray-800 font-semibold text-gray-300">Datos</td>
                            <td class="p-4 border-b border-gray-800">Imágenes (Raster)</td>
                            <td class="p-4 border-b border-gray-800">Brutos (Vector)</td>
                        </tr>
                        <tr>
                            <td class="p-4 font-semibold text-gray-300">Mantenimiento</td>
                            <td class="p-4">Fácil (Centralizado)</td>
                            <td class="p-4">Difícil (Por usuario)</td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </div>
    </section>

    <section class="section-container">
        <div class="max-w-4xl w-full">
            <h2 class="section-title scroll-animate">
                3. Estándares
                <span class="bg-clip-text text-transparent bg-gradient-to-r from-orange-400 to-yellow-400">OGC</span>
            </h2>
            
            <div class="info-card text-center mb-12 scroll-animate delay-1 bg-gradient-to-br from-[#1a1a25] to-[#11111a]">
                <h3 class="text-2xl md:text-3xl font-bold text-white mb-4">Open Geospatial Consortium</h3>
                <p class="text-lg text-gray-400">
                    Estándares públicos para la interoperabilidad. Utilizan <span class="code-keyword">XML</span> y <span class="code-keyword">HTTP</span> para integrar múltiples fuentes.
                </p>
            </div>

            <div class="space-y-4" id="ogc-accordion">
                
                <div class="info-card scroll-animate delay-1 cursor-pointer hover:border-orange-500/50 transition-colors">
                    <button class="accordion-toggle w-full flex justify-between items-center text-left focus:outline-none">
                        <h4 class="text-xl md:text-2xl font-bold text-orange-400">Web Map Service (WMS)</h4>
                        <div class="accordion-icon transition-transform transform duration-300">
                            <svg class="w-8 h-8 text-gray-500" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 4v16m8-8H4"></path></svg>
                        </div>
                    </button>
                    <div class="accordion-content">
                        <div class="mt-4 pt-4 border-t border-gray-700">
                            <p class="text-gray-300 mb-2">Devuelve <b>imágenes</b> (mapas renderizados: JPEG, PNG).</p>
                            <ul class="list-disc list-inside text-gray-400 space-y-1 text-sm md:text-base">
                                <li><b class="text-gray-200">GetCapabilities:</b> Metadatos del servicio.</li>
                                <li><b class="text-gray-200">GetMap:</b> La imagen del mapa.</li>
                                <li><b class="text-gray-200">GetFeatureInfo:</b> Datos de un punto (clic).</li>
                            </ul>
                        </div>
                    </div>
                </div>

                <div class="info-card scroll-animate delay-2 cursor-pointer hover:border-orange-500/50 transition-colors">
                    <button class="accordion-toggle w-full flex justify-between items-center text-left focus:outline-none">
                        <h4 class="text-xl md:text-2xl font-bold text-orange-400">Web Feature Service (WFS)</h4>
                        <div class="accordion-icon transition-transform transform duration-300">
                            <svg class="w-8 h-8 text-gray-500" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 4v16m8-8H4"></path></svg>
                        </div>
                    </button>
                    <div class="accordion-content">
                        <div class="mt-4 pt-4 border-t border-gray-700">
                            <p class="text-gray-300 mb-2">Devuelve objetos <b>vectoriales</b> reales (puntos, líneas).</p>
                            <ul class="list-disc list-inside text-gray-400 space-y-1 text-sm md:text-base">
                                <li>Usa <span class="code-keyword-green">GML</span> (Geography Markup Language).</li>
                                <li>Permite consultas espaciales complejas.</li>
                                <li>Permite editar datos (Transaccional).</li>
                            </ul>
                        </div>
                    </div>
                </div>

                <div class="info-card scroll-animate delay-3 cursor-pointer hover:border-orange-500/50 transition-colors">
                    <button class="accordion-toggle w-full flex justify-between items-center text-left focus:outline-none">
                        <h4 class="text-xl md:text-2xl font-bold text-orange-400">Web Coverage Service (WCS)</h4>
                        <div class="accordion-icon transition-transform transform duration-300">
                            <svg class="w-8 h-8 text-gray-500" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 4v16m8-8H4"></path></svg>
                        </div>
                    </button>
                    <div class="accordion-content">
                        <div class="mt-4 pt-4 border-t border-gray-700">
                            <p class="text-gray-300 mb-2">Devuelve datos <b>crudos</b> de coberturas (Raster/Grid).</p>
                            <ul class="list-disc list-inside text-gray-400 space-y-1 text-sm md:text-base">
                                <li>A diferencia de WMS (imagen), WCS da los valores reales de los píxeles.</li>
                                <li>Ideal para análisis científico y modelos.</li>
                            </ul>
                        </div>
                    </div>
                </div>

            </div>
        </div>
    </section>

    <section class="section-container">
        <div class="max-w-6xl w-full">
            <h2 class="section-title scroll-animate">
                4. Caso de Estudio
                <span class="bg-clip-text text-transparent bg-gradient-to-r from-teal-400 to-blue-400">NMSHE</span>
            </h2>
            
            <div class="grid md:grid-cols-2 gap-8 mb-16">
                <div class="info-card scroll-animate delay-1">
                    <h3 class="text-2xl font-bold text-white mb-4">Ecosistema del Himalaya</h3>
                    <p class="text-gray-300 leading-relaxed mb-4">
                        La Misión Nacional para el Mantenimiento del Ecosistema del Himalaya (<b class="text-teal-400">NMSHE</b>) estudia la vulnerabilidad climática de la región.
                    </p>
                    <p class="text-gray-400 text-sm">
                        El aumento de temperatura provoca el retroceso de glaciares. El proyecto desarrolló un portal para evaluar el impacto sobre el agua y la nieve usando análisis geoespacial web.
                    </p>
                </div>
                
                <div class="info-card scroll-animate delay-2">
                    <h3 class="text-2xl font-bold text-white mb-4">Flujo de Trabajo</h3>
                    <div class="space-y-4">
                        <div class="flex items-start">
                            <div class="flex-shrink-0 w-8 h-8 flex items-center justify-center bg-teal-900 text-teal-300 rounded-full font-bold text-sm">1</div>
                            <p class="ml-3 text-gray-300 text-sm"><b class="text-white">ArcMap:</b> Preprocesamiento de mapas de drenaje y nieve.</p>
                        </div>
                        <div class="flex items-start">
                            <div class="flex-shrink-0 w-8 h-8 flex items-center justify-center bg-teal-900 text-teal-300 rounded-full font-bold text-sm">2</div>
                            <p class="ml-3 text-gray-300 text-sm"><b class="text-white">GeoServer:</b> Publicación de mapas mediante estándares OGC.</p>
                        </div>
                        <div class="flex items-start">
                            <div class="flex-shrink-0 w-8 h-8 flex items-center justify-center bg-teal-900 text-teal-300 rounded-full font-bold text-sm">3</div>
                            <p class="ml-3 text-gray-300 text-sm"><b class="text-white">OpenLayers:</b> Visualización interactiva en el cliente web.</p>
                        </div>
                    </div>
                </div>
            </div>

            <h3 class="text-2xl md:text-3xl font-bold text-white text-center mb-10 scroll-animate">Software Stack</h3>
            <div class="grid grid-cols-2 md:grid-cols-3 gap-4">
                <div class="info-card p-4 text-center scroll-animate delay-1">
                    <div class="text-teal-400 font-bold mb-1">ArcGIS 10.3</div>
                    <div class="text-xs text-gray-500">Preparación de datos</div>
                </div>
                <div class="info-card p-4 text-center scroll-animate delay-2">
                    <div class="text-teal-400 font-bold mb-1">Apache Tomcat</div>
                    <div class="text-xs text-gray-500">Servidor Web (Java)</div>
                </div>
                <div class="info-card p-4 text-center scroll-animate delay-3">
                    <div class="text-teal-400 font-bold mb-1">GeoServer</div>
                    <div class="text-xs text-gray-500">Servidor GIS (OGC)</div>
                </div>
                <div class="info-card p-4 text-center scroll-animate delay-1 md:delay-4 border-blue-500/50 bg-blue-900/10">
                    <div class="text-blue-400 font-bold mb-1">OpenLayers</div>
                    <div class="text-xs text-gray-500">Librería Cliente JS</div>
                </div>
                <div class="info-card p-4 text-center scroll-animate delay-2 md:delay-5">
                    <div class="text-teal-400 font-bold mb-1">GeoExt</div>
                    <div class="text-xs text-gray-500">UI Framework</div>
                </div>
                <div class="info-card p-4 text-center scroll-animate delay-3 md:delay-6">
                    <div class="text-teal-400 font-bold mb-1">PostgreSQL</div>
                    <div class="text-xs text-gray-500">Base de datos (Opcional)</div>
                </div>
            </div>
        </div>
    </section>
    
    <section class="section-container">
        <div class="max-w-4xl w-full">
            <h2 class="section-title scroll-animate">
                5. Conclusiones
            </h2>
            
            <div class="grid gap-6">
                <div class="info-card p-6 md:p-8 scroll-animate delay-1 border-l-4 border-l-rose-500">
                    <h4 class="text-xl font-bold text-white mb-2">Desarrollo como Proceso</h4>
                    <p class="text-gray-300">
                        No es solo comprar hardware; requiere un ciclo continuo desde los requisitos hasta el mantenimiento.
                    </p>
                </div>

                <div class="info-card p-6 md:p-8 scroll-animate delay-2 border-l-4 border-l-rose-500">
                    <h4 class="text-xl font-bold text-white mb-2">Arquitectura vs Requisitos</h4>
                    <p class="text-gray-300">
                        Para el caso NMSHE, una arquitectura de cliente medio fue la ideal para balancear interactividad y carga.
                    </p>
                </div>

                <div class="info-card p-6 md:p-8 scroll-animate delay-3 border-l-4 border-l-rose-500">
                    <h4 class="text-xl font-bold text-white mb-2">Desafíos Técnicos</h4>
                    <p class="text-gray-300">
                        La transferencia de datos geoespaciales exige un <b>ancho de banda elevado</b> y servidores robustos.
                    </p>
                </div>
            </div>
        </div>
    </section>

    <footer class="text-center py-20 px-4 text-gray-500 border-t border-gray-900">
        <div class="max-w-2xl mx-auto">
            <p class="text-sm font-semibold text-gray-400 mb-2 uppercase tracking-widest">Elaborado por</p>
            <p class="text-2xl text-white font-bold mb-1">David Leonardo Sanabria Garcia</p>
            <p class="text-gray-400 mb-4">Maestría en Geoinformación del Territorio</p>
            <p class="text-xs text-gray-600">Escuela de Ciencias Agrícolas, Pecuarias y del Medio Ambiente</p>
        </div>
    </footer>


    <script>
        // --- SCRIPT PARA ANIMACIÓN EN SCROLL ---
        document.addEventListener("DOMContentLoaded", () => {
            const animatedElements = document.querySelectorAll(".scroll-animate");

            if ("IntersectionObserver" in window) {
                const observer = new IntersectionObserver((entries, obs) => {
                    entries.forEach(entry => {
                        if (entry.isIntersecting) {
                            entry.target.classList.add("is-visible");
                            obs.unobserve(entry.target);
                        }
                    });
                }, { threshold: 0.1 });

                animatedElements.forEach(el => observer.observe(el));
            } else {
                // Fallback para navegadores antiguos
                animatedElements.forEach(el => el.classList.add("is-visible"));
            }

            // --- SCRIPT PARA ACORDEÓN ---
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
