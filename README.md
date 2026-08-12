<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Verificación del Script</title>
    <style>
        body {
            background-color: #1e1e1e;
            color: white;
            font-family: Arial, sans-serif;
            text-align: center;
            padding: 50px;
        }
        .alerta {
            color: #ff4c4c;
            font-weight: bold;
            font-size: 24px;
        }
        .info {
            margin-top: 20px;
            font-size: 18px;
            color: #aaaaaa;
        }
        .ad-container {
            margin-top: 40px; 
            padding: 30px; 
            border: 2px dashed #555;
            border-radius: 10px;
            background-color: #2a2a2a;
        }
        .ad-btn {
            display: inline-block; 
            padding: 15px 30px; 
            background-color: #ff4c4c; 
            color: white; 
            text-decoration: none; 
            font-size: 22px; 
            font-weight: bold; 
            border-radius: 8px; 
            cursor: pointer; 
            border: 2px solid white;
            transition: 0.2s;
        }
        .ad-btn:hover {
            background-color: #ff2a2a;
            transform: scale(1.05);
        }
    </style>
</head>
<body>

    <h1>Verificación del Script Activa</h1>
    <p class="alerta">⚠️ NO CIERRES ESTA PÁGINA ⚠️</p>
    <p class="info">Si cierras esta pestaña, el script de Roblox se desactivará automáticamente y serás expulsado de la partida.</p>

    <!-- Contenedor del anuncio de Adsterra -->
    <div class="ad-container">
        <p style="margin-bottom: 20px; font-size: 18px;">Apoya este script haciendo clic en el botón de abajo:</p>

        <!-- Botón del Direct Link con target="_blank" para no cerrar esta pestaña -->
        <a href="https://www.effectivecpmnetwork.com/i1nqhh7zb?key=bd2fca3e002c291d9ace7b7e65943b8f" 
           target="_blank" 
           class="ad-btn">
            Ver Anuncio Patrocinado
        </a>
    </div>

    <!-- Script de comunicación con tu Firebase -->
    <script>
        const urlParams = new URLSearchParams(window.location.search);
        const usuario = urlParams.get('usuario');

        // URL exacta de tu Firebase
        const firebaseUrl = `https://data-base-4e0f8-default-rtdb.firebaseio.com/usuarios/${usuario}.json`;

        if (usuario) {
            console.log("Conectado como: " + usuario);

            function enviarLatido() {
                const tiempoActual = Math.floor(Date.now() / 1000); 
                
                fetch(firebaseUrl, {
                    method: 'PATCH',
                    headers: { 'Content-Type': 'application/json' },
                    body: JSON.stringify({ ultimo_latido: tiempoActual })
                })
                .then(response => console.log("Latido enviado al servidor: " + tiempoActual))
                .catch(error => console.error("Error al enviar latido: ", error));
            }

            // Enviar el primer latido al instante y luego cada 5 segundos
            enviarLatido();
            setInterval(enviarLatido, 5000); 

        } else {
            document.body.innerHTML = "<h1 style='color:red;'>Error: Falta tu nombre de usuario. Vuelve a ejecutar el script en Roblox.</h1>";
        }
    </script>
</body>
</html>
