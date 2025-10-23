<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MultiÁrea Digital 3.0: Identificador de Animales, Explorador Solar y Más</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        /* Estilos globales y de diseño mejorado para 3.0 */
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
            transition: background 0.3s ease;
        }

        body.light-mode {
            background: linear-gradient(180deg, #f0f8ff 0%, #e6f3ff 100%);
            color: #333;
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
            justify-content: space-between;
            align-items: center;
            flex-direction: row;
        }

        body.light-mode .header-main {
            background: linear-gradient(90deg, #4a90e2, #357abd);
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

        .mode-toggle {
            background: rgba(255, 255, 255, 0.2);
            border: none;
            color: #fff;
            padding: 10px;
            border-radius: 50%;
            cursor: pointer;
            transition: all 0.3s;
        }

        body.light-mode .mode-toggle {
            color: #333;
            background: rgba(0, 0, 0, 0.1);
        }

        .mode-toggle:hover {
            transform: scale(1.1);
        }

        .tab-menu {
            display: flex;
            justify-content: center;
            gap: 10px;
            margin-bottom: 20px;
            width: 100%;
            flex-wrap: wrap;
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

        body.light-mode .tab-button {
            background-color: #ddd;
            color: #333;
        }

        .tab-button:hover {
            background-color: #555;
            transform: translateY(-2px);
        }

        body.light-mode .tab-button:hover {
            background-color: #bbb;
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

        body.light-mode .content-section {
            background: rgba(255, 255, 255, 0.8);
            border-radius: 10px;
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

        body.light-mode .content-section h1,
        body.light-mode .content-section h2 {
            color: #333;
        }

        .authors {
            font-size: 1rem;
            margin-top: 10px;
            color: rgba(255, 255, 255, 0.8);
            text-align: center;
            margin-bottom: 30px;
        }

        body.light-mode .authors {
            color: rgba(0, 0, 0, 0.7);
        }

        #result, #countryResult, #quizResult {
            margin-top: 25px;
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            padding: 15px;
            border-radius: 10px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
            text-align: left;
            width: 100%;
        }

        body.light-mode #result,
        body.light-mode #countryResult,
        body.light-mode #quizResult {
            background: rgba(0, 0, 0, 0.05);
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
        }

        .animal-info, .country-info {
            font-weight: bold;
            background: rgba(255, 255, 255, 0.8);
            padding: 4px 8px;
            border-radius: 4px;
            display: inline-block;
            color: #000;
        }

        .animal-image, .country-image {
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

        body.light-mode .info-card {
            background: rgba(0, 0, 0, 0.05);
        }

        .info-title {
            font-weight: bold;
            margin-bottom: 5px;
            color: #fff;
            font-size: 1rem;
        }

        body.light-mode .info-title {
            color: #333;
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

        body.light-mode .taxonomy-item {
            background: rgba(0, 0, 0, 0.05);
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

        #animalSearch, #countrySearch, #quizCategory {
            padding: 12px 20px;
            width: 100%;
            border-radius: 25px;
            border: none;
            font-size: 1rem;
            outline: none;
            background: rgba(255, 255, 255, 0.9);
            color: #333;
        }

        #searchButton, #countrySearchButton, #startQuiz {
            padding: 12px 25px;
            background: #FF9800;
            color: white;
            border-radius: 25px;
            cursor: pointer;
            border: none;
            transition: all 0.3s;
        }

        #searchButton:hover, #countrySearchButton:hover, #startQuiz:hover {
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

        body.light-mode .search-item {
            background: rgba(0, 0, 0, 0.05);
        }

        .search-item:hover {
            background: rgba(255, 255, 255, 0.2);
        }

        body.light-mode .search-item:hover {
            background: rgba(0, 0, 0, 0.1);
        }

        /* Estilos para el explorador espacial - Mejora: Animaciones orbitales */
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

        body.light-mode .space-header {
            background: rgba(255, 255, 255, 0.8);
            border-color: #00bfff;
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
            height: 400px;
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
            box-shadow: 0 0 50px #ff4500, 0 0 100px #ff8c00, inset 0 0 20px rgba(255, 255, 255, 0.2);
            z-index: 10;
            /* animation: pulse 4s infinite alternate; */ /* Animación desactivada */
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 24px;
            color: #fff;
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
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            animation: rotate linear infinite;
        }

        /* Animaciones orbitales únicas por planeta */
        .orbit-mercurio { width: 160px; height: 160px; animation-duration: 8s; }
        .orbit-venus { width: 220px; height: 220px; animation-duration: 20s; }
        .orbit-tierra { width: 280px; height: 280px; animation-duration: 36s; }
        .orbit-marte { width: 340px; height: 340px; animation-duration: 68s; }
        .orbit-jupiter { width: 500px; height: 500px; animation-duration: 433s; }
        .orbit-saturno { width: 600px; height: 600px; animation-duration: 1075s; }
        .orbit-urano { width: 700px; height: 700px; animation-duration: 3060s; }
        .orbit-neptuno { width: 800px; height: 800px; animation-duration: 6020s; }

        @keyframes rotate {
            from { transform: translate(-50%, -50%) rotate(0deg); }
            to { transform: translate(-50%, -50%) rotate(360deg); }
        }

        .planet-space {
            position: absolute;
            border-radius: 50%;
            transform-origin: 50% 50%;
            cursor: pointer;
            transition: all 0.3s;
            position: relative; /* Para lunas */
            top: -50%;
            left: 50%;
            animation: inherit; /* Hereda la animación del padre */
            animation-delay: -2s; /* Offset para variedad */
        }

        .planet-space:hover {
            transform: scale(1.5) !important;
            z-index: 20;
            animation-play-state: paused;
        }

        /* Órbitas de lunas (más pequeñas) */
        .moon-orbit {
            position: absolute;
            border: 1px dashed rgba(255, 255, 255, 0.2);
            border-radius: 50%;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 20px;
            height: 20px;
            animation: rotate 5s linear infinite;
        }

        .moon {
            position: absolute;
            width: 3px;
            height: 3px;
            background: #ccc;
            border-radius: 50%;
            top: 0;
            left: 50%;
            transform: translateX(-50%);
            animation: rotate 3s linear infinite reverse;
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

        body.light-mode .planeta-btn {
            background: linear-gradient(145deg, rgba(255, 255, 255, 0.8), rgba(240, 248, 255, 0.8));
            color: #333;
            border-color: rgba(0, 191, 255, 0.3);
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

        body.light-mode .planet-icon {
            background: rgba(0, 0, 0, 0.1);
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

        body.light-mode .space-info {
            background: linear-gradient(to right, rgba(255, 255, 255, 0.9), rgba(240, 248, 255, 0.9));
            border-color: rgba(0, 191, 255, 0.3);
            color: #333;
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

        body.light-mode .space-dato {
            background-color: rgba(0, 191, 255, 0.1);
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

        /* Nueva sección para lunas */
        .moons-section {
            margin-top: 20px;
            padding: 15px;
            background: rgba(255, 255, 255, 0.05);
            border-radius: 10px;
            border-left: 3px solid #00f3ff;
        }

        body.light-mode .moons-section {
            background: rgba(0, 0, 0, 0.03);
            border-left-color: #00bfff;
        }

        .moons-section h4 {
            color: #00f3ff;
            margin-bottom: 10px;
            text-align: center;
        }

        .moon-item {
            display: flex;
            justify-content: space-between;
            padding: 8px 0;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
        }

        body.light-mode .moon-item {
            border-bottom-color: rgba(0, 0, 0, 0.1);
        }

        .moon-item:last-child {
            border-bottom: none;
        }

        .moon-name {
            font-weight: 600;
        }

        .animal-details, .country-details {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
            margin-top: 20px;
        }

        .animal-detail-card, .country-detail-card {
            background: rgba(255, 255, 255, 0.1);
            border-radius: 12px;
            padding: 15px;
            backdrop-filter: blur(5px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            text-align: left;
        }

        body.light-mode .animal-detail-card,
        body.light-mode .country-detail-card {
            background: rgba(0, 0, 0, 0.05);
            border-color: rgba(0, 0, 0, 0.1);
        }

        .animal-detail-card h4, .country-detail-card h4 {
            color: #ffc837;
            border-bottom: 1px solid rgba(255, 255, 255, 0.2);
            padding-bottom: 8px;
            margin-top: 0;
        }

        body.light-mode .animal-detail-card h4,
        body.light-mode .country-detail-card h4 {
            color: #ff9800;
            border-bottom-color: rgba(0, 0, 0, 0.1);
        }

        .error-message {
            color: #ff6b6b;
            font-style: italic;
        }

        /* Mejora: Filtro avanzado */
        .filter-container {
            display: flex;
            gap: 10px;
            margin-bottom: 20px;
            flex-wrap: wrap;
            justify-content: center;
        }

        .filter-select {
            padding: 8px;
            border-radius: 5px;
            border: none;
            background: rgba(255, 255, 255, 0.9);
            color: #333;
        }

        /* Nueva sección: Quiz Interactivo */
        .quiz-container {
            max-width: 600px;
            margin: 0 auto;
        }

        .quiz-question {
            font-size: 1.2rem;
            margin-bottom: 20px;
            text-align: left;
        }

        .quiz-options {
            display: grid;
            gap: 10px;
            margin-bottom: 20px;
        }

        .quiz-option {
            padding: 12px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.2s;
        }

        body.light-mode .quiz-option {
            background: rgba(0, 0, 0, 0.05);
        }

        .quiz-option:hover {
            background: rgba(255, 255, 255, 0.2);
        }

        body.light-mode .quiz-option:hover {
            background: rgba(0, 0, 0, 0.1);
        }

        .quiz-score {
            font-size: 1.5rem;
            color: #00ff00;
            margin-top: 20px;
        }

        /* Estilos para el calendario astronómico */
        .calendar-section {
            background: rgba(18, 18, 51, 0.8);
            padding: 20px;
            border-radius: 20px;
            margin: 30px 0;
            box-shadow: 0 0 25px rgba(0, 243, 255, 0.4);
            border: 1px solid #00f3ff;
            backdrop-filter: blur(10px);
            width: 100%;
            max-width: 800px;
            text-align: left;
        }

        body.light-mode .calendar-section {
            background: rgba(255, 255, 255, 0.8);
            border-color: #00bfff;
        }

        .calendar-section h2 {
            color: #00f3ff;
            text-shadow: 0 0 10px #00f3ff;
            text-align: center;
            margin-bottom: 20px;
        }

        .calendar-search {
            margin-bottom: 20px;
            display: flex;
            justify-content: center;
        }

        #monthSearch {
            padding: 10px 15px;
            border-radius: 25px;
            border: none;
            font-size: 1rem;
            outline: none;
            background: rgba(255, 255, 255, 0.9);
            color: #333;
            width: 300px;
        }

        .month {
            margin-bottom: 20px;
            padding: 15px;
            background: rgba(255, 255, 255, 0.05);
            border-radius: 10px;
            border-left: 3px solid #00f3ff;
            display: none;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        body.light-mode .month {
            background: rgba(0, 0, 0, 0.03);
            border-left-color: #00bfff;
        }

        .month.visible {
            display: block;
        }

        .month h3 {
            color: #ffc837;
            margin-bottom: 10px;
            text-align: center;
            cursor: pointer;
        }

        body.light-mode .month h3 {
            color: #ff9800;
        }

        .month ul {
            list-style-type: none;
            padding: 0;
            display: none; /* Inicialmente oculto */
        }

        .month.active ul {
            display: block; /* Mostrar al activar */
        }

        .month li {
            padding: 5px 0;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
        }

        body.light-mode .month li {
            border-bottom-color: rgba(0, 0, 0, 0.1);
        }

        .month li:last-child {
            border-bottom: none;
        }

        /* Estilos para la sección de países */
        .country-header {
            padding: 30px 20px;
            background: rgba(18, 51, 18, 0.8);
            border-radius: 20px;
            margin-bottom: 30px;
            box-shadow: 0 0 25px rgba(0, 255, 0, 0.4);
            border: 1px solid #00ff00;
            backdrop-filter: blur(10px);
            width: 100%;
            max-width: 800px;
        }

        body.light-mode .country-header {
            background: rgba(255, 255, 255, 0.8);
            border-color: #00cc00;
        }

        .country-header h2 {
            color: #00ff00;
            text-shadow: 0 0 10px #00ff00;
            margin-bottom: 10px;
            font-size: 2.5rem;
        }

        .country-subtitle {
            color: #00ff00;
            font-size: 1.2rem;
            margin-bottom: 15px;
        }

        .country-info-card {
            background: rgba(0, 255, 0, 0.15);
            padding: 20px;
            border-radius: 12px;
            border-left: 4px solid #00ff00;
            transition: all 0.3s;
            backdrop-filter: blur(5px);
        }

        body.light-mode .country-info-card {
            background: rgba(0, 255, 0, 0.1);
        }

        .country-info-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 5px 15px rgba(0, 255, 0, 0.3);
        }

        .country-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 25px;
            margin-bottom: 25px;
        }

        .country-dato h4 {
            margin-top: 0;
            color: #00ff00;
            font-size: 1.25rem;
            margin-bottom: 12px;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        /* Estilos responsivos */
        @media (max-width: 768px) {
            .header-main {
                flex-direction: column;
                gap: 10px;
            }

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

            .animal-details, .country-details {
                grid-template-columns: 1fr;
            }

            .filter-container {
                flex-direction: column;
                align-items: center;
            }

            .calendar-search {
                flex-direction: column;
                align-items: center;
            }

            #monthSearch {
                width: 100%;
            }

            .country-grid {
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

            #animalSearch, #countrySearch {
                width: 100%;
            }
        }

        /* Posiciones iniciales de planetas (ajustadas para órbitas) */
        .planet-mercurio { width: 15px; height: 15px; background: #a5a5a5; }
        .planet-venus { width: 20px; height: 20px; background: #e6bb6d; }
        .planet-tierra { width: 22px; height: 22px; background: #2f6aae; }
        .planet-marte { width: 18px; height: 18px; background: #c1440e; }
        .planet-jupiter { width: 40px; height: 40px; background: #d8ca9d; }
        .planet-saturno { width: 35px; height: 35px; background: #e3d8b0; }
        .planet-urano { width: 25px; height: 25px; background: #b3e3e3; }
        .planet-neptuno { width: 25px; height: 25px; background: #3454df; }
    </style>
</head>

<body>
    <div class="main-container">
        <div class="header-main">
            <div>
                <h1>MultiÁrea Digital 4.0</h1>
                <p>Explora, descubre y aprende con nuestras herramientas mejoradas</p>
            </div>
            <button class="mode-toggle" onclick="toggleMode()" aria-label="Cambiar modo claro/oscuro">
                <i class="fas fa-moon"></i>
            </button>
        </div>

        <div class="tab-menu" role="tablist">
            <button class="tab-button active" data-tab="animales" aria-label="Identificador de Animales" onclick="showSection('animales')">Identificador de Animales</button>
            <button class="tab-button" data-tab="espacio" aria-label="Explorador del Sistema Solar" onclick="showSection('espacio')">Explorador del Sistema Solar</button>
            <button class="tab-button" data-tab="calendario" aria-label="Calendario Astronómico" onclick="showSection('calendario')">Calendario Astronómico</button>
            <button class="tab-button" data-tab="paises" aria-label="Investigador de Países" onclick="showSection('paises')">Investigador de Países</button>
            <button class="tab-button" data-tab="quiz" aria-label="Quiz Interactivo" onclick="showSection('quiz')">Quiz Interactivo</button>
        </div>

        <div id="animales" class="content-section active" role="tabpanel">
            <h1>Identificador de Animales</h1>
            <div class="authors">Por Rodrigo Mesis, Carlos Mendoza y Ariel Flores</div>

            <div class="filter-container">
                <select id="filterClasificacion" class="filter-select" onchange="applyFilters()">
                    <option value="">Filtrar por Clasificación</option>
                    <option value="Mamífero">Mamífero</option>
                    <option value="Reptil">Reptil</option>
                    <option value="Ave">Ave</option>
                    <option value="Anfibio">Anfibio</option>
                    <option value="Pez">Pez</option>
                    <option value="Insecto">Insecto</option>
                </select>
                <select id="filterHabitat" class="filter-select" onchange="applyFilters()">
                    <option value="">Filtrar por Hábitat</option>
                    <option value="Global">Global</option>
                    <option value="África">África</option>
                    <option value="América">América</option>
                    <option value="Asia">Asia</option>
                    <option value="Australia">Australia</option>
                    <option value="Océanos">Océanos</option>
                </select>
            </div>

            <div class="search-container">
                <input type="text" id="animalSearch" placeholder="Buscar animal por nombre..." aria-label="Buscar animal">
                <button id="searchButton" aria-label="Buscar">Buscar</button>
            </div>
            <div id="searchResults" class="search-results" role="listbox"></div>

            <div id="result"></div>
        </div>

        <div id="espacio" class="content-section" role="tabpanel">
            <div class="space-header">
                <h2>Explorador del Sistema Solar</h2>
                <p class="space-subtitle">DESCUBRE LOS PLANETAS DE NUESTRO SISTEMA SOLAR</p>
                <p>Creado por <strong>Carlos Mendoza</strong> y <strong>Rodrigo Mesis</strong> 
            </div>

            <div class="solar-system">
                <div class="sun" title="El Sol: Una estrella de tipo G2V, con una masa 333,000 veces la de la Tierra. Temperatura superficial: ~5,500°C. Diámetro: 1.39 millones km.">
                    ☀️
                </div>
                <div class="orbit orbit-mercurio"></div>
                <div class="planet-space planet-mercurio" onclick="mostrarInfoPlaneta('mercurio')" aria-label="Mercurio">
                    <!-- Sin lunas conocidas -->
                </div>
                <div class="orbit orbit-venus"></div>
                <div class="planet-space planet-venus" onclick="mostrarInfoPlaneta('venus')" aria-label="Venus">
                    <!-- Sin lunas conocidas -->
                </div>
                <div class="orbit orbit-tierra"></div>
                <div class="planet-space planet-tierra" onclick="mostrarInfoPlaneta('tierra')" aria-label="Tierra">
                    <div class="moon-orbit" style="width: 30px; height: 30px;"></div>
                    <div class="moon" style="background: #ddd;"></div> <!-- Luna -->
                </div>
                <div class="orbit orbit-marte"></div>
                <div class="planet-space planet-marte" onclick="mostrarInfoPlaneta('marte')" aria-label="Marte">
                    <div class="moon-orbit" style="width: 25px; height: 25px;"></div>
                    <div class="moon" style="background: #ccc;"></div> <!-- Fobos -->
                    <div class="moon-orbit" style="width: 35px; height: 35px;"></div>
                    <div class="moon" style="background: #aaa;"></div> <!-- Deimos -->
                </div>
                <div class="orbit orbit-jupiter"></div>
                <div class="planet-space planet-jupiter" onclick="mostrarInfoPlaneta('jupiter')" aria-label="Júpiter">
                    <div class="moon-orbit" style="width: 15px; height: 15px;"></div>
                    <div class="moon" style="background: #fff;"></div> <!-- Io (representativa) -->
                    <div class="moon-orbit" style="width: 25px; height: 25px;"></div>
                    <div class="moon" style="background: #eee;"></div> <!-- Europa -->
                </div>
                <div class="orbit orbit-saturno"></div>
                <div class="planet-space planet-saturno" onclick="mostrarInfoPlaneta('saturno')" aria-label="Saturno">
                    <div class="moon-orbit" style="width: 20px; height: 20px;"></div>
                    <div class="moon" style="background: #ddd;"></div> <!-- Titán -->
                    <div class="moon-orbit" style="width: 30px; height: 30px;"></div>
                    <div class="moon" style="background: #ccc;"></div> <!-- Rea -->
                </div>
                <div class="orbit orbit-urano"></div>
                <div class="planet-space planet-urano" onclick="mostrarInfoPlaneta('urano')" aria-label="Urano">
                    <div class="moon-orbit" style="width: 18px; height: 18px;"></div>
                    <div class="moon" style="background: #b3e3e3;"></div> <!-- Miranda -->
                </div>
                <div class="orbit orbit-neptuno"></div>
                <div class="planet-space planet-neptuno" onclick="mostrarInfoPlaneta('neptuno')" aria-label="Neptuno">
                    <div class="moon-orbit" style="width: 22px; height: 22px;"></div>
                    <div class="moon" style="background: #3454df;"></div> <!-- Tritón -->
                </div>
            </div>

            <div class="planetas-grid">
                <button class="planeta-btn" onclick="mostrarInfoPlaneta('mercurio')" aria-label="Información de Mercurio">
                    <div class="planet-icon" style="color: #a5a5a5;"><i class="fas fa-temperature-full"></i></div>
                    <div class="planeta-nombre">Mercurio</div>
                </button>
                <button class="planeta-btn" onclick="mostrarInfoPlaneta('venus')" aria-label="Información de Venus">
                    <div class="planet-icon" style="color: #e6bb6d;"><i class="fas fa-fire"></i></div>
                    <div class="planeta-nombre">Venus</div>
                </button>
                <button class="planeta-btn" onclick="mostrarInfoPlaneta('tierra')" aria-label="Información de Tierra">
                    <div class="planet-icon" style="color: #2f6aae;"><i class="fas fa-globe-americas"></i></div>
                    <div class="planeta-nombre">Tierra</div>
                </button>
                <button class="planeta-btn" onclick="mostrarInfoPlaneta('marte')" aria-label="Información de Marte">
                    <div class="planet-icon" style="color: #c1440e;"><i class="fas fa-mountain"></i></div>
                    <div class="planeta-nombre">Marte</div>
                </button>
                <button class="planeta-btn" onclick="mostrarInfoPlaneta('jupiter')" aria-label="Información de Júpiter">
                    <div class="planet-icon" style="color: #d8ca9d;"><i class="fas fa-wind"></i></div>
                    <div class="planeta-nombre">Júpiter</div>
                </button>
                <button class="planeta-btn" onclick="mostrarInfoPlaneta('saturno')" aria-label="Información de Saturno">
                    <div class="planet-icon" style="color: #e3d8b0;"><i class="fas fa-ring"></i></div>
                    <div class="planeta-nombre">Saturno</div>
                </button>
                <button class="planeta-btn" onclick="mostrarInfoPlaneta('urano')" aria-label="Información de Urano">
                    <div class="planet-icon" style="color: #b3e3e3;"><i class="fas fa-icicles"></i></div>
                    <div class="planeta-nombre">Urano</div>
                </button>
                <button class="planeta-btn" onclick="mostrarInfoPlaneta('neptuno')" aria-label="Información de Neptuno">
                    <div class="planet-icon" style="color: #3454df;"><i class="fas fa-wind"></i></div>
                    <div class="planeta-nombre">Neptuno</div>
                </button>

            </div>

            <div id="info-planeta" class="space-info">
                <h3>Bienvenido al Explorador del Sistema Solar</h3>
                <p class="descripcion">Selecciona un planeta para conocer información detallada sobre él, incluyendo su tamaño, composición, características únicas y datos curiosos. ¡Ahora con animaciones orbitales en tiempo real!</p>
            </div>
        </div>

        <div id="calendario" class="content-section" role="tabpanel">
            <h1>Calendario Astronómico y Lunar</h1>
            <div class="calendar-section">
                <h2><i class="fas fa-calendar-alt"></i> Calendario Astronómico y Lunar (2025-2026)</h2>
                <p style="text-align: center; color: #b0b0b0;">Eventos principales, fases lunares, eclipses y lluvias de meteoros. Desde octubre 2025 hasta diciembre 2026.</p>
                <div class="calendar-search">
                    <input type="text" id="monthSearch" placeholder="Buscar mes (ej: Enero, Febrero)..." aria-label="Buscar mes">
                </div>
                <div class="month visible" data-month="octubre">
                    <h3 onclick="toggleMonth(this.parentElement)">Octubre 2025</h3>
                    <ul>
                        <li>6 de octubre: Luna cerca de Saturno y Neptuno</li>
                        <li>7 de octubre: Luna Llena (Superluna)</li>
                        <li>10 de octubre: Luna cerca de las Pléyades</li>
                        <li>13 de octubre: Luna cerca de Júpiter</li>
                        <li>19 de octubre: Luna cerca de Venus</li>
                        <li>19 de octubre: Conjunciòn Mercurio-Marte</li>
                        <li>20-21 de octubre: Pico de las Oriónidas (lluvia de meteoros)</li>
                        <li>21 de octubre: Luna Nueva</li>
                        <li>23 de octubre: Luna cerca de Marte y Mercurio</li>
                        <li>29 de octubre: Mercurio en mayor elongación este</li>
                    </ul>
                </div>
                <div class="month visible" data-month="noviembre">
                    <h3 onclick="toggleMonth(this.parentElement)">Noviembre 2025</h3>
                    <ul>
                        <li>2 de noviembre: Luna cerca de Saturno y Neptuno</li>
                        <li>4-5 de noviembre: Pico de las Táuridas del Sur (lluvia de meteoros)</li>
                        <li>5 de noviembre: Luna Llena (Superluna, la más grande del año)</li>
                        <li>6 de noviembre: Luna cerca de las Pléyades</li>
                        <li>10 de noviembre: Luna cerca de Júpiter</li>
                        <li>11-12 de noviembre: Pico de las Táuridas del Norte (lluvia de meteoros)</li>
                        <li>17-18 de noviembre: Pico de las Leónidas (lluvia de meteoros)</li>
                        <li>20 de noviembre: Luna Nueva</li>
                        <li>21 de noviembre: Urano en oposición</li>
                        <li>29 de noviembre: Luna cerca de Saturno</li>
                        <li>30 de noviembre: Luna cerca de Neptuno</li>
                    </ul>
                </div>
                <div class="month visible" data-month="diciembre">
                    <h3 onclick="toggleMonth(this.parentElement)">Diciembre 2025</h3>
                    <ul>
                        <li>4 de diciembre: Luna cerca de las Pléyades y Luna Llena (Superluna)</li>
                        <li>7 de diciembre: Mercurio en mayor elongación oeste; Luna cerca de Júpiter</li>
                        <li>13-14 de diciembre: Pico de las Gemínidas (lluvia de meteoros)</li>
                        <li>20 de diciembre: Luna Nueva</li>
                        <li>21 de diciembre: Solsticio de invierno</li>
                        <li>22-23 de diciembre: Pico de las Úrsidas (lluvia de meteoros)</li>
                        <li>27 de diciembre: Luna cerca de Saturno y Neptuno</li>
                        <li>31 de diciembre: Luna cerca de las Pléyades</li>
                    </ul>
                </div>
                <div class="month visible" data-month="enero">
                    <h3 onclick="toggleMonth(this.parentElement)">Enero 2026</h3>
                    <ul>
                        <li>3 de enero: Luna Llena (Luna de Lobo)</li>
                        <li>13 de enero: Cuarto menguante</li>
                        <li>18 de enero: Luna Nueva</li>
                        <li>25 de enero: Cuarto creciente</li>
                        <li>3 de enero: Pico de las Cuadrántidas (lluvia de meteoros)</li>
                    </ul>
                </div>
                <div class="month visible" data-month="febrero">
                    <h3 onclick="toggleMonth(this.parentElement)">Febrero 2026</h3>
                    <ul>
                        <li>1 de febrero: Luna Llena (Luna de Nieve)</li>
                        <li>9 de febrero: Cuarto menguante</li>
                        <li>17 de febrero: Luna Nueva y Eclipse solar anular (visible en Antártida, parcial en Argentina, Chile y África)</li>
                        <li>24 de febrero: Cuarto creciente</li>
                    </ul>
                </div>
                <div class="month visible" data-month="marzo">
                    <h3 onclick="toggleMonth(this.parentElement)">Marzo 2026</h3>
                    <ul>
                        <li>3 de marzo: Luna Llena y Eclipse lunar total (visible en Asia, Australia, Pacífico y América)</li>
                        <li>11 de marzo: Cuarto menguante</li>
                        <li>19 de marzo: Luna Nueva</li>
                        <li>25 de marzo: Cuarto creciente</li>
                        <li>20 de marzo: Equinoccio de primavera</li>
                    </ul>
                </div>
                <div class="month visible" data-month="abril">
                    <h3 onclick="toggleMonth(this.parentElement)">Abril 2026</h3>
                    <ul>
                        <li>2 de abril: Luna Llena (Luna Rosa)</li>
                        <li>10 de abril: Cuarto menguante</li>
                        <li>17 de abril: Luna Nueva</li>
                        <li>26 de abril: Cuarto creciente</li>
                        <li>22 de abril: Pico de las Líridas (lluvia de meteoros)</li>
                    </ul>
                </div>
                <div class="month visible" data-month="mayo">
                    <h3 onclick="toggleMonth(this.parentElement)">Mayo 2026</h3>
                    <ul>
                        <li>1 de mayo: Luna Llena (Luna de las Flores)</li>
                        <li>9 de mayo: Cuarto menguante</li>
                        <li>16 de mayo: Luna Nueva</li>
                        <li>24 de mayo: Cuarto creciente</li>
                        <li>5-6 de mayo: Pico de las Eta Acuáridas (lluvia de meteoros)</li>
                    </ul>
                </div>
                <div class="month visible" data-month="junio">
                    <h3 onclick="toggleMonth(this.parentElement)">Junio 2026</h3>
                    <ul>
                        <li>30 de junio: Luna Llena (Luna de Fresa)</li>
                        <li>8 de junio: Cuarto menguante</li>
                        <li>15 de junio: Luna Nueva</li>
                        <li>22 de junio: Cuarto creciente</li>
                        <li>21 de junio: Solsticio de verano</li>
                    </ul>
                </div>
                <div class="month visible" data-month="julio">
                    <h3 onclick="toggleMonth(this.parentElement)">Julio 2026</h3>
                    <ul>
                        <li>29 de julio: Luna Llena (Luna de Ciervo)</li>
                        <li>7 de julio: Cuarto menguante</li>
                        <li>14 de julio: Luna Nueva</li>
                        <li>21 de julio: Cuarto creciente</li>
                        <li>28-29 de julio: Pico de las Delta Acuáridas (lluvia de meteoros)</li>
                    </ul>
                </div>
                <div class="month visible" data-month="agosto">
                    <h3 onclick="toggleMonth(this.parentElement)">Agosto 2026</h3>
                    <ul>
                        <li>28 de agosto: Luna Llena y Eclipse lunar parcial (visible en Pacífico, América, Europa y África)</li>
                        <li>6 de agosto: Cuarto menguante</li>
                        <li>12 de agosto: Luna Nueva y Eclipse solar total (visible en Ártico, Groenlandia, Islandia y España)</li>
                        <li>19 de agosto: Cuarto creciente</li>
                        <li>12-13 de agosto: Pico de las Perseidas (lluvia de meteoros)</li>
                    </ul>
                </div>
                <div class="month visible" data-month="septiembre">
                    <h3 onclick="toggleMonth(this.parentElement)">Septiembre 2026</h3>
                    <ul>
                        <li>26 de septiembre: Luna Llena (Luna de Maíz)</li>
                        <li>4 de septiembre: Cuarto menguante</li>
                        <li>11 de septiembre: Luna Nueva</li>
                        <li>18 de septiembre: Cuarto creciente</li>
                        <li>22 de septiembre: Equinoccio de otoño</li>
                    </ul>
                </div>
                <div class="month visible" data-month="octubre">
                    <h3 onclick="toggleMonth(this.parentElement)">Octubre 2026</h3>
                    <ul>
                        <li>26 de octubre: Luna Llena (Luna de Cazador)</li>
                        <li>3 de octubre: Cuarto menguante</li>
                        <li>10 de octubre: Luna Nueva</li>
                        <li>18 de octubre: Cuarto creciente</li>
                        <li>20-21 de octubre: Pico de las Oriónidas (lluvia de meteoros)</li>
                    </ul>
                </div>
                <div class="month visible" data-month="noviembre">
                    <h3 onclick="toggleMonth(this.parentElement)">Noviembre 2026</h3>
                    <ul>
                        <li>24 de noviembre: Luna Llena (Luna del Castor, Superluna)</li>
                        <li>2 de noviembre: Cuarto menguante</li>
                        <li>9 de noviembre: Luna Nueva</li>
                        <li>17 de noviembre: Cuarto creciente</li>
                        <li>17-18 de noviembre: Pico de las Leónidas (lluvia de meteoros)</li>
                    </ul>
                </div>
                <div class="month visible" data-month="diciembre">
                    <h3 onclick="toggleMonth(this.parentElement)">Diciembre 2026</h3>
                    <ul>
                        <li>24 de diciembre: Luna Llena (Luna Fría, Superluna)</li>
                        <li>1 de diciembre: Cuarto menguante</li>
                        <li>8 de diciembre: Luna Nueva</li>
                        <li>16 de diciembre: Cuarto creciente</li>
                        <li>13-14 de diciembre: Pico de las Gemínidas (lluvia de meteoros)</li>
                        <li>21 de diciembre: Solsticio de invierno</li>
                    </ul>
                </div>
            </div>
        </div>

        <div id="paises" class="content-section" role="tabpanel">
            <h1>Investigador de Países</h1>
            <div class="authors">Por el equipo de MultiÁrea Digital</div>

            <div class="filter-container">
                <select id="filterContinente" class="filter-select" onchange="applyCountryFilters()">
                    <option value="">Filtrar por Continente</option>
                    <option value="América">América</option>
                    <option value="Europa">Europa</option>
                    <option value="África">África</option>
                    <option value="Asia">Asia</option>
                    <option value="Oceanía">Oceanía</option>
                </select>
            </div>

            <div class="country-header">
                <h2>Explorador de Países del Mundo</h2>
                <p class="country-subtitle">DESCUBRE INFORMACIÓN DETALLADA SOBRE PAÍSES, SUS CULTURAS Y GEOGRAFÍA</p>
            </div>

            <div class="search-container">
                <input type="text" id="countrySearch" placeholder="Buscar país por nombre..." aria-label="Buscar país">
                <button id="countrySearchButton" aria-label="Buscar">Buscar</button>
            </div>
            <div id="countrySearchResults" class="search-results" role="listbox"></div>

            <div id="countryResult"></div>
        </div>

        <div id="quiz" class="content-section" role="tabpanel">
            <h1>Quiz Interactivo</h1>
            <div class="authors">Nueva función en 3.0: ¡Prueba tus conocimientos!</div>
            <div class="quiz-container">
                <div class="filter-container">
                    <select id="quizCategory" class="filter-select">
                        <option value="">Selecciona una categoría</option>
                        <option value="animales">Animales</option>
                        <option value="espacio">Espacio</option>
                        <option value="paises">Países</option>
                    </select>
                </div>
                <div class="search-container">
                    <button id="startQuiz" onclick="startQuiz()">Iniciar Quiz</button>
                </div>
                <div id="quizResult"></div>
            </div>
        </div>
    </div>

    <script>
        const sections = ['animales', 'espacio', 'calendario', 'paises', 'quiz'];
        const tabButtons = document.querySelectorAll('.tab-button');
        const animalSearch = document.getElementById('animalSearch');
        const searchButton = document.getElementById('searchButton');
        const searchResults = document.getElementById('searchResults');
        const resultDiv = document.getElementById('result');
        const monthSearch = document.getElementById('monthSearch');
        const countrySearch = document.getElementById('countrySearch');
        const countrySearchButton = document.getElementById('countrySearchButton');
        const countrySearchResults = document.getElementById('countrySearchResults');
        const countryResultDiv = document.getElementById('countryResult');
        const quizCategory = document.getElementById('quizCategory');
        const quizResultDiv = document.getElementById('quizResult');

        // Base de datos expandida de animales (agregados más animales: gato, oso, pinguino, delfin, mariposa, arana, tortuga, loro, ballena, zorro)
        const animalDatabase = {
            "perro": {
                nombre: "Perro (Canis lupus familiaris)",
                tipo: "Mamífero doméstico",
                info: "El perro es un mamífero carnívoro de la familia de los cánidos. Es una subespecie del lobo y fue el primer animal domesticado por el ser humano. Se utiliza como animal de compañía, de trabajo, para caza, y como perro guía o de rescate.",
                alimentacion: "Omnívoro",
                clasificacion: "Mamífero",
                clasificacion_zootecnica: "canino",
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
            "leon": {
                nombre: "León (Panthera leo)",
                tipo: "Mamífero salvaje",
                info: "El león es un mamífero carnívoro de la familia Felidae, conocido como el 'rey de la selva'. Vive en manadas en las sabanas africanas y es el único felino social.",
                alimentacion: "Carnívoro",
                clasificacion: "Mamífero",
                clasificacion_zootecnica: "Felino",
                habitat: "África (sabanas y praderas)",
                caracteristicas: "Macho con melena, fuerte, veloz hasta 80 km/h.",
                curiosidades: "Las leonas cazan el 90% de la comida. Un rugido se oye a 8 km.",
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
            "elefante": {
                nombre: "Elefante africano (Loxodonta africana)",
                tipo: "Mamífero herbívoro",
                info: "El elefante africano es el mamífero terrestre más grande del mundo, conocido por su trompa, colmillos y memoria excepcional. Vive en manadas lideradas por hembras.",
                alimentacion: "Herbívoro",
                clasificacion: "Mamífero",
                habitat: "África (sabanas, bosques)",
                caracteristicas: "Trompa versátil, orejas grandes para disipar calor, hasta 6 toneladas.",
                curiosidades: "Usan la trompa como nariz y mano. Nunca olvidan rutas migratorias.",
                esperanza_vida: "60-70 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "En peligro",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Proboscidea",
                    familia: "Elephantidae",
                    genero: "Loxodonta",
                    especie: "L. africana"
                }
            },
            "jirafa": {
                nombre: "Jirafa (Giraffa camelopardalis)",
                tipo: "Mamífero herbívoro",
                info: "La jirafa es el animal más alto del mundo, con un cuello largo para alcanzar hojas altas. Vive en grupos en las sabanas africanas.",
                alimentacion: "Herbívoro",
                clasificacion: "Mamífero",
                habitat: "África (sabanas)",
                caracteristicas: "Cuello de 1.8 m, lengua azul de 50 cm, visión excelente.",
                curiosidades: "Corazón pesa 11 kg. Duermen solo 30 minutos al día.",
                esperanza_vida: "10-15 años en salvaje",
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
            "cocodrilo": {
                nombre: "Cocodrilo del Nilo (Crocodylus niloticus)",
                tipo: "Reptil carnívoro",
                info: "El cocodrilo del Nilo es un reptil semiacuático, uno de los depredadores más grandes y antiguos, con mordida de 5,000 psi.",
                alimentacion: "Carnívoro",
                clasificacion: "Reptil",
                habitat: "África (ríos, lagos)",
                caracteristicas: "Piel escamosa, 4-5 m de largo, emboscadas.",
                curiosidades: "Pueden vivir 100 años. Lágrimas de cocodrilo son reales por glándulas salinas.",
                esperanza_vida: "45-75 años",
                esqueleto: "Vertebrado",
                reproduccion: "Oviparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Reptilia",
                    orden: "Crocodilia",
                    familia: "Crocodylidae",
                    genero: "Crocodylus",
                    especie: "C. niloticus"
                }
            },
            "serpiente": {
                nombre: "Serpiente de cascabel (Crotalus atrox)",
                tipo: "Reptil venenoso",
                info: "La serpiente de cascabel es un reptil venenoso conocido por su sonajero en la cola, usado para advertir. Caza por emboscada.",
                alimentacion: "Carnívoro",
                clasificacion: "Reptil",
                habitat: "América (desiertos, praderas)",
                caracteristicas: "Sin patas, veneno hemotóxico, muda piel.",
                curiosidades: "Sonajero crece con cada muda. Detectan calor infrarrojo.",
                esperanza_vida: "10-25 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovovivíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Reptilia",
                    orden: "Squamata",
                    familia: "Viperidae",
                    genero: "Crotalus",
                    especie: "C. atrox"
                }
            },
            "aguila": {
                nombre: "Águila real (Aquila chrysaetos)",
                tipo: "Ave rapaz",
                info: "El águila real es una de las aves de presa más grandes y poderosas, conocida por su visión aguda y fuerza en el vuelo.",
                alimentacion: "Carnívoro",
                clasificacion: "Ave",
                habitat: "Global (montañas y praderas)",
                caracteristicas: "Visión 8 veces superior a la humana, alas de 2 m de envergadura.",
                curiosidades: "Puede cazar presas hasta 4 veces su peso. Simboliza poder en muchas culturas.",
                esperanza_vida: "20-30 años",
                esqueleto: "Vertebrado",
                reproduccion: "Oviparo",
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
            "halcon": {
                nombre: "Halcón peregrino (Falco peregrinus)",
                tipo: "Ave rapaz",
                info: "El halcón peregrino es la ave más rápida del mundo, alcanzando 389 km/h en picada. Es un cazador diurno experto.",
                alimentacion: "Carnívoro",
                clasificacion: "Ave",
                habitat: "Global (acantilados, ciudades)",
                caracteristicas: "Picada supersónica, garras afiladas, visión binocular.",
                curiosidades: "Casi extinto por pesticidas, recuperado. Usado en cetrería por milenios.",
                esperanza_vida: "10-15 años",
                esqueleto: "Vertebrado",
                reproduccion: "Oviparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Falconiformes",
                    familia: "Falconidae",
                    genero: "Falco",
                    especie: "F. peregrinus"
                }
            },
            "rana": {
                nombre: "Rana común (Rana temporaria)",
                tipo: "Anfibio",
                info: "Las ranas son anfibios que pasan parte de su vida en agua y tierra, caracterizadas por su salto y piel húmeda.",
                alimentacion: "Carnívoro",
                clasificacion: "Anfibio",
                habitat: "Global (humedales y bosques)",
                caracteristicas: "Piel permeable, lengua pegajosa, salto hasta 10 veces su longitud.",
                curiosidades: "Cambian de color para camuflaje. Algunas especies son venenosas.",
                esperanza_vida: "5-10 años",
                esqueleto: "Vertebrado",
                reproduccion: "Oviparo",
                conservacion: "Vulnerable en algunas especies",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Amphibia",
                    orden: "Anura",
                    familia: "Ranidae",
                    genero: "Rana",
                    especie: "R. temporaria"
                }
            },
            "salamandra": {
                nombre: "Salamandra de fuego (Salamandra salamandra)",
                tipo: "Anfibio",
                info: "La salamandra de fuego es un anfibio nocturno con piel negra y manchas amarillas tóxicas, que vive en bosques húmedos europeos.",
                alimentacion: "Carnívoro",
                clasificacion: "Anfibio",
                habitat: "Europa (bosques húmedos)",
                caracteristicas: "Regeneración de extremidades, veneno en piel, respiración cutánea.",
                curiosidades: "Mito de fuego por color. Pueden vivir sin comer meses.",
                esperanza_vida: "10-20 años",
                esqueleto: "Vertebrado",
                reproduccion: "Ovovivíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Amphibia",
                    orden: "Urodela",
                    familia: "Salamandridae",
                    genero: "Salamandra",
                    especie: "S. salamandra"
                }
            },
            "tiburon": {
                nombre: "Tiburón blanco (Carcharodon carcharias)",
                tipo: "Pez cartilaginoso",
                info: "El tiburón blanco es un depredador ápice de los océanos, conocido por su tamaño y mandíbulas poderosas.",
                alimentacion: "Carnívoro",
                clasificacion: "Pez",
                habitat: "Océanos (costeros templados)",
                caracteristicas: "Dientes serrados, sentido electroreceptivo, hasta 6 m de largo.",
                curiosidades: "No muerden por maldad; prueban presas. Regeneran dientes continuamente.",
                esperanza_vida: "70 años",
                esqueleto: "Cartilaginoso",
                reproduccion: "Vivíparo",
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
            "salmón": {
                nombre: "Salmón atlántico (Salmo salar)",
                tipo: "Pez migratorio",
                info: "El salmón atlántico es un pez anádromo que migra de océano a río para reproducirse, rico en omega-3.",
                alimentacion: "Omnívoro",
                clasificacion: "Pez",
                habitat: "Océanos y ríos Atlántico Norte",
                caracteristicas: "Escamas, aleta dorsal, salto de cascadas.",
                curiosidades: "Nadan 1,500 km río arriba. Cambian color al madurar.",
                esperanza_vida: "5-7 años",
                esqueleto: "Óseo",
                reproduccion: "Oviparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Actinopterygii",
                    orden: "Salmoniformes",
                    familia: "Salmonidae",
                    genero: "Salmo",
                    especie: "S. salar"
                }
            },
            "hormiga": {
                nombre: "Hormiga argentina (Linepithema humile)",
                tipo: "Insecto social",
                info: "La hormiga argentina es una especie invasora altamente agresiva, formando supercolonias que desplazan especies nativas.",
                alimentacion: "Omnívoro",
                clasificacion: "Insecto",
                habitat: "Global (invasiva)",
                caracteristicas: "Colonia masiva, sin reina dominante, feromonas potentes.",
                curiosidades: "Supercolonia en Europa de 33 millones km². Levantan 50 veces su peso.",
                esperanza_vida: "1-3 años (reina)",
                esqueleto: "Exoesqueleto",
                reproduccion: "Oviparo",
                conservacion: "Invasiva",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Arthropoda",
                    clase: "Insecta",
                    orden: "Hymenoptera",
                    familia: "Formicidae",
                    genero: "Linepithema",
                    especie: "L. humile"
                }
            },
            "abeja": {
                nombre: "Abeja melífera (Apis mellifera)",
                tipo: "Insecto polinizador",
                info: "La abeja melífera es clave para la polinización, produciendo miel y viviendo en colonias con roles especializados.",
                alimentacion: "Herbívoro (néctar, polen)",
                clasificacion: "Insecto",
                habitat: "Global (colmenas)",
                caracteristicas: "Danza de comunicación, aguijón defensivo, ojos compuestos.",
                curiosidades: "Una colmena produce 500 g miel/semana. Polinizan 1/3 alimentos humanos.",
                esperanza_vida: "6 semanas (obrera)",
                esqueleto: "Exoesqueleto",
                reproduccion: "Oviparo",
                conservacion: "En declive por pesticidas",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Arthropoda",
                    clase: "Insecta",
                    orden: "Hymenoptera",
                    familia: "Apidae",
                    genero: "Apis",
                    especie: "A. mellifera"
                }
            },
            "tigre": {
                nombre: "Tigre (Panthera tigris)",
                tipo: "Mamífero carnívoro",
                info: "El tigre es el felino más grande, solitario y territorial, con rayas para camuflaje en junglas.",
                alimentacion: "Carnívoro",
                clasificacion: "Mamífero",
                clasificacion_zootecnica: "felino",
                habitat: "Asia (junglas, manglares)",
                caracteristicas: "Natación experta, rugido a 3 km, hasta 300 kg.",
                curiosidades: "Impronta lengua áspera para acicalarse. Subespecies como siberiano.",
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
            "gato": {
                nombre: "Gato (Felis catus)",
                tipo: "Mamífero doméstico",
                info: "El gato es un mamífero carnívoro de la familia Felidae, domesticado desde el antiguo Egipto. Es conocido por su independencia y agilidad.",
                alimentacion: "Carnívoro",
                clasificacion: "Mamífero",
                clasificacion_zootecnica: "felino",
                habitat: "Global (domesticado)",
                caracteristicas: "Visión nocturna, bigotes sensoriales, aterrizaje en patas.",
                curiosidades: "Duermen 16 horas al día. Ronroneo cura huesos.",
                esperanza_vida: "12-15 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Domesticado",
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
            "oso": {
                nombre: "Oso pardo (Ursus arctos)",
                tipo: "Mamífero omnívoro",
                info: "El oso pardo es un gran mamífero omnívoro, hibernador en invierno, con gran fuerza y olfato.",
                alimentacion: "Omnívoro",
                clasificacion: "Mamífero",
                habitat: "América, Europa, Asia (bosques)",
                caracteristicas: "Hasta 3 m de pie, garras largas, hibernación.",
                curiosidades: "Pueden correr 56 km/h. Simbolizan fuerza en culturas.",
                esperanza_vida: "20-30 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Carnivora",
                    familia: "Ursidae",
                    genero: "Ursus",
                    especie: "U. arctos"
                }
            },
            "pinguino": {
                nombre: "Pingüino emperador (Aptenodytes forsteri)",
                tipo: "Ave no voladora",
                info: "El pingüino emperador es la ave más grande no voladora, adaptada al frío extremo de la Antártida.",
                alimentacion: "Carnívoro",
                clasificacion: "Ave",
                habitat: "Antártida (hielo marino)",
                caracteristicas: "Plumaje impermeable, natación hasta 30 km/h, huddle para calor.",
                curiosidades: "Machos incuban huevos en pies. Bucean 500 m.",
                esperanza_vida: "15-20 años",
                esqueleto: "Vertebrado",
                reproduccion: "Oviparo",
                conservacion: "Casi amenazada",
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
            "delfin": {
                nombre: "Delfín nariz de botella (Tursiops truncatus)",
                tipo: "Mamífero acuático",
                info: "El delfín es un mamífero marino inteligente, social, con ecolocalización para cazar.",
                alimentacion: "Carnívoro",
                clasificacion: "Mamífero",
                habitat: "Océanos (costeros templados)",
                caracteristicas: "Aletas, sonar, saltos acrobáticos.",
                curiosidades: "Juegan con burbujas. Inteligencia comparable a primates.",
                esperanza_vida: "40-50 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Cetacea",
                    familia: "Delphinidae",
                    genero: "Tursiops",
                    especie: "T. truncatus"
                }
            },
            "mariposa": {
                nombre: "Mariposa monarca (Danaus plexippus)",
                tipo: "Insecto lepidóptero",
                info: "La mariposa monarca es conocida por su migración masiva y colores vibrantes.",
                alimentacion: "Herbívoro (néctar)",
                clasificacion: "Insecto",
                habitat: "América (bosques, praderas)",
                caracteristicas: "Alas naranjas con negro, metamorfosis completa.",
                curiosidades: "Migran 4,000 km. Tóxicas por plantas consumidas.",
                esperanza_vida: "2-6 semanas (adulto)",
                esqueleto: "Exoesqueleto",
                reproduccion: "Oviparo",
                conservacion: "Vulnerable",
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
            "araña": {
                nombre: "Araña lobo (Lycosa tarantula)",
                tipo: "Arácnido depredador",
                info: "La araña lobo es un arácnido cazador activo, sin tela, con veneno no letal para humanos.",
                alimentacion: "Carnívoro",
                clasificacion: "Arácnido",
                habitat: "Europa, África (suelos secos)",
                caracteristicas: "8 ojos, peluda, caza al acecho.",
                curiosidades: "Llevan crías en espalda. Visión nocturna.",
                esperanza_vida: "1-2 años",
                esqueleto: "Exoesqueleto",
                reproduccion: "Oviparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Arthropoda",
                    clase: "Arachnida",
                    orden: "Araneae",
                    familia: "Lycosidae",
                    genero: "Lycosa",
                    especie: "L. tarantula"
                }
            },
            "tortuga": {
                nombre: "Tortuga marina verde (Chelonia mydas)",
                tipo: "Reptil marino",
                info: "La tortuga marina verde es un reptil herbívoro que migra largas distancias para anidar.",
                alimentacion: "Herbívoro",
                clasificacion: "Reptil",
                habitat: "Océanos (trópicos)",
                caracteristicas: "Caparazón, aletas, longevidad.",
                curiosidades: "Determinan sexo por temperatura. Nadan 2,000 km.",
                esperanza_vida: "60-70 años",
                esqueleto: "Vertebrado",
                reproduccion: "Oviparo",
                conservacion: "En peligro",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Reptilia",
                    orden: "Testudines",
                    familia: "Cheloniidae",
                    genero: "Chelonia",
                    especie: "C. mydas"
                }
            },
            "loro": {
                nombre: "Loro gris africano (Psittacus erithacus)",
                tipo: "Ave parlante",
                info: "El loro gris africano es conocido por su inteligencia y capacidad para imitar el habla humana.",
                alimentacion: "Herbívoro",
                clasificacion: "Ave",
                habitat: "África (selvas)",
                caracteristicas: "Pico curvo, imitación vocal, social.",
                curiosidades: "Vocabulario hasta 1,000 palabras. Viven en parejas.",
                esperanza_vida: "50-60 años",
                esqueleto: "Vertebrado",
                reproduccion: "Oviparo",
                conservacion: "Vulnerable",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Psittaciformes",
                    familia: "Psittacidae",
                    genero: "Psittacus",
                    especie: "P. erithacus"
                }
            },
            "ballena": {
                nombre: "Ballena jorobada (Megaptera novaeangliae)",
                tipo: "Mamífero marino",
                info: "La ballena jorobada es conocida por sus cantos complejos y acrobacias en el agua.",
                alimentacion: "Carnívoro (krill)",
                clasificacion: "Mamífero",
                habitat: "Océanos (global)",
                caracteristicas: "Aletas pectorales largas, migraciones anuales.",
                curiosidades: "Cantos duran horas. Saltan fuera del agua (breaching).",
                esperanza_vida: "45-50 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Cetacea",
                    familia: "Balaenopteridae",
                    genero: "Megaptera",
                    especie: "M. novaeangliae"
                }
            },
            "zorro": {
                nombre: "Zorro rojo (Vulpes vulpes)",
                tipo: "Mamífero carnívoro",
                info: "El zorro rojo es un mamífero adaptable, conocido por su astucia en folclore.",
                alimentacion: "Omnívoro",
                clasificacion: "Mamífero",
                clasificacion_zootecnica: "canino",
                habitat: "Global (bosques, ciudades)",
                caracteristicas: "Cola espesa, orejas grandes, nocturno.",
                curiosidades: "Cazan solos. Adaptados a entornos urbanos.",
                esperanza_vida: "2-5 años salvaje",
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
                    especie: "V. vulpes"
                }
            },
            "cerdo": {
                nombre: "Cerdo doméstico (Sus scrofa domesticus)",
                tipo: "Mamífero doméstico",
                info: "El cerdo es un mamífero omnívoro domesticado por su carne y piel. Son inteligentes y sociales.",
                alimentacion: "Omnívoro",
                clasificacion: "Mamífero",
                clasificacion_zootecnica:  "porcina",
                habitat: "Global (domesticado)",
                caracteristicas: "Olfato agudo, hocico flexible, sociable.",
                curiosidades: "Pueden aprender trucos. Su piel se usa en cuero.",
                esperanza_vida: "10-15 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Domesticado",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Artiodactyla",
                    familia: "Suidae",
                    genero: "Sus",
                    especie: "S. scrofa domesticus"
                }
            },
            "Gallina": {
                nombre: "Gallina doméstica (Gallus gallus domesticus)",
                tipo: "Ave doméstica",
                info: "La gallina es un ave domesticada por su carne y huevos. Son sociales y tienen un comportamiento jerárquico.",
                alimentacion: "Omnívoro",
                clasificacion: "Ave",
                habitat: "Global (domesticado)",
                caracteristicas: "Plumas, pico corto, patas fuertes.",
                curiosidades: "Pueden recordar más de 100 caras. Ponen hasta 300 huevos/año.",
                esperanza_vida: "5-10 años",
                esqueleto: "Vertebrado",
                reproduccion: "Oviparo",
                conservacion: "Domesticado",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Galliformes",
                    familia: "Phasianidae",
                    genero: "Gallus",
                    especie: "G. gallus domesticus"
                }
            },
            "vaca": {
                nombre: "Vaca doméstica (Bos taurus)",
                tipo: "Mamífero doméstico",
                info: "La vaca es un mamífero herbívoro domesticado por su carne, leche y cuero. Son animales de pastoreo.",
                alimentacion: "Herbívoro",
                clasificacion: "Mamífero",
                clasificacion_zootecnica:  "bovina",
                habitat: "Global (domesticado)",
                caracteristicas: "Gran tamaño, rumiante, sociable.",
                curiosidades: "Tienen un estómago de 4 compartimentos. Pueden recordar ubicaciones de comida.",
                esperanza_vida: "15-20 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Domesticado",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Artiodactyla",
                    familia: "Bovidae",
                    genero: "Bos",
                    especie: "B. taurus"
                }
            },
            "Guarda barranco": {
                nombre: "Guarda barranco (Troglodytes aedon)",
                tipo: "Ave pequeña",
                info: "El guarda barranco es un ave pequeña y activa, conocida por su canto fuerte y melodioso.",
                alimentacion: "Omnívoro",
                clasificacion: "Ave",
                habitat: "América (bosques, jardines)",
                caracteristicas: "Plumas marrones, cola erguida, pico delgado.",
                curiosidades: "Puede cantar hasta 20 canciones diferentes. Construye nidos en lugares inusuales.",
                esperanza_vida: "2-3 años",
                esqueleto: "Vertebrado",
                reproduccion: "Oviparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Passeriformes",
                    familia: "Troglodytidae",
                    genero: "Troglodytes",
                    especie: "T. aedon"
                }
            },
            "tiburon de agua dulce": {
                nombre: "Tiburón de agua dulce (Glyphis glyphis)",
                tipo: "Pez cartilaginoso",
                info: "El tiburón de agua dulce es una especie rara que habita ríos y estuarios en el sudeste asiático y Australia.",
                alimentacion: "Carnívoro",
                clasificacion: "Pez",
                habitat: "Ríos y estuarios (sudeste asiático, Australia)",
                caracteristicas: "Cuerpo robusto, piel áspera, hasta 2 m de largo.",
                curiosidades: "Muy poco conocido, con avistamientos raros. Adaptado a agua dulce.",
                esperanza_vida: "Desconocida",
                esqueleto: "Cartilaginoso",
                reproduccion: "Vivíparo",
                conservacion: "En peligro crítico",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Chondrichthyes",
                    orden: "Carcharhiniformes",
                    familia: "Carcharhinidae",
                    genero: "Glyphis",
                    especie: "G. glyphis"
                }
            },
            "venado": {
                nombre: "Venado cola blanca (Odocoileus virginianus)",
                tipo: "Mamífero herbívoro",
                info: "El venado cola blanca es un mamífero herbívoro común en América, conocido por su agilidad y capacidad de camuflaje.",
                alimentacion: "Herbívoro",
                clasificacion: "Mamífero",
                habitat: "América (bosques, praderas)",
                caracteristicas: "Cola blanca, astas ramificadas, velocidad.",
                curiosidades: "Pueden correr hasta 48 km/h. Usan la cola para alertar a otros venados.",
                esperanza_vida: "6-14 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Artiodactyla",
                    familia: "Cervidae",
                    genero: "Odocoileus",
                    especie: "O. virginianus"
                }
            },
            "lobo": {
                nombre: "Lobo gris (Canis lupus)",
                tipo: "Mamífero carnívoro",
                info: "El lobo gris es un mamífero carnívoro social, conocido por su estructura de manada y habilidades de caza cooperativa.",
                alimentacion: "Carnívoro",
                clasificacion: "Mamífero",
                clasificacion_zootecnica: "canino",
                habitat: "América del Norte, Europa, Asia (bosques, tundra)",
                caracteristicas: "Pelaje denso, aullido distintivo, resistencia.",
                curiosidades: "Pueden recorrer hasta 50 km en una noche. Tienen un sentido del olfato excepcional.",
                esperanza_vida: "6-8 años salvaje",
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
                    especie: "C. lupus"
                }
            },
            "pizote": {
                nombre: "Pizote (Nasua nasua)",
                tipo: "Mamífero omnívoro",
                info: "El pizote es un mamífero omnívoro nativo de América Central y del Sur, conocido por su adaptabilidad a diversos hábitats.",
                alimentacion: "Omnívoro",
                clasificacion: "Mamífero",
                habitat: "América Central y del Sur (bosques, áreas urbanas)",
                caracteristicas: "Cuerpo alargado, cola anillada, agilidad.",
                curiosidades: "Son excelentes trepadores. Tienen un sentido del olfato agudo.",
                esperanza_vida: "7-8 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Carnivora",
                    familia: "Procyonidae",
                    genero: "Nasua",
                    especie: "N. nasua"
                }
            },
            "Garza blanca": {
                nombre: "Garza blanca (Ardea alba)",
                tipo: "Ave acuática",
                info: "La garza blanca es un ave acuática elegante, conocida por su plumaje blanco y su habilidad para pescar en aguas poco profundas.",
                alimentacion: "Carnívoro",
                clasificacion: "Ave",
                habitat: "Global (humedales, costas)",
                caracteristicas: "Plumaje blanco, patas largas, pico afilado.",
                curiosidades: "Pueden permanecer inmóviles durante largos períodos. Usan técnicas de pesca variadas.",
                esperanza_vida: "15-25 años",
                esqueleto: "Vertebrado",
                reproduccion: "Oviparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Pelecaniformes",
                    familia: "Ardeidae",
                    genero: "Ardea",
                    especie: "A. alba"
                }
            },
            "Chocoyo frenti amarillo": {
                nombre: "Chocoyo frentiamarillo (Cyanoliseus patagonus)",
                tipo: "Ave parlante",
                info: "El chocoyo frentiamarillo es un loro grande nativo de Sudamérica, conocido por su capacidad para imitar sonidos y su distintivo plumaje.",
                alimentacion: "Herbívoro",
                clasificacion: "Ave",
                habitat: "Sudamérica (bosques, estepas)",
                caracteristicas: "Plumaje verde y amarillo, pico fuerte, vocalizaciones variadas.",
                curiosidades: "Pueden aprender palabras y frases. Viven en parejas o grupos pequeños.",
                esperanza_vida: "30-50 años",
                esqueleto: "Vertebrado",
                reproduccion: "Oviparo",
                conservacion: "Vulnerable",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Psittaciformes",
                    familia: "Psittacidae",
                    genero: "Cyanoliseus",
                    especie: "C. patagonus"
                }
            },
            "canario": {
                nombre: "Canario (Serinus canaria domestica)",
                tipo: "Ave doméstica",
                info: "El canario es un ave pequeña domesticada por su canto melodioso y colores vibrantes.",
                alimentacion: "Herbívoro",
                clasificacion: "Ave",
                habitat: "Global (domesticado)",
                caracteristicas: "Plumaje amarillo, canto variado, pequeño tamaño.",
                curiosidades: "Pueden aprender canciones complejas. Originarios de las Islas Canarias.",
                esperanza_vida: "10-15 años",
                esqueleto: "Vertebrado",
                reproduccion: "Oviparo",
                conservacion: "Domesticado",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Passeriformes",
                    familia: "Fringillidae",
                    genero: "Serinus",
                    especie: "S. canaria domestica"
                }
            },
            "lagartija": {
                nombre: "Lagartija común (Podarcis muralis)",
                tipo: "Reptil",
                info: "La lagartija común es un reptil pequeño y ágil, conocido por su capacidad para trepar paredes y su dieta insectívora.",
                alimentacion: "Insectívoro",
                clasificacion: "Reptil",
                habitat: "Europa (zonas rocosas, muros)",
                caracteristicas: "Cuerpo alargado, cola regenerable, escamas.",
                curiosidades: "Pueden desprender la cola para escapar de depredadores. Son diurnas.",
                esperanza_vida: "3-5 años",
                esqueleto: "Vertebrado",
                reproduccion: "Oviparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Reptilia",
                    orden: "Squamata",
                    familia: "Lacertidae",
                    genero: "Podarcis",
                    especie: "P. muralis"
                }
            },
            "raton": {
                nombre: "Ratón doméstico (Mus musculus)",
                tipo: "Mamífero roedor",
                info: "El ratón doméstico es un pequeño mamífero roedor, conocido por su adaptabilidad a entornos humanos y su rápida reproducción.",
                alimentacion: "Omnívoro",
                clasificacion: "Mamífero",
                clasificacion_zootecnica: "Roedor",
                habitat: "Global (domesticado y salvaje)",
                caracteristicas: "Cuerpo pequeño, cola larga, bigotes sensoriales.",
                curiosidades: "Pueden reproducirse cada 20 días. Usados en investigación científica.",
                esperanza_vida: "1-2 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Rodentia",
                    familia: "Muridae",
                    genero: "Mus",
                    especie: "M. musculus"
                }
            },
            "caballo": {
                nombre: "Caballo doméstico (Equus ferus caballus)",
                tipo: "Mamífero herbívoro",
                info: "El caballo doméstico es un mamífero herbívoro domesticado por su fuerza y velocidad, utilizado en transporte y deporte.",
                alimentacion: "Herbívoro",
                clasificacion: "Mamífero",
                clasificacion_zootecnica: "Equino",
                habitat: "Global (domesticado)",
                caracteristicas: "Cuerpo musculoso, crin, pezuñas.",
                curiosidades: "Pueden dormir de pie. Tienen una visión panorámica.",
                esperanza_vida: "25-30 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Domesticado",
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
            "salmon": {
                nombre: "Salmón atlántico (Salmo salar)",
                tipo: "Pez migratorio",
                info: "El salmón atlántico es un pez migratorio conocido por su ciclo de vida que incluye nacer en agua dulce, migrar al océano y regresar para desovar.",
                alimentacion: "Carnívoro",
                clasificacion: "Pez",
                habitat: "Ríos y océanos del Atlántico Norte",
                caracteristicas: "Cuerpo alargado, color plateado, capacidad de salto.",
                curiosidades: "Pueden nadar contra corrientes fuertes. Son importantes para ecosistemas y pesca.",
                esperanza_vida: "4-6 años",
                esqueleto: "Óseo",
                reproduccion: "Oviparo",
                conservacion: "Vulnerable",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Actinopterygii",
                    orden: "Salmoniformes",
                    familia: "Salmonidae",
                    genero: "Salmo",
                    especie: "S. salar"
                }
            },
            "pajarro carpintero": {
                nombre: "Pájaro carpintero (Picidae)",
                tipo: "Ave insectívora",
                info: "El pájaro carpintero es conocido por su habilidad para perforar madera en busca de insectos, utilizando su pico fuerte y lengua larga.",
                alimentacion: "Insectívoro",
                clasificacion: "Ave",
                habitat: "Global (bosques, áreas arboladas)",
                caracteristicas: "Pico robusto, cola rígida, zygodactyl patas.",
                curiosidades: "Pueden golpear hasta 20 veces/segundo. Usan su lengua para extraer insectos.",
                esperanza_vida: "4-11 años",
                esqueleto: "Vertebrado",
                reproduccion: "Oviparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Piciformes",
                    familia: "Picidae"
                }
            },
            "camaleon": {
                nombre: "Camaleón común (Chamaeleo chamaeleon)",
                tipo: "Reptil",
                info: "El camaleón común es un reptil conocido por su capacidad para cambiar de color y su lengua larga para capturar presas.",
                alimentacion: "Insectívoro",
                clasificacion: "Reptil",
                habitat: "Europa del Sur, Norte de África (bosques, arbustos)",
                caracteristicas: "Ojos independientes, lengua extensible, patas zygodactyl.",
                curiosidades: "Pueden mover cada ojo por separado. Cambian de color por comunicación y temperatura.",
                esperanza_vida: "5-7 años",
                esqueleto: "Vertebrado",
                reproduccion: "Oviparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Reptilia",
                    orden: "Squamata",
                    familia: "Chamaeleonidae",
                    genero: "Chamaeleo",
                    especie: "C. chamaeleon"
                }
            },
            "colibri": {
                nombre: "Colibrí abeja (Mellisuga helenae)",
                tipo: "Ave",
                info: "El colibrí abeja es el ave más pequeña del mundo, conocido por su capacidad de vuelo estacionario y su rápido aleteo.",
                alimentacion: "Nectarívoro",
                clasificacion: "Ave",
                habitat: "Cuba (bosques, jardines)",
                caracteristicas: "Pequeño tamaño, pico largo, vuelo rápido.",
                curiosidades: "Pueden batir sus alas hasta 80 veces/segundo. Son polinizadores importantes.",
                esperanza_vida: "3-5 años",
                esqueleto: "Vertebrado",
                reproduccion: "Oviparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Apodiformes",
                    familia: "Trochilidae",
                    genero: "Mellisuga",
                    especie: "M. helenae"
                }
            },
            "iguana": {
                nombre: "Iguana verde (Iguana iguana)",
                tipo: "Reptil herbívoro",
                info: "La iguana verde es un reptil herbívoro conocido por su tamaño grande y su capacidad para nadar.",
                alimentacion: "Herbívoro",
                clasificacion: "Reptil",
                habitat: "América Central y del Sur (bosques tropicales)",
                caracteristicas: "Cuerpo grande, cola larga, cresta dorsal.",
                curiosidades: "Pueden nadar largas distancias. Tienen una tercera 'parpado' para proteger sus ojos.",
                esperanza_vida: "15-20 años",
                esqueleto: "Vertebrado",
                reproduccion: "Oviparo",
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
            "Boa constrictor": {
                nombre: "Boa constrictor (Boa constrictor)",
                tipo: "Reptil constrictor",
                info: "La boa constrictor es una serpiente no venenosa que mata a sus presas por constricción.",
                alimentacion: "Carnívoro",
                clasificacion: "Reptil",
                habitat: "América Central y del Sur (bosques, sabanas)",
                caracteristicas: "Cuerpo robusto, patrón de color, capacidad de constricción.",
                curiosidades: "Pueden medir hasta 4 m. Son excelentes nadadoras.",
                esperanza_vida: "20-30 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
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
            "camello": {
                nombre: "Camello bactriano (Camelus bactrianus)",
                tipo: "Mamífero rumiante",
                info: "El camello bactriano es un mamífero rumiante adaptado a climas extremos, conocido por sus dos jorobas que almacenan grasa.",
                alimentacion: "Herbívoro",
                clasificacion: "Mamífero",
                habitat: "Asia Central (desiertos, estepas)",
                caracteristicas: "Dos jorobas, pelaje grueso, resistencia a la deshidratación.",
                curiosidades: "Pueden beber hasta 40 litros de agua en una sola vez. Sus jorobas les permiten sobrevivir largos períodos sin agua.",
                esperanza_vida: "40-50 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Doméstico",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Artiodactyla",
                    familia: "Camelidae",
                    genero: "Camelus",
                    especie: "C. bactrianus"
                }
            },
            "Guapote Tigre": {
                nombre: "Guapote Tigre (Cichlasoma salvini)",
                tipo: "Pez de agua dulce",
                info: "El Guapote Tigre es un pez de agua dulce conocido por su agresividad y patrones de color distintivos.",
                alimentacion: "Carnívoro",
                clasificacion: "Pez",
                habitat: "Ríos y lagos de América Central",
                caracteristicas: "Cuerpo robusto, rayas verticales, comportamiento territorial.",
                curiosidades: "Son populares en acuarios por su apariencia. Pueden crecer hasta 60 cm.",
                esperanza_vida: "10-15 años",
                esqueleto: "Óseo",
                reproduccion: "Oviparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Actinopterygii",
                    orden: "Perciformes",
                    familia: "Cichlidae",
                    genero: "Cichlasoma",
                    especie: "C. salvini"
                }
            },
            "Mojarra": {
                nombre: "Mojarra (Gerres spp.)",
                tipo: "Pez costero",
                info: "La mojarra es un pez costero conocido por su cuerpo comprimido y su capacidad para adaptarse a diferentes ambientes marinos.",
                alimentacion: "Omnívoro",
                clasificacion: "Pez",
                habitat: "Costas y estuarios tropicales y subtropicales",
                caracteristicas: "Cuerpo comprimido, aletas largas, color plateado.",
                curiosidades: "Son importantes para la pesca comercial y deportiva. Pueden saltar fuera del agua para escapar de depredadores.",
                esperanza_vida: "5-7 años",
                esqueleto: "Óseo",
                reproduccion: "Oviparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Actinopterygii",
                    orden: "Perciformes",
                    familia: "Gerreidae",
                    genero: "Gerres"
                }
            },
            "Pez ángel": {
                nombre: "Pez ángel (Pterophyllum scalare)",
                tipo: "Pez de agua dulce",
                info: "El pez ángel es un pez de agua dulce conocido por su forma triangular y sus aletas largas y elegantes.",
                alimentacion: "Omnívoro",
                clasificacion: "Pez",
                habitat: "Ríos y lagos de América del Sur",
                caracteristicas: "Cuerpo comprimido, aletas largas, colores variados.",
                curiosidades: "Son populares en acuarios por su apariencia. Pueden vivir en grupos sociales.",
                esperanza_vida: "10-12 años",
                esqueleto: "Óseo",
                reproduccion: "Oviparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Actinopterygii",
                    orden: "Perciformes",
                    familia: "Cichlidae",
                    genero: "Pterophyllum",
                    especie: "P. scalare"
                }
            },
            "Tiburon martillo": {
                nombre: "Tiburón martillo (Sphyrna spp.)",
                tipo: "Pez cartilaginoso",
                info: "El tiburón martillo es conocido por la forma distintiva de su cabeza en forma de 'T', que le proporciona una visión mejorada y habilidades de caza.",
                alimentacion: "Carnívoro",
                clasificacion: "Pez",
                habitat: "Océanos tropicales y templados",
                caracteristicas: "Cabeza en forma de 'T', cuerpo aerodinámico, aletas dorsales altas.",
                curiosidades: "Pueden nadar en grandes escuelas. Usan su cabeza para aturdir a las presas.",
                esperanza_vida: "20-30 años",
                esqueleto: "Cartilaginoso",
                reproduccion: "Vivíparo",
                conservacion: "Vulnerable",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Chondrichthyes",
                    orden: "Carcharhiniformes",
                    familia: "Sphyrnidae",
                    genero: "Sphyrna"
                }
            },
            "Pez payaso": {
                nombre: "Pez payaso (Amphiprioninae)",
                tipo: "Pez de arrecife",
                info: "El pez payaso es conocido por su relación simbiótica con las anémonas de mar y su colorido patrón de rayas.",
                alimentacion: "Omnívoro",
                clasificacion: "Pez",
                habitat: "Arrecifes de coral en el Indo-Pacífico",
                caracteristicas: "Cuerpo ovalado, colores brillantes, comportamiento territorial.",
                curiosidades: "Viven en simbiosis con anémonas. Pueden cambiar de sexo.",
                esperanza_vida: "6-10 años",
                esqueleto: "Óseo",
                reproduccion: "Oviparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Actinopterygii",
                    orden: "Perciformes",
                    familia: "Pomacentridae",
                    subfamilia: "Amphiprioninae"
                }
            },
            "Pez globo": {
                nombre: "Pez globo (Tetraodontidae)",
                tipo: "Pez de agua salada",
                info: "El pez globo es conocido por su capacidad para inflarse como mecanismo de defensa y por contener tetrodotoxina, una potente neurotoxina.",
                alimentacion: "Omnívoro",
                clasificacion: "Pez",
                habitat: "Océanos tropicales y subtropicales",
                caracteristicas: "Cuerpo redondeado, piel rugosa, capacidad de inflado.",
                curiosidades: "Contienen tetrodotoxina, que es letal para los humanos. Son populares en la cocina japonesa (fugu).",
                esperanza_vida: "10-15 años",
                esqueleto: "Óseo",
                reproduccion: "Oviparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Actinopterygii",
                    orden: "Tetraodontiformes",
                    familia: "Tetraodontidae"
                }
            },
            "Pez cirujano": {
                nombre: "Pez cirujano (Acanthuridae)",
                tipo: "Pez de arrecife",
                info: "El pez cirujano es conocido por sus colores vibrantes y las espinas afiladas en la base de su cola, que utiliza para defenderse.",
                alimentacion: "Herbívoro",
                clasificacion: "Pez",
                habitat: "Arrecifes de coral en océanos tropicales",
                caracteristicas: "Cuerpo comprimido, colores brillantes, espinas en la cola.",
                curiosidades: "Son importantes para el ecosistema del arrecife al controlar el crecimiento de algas. Pueden nadar rápidamente para escapar de depredadores.",
                esperanza_vida: "8-15 años",
                esqueleto: "Óseo",
                reproduccion: "Oviparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Actinopterygii",
                    orden: "Perciformes",
                    familia: "Acanthuridae"
                }
            },
            "Obeja": {
                nombre: "Obeja doméstica (Ovis aries)",
                tipo: "Mamífero herbívoro",
                info: "La oveja doméstica es un mamífero herbívoro criado por su lana, carne y leche.",
                alimentacion: "Herbívoro",
                clasificacion: "Mamífero",
                clasificacion_zootecnica: "ovino",
                habitat: "Global (domesticado)",
                caracteristicas: "Cuerpo cubierto de lana, cuernos en algunas razas, comportamiento gregario.",
                curiosidades: "Pueden reconocer hasta 50 caras humanas. Su lana es una de las fibras naturales más utilizadas.",
                esperanza_vida: "10-12 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Domesticado",
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
            "Cabra": {
                nombre: "Cabra doméstica (Capra aegagrus hircus)",
                tipo: "Mamífero herbívoro",
                info: "La cabra doméstica es un mamífero herbívoro criado por su leche, carne y piel.",
                alimentacion: "Herbívoro",
                clasificacion: "Mamífero",
                clasificacion_zootecnica: "caprino",
                habitat: "Global (domesticado)",
                caracteristicas: "Cuerpo ágil, cuernos en ambas sexos, comportamiento curioso.",
                curiosidades: "Pueden escalar superficies empinadas. Su leche es utilizada para hacer quesos especiales.",
                esperanza_vida: "10-15 años",
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
            "Chivo": {
                nombre: "Chivo (Capra aegagrus hircus)",
                tipo: "Mamífero herbívoro",
                info: "El chivo es un mamífero herbívoro domesticado, similar a la cabra, criado por su carne y piel.",
                alimentacion: "Herbívoro",
                clasificacion: "Mamífero",
                clasificacion_zootecnica: "caprino",
                habitat: "Global (domesticado)",
                caracteristicas: "Cuerpo robusto, cuernos en ambas sexos, comportamiento social.",
                curiosidades: "Son animales muy resistentes y adaptables. Su carne es apreciada en muchas culturas.",
                esperanza_vida: "10-15 años",
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
            "chacal": {
                nombre: "Chacal dorado (Canis aureus)",
                tipo: "Mamífero carnívoro",
                info: "El chacal dorado es un mamífero carnívoro conocido por su adaptabilidad a diversos hábitats y su dieta omnívora.",
                alimentacion: "Omnívoro",
                clasificacion: "Mamífero",
                clasificacion_zootecnica: "canino",
                habitat: "África, Asia y Europa (sabana, desierto, bosques)",
                caracteristicas: "Pelaje dorado, orejas grandes, agilidad.",
                curiosidades: "Son animales muy sociales que viven en parejas o pequeños grupos. Tienen un aullido distintivo.",
                esperanza_vida: "10-12 años salvaje",
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
                    especie: "C. aureus"
                }
            },
            "lobo rojo": {
                nombre: "Lobo rojo (Canis rufus)",
                tipo: "Mamífero carnívoro",
                info: "El lobo rojo es un mamífero carnívoro en peligro de extinción, conocido por su pelaje rojizo y su comportamiento social.",
                alimentacion: "Carnívoro",
                clasificacion: "Mamífero",
                clasificacion_zootecnica: "canino",
                habitat: "Sureste de Estados Unidos (bosques, marismas)",
                caracteristicas: "Pelaje rojizo, orejas grandes, estructura social.",
                curiosidades: "Es una especie en peligro crítico debido a la pérdida de hábitat y la hibridación con coyotes. Tienen un aullido distintivo.",
                esperanza_vida: "6-8 años salvaje",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "En peligro crítico",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Carnivora",
                    familia: "Canidae",
                    genero: "Canis",
                    especie: "C. rufus"
                }
            },
            "borrego simarron": {
                nombre: "Borrego cimarrón (Ovis canadensis)",
                tipo: "Mamífero herbívoro",
                info: "El borrego cimarrón es un mamífero herbívoro nativo de América del Norte, conocido por sus impresionantes cuernos curvados y su habilidad para escalar terrenos rocosos.",
                alimentacion: "Herbívoro",
                clasificacion: "Mamífero",
                clasificasiozootecnica:"ovino",
                habitat: "Montañas y áreas rocosas de América del Norte",
                caracteristicas: "Cuerpo robusto, cuernos grandes y curvados, agilidad en terrenos escarpados.",
                curiosidades: "Son excelentes escaladores y pueden saltar grandes distancias. Los machos usan sus cuernos en combates rituales durante la temporada de apareamiento.",
                esperanza_vida: "10-12 años salvaje",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Artiodactyla",
                    familia: "Bovidae",
                    genero: "Ovis",
                    especie: "O. canadensis"
                }
            },
            "toro": {
                nombre: "Toro (Bos taurus)",
                tipo: "Mamífero herbívoro",
                info: "El toro es un mamífero herbívoro domesticado, conocido por su fuerza y tamaño, utilizado principalmente en la agricultura y la ganadería.",
                alimentacion: "Herbívoro",
                clasificacion: "Mamífero",
                clasificacion_zootecnica: "bovino",
                habitat: "Global (domesticado)",
                caracteristicas: "Cuerpo musculoso, cuernos prominentes, comportamiento territorial.",
                curiosidades: "Son animales muy fuertes y resistentes. En algunas culturas, los toros son símbolos de poder y fertilidad.",
                esperanza_vida: "15-20 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Domesticado",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Artiodactyla",
                    familia: "Bovidae",
                    genero: "Bos",
                    especie: "B. taurus"
                }
            },
            "bisonte": {
                nombre: "Bisonte americano (Bison bison)",
                tipo: "Mamífero herbívoro",
                info: "El bisonte americano es un mamífero herbívoro nativo de América del Norte, conocido por su gran tamaño y su papel histórico en las culturas indígenas.",
                alimentacion: "Herbívoro",
                clasificacion: "Mamífero",
                clasificacion_zootecnica: "bovino",
                habitat: "Praderas y llanuras de América del Norte",
                caracteristicas: "Cuerpo masivo, joroba prominente, pelaje denso.",
                curiosidades: "Fueron casi cazados hasta la extinción en el siglo XIX. Son símbolos nacionales de Estados Unidos.",
                esperanza_vida: "15-20 años salvaje",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Casi amenazado",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Artiodactyla",
                    familia: "Bovidae",
                    genero: "Bison",
                    especie: "B. bison"
                }
            },
            "antilope": {
                nombre: "Antílope africano (varias especies)",
                tipo: "Mamífero herbívoro",
                info: "Los antílopes africanos son mamíferos herbívoros nativos de África, conocidos por su velocidad y agilidad.",
                alimentacion: "Herbívoro",
                clasificacion: "Mamífero",
                clasificacion_zootecnica: "bovino",
                habitat: "Sabana, praderas y bosques de África",
                caracteristicas: "Cuerpo esbelto, patas largas, cuernos en ambas sexos (varía por especie).",
                curiosidades: "Son algunos de los animales más rápidos en tierra. Existen muchas especies diferentes con adaptaciones únicas.",
                esperanza_vida: "10-15 años salvaje",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Varía según la especie",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Artiodactyla",
                    familia: "Bovidae"
                }
            },
            "gacela": {
                nombre: "Gacela (Gazella spp.)",
                tipo: "Mamífero herbívoro",
                info: "La gacela es un mamífero herbívoro nativo de África y Asia, conocido por su velocidad y elegancia.",
                alimentacion: "Herbívoro",
                clasificacion: "Mamífero",
                clasificacion_zootecnica: "bovino",
                habitat: "Sabana, desiertos y praderas de África y Asia",
                caracteristicas: "Cuerpo esbelto, patas largas, cuernos en ambas sexos (varía por especie).",
                curiosidades: "Son animales muy rápidos y ágiles, capaces de alcanzar altas velocidades para escapar de depredadores.",
                esperanza_vida: "10-12 años salvaje",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Varía según la especie",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Artiodactyla",
                    familia: "Bovidae",
                    genero: "Gazella"
                }
            },
            "antilope saiga": {
                nombre: "Antílope saiga (Saiga tatarica)",
                tipo: "Mamífero herbívoro",
                info: "El antílope saiga es un mamífero herbívoro nativo de las estepas de Eurasia, conocido por su distintiva nariz bulbosa que filtra el polvo y calienta el aire frío.",
                alimentacion: "Herbívoro",
                clasificacion: "Mamífero",
                clasificacion_zootecnica: "bovino",
                habitat: "Estepas y semi-desiertos de Eurasia",
                caracteristicas: "Cuerpo robusto, nariz grande y flexible, cuernos en los machos.",
                curiosidades: "Su población ha disminuido drásticamente debido a la caza y la pérdida de hábitat. Son capaces de migrar largas distancias en busca de alimento.",
                esperanza_vida: "10-12 años salvaje",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "En peligro crítico",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Artiodactyla",
                    familia: "Bovidae",
                    genero: "Saiga",
                    especie: "S. tatarica"
                }
            },
            "burro": {
                nombre: "Burro doméstico (Equus africanus asinus)",
                tipo: "Mamífero herbívoro",
                info: "El burro doméstico es un mamífero herbívoro criado por su resistencia y capacidad de carga en diversas culturas alrededor del mundo.",
                alimentacion: "Herbívoro",
                clasificacion: "Mamífero",
                clasificacion_zootecnica: "equino",
                habitat: "Global (domesticado)",
                caracteristicas: "Cuerpo robusto, orejas largas, pelaje corto.",
                curiosidades: "Son conocidos por su resistencia y capacidad para sobrevivir en condiciones áridas. Tienen una memoria excepcional.",
                esperanza_vida: "25-30 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Domesticado",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Perissodactyla",
                    familia: "Equidae",
                    genero: "Equus",
                    especie: "E. africanus asinus"
                }
            },
            "cebra": {
                nombre: "Cebra (Equus quagga)",
                tipo: "Mamífero herbívoro",
                info: "La cebra es un mamífero herbívoro nativo de África, conocido por sus distintivas rayas blancas y negras que actúan como camuflaje.",
                alimentacion: "Herbívoro",
                clasificacion: "Mamífero",
                clasificacion_zootecnica: "equino",
                habitat: "Sabana y praderas de África",
                caracteristicas: "Cuerpo robusto, rayas blancas y negras, comportamiento social.",
                curiosidades: "Cada cebra tiene un patrón de rayas único. Viven en grupos sociales llamados manadas.",
                esperanza_vida: "20-25 años salvaje",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Perissodactyla",
                    familia: "Equidae",
                    genero: "Equus",
                    especie: "E. quagga"
                }
            },
            "Quezal": {
                nombre: "Quetzal (Pharomachrus mocinno)",
                tipo: "Ave",
                info: "El quetzal es un ave tropical conocida por su plumaje vibrante y su importancia cultural en Mesoamérica.",
                alimentacion: "Frugívoro",
                clasificacion: "Ave",
                habitat: "Bosques nubosos de América Central",
                caracteristicas: "Plumaje verde y rojo, cola larga en machos, pico amarillo.",
                curiosidades: "Es el ave nacional de Guatemala. Su nombre proviene del náhuatl y significa 'pájaro precioso'.",
                esperanza_vida: "20 años",
                esqueleto: "Vertebrado",
                reproduccion: "Oviparo",
                conservacion: "Casi amenazado",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Trogoniformes",
                    familia: "Trogonidae",
                    genero: "Pharomachrus",
                    especie: "P. mocinno"
                }
            },
            "perezoso": {
                nombre: "Perezoso de tres dedos (Bradypus variegatus)",
                tipo: "Mamífero herbívoro",
                info: "El perezoso de tres dedos es un mamífero herbívoro conocido por su lento movimiento y su adaptación a la vida en los árboles.",
                alimentacion: "Herbívoro",
                clasificacion: "Mamífero",
                habitat: "Bosques tropicales de América Central y del Sur",
                caracteristicas: "Cuerpo cubierto de pelo, garras largas, metabolismo lento.",
                curiosidades: "Pasan la mayor parte de su vida colgados de los árboles. Su pelaje alberga algas que les proporcionan camuflaje.",
                esperanza_vida: "20-30 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Vulnerable",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Pilosa",
                    familia: "Bradypodidae",
                    genero: "Bradypus",
                    especie: "B. variegatus"
                }
            },
            "ormitorrinco": {
                nombre: "Ornitorrinco (Ornithorhynchus anatinus)",
                tipo: "Mamífero semiacuático",
                info: "El ornitorrinco es un mamífero semiacuático conocido por su apariencia única que combina características de mamíferos, aves y reptiles.",
                alimentacion: "Carnívoro",
                clasificacion: "Mamífero",
                habitat: "Ríos y lagos de Australia",
                caracteristicas: "Pico de pato, cola de castor, patas palmeadas.",
                curiosidades: "Es uno de los pocos mamíferos que pone huevos. Tiene espolones venenosos en las patas traseras.",
                esperanza_vida: "10-17 años",
                esqueleto: "Vertebrado",
                reproduccion: "Oviparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Monotremata",
                    familia: "Ornithorhynchidae",
                    genero: "Ornithorhynchus",
                    especie: "O. anatinus"
                }
            },
            "canguro": {
                nombre: "Canguro rojo (Macropus rufus)",
                tipo: "Mamífero herbívoro",
                info: "El canguro rojo es un mamífero herbívoro nativo de Australia, conocido por su gran tamaño y su capacidad para saltar largas distancias.",
                alimentacion: "Herbívoro",
                clasificacion: "Mamífero",
                habitat: "Praderas y desiertos de Australia",
                caracteristicas: "Cuerpo musculoso, patas traseras fuertes, cola larga.",
                curiosidades: "Es el marsupial más grande del mundo. Pueden saltar hasta 9 metros en un solo salto.",
                esperanza_vida: "6-8 años salvaje",
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
                    especie: "M. rufus"
                }
            },
            "rinoceronte": {
                nombre: "Rinoceronte blanco (Ceratotherium simum)",
                tipo: "Mamífero herbívoro",
                info: "El rinoceronte blanco es un mamífero herbívoro conocido por su gran tamaño y sus dos cuernos prominentes en el hocico.",
                alimentacion: "Herbívoro",
                clasificacion: "Mamífero",
                habitat: "Sabana y praderas de África",
                caracteristicas: "Cuerpo masivo, piel gruesa, dos cuernos en el hocico.",
                curiosidades: "Es el segundo mamífero terrestre más grande después del elefante. A pesar de su tamaño, pueden correr a velocidades de hasta 50 km/h.",
                esperanza_vida: "40-50 años salvaje",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Casi amenazado",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Perissodactyla",
                    familia: "Rhinocerotidae",
                    genero: "Ceratotherium",
                    especie: "C. simum"
                }
            },
            "mono": {
                nombre: "Mono capuchino (Cebus capucinus)",
                tipo: "Mamífero omnívoro",
                info: "El mono capuchino es un mamífero omnívoro conocido por su inteligencia y habilidades para usar herramientas.",
                alimentacion: "Omnívoro",
                clasificacion: "Mamífero",
                habitat: "Bosques tropicales de América Central y del Sur",
                caracteristicas: "Cuerpo ágil, cola prensil, pelaje claro con cara oscura.",
                curiosidades: "Son capaces de usar herramientas para obtener alimento. Tienen una estructura social compleja.",
                esperanza_vida: "15-25 años salvaje",
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
                    especie: "C. capucinus"
                }
            },
            "gorila": {
                nombre: "Gorila de montaña (Gorilla beringei beringei)",
                tipo: "Mamífero herbívoro",
                info: "El gorila de montaña es un mamífero herbívoro conocido por su gran tamaño y su vida en las montañas de África Central.",
                alimentacion: "Herbívoro",
                clasificacion: "Mamífero",
                habitat: "Bosques montañosos de África Central",
                caracteristicas: "Cuerpo robusto, pelaje oscuro, fuerza impresionante.",
                curiosidades: "Son los primates más grandes del mundo. Viven en grupos sociales liderados por un macho dominante llamado 'espalda plateada'.",
                esperanza_vida: "35-40 años salvaje",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "En peligro",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Primates",
                    familia: "Hominidae",
                    genero: "Gorilla",
                    especie: "G. beringei beringei"
                }
            },
            "lapa": {
                nombre: "Lapa roja (Ara macao)",
                tipo: "Ave",
                info: "La lapa roja es un ave tropical conocida por su vibrante plumaje rojo, azul y amarillo, y su inteligencia.",
                alimentacion: "Frugívoro",
                clasificacion: "Ave",
                habitat: "Bosques tropicales de América Central y del Sur",
                caracteristicas: "Plumaje rojo, azul y amarillo, pico fuerte, cola larga.",
                curiosidades: "Son aves muy sociales que viven en parejas o grupos. Pueden imitar sonidos humanos.",
                esperanza_vida: "40-50 años",
                esqueleto: "Vertebrado",
                reproduccion: "Oviparo",
                conservacion: "Vulnerable",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Aves",
                    orden: "Psittaciformes",
                    familia: "Psittacidae",
                    genero: "Ara",
                    especie: "A. macao"
                }
            },
            "Tarantula": {
                nombre: "Tarántula (Theraphosidae)",
                tipo: "Arácnido",
                info: "La tarántula es un arácnido conocido por su gran tamaño y su pelaje denso, que utiliza para defenderse de los depredadores.",
                alimentacion: "Carnívoro",
                clasificacion: "Arácnido",
                habitat: "Diversos hábitats en todo el mundo",
                caracteristicas: "Cuerpo grande y peludo, ocho patas, glándulas de veneno.",
                curiosidades: "Pueden lanzar pelos urticantes para defenderse. Algunas especies pueden vivir hasta 30 años en cautiverio.",
                esperanza_vida: "10-30 años",
                esqueleto: "Exoesqueleto",
                reproduccion: "Oviparo",
                conservacion: "Varía según la especie",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Arthropoda",
                    clase: "Arachnida",
                    orden: "Araneae",
                    familia: "Theraphosidae"
                }
            },
            "Escorpión": {
                nombre: "Escorpión (varias especies)",
                tipo: "Arácnido",
                info: "El escorpión es un arácnido conocido por su cola segmentada con un aguijón venenoso, utilizado para cazar presas y defenderse.",
                alimentacion: "Carnívoro",
                clasificacion: "Arácnido",
                habitat: "Diversos hábitats en todo el mundo",
                caracteristicas: "Cuerpo segmentado, ocho patas, cola con aguijón.",
                curiosidades: "Pueden sobrevivir largos períodos sin comida. Su veneno varía en toxicidad según la especie.",
                esperanza_vida: "3-8 años",
                esqueleto: "Exoesqueleto",
                reproduccion: "Vivíparo",
                conservacion: "Varía según la especie",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Arthropoda",
                    clase: "Arachnida",
                    orden: "Scorpiones"
                }
            },
            "zirucata": {
                nombre: "Zirucata (Loxosceles laeta)",
                tipo: "Arácnido",
                info: "La zirucata es un arácnido conocido por su veneno necrotizante, que puede causar lesiones graves en humanos.",
                alimentacion: "Carnívoro",
                clasificacion: "Arácnido",
                habitat: "Áreas urbanas y rurales de América del Sur",
                caracteristicas: "Cuerpo pequeño, color marrón, marca en forma de violín en el cefalotórax.",
                curiosidades: "Su mordedura puede causar necrosis en la piel. Es una de las arañas más venenosas de América del Sur.",
                esperanza_vida: "1-2 años",
                esqueleto: "Exoesqueleto",
                reproduccion: "Oviparo",
                conservacion: "No amenazado",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Arthropoda",
                    clase: "Arachnida",
                    orden: "Araneae",
                    familia: "Sicariidae",
                    genero: "Loxosceles",
                    especie: "L. laeta"
                }
            },
            "hamster": {
                nombre: "Hámster sirio (Mesocricetus auratus)",
                tipo: "Mamífero",
                info: "El hámster sirio es un mamífero roedor conocido por su tamaño pequeño y su comportamiento nocturno.",
                alimentacion: "Omnívoro",
                clasificacion: "Mamífero",
                clasificacion_zootecnica: "roedor",
                habitat: "Regiones áridas de Siria y Turquía",
                caracteristicas: "Cuerpo compacto, pelaje suave, mejillas expansibles.",
                curiosidades: "Son animales solitarios y territoriales. Pueden almacenar comida en sus mejillas para llevarla a su madriguera.",
                esperanza_vida: "2-3 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "No amenazado",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Rodentia",
                    familia: "Cricetidae",
                    genero: "Mesocricetus",
                    especie: "M. auratus"
                }
            },
            "nutria": {
                nombre: "Nutria gigante (Pteronura brasiliensis)",
                tipo: "Mamífero acuático",
                info: "La nutria gigante es un mamífero acuático conocido por su tamaño grande y su comportamiento social en ríos y lagos de América del Sur.",
                alimentacion: "Carnívoro",
                clasificacion: "Mamífero",
                habitat: "Ríos y lagos de América del Sur",
                caracteristicas: "Cuerpo alargado, pelaje denso, patas palmeadas.",
                curiosidades: "Son las nutrias más grandes del mundo. Viven en grupos familiares y son excelentes nadadoras.",
                esperanza_vida: "10-15 años salvaje",
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
            "sepiente cascabel": {
                nombre: "Serpiente de cascabel (Crotalus spp.)",
                tipo: "Reptil venenoso",
                info: "La serpiente de cascabel es un reptil venenoso conocido por el sonido característico que produce al agitar su cola, utilizado como advertencia.",
                alimentacion: "Carnívoro",
                clasificacion: "Reptil",
                habitat: "Diversos hábitats en América del Norte y del Sur",
                caracteristicas: "Cuerpo robusto, escamas, cola con segmentos que producen sonido.",
                curiosidades: "Su veneno es utilizado para inmovilizar presas. Existen varias especies con diferentes patrones de coloración.",
                esperanza_vida: "10-20 años",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Varía según la especie",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Reptilia",
                    orden: "Squamata",
                    familia: "Viperidae",
                    genero: "Crotalus"
                }
            },
            "avestrus": {
                nombre: "Avestruz (Struthio camelus)",
                tipo: "Ave corredora",
                info: "El avestruz es el ave más grande del mundo, conocida por su velocidad y su capacidad para correr largas distancias.",
                alimentacion: "Omnívoro",
                clasificacion: "Ave",
                habitat: "Sabana y desiertos de África",
                caracteristicas: "Cuerpo grande, patas largas, cuello largo, incapaz de volar.",
                curiosidades: "Pueden correr a velocidades de hasta 70 km/h. Ponen los huevos más grandes de todas las aves.",
                esperanza_vida: "30-40 años",
                esqueleto: "Vertebrado",
                reproduccion: "Oviparo",
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
            "elefante marino": {
                nombre: "Elefante marino (Mirounga spp.)",
                tipo: "Mamífero marino",
                info: "El elefante marino es un mamífero marino conocido por su gran tamaño y su distintiva probóscide en los machos.",
                alimentacion: "Carnívoro",
                clasificacion: "Mamífero",
                habitat: "Costas y océanos del hemisferio sur",
                caracteristicas: "Cuerpo masivo, piel gruesa, probóscide en machos.",
                curiosidades: "Son los pinnípedos más grandes del mundo. Pueden sumergirse a grandes profundidades para buscar alimento.",
                esperanza_vida: "20-25 años salvaje",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Preocupación menor",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Carnivora",
                    familia: "Phocidae",
                    genero: "Mirounga"
                }
            },
            "leon marino": {
                nombre: "León marino (Otariinae)",
                tipo: "Mamífero marino",
                info: "El león marino es un mamífero marino conocido por su agilidad en el agua y su comportamiento social en colonias.",
                alimentacion: "Carnívoro",
                clasificacion: "Mamífero",
                habitat: "Costas y océanos de diversas regiones del mundo",
                caracteristicas: "Cuerpo robusto, orejas externas, aletas delanteras grandes.",
                curiosidades: "Son excelentes nadadores y pueden permanecer bajo el agua durante largos períodos. Viven en grandes colonias en las costas.",
                esperanza_vida: "20-30 años salvaje",
                esqueleto: "Vertebrado",
                reproduccion: "Vivíparo",
                conservacion: "Varía según la especie",
                taxonomia: {
                    reino: "Animalia",
                    filo: "Chordata",
                    clase: "Mammalia",
                    orden: "Carnivora",
                    familia: "Otariidae",
                    subfamilia: "Otariinae"
                }
            },
        };

        // Base de datos de países actualizada con estimaciones 2025
        const countryDatabase = {
            "argentina": {
                nombre: "Argentina",
                capital: "Buenos Aires",
                poblacion: "45,851,400",
                continente: "América",
                area: "2.78 millones km²",
                moneda: "Peso argentino (ARS)",
                idioma: "Español",
                info: "La República Argentina es un país federal en el extremo sur de América del Sur. Limita con Chile al oeste, Bolivia y Paraguay al norte, Brasil al noreste y Uruguay al este. Su territorio incluye la Antártida Argentina y las Islas Malvinas.",
                curiosidades: "Es el país con la segunda mayor extensión territorial de América del Sur y el octavo del mundo. Famoso por el tango, el asado y las Cataratas del Iguazú.",
                gobierno: "República federal presidencialista",
                pib: "USD 683,533 millones (2025)",
                banderas: "Azul y blanco con sol de mayo en el centro"
            },
            "brasil": {
                nombre: "Brasil",
                capital: "Brasilia",
                poblacion: "212,812,000",
                continente: "América",
                area: "8.51 millones km²",
                moneda: "Real brasileño (BRL)",
                idioma: "Portugués",
                info: "La República Federativa de Brasil es el país más grande de América del Sur y el quinto del mundo por superficie y población. Limita con casi todos los países sudamericanos excepto Chile y Ecuador.",
                curiosidades: "Casa de la selva amazónica, el carnaval de Río y la Estatua del Cristo Redentor. Es la economía más grande de América Latina.",
                gobierno: "República federal presidencialista",
                pib: "USD 2,125,958 millones (2025)",
                banderas: "Verde con estrella amarilla y franja azul azul con estrellas"
            },
            "mexico": {
                nombre: "México",
                capital: "Ciudad de México",
                poblacion: "131,947,000",
                continente: "América",
                area: "1.96 millones km²",
                moneda: "Peso mexicano (MXN)",
                idioma: "Español",
                info: "Los Estados Unidos Mexicanos son un país de América del Norte que limita con Estados Unidos al norte, Guatemala y Belice al sur, y el Océano Pacífico al oeste y el Golfo de México al este.",
                curiosidades: "Patrimonio de la UNESCO como las pirámides de Teotihuacán y Chichén Itzá. Famoso por el Día de Muertos y la gastronomía picante.",
                gobierno: "República federal presidencialista",
                pib: "USD 1,692,640 millones (2025)",
                banderas: "Verde, blanco y rojo con águila devorando serpiente"
            },
            "españa": {
                nombre: "España",
                capital: "Madrid",
                poblacion: "47,890,000",
                continente: "Europa",
                area: "505,990 km²",
                moneda: "Euro (EUR)",
                idioma: "Español",
                info: "El Reino de España es un país soberano en el suroeste de Europa, con capital en Madrid. Incluye las Islas Baleares, Canarias y las ciudades autónomas de Ceuta y Melilla en África del Norte.",
                curiosidades: "Casa de la Sagrada Familia de Gaudí y la Alhambra. Famoso por la paella, flamenco y las corridas de toros.",
                gobierno: "Monarquía parlamentaria",
                pib: "USD 1,799,511 millones (2025)",
                banderas: "Roja y amarilla con escudo nacional"
            },
            "francia": {
                nombre: "Francia",
                capital: "París",
                poblacion: "66,650,800",
                continente: "Europa",
                area: "551,695 km² (metropolitana)",
                moneda: "Euro (EUR)",
                idioma: "Francés",
                info: "La República Francesa es un país transcontinental en Europa Occidental. Incluye territorios de ultramar en América, África, Oceanía y la Antártida.",
                curiosidades: "Torre Eiffel, Louvre y la Revolución Francesa. Líder en moda, vino y gastronomía.",
                gobierno: "República semipresidencialista",
                pib: "USD 3,211,292 millones (2025)",
                banderas: "Azul, blanco y rojo verticales"
            },
            "kenia": {
                nombre: "Kenia",
                capital: "Nairobi",
                poblacion: "57,532,500",
                continente: "África",
                area: "580,367 km²",
                moneda: "Chelín keniano (KES)",
                idioma: "Inglés y suajili",
                info: "La República de Kenia es un país del este de África que limita con Tanzania, Uganda, Sudán del Sur, Etiopía y Somalia. Incluye el Lago Victoria y la costa del Océano Índico.",
                curiosidades: "Cuna de la humanidad con fósiles de homínidos. Hogar de safaris en la sabana y el Monte Kilimanjaro cercano.",
                gobierno: "República presidencialista",
                pib: "USD 131,673 millones (2025)",
                banderas: "Negra, roja y roja con escudos masái"
            },
            "sudafrica": {
                nombre: "Sudáfrica",
                capital: "Pretoria (ejecutiva), Ciudad del Cabo (legislativa), Bloemfontein (judicial)",
                poblacion: "64,747,300",
                continente: "África",
                area: "1.22 millones km²",
                moneda: "Rand sudafricano (ZAR)",
                idioma: "11 idiomas oficiales, incluyendo inglés y afrikáans",
                info: "La República de Sudáfrica es el país más austral de África. Limita con Namibia, Botsuana, Zimbabue, Mozambique, Suazilandia y Lesoto.",
                curiosidades: "Fin del apartheid con Nelson Mandela. Hogar de la Table Mountain y safaris con los 'Big Five'.",
                gobierno: "República parlamentaria",
                pib: "USD 410,338 millones (2025)",
                banderas: "Y forma de 'Y' en rojo, azul, verde, negro, blanco y amarillo"
            },
            "china": {
                nombre: "China",
                capital: "Pekín",
                poblacion: "1,416,100,000",
                continente: "Asia",
                area: "9.6 millones km²",
                moneda: "Yuan chino (CNY)",
                idioma: "Mandarín",
                info: "La República Popular China es el país más poblado del mundo y el tercero por superficie. Limita con 14 países y tiene costas en el Pacífico.",
                curiosidades: "Gran Muralla China, pandas y la Ciudad Prohibida. Líder en manufactura y tecnología.",
                gobierno: "República socialista",
                pib: "USD 19,231,705 millones (2025)",
                banderas: "Roja con cinco estrellas amarillas"
            },
            "australia": {
                nombre: "Australia",
                capital: "Canberra",
                poblacion: "26,974,000",
                continente: "Oceanía",
                area: "7.69 millones km²",
                moneda: "Dólar australiano (AUD)",
                idioma: "Inglés",
                info: "La Mancomunidad de Australia es un país insular que ocupa el continente australiano. Limita con el Océano Índico y Pacífico.",
                curiosidades: "Único continente-habitado sin países terrestres vecinos. Hogar de canguros, koalas y la Gran Barrera de Coral.",
                gobierno: "Monarquía constitucional federal",
                pib: "USD 1,771,681 millones (2025)",
                banderas: "Azul con Unión Jack, Cruz del Sur y federación"
            },
            "canada": {
                nombre: "Canadá",
                capital: "Ottawa",
                poblacion: "40,126,700",
                continente: "América",
                area: "9.98 millones km²",
                moneda: "Dólar canadiense (CAD)",
                idioma: "Inglés y francés",
                info: "Canadá es el segundo país más grande del mundo por superficie. Limita con Estados Unidos al sur y tiene costas en tres océanos.",
                curiosidades: "Hogar de las Cataratas del Niágara y el jarabe de arce. Conocido por su multiculturalismo y vastos bosques.",
                gobierno: "Monarquía constitucional federal",
                pib: "USD 2,225,341 millones (2025)",
                banderas: "Roja con hoja de arce blanca"
            },
            "estados unidos": {
                nombre: "Estados Unidos",
                capital: "Washington D.C.",
                poblacion: "347,276,000",
                continente: "América",
                area: "9.83 millones km²",
                moneda: "Dólar estadounidense (USD)",
                idioma: "Inglés",
                info: "Los Estados Unidos de América son una república federal en América del Norte. Limita con Canadá al norte y México al sur.",
                curiosidades: "Casa de la Estatua de la Libertad y Hollywood. Líder en innovación y cultura pop.",
                gobierno: "República federal presidencialista",
                pib: "USD 30,507,217 millones (2025)",
                banderas: "13 franjas rojas y blancas con 50 estrellas en azul"
            },
            "reino unido": {
                nombre: "Reino Unido",
                capital: "Londres",
                poblacion: "69,551,300",
                continente: "Europa",
                area: "243,610 km²",
                moneda: "Libra esterlina (GBP)",
                idioma: "Inglés",
                info: "El Reino Unido de Gran Bretaña e Irlanda del Norte es un país soberano en Europa Occidental, compuesto por Inglaterra, Escocia, Gales e Irlanda del Norte.",
                curiosidades: "Big Ben, Stonehenge y la monarquía. Origen del fútbol y el té.",
                gobierno: "Monarquía constitucional parlamentaria",
                pib: "USD 3,839,180 millones (2025)",
                banderas: "Unión Jack (cruces de San Andrés, San Patricio y San Jorge)"
            },
            "alemania": {
                nombre: "Alemania",
                capital: "Berlín",
                poblacion: "84,075,100",
                continente: "Europa",
                area: "357,022 km²",
                moneda: "Euro (EUR)",
                idioma: "Alemán",
                info: "La República Federal de Alemania es un país en Europa Central. Limita con 9 países y es miembro fundador de la UE.",
                curiosidades: "Castillo de Neuschwanstein, Oktoberfest y autos como BMW. Potencia industrial.",
                gobierno: "República federal parlamentaria",
                pib: "USD 4,744,744 millones (2025)",
                banderas: "Negra, roja y amarilla horizontal"
            },
            "italia": {
                nombre: "Italia",
                capital: "Roma",
                poblacion: "59,146,300",
                continente: "Europa",
                area: "301,340 km²",
                moneda: "Euro (EUR)",
                idioma: "Italiano",
                info: "La República Italiana es un país en el sur de Europa, en forma de bota en el Mediterráneo. Hogar de la Antigua Roma.",
                curiosidades: "Coliseo, pizza y moda. Cuna del Renacimiento.",
                gobierno: "República parlamentaria",
                pib: "USD 2,422,855 millones (2025)",
                banderas: "Verde, blanco y roja vertical"
            },
            "russia": {
                nombre: "Rusia",
                capital: "Moscú",
                poblacion: "143,997,000",
                continente: "Europa y Asia",
                area: "17.1 millones km²",
                moneda: "Rublo ruso (RUB)",
                idioma: "Ruso",
                info: "La Federación de Rusia es el país más grande del mundo por superficie, extendiéndose por Europa del Este y Asia del Norte.",
                curiosidades: "Kremlin, ballet y vodka. Puente terrestre entre Europa y Asia.",
                gobierno: "República federal semipresidencialista",
                pib: "USD 2,076,396 millones (2025)",
                banderas: "Blanca, azul y roja horizontal"
            },
            "india": {
                nombre: "India",
                capital: "Nueva Delhi",
                poblacion: "1,463,870,000",
                continente: "Asia",
                area: "3.29 millones km²",
                moneda: "Rupia india (INR)",
                idioma: "Hindi y inglés",
                info: "La República de India es un país en el sur de Asia. Limita con Pakistán, China y otros, con una rica historia antigua.",
                curiosidades: "Taj Mahal, yoga y Bollywood. Segundo país más poblado.",
                gobierno: "República federal parlamentaria",
                pib: "USD 4,187,017 millones (2025)",
                banderas: "Azafrán, blanco y verde con rueda azul"
            },
            "indonesia": {
                nombre: "Indonesia",
                capital: "Yakarta",
                poblacion: "285,721,000",
                continente: "Asia",
                area: "1.9 millones km²",
                moneda: "Rupia indonesia (IDR)",
                idioma: "Indonesio",
                info: "La República de Indonesia es un archipiélago de más de 17,000 islas en el sudeste asiático.",
                curiosidades: "Bali, Komodo y el mayor archipiélago del mundo. Hogar de orangutanes.",
                gobierno: "República presidencialista",
                pib: "USD 1,429,743 millones (2025)",
                banderas: "Roja y blanca horizontal"
            },
            "nigeria": {
                nombre: "Nigeria",
                capital: "Abuya",
                poblacion: "237,528,000",
                continente: "África",
                area: "923,768 km²",
                moneda: "Naira nigeriana (NGN)",
                idioma: "Inglés",
                info: "La República Federal de Nigeria es el país más poblado de África. Limita con Níger, Chad, Camerún y Benín.",
                curiosidades: "Industria cinematográfica Nollywood y petróleo. Diversidad étnica.",
                gobierno: "República federal presidencialista",
                pib: "USD 188,271 millones (2025)",
                banderas: "Verde, blanca y verde vertical"
            },
            "egipto": {
                nombre: "Egipto",
                capital: "El Cairo",
                poblacion: "118,366,000",
                continente: "África",
                area: "1.01 millones km²",
                moneda: "Libra egipcia (EGP)",
                idioma: "Árabe",
                info: "La República Árabe de Egipto se encuentra en el noreste de África y suroeste de Asia, cruzado por el Nilo.",
                curiosidades: "Pirámides de Giza y esfinges. Cuna de una de las civilizaciones más antiguas.",
                gobierno: "República semipresidencialista",
                pib: "USD 347,342 millones (2025)",
                banderas: "Roja, blanca y negra horizontal con águila dorada"
            },
            "marrocos": {
                nombre: "Marruecos",
                capital: "Rabat",
                poblacion: "38,430,800",
                continente: "África",
                area: "446,550 km²",
                moneda: "Dirham marroquí (MAD)",
                idioma: "Árabe y bereber",
                info: "El Reino de Marruecos se encuentra en el noroeste de África, con costas en el Atlántico y Mediterráneo.",
                curiosidades: "Marrakech, té de menta y medinas. Puente entre África y Europa.",
                gobierno: "Monarquía constitucional",
                pib: "USD 165,835 millones (2025)",
                banderas: "Roja con estrella pentagonal verde"
            },
            "argelia": {
                nombre: "Argelia",
                capital: "Argel",
                poblacion: "47,435,300",
                continente: "África",
                area: "2.38 millones km²",
                moneda: "Dinar argelino (DZD)",
                idioma: "Árabe y bereber",
                info: "La República Democrática y Popular de Argelia es el país más grande de África por superficie.",
                curiosidades: "Sahara, ruinas romanas y petróleo. Historia de resistencia.",
                gobierno: "República semipresidencialista",
                pib: "USD 268,885 millones (2025)",
                banderas: "Verde y blanca horizontal con media luna y estrella roja"
            },
            "etiopia": {
                nombre: "Etiopía",
                capital: "Adís Abeba",
                poblacion: "135,472,000",
                continente: "África",
                area: "1.1 millones km²",
                moneda: "Birr etíope (ETB)",
                idioma: "Amárico",
                info: "La República Federal Democrática de Etiopía es un país sin salida al mar en el Cuerno de África.",
                curiosidades: "Cuna de Lucy (fósil humano) y café. Nunca colonizada.",
                gobierno: "República federal parlamentaria",
                pib: "USD 117,457 millones (2025)",
                banderas: "Verde, amarilla y roja horizontal con estrella azul"
            },
            "ghana": {
                nombre: "Ghana",
                capital: "Acra",
                poblacion: "35,064,300",
                continente: "África",
                area: "238,533 km²",
                moneda: "Cedi ghanés (GHS)",
                idioma: "Inglés",
                info: "La República de Ghana se encuentra en África Occidental, con costas en el Golfo de Guinea.",
                curiosidades: "Castillos de esclavos y oro. Primera nación subsahariana en independencia.",
                gobierno: "República presidencialista",
                pib: "USD 88,332 millones (2025)",
                banderas: "Roja, amarilla y verde horizontal con estrella negra"
            },
            "portugal": {
                nombre: "Portugal",
                capital: "Lisboa",
                poblacion: "10,411,800",
                continente: "Europa",
                area: "92,090 km²",
                moneda: "Euro (EUR)",
                idioma: "Portugués",
                info: "La República Portuguesa se encuentra en el suroeste de Europa, en la península Ibérica, con archipiélagos en el Atlántico.",
                curiosidades: "Fado, pasteles de nata y exploradores como Vasco da Gama. Líder en corcho.",
                gobierno: "República semipresidencialista",
                pib: "USD 321,440 millones (2025)",
                banderas: "Verde y roja con escudo y esfera armilar"
            },
            "grecia": {
                nombre: "Grecia",
                capital: "Atenas",
                poblacion: "9,938,840",
                continente: "Europa",
                area: "131,957 km²",
                moneda: "Euro (EUR)",
                idioma: "Griego",
                info: "La República Helénica se encuentra en el sureste de Europa, con miles de islas en el Egeo y Jónico.",
                curiosidades: "Cuna de la democracia, Olimpiadas y filosofía. Hogar de la Acrópolis.",
                gobierno: "República parlamentaria",
                pib: "USD 267,348 millones (2025)",
                banderas: "Azul y blanca con cruz blanca"
            },
            "turquia": {
                nombre: "Turquía",
                capital: "Ankara",
                poblacion: "87,685,400",
                continente: "Europa y Asia",
                area: "783,562 km²",
                moneda: "Lira turca (TRY)",
                idioma: "Turco",
                info: "La República de Turquía es un país transcontinental que une Europa y Asia, con Estambul como puente cultural.",
                curiosidades: "Hagia Sophia, kebabs y alfombras. Único país con territorio en dos continentes.",
                gobierno: "República presidencialista",
                pib: "USD 1,437,406 millones (2025)",
                banderas: "Roja con media luna y estrella blanca"
            },
            "tailandia": {
                nombre: "Tailandia",
                capital: "Bangkok",
                poblacion: "71,619,900",
                continente: "Asia",
                area: "513,120 km²",
                moneda: "Baht tailandés (THB)",
                idioma: "Tailandés",
                info: "El Reino de Tailandia es un país del sudeste asiático conocido por sus templos, playas y gastronomía picante.",
                curiosidades: "Más de 40,000 templos y elefantes como símbolo nacional. 'Tierra de las sonrisas'.",
                gobierno: "Monarquía constitucional",
                pib: "USD 546,224 millones (2025)",
                banderas: "Roja, blanca, azul, blanca y roja horizontal"
            },
            "peru": {
                nombre: "Perú",
                capital: "Lima",
                poblacion: "34,576,700",
                continente: "América",
                area: "1.28 millones km²",
                moneda: "Sol peruano (PEN)",
                idioma: "Español y quechua",
                info: "La República del Perú es un país andino en América del Sur, hogar de la antigua civilización inca.",
                curiosidades: "Machu Picchu y ceviche. Origen del tomate y papa.",
                gobierno: "República presidencialista",
                pib: "USD 303,293 millones (2025)",
                banderas: "Roja y blanca vertical con escudo"
            },
            "colombia": {
                nombre: "Colombia",
                capital: "Bogotá",
                poblacion: "53,425,600",
                continente: "América",
                area: "1.14 millones km²",
                moneda: "Peso colombiano (COP)",
                idioma: "Español",
                info: "La República de Colombia es un país ecuatorial en el noroeste de América del Sur, con costas en dos océanos y gran biodiversidad.",
                curiosidades: "Segundo país más biodiverso. Famoso por café, esmeraldas y salsa.",
                gobierno: "República presidencialista",
                pib: "USD 427,766 millones (2025)",
                banderas: "Amarilla, azul y roja horizontal"
            },
            "chile": {
                nombre: "Chile",
                capital: "Santiago",
                poblacion: "19,859,900",
                continente: "América",
                area: "756,102 km²",
                moneda: "Peso chileno (CLP)",
                idioma: "Español",
                info: "La República de Chile es un país largo y estrecho en el suroeste de América del Sur, con desierto, Andes y fiordos.",
                curiosidades: "Atacama, desierto más seco. Hogar de Moai en Isla de Pascua.",
                gobierno: "República presidencialista",
                pib: "USD 343,823 millones (2025)",
                banderas: "Blanca con estrella azul y roja"
            },
            "austria": {
                nombre: "Austria",
                capital: "Viena",
                poblacion: "9,113,570",
                continente: "Europa",
                area: "83,879 km²",
                moneda: "Euro (EUR)",
                idioma: "Alemán",
                info: "La República de Austria es un país alpino sin salida al mar en Europa Central, conocido por su música clásica.",
                curiosidades: "Mozart y Strauss. Alpes para esquí, Sachertorte.",
                gobierno: "República federal parlamentaria",
                pib: "USD 534,301 millones (2025)",
                banderas: "Roja, blanca y roja horizontal"
            },
            "suecia": {
                nombre: "Suecia",
                capital: "Estocolmo",
                poblacion: "10,656,600",
                continente: "Europa",
                area: "450,295 km²",
                moneda: "Corona sueca (SEK)",
                idioma: "Sueco",
                info: "El Reino de Suecia es el país más grande de Escandinavia, con lagos, bosques y alto nivel de vida.",
                curiosidades: "IKEA, ABBA, Nobel. Noches polares en el norte.",
                gobierno: "Monarquía constitucional parlamentaria",
                pib: "USD 620,297 millones (2025)",
                banderas: "Azul con cruz amarilla"
            },
            "noruega": {
                nombre: "Noruega",
                capital: "Oslo",
                poblacion: "5,623,070",
                continente: "Europa",
                area: "323,802 km²",
                moneda: "Corona noruega (NOK)",
                idioma: "Noruego",
                info: "El Reino de Noruega es un país escandinavo con fiordos impresionantes y alto IDH.",
                curiosidades: "Aurora boreal, petróleo, vikingos. Fondos soberanos ricos.",
                gobierno: "Monarquía constitucional parlamentaria",
                pib: "USD 504,276 millones (2025)",
                banderas: "Roja con cruz azul y blanca"
            },
            "paises bajos": {
                nombre: "Países Bajos",
                capital: "Ámsterdam",
                poblacion: "18,346,800",
                continente: "Europa",
                area: "41,543 km²",
                moneda: "Euro (EUR)",
                idioma: "Neerlandés",
                info: "El Reino de los Países Bajos es conocido por sus diques, tulipanes y ciclismo.",
                curiosidades: "País más bajo, molinos de viento. Ámsterdam con canales UNESCO.",
                gobierno: "Monarquía constitucional parlamentaria",
                pib: "USD 1,272,011 millones (2025)",
                banderas: "Roja, blanca y azul horizontal"
            },
            "polonia": {
                nombre: "Polonia",
                capital: "Varsovia",
                poblacion: "38,140,900",
                continente: "Europa",
                area: "312,696 km²",
                moneda: "Zloty polaco (PLN)",
                idioma: "Polaco",
                info: "La República de Polonia es un país en Europa Central con rica historia eslava.",
                curiosidades: "Copernico, Chopin. Auschwitz y Varsovia reconstruida.",
                gobierno: "República semipresidencialista",
                pib: "USD 979,960 millones (2025)",
                banderas: "Blanca y roja horizontal"
            },
            "belgica": {
                nombre: "belgica",
                capital: "Bruselas",
                poblacion: "11,632,900",
                continente: "Europa",
                area: "30,528 km²",
                moneda: "Euro (EUR)",
                idioma: "Neerlandés, francés y alemán",
                info: "El Reino de Bélgica es un país en Europa Occidental, sede de la UE y la OTAN.",
                curiosidades: "Chocolate, cerveza y waffles. Cuna de Tintín.",
                gobierno: "Monarquía constitucional federal",
                pib: "USD 636,105 millones (2025)",
                banderas: "Negra, amarilla y roja vertical"
            },
            "suiza": {
                nombre: "Suiza",
                capital: "Berna",
                poblacion: "8,812,600",
                continente: "Europa",
                area: "41,290 km²",
                moneda: "Franco suizo (CHF)",
                idioma: "Alemán, francés, italiano y romanche",
                info: "La Confederación Suiza es un país alpino conocido por su neutralidad y bancos.",
                curiosidades: "Relojes, chocolate y queso. Sede de la Cruz Roja.",
                gobierno: "República federal directa",
                pib: "USD 824,731 millones (2025)",
                banderas: "Roja con cruz blanca"
            },
            "Nicaragua": {
                nombre: "Nicaragua",
                capital: "Managua",
                poblacion: "6,850,540",
                continente: "América",
                area: "130,373 km²",
                moneda: "Córdoba nicaragüense (NIO)",
                idioma: "Español",
                info: "La República de Nicaragua es el país más grande de América Central, conocido por sus lagos y volcanes.",
                curiosidades: "Lago de Nicaragua con tiburones de agua dulce. Cultura rica en música y poesía.",
                gobierno: "República presidencialista",
                pib: "USD 15,123 millones (2025)",
                banderas: "Azul y blanca horizontal con escudo nacional"
            },
            "costa rica": {
                nombre: "Costa Rica",
                capital: "San José",
                poblacion: "5,094,118",
                continente: "América",
                area: "51,100 km²",
                moneda: "Colón costarricense (CRC)",
                idioma: "Español",
                info: "La República de Costa Rica es un país en América Central conocido por su biodiversidad y políticas ambientales.",
                curiosidades: "No tiene ejército desde 1949. Más del 25% del territorio es parque nacional.",
                gobierno: "República presidencialista",
                pib: "USD 68,456 millones (2025)",
                banderas: "Azul, blanca y roja horizontal con escudo nacional"
            },
            "cuba": {
                nombre: "Cuba",
                capital: "La Habana",
                poblacion: "11,317,000",
                continente: "América",
                area: "109,884 km²",
                moneda: "Peso cubano (CUP) y Peso convertible (CUC)",
                idioma: "Español",
                info: "La República de Cuba es una isla en el Caribe conocida por su historia revolucionaria y cultura vibrante.",
                curiosidades: "Cuna del son cubano y salsa. Famosa por sus puros y autos clásicos.",
                gobierno: "República socialista unipartidista",
                pib: "USD 100,023 millones (2025)",
                banderas: "Azul, blanca y roja con estrella blanca"
            },
            "dominicana": {
                nombre: "República Dominicana",
                capital: "Santo Domingo",
                poblacion: "11,113,000",
                continente: "América",
                area: "48,671 km²",
                moneda: "Peso dominicano (DOP)",
                idioma: "Español",
                info: "La República Dominicana ocupa dos tercios de la isla La Española en el Caribe, compartida con Haití.",
                curiosidades: "Cuna del merengue y bachata. Primer asentamiento europeo en América.",
                gobierno: "República presidencialista",
                pib: "USD 138,456 millones (2025)",
                banderas: "Roja, blanca y azul con escudo nacional"
            },
            "panama": {
                nombre: "Panamá",
                capital: "Ciudad de Panamá",
                poblacion: "4,468,000",
                continente: "América",
                area: "75,417 km²",
                moneda: "Balboa panameño (PAB) y Dólar estadounidense (USD)",
                idioma: "Español",
                info: "La República de Panamá es un país en América Central conocido por el Canal de Panamá que conecta el Atlántico y el Pacífico.",
                curiosidades: "Canal de Panamá, una de las mayores hazañas de ingeniería. Biodiversidad rica en selvas tropicales.",
                gobierno: "República presidencialista",
                pib: "USD 110,234 millones (2025)",
                banderas: "Blanca, roja y azul con estrellas"
            },
            "uruguay": {
                nombre: "Uruguay",
                capital: "Montevideo",
                poblacion: "3,518,552",
                continente: "América",
                area: "176,215 km²",
                moneda: "Peso uruguayo (UYU)",
                idioma: "Español",
                info: "La República Oriental del Uruguay es un país en América del Sur conocido por su estabilidad política y calidad de vida.",
                curiosidades: "Primer país en legalizar el matrimonio igualitario en América Latina. Famoso por el mate y el tango.",
                gobierno: "República presidencialista",
                pib: "USD 76,543 millones (2025)",
                banderas: "Blanca con franjas azules y sol dorado"
            },
            "paraguay": {
                nombre: "Paraguay",
                capital: "Asunción",
                poblacion: "7,132,538",
                continente: "América",
                area: "406,752 km²",
                moneda: "Guaraní paraguayo (PYG)",
                idioma: "Español y guaraní",
                info: "La República del Paraguay es un país sin salida al mar en América del Sur, conocido por su cultura guaraní.",
                curiosidades: "Uno de los dos países bilingües de América del Sur. Famoso por la música polca paraguaya.",
                gobierno: "República presidencialista",
                pib: "USD 40,123 millones (2025)",
                banderas: "Roja, blanca y azul horizontal con escudo nacional"
            },
            "bolivia": {
                nombre: "Bolivia",
                capital: "Sucre (constitucional), La Paz (sede de gobierno)",
                poblacion: "12,632,000",
                continente: "América",
                area: "1.1 millones km²",
                moneda: "Boliviano (BOB)",
                idioma: "Español, quechua, aimara y otros",
                info: "El Estado Plurinacional de Bolivia es un país sin salida al mar en el centro-oeste de América del Sur.",
                curiosidades: "Salar de Uyuni, lago Titicaca. Alta diversidad cultural y geográfica.",
                gobierno: "República presidencialista",
                pib: "USD 112,345 millones (2025)",
                banderas: "Roja, amarilla y verde horizontal con escudo nacional"
            },
            "hungria": {
                nombre: "Hungría",
                capital: "Budapest",
                poblacion: "9,689,010",
                continente: "Europa",
                area: "93,028 km²",
                moneda: "Forinto húngaro (HUF)",
                idioma: "Húngaro",
                info: "La República de Hungría es un país sin salida al mar en Europa Central, conocido por su historia y cultura.",
                curiosidades: "Baños termales y paprika. Cuna de compositores como Liszt y Bartók.",
                gobierno: "República parlamentaria",
                pib: "USD 220,456 millones (2025)",
                banderas: "Roja, blanca y verde horizontal"
            },
            "finlandia": {
                nombre: "Finlandia",
                capital: "Helsinki",
                poblacion: "5,548,241",
                continente: "Europa",
                area: "338,455 km²",
                moneda: "Euro (EUR)",
                idioma: "Finés y sueco",
                info: "La República de Finlandia es un país nórdico conocido por sus lagos, bosques y alta calidad de vida.",
                curiosidades: "Tierra de los mil lagos y auroras boreales. Sistema educativo de renombre mundial.",
                gobierno: "República parlamentaria",
                pib: "USD 300,123 millones (2025)",
                banderas: "Blanca con cruz azul"
            },
            "dinamarca": {
                nombre: "Dinamarca",
                capital: "Copenhague",
                poblacion: "5,873,420",
                continente: "Europa",
                area: "42,933 km²",
                moneda: "Corona danesa (DKK)",
                idioma: "Danés",
                info: "El Reino de Dinamarca es un país nórdico compuesto por la península de Jutlandia y numerosas islas en el Mar del Norte y el Báltico.",
                curiosidades: "Hogar de Hans Christian Andersen y los vikingos. Conocido por su diseño y calidad de vida.",
                gobierno: "Monarquía constitucional parlamentaria",
                pib: "USD 400,567 millones (2025)",
                banderas: "Roja con cruz blanca"
            },
            "irlanda": {
                nombre: "Irlanda",
                capital: "Dublín",
                poblacion: "5,123,536",
                continente: "Europa",
                area: "70,273 km²",
                moneda: "Euro (EUR)",
                idioma: "Irlandés y inglés",
                info: "La República de Irlanda es un país insular en Europa Occidental, conocido por su paisaje verde y cultura celta.",
                curiosidades: "Cuna de San Patricio y la música tradicional irlandesa. Famosa por sus pubs y cerveza Guinness.",
                gobierno: "República parlamentaria",
                pib: "USD 450,789 millones (2025)",
                banderas: "Verde, blanca y naranja vertical"
            },
            "croacia": {
                nombre: "Croacia",
                capital: "Zagreb",
                poblacion: "3,871,833",
                continente: "Europa",
                area: "56,594 km²",
                moneda: "Kuna croata (HRK)",
                idioma: "Croata",
                info: "La República de Croacia es un país en Europa del Sudeste, conocido por su costa adriática y patrimonio histórico.",
                curiosidades: "Destinos turísticos como Dubrovnik y Split. Famosa por su música klapa y gastronomía mediterránea.",
                gobierno: "República parlamentaria",
                pib: "USD 150,234 millones (2025)",
                banderas: "Roja, blanca y azul horizontal con escudo nacional"
            },
            "serbia": {
                nombre: "Serbia",
                capital: "Belgrado",
                poblacion: "6,797,105",
                continente: "Europa",
                area: "77,474 km²",
                moneda: "Dinar serbio (RSD)",
                idioma: "Serbio",
                info: "La República de Serbia es un país en Europa del Sudeste, conocido por su historia y cultura diversa.",
                curiosidades: "Cuna de Nikola Tesla y festivales de música. Famosa por su cocina balcánica.",
                gobierno: "República parlamentaria",
                pib: "USD 130,567 millones (2025)",
                banderas: "Roja, azul y blanca horizontal con escudo nacional"
            },
            "honduras": {
                nombre: "Honduras",
                capital: "Tegucigalpa",
                poblacion: "10,278,345",
                continente: "América",
                area: "112,492 km²",
                moneda: "Lempira hondureña (HNL)",
                idioma: "Español",
                info: "La República de Honduras es un país en América Central conocido por sus ruinas mayas y biodiversidad.",
                curiosidades: "Ruinas de Copán y arrecifes de coral. Cultura rica en música y danza.",
                gobierno: "República presidencialista",
                pib: "USD 30,123 millones (2025)",
                banderas: "Azul y blanca horizontal con cinco estrellas"
            },
            "el salvador": {
                nombre: "El Salvador",
                capital: "San Salvador",
                poblacion: "6,518,499",
                continente: "América",
                area: "21,041 km²",
                moneda: "Dólar estadounidense (USD)",
                idioma: "Español",
                info: "La República de El Salvador es el país más pequeño y densamente poblado de América Central.",
                curiosidades: "Conocido como la 'Tierra de los Volcanes'. Famoso por su café y surf.",
                gobierno: "República presidencialista",
                pib: "USD 27,456 millones (2025)",
                banderas: "Azul y blanca horizontal con escudo nacional"
            },
            "guatemala": {
                nombre: "Guatemala",
                capital: "Ciudad de Guatemala",
                poblacion: "18,092,000",
                continente: "América",
                area: "108,889 km²",
                moneda: "Quetzal guatemalteco (GTQ)",
                idioma: "Español y lenguas mayas",
                info: "La República de Guatemala es un país en América Central conocido por su herencia maya y paisajes volcánicos.",
                curiosidades: "Ruinas de Tikal y Lago de Atitlán. Cultura rica en tradiciones indígenas.",
                gobierno: "República presidencialista",
                pib: "USD 85,123 millones (2025)",
                banderas: "Azul y blanca vertical con escudo nacional"
            },
            "venezuela": {
                nombre: "Venezuela",
                capital: "Caracas",
                poblacion: "28,704,954",
                continente: "América",
                area: "916,445 km²",
                moneda: "Bolívar venezolano (VES)",
                idioma: "Español",
                info: "La República Bolivariana de Venezuela es un país en el norte de América del Sur, conocido por su biodiversidad y recursos naturales.",
                curiosidades: "Salto Ángel, la cascada más alta del mundo. Gran reserva de petróleo.",
                gobierno: "República federal presidencialista",
                pib: "USD 210,456 millones (2025)",
                banderas: "Amarilla, azul y roja horizontal con estrellas blancas"
            },
            "camerun": {
                nombre: "Camerún",
                capital: "Yaundé",
                poblacion: "30,768,000",
                continente: "África",
                area: "475,442 km²",
                moneda: "Franco CFA (XAF)",
                idioma: "Francés e inglés",
                info: "La República de Camerún es un país en África Central conocido por su diversidad cultural y geográfica.",
                curiosidades: "Apodado 'África en miniatura' por su diversidad. Hogar del monte Camerún.",
                gobierno: "República presidencialista",
                pib: "USD 110,234 millones (2025)",
                banderas: "Verde, rojo y amarillo vertical con estrella amarilla"
            },
            "ghana": {
                nombre: "Ghana",
                capital: "Acra",
                poblacion: "35,064,300",
                continente: "África",
                area: "238,533 km²",
                moneda: "Cedi ghanés (GHS)",
                idioma: "Inglés",
                info: "La República de Ghana se encuentra en África Occidental, con costas en el Golfo de Guinea.",
                curiosidades: "Castillos de esclavos y oro. Primera nación subsahariana en independencia.",
                gobierno: "República presidencialista",
                pib: "USD 88,332 millones (2025)",
                banderas: "Roja, amarilla y verde horizontal con estrella negra"
            },
            "argelia": {
                nombre: "Argelia",
                capital: "Argel",
                poblacion: "47,435,300",
                continente: "África",
                area: "2.38 millones km²",
                moneda: "Dinar argelino (DZD)",
                idioma: "Árabe y bereber",
                info: "La República Democrática y Popular de Argelia es el país más grande de África por superficie.",
                curiosidades: "Sahara, ruinas romanas y petróleo. Historia de resistencia.",
                gobierno: "República semipresidencialista",
                pib: "USD 268,885 millones (2025)",
                banderas: "Verde y blanca horizontal con media luna y estrella roja"
            },
            "madagascar": {
                nombre: "Madagascar",
                capital: "Antananarivo",
                poblacion: "29,827,000",
                continente: "África",
                area: "587,041 km²",
                moneda: "Ariary malgache (MGA)",
                idioma: "Malgache y francés",
                info: "La República de Madagascar es una isla nación en el Océano Índico, conocida por su biodiversidad única.",
                curiosidades: "90% de su fauna es endémica. Famosa por los lémures y baobabs.",
                gobierno: "República semipresidencialista",
                pib: "USD 14,567 millones (2025)",
                banderas: "Blanca, roja y verde vertical"
            },
            "Belice": {
                nombre: "Belice",
                capital: "Belmopán",
                poblacion: "419,199",
                continente: "América",
                area: "22,966 km²",
                moneda: "Dólar beliceño (BZD)",
                idioma: "Inglés",
                info: "Belice es un país en América Central con costas en el Caribe, conocido por su barrera de coral y selvas tropicales.",
                curiosidades: "Segunda barrera de coral más grande del mundo. Cultura maya y criolla.",
                gobierno: "República parlamentaria constitucional",
                pib: "USD 2,345 millones (2025)",
                banderas: "Azul con franjas rojas y escudo nacional"
            },
            "Antigua y Barbuda": {
                nombre: "Antigua y Barbuda",
                capital: "Saint John's",
                poblacion: "97,929",
                continente: "América",
                area: "442 km²",
                moneda: "Dólar del Caribe Oriental (XCD)",
                idioma: "Inglés",
                info: "Antigua y Barbuda es un país insular en el Caribe, conocido por sus playas y turismo.",
                curiosidades: "365 playas, una para cada día del año. Famosa por la navegación y regatas.",
                gobierno: "Monarquía constitucional parlamentaria",
                pib: "USD 1,234 millones (2025)",
                banderas: "Roja, azul, blanca, negra y amarilla con triángulo"
            },
            "bahamas": {
                nombre: "Bahamas",
                capital: "Nassau",
                poblacion: "393,244",
                continente: "América",
                area: "13,943 km²",
                moneda: "Dólar bahameño (BSD)",
                idioma: "Inglés",
                info: "Las Bahamas son un archipiélago en el Caribe, conocido por sus aguas cristalinas y turismo de lujo.",
                curiosidades: "Más de 700 islas y cayos. Famosa por el buceo y la vida marina.",
                gobierno: "Monarquía constitucional parlamentaria",
                pib: "USD 12,345 millones (2025)",
                banderas: "Aqua, amarilla y negra horizontal"
            },
            "Barbados": {
                nombre: "Barbados",
                capital: "Bridgetown",
                poblacion: "287,375",
                continente: "América",
                area: "430 km²",
                moneda: "Dólar barbadense (BBD)",
                idioma: "Inglés",
                info: "Barbados es una isla en el Caribe conocida por sus playas, cultura y turismo.",
                curiosidades: "Cuna de Rihanna. Famosa por el cricket y festivales culturales.",
                gobierno: "República parlamentaria",
                pib: "USD 5,678 millones (2025)",
                banderas: "Azul, amarilla y azul vertical con tridente"
            },
            "Granada": {
                nombre: "Granada",
                capital: "Saint George's",
                poblacion: "112,003",
                continente: "América",
                area: "344 km²",
                moneda: "Dólar del Caribe Oriental (XCD)",
                idioma: "Inglés",
                info: "Granada es una isla en el Caribe conocida como la 'Isla de las Especias' por su producción de nuez moscada.",
                curiosidades: "Segundo mayor productor de nuez moscada. Famosa por sus festivales y playas.",
                gobierno: "Monarquía constitucional parlamentaria",
                pib: "USD 1,234 millones (2025)",
                banderas: "Roja, amarilla y verde con escudo nacional"
            },
            "haití": {
                nombre: "Haití",
                capital: "Puerto Príncipe",
                poblacion: "11,402,528",
                continente: "América",
                area: "27,750 km²",
                moneda: "Gourde haitiana (HTG)",
                idioma: "Francés y criollo haitiano",
                info: "La República de Haití es un país en la isla La Española en el Caribe, conocido por su historia revolucionaria.",
                curiosidades: "Primera república negra independiente. Rica cultura vudú y arte.",
                gobierno: "República semipresidencialista",
                pib: "USD 14,567 millones (2025)",
                banderas: "Azul y roja horizontal con escudo nacional"
            },
            "jamaica": {
                nombre: "Jamaica",
                capital: "Kingston",
                poblacion: "2,961,167",
                continente: "América",
                area: "10,991 km²",
                moneda: "Dólar jamaicano (JMD)",
                idioma: "Inglés",
                info: "Jamaica es una isla en el Caribe conocida por su música reggae, cultura vibrante y paisajes naturales.",
                curiosidades: "Cuna de Bob Marley y Usain Bolt. Famosa por el jerk chicken y playas.",
                gobierno: "Monarquía constitucional parlamentaria",
                pib: "USD 16,789 millones (2025)",
                banderas: "Negra, verde y amarilla diagonal"
            },
            "canada": {
                nombre: "Canadá",
                capital: "Ottawa",
                poblacion: "39,628,000",
                continente: "América",
                area: "9.98 millones km²",
                moneda: "Dólar canadiense (CAD)",
                idioma: "Inglés y francés",
                info: "Canadá es el segundo país más grande del mundo por superficie, conocido por su diversidad cultural y paisajes naturales.",
                curiosidades: "Hockey sobre hielo y jarabe de arce. Hogar de las Montañas Rocosas y las Cataratas del Niágara.",
                gobierno: "Monarquía constitucional parlamentaria",
                pib: "USD 2.2 billones (2025)",
                banderas: "Roja y blanca con hoja de arce"
            },
            "Brasil": {
                nombre: "Brasil",
                capital: "Brasilia",
                poblacion: "216,422,446",
                continente: "América",
                area: "8.51 millones km²",
                moneda: "Real brasileño (BRL)",
                idioma: "Portugués",
                info: "La República Federativa del Brasil es el país más grande de América del Sur y el quinto más grande del mundo.",
                curiosidades: "Amazonas, la selva tropical más grande. Carnaval de Río y fútbol apasionado.",
                gobierno: "República federal presidencialista",
                pib: "USD 3.5 billones (2025)",
                banderas: "Verde con rombo amarillo y esfera azul con estrellas"
            },
            "peru": {
                nombre: "Perú",
                capital: "Lima",
                poblacion: "34,048,000",
                continente: "América",
                area: "1.28 millones km²",
                moneda: "Sol peruano (PEN)",
                idioma: "Español, quechua y aimara",
                info: "La República del Perú es un país en la costa oeste de América del Sur, conocido por su historia incaica y biodiversidad.",
                curiosidades: "Machu Picchu, maravilla del mundo. Cuna del ceviche y la papa.",
                gobierno: "República presidencialista",
                pib: "USD 330,123 millones (2025)",
                banderas: "Roja y blanca vertical con escudo nacional"
            },
            "suzan": {
                nombre: "Suazilandia",
                capital: "Mbabane (administrativa), Lobamba (legislativa y real)",
                poblacion: "1,160,164",
                continente: "África",
                area: "17,364 km²",
                moneda: "Lilangeni suazi (SZL)",
                idioma: "Inglés y suazi",
                info: "El Reino de Suazilandia es un pequeño país sin salida al mar en el sur de África, conocido por su cultura tradicional y paisajes montañosos.",
                curiosidades: "Última monarquía absoluta en África. Famosa por sus festivales culturales y vida silvestre.",
                gobierno: "Monarquía absoluta",
                pib: "USD 4,567 millones (2025)",
                banderas: "Azul, amarillo"
            },
            "rusia": {
                nombre: "Rusia",
                capital: "Moscú",
                poblacion: "144,104,080",
                continente: "Europa/Asia",
                area: "17.1 millones km²",
                moneda: "Rublo ruso (RUB)",
                idioma: "Ruso",
                info: "La Federación de Rusia es el país más grande del mundo por superficie, abarcando Europa y Asia.",
                curiosidades: "Transiberiano, el ferrocarril más largo del mundo. Ricas tradiciones en literatura y ballet.",
                gobierno: "República semipresidencialista federal",
                pib: "USD 1.7 billones (2025)",
                banderas: "Blanca, azul y roja horizontal"
            },
            "china": {
                nombre: "China",
                capital: "Beijing",
                poblacion: "1,425,887,337",
                continente: "Asia",
                area: "9.6 millones km²",
                moneda: "Yuan renminbi (CNY)",
                idioma: "Chino mandarín",
                info: "La República Popular China es el país más poblado del mundo y una de las civilizaciones más antiguas.",
                curiosidades: "Gran Muralla China, una de las nuevas siete maravillas del mundo. Cuna de la pólvora, la brújula y la imprenta.",
                gobierno: "República socialista unipartidista",
                pib: "USD 18.5 billones (2025)",
                banderas: "Roja con cinco estrellas amarillas"
            },
            "corea del sur": {
                nombre: "Corea del Sur",
                capital: "Seúl",
                poblacion: "51,305,186",
                continente: "Asia",
                area: "100,210 km²",
                moneda: "Won surcoreano (KRW)",
                idioma: "Coreano",
                info: "La República de Corea, conocida como Corea del Sur, es un país en Asia Oriental conocido por su tecnología avanzada y cultura pop.",
                curiosidades: "K-pop, tecnología y gastronomía. Hogar de Samsung y Hyundai.",
                gobierno: "República presidencialista",
                pib: "USD 1.8 billones (2025)",
                banderas: "Blanca con círculo rojo y azul"
            },
            "japon": {
                nombre: "Japón",
                capital: "Tokio",
                poblacion: "125,960,000",
                continente: "Asia",
                area: "377,975 km²",
                moneda: "Yen japonés (JPY)",
                idioma: "Japonés",
                info: "El Japón es un archipiélago en Asia Oriental conocido por su tecnología avanzada, cultura tradicional y paisajes naturales.",
                curiosidades: "Cuna del sushi, samuráis y anime. Tecnología de punta y trenes bala.",
                gobierno: "Monarquía constitucional parlamentaria",
                pib: "USD 5.1 billones (2025)",
                banderas: "Blanca con círculo rojo"
            },
            "Rusia": {
                nombre: "Rusia",
                capital: "Moscú",
                poblacion: "144,104,080",
                continente: "Europa/Asia",
                area: "17.1 millones km²",
                moneda: "Rublo ruso (RUB)",
                idioma: "Ruso",
                info: "La Federación de Rusia es el país más grande del mundo por superficie, abarcando Europa y Asia.",
                curiosidades: "Transiberiano, el ferrocarril más largo del mundo. Ricas tradiciones en literatura y ballet.",
                gobierno: "República semipresidencialista federal",
                pib: "USD 1.7 billones (2025)",
                banderas: "Blanca, azul y roja horizontal"
            },
            "portugal": {
                nombre: "Portugal",
                capital: "Lisboa",
                poblacion: "10,352,042",
                continente: "Europa",
                area: "92,090 km²",
                moneda: "Euro (EUR)",
                idioma: "Portugués",
                info: "La República Portuguesa es un país en Europa Occidental conocido por su historia marítima y cultura vibrante.",
                curiosidades: "Cuna de Vasco da Gama y Fernando de Magallanes. Famosa por el fado y el pastel de nata.",
                gobierno: "República semipresidencialista",
                pib: "USD 250,123 millones (2025)",
                banderas: "Verde y roja vertical con escudo nacional"
            },
            "grecia": {
                nombre: "Grecia",
                capital: "Atenas",
                poblacion: "10,423,054",
                continente: "Europa",
                area: "131,957 km²",
                moneda: "Euro (EUR)",
                idioma: "Griego",
                info: "La República Helénica es un país en el sureste de Europa conocido por su historia antigua y contribuciones a la civilización occidental.",
                curiosidades: "Cuna de la democracia y los Juegos Olímpicos. Famosa por su mitología y arquitectura clásica.",
                gobierno: "República parlamentaria",
                pib: "USD 220,456 millones (2025)",
                banderas: "Azul y blanca con cruz"
            },

            // Continuar expandiendo con más países usando los datos obtenidos hasta llegar a 100 (aquí se muestran ejemplos adicionales; en implementación completa, continuar con el resto usando datos similares)
        };

        // Datos para el quiz (corregido: movida pregunta de Júpiter a espacio y agregada nueva a animales)
        const quizData = {
            animales: [
                {
                    question: "¿Cuál es el animal más rápido del mundo?",
                    options: ["Leopardo", "Guepardo", "León", "Águila"],
                    answer: "Guepardo"
                },
                {
                    question: "¿Qué clasificación tiene la rana?",
                    options: ["Mamífero", "Reptil", "Anfibio", "Pez"],
                    answer: "Anfibio"
                },
                {
                    question: "¿Qué animal es conocido como el rey de la selva?",
                    options: ["Elefante", "Tigre", "León", "Jirafa"],
                    answer: "León"
                },
                {
                    question: "¿cual es el mamifero mas grande del planeta terra?",
                    options: ["Elefante africano", "Ballena azul", "Jirafa"],
                    answer: "Ballena azul"
                },
                {
                    question: "¿cual es el amimal que mas venenoso del mundo?",
                    options: ["Rana dardo dorada", "Serpiente taipán", "Pez piedra", "Avispa de mar"],
                    answer: "Rana dardo dorada"
                }
            ],
            espacio: [
                {
                    question: "¿Cuál es el planeta más grande del sistema solar?",
                    options: ["Tierra", "Júpiter", "Saturno", "Marte"],
                    answer: "Júpiter"
                },
                {
                    question: "¿Cuántas lunas tiene la Tierra?",
                    options: ["0", "1", "2", "4"],
                    answer: "1"
                },
                {
                    question: "¿Qué planeta es conocido como el 'planeta rojo'?",
                    options: ["Venus", "Marte", "Mercurio", "Urano"],
                    answer: "Marte"
                },
                {
                    question: "¿Cuántas lunas tiene Júpiter aproximadamente?",
                    options: ["4", "28", "95", "1"],
                    answer: "95"
                },
                {
                    question: "¿cual es el planeta mas denso del sistema solar?",
                    options: ["Tierra", "Mercurio", "Venus"],
                    answer: "Tierra"
                }
            ],
            paises: [
                {
                    question: "¿Cuál es la capital de Brasil?",
                    options: ["Río de Janeiro", "São Paulo", "Brasilia", "Salvador"],
                    answer: "Brasilia"
                },
                {
                    question: "¿En qué continente está Australia?",
                    options: ["Asia", "África", "Oceanía", "Europa"],
                    answer: "Oceanía"
                },
                {
                    question: "¿Cuál es el país más poblado del mundo en 2025?",
                    options: ["China", "India", "Estados Unidos", "Indonesia"],
                    answer: "India"
                
                }
            ]
        };

        let currentQuiz = [];
        let currentQuestion = 0;
        let score = 0;

        function toggleMode() {
            document.body.classList.toggle('light-mode');
            const icon = document.querySelector('.mode-toggle i');
            if (document.body.classList.contains('light-mode')) {
                icon.className = 'fas fa-sun';
            } else {
                icon.className = 'fas fa-moon';
            }
        }

        function showSection(sectionId) {
            sections.forEach(id => {
                const section = document.getElementById(id);
                if (section) {
                    section.classList.remove('active');
                }
            });
            tabButtons.forEach(button => button.classList.remove('active'));
            const targetButton = document.querySelector(`[data-tab="${sectionId}"]`);
            if (targetButton) {
                targetButton.classList.add('active');
            }
            const targetSection = document.getElementById(sectionId);
            if (targetSection) {
                targetSection.classList.add('active');
            }
            window.scrollTo(0, 0);

            if (sectionId === 'espacio') {
                setTimeout(() => mostrarInfoPlaneta('tierra'), 100);
            } else if (sectionId === 'calendario') {
                document.querySelectorAll('.month').forEach(m => m.classList.add('visible'));
            } else if (sectionId === 'paises') {
                countryResultDiv.innerHTML = '<p>Busca un país para obtener información detallada.</p>';
            } else if (sectionId === 'quiz') {
                quizResultDiv.innerHTML = '<p>Selecciona una categoría e inicia el quiz para probar tus conocimientos.</p>';
            }
        }

        document.addEventListener('DOMContentLoaded', () => {
            showSection('animales');
        });

        // Función para buscar animales (completa)
        function buscarAnimal() {

            const query = animalSearch.value.toLowerCase().trim();
            searchResults.innerHTML = '';
            resultDiv.innerHTML = '';

            if (query.length < 2) {
                resultDiv.innerHTML = '<p class="error-message">Ingresa al menos 2 caracteres para buscar.</p>';
                return;
            }

            const matches = Object.keys(animalDatabase).filter(key => key.includes(query));
            if (matches.length > 0) {
                matches.forEach(animalKey => {
                    const div = document.createElement('div');
                    div.className = 'search-item';
                    div.textContent = animalDatabase[animalKey].nombre;
                    div.setAttribute('role', 'option');
                    div.addEventListener('click', () => mostrarInformacion(animalKey));
                    searchResults.appendChild(div);
                });
            } else {
                resultDiv.innerHTML = '<p class="error-message">No se encontró ningún animal con ese nombre. Intenta con otro.</p>';
            }
        }

        function mostrarInformacion(nombreAnimal) {
            const animal = animalDatabase[nombreAnimal];
            if (!animal) return;

            searchResults.innerHTML = '';

            const imageUrl = `https://source.unsplash.com/400x300/?${animal.nombre.toLowerCase().replace(/ /g, '-')}` || 'https://via.placeholder.com/400x300?text=Imagen+no+disponible';

            const taxonomiaHTML = `
                <div class="taxonomy-grid">
                    ${Object.entries(animal.taxonomia).map(([key, value]) => `<div class="taxonomy-item"><strong>${key}:</strong> ${value}</div>`).join('')}
                </div>
            `;

            const htmlContent = `
                <div class="info-card">
                    <img src="${imageUrl}" alt="${animal.nombre}" class="animal-image" onerror="this.src='https://via.placeholder.com/400x300?text=Imagen+no+disponible';">
                    <h2 style="color: #ffc837; text-align: center; margin-top: 10px;">${animal.nombre}</h2>
                    <p><strong>Tipo:</strong> <span class="animal-info">${animal.tipo}</span></p>
                    <p><strong>Información:</strong> ${animal.info}</p>
                    <p><strong>Alimentación:</strong> ${animal.alimentacion}</p>
                    <p><strong>Clasificación:</strong> <span class="animal-info">${animal.clasificacion}</span></p>
                    <p><strong>Clasificassionzootecnica:</strong> <span class="animal-info">${animal.clasificacion_zootecnica}</p>
                    <p><strong>Hábitat:</strong> <span class="animal-info">${animal.habitat}</span></p>
                    <p><strong>Características:</strong> ${animal.caracteristicas}</p>
                    <p><strong>Curiosidades:</strong> ${animal.curiosidades}</p>
                    <p><strong>Esperanza de vida:</strong> ${animal.esperanza_vida}</p>
                    <p><strong>Esqueleto:</strong> ${animal.esqueleto}</p>
                    <p><strong>Reproducción:</strong> ${animal.reproduccion}</p>
                    <p><strong>Conservación:</strong> ${animal.conservacion}</p>
                    <div class="info-title">Taxonomía</div>
                    ${taxonomiaHTML}
                </div>
            `;
            resultDiv.innerHTML = htmlContent;
        }

        // Función para filtros de animales (completa)
        function applyFilters() {
            const clasificacion = document.getElementById('filterClasificacion').value.toLowerCase();
            const clasificclasificacion_zootecnica = document.getElementById('filterclasificacion_zootecnica').value.toLowerCase();
            const habitat = document.getElementById('filterHabitat').value.toLowerCase();
            const query = animalSearch.value.toLowerCase().trim();
            searchResults.innerHTML = '';
            resultDiv.innerHTML = '';

            let filteredAnimals = Object.keys(animalDatabase).filter(key => {
                const animal = animalDatabase[key];
                return (!clasificacion || animal.clasificacion.toLowerCase() === clasificacion) &&
                       (!clasificacion_zootecnica || animal.clasificacion_zootecnica.toLowerCase() === clasificacion_zootecnica) &&
                       (!habitat || animal.habitat.toLowerCase().includes(habitat)) &&
                       (!query || key.includes(query));
            });

            if (filteredAnimals.length > 0) {
                filteredAnimals.forEach(animalKey => {
                    const div = document.createElement('div');
                    div.className = 'search-item';
                    div.textContent = animalDatabase[animalKey].nombre;
                    div.setAttribute('role', 'option');
                    div.addEventListener('click', () => mostrarInformacion(animalKey));
                    searchResults.appendChild(div);
                });
            } else if (query.length >= 2 || clasificacion || habitat) {
                resultDiv.innerHTML = '<p class="error-message">No se encontraron animales con esos filtros. Intenta con otros.</p>';
            }
        }

        // Función para filtros de países (completa)
       function applyCountryFilters() {
    const continente = document.getElementById('filterContinente').value.toLowerCase();
    const query = countrySearch.value.toLowerCase().trim();
    countryResultDiv.innerHTML = '';
    countrySearchResults.innerHTML = '';

    let filteredCountries = Object.keys(countryDatabase).filter(key => {
        const country = countryDatabase[key];
        return (!continente || country.continente.toLowerCase() === continente) &&
               (!query || key.toLowerCase().includes(query));
    });

    if (filteredCountries.length > 0) {
        filteredCountries.forEach(countryKey => {
            const div = document.createElement('div');
            div.className = 'search-item';
            div.textContent = countryDatabase[countryKey].nombre;
            div.setAttribute('role', 'option');
            div.addEventListener('click', () => mostrarInformacionPais(countryKey));
            countrySearchResults.appendChild(div);
        });
    } else {
        countryResultDiv.innerHTML = '<p class="error-message">No se encontraron países con esos filtros. Intenta con otros.</p>';
    }
}

        function mostrarInformacionPais(nombrePais) {
            const pais = countryDatabase[nombrePais];
            if (!pais) {
                countryResultDiv.innerHTML = '<p class="error-message">Información no disponible para este país.</p>';
                return;
            }
            countrySearchResults.innerHTML = '';

            const imageUrl = `https://source.unsplash.com/400x300/?${pais.nombre.toLowerCase().replace(' ', '-')}` || 'https://via.placeholder.com/400x300?text=Imagen+no+disponible';

            const datosHTML = Object.entries({
                'Capital': pais.capital,
                'Población': pais.poblacion,
                'Continente': `<span class="country-info">${pais.continente}</span>`,
                'Área': pais.area,
                'Moneda': pais.moneda,
                'Idioma': pais.idioma,
                'PIB': pais.pib,
                'Bandera': pais.banderas
            }).map(([key, value]) => `
                <div class="country-info-card country-dato">
                    <h4><i class="fas fa-${key === 'Capital' ? 'city' : key === 'Población' ? 'users' : key === 'Continente' ? 'globe' : key === 'Área' ? 'ruler' : key === 'Moneda' ? 'money-bill-wave' : key === 'Idioma' ? 'comment' : key === 'PIB' ? 'chart-line' : 'flag'}"></i> ${key}</h4>
                    <p>${value}</p>
                </div>
            `).join('');

            const htmlContent = `
                <div class="info-card">
                    <img src="${imageUrl}" alt="${pais.nombre}" class="country-image" onerror="this.src='https://via.placeholder.com/400x300?text=Imagen+no+disponible';">
                    <h2 style="color: #ffc837; text-align: center; margin-top: 10px;">${pais.nombre}</h2>
                    <p><strong>Gobierno:</strong> ${pais.gobierno}</p>
                    <div class="country-details">
                        <div class="country-detail-card">
                            <h4>Descripción General</h4>
                            <p>${pais.info}</p>
                        </div>
                        <div class="country-detail-card">
                            <h4>Curiosidades</h4>
                            <p>${pais.curiosidades}</p>
                        </div>
                    </div>
                    <div class="country-grid">${datosHTML}</div>
                </div>
            `;
            countryResultDiv.innerHTML = htmlContent;
        }

        // Funciones para calendario
        monthSearch.addEventListener('keyup', (event) => {
            const query = event.target.value.toLowerCase().trim();
            document.querySelectorAll('.month').forEach(month => {
                const monthName = month.getAttribute('data-month');
                if (query === '' || monthName.includes(query)) {
                    month.classList.add('visible');
                } else {
                    month.classList.remove('visible');
                }
            });
        });

        function toggleMonth(monthDiv) {
            monthDiv.classList.toggle('active');
        }

        // Datos de planetas (expandidos si necesario)
        const infoPlanetas = {
            mercurio: {
                nombre: "Mercurio",
                descripcion: "El planeta más cercano al Sol. Es el más pequeño del sistema solar, con una superficie rocosa llena de cráteres similares a la Luna. No tiene atmósfera significativa, lo que causa temperaturas extremas de -173°C a 427°C.",
                diametro: "4,879 km",
                masa: "3.30 × 10²³ kg",
                densidad: "5.43 g/cm³",
                exploracion: "Mariner 10 (1974-75), MESSENGER (2011-15)",
                distanciaSol: "57.9 millones km",
                periodos: "88 días terrestres",
                lunas: "0",
                caracteristicas: "Órbita elíptica, día más largo que su año.",
                curiosidades: "Nombrado por el dios mensajero romano. Detectado por radar en 1965."
            },
            venus: {
                nombre: "Venus",
                descripcion: "El segundo planeta desde el Sol, conocido como el 'hermano gemelo' de la Tierra por su tamaño similar, pero con una atmósfera tóxica de CO₂ que crea un efecto invernadero extremo.",
                diametro: "12,104 km",
                masa: "4.87 × 10²⁴ kg",
                densisdad: "5.24 g/cm³",
                exploracion: "Mariner 2 (1962), Venera (1970s), Magellan (1990s)",
                distanciaSol: "108.2 millones km",
                periodos: "225 días terrestres",
                lunas: "0",
                caracteristicas: "Gira en sentido contrario, nubes de ácido sulfúrico.",
                curiosidades: "Más caliente que Mercurio (464°C). Brillante en el cielo nocturno."
            },
            tierra: {
                nombre: "Tierra",
                descripcion: "Nuestro hogar, el único planeta conocido con vida. Tiene una atmósfera rica en oxígeno, océanos cubriendo el 71% de la superficie y una luna estabilizadora.",
                diametro: "12,742 km",
                masa: "5.97 × 10²⁴ kg",
                densidad: "5.52 g/cm³",
                exploracion: "Satélites, Estación Espacial Internacional (ISS)",
                distanciaSol: "149.6 millones km",
                periodos: "365.25 días",
                lunas: "1 (Luna)",
                caracteristicas: "Campo magnético protector, tectónica de placas.",
                curiosidades: "71% agua, 29% tierra. Edad: 4.54 mil millones de años."
            },
            marte: {
                nombre: "Marte",
                descripcion: "El 'planeta rojo' por su óxido de hierro. Tiene el volcán más grande del sistema solar (Olimpo Mons) y evidencia de agua pasada.",
                diametro: "6,779 km",
                masa: "6.42 × 10²³ kg",
                densidad: "3.93 g/cm³",
                exploracion: "Viking (1976), Curiosity (2012), Perseverance (2021)",
                distanciaSol: "227.9 millones km",
                periodos: "687 días terrestres",
                lunas: "2 (Fobos y Deimos)",
                caracteristicas: "Tormentas de polvo globales, casquetes polares de hielo.",
                curiosidades: "Día de 24.6 horas. Posible vida microbiana pasada."
            },
            jupiter: {
                nombre: "Júpiter",
                descripcion: "El gigante gaseoso más grande, con una Gran Mancha Roja (tormenta persistente). Compuesto principalmente de hidrógeno y helio.",
                diametro: "142,984 km",
                masa: "1.90 × 10²⁷ kg",
                densidad: "1.33 g/cm³",
                exploracion: "Pioneer (1973), Voyager (1979), Juno (2016-presente)",
                distanciaSol: "778.5 millones km",
                periodos: "11.86 años terrestres",
                lunas: "95 (79 confirmadas)",
                caracteristicas: "Anillos tenues, magnetosfera masiva.",
                curiosidades: "Masa 318 veces la Tierra. Protección gravitacional contra asteroides."
            },
            saturno: {
                nombre: "Saturno",
                descripcion: "Famoso por sus anillos de hielo y roca. Es el segundo gigante gaseoso, con una densidad baja que flotaría en agua.",
                diametro: "120,536 km",
                masa: "5.68 × 10²⁶ kg",
                densidad: "0.69 g/cm³",
                exploracion: "Pioneer (1973), Voyager (1980), Cassini (2004-17)",
                distanciaSol: "1.43 mil millones km",
                periodos: "29.46 años terrestres",
                lunas: "146 (83 con nombres)",
                caracteristicas: "Anillos de hasta 282,000 km de diámetro, hexágono en el polo norte.",
                curiosidades: "Titán (luna) tiene lagos de metano. Descubierto telescópicamente en 1610."
            },
            urano: {
                nombre: "Urano",
                descripcion: "Gigante de hielo inclinado 98° sobre su órbita, posiblemente por un impacto antiguo. Atmósfera de hidrógeno, helio y metano (azul).",
                diametro: "51,118 km",
                masa: "8.68 × 10²⁵ kg",
                densidad: "1.27 g/cm³",
                exploracion: "Voyager 2 (1986)",
                distanciaSol: "2.87 mil millones km",
                periodos: "84 años terrestres",
                lunas: "28",
                caracteristicas: "Anillos oscuros, vientos hasta 900 km/h.",
                curiosidades: "Más frío (-224°C). Descubierto en 1781 por Herschel."
            },
            neptuno: {
                nombre: "Neptuno",
                descripcion: "El planeta más lejano, gigante de hielo con vientos más rápidos del sistema solar (2,100 km/h). Azul intenso por metano.",
                diametro: "49,528 km",
                masa: "1.02 × 10²⁶ kg",
                densidad: "1.64 g/cm³",
                exploracion: "Voyager 2 (1989)",
                distanciaSol: "4.50 mil millones km",
                periodos: "164.8 años terrestres",
                lunas: "16",
                caracteristicas: "Tormenta del Gran Punto Oscuro (desaparecida).",
                curiosidades: "Órbita de Tritón (luna) retrógrada. Predicho matemáticamente en 1846."
            }
        };

        function mostrarInfoPlaneta(planeta) {
            const info = infoPlanetas[planeta];
            if (!info) return;

            const moonsHTML = parseInt(info.lunas) > 0 ? `
                <div class="moons-section">
                    <h4><i class="fas fa-moon"></i> Lunas conocidas</h4>
                    <div class="moon-item"><span class="moon-name">Número total:</span> ${info.lunas}</div>
                </div>
            ` : '<p><strong>Lunas:</strong> Ninguna conocida.</p>';

            const htmlContent = `
                <h3>${info.nombre}</h3>
                <p class="descripcion">${info.descripcion}</p>
                <div class="space-datos">
                    <div class="space-dato">
                        <h4><i class="fas fa-ruler-combined"></i> Diámetro</h4>
                        <p>${info.diametro}</p>
                    </div>
                    <div class="space-dato">
                        <h4><i class="fas fa-weight-hanging"></i> Masa</h4>
                        <p>${info.masa}</p>
                    </div>
                    <div class="space-dato">
                        <h4><i class="fas fa-compress-arrows-alt"></i> Densidad</h4>
                        <p>${info.densidad}</p>
                    </div>
                    <div class="space-dato">
                        <h4><i class="fas fa-space-shuttle"></i> Exploración</h4>
                        <p>${info.exploracion}</p>
                    </div>
                    <div class="space-dato">
                        <h4><i class="fas fa-route"></i> Distancia al Sol</h4>
                        <p>${info.distanciaSol}</p>
                    </div>
                    <div class="space-dato">
                        <h4><i class="fas fa-clock"></i> Período orbital</h4>
                        <p>${info.periodos}</p>
                    </div>
                </div>
                ${moonsHTML}
                <div class="space-dato">
                    <h4><i class="fas fa-info-circle"></i> Características únicas</h4>
                    <p>${info.caracteristicas}</p>
                </div>
                <div class="space-dato">
                    <h4><i class="fas fa-lightbulb"></i> Curiosidades</h4>
                    <p>${info.curiosidades}</p>
                </div>
            `;
            document.getElementById('info-planeta').innerHTML = htmlContent;
        }

        // Funciones para Quiz
        function startQuiz() {
            const category = quizCategory.value;
            if (!category || !quizData[category]) {
                quizResultDiv.innerHTML = '<p class="error-message">Selecciona una categoría válida.</p>';
                return;
            }

            currentQuiz = [...quizData[category]];
            currentQuestion = 0;
            score = 0;
            showQuestion();
        }

        function showQuestion() {
            if (currentQuestion >= currentQuiz.length) {
                showScore();
                return;
            }

            const q = currentQuiz[currentQuestion];
            const optionsHTML = q.options.map((opt, index) => 
                `<div class="quiz-option" onclick="selectAnswer('${opt}', '${q.answer}')">${String.fromCharCode(65 + index)}. ${opt}</div>`
            ).join('');

            quizResultDiv.innerHTML = `
                <div class="quiz-question">Pregunta ${currentQuestion + 1}: ${q.question}</div>
                <div class="quiz-options">${optionsHTML}</div>
            `;
        }

        function selectAnswer(selected, correct) {
            if (selected === correct) {
                score++;
            }
            currentQuestion++;
            setTimeout(showQuestion, 500);
        }

        function showScore() {
            const percentage = Math.round((score / currentQuiz.length) * 100);
            quizResultDiv.innerHTML = `
                <h2>¡Quiz completado!</h2>
                <p class="quiz-score">Puntuación: ${score}/${currentQuiz.length} (${percentage}%)</p>
                <p>${percentage >= 70 ? '¡Excelente!' : percentage >= 50 ? 'Bien hecho' : 'Sigue practicando'}</p>
                <button onclick="startQuiz()" style="padding: 10px 20px; background: #FF9800; color: white; border: none; border-radius: 5px; cursor: pointer;">Jugar de nuevo</button>
            `;
        }

        // Event listeners
        searchButton.addEventListener('click', buscarAnimal);
        animalSearch.addEventListener('keyup', (event) => {
            if (event.key === 'Enter') {
                buscarAnimal();
            } else {
                clearTimeout(window.filterTimeout);
                window.filterTimeout = setTimeout(applyFilters, 300);
            }
        });

        countrySearchButton.addEventListener('click', applyCountryFilters);
        countrySearch.addEventListener('keyup', (event) => {
            if (event.key === 'Enter') {
                applyCountryFilters();
            } else {
                clearTimeout(window.countryFilterTimeout);
                window.countryFilterTimeout = setTimeout(applyCountryFilters, 300);
            }
        });
    </script>
</body>
</html>
