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
    background: #fff0f3;
    overflow: hidden;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
  }

  .card {
    background: #ffffff;
    width: 90%;
    max-width: 400px;
    border-radius: 22px;
    padding: 25px;
    text-align: center;
    box-shadow: 0 25px 50px rgba(0,0,0,0.2);
    position: relative;
    z-index: 2;
  }

  .rose {
    font-size: 40px;
  }

  h1 {
    color: #c9184a;
    font-size: 22px;
    margin-bottom: 5px;
  }

  h2 {
    font-size: 20px;
    margin-bottom: 10px;
  }

  p {
    font-size: 14px;
    color: #555;
  }

  .buttons {
    margin-top: 25px;
    position: relative;
    height: 60px;
  }

  button {
    padding: 12px 20px;
    border: none;
    border-radius: 12px;
    font-size: 15px;
    font-weight: 600;
    cursor: pointer;
    position: absolute;
  }

  #yesBtn {
    background: #ff4d6d;
    color: white;
    left: 20%;
  }

  #noBtn {
    background: #adb5bd;
    color: white;
    right: 20%;
  }

  .message {
    display: none;
    margin-top: 20px;
    font-size: 14px;
    line-height: 1.6;
    border: 2px dashed #ffb3c1;
    padding: 15px;
    border-radius: 15px;
  }

  .petal {
    position: fixed;
    top: -10px;
    font-size: 18px;
    animation: fall linear infinite;
    z-index: 1;
  }

  @keyframes fall {
    to {
      transform: translateY(110vh) rotate(360deg);
    }
  }
</style>
</head>

<body>

<div class="card">
  <div class="rose">🌹</div>
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
  // Moving NO button 😄
  const noBtn = document.getElementById("noBtn");

  noBtn.addEventListener("mouseover", moveButton);
  noBtn.addEventListener("click", moveButton);

  function moveButton() {
    const x = Math.random() * 200 - 100;
    const y = Math.random() * 100 - 50;
    noBtn.style.transform = `translate(${x}px, ${y}px)`;
  }

  // YES button action
  function showLove() {
    document.getElementById("loveMsg").style.display = "block";
  }

  // Falling rose petals 🌹
  function createPetal() {
    const petal = document.createElement("div");
    petal.classList.add("petal");
    petal.innerHTML = "🌹";
    petal.style.left = Math.random() * 100 + "vw";
    petal.style.animationDuration = Math.random() * 3 + 3 + "s";
    document.body.appendChild(petal);

    setTimeout(() => petal.remove(), 6000);
  }

  setInterval(createPetal, 400);
</script>

</body>
</html>
