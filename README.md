<!index.html
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>WLD Bomb Game</title>
  <style>
    body {
      margin: 0;
      font-family: Arial, sans-serif;
      background: #111;
      color: #fff;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
    }

    canvas {
      border: 2px solid white;
      background: #222;
    }

    button {
      margin-top: 10px;
      padding: 10px 20px;
      font-size: 16px;
      cursor: pointer;
    }

    h1 {
      margin-bottom: 10px;
    }
  </style>
</head>
<body>
  <h1>💣 WLD Bomb 2D</h1>
  <canvas id="gameCanvas" width="400" height="300"></canvas>
  <h3 id="status">Jugador: 1 | Tiempo: <span id="timer">30</span>s</h3>
  <button onclick="passBomb()">Pasar Bomba</button>

  <script>
    const canvas = document.getElementById('gameCanvas');
    const ctx = canvas.getContext('2d');
    let currentPlayer = 1;
    let timer = 30;
    let interval;

    function drawPlayer(x, y, label) {
      ctx.beginPath();
      ctx.arc(x, y, 30, 0, Math.PI * 2);
      ctx.fillStyle = '#00d8ff';
      ctx.fill();
      ctx.strokeStyle = '#fff';
      ctx.stroke();
      ctx.closePath();
      ctx.fillStyle = '#fff';
      ctx.font = '16px Arial';
      ctx.fillText(label, x - 20, y + 5);
    }

    function drawBomb(x, y) {
      ctx.beginPath();
      ctx.arc(x, y, 15, 0, Math.PI * 2);
      ctx.fillStyle = '#ff4444';
      ctx.fill();
      ctx.strokeStyle = '#fff';
      ctx.stroke();
      ctx.closePath();
    }

    function updateGame() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      drawPlayer(100, 150, 'Jugador 1');
      drawPlayer(300, 150, 'Jugador 2');
      if (currentPlayer === 1) drawBomb(100, 120);
      else drawBomb(300, 120);
    }

    function startTimer() {
      clearInterval(interval);
      timer = 30;
      document.getElementById('timer').textContent = timer;
      interval = setInterval(() => {
        timer--;
        document.getElementById('timer').textContent = timer;
        if (timer <= 0) {
          clearInterval(interval);
          document.getElementById('status').textContent = `💥 ¡Jugador ${currentPlayer} perdió!`;
        }
      }, 1000);
    }

    function passBomb() {
      currentPlayer = currentPlayer === 1 ? 2 : 1;
      document.getElementById('status').textContent = `Jugador: ${currentPlayer} | Tiempo: ${timer}s`;
      startTimer();
      updateGame();
    }

    // Inicializar
    updateGame();
    startTimer();
  </script>
</body>
</html>
