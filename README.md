<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Happy Rose Day ❤️</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;500;700&display=swap" rel="stylesheet">

<style>
  body {
    margin: 0;
    font-family: 'Poppins', sans-serif;
    background: radial-gradient(circle at top, #fff0f3, #ffd6e0);
    overflow: hidden;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
  }

  .card {
    background: #ffffff;
    width: 90%;
    max-width: 420px;
    border-radius: 26px;
    padding: 30px;
    text-align: center;
    box-shadow: 0 30px 60px rgba(0,0,0,0.18);
    position: relative;
    z-index: 5;
  }

  /* Growing rose */
  .rose {
    font-size: 42px;
    transition: transform 1s ease-in-out;
    display: inline-block;
    margin-bottom: 10px;
  }

  h1 {
    color: #c9184a;
    font-size: 22px;
    margin: 8px 0;
  }

  h2 {
    font-size: 20px;
    margin-bottom: 8px;
  }

  p {
    font-size: 14px;
    color: #555;
  }

  .buttons {
    margin-top: 26px;
    position: relative;
    height: 70px;
  }

  button {
    padding: 12px 22px;
    border: none;
    border-radius: 14px;
    font-size: 15px;
    font-weight: 600;
    cursor: pointer;
    position: absolute;
  }

  #yesBtn {
    background: linear-gradient(135deg, #ff4d6d, #ff758f);
    color: white;
    left: 18%;
  }

  #noBtn {
    background: #adb5bd;
    color: white;
    right: 18%;
  }

  .message {
    display: none;
    margin-top: 22px;
    font-size: 14px;
    line-height: 1.7;
    border: 2px dashed #ffb3c1;
    padding: 18px;
    border-radius: 16px;
    animation: fadeIn 0.8s ease;
  }

  @keyframes fadeIn {
    from { opacity: 0; transform: translateY(10px); }
    to { opacity: 1; transform: translateY(0); }
  }

  /* Falling items */
  .float {
    position: fixed;
    top: -10px;
    font-size: 18px;
    animation: fall linear infinite;
    z-index: 1;
    opacity: 0.9;
  }

  @keyframes fall {
    to {
      transform: translateY(110vh) rotate(360deg);
    }
  }

  /* Confetti burst */
  .confetti {
    position: fixed;
    font-size: 16px;
    animation: burst 1.2s ease forwards;
    z-index: 10;
  }

  @keyframes burst {
    0% { transform: scale(0) translateY(0); opacity: 1; }
    100% { transform: scale(1.5) translateY(-120px); opacity: 0; }
  }
</style>
</head>

<body>

<div class="card">
  <div class="rose" id="rose">🌹</div>

  <h1>Happy Rose Day</h1>
  <h2>Hey Rishitha!</h2>
  <p>Our love blooms brighter than any rose.</p>

  <p><b>Will you accept this rose? 🤗</b></p>

  <div class="buttons">
    <button id="yesBtn" onclick="showLove()">Yes ❤️</button>
    <button id="noBtn">No 🙈</button>
  </div>

  <div class="message" id="loveMsg">
    💌 <b>Happy Rose Day, Rishitha!</b><br><br>
    Just like this rose, my feelings for you grow more beautiful every single day.
    You make everything feel like springtime 🌸<br><br>
    Thank you for being you ❤️✨
  </div>
</div>

<script>
  /* Growing rose + confetti */
  let scale = 1;
  const rose = document.getElementById("rose");

  setInterval(() => {
    scale += 0.08;
    rose.style.transform = `scale(${scale})`;
    blastConfetti();
  }, 1000);

  /* Confetti blast */
  function blastConfetti() {
    for (let i = 0; i < 8; i++) {
      const c = document.createElement("div");
      c.classList.add("confetti");
      c.innerHTML = Math.random() > 0.5 ? "❤️" : "✨";
      c.style.left = 45 + Math.random() * 10 + "vw";
      c.style.top = "45vh";
      document.body.appendChild(c);
      setTimeout(() => c.remove(), 1200);
    }
  }

  /* NO button escape */
  const noBtn = document.getElementById("noBtn");
  noBtn.addEventListener("mouseover", moveButton);
  noBtn.addEventListener("click", moveButton);

  function moveButton() {
    const x = Math.random() * 220 - 110;
    const y = Math.random() * 120 - 60;
    noBtn.style.transform = `translate(${x}px, ${y}px)`;
  }

  /* YES action */
  function showLove() {
    document.getElementById("loveMsg").style.display = "block";
  }

  /* Falling hearts & roses */
  function createFloat() {
    const el = document.createElement("div");
    el.classList.add("float");
    el.innerHTML = Math.random() > 0.5 ? "❤️" : "🌹";
    el.style.left = Math.random() * 100 + "vw";
    el.style.animationDuration = Math.random() * 3 + 4 + "s";
    document.body.appendChild(el);
    setTimeout(() => el.remove(), 7000);
  }

  setInterval(createFloat, 350);
</script>

</body>
</html>
