# te-amo
Un regalito para mi amor 💘
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Te amo mi niña bonita 💚</title>
  <style>
    body {
      margin: 0;
      background: black;
      overflow: hidden;
      color: #0F0;
      font-family: monospace, monospace;
    }
    canvas {
      display: block;
      position: fixed;
      top: 0; left: 0;
      width: 100vw;
      height: 100vh;
      z-index: -1;
    }
    .mensaje {
      position: absolute;
      top: 40%;
      width: 100%;
      text-align: center;
      font-size: 3em;
      color: #0F0;
      text-shadow: 0 0 10px #0f0;
      font-family: 'Courier New', Courier, monospace;
      user-select: none;
    }
  </style>
</head>
<body>
  <canvas id="matrix"></canvas>
  <div class="mensaje">Te amo mi niña bonita 💚</div>

  <script>
    const canvas = document.getElementById('matrix');
    const ctx = canvas.getContext('2d');

    // Ajustar tamaño
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;

    const letters = 'Te amo mi niña bonita ';
    const fontSize = 20;
    const columns = canvas.width / fontSize;

    // Array para las posiciones y la letra actual por columna
    const drops = [];
    for(let x = 0; x < columns; x++) {
      drops[x] = Math.floor(Math.random() * letters.length);
    }

    function draw() {
      // Fondo semi-transparente para efecto de "trazo"
      ctx.fillStyle = 'rgba(0, 0, 0, 0.05)';
      ctx.fillRect(0, 0, canvas.width, canvas.height);

      ctx.fillStyle = '#0F0'; // Verde matrix
      ctx.font = fontSize + 'px monospace';

      for(let i = 0; i < drops.length; i++) {
        const text = letters.charAt(drops[i]);
        ctx.fillText(text, i * fontSize, drops[i] * fontSize);

        // Reiniciar posición cuando baja fuera de pantalla
        if(drops[i] * fontSize > canvas.height && Math.random() > 0.975) {
          drops[i] = 0;
        }

        drops[i]++;
      }
    }

    setInterval(draw, 50);

    // Ajustar tamaño si se cambia la ventana
    window.addEventListener('resize', () => {
      canvas.width = window.innerWidth;
      canvas.height = window.innerHeight;
    });
  </script>
</body>
</html>
