# Game-website-
!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Tap Jump Game</title>
<style>
  body {
    background: #f0f0f0;
    font-family: Arial, sans-serif;
    display: flex;
    justify-content: center;
    margin: 0;
    padding: 20px;
  }

  #container {
    width: 320px;
    text-align: center;
  }

  .ad {
    height: 60px;
    background: #ddd;
    margin: 10px 0;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 14px;
    border: 1px solid #aaa;
  }

  #game {
    width: 300px;
    height: 400px;
    background: #fff;
    border: 2px solid #ccc;
    position: relative;
    overflow: hidden;
    margin: 0 auto;
    border-radius: 10px;
  }

  #player {
    width: 40px;
    height: 40px;
    background: #4caf50;
    position: absolute;
    bottom: 0;
    left: 30px;
    border-radius: 5px;
  }

  #obstacle {
    width: 40px;
    height: 40px;
    background: #f44336;
    position: absolute;
    bottom: 0;
    right: -40px;
    border-radius: 5px;
    animation: move 2s linear infinite;
  }

  @keyframes move {
    0% { right: -40px; }
    100% { right: 300px; }
  }

  .jump {
    animation: jump 0.5s;
  }

  @keyframes jump {
    0% { bottom: 0; }
    50% { bottom: 120px; }
    100% { bottom: 0; }
  }

  #score {
    position: absolute;
    top: 5px;
    left: 10px;
    font-size: 16px;
    font-weight: bold;
  }
</style>
</head>
<body>

<div id="container">

  <div class="ad" id="topAd">Top Ad</div>

  <div id="game">
    <div id="score">Score: 0</div>
    <div id="player"></div>
    <div id="obstacle"></div>
  </div>

  <div class="ad" id="bottomAd">Bottom Ad</div>

</div>

<!-- Sound -->
<audio id="jumpSound" src="https://www.soundjay.com/buttons/sounds/button-16.mp3"></audio>

<script>
const player = document.getElementById("player");
const obstacle = document.getElementById("obstacle");
const scoreText = document.getElementById("score");
const jumpSound = document.getElementById("jumpSound");
let score = 0;

document.addEventListener("click", jump);

function jump() {
  if (!player.classList.contains("jump")) {
    player.classList.add("jump");
    jumpSound.play();
    setTimeout(() => {
      player.classList.remove("jump");
    }, 500);
  }
}

// Game Loop
setInterval(() => {
  const playerBottom = parseInt(
    window.getComputedStyle(player).getPropertyValue("bottom")
  );
  const obstacleRight = parseInt(
    window.getComputedStyle(obstacle).getPropertyValue("right")
  );

  if (obstacleRight > 220 && obstacleRight < 260 && playerBottom < 40) {
    alert("Game Over! Score: " + score);
    score = 0;
    scoreText.innerText = "Score: 0";
  } else {
    score++;
    scoreText.innerText = "Score: " + score;
  }
}, 100);

// Ads Links (replace # with your ad URLs)
document.getElementById("topAd").onclick = () => window.open("#", "_blank");
document.getElementById("bottomAd").onclick = () => window.open("#", "_blank");

</script>

</body>
</html>
