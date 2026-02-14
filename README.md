<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>For Deepashree</title>

<style>
body {
  margin: 0;
  padding: 0;
  overflow: hidden;
  background: linear-gradient(135deg, #ff4e8a, #ff9ecf);
  font-family: Arial, sans-serif;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  color: white;
  text-align: center;
}

.sticker {
  position: absolute;
  animation: float 12s linear infinite;
  opacity: 0.8;
}

@keyframes float {
  from { transform: translateY(100vh); }
  to { transform: translateY(-10vh); }
}

.card {
  background: rgba(0,0,0,0.25);
  padding: 80px;
  border-radius: 20px;
  box-shadow: 0 10px 30px rgba(0,0,0,0.3);
  max-width: 1200px;
  z-index: 10;
}

h1 {
  font-size: 210px;
  margin-bottom: 40px;
  line-height: 1.15;
}

button {
  padding: 36px 60px;
  border: none;
  border-radius: 16px;
  font-size: 120px;
  cursor: pointer;
  margin: 20px;
  position: relative;
}

.yes {
  background: #00ff9d;
  color: black;
}

.no {
  background: #ff2b5e;
  color: white;
  position: absolute;
}

.confetti {
  position: absolute;
  animation: fall 2s linear forwards;
}

@keyframes fall {
  to {
    transform: translateY(100vh) rotate(720deg);
    opacity: 0;
  }
}

.popup {
  position: fixed;
  background: black;
  padding: 30px;
  border-radius: 20px;
  font-size: 90px;
  z-index: 50;
}

.finalMessage {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%) scale(0);
  background: black;
  padding: 40px;
  border-radius: 20px;
  font-size: 120px;
  z-index: 20;
  animation: pop 0.6s forwards;
}

@keyframes pop {
  to { transform: translate(-50%, -50%) scale(1); }
}

.linkBtn {
  display: block;
  margin-top: 30px;
  font-size: 60px;
  padding: 20px 30px;
  background: #25D366;
  color: white;
  border-radius: 12px;
  text-decoration: none;
}
</style>
</head>

<body>

<div class="card">
  <h1>
    Deepashree…<br>
    will you eat out at least,<br>
    who cares about Valentine's 😅
  </h1>

  <button class="yes" onclick="confetti()">Yes</button>
  <button class="no" id="noBtn">No</button>
</div>

<script>
const foods = ["🍕","🍔","🥞","🍉","🍓","🍇","🍍","🍌","🍎","🥝","🍊","🥭","🍟","🍿","🥗"];
const emojis = ["😂","😜","🤡","😈","🤣","🙄","😝","🤭","🥴","😹"];

for (let i = 0; i < 30; i++) {
  let s = document.createElement("div");
  s.className = "sticker";
  s.innerText = foods[Math.floor(Math.random()*foods.length)];
  s.style.left = Math.random()*100 + "vw";
  s.style.fontSize = 40 + Math.random()*40 + "px";
  document.body.appendChild(s);
}

let noCount = 0;

const noBtn = document.getElementById("noBtn");
noBtn.addEventListener("click", () => {
  noCount++;

  const x = Math.random() * (window.innerWidth - 200);
  const y = Math.random() * (window.innerHeight - 150);
  noBtn.style.left = x + "px";
  noBtn.style.top = y + "px";

  if (noCount === 3) {
    popup("Arre, itni ziddi 😛");
  } else if (noCount > 3) {
    let emoji = emojis[noCount % emojis.length];
    popup(emoji + " Firse");
  }
});

function popup(text) {
  let p = document.createElement("div");
  p.className = "popup";
  p.innerText = text;
  p.style.left = Math.random()*70 + "vw";
  p.style.top = Math.random()*70 + "vh";
  document.body.appendChild(p);
  setTimeout(() => p.remove(), 1500);
}

function confetti() {
  for (let i = 0; i < 80; i++) {
    let c = document.createElement("div");
    c.className = "confetti";
    c.innerText = foods[Math.floor(Math.random()*foods.length)];
    c.style.left = Math.random()*100 + "vw";
    c.style.top = "-20px";
    c.style.fontSize = 40 + Math.random()*40 + "px";
    document.body.appendChild(c);
    setTimeout(() => c.remove(), 2500);
  }

  const msg = document.createElement("div");
  msg.className = "finalMessage";
  msg.innerHTML = `
    See you, Panipuri at your favourite place Shawty 😌
    <a class="linkBtn" href="https://wa.me/919619756863" target="_blank">
      Send location
    </a>
  `;
  document.body.appendChild(msg);

  popup("At last maangayi 😅");
}
</script>

</body>
</html>
