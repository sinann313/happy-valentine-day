<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Game Valentine ❤️</title>

<style>
body {
  margin: 0;
  height: 100vh;
  background: linear-gradient(135deg, #ff758c, #ff7eb3);
  font-family: 'Segoe UI', sans-serif;
  overflow: hidden;
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  text-align: center;
}

/* Card */
.card {
  background: rgba(255,255,255,0.15);
  backdrop-filter: blur(10px);
  padding: 40px;
  border-radius: 25px;
  box-shadow: 0 20px 40px rgba(0,0,0,0.25);
  max-width: 400px;
}

button {
  margin-top: 20px;
  padding: 12px 25px;
  border-radius: 15px;
  border: none;
  font-size: 16px;
  cursor: pointer;
  background: white;
  color: #ff5a8a;
  font-weight: bold;
}

/* Game heart */
#heart {
  position: absolute;
  font-size: 45px;
  cursor: pointer;
  display: none;
  transition: 0.2s;
}

#score {
  margin-top: 10px;
}

.win {
  font-size: 20px;
  margin-top: 15px;
  animation: pop 0.5s ease;
}

@keyframes pop {
  from { transform: scale(0); }
  to { transform: scale(1); }
}
</style>
</head>

<body>

<div class="card" id="card">
  <h1>Happy Valentine ❤️</h1>
  <p>Main game dulu ya 😆<br>Tangkap 5 hati buat buka pesan rahasia 💌</p>
  <button onclick="startGame()">Mulai Game</button>
  <div id="score"></div>
  <div id="message"></div>
</div>

<div id="heart">❤️</div>

<script>
let score = 0;
const heart = document.getElementById("heart");
const scoreText = document.getElementById("score");
const message = document.getElementById("message");

function randomPos() {
  const x = Math.random() * (window.innerWidth - 50);
  const y = Math.random() * (window.innerHeight - 50);
  heart.style.left = x + "px";
  heart.style.top = y + "px";
}

function startGame() {
  score = 0;
  message.innerHTML = "";
  heart.style.display = "block";
  scoreText.innerHTML = "Skor: 0 / 5";
  randomPos();
}

heart.onclick = () => {
  score++;
  scoreText.innerHTML = `Skor: ${score} / 5`;

  if (score >= 5) {
    heart.style.display = "none";
    message.innerHTML = `
      <div class="win">
      💖 Yeay kamu menang! 💖<br><br>
      Sebenarnya hadiahnya cuma satu...<br>
      Aku sayang kamu banget 🤍<br>
      Mau jadi Valentine-ku terus?
      </div>
    `;
  } else {
    randomPos();
  }
};
</script>

</body>
</html>
