# Game-website-
<!DOCTYPE html>
<html>
<head>
  <title>Click Game</title>
  <style>
    body {
      background: #f2f6ff;
      font-family: Arial;
      text-align: center;
    }
    h1 { color: #333; }
    button {
      padding: 15px 30px;
      font-size: 20px;
      border: none;
      border-radius: 8px;
      background: #4caf50;
      color: white;
      cursor: pointer;
    }
    button:hover {
      background: #43a047;
    }
  </style>
</head>
<body>

  <h1>🎮 Click Game</h1>
  <p>Score: <span id="score">0</span></p>

  <button onclick="addScore()">CLICK ME</button>

  <script>
    let score = 0;
    function addScore() {
      score++;
      document.getElementById("score").innerText = score;
    }
  </script>

</body>
</html>
