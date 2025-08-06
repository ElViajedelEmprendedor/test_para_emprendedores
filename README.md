# test_para_emprendedores
Un programa de 12 semanas para descubrir tu propósito, sanar tu historia y materializar  el emprendimiento de tu alma.
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>¿Estás Listo para Emprender?</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Arial', sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            padding: 20px;
        }

        .container {
            max-width: 800px;
            margin: 0 auto;
            background: rgba(255, 255, 255, 0.95);
            border-radius: 20px;
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
            overflow: hidden;
            backdrop-filter: blur(10px);
        }

        .header {
            background: linear-gradient(135deg, #ff6b6b, #ee5a24);
            color: white;
            padding: 40px;
            text-align: center;
            position: relative;
            overflow: hidden;
        }

        .header::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: repeating-linear-gradient(
                45deg,
                transparent,
                transparent 20px,
                rgba(255,255,255,0.05) 20px,
                rgba(255,255,255,0.05) 40px
            );
            animation: slide 20s linear infinite;
        }

        @keyframes slide {
            0% { transform: translate(-50%, -50%) rotate(0deg); }
            100% { transform: translate(-50%, -50%) rotate(360deg); }
        }

        .header h1 {
            font-size: 2.5em;
            margin-bottom: 10px;
            position: relative;
            z-index: 1;
        }

        .header p {
            font-size: 1.2em;
            opacity: 0.9;
            position: relative;
            z-index: 1;
        }

        .content {
            padding: 40px;
        }

        .intro {
            background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
            color: white;
            padding: 30px;
            border-radius: 15px;
            margin-bottom: 30px;
            box-shadow: 0 10px 30px rgba(240, 147, 251, 0.3);
        }

        .question-section {
            margin-bottom: 40px;
            padding: 30px;
            background: linear-gradient(135deg, #ffecd2 0%, #fcb69f 100%);
            border-radius: 15px;
            box-shadow: 0 8px 25px rgba(252, 182, 159, 0.3);
            transform: translateY(10px);
            opacity: 0;
            animation: fadeInUp 0.6s ease forwards;
        }

        .question-section:nth-child(even) {
            background: linear-gradient(135deg, #a8edea 0%, #fed6e3 100%);
            box-shadow: 0 8px 25px rgba(168, 237, 234, 0.3);
        }

        .question-section:nth-child(odd) {
            animation-delay: 0.1s;
        }

        .question-section:nth-child(even) {
            animation-delay: 0.2s;
        }

        @keyframes fadeInUp {
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .category-title {
            font-size: 1.4em;
            font-weight: bold;
            color: #2c3e50;
            margin-bottom: 20px;
            text-align: center;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .question {
            margin-bottom: 25px;
            padding: 20px;
            background: rgba(255, 255, 255, 0.8);
            border-radius: 10px;
            border-left: 4px solid #3498db;
            transition: all 0.3s ease;
        }

        .question:hover {
            transform: translateX(5px);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }

        .question h3 {
            color: #2c3e50;
            margin-bottom: 15px;
            font-size: 1.1em;
        }

        .question-subtitle {
            font-style: italic;
            color: #7f8c8d;
            margin-bottom: 15px;
            font-size: 0.9em;
        }

        .options {
            display: flex;
            flex-direction: column;
            gap: 10px;
        }

        .option {
            display: flex;
            align-items: center;
            padding: 12px;
            background: rgba(255, 255, 255, 0.9);
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.3s ease;
            border: 2px solid transparent;
        }

        .option:hover {
            background: rgba(52, 152, 219, 0.1);
            border-color: #3498db;
            transform: scale(1.02);
        }

        .option input[type="radio"] {
            margin-right: 12px;
            transform: scale(1.2);
        }

        .option label {
            cursor: pointer;
            flex: 1;
        }

        .calculate-btn {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 20px 40px;
            border: none;
            border-radius: 50px;
            font-size: 1.2em;
            font-weight: bold;
            cursor: pointer;
            display: block;
            margin: 40px auto;
            transition: all 0.3s ease;
            box-shadow: 0 10px 30px rgba(102, 126, 234, 0.4);
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .calculate-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 15px 40px rgba(102, 126, 234, 0.6);
        }

        .calculate-btn:active {
            transform: translateY(-1px);
        }

        .result {
            margin-top: 40px;
            padding: 40px;
            border-radius: 15px;
            text-align: center;
            font-size: 1.1em;
            line-height: 1.6;
            display: none;
            animation: resultAppear 0.8s ease;
        }

        @keyframes resultAppear {
            from {
                opacity: 0;
                transform: scale(0.9);
            }
            to {
                opacity: 1;
                transform: scale(1);
            }
        }

        .result.high {
            background: linear-gradient(135deg, #11998e 0%, #38ef7d 100%);
            color: white;
            box-shadow: 0 15px 40px rgba(17, 153, 142, 0.4);
        }

        .result.medium {
            background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
            color: white;
            box-shadow: 0 15px 40px rgba(240, 147, 251, 0.4);
        }

        .result.low {
            background: linear-gradient(135deg, #ffecd2 0%, #fcb69f 100%);
            color: #2c3e50;
            box-shadow: 0 15px 40px rgba(252, 182, 159, 0.4);
        }

        .result h2 {
            font-size: 2em;
            margin-bottom: 20px;
            text-transform: uppercase;
            letter-spacing: 2px;
        }

        .score {
            font-size: 3em;
            font-weight: bold;
            margin: 20px 0;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
        }

        .recommendations {
            background: rgba(255, 255, 255, 0.2);
            padding: 25px;
            border-radius: 10px;
            margin-top: 25px;
            text-align: left;
        }

        .recommendations h3 {
            margin-bottom: 15px;
            font-size: 1.3em;
        }

        .recommendations ul {
            list-style: none;
            padding: 0;
        }

        .recommendations li {
            padding: 8px 0;
            border-bottom: 1px solid rgba(255, 255, 255, 0.3);
        }

        .recommendations li:before {
            content: "💡 ";
            margin-right: 8px;
        }

        @media (max-width: 768px) {
            .container {
                margin: 10px;
                border-radius: 15px;
            }
            
            .header {
                padding: 30px 20px;
            }
            
            .header h1 {
                font-size: 2em;
            }
            
            .content {
                padding: 20px;
            }
            
            .question-section {
                padding: 20px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>🚀 ¿Estás listo para emprender?</h1>
            <p>Evaluación Reflexiva para Futuros Empresarios</p>
        </div>
        
        <div class="content">
            <div class="intro">
                <h2>Instrucciones</h2>
                <p>Este test está diseñado para ayudarte a reflexionar sobre tu preparación para el emprendimiento. Responde con honestidad y tómate tu tiempo para pensar en cada pregunta. No hay respuestas correctas o incorrectas, solo diferentes niveles de preparación.</p>
            </div>

            <form id="entrepreneurTest">
                <!-- Mentalidad y Motivación -->
                <div class="question-section">
                    <div class="category-title">🧠 Mentalidad y Motivación</div>
                    
                    <div class="question">
                        <h3>1. ¿Cuál es tu principal motivación para emprender?</h3>
                        <div class="question-subtitle">Reflexiona sobre el motor que te impulsa</div>
                        <div class="options">
                            <div class="option">
                                <input type="radio" name="q1" value="3" id="q1a">
                                <label for="q1a">Resolver un problema real que me apasiona y crear valor genuino</label>
                            </div>
                            <div class="option">
                                <input type="radio" name="q1" value="2" id="q1b">
                                <label for="q1b">Tener independencia financiera y profesional</label>
                            </div>
                            <div class="option">
                                <input type="radio" name="q1" value="1" id="q1c">
                                <label for="q1c">Hacer dinero rápido o seguir una tendencia</label>
                            </div>
                            <div class="option">
                                <input type="radio" name="q1" value="0" id="q1d">
                                <label for="q1d">No tengo una motivación clara aún</label>
                            </div>
                        </div>
                    </div>

                    <div class="question">
                        <h3>2. Cuando enfrentas un fracaso significativo, tu reacción típica es:</h3>
                        <div class="question-subtitle">La resiliencia es clave en el emprendimiento</div>
                        <div class="options">
                            <div class="option">
                                <input type="radio" name="q2" value="3" id="q2a">
                                <label for="q2a">Analizo qué salió mal, aprendo y ajusto mi estrategia</label>
                            </div>
                            <div class="option">
                                <input type="radio" name="q2" value="2" id="q2b">
                                <label for="q2b">Me siento mal temporalmente, pero me recupero y sigo adelante</label>
                            </div>
                            <div class="option">
                                <input type="radio" name="q2" value="1" id="q2c">
                                <label for="q2c">Me desanimo considerablemente y necesito tiempo para recuperarme</label>
                            </div>
                            <div class="option">
                                <input type="radio" name="q2" value="0" id="q2d">
                                <label for="q2d">Tiendo a abandonar o culpar a factores externos</label>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Recursos y Preparación -->
                <div class="question-section">
                    <div class="category-title">💰 Recursos y Preparación Financiera</div>
                    
                    <div class="question">
                        <h3>3. ¿Tienes una idea de negocio en la que puedas emprender tu emprendimiento?</h3>
                        <div class="question-subtitle">Una idea clara y viable es el punto de partida de todo emprendimiento</div>
                        <div class="options">
                            <div class="option">
                                <input type="radio" name="q3" value="3" id="q3a">
                                <label for="q3a">Sí, tengo una idea específica que he validado con potenciales clientes</label>
                            </div>
                            <div class="option">
                                <input type="radio" name="q3" value="2" id="q3b">
                                <label for="q3b">Tengo una idea clara pero aún necesito validarla en el mercado</label>
                            </div>
                            <div class="option">
                                <input type="radio" name="q3" value="1" id="q3c">
                                <label for="q3c">Tengo varias ideas pero no he decidido cuál desarrollar</label>
                            </div>
                            <div class="option">
                                <input type="radio" name="q3" value="0" id="q3d">
                                <label for="q3d">No tengo una idea concreta, solo el deseo de emprender</label>
                            </div>
                        </div>
                    </div>

                    <div class="question">
                        <h3>4. ¿Cuál es tu situación financiera actual para emprender?</h3>
                        <div class="question-subtitle">La estabilidad financiera es crucial para tomar riesgos calculados</div>
                        <div class="options">
                            <div class="option">
                                <input type="radio" name="q5" value="3" id="q5a">
                                <label for="q4a">Tengo ahorros suficientes para 12+ meses sin ingresos</label>
                            </div>
                            <div class="option">
                                <input type="radio" name="q4" value="2" id="q4b">
                                <label for="q4b">Puedo mantenerme 6-12 meses con mis ahorros</label>
                            </div>
                            <div class="option">
                                <input type="radio" name="q4" value="1" id="q4c">
                                <label for="q4c">Tengo algunos ahorros pero tendría que conseguir ingresos pronto</label>
                            </div>
                            <div class="option">
                                <input type="radio" name="q4" value="0" id="q4d">
                                <label for="q4d">Vivo al día o dependería completamente del emprendimiento</label>
                            </div>
                        </div>
                    </div>

                    <div class="question">
                        <h3>5. Tu nivel de conocimiento sobre el mercado donde quieres emprender es:</h3>
                        <div class="question-subtitle">El conocimiento del mercado reduce significativamente el riesgo</div>
                        <div class="options">
                            <div class="option">
                                <input type="radio" name="q4" value="3" id="q4a">
                                <label for="q5a">Profundo: conozco a mis competidores, clientes y tendencias</label>
                            </div>
                            <div class="option">
                                <input type="radio" name="q5" value="2" id="q5b">
                                <label for="q5b">Bueno: he investigado y tengo una comprensión sólida</label>
                            </div>
                            <div class="option">
                                <input type="radio" name="q5" value="1" id="q5c">
                                <label for="q5c">Básico: tengo una idea general pero necesito investigar más</label>
                            </div>
                            <div class="option">
                                <input type="radio" name="q5" value="0" id="q5d">
                                <label for="q5d">Limitado: no he investigado a fondo el mercado</label>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Habilidades y Competencias -->
                <div class="question-section">
                    <div class="category-title">🎯 Habilidades y Competencias</div>
                    
                    <div class="question">
                        <h3>6. ¿Cómo describirías tus habilidades de liderazgo y gestión de equipos?</h3>
                        <div class="question-subtitle">El emprendimiento eventualmente requiere liderar y motivar a otros</div>
                        <div class="options">
                            <div class="option">
                                <input type="radio" name="q6" value="3" id="q6a">
                                <label for="q6a">Tengo experiencia liderando equipos y me siento cómodo haciéndolo</label>
                            </div>
                            <div class="option">
                                <input type="radio" name="q6" value="2" id="q6b">
                                <label for="q6b">He liderado en algunas ocasiones con resultados mixtos</label>
                            </div>
                            <div class="option">
                                <input type="radio" name="q6" value="1" id="q6c">
                                <label for="q6c">Prefiero trabajar solo pero estoy dispuesto a aprender</label>
                            </div>
                            <div class="option">
                                <input type="radio" name="q6" value="0" id="q6d">
                                <label for="q6d">No tengo experiencia ni interés en liderar equipos</label>
                            </div>
                        </div>
                    </div>

                    <div class="question">
                        <h3>7. Tu capacidad para tomar decisiones bajo presión e incertidumbre es:</h3>
                        <div class="question-subtitle">Los emprendedores constantemente enfrentan decisiones difíciles con información limitada</div>
                        <div class="options">
                            <div class="option">
                                <input type="radio" name="q7" value="3" id="q7a">
                                <label for="q7a">Excelente: puedo decidir rápidamente con información limitada</label>
                            </div>
                            <div class="option">
                                <input type="radio" name="q7" value="2" id="q7b">
                                <label for="q7b">Buena: aunque a veces me toma tiempo, puedo decidir</label>
                            </div>
                            <div class="option">
                                <input type="radio" name="q7" value="1" id="q7c">
                                <label for="q7c">Regular: me paralizo con demasiadas opciones</label>
                            </div>
                            <div class="option">
                                <input type="radio" name="q7" value="0" id="q7d">
                                <label for="q7d">Pobre: evito tomar decisiones difíciles</label>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Relaciones y Red de Contactos -->
                <div class="question-section">
                    <div class="category-title">🤝 Relaciones y Networking</div>
                    
                    <div class="question">
                        <h3>8. ¿Cómo es tu red de contactos profesionales actual?</h3>
                        <div class="question-subtitle">Las conexiones pueden abrir puertas y proporcionar recursos valiosos</div>
                        <div class="options">
                            <div class="option">
                                <input type="radio" name="q8" value="3" id="q8a">
                                <label for="q8a">Amplia: tengo contactos en mi industria y áreas relacionadas</label>
                            </div>
                            <div class="option">
                                <input type="radio" name="q8" value="2" id="q8b">
                                <label for="q8b">Moderada: conozco algunas personas clave en mi área</label>
                            </div>
                            <div class="option">
                                <input type="radio" name="q8" value="1" id="q8c">
                                <label for="q8c">Limitada: principalmente colegas cercanos y amigos</label>
                            </div>
                            <div class="option">
                                <input type="radio" name="q8" value="0" id="q8d">
                                <label for="q8d">Muy pequeña: no tengo una red profesional desarrollada</label>
                            </div>
                        </div>
                    </div>

                    <div class="question">
                        <h3>9. ¿Tienes acceso a mentores o asesores experimentados?</h3>
                        <div class="question-subtitle">La guía de personas con experiencia puede acelerar tu aprendizaje</div>
                        <div class="options">
                            <div class="option">
                                <input type="radio" name="q9" value="3" id="q9a">
                                <label for="q9a">Sí, tengo mentores establecidos que me apoyan</label>
                            </div>
                            <div class="option">
                                <input type="radio" name="q9" value="2" id="q9b">
                                <label for="q9b">Tengo algunas personas a quienes puedo consultar ocasionalmente</label>
                            </div>
                            <div class="option">
                                <input type="radio" name="q9" value="1" id="q9c">
                                <label for="q9c">No tengo mentores pero sé cómo encontrarlos</label>
                            </div>
                            <div class="option">
                                <input type="radio" name="q9" value="0" id="q9d">
                                <label for="q9d">No tengo acceso a mentores ni sé cómo conseguirlos</label>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Tolerancia al Riesgo y Compromiso -->
                <div class="question-section">
                    <div class="category-title">⚡ Tolerancia al Riesgo y Compromiso</div>
                    
                    <div class="question">
                        <h3>10. ¿Estás dispuesto a trabajar 60-80 horas semanales durante los primeros años?</h3>
                        <div class="question-subtitle">El emprendimiento inicial suele requerir un compromiso de tiempo intenso</div>
                        <div class="options">
                            <div class="option">
                                <input type="radio" name="q10" value="3" id="q10a">
                                <label for="q10a">Absolutamente, estoy preparado para ese nivel de dedicación</label>
                            </div>
                            <div class="option">
                                <input type="radio" name="q10" value="2" id="q10b">
                                <label for="q10b">Sí, aunque preferiría mantener cierto equilibrio</label>
                            </div>
                            <div class="option">
                                <input type="radio" name="q10" value="1" id="q10c">
                                <label for="q10c">Solo temporalmente, no como estilo de vida permanente</label>
                            </div>
                            <div class="option">
                                <input type="radio" name="q10" value="0" id="q10d">
                                <label for="q10d">No, valoro demasiado mi tiempo personal y familiar</label>
                            </div>
                        </div>
                    </div>

                    <div class="question">
                        <h3>11. Si tu emprendimiento no genera ingresos en los primeros 18 meses:</h3>
                        <div class="question-subtitle">Esta pregunta evalúa tu compromiso a largo plazo y perseverancia</div>
                        <div class="options">
                            <div class="option">
                                <input type="radio" name="q11" value="3" id="q11a">
                                <label for="q11a">Evaluaría, ajustaría la estrategia y continuaría si veo progreso</label>
                            </div>
                            <div class="option">
                                <input type="radio" name="q11" value="2" id="q11b">
                                <label for="q11b">Buscaría financiamiento o socios para continuar</label>
                            </div>
                            <div class="option">
                                <input type="radio" name="q11" value="1" id="q11c">
                                <label for="q11c">Probablemente buscaría un empleo mientras continúo como proyecto paralelo</label>
                            </div>
                            <div class="option">
                                <input type="radio" name="q11" value="0" id="q11d">
                                <label for="q11d">Abandonaría el proyecto y buscaría otras opciones</label>
                            </div>
                        </div>
                    </div>
                </div>

                <button type="button" class="calculate-btn" onclick="calculateResult()">
                    🎯 Evaluar Mi Preparación Emprendedora
                </button>
            </form>

            <div id="result" class="result"></div>
        </div>
    </div>

    <script>
        function calculateResult() {
            const form = document.getElementById('entrepreneurTest');
            const formData = new FormData(form);
            let totalScore = 0;
            let answeredQuestions = 0;

            // Verificar que todas las preguntas están respondidas
            for (let i = 1; i <= 11; i++) {
                const answer = formData.get(`q${i}`);
                if (answer) {
                    totalScore += parseInt(answer);
                    answeredQuestions++;
                }
            }

            if (answeredQuestions < 11) {
                alert('Por favor, responde todas las preguntas antes de continuar.');
                return;
            }

            const percentage = Math.round((totalScore / 33) * 100);
            const resultDiv = document.getElementById('result');
            
            let resultClass, title, message, recommendations;

            if (percentage >= 80) {
                resultClass = 'high';
                title = '🚀 ¡Excelente! Estás muy preparado';
                message = `Tu puntuación de ${percentage}% indica que tienes una base sólida para emprender. Demuestras una mentalidad emprendedora madura, recursos adecuados y las habilidades necesarias para enfrentar los desafíos del emprendimiento.`;
                recommendations = [
                    'Desarrolla un plan de negocio detallado y comienza a ejecutar',
                    'Busca oportunidades de financiamiento si es necesario',
                    'Conecta con otros emprendedores para intercambiar experiencias',
                    'Considera empezar como proyecto paralelo para reducir riesgos',
                    'Establece métricas claras para medir tu progreso'
                ];
            } else if (percentage >= 60) {
                resultClass = 'medium';
                title = '⚡ Tienes potencial, pero necesitas prepararte más';
                message = `Con ${percentage}% de preparación, tienes una base decente pero hay áreas importantes que necesitas fortalecer antes de dar el gran salto. El emprendimiento es posible, pero requerirá más preparación.`;
                recommendations = [
                    'Identifica y trabaja en tus áreas más débiles',
                    'Considera ganar más experiencia en tu campo profesional',
                    'Desarrolla tu red de contactos profesionales',
                    'Ahorra más capital antes de emprender',
                    'Busca un mentor o asesor experimentado',
                    'Practica habilidades de liderazgo y toma de decisiones'
                ];
            } else {
                resultClass = 'low';
                title = '🌱 Necesitas más preparación antes de emprender';
                message = `Tu puntuación de ${percentage}% sugiere que aún no estás listo para emprender de manera independiente. Esto no es negativo, significa que tienes la oportunidad de prepararte mejor y aumentar significativamente tus probabilidades de éxito.`;
                recommendations = [
                    'Desarrolla experiencia laboral en tu área de interés',
                    'Mejora tu situación financiera personal',
                    'Estudia sobre emprendimiento y gestión de negocios',
                    'Comienza con proyectos pequeños o freelancing',
                    'Construye una red de contactos profesionales',
                    'Considera trabajar en una startup para ganar experiencia',
                    'Desarrolla habilidades de liderazgo y comunicación'
                ];
            }

            resultDiv.innerHTML = `
                <h2>${title}</h2>
                <div class="score">${percentage}%</div>
                <p>${message}</p>
                <div class="recommendations">
                    <h3>🎯 Recomendaciones para tu siguiente paso:</h3>
                    <ul>
                        ${recommendations.map(rec => `<li>${rec}</li>`).join('')}
                    </ul>
                </div>
            `;
            
            resultDiv.className = `result ${resultClass}`;
            resultDiv.style.display = 'block';
            
            // Scroll to results
            resultDiv.scrollIntoView({ behavior: 'smooth' });
        }

        // Add some interactive animations
        document.addEventListener('DOMContentLoaded', function() {
            const options = document.querySelectorAll('.option');
            
            options.forEach(option => {
                option.addEventListener('click', function() {
                    // Remove selection from other options in the same question
                    const questionOptions = this.closest('.question').querySelectorAll('.option');
                    questionOptions.forEach(opt => opt.style.background = 'rgba(255, 255, 255, 0.9)');
                    
                    // Highlight selected option
                    this.style.background = 'rgba(52, 152, 219, 0.2)';
                });
            });
        });
    </script>
</body>
</html>
