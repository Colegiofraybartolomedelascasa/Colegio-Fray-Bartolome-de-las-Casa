<!DOCTYPE html>
<html lang="es">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MultiÁrea Digital 2.0</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        /* Estilos globales y de diseño mejorado */
        * {
            box-sizing: border-box;
            -webkit-font-smoothing: antialiased;
            -moz-osx-font-smoothing: grayscale;
        }

        body {
            font-family: 'Poppins', sans-serif;
            margin: 0;
            padding: 0;
            background: linear-gradient(180deg, #0a0a1a 0%, #0d0d2b 100%);
            color: #fff;
            text-align: center;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            overflow-x: hidden;
        }

        .main-container {
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 20px 20px;
            max-width: 900px;
            width: 100%;
            margin: auto;
            justify-content: center;
        }

        .header-main {
            width: 100%;
            background: linear-gradient(90deg, #2a5298, #1e3c72);
            color: #fff;
            padding: 20px;
            border-radius: 15px;
            margin-bottom: 20px;
            box-shadow: 0 4px 15px rgba(30, 60, 114, 0.4);
            display: flex;
            justify-content: center;
            align-items: center;
            flex-direction: column;
        }

        .header-main h1 {
            font-size: 2rem;
            margin: 0;
            font-weight: 700;
        }

        .header-main p {
            font-size: 1rem;
            margin: 5px 0 0;
            color: #b0b0b0;
        }

        .tab-menu {
            display: flex;
            justify-content: center;
            gap: 10px;
            margin-bottom: 20px;
            width: 100%;
        }

        .tab-button {
            background-color: #333;
            color: #fff;
            border: none;
            padding: 12px 20px;
            border-radius: 8px;
            cursor: pointer;
            transition: background-color 0.3s ease, transform 0.2s;
            font-size: 1rem;
            font-weight: 600;
        }

        .tab-button:hover {
            background-color: #555;
            transform: translateY(-2px);
        }

        .tab-button.active {
            background-color: #1e90ff;
            box-shadow: 0 4px 10px rgba(30, 144, 255, 0.5);
        }

        /* Estilos para secciones de contenido */
        .content-section {
            display: none;
            padding: 20px;
            max-width: 900px;
            margin: 20px auto;
            text-align: left;
            width: 100%;
        }

        .content-section.active {
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        .content-section h1,
        .content-section h2 {
            font-size: 2.5rem;
            margin-bottom: 20px;
            color: #f0f0f0;
            text-align: center;
        }

        .authors {
            font-size: 1rem;
            margin-top: 10px;
            color: rgba(255, 255, 255, 0.8);
            text-align: center;
            margin-bottom: 30px;
        }

        #result {
            margin-top: 25px;
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            padding: 15px;
            border-radius: 10px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
            text-align: left;
            width: 100%;
        }

        .animal-info {
            font-weight: bold;
            background: rgba(255, 255, 255, 0.8);
            padding: 4px 8px;
            border-radius: 4px;
            display: inline-block;
            color: #000;
        }

        .animal-image {
            max-width: 100%;
            max-height: 300px;
            margin-top: 10px;
            border-radius: 8px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
        }

        .info-card {
            background: rgba(255, 255, 255, 0.15);
            padding: 12px;
            border-radius: 8px;
            margin: 8px 0;
        }

        .info-title {
            font-weight: bold;
            margin-bottom: 5px;
            color: #fff;
            font-size: 1rem;
        }

        .taxonomy-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
            gap: 8px;
            margin-top: 8px;
        }

        .taxonomy-item {
            background: rgba(255, 255, 255, 0.1);
            padding: 6px;
            border-radius: 4px;
            font-size: 0.85rem;
            text-align: center;
        }

        .search-container {
            margin: 20px auto;
            max-width: 500px;
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 10px;
            width: 100%;
        }

        #animalSearch {
            padding: 12px 20px;
            width: 100%;
            border-radius: 25px;
            border: none;
            font-size: 1rem;
            outline: none;
            background: rgba(255, 255, 255, 0.9);
            color: #333;
        }

        #searchButton {
            padding: 12px 25px;
            background: #FF9800;
            color: white;
            border-radius: 25px;
            cursor: pointer;
            border: none;
            transition: all 0.3s;
        }

        #searchButton:hover {
            background: #F57C00;
            transform: translateY(-2px);
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
        }

        .search-results {
            margin-top: 15px;
            text-align: left;
            width: 100%;
            max-width: 500px;
        }

        .search-item {
            padding: 10px 15px;
            margin: 5px 0;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.2s;
        }

        .search-item:hover {
            background: rgba(255, 255, 255, 0.2);
        }

        /* Estilos para el explorador espacial */
        .space-header {
            padding: 30px 20px;
            background: rgba(18, 18, 51, 0.8);
            border-radius: 20px;
            margin-bottom: 30px;
            box-shadow: 0 0 25px rgba(0, 243, 255, 0.4);
            border: 1px solid #00f3ff;
            backdrop-filter: blur(10px);
            position: relative;
            overflow: hidden;
            width: 100%;
            max-width: 800px;
        }

        .space-header h2 {
            color: #00f3ff;
            text-shadow: 0 0 10px #00f3ff, 0 0 20px #00f3ff;
            margin-bottom: 10px;
            font-size: 2.5rem;
            letter-spacing: 2px;
        }

        .space-subtitle {
            color: #00f3ff;
            font-size: 1.2rem;
            margin-bottom: 15px;
        }

        .solar-system {
            position: relative;
            width: 100%;
            max-width: 800px;
            height: 300px;
            margin: 40px auto;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .sun {
            position: absolute;
            width: 80px;
            height: 80px;
            background: radial-gradient(circle, #ffd700, #ff8c00, #ff4500);
            border-radius: 50%;
            box-shadow: 0 0 50px #ff4500, 0 0 100px #ff8c00;
            z-index: 10;
            animation: pulse 4s infinite alternate;
        }

        @keyframes pulse {
            0% {
                transform: scale(1);
                box-shadow: 0 0 50px #ff4500, 0 0 100px #ff8c00;
            }

            100% {
                transform: scale(1.1);
                box-shadow: 0 0 70px #ff4500, 0 0 120px #ff8c00;
            }
        }

        .orbit {
            position: absolute;
            border: 1px solid rgba(0, 243, 255, 0.3);
            border-radius: 50%;
        }

        .planet-space {
            position: absolute;
            border-radius: 50%;
            transform-origin: center;
            animation: orbit linear infinite;
            cursor: pointer;
            transition: all 0.3s;
        }

        .planet-space:hover {
            transform: scale(1.5);
            z-index: 20;
        }

        .planetas-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
            margin-top: 40px;
            width: 100%;
            max-width: 1000px;
            margin: 0 auto;
        }

        .planeta-btn {
            padding: 20px 15px;
            border: none;
            background: linear-gradient(145deg, rgba(18, 18, 51, 0.8), rgba(10, 10, 35, 0.8));
            color: white;
            border-radius: 15px;
            font-size: 16px;
            cursor: pointer;
            transition: all 0.3s;
            box-shadow: 0 6px 12px rgba(0, 191, 255, 0.4);
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            min-height: 130px;
            position: relative;
            overflow: hidden;
            backdrop-filter: blur(5px);
            border: 1px solid rgba(0, 243, 255, 0.3);
        }

        .planeta-btn:hover {
            transform: translateY(-8px) scale(1.05);
            box-shadow: 0 12px 20px rgba(0, 191, 255, 0.6);
        }

        .planet-icon {
            width: 60px;
            height: 60px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-bottom: 12px;
            font-size: 30px;
            background: rgba(0, 0, 0, 0.2);
            box-shadow: 0 0 15px currentColor;
            transition: all 0.3s;
        }

        .planeta-btn:hover .planet-icon {
            transform: scale(1.2) rotate(10deg);
        }

        .space-info {
            margin-top: 40px;
            background: linear-gradient(to right, rgba(13, 27, 42, 0.9), rgba(27, 38, 53, 0.9));
            padding: 30px;
            border-radius: 20px;
            box-shadow: 0 0 25px #00f3ff;
            text-align: left;
            max-width: 1000px;
            margin-left: auto;
            margin-right: auto;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(0, 255, 255, 0.3);
        }

        .space-info h3 {
            color: #00f3ff;
            border-bottom: 2px solid #00f3ff;
            padding-bottom: 15px;
            margin-top: 0;
            text-align: center;
            font-size: 2rem;
            margin-bottom: 25px;
        }

        .space-datos {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 25px;
            margin-bottom: 25px;
        }

        .space-dato {
            background-color: rgba(0, 191, 255, 0.15);
            padding: 20px;
            border-radius: 12px;
            border-left: 4px solid #00f3ff;
            transition: all 0.3s;
            backdrop-filter: blur(5px);
        }

        .space-dato:hover {
            transform: translateY(-5px);
            box-shadow: 0 5px 15px rgba(0, 191, 255, 0.3);
        }

        .space-dato h4 {
            margin-top: 0;
            color: #00f3ff;
            font-size: 1.25rem;
            margin-bottom: 12px;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .animal-details {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
            margin-top: 20px;
        }

        .animal-detail-card {
            background: rgba(255, 255, 255, 0.1);
            border-radius: 12px;
            padding: 15px;
            backdrop-filter: blur(5px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            text-align: left;
        }

        .animal-detail-card h4 {
            color: #ffc837;
            border-bottom: 1px solid rgba(255, 255, 255, 0.2);
            padding-bottom: 8px;
            margin-top: 0;
        }

        /* Estilos responsivos */
        @media (max-width: 768px) {
            .header-main h1 {
                font-size: 2rem;
            }

            .tab-menu {
                flex-direction: column;
            }

            .tab-button {
                width: 100%;
            }

            .content-section h1,
            .space-header h2 {
                font-size: 2rem;
            }

            .planetas-grid {
                grid-template-columns: repeat(2, 1fr);
            }

            .space-datos {
                grid-template-columns: 1fr;
            }

            .animal-details {
                grid-template-columns: 1fr;
            }
        }

        @media (max-width: 480px) {
            .planetas-grid {
                grid-template-columns: 1fr;
            }

            .solar-system {
                display: none;
            }

            .search-container {
                flex-direction: column;
            }

            #animalSearch {
                width: 100%;
            }
        }
    </style>
</head>

<body>
    <div class="main-container">
        <div class="header-main">
            <h1>MultiÁrea Digital</h1>
            <p>Explora, descubre y aprende con nuestras herramientas</p>
        </div>

        <div class="tab-menu">
            <button class="tab-button active" onclick="showSection('animales')">Identificador de Animales</button>
            <button class="tab-button" onclick="showSection('espacio')">Explorador del Sistema Solar</button>
        </div>

        <div id="animales" class="content-section active">
            <h1>Identificador de Animales</h1>
            <div class="authors">Por Rodrigo Mesis, Carlos Mendoza y Ariel Flores</div>

            <div class="search-container">
                <input type="text" id="animalSearch" placeholder="Buscar animal por nombre...">
                <button id="searchButton">Buscar</button>
            </div>
            <div id="searchResults" class="search-results"></div>

            <div id="result"></div>
        </div>

        <div id="espacio" class="content-section">
            <div class="space-header">
                <h2>Explorador del Sistema Solar</h2>
                <p class="space-subtitle">DESCUBRE LOS PLANETAS DE NUESTRO SISTEMA SOLAR</p>
                <p>Creado por <strong>Carlos Mendoza</strong> y <strong>Rodrigo Mesis</strong></p>
            </div>

            <div class="solar-system">
                <div class="sun"></div>
                <div class="orbit" style="width: 160px; height: 160px;"></div>
                <div class="planet-space" style="width: 15px; height: 15px; background: #a5a5a5; animation-duration: 5s; top: 0; left: 80px;" onclick="mostrarInfoPlaneta('mercurio')"></div>
                <div class="orbit" style="width: 220px; height: 220px;"></div>
                <div class="planet-space" style="width: 20px; height: 20px; background: #e6bb6d; animation-duration: 8s; top: 0; left: 110px;" onclick="mostrarInfoPlaneta('venus')"></div>
                <div class="orbit" style="width: 280px; height: 280px;"></div>
                <div class="planet-space" style="width: 22px; height: 22px; background: #2f6aae; animation-duration: 12s; top: 0; left: 140px;" onclick="mostrarInfoPlaneta('tierra')"></div>
                <div class="orbit" style="width: 340px; height: 340px;"></div>
                <div class="planet-space" style="width: 18px; height: 18px; background: #c1440e; animation-duration: 15s; top: 0; left: 170px;" onclick="mostrarInfoPlaneta('marte')"></div>
            </div>

            <div class="planetas-grid">
                <button class="planeta-btn" onclick="mostrarInfoPlaneta('mercurio')">
                    <div class="planet-icon" style="color: #a5a5a5;"><i class="fas fa-temperature-full"></i></div>
                    <div class="planeta-nombre">Mercurio</div>
                </button>
                <button class="planeta-btn" onclick="mostrarInfoPlaneta('venus')">
                    <div class="planet-icon" style="color: #e6bb6d;"><i class="fas fa-fire"></i></div>
                    <div class="planeta-nombre">Venus</div>
                </button>
                <button class="planeta-btn" onclick="mostrarInfoPlaneta('tierra')">
                    <div class="planet-icon" style="color: #2f6aae;"><i class="fas fa-globe-americas"></i></div>
                    <div class="planeta-nombre">Tierra</div>
                </button>
                <button class="planeta-btn" onclick="mostrarInfoPlaneta('marte')">
                    <div class="planet-icon" style="color: #c1440e;"><i class="fas fa-mountain"></i></div>
                    <div class="planeta-nombre">Marte</div>
                </button>
                <button class="planeta-btn" onclick="mostrarInfoPlaneta('jupiter')">
                    <div class="planet-icon" style="color: #d8ca9d;"><i class="fas fa-wind"></i></div>
                    <div class="planeta-nombre">Júpiter</div>
                </button>
                <button class="planeta-btn" onclick="mostrarInfoPlaneta('saturno')">
                    <div class="planet-icon" style="color: #e3d8b0;"><i class="fas fa-ring"></i></div>
                    <div class="planeta-nombre">Saturno</div>
                </button>
                <button class="planeta-btn" onclick="mostrarInfoPlaneta('urano')">
                    <div class="planet-icon" style="color: #b3e3e3;"><i class="fas fa-icicles"></i></div>
                    <div class="planeta-nombre">Urano</div>
                </button>
                <button class="planeta-btn" onclick="mostrarInfoPlaneta('neptuno')">
                    <div class="planet-icon" style="color: #3454df;"><i class="fas fa-wind"></i></div>
                    <div class="planeta-nombre">Neptuno</div>
                </button>
            </div>

            <div id="info-planeta" class="space-info">
                <h3>Bienvenido al Explorador del Sistema Solar</h3>
                <p class="descripcion">Selecciona un planeta para conocer información detallada sobre él, incluyendo su tamaño, composición, características únicas y datos curiosos.</p>
            </div>
        </div>
    </div>

    <script>
        const sections = ['animales', 'espacio'];
        const tabButtons = document.querySelectorAll('.tab-button');
        const animalSearch = document.getElementById('animalSearch');
        const searchButton = document.getElementById('searchButton');
        const searchResults = document.getElementById('searchResults');
        const resultDiv = document.getElementById('result');

        function showSection(sectionId) {
            sections.forEach(id => {
                const section = document.getElementById(id);
                if (section) {
                    section.classList.remove('active');
                }
            });
            tabButtons.forEach(button => {
                button.classList.remove('active');
                if (button.textContent.includes(sectionId === 'animales' ? 'Animales' : 'Sistema')) {
                    button.classList.add('active');
                }
            });
            const targetSection = document.getElementById(sectionId);
            if (targetSection) {
                targetSection.classList.add('active');
            }
            window.scrollTo(0, 0);
        }

        document.addEventListener('DOMContentLoaded', () => {
            showSection('animales');
        });

        // Base de datos de 70 animales
        const animalDatabase = {
            "perro": {
                nombre: "Perro (Canis lupus familiaris)",
                tipo: "Mamífero doméstico",
                info: "El perro es un mamífero carnívoro de la familia de los cánidos. Es una subespecie del lobo y fue el primer animal domesticado por el ser humano. Se utiliza como animal de compañía, de trabajo, para caza, y como perro guía o de rescate.",
                alimentacion: "Omnívoro",
                clasificacion: "Mamífero",
                habitat: "Global (domesticado), originario de Eurasia",
                caracteristicas: "Excelente olfato, social, jerárquico y adaptable.",
                curiosidades: "Pueden entender hasta 250 palabras y gestos. Su nariz tiene una huella única.",
                esperanza_vida: "10-13 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Domesticado, no en peligro",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Carnivora",
                    familia: "Canidae",
                    genero: "Canis",
                    especie: "C. lupus familiaris"
                }
            },
            "gato": {
                nombre: "Gato (Felis catus)",
                tipo: "Mamífero doméstico",
                info: "El gato es un mamífero carnívoro de la familia Felidae. Es un depredador natural de pequeños animales y ha convivido con los humanos desde hace unos 9500 años.",
                alimentacion: "Carnívoro estricto",
                clasificacion: "Mamífero",
                habitat: "Global (domesticado), originario de Oriente Medio",
                caracteristicas: "Excelente visión nocturna, oído agudo, flexibilidad y gran capacidad de salto.",
                curiosidades: "Pasan aproximadamente 2/3 del día durmiendo. Su ronroneo puede tener efectos curativos.",
                esperanza_vida: "12-15 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Domesticado, no en peligro",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Carnivora",
                    familia: "Felidae",
                    genero: "Felis",
                    especie: "F. catus"
                }
            },
            "león": {
                nombre: "León (Panthera leo)",
                tipo: "Mamífero carnívoro",
                info: "El león es un gran felino carnívoro, conocido como el 'rey de la selva'. Es el único felino que vive en manadas. Los machos son fácilmente reconocibles por su melena.",
                alimentacion: "Carnívoro",
                clasificacion: "Mamífero",
                habitat: "Sabanas y pastizales de África",
                caracteristicas: "Depredador ápice, vive en manadas, fuerte rugido que se escucha a 8 km de distancia.",
                curiosidades: "Las leonas hacen la mayor parte de la caza. Un león adulto necesita comer alrededor de 5 kg de carne al día.",
                esperanza_vida: "10-14 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Vulnerable",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Carnivora",
                    familia: "Felidae",
                    genero: "Panthera",
                    especie: "P. leo"
                }
            },
            "tigre": {
                nombre: "Tigre (Panthera tigris)",
                tipo: "Mamífero carnívoro",
                info: "El tigre es el felino más grande del mundo, conocido por su pelaje naranja con rayas negras. Es un superdepredador solitario y caza ungulados de gran tamaño.",
                alimentacion: "Carnívoro",
                clasificacion: "Mamífero",
                habitat: "Bosques, selvas y manglares de Asia",
                caracteristicas: "Habilidosos nadadores, a diferencia de otros felinos. Sus rayas son únicas para cada individuo.",
                curiosidades: "Las rayas de su piel también están en su pelaje. El tigre blanco es una variante genética.",
                esperanza_vida: "10-15 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "En peligro",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Carnivora",
                    familia: "Felidae",
                    genero: "Panthera",
                    especie: "P. tigris"
                }
            },
            "oso": {
                nombre: "Oso (Ursidae)",
                tipo: "Mamífero omnívoro",
                info: "Los osos son grandes mamíferos con colas cortas y fuertes extremidades. Se caracterizan por su pelaje denso y por caminar sobre las plantas de sus pies. Son omnívoros y se encuentran en diversos hábitats.",
                alimentacion: "Omnívoro",
                clasificacion: "Mamífero",
                habitat: "América, Europa, Asia",
                caracteristicas: "Grandes y poderosos. Muchos hibernan en invierno.",
                curiosidades: "El oso panda es el que más tiempo pasa comiendo, hasta 12 horas al día.",
                esperanza_vida: "20-30 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Depende de la especie",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Carnivora",
                    familia: "Ursidae",
                    genero: "Ursus",
                    especie: "Varias"
                }
            },
            "elefante": {
                nombre: "Elefante (Elephantidae)",
                tipo: "Mamífero herbívoro",
                info: "Los elefantes son los animales terrestres más grandes. Son conocidos por su trompa, que utilizan para respirar, beber y agarrar objetos, y por sus grandes orejas que les ayudan a regular la temperatura.",
                alimentacion: "Herbívoro",
                clasificacion: "Mamífero",
                habitat: "África y Asia",
                caracteristicas: "Inteligencia notable, fuertes lazos sociales, gran tamaño.",
                curiosidades: "La trompa tiene más de 40.000 músculos. Pueden oler el agua a kilómetros de distancia.",
                esperanza_vida: "60-70 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "En peligro (Elefante africano de bosque) y En peligro crítico (Elefante asiático)",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Proboscidea",
                    familia: "Elephantidae",
                    genero: "Loxodonta, Elephas",
                    especie: "Varias"
                }
            },
            "cebra": {
                nombre: "Cebra (Equus)",
                tipo: "Mamífero herbívoro",
                info: "La cebra es un mamífero equino nativo de África, famoso por su distintivo pelaje a rayas blancas y negras.",
                alimentacion: "Herbívoro",
                clasificacion: "Mamífero",
                habitat: "África oriental y meridional",
                caracteristicas: "Rápida, ágil, vive en manadas. Sus rayas son únicas para cada individuo.",
                curiosidades: "No hay dos cebras con el mismo patrón de rayas. Se cree que las rayas ayudan a confundir a los depredadores y a repeler moscas.",
                esperanza_vida: "20-30 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Depende de la especie (algunas en peligro)",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Perissodactyla",
                    familia: "Equidae",
                    genero: "Equus",
                    especie: "Varias subespecies"
                }
            },
            "jirafa": {
                nombre: "Jirafa (Giraffa camelopardalis)",
                tipo: "Mamífero herbívoro",
                info: "La jirafa es el animal terrestre más alto, caracterizada por su cuello extremadamente largo y su distintivo patrón de manchas. Es nativa de África.",
                alimentacion: "Herbívoro (se alimenta de hojas de árboles)",
                clasificacion: "Mamífero",
                habitat: "Sabanas de África",
                caracteristicas: "Largo cuello, cuernos osificados, lengua prensil de 50 cm.",
                curiosidades: "Duermen muy poco, solo entre 10 minutos y 2 horas al día. Sus cuernos se llaman osiconos.",
                esperanza_vida: "20-25 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Vulnerable",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Artiodactyla",
                    familia: "Giraffidae",
                    genero: "Giraffa",
                    especie: "G. camelopardalis"
                }
            },
            "mono": {
                nombre: "Mono (Simios)",
                tipo: "Mamífero omnívoro",
                info: "Los monos son primates de tamaño pequeño a mediano, que habitan principalmente en árboles. Se caracterizan por su inteligencia y agilidad.",
                alimentacion: "Omnívoro",
                clasificacion: "Mamífero",
                habitat: "Bosques tropicales y selvas de América, África y Asia",
                caracteristicas: "Manos y pies prensiles, visión binocular, alta socialización.",
                curiosidades: "Algunas especies de monos pueden usar herramientas. Los monos capuchinos son conocidos por su inteligencia.",
                esperanza_vida: "15-40 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Depende de la especie (algunas en peligro)",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Primates",
                    familia: "Cercopithecidae",
                    genero: "Varias",
                    especie: "Varias"
                }
            },
            "caballo": {
                nombre: "Caballo (Equus ferus caballus)",
                tipo: "Mamífero herbívoro",
                info: "El caballo es un mamífero perisodáctilo de la familia de los équidos. Ha sido domesticado por el ser humano y es utilizado para el transporte, la agricultura y el deporte.",
                alimentacion: "Herbívoro",
                clasificacion: "Mamífero",
                habitat: "Global (domesticado), originario de Asia Central",
                caracteristicas: "Fuerte, veloz y con un excelente sentido del oído. Duermen de pie.",
                curiosidades: "Los caballos no pueden vomitar. Sus ojos están en los costados de la cabeza, lo que les da una visión casi de 360 grados.",
                esperanza_vida: "25-30 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Domesticado, no en peligro",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Perissodactyla",
                    familia: "Equidae",
                    genero: "Equus",
                    especie: "E. ferus caballus"
                }
            },
            "pájaro": {
                nombre: "Pájaro (Aves)",
                tipo: "Vertebrado volador",
                info: "Las aves son animales vertebrados, de sangre caliente, que se caracterizan por tener el cuerpo recubierto de plumas, alas para volar y un pico sin dientes.",
                alimentacion: "Depende de la especie (herbívoro, carnívoro, omnívoro)",
                clasificacion: "Ave",
                habitat: "Global",
                caracteristicas: "Vuelo, plumas, pico, ponen huevos.",
                curiosidades: "El colibrí es el único pájaro que puede volar hacia atrás.",
                esperanza_vida: "Varía mucho",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Varía mucho",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Varias",
                    familia: "Varias",
                    genero: "Varias",
                    especie: "Varias"
                }
            },
            "serpiente": {
                nombre: "Serpiente (Serpentes)",
                tipo: "Reptil carnívoro",
                info: "Las serpientes son reptiles sin patas que se desplazan reptando. Hay especies venenosas y no venenosas, y se encuentran en casi todos los continentes.",
                alimentacion: "Carnívoro",
                clasificacion: "Reptil",
                habitat: "Global, excepto la Antártida y algunas islas",
                caracteristicas: "Cuerpo alargado sin patas, escamas, mandíbula flexible para tragar presas grandes.",
                curiosidades: "Las serpientes no tienen párpados. Mudan su piel varias veces al año.",
                esperanza_vida: "Varía (10-40 años)",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo o vivíparo, según la especie",
                conservacion: "Depende de la especie",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Reptilia",
                    orden: "Squamata",
                    familia: "Varias",
                    genero: "Varias",
                    especie: "Varias"
                }
            },
            "tortuga": {
                nombre: "Tortuga (Testudines)",
                tipo: "Reptil",
                info: "Las tortugas son reptiles caracterizados por tener un caparazón que protege sus órganos internos. Existen especies terrestres, marinas y de agua dulce.",
                alimentacion: "Depende de la especie (herbívoro, carnívoro, omnívoro)",
                clasificacion: "Reptil",
                habitat: "Global (terrestre, marina, agua dulce)",
                caracteristicas: "Caparazón protector, longevidad, pico en lugar de dientes.",
                curiosidades: "Algunas especies de tortugas marinas migran miles de kilómetros. La tortuga gigante de Galápagos es una de las criaturas más longevas de la Tierra.",
                esperanza_vida: "Varía (20-150+ años)",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Depende de la especie (muchas en peligro)",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Reptilia",
                    orden: "Testudines",
                    familia: "Varias",
                    genero: "Varias",
                    especie: "Varias"
                }
            },
            "pez": {
                nombre: "Pez (Pisces)",
                tipo: "Vertebrado acuático",
                info: "Los peces son animales vertebrados acuáticos, generalmente de sangre fría, que respiran a través de branquias y tienen aletas para moverse.",
                alimentacion: "Depende de la especie (carnívoro, herbívoro, omnívoro)",
                clasificacion: "Pez",
                habitat: "Mares y aguas dulces de todo el mundo",
                caracteristicas: "Branquias para respirar, aletas, cuerpo cubierto de escamas.",
                curiosidades: "El pez más grande es el tiburón ballena, y el más pequeño es el pez de los dedos de Paedocypris progenetica.",
                esperanza_vida: "Varía mucho",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo, vivíparo o ovovivíparo",
                conservacion: "Depende de la especie",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Actinopterygii, Chondrichthyes, etc.",
                    orden: "Varias",
                    familia: "Varias",
                    genero: "Varias",
                    especie: "Varias"
                }
            },
            "tiburón": {
                nombre: "Tiburón (Selachimorpha)",
                tipo: "Pez cartilaginoso",
                info: "Los tiburones son peces depredadores que se caracterizan por su esqueleto de cartílago, su gran tamaño y sus aletas afiladas. Son superdepredadores marinos.",
                alimentacion: "Carnívoro",
                clasificacion: "Pez",
                habitat: "Océanos de todo el mundo",
                caracteristicas: "Esqueleto de cartílago, varias filas de dientes, excelente sentido del olfato.",
                curiosidades: "Los tiburones no tienen huesos, solo cartílago. Han existido en la Tierra por más de 450 millones de años.",
                esperanza_vida: "Varía (20-100 años)",
                esqueleto: "Vertebrado (cartilaginoso)",
                reproduccion: "Ovovivíparo o vivíparo",
                conservacion: "Depende de la especie (muchas en peligro)",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Chondrichthyes",
                    orden: "Varias",
                    familia: "Varias",
                    genero: "Varias",
                    especie: "Varias"
                }
            },
            "rana": {
                nombre: "Rana (Anura)",
                tipo: "Anfibio",
                info: "Las ranas son anfibios conocidos por su piel suave, ojos saltones y la capacidad de dar grandes saltos. Viven tanto en agua dulce como en tierra húmeda.",
                alimentacion: "Carnívoro (insectos y pequeños invertebrados)",
                clasificacion: "Anfibio",
                habitat: "Global (ambientes húmedos)",
                caracteristicas: "Metamorfosis (de renacuajo a rana), piel permeable, patas traseras adaptadas para saltar.",
                curiosidades: "La rana más grande es la Goliat de África, que puede pesar hasta 3.3 kg.",
                esperanza_vida: "5-15 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Depende de la especie",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Amphibia",
                    orden: "Anura",
                    familia: "Varias",
                    genero: "Varias",
                    especie: "Varias"
                }
            },
            "búho": {
                nombre: "Búho (Strigiformes)",
                tipo: "Ave rapaz",
                info: "Los búhos son aves rapaces nocturnas conocidas por su visión y oído excepcionales. Son depredadores sigilosos y tienen la capacidad de girar la cabeza casi 360 grados.",
                alimentacion: "Carnívoro (roedores, insectos, otros pájaros)",
                clasificacion: "Ave",
                habitat: "Global (excepto Antártida)",
                caracteristicas: "Visión y oído nocturnos, plumas silenciosas, garras afiladas.",
                curiosidades: "Los ojos de un búho son tubos fijos en sus cabezas, por eso tienen que girar sus cuellos.",
                esperanza_vida: "5-30 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Depende de la especie",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Strigiformes",
                    familia: "Varias",
                    genero: "Varias",
                    especie: "Varias"
                }
            },
            "pingüino": {
                nombre: "Pingüino (Spheniscidae)",
                tipo: "Ave no voladora",
                info: "Los pingüinos son aves marinas no voladoras que viven principalmente en el hemisferio sur. Están perfectamente adaptados a la vida acuática, con alas convertidas en aletas.",
                alimentacion: "Carnívoro (peces, krill)",
                clasificacion: "Ave",
                habitat: "Hemisferio Sur (Antártida, América del Sur, África, Australia)",
                caracteristicas: "No vuela, nadador excepcional, plumaje impermeable, vive en colonias.",
                curiosidades: "El pingüino emperador es el único animal de sangre caliente que se reproduce en el invierno antártico.",
                esperanza_vida: "15-20 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Depende de la especie (algunas vulnerables)",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Sphenisciformes",
                    familia: "Spheniscidae",
                    genero: "Varias",
                    especie: "Varias"
                }
            },
            "lobo": {
                nombre: "Lobo (Canis lupus)",
                tipo: "Mamífero carnívoro",
                info: "El lobo es un mamífero de la familia de los cánidos, depredador que vive y caza en manadas organizadas. Es el ancestro directo del perro doméstico.",
                alimentacion: "Carnívoro",
                clasificacion: "Mamífero",
                habitat: "Bosques, tundras y desiertos de América del Norte y Eurasia",
                caracteristicas: "Social, comunicación compleja, aullidos distintivos.",
                curiosidades: "Los lobos aúllan para comunicarse con su manada y para delimitar su territorio.",
                esperanza_vida: "6-8 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Preocupación menor, pero algunas subespecies en peligro",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Carnivora",
                    familia: "Canidae",
                    genero: "Canis",
                    especie: "C. lupus"
                }
            },
            "mariposa": {
                nombre: "Mariposa (Rhopalocera)",
                tipo: "Insecto",
                info: "Las mariposas son insectos voladores conocidos por sus grandes y coloridas alas. Pasan por un proceso de metamorfosis de oruga a mariposa adulta.",
                alimentacion: "Néctar, jugos de frutas",
                clasificacion: "Insecto",
                habitat: "Global, en la mayoría de los hábitats terrestres",
                caracteristicas: "Metamorfosis, alas grandes y coloridas, antenas.",
                curiosidades: "Las alas de las mariposas están cubiertas de pequeñas escamas. Algunas mariposas migran miles de kilómetros.",
                esperanza_vida: "2 semanas a 1 año",
                esqueleto: "Exoesqueleto",
                reproduccion: "Ovíparo",
                conservacion: "Depende de la especie",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Arthropoda",
                    clase: "Insecta",
                    orden: "Lepidoptera",
                    familia: "Varias",
                    genero: "Varias",
                    especie: "Varias"
                }
            },
            "vaca": {
                nombre: "Vaca (Bos primigenius taurus)",
                tipo: "Mamífero herbívoro",
                info: "La vaca es un mamífero rumiante de la familia de los bóvidos, domesticado para la producción de carne, leche y cuero.",
                alimentacion: "Herbívoro",
                clasificacion: "Mamífero",
                habitat: "Global (domesticado)",
                caracteristicas: "Rumiante, cuernos, grandes, cola con mechón.",
                curiosidades: "Las vacas tienen cuatro estómagos. Producen metano, un gas de efecto invernadero.",
                esperanza_vida: "18-22 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Domesticado, no en peligro",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Artiodactyla",
                    familia: "Bovidae",
                    genero: "Bos",
                    especie: "B. primigenius taurus"
                }
            },
            "cerdo": {
                nombre: "Cerdo (Sus scrofa domestica)",
                tipo: "Mamífero omnívoro",
                info: "El cerdo es un mamífero artiodáctilo de la familia de los suidos, domesticado por el ser humano para su aprovechamiento alimenticio.",
                alimentacion: "Omnívoro",
                clasificacion: "Mamífero",
                habitat: "Global (domesticado)",
                caracteristicas: "Hocico cartilaginoso, cuerpo robusto, inteligencia notable.",
                curiosidades: "Los cerdos son más limpios de lo que se cree. No sudan y usan el barro para refrescarse.",
                esperanza_vida: "15-20 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Domesticado, no en peligro",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Artiodactyla",
                    familia: "Suidae",
                    genero: "Sus",
                    especie: "S. scrofa domestica"
                }
            },
            "oveja": {
                nombre: "Oveja (Ovis aries)",
                tipo: "Mamífero herbívoro",
                info: "La oveja es un mamífero rumiante de la familia de los bóvidos, domesticada por el ser humano para aprovechar su lana, leche y carne.",
                alimentacion: "Herbívoro",
                clasificacion: "Mamífero",
                habitat: "Global (domesticado)",
                caracteristicas: "Rumiante, pelaje de lana densa, animal gregario.",
                curiosidades: "Las ovejas son muy inteligentes. Pueden reconocer hasta 50 caras diferentes de otras ovejas y humanos.",
                esperanza_vida: "10-12 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Domesticado, no en peligro",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Artiodactyla",
                    familia: "Bovidae",
                    genero: "Ovis",
                    especie: "O. aries"
                }
            },
            "conejo": {
                nombre: "Conejo (Oryctolagus cuniculus)",
                tipo: "Mamífero herbívoro",
                info: "El conejo es un pequeño mamífero lagomorfo, conocido por sus largas orejas, su rápido movimiento y su reproducción prolífica.",
                alimentacion: "Herbívoro",
                clasificacion: "Mamífero",
                habitat: "Europa, Asia, África (domesticado globalmente)",
                caracteristicas: "Largas orejas, patas traseras fuertes, roedores con dientes frontales de crecimiento continuo.",
                curiosidades: "A diferencia de los roedores, los conejos tienen 4 incisivos en el maxilar superior.",
                esperanza_vida: "8-12 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Casi amenazado",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Lagomorpha",
                    familia: "Leporidae",
                    genero: "Oryctolagus",
                    especie: "O. cuniculus"
                }
            },
            "ardilla": {
                nombre: "Ardilla (Sciuridae)",
                tipo: "Mamífero roedor",
                info: "Las ardillas son pequeños roedores conocidos por su cola tupida y por su hábito de almacenar nueces y semillas para el invierno.",
                alimentacion: "Omnívoro (nueces, semillas, frutas, insectos)",
                clasificacion: "Mamífero",
                habitat: "Global (excepto Australia y la Antártida)",
                caracteristicas: "Cola tupida, trepadora ágil, dientes frontales de crecimiento continuo.",
                curiosidades: "Las ardillas pueden encontrar comida que enterraron hace meses, incluso bajo un metro de nieve.",
                esperanza_vida: "5-10 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Rodentia",
                    familia: "Sciuridae",
                    genero: "Varias",
                    especie: "Varias"
                }
            },
            "zorro": {
                nombre: "Zorro (Vulpes)",
                tipo: "Mamífero carnívoro",
                info: "Los zorros son mamíferos cánidos de tamaño pequeño a mediano, conocidos por su astucia y por sus colas tupidas.",
                alimentacion: "Omnívoro (pequeños mamíferos, aves, insectos, frutas)",
                clasificacion: "Mamífero",
                habitat: "Global, en la mayoría de los hábitats terrestres",
                caracteristicas: "Astuto, solitario, excelente oído y olfato.",
                curiosidades: "Los zorros pueden escuchar roedores subterráneos y saltar para atraparlos con una precisión asombrosa.",
                esperanza_vida: "2-5 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Carnivora",
                    familia: "Canidae",
                    genero: "Vulpes",
                    especie: "Varias"
                }
            },
            "puma": {
                nombre: "Puma (Puma concolor)",
                tipo: "Mamífero carnívoro",
                info: "El puma, también conocido como león de montaña, es un gran felino nativo de las Américas. Es un depredador solitario y ágil.",
                alimentacion: "Carnívoro (ciervos, alces, conejos)",
                clasificacion: "Mamífero",
                habitat: "América, desde Canadá hasta el sur de la Cordillera de los Andes",
                caracteristicas: "Depredador sigiloso, gran capacidad de salto, coloración uniforme.",
                curiosidades: "El puma tiene el rango de distribución más amplio de cualquier mamífero terrestre en el hemisferio occidental.",
                esperanza_vida: "10-15 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Carnivora",
                    familia: "Felidae",
                    genero: "Puma",
                    especie: "P. concolor"
                }
            },
            "cocodrilo": {
                nombre: "Cocodrilo (Crocodylinae)",
                tipo: "Reptil carnívoro",
                info: "Los cocodrilos son grandes reptiles depredadores que habitan en los trópicos de África, Asia, América y Australia. Son conocidos por sus poderosas mandíbulas.",
                alimentacion: "Carnívoro",
                clasificacion: "Reptil",
                habitat: "Ríos, lagos y estuarios tropicales",
                caracteristicas: "Mandíbulas fuertes, cuerpo blindado con escamas, excelentes nadadores.",
                curiosidades: "La fuerza de mordida de un cocodrilo es la más fuerte del reino animal. Lloran al comer por una cuestión fisiológica.",
                esperanza_vida: "70-100 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Depende de la especie (algunas en peligro)",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Reptilia",
                    orden: "Crocodylia",
                    familia: "Crocodylidae",
                    genero: "Varias",
                    especie: "Varias"
                }
            },
            "águila": {
                nombre: "Águila (Accipitridae)",
                tipo: "Ave rapaz",
                info: "Las águilas son grandes aves rapaces, conocidas por su poderoso vuelo y su agudeza visual. Son depredadores ápices que cazan presas de gran tamaño.",
                alimentacion: "Carnívoro",
                clasificacion: "Ave",
                habitat: "Global (diversos hábitats)",
                caracteristicas: "Vista excepcional, garras y pico fuertes, gran tamaño.",
                curiosidades: "El águila calva es el símbolo nacional de Estados Unidos.",
                esperanza_vida: "20-30 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Depende de la especie",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Accipitriformes",
                    familia: "Accipitridae",
                    genero: "Aquila",
                    especie: "Varias"
                }
            },
            "pato": {
                nombre: "Pato (Anatidae)",
                tipo: "Ave acuática",
                info: "Los patos son aves acuáticas con patas palmeadas, conocidas por sus graznidos. Habitan tanto en agua dulce como salada.",
                alimentacion: "Omnívoro",
                clasificacion: "Ave",
                habitat: "Global",
                caracteristicas: "Patas palmeadas para nadar, pico aplanado, plumaje impermeable.",
                curiosidades: "El graznido de un pato no produce eco.",
                esperanza_vida: "5-10 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Anseriformes",
                    familia: "Anatidae",
                    genero: "Anas",
                    especie: "Varias"
                }
            },
            "pez payaso": {
                nombre: "Pez Payaso (Amphiprioninae)",
                tipo: "Pez marino",
                info: "El pez payaso es una especie de pez marino que vive en simbiosis con las anémonas. Es famoso por sus colores brillantes y por la película 'Buscando a Nemo'.",
                alimentacion: "Omnívoro",
                clasificacion: "Pez",
                habitat: "Arrecifes de coral del Indo-Pacífico",
                caracteristicas: "Simbiosis con anémonas, cuerpo aplanado lateralmente, colores vibrantes.",
                curiosidades: "El pez payaso puede cambiar de sexo, comenzando como macho y convirtiéndose en hembra si la hembra dominante muere.",
                esperanza_vida: "6-10 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Actinopterygii",
                    orden: "Perciformes",
                    familia: "Pomacentridae",
                    genero: "Amphiprion",
                    especie: "Varias"
                }
            },
            "iguana": {
                nombre: "Iguana (Iguanidae)",
                tipo: "Reptil herbívoro",
                info: "Las iguanas son grandes reptiles de América, conocidas por su cresta dorsal y su papada. La iguana verde es una de las especies más comunes.",
                alimentacion: "Herbívoro",
                clasificacion: "Reptil",
                habitat: "Áreas tropicales de América Central y del Sur",
                caracteristicas: "Cresta dorsal, escamas, capacidad para trepar árboles.",
                curiosidades: "Pueden desprender su cola para escapar de depredadores, aunque no es permanente.",
                esperanza_vida: "15-20 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Depende de la especie",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Reptilia",
                    orden: "Squamata",
                    familia: "Iguanidae",
                    genero: "Iguana",
                    especie: "Varias"
                }
            },
            "koala": {
                nombre: "Koala (Phascolarctos cinereus)",
                tipo: "Mamífero marsupial",
                info: "El koala es un marsupial arbóreo nativo de Australia. Se alimenta casi exclusivamente de hojas de eucalipto, que son tóxicas para la mayoría de los animales.",
                alimentacion: "Herbívoro (hojas de eucalipto)",
                clasificacion: "Mamífero",
                habitat: "Bosques de eucalipto de Australia",
                caracteristicas: "Marsupial, garras afiladas, bolsas para llevar crías.",
                curiosidades: "Duermen hasta 20 horas al día debido a su dieta baja en nutrientes.",
                esperanza_vida: "13-18 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo (marsupial)",
                conservacion: "Vulnerable",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Diprotodontia",
                    familia: "Phascolarctidae",
                    genero: "Phascolarctos",
                    especie: "P. cinereus"
                }
            },
            "pavo real": {
                nombre: "Pavo Real (Pavo cristatus)",
                tipo: "Ave",
                info: "El pavo real es un ave conocida por su deslumbrante cola, que despliega para el cortejo. Es nativo de Asia del Sur.",
                alimentacion: "Omnívoro",
                clasificacion: "Ave",
                habitat: "Bosques y campos de Asia del Sur",
                caracteristicas: "Cola grande y colorida en los machos, plumaje iridiscente.",
                curiosidades: "La cola del pavo real puede llegar a medir hasta 1.5 metros de largo.",
                esperanza_vida: "10-20 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Galliformes",
                    familia: "Phasianidae",
                    genero: "Pavo",
                    especie: "P. cristatus"
                }
            },
            "camaleón": {
                nombre: "Camaleón (Chamaeleonidae)",
                tipo: "Reptil",
                info: "Los camaleones son lagartos conocidos por su habilidad para cambiar de color y por su lengua proyectable para atrapar insectos.",
                alimentacion: "Carnívoro (insectos)",
                clasificacion: "Reptil",
                habitat: "África, Madagascar, sur de Europa y Asia",
                caracteristicas: "Cambio de color, ojos que se mueven independientemente, lengua larga y pegajosa.",
                curiosidades: "Su lengua puede ser más larga que su propio cuerpo.",
                esperanza_vida: "2-10 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo o vivíparo",
                conservacion: "Depende de la especie",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Reptilia",
                    orden: "Squamata",
                    familia: "Chamaeleonidae",
                    genero: "Varias",
                    especie: "Varias"
                }
            },
            "colibrí": {
                nombre: "Colibrí (Trochilidae)",
                tipo: "Ave",
                info: "El colibrí es un ave pequeña conocida por su capacidad de mantenerse suspendida en el aire, moviendo sus alas a gran velocidad.",
                alimentacion: "Néctar, pequeños insectos",
                clasificacion: "Ave",
                habitat: "América",
                caracteristicas: "Vuelo estacionario, rápido movimiento de alas.",
                curiosidades: "El colibrí es el único pájaro que puede volar hacia atrás. Su corazón late hasta 1,260 veces por minuto.",
                esperanza_vida: "3-5 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Depende de la especie",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Apodiformes",
                    familia: "Trochilidae",
                    genero: "Varias",
                    especie: "Varias"
                }
            },
            "rinoceronte": {
                nombre: "Rinoceronte (Rhinocerotidae)",
                tipo: "Mamífero herbívoro",
                info: "Los rinocerontes son grandes mamíferos con uno o dos cuernos en el hocico. Son conocidos por su piel gruesa y su comportamiento territorial.",
                alimentacion: "Herbívoro",
                clasificacion: "Mamífero",
                habitat: "África y Asia",
                caracteristicas: "Piel gruesa, grandes cuernos de queratina.",
                curiosidades: "Sus cuernos están hechos de queratina, la misma proteína de la que están hechas las uñas y el cabello humanos.",
                esperanza_vida: "35-50 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "En peligro crítico (algunas especies)",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Perissodactyla",
                    familia: "Rhinocerotidae",
                    genero: "Varias",
                    especie: "Varias"
                }
            },
            "hipopótamo": {
                nombre: "Hipopótamo (Hippopotamus amphibius)",
                tipo: "Mamífero herbívoro",
                info: "El hipopótamo es un mamífero semi-acuático de gran tamaño, conocido por su piel sin pelo y su comportamiento agresivo. Pasan la mayor parte del día en el agua.",
                alimentacion: "Herbívoro",
                clasificacion: "Mamífero",
                habitat: "África Subsahariana",
                caracteristicas: "Gran tamaño, piel gruesa, pasa mucho tiempo en el agua.",
                curiosidades: "Su piel segrega una sustancia rojiza que actúa como protector solar y antiséptico natural.",
                esperanza_vida: "40-50 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Vulnerable",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Artiodactyla",
                    familia: "Hippopotamidae",
                    genero: "Hippopotamus",
                    especie: "H. amphibius"
                }
            },
            "canguro": {
                nombre: "Canguro (Macropus)",
                tipo: "Mamífero marsupial",
                info: "El canguro es un marsupial endémico de Australia, conocido por su capacidad para saltar gracias a sus poderosas patas traseras y su larga cola.",
                alimentacion: "Herbívoro",
                clasificacion: "Mamífero",
                habitat: "Australia y Nueva Guinea",
                caracteristicas: "Grandes patas traseras para saltar, bolsa marsupial para crías.",
                curiosidades: "Pueden saltar hasta 9 metros de largo y 3 metros de alto. Los canguros machos 'boxean' para competir por las hembras.",
                esperanza_vida: "6-23 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo (marsupial)",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Diprotodontia",
                    familia: "Macropodidae",
                    genero: "Macropus",
                    especie: "Varias"
                }
            },
            "mono aullador": {
                nombre: "Mono Aullador (Alouatta)",
                tipo: "Mamífero primate",
                info: "El mono aullador es un mono del Nuevo Mundo conocido por sus fuertes y distintivos aullidos, que se pueden escuchar a varios kilómetros de distancia.",
                alimentacion: "Herbívoro (principalmente hojas)",
                clasificacion: "Mamífero",
                habitat: "Bosques tropicales de América",
                caracteristicas: "Aullidos potentes, cola prensil, mandíbula grande.",
                curiosidades: "Su aullido es el sonido más fuerte producido por un animal terrestre.",
                esperanza_vida: "15-20 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Depende de la especie (algunas en peligro)",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Primates",
                    familia: "Atelidae",
                    genero: "Alouatta",
                    especie: "Varias"
                }
            },
            "panda rojo": {
                nombre: "Panda Rojo (Ailurus fulgens)",
                tipo: "Mamífero carnívoro",
                info: "El panda rojo es un mamífero pequeño, similar a un mapache, con un distintivo pelaje rojizo. Habita en el Himalaya oriental y el suroeste de China.",
                alimentacion: "Omnívoro (principalmente bambú)",
                clasificacion: "Mamífero",
                habitat: "Bosques templados del Himalaya",
                caracteristicas: "Cola larga y tupida, pelaje rojizo.",
                curiosidades: "A pesar de su nombre, no está estrechamente relacionado con el panda gigante. Es el único miembro vivo de su familia.",
                esperanza_vida: "8-10 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "En peligro",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Carnivora",
                    familia: "Ailuridae",
                    genero: "Ailurus",
                    especie: "A. fulgens"
                }
            },
            "perezoso": {
                nombre: "Perezoso (Folivora)",
                tipo: "Mamífero herbívoro",
                info: "El perezoso es un mamífero arbóreo conocido por su lentitud extrema. Pasan casi toda su vida colgados de los árboles en las selvas de América Central y del Sur.",
                alimentacion: "Herbívoro (hojas y brotes)",
                clasificacion: "Mamífero",
                habitat: "Selvas tropicales de América",
                caracteristicas: "Movimiento lento, garras largas para agarrarse, vive en los árboles.",
                curiosidades: "El perezoso es tan lento que algas y polillas pueden crecer en su pelaje, lo que le ayuda a camuflarse.",
                esperanza_vida: "20-30 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Depende de la especie",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Pilosa",
                    familia: "Bradypodidae, Megalonychidae",
                    genero: "Varias",
                    especie: "Varias"
                }
            },
            "nutria": {
                nombre: "Nutria (Lutrinae)",
                tipo: "Mamífero carnívoro",
                info: "Las nutrias son mamíferos semi-acuáticos de la familia de las comadrejas. Son conocidas por su naturaleza juguetona y su habilidad para usar piedras como herramientas para romper conchas.",
                alimentacion: "Carnívoro (peces, cangrejos)",
                clasificacion: "Mamífero",
                habitat: "Ríos, lagos y costas de todo el mundo",
                caracteristicas: "Cuerpo hidrodinámico, patas palmeadas, pelaje denso e impermeable.",
                curiosidades: "Las nutrias marinas duermen tomadas de la mano para no separarse flotando.",
                esperanza_vida: "10-15 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Depende de la especie (algunas en peligro)",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Carnivora",
                    familia: "Mustelidae",
                    genero: "Lontra, Lutra, etc.",
                    especie: "Varias"
                }
            },
            "jaguar": {
                nombre: "Jaguar (Panthera onca)",
                tipo: "Mamífero carnívoro",
                info: "El jaguar es el felino más grande de América. Es un depredador solitario y oportunista, conocido por su potente mordida, la cual puede perforar caparazones de tortugas.",
                alimentacion: "Carnívoro",
                clasificacion: "Mamífero",
                habitat: "Selvas tropicales de América",
                caracteristicas: "Manchas rosetas, mandíbula extremadamente fuerte.",
                curiosidades: "Es el único gran felino que se encuentra en el Nuevo Mundo. A diferencia de otros felinos, los jaguares disfrutan del agua.",
                esperanza_vida: "12-15 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Casi amenazado",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Carnivora",
                    familia: "Felidae",
                    genero: "Panthera",
                    especie: "P. onca"
                }
            },
            "leopardo": {
                nombre: "Leopardo (Panthera pardus)",
                tipo: "Mamífero carnívoro",
                info: "El leopardo es un gran felino conocido por sus manchas en forma de roseta. Es un animal muy adaptable que puede vivir en diversos hábitats.",
                alimentacion: "Carnívoro",
                clasificacion: "Mamífero",
                habitat: "África y Asia",
                caracteristicas: "Habilidoso escalador de árboles, caza solitaria.",
                curiosidades: "Los leopardos negros son una variante genética. Tienen una visión nocturna excepcional.",
                esperanza_vida: "12-17 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Vulnerable",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Carnivora",
                    familia: "Felidae",
                    genero: "Panthera",
                    especie: "P. pardus"
                }
            },
            "guepardo": {
                nombre: "Guepardo (Acinonyx jubatus)",
                tipo: "Mamífero carnívoro",
                info: "El guepardo es el animal terrestre más rápido del mundo, capaz de alcanzar velocidades de hasta 120 km/h en distancias cortas.",
                alimentacion: "Carnívoro (antílopes, gacelas)",
                clasificacion: "Mamífero",
                habitat: "África y partes de Asia",
                caracteristicas: "Gran velocidad, cuerpo delgado, garras no retráctiles.",
                curiosidades: "A diferencia de otros felinos, sus garras son semi-retráctiles, lo que les da tracción al correr.",
                esperanza_vida: "10-12 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Vulnerable",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Carnivora",
                    familia: "Felidae",
                    genero: "Acinonyx",
                    especie: "A. jubatus"
                }
            },
            "cocodrilo": {
                nombre: "Cocodrilo (Crocodylinae)",
                tipo: "Reptil carnívoro",
                info: "Los cocodrilos son grandes reptiles depredadores que habitan en los trópicos de África, Asia, América y Australia. Son conocidos por sus poderosas mandíbulas.",
                alimentacion: "Carnívoro",
                clasificacion: "Reptil",
                habitat: "Ríos, lagos y estuarios tropicales",
                caracteristicas: "Mandíbulas fuertes, cuerpo blindado con escamas, excelentes nadadores.",
                curiosidades: "La fuerza de mordida de un cocodrilo es la más fuerte del reino animal. Lloran al comer por una cuestión fisiológica.",
                esperanza_vida: "70-100 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Depende de la especie (algunas en peligro)",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Reptilia",
                    orden: "Crocodylia",
                    familia: "Crocodylidae",
                    genero: "Varias",
                    especie: "Varias"
                }
            },
            "gorila": {
                nombre: "Gorila (Gorilla)",
                tipo: "Mamífero primate",
                info: "Los gorilas son los primates más grandes del mundo. Son animales sociales, inteligentes y conocidos por su fuerza y complexión robusta.",
                alimentacion: "Herbívoro",
                clasificacion: "Mamífero",
                habitat: "Selvas de África Central",
                caracteristicas: "Gran tamaño, inteligencia, vida en grupos familiares.",
                curiosidades: "Comparten el 98% de su ADN con los humanos. Los machos dominantes se llaman 'espalda plateada'.",
                esperanza_vida: "35-50 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "En peligro crítico",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Primates",
                    familia: "Hominidae",
                    genero: "Gorilla",
                    especie: "Varias"
                }
            },
            "rinoceronte": {
                nombre: "Rinoceronte (Rhinocerotidae)",
                tipo: "Mamífero herbívoro",
                info: "Los rinocerontes son grandes mamíferos con uno o dos cuernos en el hocico. Son conocidos por su piel gruesa y su comportamiento territorial.",
                alimentacion: "Herbívoro",
                clasificacion: "Mamífero",
                habitat: "África y Asia",
                caracteristicas: "Piel gruesa, grandes cuernos de queratina.",
                curiosidades: "Sus cuernos están hechos de queratina, la misma proteína de la que están hechas las uñas y el cabello humanos.",
                esperanza_vida: "35-50 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "En peligro crítico (algunas especies)",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Perissodactyla",
                    familia: "Rhinocerotidae",
                    genero: "Varias",
                    especie: "Varias"
                }
            },
            "tucán": {
                nombre: "Tucán (Ramphastidae)",
                tipo: "Ave",
                info: "El tucán es un ave tropical conocida por su enorme y colorido pico. A pesar de su tamaño, el pico es muy ligero.",
                alimentacion: "Frugívoro (frutas), insectos",
                clasificacion: "Ave",
                habitat: "América Central y del Sur",
                caracteristicas: "Pico grande y colorido, plumaje brillante.",
                curiosidades: "El pico del tucán ayuda a regular su temperatura corporal.",
                esperanza_vida: "20-25 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Piciformes",
                    familia: "Ramphastidae",
                    genero: "Varias",
                    especie: "Varias"
                }
            },
            "panda gigante": {
                nombre: "Panda Gigante (Ailuropoda melanoleuca)",
                tipo: "Mamífero omnívoro",
                info: "El panda gigante es un oso nativo de China, conocido por su pelaje distintivo en blanco y negro y su dieta casi exclusiva de bambú.",
                alimentacion: "Omnívoro (principalmente bambú)",
                clasificacion: "Mamífero",
                habitat: "Regiones montañosas de China central",
                caracteristicas: "Pelaje blanco y negro, gran tamaño, dieta especializada.",
                curiosidades: "A pesar de ser de la familia de los osos, su dieta es 99% vegetariana. Tienen un 'pulgar' extra en su muñeca para agarrar el bambú.",
                esperanza_vida: "20 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Vulnerable",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Carnivora",
                    familia: "Ursidae",
                    genero: "Ailuropoda",
                    especie: "A. melanoleuca"
                }
            },
            "lemur": {
                nombre: "Lémur (Lemuroidea)",
                tipo: "Mamífero primate",
                info: "Los lémures son primates nativos de Madagascar. Son conocidos por sus ojos grandes, su larga cola y su comportamiento social.",
                alimentacion: "Omnívoro",
                clasificacion: "Mamífero",
                habitat: "Madagascar",
                caracteristicas: "Grandes ojos, cola larga, vida en grupos sociales.",
                curiosidades: "Los lémures son los primates más antiguos del mundo. Su supervivencia está en riesgo por la deforestación.",
                esperanza_vida: "15-20 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Depende de la especie (muchas en peligro)",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Primates",
                    familia: "Lemuridae",
                    genero: "Varias",
                    especie: "Varias"
                }
            },
            "delfín": {
                nombre: "Delfín (Delphinidae)",
                tipo: "Mamífero marino",
                info: "Los delfines son mamíferos marinos inteligentes, conocidos por su naturaleza social, su capacidad de comunicarse con clics y silbidos, y sus saltos acrobáticos.",
                alimentacion: "Carnívoro (peces, calamares)",
                clasificacion: "Mamífero",
                habitat: "Océanos y ríos de todo el mundo",
                caracteristicas: "Inteligencia, ecolocalización, naturaleza social.",
                curiosidades: "Los delfines duermen con la mitad de su cerebro a la vez, lo que les permite estar alerta a los depredadores y continuar nadando.",
                esperanza_vida: "20-50 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Depende de la especie",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Cetacea",
                    familia: "Delphinidae",
                    genero: "Varias",
                    especie: "Varias"
                }
            },
            "cocodrilo": {
                nombre: "Cocodrilo (Crocodylinae)",
                tipo: "Reptil carnívoro",
                info: "Los cocodrilos son grandes reptiles depredadores que habitan en los trópicos de África, Asia, América y Australia. Son conocidos por sus poderosas mandíbulas.",
                alimentacion: "Carnívoro",
                clasificacion: "Reptil",
                habitat: "Ríos, lagos y estuarios tropicales",
                caracteristicas: "Mandíbulas fuertes, cuerpo blindado con escamas, excelentes nadadores.",
                curiosidades: "La fuerza de mordida de un cocodrilo es la más fuerte del reino animal. Lloran al comer por una cuestión fisiológica.",
                esperanza_vida: "70-100 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Depende de la especie (algunas en peligro)",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Reptilia",
                    orden: "Crocodylia",
                    familia: "Crocodylidae",
                    genero: "Varias",
                    especie: "Varias"
                }
            },
            "pato": {
                nombre: "Pato (Anatidae)",
                tipo: "Ave acuática",
                info: "Los patos son aves acuáticas con patas palmeadas, conocidas por sus graznidos. Habitan tanto en agua dulce como salada.",
                alimentacion: "Omnívoro",
                clasificacion: "Ave",
                habitat: "Global",
                caracteristicas: "Patas palmeadas para nadar, pico aplanado, plumaje impermeable.",
                curiosidades: "El graznido de un pato no produce eco.",
                esperanza_vida: "5-10 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Anseriformes",
                    familia: "Anatidae",
                    genero: "Anas",
                    especie: "Varias"
                }
            },
            "leopardo de las nieves": {
                nombre: "Leopardo de las Nieves (Panthera uncia)",
                tipo: "Mamífero carnívoro",
                info: "El leopardo de las nieves es un felino de gran tamaño que vive en las regiones montañosas de Asia Central. Es conocido por su pelaje gris y espeso y por ser un animal muy elusivo.",
                alimentacion: "Carnívoro",
                clasificacion: "Mamífero",
                habitat: "Montañas de Asia Central",
                caracteristicas: "Pelaje espeso, cola larga para el equilibrio, muy elusivo.",
                curiosidades: "Su larga y gruesa cola le ayuda a mantener el equilibrio en terrenos rocosos y a mantenerse caliente en el frío.",
                esperanza_vida: "10-15 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Vulnerable",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Carnivora",
                    familia: "Felidae",
                    genero: "Panthera",
                    especie: "P. uncia"
                }
            },
            "chimpancé": {
                nombre: "Chimpancé (Pan troglodytes)",
                tipo: "Mamífero primate",
                info: "El chimpancé es un gran simio que habita en los bosques y sabanas de África. Es uno de los parientes más cercanos al ser humano, con el que comparte el 98.6% del ADN.",
                alimentacion: "Omnívoro",
                clasificacion: "Mamífero",
                habitat: "Selvas tropicales de África",
                caracteristicas: "Inteligencia notable, uso de herramientas, comportamiento social complejo.",
                curiosidades: "Son capaces de aprender y usar el lenguaje de señas. Usan herramientas para cazar y recolectar comida.",
                esperanza_vida: "40-50 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "En peligro",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Primates",
                    familia: "Hominidae",
                    genero: "Pan",
                    especie: "P. troglodytes"
                }
            },
            "pato mandarín": {
                nombre: "Pato Mandarín (Aix galericulata)",
                tipo: "Ave acuática",
                info: "El pato mandarín es un ave ornamental originaria de Asia Oriental. El macho es famoso por su plumaje extraordinariamente colorido.",
                alimentacion: "Omnívoro",
                clasificacion: "Ave",
                habitat: "Bosques densos cerca de lagos y ríos",
                caracteristicas: "Plumaje muy colorido en el macho.",
                curiosidades: "En China, el pato mandarín es un símbolo de amor y fidelidad conyugal.",
                esperanza_vida: "6-10 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Anseriformes",
                    familia: "Anatidae",
                    genero: "Aix",
                    especie: "A. galericulata"
                }
            },
            "camello": {
                nombre: "Camello (Camelus)",
                tipo: "Mamífero herbívoro",
                info: "Los camellos son grandes mamíferos ungulados que viven en desiertos de Asia y África del Norte. Son conocidos por sus jorobas, que almacenan grasa.",
                alimentacion: "Herbívoro",
                clasificacion: "Mamífero",
                habitat: "Desiertos",
                caracteristicas: "Jorobas de grasa, resistencia a la sequía, pestañas largas para protegerse de la arena.",
                curiosidades: "Las jorobas de los camellos no almacenan agua, sino grasa. Sus pestañas triples protegen sus ojos de las tormentas de arena.",
                esperanza_vida: "40-50 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Domesticado",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Artiodactyla",
                    familia: "Camelidae",
                    genero: "Camelus",
                    especie: "Varias"
                }
            },
            "dromedario": {
                nombre: "Dromedario (Camelus dromedarius)",
                tipo: "Mamífero herbívoro",
                info: "El dromedario es una especie de camello con una sola joroba. Es nativo de las regiones desérticas de África del Norte, Oriente Medio y Asia del Sur.",
                alimentacion: "Herbívoro",
                clasificacion: "Mamífero",
                habitat: "Desiertos cálidos",
                caracteristicas: "Una joroba, muy resistente a la deshidratación.",
                curiosidades: "Puede sobrevivir sin agua durante días o semanas. Es el animal de carga por excelencia en los desiertos.",
                esperanza_vida: "40-50 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Domesticado",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Artiodactyla",
                    familia: "Camelidae",
                    genero: "Camelus",
                    especie: "C. dromedarius"
                }
            },
            "cebra": {
                nombre: "Cebra (Equus)",
                tipo: "Mamífero herbívoro",
                info: "La cebra es un mamífero equino nativo de África, famoso por su distintivo pelaje a rayas blancas y negras.",
                alimentacion: "Herbívoro",
                clasificacion: "Mamífero",
                habitat: "África oriental y meridional",
                caracteristicas: "Rápida, ágil, vive en manadas. Sus rayas son únicas para cada individuo.",
                curiosidades: "No hay dos cebras con el mismo patrón de rayas. Se cree que las rayas ayudan a confundir a los depredadores y a repeler moscas.",
                esperanza_vida: "20-30 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Depende de la especie (algunas en peligro)",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Perissodactyla",
                    familia: "Equidae",
                    genero: "Equus",
                    especie: "Varias subespecies"
                }
            },
            "serpiente": {
                nombre: "Serpiente (Serpentes)",
                tipo: "Reptil carnívoro",
                info: "Las serpientes son reptiles sin patas que se desplazan reptando. Hay especies venenosas y no venenosas, y se encuentran en casi todos los continentes.",
                alimentacion: "Carnívoro",
                clasificacion: "Reptil",
                habitat: "Global, excepto la Antártida y algunas islas",
                caracteristicas: "Cuerpo alargado sin patas, escamas, mandíbula flexible para tragar presas grandes.",
                curiosidades: "Las serpientes no tienen párpados. Mudan su piel varias veces al año.",
                esperanza_vida: "Varía (10-40 años)",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo o vivíparo, según la especie",
                conservacion: "Depende de la especie",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Reptilia",
                    orden: "Squamata",
                    familia: "Varias",
                    genero: "Varias",
                    especie: "Varias"
                }
            },
            "loro": {
                nombre: "Loro (Psittaciformes)",
                tipo: "Ave",
                info: "Los loros son aves tropicales conocidas por su pico curvado, patas zigodáctilas (dos dedos hacia adelante, dos hacia atrás) y por su capacidad para imitar sonidos.",
                alimentacion: "Omnívoro",
                clasificacion: "Ave",
                habitat: "Regiones tropicales y subtropicales de todo el mundo",
                caracteristicas: "Pico curvado, brillante plumaje, capacidad de imitar sonidos.",
                curiosidades: "El loro más grande es el guacamayo jacinto. Los loros son animales sociales y muy inteligentes.",
                esperanza_vida: "15-80 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Depende de la especie",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Psittaciformes",
                    familia: "Varias",
                    genero: "Varias",
                    especie: "Varias"
                }
            },
            "pulpo": {
                nombre: "Pulpo (Octopoda)",
                tipo: "Cefalópodo marino",
                info: "El pulpo es un molusco marino con ocho brazos. Son conocidos por su alta inteligencia, su capacidad para cambiar de color y su habilidad para usar herramientas.",
                alimentacion: "Carnívoro",
                clasificacion: "Cefalópodo",
                habitat: "Océanos de todo el mundo",
                caracteristicas: "Ocho brazos, inteligencia notable, capacidad de camuflaje.",
                curiosidades: "Los pulpos tienen tres corazones y sangre azul. Sus brazos tienen un 'cerebro' propio y pueden actuar de forma independiente.",
                esperanza_vida: "1-2 años",
                esqueleto: "Invertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Mollusca",
                    clase: "Cephalopoda",
                    orden: "Octopoda",
                    familia: "Varias",
                    genero: "Varias",
                    especie: "Varias"
                }
            },
            "hormiga": {
                nombre: "Hormiga (Formicidae)",
                tipo: "Insecto social",
                info: "Las hormigas son insectos sociales que viven en colonias. Son conocidas por su gran organización y por su capacidad para cargar objetos muchas veces su peso.",
                alimentacion: "Depende de la especie",
                clasificacion: "Insecto",
                habitat: "Global",
                caracteristicas: "Vida en colonias, división del trabajo, gran fuerza.",
                curiosidades: "Una colonia de hormigas tiene una reina que pone huevos. Algunas especies de hormigas cultivan hongos para alimentarse.",
                esperanza_vida: "Varía (desde semanas hasta años para la reina)",
                esqueleto: "Exoesqueleto",
                reproduccion: "Ovíparo",
                conservacion: "No en peligro",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Arthropoda",
                    clase: "Insecta",
                    orden: "Hymenoptera",
                    familia: "Formicidae",
                    genero: "Varias",
                    especie: "Varias"
                }
            },
            "abeja": {
                nombre: "Abeja (Apis)",
                tipo: "Insecto social",
                info: "Las abejas son insectos voladores que viven en colonias. Son cruciales para la polinización de las plantas y la producción de miel.",
                alimentacion: "Néctar, polen",
                clasificacion: "Insecto",
                habitat: "Global",
                caracteristicas: "Vuelo, producción de miel, polinización.",
                curiosidades: "Las abejas se comunican con danzas para indicar la ubicación de las flores.",
                esperanza_vida: "1-2 meses (obreras), 5 años (reina)",
                esqueleto: "Exoesqueleto",
                reproduccion: "Ovíparo",
                conservacion: "Depende de la especie",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Arthropoda",
                    clase: "Insecta",
                    orden: "Hymenoptera",
                    familia: "Apidae",
                    genero: "Apis",
                    especie: "Varias"
                }
            },
            "araña": {
                nombre: "Araña (Araneae)",
                tipo: "Arácnido",
                info: "Las arañas son arácnidos de ocho patas que producen seda para tejer telarañas. Son depredadores que cazan insectos.",
                alimentacion: "Carnívoro",
                clasificacion: "Arácnido",
                habitat: "Global",
                caracteristicas: "Ocho patas, producción de seda, veneno para cazar.",
                curiosidades: "No son insectos. Algunas arañas pueden vivir más de 20 años.",
                esperanza_vida: "Varía",
                esqueleto: "Exoesqueleto",
                reproduccion: "Ovíparo",
                conservacion: "No en peligro",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Arthropoda",
                    clase: "Arachnida",
                    orden: "Araneae",
                    familia: "Varias",
                    genero: "Varias",
                    especie: "Varias"
                }
            },
            "mariposa monarca": {
                nombre: "Mariposa Monarca (Danaus plexippus)",
                tipo: "Insecto",
                info: "La mariposa monarca es una de las especies de mariposas más conocidas, famosa por su larga migración anual desde Canadá y Estados Unidos a México.",
                alimentacion: "Néctar",
                clasificacion: "Insecto",
                habitat: "América del Norte",
                caracteristicas: "Alas naranja y negro, migración masiva.",
                curiosidades: "Recorren miles de kilómetros en su migración, un viaje que puede durar varias generaciones.",
                esperanza_vida: "2-6 semanas (generaciones de verano), 8 meses (generación migratoria)",
                esqueleto: "Exoesqueleto",
                reproduccion: "Ovíparo",
                conservacion: "En peligro",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Arthropoda",
                    clase: "Insecta",
                    orden: "Lepidoptera",
                    familia: "Nymphalidae",
                    genero: "Danaus",
                    especie: "D. plexippus"
                }
            },
            "rana de cristal": {
                nombre: "Rana de Cristal (Centrolenidae)",
                tipo: "Anfibio",
                info: "La rana de cristal es una familia de ranas que se caracterizan por su piel translúcida en la parte inferior, lo que permite ver sus órganos internos.",
                alimentacion: "Carnívoro (insectos)",
                clasificacion: "Anfibio",
                habitat: "Selvas tropicales de América Central y del Sur",
                caracteristicas: "Piel translúcida.",
                curiosidades: "Su transparencia es una forma de camuflaje que les ayuda a evadir a los depredadores.",
                esperanza_vida: "5-10 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Depende de la especie",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Amphibia",
                    orden: "Anura",
                    familia: "Centrolenidae",
                    genero: "Varias",
                    especie: "Varias"
                }
            },
            "salamandra gigante": {
                nombre: "Salamandra Gigante (Andrias)",
                tipo: "Anfibio",
                info: "La salamandra gigante es el anfibio más grande del mundo. Es una especie en peligro crítico que habita en los ríos de China y Japón.",
                alimentacion: "Carnívoro",
                clasificacion: "Anfibio",
                habitat: "Ríos de montaña de China y Japón",
                caracteristicas: "Gran tamaño, piel arrugada, respiración a través de la piel.",
                curiosidades: "Puede respirar a través de su piel, lo que le permite absorber oxígeno del agua.",
                esperanza_vida: "60-80 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "En peligro crítico",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Amphibia",
                    orden: "Caudata",
                    familia: "Cryptobranchidae",
                    genero: "Andrias",
                    especie: "Varias"
                }
            },
            "pavo real": {
                nombre: "Pavo Real (Pavo cristatus)",
                tipo: "Ave",
                info: "El pavo real es un ave conocida por su deslumbrante cola, que despliega para el cortejo. Es nativo de Asia del Sur.",
                alimentacion: "Omnívoro",
                clasificacion: "Ave",
                habitat: "Bosques y campos de Asia del Sur",
                caracteristicas: "Cola grande y colorida en los machos, plumaje iridiscente.",
                curiosidades: "La cola del pavo real puede llegar a medir hasta 1.5 metros de largo.",
                esperanza_vida: "10-20 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Galliformes",
                    familia: "Phasianidae",
                    genero: "Pavo",
                    especie: "P. cristatus"
                }
            },
            "murciélago": {
                nombre: "Murciélago (Chiroptera)",
                tipo: "Mamífero",
                info: "Los murciélagos son los únicos mamíferos capaces de volar. Se orientan y cazan mediante la ecolocalización.",
                alimentacion: "Depende de la especie (insectívoro, frugívoro, etc.)",
                clasificacion: "Mamífero",
                habitat: "Global (excepto Antártida)",
                caracteristicas: "Vuelo, ecolocalización.",
                curiosidades: "Pueden comer miles de insectos en una noche.",
                esperanza_vida: "10-20 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Depende de la especie",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Chiroptera",
                    familia: "Varias",
                    genero: "Varias",
                    especie: "Varias"
                }
            },
            "avestruz": {
                nombre: "Avestruz (Struthio camelus)",
                tipo: "Ave no voladora",
                info: "El avestruz es el ave más grande y pesada del mundo. A pesar de no volar, es un corredor muy rápido y puede alcanzar los 70 km/h.",
                alimentacion: "Herbívoro (plantas, raíces)",
                clasificacion: "Ave",
                habitat: "Sabanas y desiertos de África",
                caracteristicas: "Gran tamaño, no vuela, huevos grandes.",
                curiosidades: "Sus ojos son los más grandes de cualquier animal terrestre. Sus huevos pueden pesar hasta 1.5 kg.",
                esperanza_vida: "30-40 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Struthioniformes",
                    familia: "Struthionidae",
                    genero: "Struthio",
                    especie: "S. camelus"
                }
            },
            "cisne": {
                nombre: "Cisne (Cygnus)",
                tipo: "Ave acuática",
                info: "Los cisnes son grandes aves acuáticas, conocidas por su elegante cuello largo y su plumaje generalmente blanco.",
                alimentacion: "Herbívoro",
                clasificacion: "Ave",
                habitat: "Regiones templadas de todo el mundo",
                caracteristicas: "Cuello largo y curvado, nadador elegante.",
                curiosidades: "Los cisnes forman parejas monógamas que duran toda la vida.",
                esperanza_vida: "20-30 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Anseriformes",
                    familia: "Anatidae",
                    genero: "Cygnus",
                    especie: "Varias"
                }
            },
            "flamenco": {
                nombre: "Flamenco (Phoenicopteridae)",
                tipo: "Ave zancuda",
                info: "Los flamencos son aves acuáticas conocidas por su plumaje rosado brillante y su postura sobre una sola pata.",
                alimentacion: "Crustáceos, algas",
                clasificacion: "Ave",
                habitat: "América, África, Asia y Europa",
                caracteristicas: "Plumaje rosado, pico curvado, patas largas.",
                curiosidades: "Nacen con plumaje gris, el color rosado lo obtienen de su dieta rica en carotenos.",
                esperanza_vida: "20-30 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Phoenicopteriformes",
                    familia: "Phoenicopteridae",
                    genero: "Phoenicopterus",
                    especie: "Varias"
                }
            },
            "condor": {
                nombre: "Cóndor (Vultur gryphus)",
                tipo: "Ave rapaz",
                info: "El cóndor andino es un ave rapaz, carroñera y una de las aves voladoras más grandes del mundo. Es un símbolo nacional en varios países de América del Sur.",
                alimentacion: "Carroñero",
                clasificacion: "Ave",
                habitat: "Cordillera de los Andes, América del Sur",
                caracteristicas: "Envergadura de alas muy grande, cabeza sin plumas.",
                curiosidades: "Pueden volar a altitudes de hasta 5,500 metros sobre el nivel del mar y planear durante horas sin batir las alas.",
                esperanza_vida: "50-70 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Casi amenazado",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Cathartiformes",
                    familia: "Cathartidae",
                    genero: "Vultur",
                    especie: "V. gryphus"
                }
            },
            "pato": {
                nombre: "Pato (Anatidae)",
                tipo: "Ave acuática",
                info: "Los patos son aves acuáticas con patas palmeadas, conocidas por sus graznidos. Habitan tanto en agua dulce como salada.",
                alimentacion: "Omnívoro",
                clasificacion: "Ave",
                habitat: "Global",
                caracteristicas: "Patas palmeadas para nadar, pico aplanado, plumaje impermeable.",
                curiosidades: "El graznido de un pato no produce eco.",
                esperanza_vida: "5-10 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Anseriformes",
                    familia: "Anatidae",
                    genero: "Anas",
                    especie: "Varias"
                }
            },
            "boa": {
                nombre: "Boa Constrictor (Boa constrictor)",
                tipo: "Reptil",
                info: "La boa constrictor es una serpiente no venenosa que mata a sus presas por constricción, estrangulándolas hasta la asfixia.",
                alimentacion: "Carnívoro (mamíferos, aves)",
                clasificacion: "Reptil",
                habitat: "América Central y del Sur",
                caracteristicas: "Cuerpo muscular y fuerte, mandíbula flexible, no venenosa.",
                curiosidades: "Pueden vivir en diversos hábitats, desde selvas tropicales hasta zonas semiáridas.",
                esperanza_vida: "20-30 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovovivíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Reptilia",
                    orden: "Squamata",
                    familia: "Boidae",
                    genero: "Boa",
                    especie: "B. constrictor"
                }
            },
            "coyote": {
                nombre: "Coyote (Canis latrans)",
                tipo: "Mamífero carnívoro",
                info: "El coyote es un canino salvaje que vive en América del Norte y Central. Es muy adaptable y puede sobrevivir en diversos hábitats.",
                alimentacion: "Omnívoro",
                clasificacion: "Mamífero",
                habitat: "América del Norte y Central",
                caracteristicas: "Aullidos distintivos, adaptable, animal social.",
                curiosidades: "Son conocidos por sus aullidos y ladridos que emiten en grupo. Pueden correr hasta 65 km/h.",
                esperanza_vida: "10-14 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Carnivora",
                    familia: "Canidae",
                    genero: "Canis",
                    especie: "C. latrans"
                }
            },
            "nutria marina": {
                nombre: "Nutria Marina (Enhydra lutris)",
                tipo: "Mamífero marino",
                info: "La nutria marina es un mamífero marino nativo de las costas del norte y este del Océano Pacífico. Es el mamífero marino más pequeño.",
                alimentacion: "Carnívoro (erizos de mar, moluscos)",
                clasificacion: "Mamífero",
                habitat: "Costas del Océano Pacífico",
                caracteristicas: "Pelaje denso, utiliza herramientas, flotas de espaldas.",
                curiosidades: "Tienen la piel más densa de cualquier animal, con más de 100,000 pelos por centímetro cuadrado.",
                esperanza_vida: "15-20 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "En peligro",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Carnivora",
                    familia: "Mustelidae",
                    genero: "Enhydra",
                    especie: "E. lutris"
                }
            },
            "pájaro carpintero": {
                nombre: "Pájaro Carpintero (Picidae)",
                tipo: "Ave",
                info: "El pájaro carpintero es un ave conocida por su hábito de picotear árboles con su pico fuerte para encontrar insectos y crear nidos.",
                alimentacion: "Insectívoro",
                clasificacion: "Ave",
                habitat: "Global (excepto Australia y Antártida)",
                caracteristicas: "Pico fuerte, lengua larga y pegajosa.",
                curiosidades: "Su lengua es tan larga que se enrolla alrededor de su cráneo. Tienen una almohadilla de tejido elástico para amortiguar los golpes en su cabeza.",
                esperanza_vida: "4-12 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Piciformes",
                    familia: "Picidae",
                    genero: "Varias",
                    especie: "Varias"
                }
            },
            "gecko": {
                nombre: "Geco (Gekkonidae)",
                tipo: "Reptil",
                info: "Los gecos son lagartos pequeños y ágiles. Son conocidos por su capacidad de escalar superficies verticales y caminar sobre techos.",
                alimentacion: "Insectívoro",
                clasificacion: "Reptil",
                habitat: "Climas cálidos y tropicales de todo el mundo",
                caracteristicas: "Almohadillas adhesivas en los dedos, ojos grandes, vocalizaciones.",
                curiosidades: "Sus almohadillas en los dedos tienen millones de pelos microscópicos que les permiten adherirse a casi cualquier superficie.",
                esperanza_vida: "10-20 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Depende de la especie",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Reptilia",
                    orden: "Squamata",
                    familia: "Gekkonidae",
                    genero: "Varias",
                    especie: "Varias"
                }
            },
            "sinsonte": {
                nombre: "Sinsonte (Mimus polyglottos)",
                tipo: "Ave",
                info: "El sinsonte es un ave conocida por su habilidad para imitar los sonidos y cantos de otras aves y animales.",
                alimentacion: "Omnívoro",
                clasificacion: "Ave",
                habitat: "América del Norte y Central",
                caracteristicas: "Habilidad para imitar sonidos.",
                curiosidades: "Un sinsonte macho puede aprender y cantar hasta 200 canciones diferentes. Es un símbolo de la canción en la cultura americana.",
                esperanza_vida: "8-10 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Passeriformes",
                    familia: "Mimidae",
                    genero: "Mimus",
                    especie: "M. polyglottos"
                }
            },
            "cangrejo": {
                nombre: "Cangrejo (Brachyura)",
                tipo: "Crustáceo",
                info: "Los cangrejos son crustáceos decápodos con un caparazón duro. Son conocidos por caminar de lado y por sus pinzas.",
                alimentacion: "Omnívoro",
                clasificacion: "Crustáceo",
                habitat: "Océanos, agua dulce y tierra",
                caracteristicas: "Caminar de lado, caparazón duro, pinzas.",
                curiosidades: "Algunos cangrejos pueden regenerar sus pinzas si las pierden.",
                esperanza_vida: "Varía (3-10 años)",
                esqueleto: "Exoesqueleto",
                reproduccion: "Ovíparo",
                conservacion: "No en peligro",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Arthropoda",
                    clase: "Malacostraca",
                    orden: "Decapoda",
                    familia: "Varias",
                    genero: "Varias",
                    especie: "Varias"
                }
            },
            "cocodrilo de agua salada": {
                nombre: "Cocodrilo de Agua Salada (Crocodylus porosus)",
                tipo: "Reptil",
                info: "El cocodrilo de agua salada es el reptil más grande del mundo y el cocodrilo más grande que existe. Puede vivir tanto en agua dulce como salada.",
                alimentacion: "Carnívoro",
                clasificacion: "Reptil",
                habitat: "Estuarios y costas de Asia y Australia",
                caracteristicas: "Gran tamaño, agresivo, puede vivir en agua salada.",
                curiosidades: "Los machos pueden alcanzar hasta 7 metros de largo. Son depredadores ápices en su ecosistema.",
                esperanza_vida: "70+ años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Reptilia",
                    orden: "Crocodylia",
                    familia: "Crocodylidae",
                    genero: "Crocodylus",
                    especie: "C. porosus"
                }
            },
            "komodo": {
                nombre: "Dragón de Komodo (Varanus komodoensis)",
                tipo: "Reptil",
                info: "El dragón de Komodo es el lagarto más grande del mundo. Es un superdepredador nativo de algunas islas de Indonesia.",
                alimentacion: "Carnívoro",
                clasificacion: "Reptil",
                habitat: "Islas de Indonesia",
                caracteristicas: "Gran tamaño, saliva venenosa.",
                curiosidades: "Tienen un veneno anticoagulante en su saliva que debilita a sus presas. Pueden comer hasta el 80% de su peso en una sola comida.",
                esperanza_vida: "30 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "En peligro",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Reptilia",
                    orden: "Squamata",
                    familia: "Varanidae",
                    genero: "Varanus",
                    especie: "V. komodoensis"
                }
            },
            "águila harpía": {
                nombre: "Águila Harpía (Harpia harpyja)",
                tipo: "Ave rapaz",
                info: "El águila harpía es una de las águilas más grandes y poderosas del mundo. Habita en las selvas tropicales de América y es capaz de cazar monos y perezosos.",
                alimentacion: "Carnívoro",
                clasificacion: "Ave",
                habitat: "Selvas tropicales de América",
                caracteristicas: "Gran tamaño, garras poderosas, cresta de plumas.",
                curiosidades: "Sus garras son más grandes y fuertes que las de un oso Grizzly. Su envergadura puede superar los 2 metros.",
                esperanza_vida: "25-35 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Casi amenazado",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Accipitriformes",
                    familia: "Accipitridae",
                    genero: "Harpia",
                    especie: "H. harpyja"
                }
            },
            "gato montés": {
                nombre: "Gato Montés (Lynx rufus)",
                tipo: "Mamífero carnívoro",
                info: "El gato montés es un felino salvaje de América del Norte, conocido por sus orejas con mechones de pelo y su cola corta.",
                alimentacion: "Carnívoro",
                clasificacion: "Mamífero",
                habitat: "América del Norte",
                caracteristicas: "Orejas con mechones, cola corta.",
                curiosidades: "Son cazadores nocturnos muy sigilosos. Pueden saltar hasta 3 metros de largo.",
                esperanza_vida: "10-12 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Carnivora",
                    familia: "Felidae",
                    genero: "Lynx",
                    especie: "L. rufus"
                }
            },
            "nutria de río": {
                nombre: "Nutria de Río (Lontra canadensis)",
                tipo: "Mamífero carnívoro",
                info: "La nutria de río es un mamífero semi-acuático conocido por su cuerpo alargado y su naturaleza juguetona. Es un excelente nadador y se desliza sobre la nieve o el hielo.",
                alimentacion: "Carnívoro (peces, cangrejos)",
                clasificacion: "Mamífero",
                habitat: "Ríos y lagos de América del Norte",
                caracteristicas: "Cuerpo alargado, patas palmeadas, naturaleza juguetona.",
                curiosidades: "A menudo se les ve deslizándose sobre el barro o la nieve para divertirse.",
                esperanza_vida: "10-15 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Carnivora",
                    familia: "Mustelidae",
                    genero: "Lontra",
                    especie: "L. canadensis"
                }
            },
            "pato mallard": {
                nombre: "Pato Mallard (Anas platyrhynchos)",
                tipo: "Ave acuática",
                info: "El pato mallard es la especie de pato más común en el hemisferio norte. El macho es conocido por su cabeza verde iridiscente.",
                alimentacion: "Omnívoro",
                clasificacion: "Ave",
                habitat: "Humedales, ríos y lagos del hemisferio norte",
                caracteristicas: "Cabeza verde iridiscente en el macho, graznido ruidoso.",
                curiosidades: "El pato doméstico desciende del pato mallard.",
                esperanza_vida: "5-10 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Anseriformes",
                    familia: "Anatidae",
                    genero: "Anas",
                    especie: "A. platyrhynchos"
                }
            },
            "pelícano": {
                nombre: "Pelícano (Pelecanus)",
                tipo: "Ave acuática",
                info: "El pelícano es un ave acuática grande conocida por su enorme pico con una bolsa gular extensible para atrapar peces.",
                alimentacion: "Carnívoro (peces)",
                clasificacion: "Ave",
                habitat: "Regiones costeras y humedales de todo el mundo",
                caracteristicas: "Pico con bolsa gular, grandes alas.",
                curiosidades: "La bolsa del pico puede contener hasta 11 litros de agua.",
                esperanza_vida: "15-25 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Pelecaniformes",
                    familia: "Pelecanidae",
                    genero: "Pelecanus",
                    especie: "Varias"
                }
            },
            "iguana marina": {
                nombre: "Iguana Marina (Amblyrhynchus cristatus)",
                tipo: "Reptil",
                info: "La iguana marina es un lagarto endémico de las Islas Galápagos y el único lagarto que busca alimento en el mar.",
                alimentacion: "Herbívoro (algas marinas)",
                clasificacion: "Reptil",
                habitat: "Islas Galápagos",
                caracteristicas: "Adaptada a la vida marina, expulsa sal por la nariz.",
                curiosidades: "Tienen una glándula especial que filtra el exceso de sal que ingieren al comer algas marinas, expulsándola por la nariz.",
                esperanza_vida: "10-20 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Vulnerable",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Reptilia",
                    orden: "Squamata",
                    familia: "Iguanidae",
                    genero: "Amblyrhynchus",
                    especie: "A. cristatus"
                }
            },
            "cocodrilo de nilo": {
                nombre: "Cocodrilo del Nilo (Crocodylus niloticus)",
                tipo: "Reptil",
                info: "El cocodrilo del Nilo es un gran reptil que habita en los lagos, ríos y pantanos de África Subsahariana. Es uno de los depredadores más temidos de África.",
                alimentacion: "Carnívoro",
                clasificacion: "Reptil",
                habitat: "Ríos y lagos de África Subsahariana",
                caracteristicas: "Gran tamaño, poderoso nadador, mandíbula fuerte.",
                curiosidades: "Pueden pasar horas sumergidos, con solo sus ojos y fosas nasales fuera del agua.",
                esperanza_vida: "45-50 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Reptilia",
                    orden: "Crocodylia",
                    familia: "Crocodylidae",
                    genero: "Crocodylus",
                    especie: "C. niloticus"
                }
            },
            "pato real": {
                nombre: "Pato Real (Cairina moschata)",
                tipo: "Ave acuática",
                info: "El pato real es una especie de ave grande y pesada, originaria de América. Es un pato de plumaje oscuro y a menudo se domestica.",
                alimentacion: "Omnívoro",
                clasificacion: "Ave",
                habitat: "América Central y del Sur",
                caracteristicas: "Grande, pico con carúnculas rojas.",
                curiosidades: "Es conocido por ser muy silencioso, ya que rara vez grazna.",
                esperanza_vida: "8-12 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Anseriformes",
                    familia: "Anatidae",
                    genero: "Cairina",
                    especie: "C. moschata"
                }
            },
            "rana arborícola": {
                nombre: "Rana Arborícola (Hylidae)",
                tipo: "Anfibio",
                info: "Las ranas arborícolas son anfibios conocidos por sus discos adhesivos en los dedos, que les permiten trepar a los árboles y hojas.",
                alimentacion: "Carnívoro (insectos)",
                clasificacion: "Anfibio",
                habitat: "América, Asia, Europa y Australia",
                caracteristicas: "Discos adhesivos en los dedos, trepadora ágil.",
                curiosidades: "Sus dedos actúan como ventosas, permitiéndoles aferrarse a superficies lisas.",
                esperanza_vida: "5-10 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Depende de la especie",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Amphibia",
                    orden: "Anura",
                    familia: "Hylidae",
                    genero: "Varias",
                    especie: "Varias"
                }
            },
            "iguana verde": {
                nombre: "Iguana Verde (Iguana iguana)",
                tipo: "Reptil",
                info: "La iguana verde es un lagarto grande y herbívoro, muy popular como mascota. Es nativa de América Central y del Sur.",
                alimentacion: "Herbívoro",
                clasificacion: "Reptil",
                habitat: "Selvas tropicales de América",
                caracteristicas: "Color verde, cresta dorsal, papada.",
                curiosidades: "Son excelentes nadadoras y pueden aguantar la respiración bajo el agua durante largos períodos.",
                esperanza_vida: "15-20 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Reptilia",
                    orden: "Squamata",
                    familia: "Iguanidae",
                    genero: "Iguana",
                    especie: "I. iguana"
                }
            },
            "perezoso de dos dedos": {
                nombre: "Perezoso de Dos Dedos (Choloepus)",
                tipo: "Mamífero herbívoro",
                info: "El perezoso de dos dedos es una especie de perezoso que, a diferencia del de tres dedos, tiene dos garras en las patas delanteras. Es más activo que su pariente.",
                alimentacion: "Omnívoro (hojas, frutos, insectos)",
                clasificacion: "Mamífero",
                habitat: "Selvas tropicales de América Central y del Sur",
                caracteristicas: "Dos garras en las patas delanteras, menos lento que el de tres dedos.",
                curiosidades: "A pesar de su nombre, en realidad tiene 3 dedos en las patas traseras.",
                esperanza_vida: "20-30 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Pilosa",
                    familia: "Megalonychidae",
                    genero: "Choloepus",
                    especie: "Varias"
                }
            },
            "nutria gigante": {
                nombre: "Nutria Gigante (Pteronura brasiliensis)",
                tipo: "Mamífero carnívoro",
                info: "La nutria gigante es la nutria más grande del mundo, nativa de América del Sur. Es un animal social que vive en grupos familiares.",
                alimentacion: "Carnívoro (peces, cangrejos)",
                clasificacion: "Mamífero",
                habitat: "Ríos y humedales de América del Sur",
                caracteristicas: "Gran tamaño, naturaleza social, comportamiento ruidoso.",
                curiosidades: "A menudo se le llama 'lobo de río' en Sudamérica.",
                esperanza_vida: "10-15 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "En peligro",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Carnivora",
                    familia: "Mustelidae",
                    genero: "Pteronura",
                    especie: "P. brasiliensis"
                }
            },
            "águila real": {
                nombre: "Águila Real (Aquila chrysaetos)",
                tipo: "Ave rapaz",
                info: "El águila real es una de las aves rapaces más conocidas y la más grande del hemisferio norte. Es un poderoso cazador.",
                alimentacion: "Carnívoro",
                clasificacion: "Ave",
                habitat: "Hemisferio Norte",
                caracteristicas: "Grandes garras, vista aguda.",
                curiosidades: "Ha sido utilizada en cetrería desde la antigüedad. Su vista es hasta 8 veces mejor que la de un humano.",
                esperanza_vida: "20-30 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Accipitriformes",
                    familia: "Accipitridae",
                    genero: "Aquila",
                    especie: "A. chrysaetos"
                }
            },
            "cisne negro": {
                nombre: "Cisne Negro (Cygnus atratus)",
                tipo: "Ave acuática",
                info: "El cisne negro es una especie de cisne originaria de Australia. Es conocido por su plumaje completamente negro y su pico rojo.",
                alimentacion: "Herbívoro",
                clasificacion: "Ave",
                habitat: "Humedales y lagos de Australia",
                caracteristicas: "Plumaje negro, pico rojo brillante.",
                curiosidades: "En la cultura occidental, el cisne negro era un símbolo de algo imposible hasta que se descubrió su existencia.",
                esperanza_vida: "10-15 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Anseriformes",
                    familia: "Anatidae",
                    genero: "Cygnus",
                    especie: "C. atratus"
                }
            },
            "pato criollo": {
                nombre: "Pato Criollo (Cairina moschata)",
                tipo: "Ave acuática",
                info: "El pato criollo es una especie de pato doméstico, conocido por sus excrecencias rojizas alrededor de la cara.",
                alimentacion: "Omnívoro",
                clasificacion: "Ave",
                habitat: "Global (domesticado)",
                caracteristicas: "Excrecencias rojas, plumaje oscuro.",
                curiosidades: "Es el pato domesticado de América. Se les cría por su carne y sus huevos.",
                esperanza_vida: "8-12 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Domesticado",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Anseriformes",
                    familia: "Anatidae",
                    genero: "Cairina",
                    especie: "C. moschata"
                }
            },
            "rana dorada": {
                nombre: "Rana Dorada (Phyllobates terribilis)",
                tipo: "Anfibio",
                info: "La rana dorada es una especie de rana venenosa que se encuentra en la selva tropical de Colombia. Es uno de los animales más tóxicos del mundo.",
                alimentacion: "Insectívoro",
                clasificacion: "Anfibio",
                habitat: "Selva tropical de Colombia",
                caracteristicas: "Piel brillante, altamente venenosa.",
                curiosidades: "Su veneno puede matar a 10 humanos adultos. El veneno se usa en las puntas de las flechas de las tribus indígenas.",
                esperanza_vida: "10 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "En peligro",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Amphibia",
                    orden: "Anura",
                    familia: "Dendrobatidae",
                    genero: "Phyllobates",
                    especie: "P. terribilis"
                }
            },
            "salamandra gigante china": {
                nombre: "Salamandra Gigante China (Andrias davidianus)",
                tipo: "Anfibio",
                info: "La salamandra gigante china es la salamandra más grande del mundo. Es una especie en peligro crítico que se encuentra en los ríos de China.",
                alimentacion: "Carnívoro",
                clasificacion: "Anfibio",
                habitat: "Ríos de montaña de China",
                caracteristicas: "Gran tamaño, piel arrugada, vocaliza.",
                curiosidades: "Produce un sonido similar al llanto de un bebé, por lo que a veces se le llama 'pez bebé'.",
                esperanza_vida: "50-60 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "En peligro crítico",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Amphibia",
                    orden: "Caudata",
                    familia: "Cryptobranchidae",
                    genero: "Andrias",
                    especie: "A. davidianus"
                }
            },
            "mariposa azul morfo": {
                nombre: "Mariposa Azul Morfo (Morpho menelaus)",
                tipo: "Insecto",
                info: "La mariposa azul morfo es una mariposa tropical conocida por sus alas iridiscentes de color azul brillante.",
                alimentacion: "Néctar, savia de árboles",
                clasificacion: "Insecto",
                habitat: "Selvas de América Central y del Sur",
                caracteristicas: "Alas azul brillante, patrones complejos.",
                curiosidades: "El color azul de sus alas no es un pigmento, sino una estructura que refracta la luz, creando el efecto iridiscente.",
                esperanza_vida: "2-3 semanas",
                esqueleto: "Exoesqueleto",
                reproduccion: "Ovíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Arthropoda",
                    clase: "Insecta",
                    orden: "Lepidoptera",
                    familia: "Nymphalidae",
                    genero: "Morpho",
                    especie: "M. menelaus"
                }
            },
            "perezoso de tres dedos": {
                nombre: "Perezoso de Tres Dedos (Bradypus)",
                tipo: "Mamífero herbívoro",
                info: "El perezoso de tres dedos es una especie de perezoso conocida por su movimiento extremadamente lento y sus tres garras en cada pata.",
                alimentacion: "Herbívoro (hojas de cecropia)",
                clasificacion: "Mamífero",
                habitat: "Selvas tropicales de América Central y del Sur",
                caracteristicas: "Movimiento extremadamente lento, tres garras en cada pata.",
                curiosidades: "Tienen un cuello tan flexible que pueden girar la cabeza 270 grados. Su metabolismo es muy lento.",
                esperanza_vida: "20-30 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Pilosa",
                    familia: "Bradypodidae",
                    genero: "Bradypus",
                    especie: "Varias"
                }
            },
            "nutria europea": {
                nombre: "Nutria Europea (Lutra lutra)",
                tipo: "Mamífero carnívoro",
                info: "La nutria europea es una especie de nutria que vive en ríos y lagos de Europa, Asia y el norte de África. Es un excelente nadador.",
                alimentacion: "Carnívoro (peces)",
                clasificacion: "Mamífero",
                habitat: "Ríos y lagos de Eurasia y África",
                caracteristicas: "Cuerpo hidrodinámico, juguetona.",
                curiosidades: "Son indicadores de la calidad del agua, ya que solo pueden vivir en aguas limpias.",
                esperanza_vida: "10-15 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Casi amenazado",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Carnivora",
                    familia: "Mustelidae",
                    genero: "Lutra",
                    especie: "L. lutra"
                }
            },
            "salamandra": {
                nombre: "Salamandra (Salamandridae)",
                tipo: "Anfibio",
                info: "Las salamandras son anfibios conocidos por su cuerpo alargado y su cola. Tienen la capacidad de regenerar extremidades y partes del cuerpo.",
                alimentacion: "Carnívoro (insectos, gusanos)",
                clasificacion: "Anfibio",
                habitat: "Global, en ambientes húmedos",
                caracteristicas: "Cuerpo alargado, cola, capacidad de regeneración.",
                curiosidades: "No se queman en el fuego. La creencia de que pueden vivir en el fuego proviene de su costumbre de esconderse en troncos.",
                esperanza_vida: "Varía (5-25 años)",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo o vivíparo",
                conservacion: "Depende de la especie",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Amphibia",
                    orden: "Urodela",
                    familia: "Salamandridae",
                    genero: "Varias",
                    especie: "Varias"
                }
            },
            "pavo": {
                nombre: "Pavo (Meleagris gallopavo)",
                tipo: "Ave",
                info: "El pavo es un ave grande y social, nativa de América del Norte. Ha sido domesticado para la producción de carne.",
                alimentacion: "Omnívoro",
                clasificacion: "Ave",
                habitat: "América del Norte (bosques)",
                caracteristicas: "Tamaño grande, plumaje vistoso en el macho.",
                curiosidades: "Los machos hinchan su cuello y despliegan la cola para impresionar a las hembras.",
                esperanza_vida: "10-15 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Galliformes",
                    familia: "Phasianidae",
                    genero: "Meleagris",
                    especie: "M. gallopavo"
                }
            },
            "loro gris africano": {
                nombre: "Loro Gris Africano (Psittacus erithacus)",
                tipo: "Ave",
                info: "El loro gris africano es una especie de loro nativa de África Central y Occidental. Es considerado uno de los animales más inteligentes y con mayor capacidad de imitar el habla humana.",
                alimentacion: "Omnívoro",
                clasificacion: "Ave",
                habitat: "Bosques de África Central y Occidental",
                caracteristicas: "Plumaje gris, cola roja, inteligencia notable.",
                curiosidades: "Algunos individuos pueden llegar a tener un vocabulario de cientos de palabras y entender el significado de algunas de ellas.",
                esperanza_vida: "40-60 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "En peligro",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Psittaciformes",
                    familia: "Psittaculidae",
                    genero: "Psittacus",
                    especie: "P. erithacus"
                }
            },
            "araña viuda negra": {
                nombre: "Araña Viuda Negra (Latrodectus)",
                tipo: "Arácnido",
                info: "La viuda negra es una araña conocida por su veneno neurotóxico, uno de los más potentes del mundo.",
                alimentacion: "Carnívoro (insectos)",
                clasificacion: "Arácnido",
                habitat: "Global, en climas templados",
                caracteristicas: "Color negro, marca roja en forma de reloj de arena.",
                curiosidades: "La hembra es más grande y venenosa que el macho.",
                esperanza_vida: "1-3 años",
                esqueleto: "Exoesqueleto",
                reproduccion: "Ovíparo",
                conservacion: "No en peligro",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Arthropoda",
                    clase: "Arachnida",
                    orden: "Araneae",
                    familia: "Theridiidae",
                    genero: "Latrodectus",
                    especie: "Varias"
                }
            },
            "cebra de grevy": {
                nombre: "Cebra de Grevy (Equus grevyi)",
                tipo: "Mamífero herbívoro",
                info: "La cebra de Grevy es la especie de cebra más grande y se caracteriza por tener las rayas más finas y juntas.",
                alimentacion: "Herbívoro",
                clasificacion: "Mamífero",
                habitat: "Este de África",
                caracteristicas: "Rayas más finas y densas, grandes orejas.",
                curiosidades: "Es la única especie de cebra que no forma rebaños. Viven en pequeños grupos de machos y hembras no permanentes.",
                esperanza_vida: "20-25 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "En peligro",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Perissodactyla",
                    familia: "Equidae",
                    genero: "Equus",
                    especie: "E. grevyi"
                }
            },
            "serpiente de cascabel": {
                nombre: "Serpiente de Cascabel (Crotalus)",
                tipo: "Reptil venenoso",
                info: "La serpiente de cascabel es un tipo de víbora venenosa que se encuentra en América. Es conocida por el sonido de su cascabel en la cola, que usa para advertir.",
                alimentacion: "Carnívoro",
                clasificacion: "Reptil",
                habitat: "América, desde Canadá hasta Argentina",
                caracteristicas: "Cascabel en la cola, veneno neurotóxico y hemotóxico.",
                curiosidades: "El cascabel está hecho de queratina. Cada vez que mudan de piel, añaden un segmento más.",
                esperanza_vida: "10-20 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Reptilia",
                    orden: "Squamata",
                    familia: "Viperidae",
                    genero: "Crotalus",
                    especie: "Varias"
                }
            },
            "oso polar": {
                nombre: "Oso Polar (Ursus maritimus)",
                tipo: "Mamífero carnívoro",
                info: "El oso polar es un gran mamífero carnívoro que habita en las regiones árticas. Es el depredador terrestre más grande del planeta.",
                alimentacion: "Carnívoro (focas, morsas)",
                clasificacion: "Mamífero",
                habitat: "Regiones árticas",
                caracteristicas: "Pelaje blanco, gran tamaño, adaptado al frío extremo.",
                curiosidades: "Su piel es negra y su pelaje es translúcido, lo que le ayuda a absorber el calor del sol.",
                esperanza_vida: "20-30 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Vulnerable",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Carnivora",
                    familia: "Ursidae",
                    genero: "Ursus",
                    especie: "U. maritimus"
                }
            },
            "cabra": {
                nombre: "Cabra (Capra aegagrus hircus)",
                tipo: "Mamífero herbívoro",
                info: "La cabra es un mamífero domesticado, criado por su leche, carne, pelo y piel.",
                alimentacion: "Herbívoro",
                clasificacion: "Mamífero",
                habitat: "Global (domesticado)",
                caracteristicas: "Cuernos curvos, inteligencia, agilidad en terrenos rocosos.",
                curiosidades: "Son animales muy curiosos y pueden comer una variedad de plantas. Se cree que fueron los primeros animales en ser domesticados, junto con los perros.",
                esperanza_vida: "15-18 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Domesticado",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Artiodactyla",
                    familia: "Bovidae",
                    genero: "Capra",
                    especie: "C. aegagrus hircus"
                }
            },
            "cisne mudo": {
                nombre: "Cisne Mudo (Cygnus olor)",
                tipo: "Ave acuática",
                info: "El cisne mudo es una especie de cisne originaria de Eurasia. A pesar de su nombre, emite sonidos sibilantes y gruñidos.",
                alimentacion: "Herbívoro",
                clasificacion: "Ave",
                habitat: "Eurasia",
                caracteristicas: "Plumaje blanco, pico anaranjado con protuberancia negra.",
                curiosidades: "Es el cisne más común en parques y lagos de Europa.",
                esperanza_vida: "20-30 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Anseriformes",
                    familia: "Anatidae",
                    genero: "Cygnus",
                    especie: "C. olor"
                }
            },
            "gorrión": {
                nombre: "Gorrión (Passer domesticus)",
                tipo: "Ave",
                info: "El gorrión es un ave pequeña y robusta, una de las más comunes en el mundo. Se ha adaptado a vivir en entornos urbanos y rurales.",
                alimentacion: "Omnívoro",
                clasificacion: "Ave",
                habitat: "Global",
                caracteristicas: "Pequeño, social, canto distintivo.",
                curiosidades: "Son una de las aves más ampliamente distribuidas en el planeta, excepto en la Antártida.",
                esperanza_vida: "3-5 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Passeriformes",
                    familia: "Passeridae",
                    genero: "Passer",
                    especie: "P. domesticus"
                }
            },
            "pájaro carpintero picapinos": {
                nombre: "Pájaro Carpintero Picapinos (Dendrocopos major)",
                tipo: "Ave",
                info: "El pájaro carpintero picapinos es una especie común de pájaro carpintero en Eurasia. Tiene un plumaje blanco y negro con una marca roja distintiva.",
                alimentacion: "Insectívoro",
                clasificacion: "Ave",
                habitat: "Bosques de Eurasia",
                caracteristicas: "Plumaje distintivo, picoteo ruidoso.",
                curiosidades: "Pueden picotear la madera hasta 12,000 veces al día.",
                esperanza_vida: "5-8 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Piciformes",
                    familia: "Picidae",
                    genero: "Dendrocopos",
                    especie: "D. major"
                }
            },
            "rana verde": {
                nombre: "Rana Verde (Lithobates clamitans)",
                tipo: "Anfibio",
                info: "La rana verde es un anfibio común en América del Norte, conocida por su coloración verde o marrón y su canto similar a un banjo.",
                alimentacion: "Carnívoro (insectos, gusanos)",
                clasificacion: "Anfibio",
                habitat: "América del Norte",
                caracteristicas: "Canto distintivo, piel lisa.",
                curiosidades: "El macho emite un canto que se asemeja a la cuerda de un banjo, 'thrum-thrum'.",
                esperanza_vida: "5-10 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Amphibia",
                    orden: "Anura",
                    familia: "Ranidae",
                    genero: "Lithobates",
                    especie: "L. clamitans"
                }
            },
            "salamandra roja": {
                nombre: "Salamandra Roja (Pseudotriton ruber)",
                tipo: "Anfibio",
                info: "La salamandra roja es una especie de salamandra con una coloración roja o anaranjada brillante, que vive en el este de América del Norte.",
                alimentacion: "Carnívoro (insectos, gusanos)",
                clasificacion: "Anfibio",
                habitat: "Este de América del Norte",
                caracteristicas: "Coloración roja brillante, piel lisa.",
                curiosidades: "A menudo se confunde con la salamandra de barro, pero la salamandra roja tiene puntos negros en todo su cuerpo.",
                esperanza_vida: "15-20 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Amphibia",
                    orden: "Urodela",
                    familia: "Plethodontidae",
                    genero: "Pseudotriton",
                    especie: "P. ruber"
                }
            },
            "tiburón blanco": {
                nombre: "Tiburón Blanco (Carcharodon carcharias)",
                tipo: "Pez cartilaginoso",
                info: "El tiburón blanco es una especie de tiburón de gran tamaño, conocido como uno de los depredadores más grandes del océano. Es un depredador ápice.",
                alimentacion: "Carnívoro (mamíferos marinos)",
                clasificacion: "Pez",
                habitat: "Océanos de todo el mundo",
                caracteristicas: "Gran tamaño, poderosas mandíbulas, dientes afilados.",
                curiosidades: "El tiburón blanco es el pez depredador más grande del mundo.",
                esperanza_vida: "70+ años",
                esqueleto: "Vertebrado (cartilaginoso)",
                reproduccion: "Ovovivíparo",
                conservacion: "Vulnerable",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Chondrichthyes",
                    orden: "Lamniformes",
                    familia: "Lamnidae",
                    genero: "Carcharodon",
                    especie: "C. carcharias"
                }
            },
            "pato salvaje": {
                nombre: "Pato Salvaje (Anas platyrhynchos)",
                tipo: "Ave acuática",
                info: "El pato salvaje es la especie de pato más común en el hemisferio norte. El macho es conocido por su cabeza verde iridiscente.",
                alimentacion: "Omnívoro",
                clasificacion: "Ave",
                habitat: "Humedales, ríos y lagos del hemisferio norte",
                caracteristicas: "Cabeza verde iridiscente en el macho, graznido ruidoso.",
                curiosidades: "El pato doméstico desciende del pato salvaje.",
                esperanza_vida: "5-10 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Anseriformes",
                    familia: "Anatidae",
                    genero: "Anas",
                    especie: "A. platyrhynchos"
                }
            },
            "serpiente de maíz": {
                nombre: "Serpiente de Maíz (Pantherophis guttatus)",
                tipo: "Reptil no venenoso",
                info: "La serpiente de maíz es una serpiente no venenosa de América del Norte. Es muy popular como mascota debido a su docilidad y sus colores llamativos.",
                alimentacion: "Carnívoro (roedores)",
                clasificacion: "Reptil",
                habitat: "Este y centro de América del Norte",
                caracteristicas: "Colores brillantes, no venenosa, dócil.",
                curiosidades: "El nombre 'serpiente de maíz' se debe a que su patrón de escamas se parece a los granos de maíz.",
                esperanza_vida: "15-20 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Reptilia",
                    orden: "Squamata",
                    familia: "Colubridae",
                    genero: "Pantherophis",
                    especie: "P. guttatus"
                }
            },
            "mono capuchino": {
                nombre: "Mono Capuchino (Cebus)",
                tipo: "Mamífero primate",
                info: "El mono capuchino es un primate del Nuevo Mundo conocido por su inteligencia y su capacidad para usar herramientas, como piedras para romper nueces.",
                alimentacion: "Omnívoro",
                clasificacion: "Mamífero",
                habitat: "Selvas de América Central y del Sur",
                caracteristicas: "Inteligencia notable, uso de herramientas, cola prensil.",
                curiosidades: "Son conocidos por ser los primates no humanos más inteligentes.",
                esperanza_vida: "25 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Primates",
                    familia: "Cebidae",
                    genero: "Cebus",
                    especie: "Varias"
                }
            },
            "loro yaco": {
                nombre: "Loro Yaco (Psittacus erithacus)",
                tipo: "Ave",
                info: "El loro yaco, también conocido como loro gris africano, es una de las aves con mayor capacidad para imitar el habla humana. Su inteligencia es comparable a la de un niño de 5 años.",
                alimentacion: "Omnívoro",
                clasificacion: "Ave",
                habitat: "África Central",
                caracteristicas: "Plumaje gris, cola roja, inteligencia notable.",
                curiosidades: "Pueden aprender un vocabulario de hasta 1,000 palabras.",
                esperanza_vida: "40-60 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "En peligro",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Psittaciformes",
                    familia: "Psittaculidae",
                    genero: "Psittacus",
                    especie: "P. erithacus"
                }
            },
            "araña de tela de embudo": {
                nombre: "Araña de Tela de Embudo (Hexathelidae)",
                tipo: "Arácnido",
                info: "Las arañas de tela de embudo son arácnidos venenosos, conocidos por la forma de sus telarañas. Son originarias de Australia y otras regiones.",
                alimentacion: "Carnívoro",
                clasificacion: "Arácnido",
                habitat: "Australia, Asia, América",
                caracteristicas: "Veneno potente, patas gruesas.",
                curiosidades: "Su veneno puede ser mortal para los humanos si no se trata a tiempo.",
                esperanza_vida: "5-10 años",
                esqueleto: "Exoesqueleto",
                reproduccion: "Ovíparo",
                conservacion: "Depende de la especie",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Arthropoda",
                    clase: "Arachnida",
                    orden: "Araneae",
                    familia: "Hexathelidae",
                    genero: "Varias",
                    especie: "Varias"
                }
            },
            "pato almizclado": {
                nombre: "Pato Almizclado (Cairina moschata)",
                tipo: "Ave acuática",
                info: "El pato almizclado es una especie de pato grande, con plumaje oscuro y una carúncula roja en el pico. Es nativo de América Central y del Sur.",
                alimentacion: "Omnívoro",
                clasificacion: "Ave",
                habitat: "América Central y del Sur",
                caracteristicas: "Carúnculas rojas en la cara, gran tamaño.",
                curiosidades: "Es el pato domesticado de América, conocido por su tranquilidad y su carne de alta calidad.",
                esperanza_vida: "8-12 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Anseriformes",
                    familia: "Anatidae",
                    genero: "Cairina",
                    especie: "C. moschata"
                }
            },
            "perezoso de dos dedos de linnaeus": {
                nombre: "Perezoso de Dos Dedos de Linnaeus (Choloepus didactylus)",
                tipo: "Mamífero herbívoro",
                info: "El perezoso de dos dedos de Linnaeus es una especie de perezoso que habita en las selvas de América del Sur. Es conocido por su gran agilidad a pesar de su movimiento lento.",
                alimentacion: "Herbívoro",
                clasificacion: "Mamífero",
                habitat: "Selvas de América del Sur",
                caracteristicas: "Dos garras en patas delanteras, menos lento.",
                curiosidades: "A diferencia de los perezosos de tres dedos, este perezoso es más activo y nocturno.",
                esperanza_vida: "20-30 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Pilosa",
                    familia: "Megalonychidae",
                    genero: "Choloepus",
                    especie: "C. didactylus"
                }
            },
            "pingüino emperador": {
                nombre: "Pingüino Emperador (Aptenodytes forsteri)",
                tipo: "Ave no voladora",
                info: "El pingüino emperador es la especie de pingüino más grande y vive en la Antártida. Es conocido por su capacidad para sobrevivir en las condiciones más frías del planeta.",
                alimentacion: "Carnívoro (peces, krill)",
                clasificacion: "Ave",
                habitat: "Antártida",
                caracteristicas: "Gran tamaño, resistente al frío extremo.",
                curiosidades: "Es la única especie de ave que se reproduce durante el invierno antártico. Los machos incuban el huevo sobre sus pies durante meses.",
                esperanza_vida: "20 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Casi amenazado",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Sphenisciformes",
                    familia: "Spheniscidae",
                    genero: "Aptenodytes",
                    especie: "A. forsteri"
                }
            },
            "iguana de galápagos": {
                nombre: "Iguana de Galápagos (Conolophus)",
                tipo: "Reptil",
                info: "Las iguanas de Galápagos son una especie de iguanas que se encuentran en las Islas Galápagos. Existen varias subespecies, incluyendo la iguana terrestre y la iguana rosada.",
                alimentacion: "Herbívoro",
                clasificacion: "Reptil",
                habitat: "Islas Galápagos",
                caracteristicas: "Especies endémicas, gran tamaño.",
                curiosidades: "La iguana terrestre es una de las especies de iguanas más grandes. La iguana rosada fue descubierta recientemente en la isla Isabela.",
                esperanza_vida: "50-60 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Vulnerable o en peligro crítico",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Reptilia",
                    orden: "Squamata",
                    familia: "Iguanidae",
                    genero: "Conolophus",
                    especie: "Varias"
                }
            },
            "pato negro americano": {
                nombre: "Pato Negro Americano (Anas rubripes)",
                tipo: "Ave acuática",
                info: "El pato negro americano es una especie de pato del este de América del Norte, conocido por su plumaje oscuro.",
                alimentacion: "Omnívoro",
                clasificacion: "Ave",
                habitat: "Humedales del este de América del Norte",
                caracteristicas: "Plumaje oscuro, pico amarillo.",
                curiosidades: "Puede hibridarse con el pato salvaje. Es una especie muy buscada por los cazadores.",
                esperanza_vida: "10-15 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Anseriformes",
                    familia: "Anatidae",
                    genero: "Anas",
                    especie: "A. rubripes"
                }
            },
            "murciélago de herradura": {
                nombre: "Murciélago de Herradura (Rhinolophidae)",
                tipo: "Mamífero",
                info: "Los murciélagos de herradura son una familia de murciélagos conocidos por la forma de herradura de su nariz, que les ayuda a enfocar sus emisiones de ecolocalización.",
                alimentacion: "Insectívoro",
                clasificacion: "Mamífero",
                habitat: "Global, en cuevas y árboles",
                caracteristicas: "Nariz con forma de herradura, ecolocalización.",
                curiosidades: "Son una de las familias de murciélagos más diversas. Emplean una ecolocalización muy sofisticada.",
                esperanza_vida: "20-30 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Depende de la especie",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Chiroptera",
                    familia: "Rhinolophidae",
                    genero: "Rhinolophus",
                    especie: "Varias"
                }
            },
            "avestruz de cuello rojo": {
                nombre: "Avestruz de Cuello Rojo (Struthio camelus camelus)",
                tipo: "Ave no voladora",
                info: "El avestruz de cuello rojo es una subespecie de avestruz nativa de África del Norte. Es la más grande de todas las subespecies.",
                alimentacion: "Herbívoro",
                clasificacion: "Ave",
                habitat: "África del Norte",
                caracteristicas: "Cuello rojo, gran tamaño.",
                curiosidades: "Es una de las especies más amenazadas de avestruces debido a la caza furtiva.",
                esperanza_vida: "30-40 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "En peligro crítico",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Struthioniformes",
                    familia: "Struthionidae",
                    genero: "Struthio",
                    especie: "S. camelus camelus"
                }
            },
            "cisne trompetero": {
                nombre: "Cisne Trompetero (Cygnus buccinator)",
                tipo: "Ave acuática",
                info: "El cisne trompetero es la especie de cisne nativa de América del Norte. Es la más grande de las aves acuáticas de América.",
                alimentacion: "Herbívoro",
                clasificacion: "Ave",
                habitat: "América del Norte",
                caracteristicas: "Plumaje blanco, pico negro.",
                curiosidades: "Es el ave acuática más grande del hemisferio norte.",
                esperanza_vida: "20-30 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Anseriformes",
                    familia: "Anatidae",
                    genero: "Cygnus",
                    especie: "C. buccinator"
                }
            },
            "pájaro carpintero bellotero": {
                nombre: "Pájaro Carpintero Bellotero (Melanerpes formicivorus)",
                tipo: "Ave",
                info: "El pájaro carpintero bellotero es una especie de pájaro carpintero de América del Norte y Central, conocido por su hábito de almacenar bellotas en agujeros de árboles.",
                alimentacion: "Omnívoro",
                clasificacion: "Ave",
                habitat: "Bosques de América del Norte y Central",
                caracteristicas: "Almacenador de bellotas, pico fuerte.",
                curiosidades: "Son muy sociales y viven en grupos familiares. Un solo árbol puede tener miles de bellotas almacenadas.",
                esperanza_vida: "10-15 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Piciformes",
                    familia: "Picidae",
                    genero: "Melanerpes",
                    especie: "M. formicivorus"
                }
            },
            "rana toro": {
                nombre: "Rana Toro (Lithobates catesbeianus)",
                tipo: "Anfibio",
                info: "La rana toro es la rana más grande de América del Norte. Es conocida por su gran tamaño y su canto profundo y resonante.",
                alimentacion: "Carnívoro",
                clasificacion: "Anfibio",
                habitat: "América del Norte y Central",
                caracteristicas: "Gran tamaño, canto profundo.",
                curiosidades: "Su dieta es muy variada y puede incluir insectos, peces, ratones y otras ranas.",
                esperanza_vida: "7-10 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Amphibia",
                    orden: "Anura",
                    familia: "Ranidae",
                    genero: "Lithobates",
                    especie: "L. catesbeianus"
                }
            },
            "boa esmeralda": {
                nombre: "Boa Esmeralda (Corallus caninus)",
                tipo: "Reptil no venenoso",
                info: "La boa esmeralda es una serpiente arborícola no venenosa que habita en las selvas de América del Sur. Es conocida por su color verde brillante y su posición de descanso en los árboles.",
                alimentacion: "Carnívoro (mamíferos, aves)",
                clasificacion: "Reptil",
                habitat: "Selvas de América del Sur",
                caracteristicas: "Color verde brillante, arborícola.",
                curiosidades: "Es una de las serpientes más bellas del mundo. Su posición de descanso, enrollada en una rama, es única.",
                esperanza_vida: "20+ años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Reptilia",
                    orden: "Squamata",
                    familia: "Boidae",
                    genero: "Corallus",
                    especie: "C. caninus"
                }
            },
            "pájaro carpintero pileated": {
                nombre: "Pájaro Carpintero Pileated (Dryocopus pileatus)",
                tipo: "Ave",
                info: "El pájaro carpintero pileated es una especie grande de pájaro carpintero que habita en América del Norte. Es conocido por su distintiva cresta roja.",
                alimentacion: "Insectívoro",
                clasificacion: "Ave",
                habitat: "América del Norte",
                caracteristicas: "Gran tamaño, cresta roja, excavador de agujeros rectangulares.",
                curiosidades: "Excavan agujeros rectangulares en los árboles, una característica única en su familia.",
                esperanza_vida: "10-15 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Piciformes",
                    familia: "Picidae",
                    genero: "Dryocopus",
                    especie: "D. pileatus"
                }
            },
            "pingüino de magallanes": {
                nombre: "Pingüino de Magallanes (Spheniscus magellanicus)",
                tipo: "Ave no voladora",
                info: "El pingüino de Magallanes es una especie de pingüino que habita en las costas de América del Sur. Es el pingüino más común de la región.",
                alimentacion: "Carnívoro (peces, calamares)",
                clasificacion: "Ave",
                habitat: "Costas de América del Sur",
                caracteristicas: "Tamaño mediano, franjas blancas y negras en la cabeza.",
                curiosidades: "Migran miles de kilómetros cada año. Son una especie migratoria muy importante.",
                esperanza_vida: "20-25 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Casi amenazado",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Sphenisciformes",
                    familia: "Spheniscidae",
                    genero: "Spheniscus",
                    especie: "S. magellanicus"
                }
            },
            "pato de collar": {
                nombre: "Pato de Collar (Anas platyrhynchos)",
                tipo: "Ave acuática",
                info: "El pato de collar, también conocido como pato salvaje o pato mallard, es la especie de pato más común en el hemisferio norte. El macho es conocido por su cabeza verde iridiscente y un collar blanco.",
                alimentacion: "Omnívoro",
                clasificacion: "Ave",
                habitat: "Humedales y lagos del hemisferio norte",
                caracteristicas: "Cabeza verde iridiscente, collar blanco.",
                curiosidades: "El pato doméstico desciende del pato de collar.",
                esperanza_vida: "5-10 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Anseriformes",
                    familia: "Anatidae",
                    genero: "Anas",
                    especie: "A. platyrhynchos"
                }
            },
            "rana de árbol": {
                nombre: "Rana de Árbol (Hylidae)",
                tipo: "Anfibio",
                info: "Las ranas de árbol son anfibios conocidos por sus discos adhesivos en los dedos, que les permiten trepar a los árboles y hojas.",
                alimentacion: "Carnívoro (insectos)",
                clasificacion: "Anfibio",
                habitat: "América, Asia, Europa y Australia",
                caracteristicas: "Discos adhesivos en los dedos, trepadora ágil.",
                curiosidades: "Sus dedos actúan como ventosas, permitiéndoles aferrarse a superficies lisas.",
                esperanza_vida: "5-10 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Depende de la especie",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Amphibia",
                    orden: "Anura",
                    familia: "Hylidae",
                    genero: "Varias",
                    especie: "Varias"
                }
            },
            "tortuga de caparazón blando": {
                nombre: "Tortuga de Caparazón Blando (Trionychidae)",
                tipo: "Reptil",
                info: "Las tortugas de caparazón blando son una familia de tortugas de agua dulce que tienen un caparazón flexible y aplanado, a diferencia de las tortugas con caparazón duro.",
                alimentacion: "Omnívoro",
                clasificacion: "Reptil",
                habitat: "América del Norte, Asia, África",
                caracteristicas: "Caparazón blando y aplanado, nariz larga.",
                curiosidades: "Tienen una nariz larga que les permite respirar el aire mientras el resto de su cuerpo está sumergido en el agua.",
                esperanza_vida: "20-50 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Depende de la especie",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Reptilia",
                    orden: "Testudines",
                    familia: "Trionychidae",
                    genero: "Varias",
                    especie: "Varias"
                }
            },
            "águila calva": {
                nombre: "Águila Calva (Haliaeetus leucocephalus)",
                tipo: "Ave rapaz",
                info: "El águila calva es un águila marina, un poderoso depredador que se alimenta principalmente de peces y otras aves acuáticas.",
                alimentacion: "Carnívoro",
                clasificacion: "Ave",
                habitat: "América del Norte",
                caracteristicas: "Cabeza blanca, gran envergadura.",
                curiosidades: "El águila calva es el símbolo nacional de Estados Unidos.",
                esperanza_vida: "20-30 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Accipitriformes",
                    familia: "Accipitridae",
                    genero: "Haliaeetus",
                    especie: "H. leucocephalus"
                }
            },
            "rana venenosa": {
                nombre: "Rana Venenosa (Dendrobatidae)",
                tipo: "Anfibio",
                info: "Las ranas venenosas son una familia de ranas que se caracterizan por su piel brillante y sus glándulas venenosas. Son nativas de las selvas de América Central y del Sur.",
                alimentacion: "Insectívoro",
                clasificacion: "Anfibio",
                habitat: "Selvas tropicales de América",
                caracteristicas: "Piel brillante, veneno neurotóxico.",
                curiosidades: "Su veneno se usa en las puntas de flechas de las tribus indígenas. Obtienen su veneno de los insectos que comen.",
                esperanza_vida: "10-15 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Depende de la especie",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Amphibia",
                    orden: "Anura",
                    familia: "Dendrobatidae",
                    genero: "Varias",
                    especie: "Varias"
                }
            },
            "araña lobo": {
                nombre: "Araña Lobo (Lycosidae)",
                tipo: "Arácnido",
                info: "Las arañas lobo son una familia de arañas que cazan en el suelo, en lugar de tejer telarañas. Son conocidas por su gran tamaño y su habilidad para correr rápido.",
                alimentacion: "Carnívoro (insectos)",
                clasificacion: "Arácnido",
                habitat: "Global",
                caracteristicas: "Cazan en el suelo, no tejen telarañas, grandes ojos.",
                curiosidades: "Las hembras cargan a sus crías en la espalda durante varias semanas después de que nacen.",
                esperanza_vida: "1-2 años",
                esqueleto: "Exoesqueleto",
                reproduccion: "Ovíparo",
                conservacion: "No en peligro",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Arthropoda",
                    clase: "Arachnida",
                    orden: "Araneae",
                    familia: "Lycosidae",
                    genero: "Varias",
                    especie: "Varias"
                }
            },
            "pato muscovy": {
                nombre: "Pato Muscovy (Cairina moschata)",
                tipo: "Ave acuática",
                info: "El pato muscovy, también conocido como pato criollo o pato de la jungla, es una especie de pato grande, con plumaje oscuro y una carúncula roja en el pico.",
                alimentacion: "Omnívoro",
                clasificacion: "Ave",
                habitat: "América Central y del Sur",
                caracteristicas: "Carúnculas rojas, gran tamaño.",
                curiosidades: "Es el pato domesticado de América, conocido por su tranquilidad y su carne de alta calidad.",
                esperanza_vida: "8-12 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Anseriformes",
                    familia: "Anatidae",
                    genero: "Cairina",
                    especie: "C. moschata"
                }
            }
        };

        // Función para buscar y mostrar la información del animal
        function buscarAnimal() {
            const query = animalSearch.value.toLowerCase().trim();
            resultDiv.innerHTML = '';
            searchResults.innerHTML = '';

            if (query.length < 2) {
                resultDiv.innerHTML = '<p class="error-message">Por favor, ingrese al menos 2 letras para buscar.</p>';
                return;
            }

            const animalesEncontrados = Object.keys(animalDatabase).filter(animal => animal.includes(query));

            if (animalesEncontrados.length > 0) {
                animalesEncontrados.forEach(animal => {
                    const div = document.createElement('div');
                    div.className = 'search-item';
                    div.textContent = animal.charAt(0).toUpperCase() + animal.slice(1);
                    div.addEventListener('click', () => mostrarInformacion(animal));
                    searchResults.appendChild(div);
                });
            } else {
                resultDiv.innerHTML = '<p class="error-message">No se encontraron animales con ese nombre. Intente con otro.</p>';
            }
        }

        function mostrarInformacion(nombreAnimal) {
            const animal = animalDatabase[nombreAnimal];
            if (!animal) {
                resultDiv.innerHTML = '<p class="error-message">Información no disponible para este animal.</p>';
                return;
            }
            searchResults.innerHTML = '';

            const htmlContent = `
                <div class="info-card">
                    <img src="https://source.unsplash.com/400x300/?${nombreAnimal}" alt="${animal.nombre}" class="animal-image">
                    <h2 style="color: #ffc837; text-align: center; margin-top: 10px;">${animal.nombre}</h2>
                    <p><strong>Tipo:</strong> ${animal.tipo}</p>
                    <p><strong>Clasificación:</strong> ${animal.clasificacion}</p>
                    <p><strong>Alimentación:</strong> ${animal.alimentacion}</p>
                    <p><strong>Hábitat:</strong> ${animal.habitat}</p>
                    <p><strong>Esperanza de Vida:</strong> ${animal.esperanza_vida}</p>
                    <p><strong>Curiosidades:</strong> ${animal.curiosidades}</p>
                    <p><strong>Esqueleto:</strong> ${animal.esqueleto}</p>
                    <p><strong>Reproducción:</strong> ${animal.reproduccion}</p>
                    <p><strong>Conservación:</strong> ${animal.conservacion}</p>
                    <div class="animal-details">
                        <div class="animal-detail-card">
                            <h4>Taxonomía</h4>
                            <p><strong>Reino:</strong> ${animal.taxonomia.reino}</p>
                            <p><strong>Filo:</strong> ${animal.taxonomia.filo}</p>
                            <p><strong>Clase:</strong> ${animal.taxonomia.clase}</p>
                            <p><strong>Orden:</strong> ${animal.taxonomia.orden}</p>
                            <p><strong>Familia:</strong> ${animal.taxonomia.familia}</p>
                            <p><strong>Género:</strong> ${animal.taxonomia.genero}</p>
                            <p><strong>Especie:</strong> ${animal.taxonomia.especie}</p>
                        </div>
                        <div class="animal-detail-card">
                            <h4>Características y Datos</h4>
                            <p>${animal.info}</p>
                            <p><strong>Características Principales:</strong> ${animal.caracteristicas}</p>
                        </div>
                    </div>
                </div>
            `;
            resultDiv.innerHTML = htmlContent;
        }

        searchButton.addEventListener('click', buscarAnimal);
        animalSearch.addEventListener('keyup', (event) => {
            if (event.key === 'Enter') {
                buscarAnimal();
            }
        });

        // Funcionalidad para la sección del sistema solar
        const infoPlanetaDiv = document.getElementById('info-planeta');
        const infoPlanetas = {
            mercurio: {
                nombre: "Mercurio",
                info: "Es el planeta más pequeño y el más cercano al Sol. Su superficie es rocosa y llena de cráteres, similar a la Luna. No tiene satélites ni atmósfera significativa.",
                datos: {
                    'Diámetro': '4,879 km',
                    'Distancia al Sol': '58 millones de km',
                    'Duración del Día': '59 días terrestres',
                    'Duración del Año': '88 días terrestres',
                    'Temperatura media': '-173°C (noche) a 427°C (día)'
                },
                icono: '<i class="fas fa-temperature-full"></i>'
            },
            venus: {
                nombre: "Venus",
                info: "Conocido como el 'gemelo' de la Tierra por su tamaño y composición similar, Venus es un planeta extremadamente caliente debido a su densa atmósfera de dióxido de carbono que genera un efecto invernadero descontrolado.",
                datos: {
                    'Diámetro': '12,104 km',
                    'Distancia al Sol': '108 millones de km',
                    'Duración del Día': '243 días terrestres',
                    'Duración del Año': '225 días terrestres',
                    'Temperatura media': '465°C'
                },
                icono: '<i class="fas fa-fire"></i>'
            },
            tierra: {
                nombre: "Tierra",
                info: "Nuestro hogar, la Tierra, es el único planeta conocido con vida. Su atmósfera rica en oxígeno y su superficie con agua líquida lo hacen ideal para la vida. Tiene un único satélite natural, la Luna.",
                datos: {
                    'Diámetro': '12,742 km',
                    'Distancia al Sol': '150 millones de km',
                    'Duración del Día': '24 horas',
                    'Duración del Año': '365 días',
                    'Temperatura media': '15°C'
                },
                icono: '<i class="fas fa-globe-americas"></i>'
            },
            marte: {
                nombre: "Marte",
                info: "El 'planeta rojo' debe su color a la gran cantidad de óxido de hierro en su superficie. Posee casquetes polares, cañones, volcanes y evidencia de agua líquida en el pasado. Es el foco de la exploración espacial actual.",
                datos: {
                    'Diámetro': '6,779 km',
                    'Distancia al Sol': '228 millones de km',
                    'Duración del Día': '24.6 horas terrestres',
                    'Duración del Año': '687 días terrestres',
                    'Temperatura media': '-63°C'
                },
                icono: '<i class="fas fa-mountain"></i>'
            },
            jupiter: {
                nombre: "Júpiter",
                info: "El planeta más grande del Sistema Solar, Júpiter es un gigante gaseoso con una atmósfera de hidrógeno y helio. Es famoso por su 'Gran Mancha Roja', una tormenta gigante que ha durado siglos. Tiene al menos 79 lunas.",
                datos: {
                    'Diámetro': '139,820 km',
                    'Distancia al Sol': '778 millones de km',
                    'Duración del Día': '10 horas terrestres',
                    'Duración del Año': '12 años terrestres',
                    'Temperatura media': '-145°C'
                },
                icono: '<i class="fas fa-wind"></i>'
            },
            saturno: {
                nombre: "Saturno",
                info: "Conocido por su impresionante sistema de anillos, Saturno es el segundo planeta más grande. Es un gigante gaseoso compuesto principalmente de hidrógeno y helio. Sus anillos están formados por partículas de hielo, polvo y rocas.",
                datos: {
                    'Diámetro': '116,460 km',
                    'Distancia al Sol': '1.4 mil millones de km',
                    'Duración del Día': '10.7 horas terrestres',
                    'Duración del Año': '29.5 años terrestres',
                    'Temperatura media': '-178°C'
                },
                icono: '<i class="fas fa-ring"></i>'
            },
            urano: {
                nombre: "Urano",
                info: "Un gigante de hielo con una inclinación extrema de su eje, que lo hace rodar sobre su órbita. Su atmósfera, de metano, le da un color azul verdoso. Tiene 27 lunas conocidas y un tenue sistema de anillos.",
                datos: {
                    'Diámetro': '50,724 km',
                    'Distancia al Sol': '2.9 mil millones de km',
                    'Duración del Día': '17.2 horas terrestres',
                    'Duración del Año': '84 años terrestres',
                    'Temperatura media': '-216°C'
                },
                icono: '<i class="fas fa-icicles"></i>'
            },
            neptuno: {
                nombre: "Neptuno",
                info: "El planeta más lejano del Sol, Neptuno es un gigante de hielo conocido por sus vientos increíblemente rápidos, que superan los 2.000 km/h. Tiene 14 lunas, siendo la más grande Tritón.",
                datos: {
                    'Diámetro': '49,244 km',
                    'Distancia al Sol': '4.5 mil millones de km',
                    'Duración del Día': '16.1 horas terrestres',
                    'Duración del Año': '165 años terrestres',
                    'Temperatura media': '-214°C'
                },
                icono: '<i class="fas fa-wind"></i>'
            }
        };

        function mostrarInfoPlaneta(planeta) {
            const info = infoPlanetas[planeta];
            if (!info) return;

            const datosHTML = Object.entries(info.datos).map(([key, value]) => `
                <div class="space-dato">
                    <h4>${info.icono} ${key}</h4>
                    <p>${value}</p>
                </div>
            `).join('');

            infoPlanetaDiv.innerHTML = `
                <h3>${info.nombre}</h3>
                <p class="descripcion">${info.info}</p>
                <div class="space-datos">${datosHTML}</div>
            `;
        }

        // Llamada inicial para mostrar información de la Tierra al cargar la página de espacio
        document.querySelector('.tab-button:last-child').addEventListener('click', () => {
            setTimeout(() => mostrarInfoPlaneta('tierra'), 100);
        });
    </script>
</body>

</html>
