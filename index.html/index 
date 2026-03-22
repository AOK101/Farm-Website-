<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Click the Target!</title>
  <style>
    body {
      margin: 0;
      background: #1a1a2e;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
      font-family: Arial, sans-serif;
      color: white;
      overflow: hidden;
    }

    h1 {
      margin-bottom: 10px;
      font-size: 2rem;
      color: #e94560;
    }

    #scoreboard {
      font-size: 1.2rem;
      margin-bottom: 20px;
    }

    #arena {
      position: relative;
      width: 600px;
      height: 400px;
      background: #16213e;
      border: 3px solid #e94560;
      border-radius: 12px;
      overflow: hidden;
    }

    #target {
      position: absolute;
      width: 60px;
      height: 60px;
      background: #e94560;
      border-radius: 50%;
      cursor: pointer;
      transition: transform 0.1s;
    }

    #target:hover {
      transform: scale(1.1);
    }

    #message {
      margin-top: 20px;
      font-size: 1rem;
      color: #a8a8b3;
    }

    #start-btn {
      margin-top: 15px;
      padding: 12px 30px;
      background: #e94560;
      color: white;
      border: none;
      border-radius: 8px;
      font-size: 1rem;
      cursor: pointer;
    }

    #start-btn:hover {
      background: #c73652;
    }
  </style>
</head>
<body>

  <h1>🎯 Click the Target!</h1>
  <div id="scoreboard">Score: <span id="score">0</span> &nbsp;|&nbsp; Time: <span id="timer">15</span>s</div>

  <div id="arena">
    <div id="target" style="display:none;"></div>
  </div>

  <div id="message">Press Start to play!</div>
  <button id="start-btn" onclick="startGame()">Start Game</button>

  <script>
    let score = 0;
    let timeLeft = 15;
    let interval;
    let animFrame;
    let x = 0, y = 0;
    let dx = 3, dy = 3;

    const target = document.getElementById('target');
    const scoreEl = document.getElementById('score');
    const timerEl = document.getElementById('timer');
    const messageEl = document.getElementById('message');
    const startBtn = document.getElementById('start-btn');
    const arena = document.getElementById('arena');

    function moveTarget() {
      const arenaW = arena.offsetWidth - 60;
      const arenaH = arena.offsetHeight - 60;

      x += dx;
      y += dy;

      if (x <= 0 || x >= arenaW) dx = -dx;
      if (y <= 0 || y >= arenaH) dy = -dy;

      target.style.left = x + 'px';
      target.style.top = y + 'px';

      animFrame = requestAnimationFrame(moveTarget);
    }

    target.addEventListener('click', () => {
      if (timeLeft <= 0) return;
      score++;
      scoreEl.textContent = score;
      dx = (Math.random() * 4 + 2) * (Math.random() < 0.5 ? 1 : -1);
      dy = (Math.random() * 4 + 2) * (Math.random() < 0.5 ? 1 : -1);
    });

    function startGame() {
      score = 0;
      timeLeft = 15;
      scoreEl.textContent = score;
      timerEl.textContent = timeLeft;
      messageEl.textContent = 'Click the moving circle as fast as you can!';
      startBtn.disabled = true;
      startBtn.style.background = '#555';

      x = 100;
      y = 100;
      dx = 3;
      dy = 3;

      target.style.display = 'block';
      cancelAnimationFrame(animFrame);
      moveTarget();

      clearInterval(interval);
      interval = setInterval(() => {
        timeLeft--;
        timerEl.textContent = timeLeft;
        if (timeLeft <= 0) {
          clearInterval(interval);
          cancelAnimationFrame(animFrame);
          target.style.display = 'none';
          messageEl.textContent = `⏱ Time's up! You scored ${score} points!`;
          startBtn.disabled = false;
          startBtn.style.background = '#e94560';
          startBtn.textContent = 'Play Again';
        }
      }, 1000);
    }
  </script>

</body>
</html>
