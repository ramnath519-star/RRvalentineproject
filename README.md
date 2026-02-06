<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>For Rishitha ❤️</title>

<style>
body {
  background: linear-gradient(135deg, #ffe4e1, #fff0f3);
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  margin: 0;
  font-family: 'Segoe UI', Tahoma, sans-serif;
  overflow: hidden;
  touch-action: none;
}

/* Falling hearts */
.falling-heart {
  position: fixed;
  top: -10vh;
  font-size: 18px;
  user-select: none;
  pointer-events: none;
  animation: fall linear forwards;
  z-index: 1;
}

@keyframes fall {
  to {
    transform: translateY(110vh) rotate(360deg);
    opacity: 0;
  }
}

/* Card */
.card {
  background: rgba(255,255,255,0.96);
  padding: 36px;
  border-radius: 28px;
  box-shadow: 0 25px 60px rgba(233,30,99,0.25);
  text-align: center;
  width: 320px;
  backdrop-filter: blur(10px);
  border: 2px solid #fff;
  z-index: 10;
  position: relative;
}

.main-heart {
  font-size: 60px;
  animation: pulse 0.9s infinite alternate;
}

@keyframes pulse {
  from { transform: scale(1); }
  to { transform: scale(1.15); }
}

.progress {
  font-size: 11px;
  color: #ff758c;
  letter-spacing: 1px;
  text-transform: uppercase;
  margin-bottom: 12px;
}

h1 {
  color: #d63384;
  font-size: 22px;
  margin: 20px 0;
  min-height: 80px;
  line-height: 1.4;
  display: flex;
  align-items: center;
  justify-content: center;
}

.btn-container {
  display: flex;
  justify-content: center;
  gap: 20px;
  margin-top: 20px;
  min-height: 60px;
}

button {
  padding: 12px 30px;
  font-size: 18px;
  font-weight: bold;
  border: none;
  border-radius: 50px;
  cursor: pointer;
  box-shadow: 0 4px 15px rgba(0,0,0,0.15);
}

#yes-btn {
  background-color: #ff4d6d;
  color: white;
}

#no-btn {
  background-color: #adb5bd;
  color: white;
  position: relative;
  transition: 0.15s ease;
}

#success-msg {
  display: none;
}

#countdown {
  margin-top: 20px;
  font-weight: bold;
  color: #ff4d6d;
  font-size: 1.05rem;
  background: #fff0f3;
  padding: 15px;
  border-radius: 15px;
  border: 1px dashed #ff4d6d;
}
</style>
</head>

<body>

<audio id="bgMusic" loop>
  <source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" type="audio/mpeg">
</audio>

<div class="card">
  <div id="quiz-box">
    <div class="progress" id="step-text">Step 1 of 6</div>
    <div class="main-heart">💖</div>
    <h1 id="question-text">Rishitha, do you believe in love?</h1>

    <div class="btn-container">
      <button id="yes-btn">Yes</button>
      <button id="no-btn">No</button>
    </div>
  </div>

  <div id="success-msg">
    <div class="main-heart">🥰</div>
    <h2>Yay! ❤️</h2>
    <p>I knew you'd say yes, Rishitha!</p>
    <div id="countdown">Calculating our time...</div>
  </div>
</div>

<script>
/* ---------------- DATA ---------------- */
const questions = [
  "Rishitha, do you believe in love?",
  "Rishitha, would you go on a Valentine’s date with me?",
  "Rishitha, do small surprises make you happy?",
  "Rishitha, is spending time together more important than gifts?",
  "Rishitha, do you think we’d make a good pair?",
  "Rishitha, will you be my Valentine?"
];

let currentStep = 0;
const music = document.getElementById("bgMusic");

/* ---------------- MUSIC ---------------- */
function playMusic() {
  music.play().catch(() => {});
}
document.body.addEventListener("click", playMusic, { once: true });

/* ---------------- BUTTON LOGIC ---------------- */
const yesBtn = document.getElementById("yes-btn");
const noBtn = document.getElementById("no-btn");

noBtn.addEventListener("mouseover", moveNo);
noBtn.addEventListener("touchstart", moveNo);

function moveNo() {
  playMusic();
  noBtn.style.position = "fixed";
  const maxX = window.innerWidth - noBtn.offsetWidth - 20;
  const maxY = window.innerHeight - noBtn.offsetHeight - 20;
  noBtn.style.left = Math.random() * maxX + "px";
  noBtn.style.top = Math.random() * maxY + "px";
}

yesBtn.addEventListener("click", nextQuestion);

function nextQuestion() {
  playMusic();
  currentStep++;

  if (currentStep < questions.length) {
    document.getElementById("question-text").innerText = questions[currentStep];
    document.getElementById("step-text").innerText = `Step ${currentStep + 1} of 6`;
    noBtn.style.position = "relative";
    noBtn.style.left = "0";
    noBtn.style.top = "0";
  } else {
    document.getElementById("quiz-box").style.display = "none";
    document.getElementById("success-msg").style.display = "block";
    startCountdown();
  }
}

/* ---------------- COUNTDOWN ---------------- */
function startCountdown() {
  const target = new Date("Feb 14, 2026 00:00:00").getTime();

  setInterval(() => {
    const now = Date.now();
    const gap = target - now;

    const d = Math.floor(gap / (1000 * 60 * 60 * 24));
    const h = Math.floor((gap / (1000 * 60 * 60)) % 24);
    const m = Math.floor((gap / (1000 * 60)) % 60);
    const s = Math.floor((gap / 1000) % 60);

    document.getElementById("countdown").innerText =
      `Our date in: ${d}d ${h}h ${m}m ${s}s`;
  }, 1000);
}

/* ---------------- HEARTS ---------------- */
function createHeart() {
  const heart = document.createElement("div");
  heart.className = "falling-heart";
  heart.innerText = "❤️";
  heart.style.left = Math.random() * 100 + "vw";
  heart.style.animationDuration = (Math.random() * 3 + 3) + "s";
  document.body.appendChild(heart);
  setTimeout(() => heart.remove(), 6000);
}

setInterval(createHeart, 800);
</script>

</body>
</html>
