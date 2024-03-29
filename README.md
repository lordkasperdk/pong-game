<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    body {
      display: flex;
      align-items: center;
      justify-content: center;
      height: 100vh;
      margin: 0;
      background-color: #111;
    }

    .game-container {
      position: relative;
      width: 600px;
      height: 400px;
      border: 2px solid #fff;
      overflow: hidden;
      display: flex;
      justify-content: space-between;
    }

    .pong {
      position: relative;
      width: 100%;
      height: 100%;
    }

    .ball {
      position: absolute;
      width: 20px;
      height: 20px;
      background-color: #fff;
      border-radius: 50%;
      left: 50%;
      top: 50%;
      transform: translate(-50%, -50%);
    }

    .paddle {
      position: absolute;
      width: 20px;
      height: 100px;
      background-color: #fff;
    }

    #leftPaddle {
      left: 0;
    }

    #rightPaddle {
      right: 0;
    }

    .score-container {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
    }

    .score {
      display: flex;
      align-items: center;
      font-size: 24px;
      color: #fff;
    }

    #leftScore {
      margin-right: 10px;
    }

    #rightScore {
      margin-left: 10px;
    }
  </style>
  <title>Pong Game</title>
</head>
<body>
  <div class="game-container">
    <div class="pong">
      <div class="ball"></div>
      <div class="paddle" id="leftPaddle"></div>
      <div class="paddle" id="rightPaddle"></div>
    </div>
  </div>
  <div class="score-container">
    <div class="score">
      <span id="leftScore">0</span> - <span id="rightScore">0</span>
    </div>
  </div>
  <script>
    const ball = document.querySelector('.ball');
    const leftPaddle = document.getElementById('leftPaddle');
    const rightPaddle = document.getElementById('rightPaddle');
    const leftScoreDisplay = document.getElementById('leftScore');
    const rightScoreDisplay = document.getElementById('rightScore');

    let ballX = 300;
    let ballY = 200;
    let ballSpeedX = 5;
    let ballSpeedY = 5;
    let leftPaddleY = 150;
    let rightPaddleY = 150;
    let leftScore = 0;
    let rightScore = 0;

    function update() {
      ballX += ballSpeedX;
      ballY += ballSpeedY;

      // Ball collision with walls
      if (ballY < 0 || ballY > 380) {
        ballSpeedY = -ballSpeedY;
      }

      // Ball collision with paddles
      if (
        (ballX <= 20 && ballY > leftPaddleY && ballY < leftPaddleY + 100) ||
        (ballX >= 560 && ballY > rightPaddleY && ballY < rightPaddleY + 100)
      ) {
        ballSpeedX = -ballSpeedX;
      }

      // Ball out of bounds
      if (ballX < 0) {
        rightScore++;
        resetBall();
      } else if (ballX > 600) {
        leftScore++;
        resetBall();
      }

      ball.style.left = ballX + 'px';
      ball.style.top = ballY + 'px';

      movePaddles();
      updateScore();
      requestAnimationFrame(update);
    }

    function resetBall() {
      ballX = 300;
      ballY = 200;
    }

    function movePaddles() {
      document.addEventListener('keydown', (event) => {
        if (event.key === 'w' && leftPaddleY > 0) {
          leftPaddleY -= 10;
        } else if (event.key === 's' && leftPaddleY < 300) {
          leftPaddleY += 10;
        }

        leftPaddle.style.top = leftPaddleY + 'px';
      });

      document.addEventListener('keydown', (event) => {
        if (event.key === 'ArrowUp' && rightPaddleY > 0) {
          rightPaddleY -= 10;
        } else if (event.key === 'ArrowDown' && rightPaddleY < 300) {
          rightPaddleY += 10;
        }

        rightPaddle.style.top = rightPaddleY + 'px';
      });
    }

    function updateScore() {
      leftScoreDisplay.textContent = leftScore;
      rightScoreDisplay.textContent = rightScore;
    }

    update();
  </script>
</body>
</html>
