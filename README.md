<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>WLD Bomb Game</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <h1>💣 WLD Bomb </h1>
  <canvas id="gameCanvas" width="400" height="300"></canvas>
  <h3 id="status">Jugador: 1 | Tiempo: <span id="timer">30</span>s</h3>
  <button onclick="passBomb()">Pasar Bomba</button>

  <script src="script.js"></script>
</body>
</html>