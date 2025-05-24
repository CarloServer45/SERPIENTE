<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Snake Game</title>
  <style>
    canvas { background: #000; display: block; margin: 0 auto; }
    body { text-align: center; font-family: sans-serif; background: #222; color: white; }
  </style>
</head>
<body>
  <h1>🐍 Juego de la Serpiente</h1>
  <canvas id="game" width="400" height="400"></canvas>
  <p>Usa las flechas del teclado para jugar</p>

  <script>
    const canvas = document.getElementById('game');
    const ctx = canvas.getContext('2d');
    const box = 20;
    let snake = [{ x: 9 * box, y: 10 * box }];
    let food = { x: Math.floor(Math.random() * 20) * box, y: Math.floor(Math.random() * 20) * box };
    let dir;
    let score = 0;

    document.addEventListener("keydown", (e) => {
      if (e.key === "ArrowLeft" && dir !== "RIGHT") dir = "LEFT";
      else if (e.key === "ArrowUp" && dir !== "DOWN") dir = "UP";
      else if (e.key === "ArrowRight" && dir !== "LEFT") dir = "RIGHT";
      else if (e.key === "ArrowDown" && dir !== "UP") dir = "DOWN";
    });

    function draw() {
      ctx.clearRect(0, 0, 400, 400);
      for (let i = 0; i < snake.length; i++) {
        ctx.fillStyle = i === 0 ? "lime" : "green";
        ctx.fillRect(snake[i].x, snake[i].y, box, box);
      }
      ctx.fillStyle = "red";
      ctx.fillRect(food.x, food.y, box, box);

      let head = { x: snake[0].x, y: snake[0].y };
      if (dir === "LEFT") head.x -= box;
      if (dir === "UP") head.y -= box;
      if (dir === "RIGHT") head.x += box;
      if (dir === "DOWN") head.y += box;

      if (head.x === food.x && head.y === food.y) {
        food = { x: Math.floor(Math.random() * 20) * box, y: Math.floor(Math.random() * 20) * box };
        score++;
      } else {
        snake.pop();
      }

      if (
        head.x < 0 || head.y < 0 ||
        head.x >= 400 || head.y >= 400 ||
        snake.some(seg => seg.x === head.x && seg.y === head.y)
      ) {
        clearInterval(game);
        alert("¡Game Over! Puntos: " + score);
      }

      snake.unshift(head);
    }

    const game = setInterval(draw, 100);
  </script>
</body>
</html>
