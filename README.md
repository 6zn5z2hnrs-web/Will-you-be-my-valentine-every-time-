# Will-you-be-my-valentine-every-time-
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>NNI 😘 — My Valentine Forever</title>

<style>
body {
  margin: 0;
  font-family: 'Poppins', sans-serif;
  background: radial-gradient(circle at top, #ff6b81, #ff2f68);
  color: white;
  text-align: center;
  overflow-x: hidden;
  perspective: 1000px;
}

h1, h2, h3 { margin: 10px 0; }

.box {
  background: rgba(255,255,255,0.18);
  border-radius: 25px;
  padding: 28px;
  margin: 22px;
  backdrop-filter: blur(6px);
  animation: fadeUp 1.2s ease;
  box-shadow: 0 20px 40px rgba(0,0,0,0.25);
  transform-style: preserve-3d;
}

button {
  background: white;
  color: #ff2f68;
  border: none;
  padding: 13px 26px;
  border-radius: 30px;
  font-size: 16px;
  cursor: pointer;
  margin: 10px;
  box-shadow: 0 8px 20px rgba(0,0,0,0.25);
}

button:hover {
  transform: scale(1.08);
}

.hidden { display: none; }

.option-btn {
  display: block;
  width: 85%;
  margin: 12px auto;
}

.progress {
  width: 100%;
  background: rgba(255,255,255,0.3);
  border-radius: 20px;
  overflow: hidden;
  margin: 18px 0;
}

.progress-bar {
  height: 12px;
  width: 0%;
  background: linear-gradient(90deg, #fff, #ffd6e0);
  transition: 0.6s;
}

.no-btn { position: relative; }

/* 3D LOVE ORBS */
.orb-container {
  display: flex;
  justify-content: center;
  gap: 40px;
  margin-top: 15px;
}

.orb {
  width: 110px;
  height: 110px;
  border-radius: 50%;
  background: radial-gradient(circle at top, #fff, #ff9db0);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 28px;
  font-weight: bold;
  color: #ff2f68;
  animation: float3d 6s infinite ease-in-out;
  box-shadow: 0 20px 40px rgba(0,0,0,0.35);
}

.orb:nth-child(2) { animation-delay: 3s; }

@keyframes float3d {
  0% { transform: translateY(0) rotateY(0deg); }
  50% { transform: translateY(-25px) rotateY(180deg); }
  100% { transform: translateY(0) rotateY(360deg); }
}

/* FLOATING NNI 😘 */
.name-float {
  position: fixed;
  font-size: 20px;
  opacity: 0.25;
  animation: drift 12s linear infinite;
}

@keyframes drift {
  from { transform: translateY(100vh); }
  to { transform: translateY(-120vh); }
}

/* HEARTS + CONFETTI */
.heart, .confetti {
  position: fixed;
  font-size: 20px;
  animation: rise 6s linear forwards;
}

@keyframes rise {
  to { transform: translateY(-120vh) rotate(360deg); opacity: 0; }
}

@keyframes fadeUp {
  from { opacity: 0; transform: translateY(40px); }
  to { opacity: 1; transform: translateY(0); }
}
</style>
</head>

<body>

<audio id="music" loop>
  <source src="without-you-prem-dhillon.mp3" type="audio/mpeg">
</audio>

<h1>NNI 😘 Will You Be My Valentine?</h1>

<div class="box">
  <p>
    NNI 😘,<br>
    you are my favorite feeling,<br>
    my safest place,<br>
    my forever ❤️
  </p>

  <div class="orb-container">
    <div class="orb">ME</div>
    <div class="orb">NNI 😘</div>
  </div>

  <button onclick="start()">Play Our Song 🎵</button>
</div>

<div id="questionBox" class="hidden box">
  <h2 id="questionText"></h2>

  <div class="progress">
    <div class="progress-bar" id="progressBar"></div>
  </div>

  <div id="options"></div>
</div>

<div id="final" class="hidden box">
  <h2>NNI 😘 You Are My Forever 😭❤️</h2>
  <p>
    I choose you today,<br>
    tomorrow,<br>
    and every lifetime after 💍<br><br>
    This heart?<br>
    It’s yours. Always.
  </p>
</div>

<script>
const questions = [
  { text: "Do you know you are my safest place, NNI 😘?", type: "yesno" },
  {
    text: "What is my favourite thing?",
    type: "mcq",
    options: ["Pasta 🍝", "Pizza 🍕", "Burger 🍔", "Cold Coffee ☕"],
    real: "None of these… it’s YOU baby 😍❤️"
  },
  {
    text: "When we met first time, what did I give you?",
    type: "mcq",
    options: ["Rose 🌹", "Chocolates 🍫", "Teddy 🧸", "Ring 💍"],
    real: "Not these… I gave you my HEART ❤️🥹"
  },
  { text: "Will you choose me forever, NNI 😘?", type: "yesno" }
];

let index = 0;
let noScale = 1;

function start() {
  document.getElementById("music").play();
  document.getElementById("questionBox").style.display = "block";
  showQuestion();
}

function showQuestion() {
  const q = questions[index];
  document.getElementById("questionText").innerText = q.text;
  const opt = document.getElementById("options");
  opt.innerHTML = "";

  document.getElementById("progressBar").style.width =
    (index / questions.length) * 100 + "%";

  if (q.type === "yesno") {
    opt.innerHTML = `
      <button onclick="next()">YES ❤️</button>
      <button class="no-btn" onmouseover="moveNo(this)">NO 🙄</button>
    `;
  } else {
    q.options.forEach(o => {
      const b = document.createElement("button");
      b.className = "option-btn";
      b.innerText = o;
      b.onclick = () => reveal(q.real);
      opt.appendChild(b);
    });
  }
}

function reveal(txt) {
  document.getElementById("options").innerHTML =
    `<p style="font-size:18px">${txt}</p><button onclick="next()">Aww 🥹❤️</button>`;
}

function moveNo(btn) {
  btn.style.left = Math.random() * 200 - 100 + "px";
  btn.style.top = Math.random() * 100 - 50 + "px";
  noScale -= 0.1;
  btn.style.transform = "scale(" + noScale + ")";
}

function next() {
  index++;
  if (index < questions.length) showQuestion();
  else {
    document.getElementById("questionBox").style.display = "none";
    document.getElementById("final").style.display = "block";
    celebrate();
  }
}

function celebrate() {
  for (let i = 0; i < 50; i++) {
    const e = document.createElement("div");
    e.className = Math.random() > 0.5 ? "heart" : "confetti";
    e.innerHTML = Math.random() > 0.5 ? "❤️" : "💖";
    e.style.left = Math.random() * 100 + "vw";
    document.body.appendChild(e);
    setTimeout(() => e.remove(), 6000);
  }
}

// floating NNI 😘
setInterval(() => {
  const n = document.createElement("div");
  n.className = "name-float";
  n.innerText = "NNI 😘";
  n.style.left = Math.random() * 100 + "vw";
  document.body.appendChild(n);
  setTimeout(() => n.remove(), 12000);
}, 1200);
</script>

</body>
</html>
