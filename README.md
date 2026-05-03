# tryck
<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Birthday Surprise ✨</title>

  <!-- Google Font -->
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;600&display=swap" rel="stylesheet">

  <style>
    :root {
      --name: "Teman Spesial";
      --message: "Semoga semua hal baik datang padamu 🎂";
      --accent: #ff4d6d;
    }

    body {
      margin: 0;
      font-family: 'Poppins', sans-serif;
      height: 100vh;
      overflow: hidden;
      background: radial-gradient(circle at top, #1a1a2e, #0f0f1a);
      color: white;
      display: flex;
      justify-content: center;
      align-items: center;
    }

    .container {
      text-align: center;
      z-index: 2;
      animation: fadeIn 2s ease;
    }

    h1 {
      font-size: 2.5rem;
      margin-bottom: 10px;
      background: linear-gradient(90deg, #ff4d6d, #ff9a9e);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
    }

    p {
      opacity: 0.9;
    }

    button {
      margin-top: 20px;
      padding: 12px 24px;
      border-radius: 50px;
      border: none;
      background: var(--accent);
      color: white;
      font-size: 1rem;
      cursor: pointer;
      transition: 0.3s;
      box-shadow: 0 0 15px var(--accent);
    }

    button:hover {
      transform: scale(1.1);
      box-shadow: 0 0 30px var(--accent);
    }

    canvas {
      position: absolute;
      top: 0;
      left: 0;
      z-index: 1;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(30px); }
      to { opacity: 1; transform: translateY(0); }
    }
  </style>
</head>
<body>

<canvas id="bg"></canvas>

<div class="container">
  <h1>🎉 Happy Birthday 🎉</h1>
  <h2 id="name"></h2>
  <p id="message"></p>
  <button onclick="startSurprise()">Mulai Kejutan 🎁</button>
</div>

<audio id="music" src="https://www.bensound.com/bensound-music/bensound-happyrock.mp3"></audio>

<script>
// CONFIG
const CONFIG = {
  name: "kadya diazzahra pusera",
  message: `“Happy Sweet Seventeen, my dear friend! 🎉✨
Hari ini bukan cuma nambah umur, tapi juga nambah cerita, pengalaman, dan langkah baru menuju masa depan yang lebih cerah. Di usia 17 ini, kamu lagi ada di fase yang penuh warna—kadang seru, kadang bingung, tapi justru di situlah keindahannya.
Semoga kamu selalu punya alasan untuk tersenyum, even on your hardest days. Jangan takut untuk bermimpi besar, karena you truly deserve all the good things in life. Percaya deh, semua usaha dan kebaikan yang kamu tanam sekarang bakal jadi sesuatu yang indah di masa depan.
Terima kasih sudah jadi teman yang selalu ada—yang bisa diajak ketawa bareng, cerita random, sampai saling support di saat susah. You’re not just a friend, you’re part of my best memories.
Di umur yang sweet ini, semoga kamu semakin mengenal dirimu sendiri, semakin kuat menghadapi apa pun, dan tetap jadi pribadi yang baik, tulus, dan apa adanya. Never change the good in you, karena itu yang bikin kamu spesial.
Once again, happy 17th birthday! 🎂💫
May your life be filled with happiness, love, and endless opportunities.
Stay awesome, stay kind, and stay shining—always! 🌟”`
};

document.getElementById("name").innerText = CONFIG.name;
document.getElementById("message").innerText = CONFIG.message;

// MUSIC + CONFETTI
function startSurprise() {
  document.getElementById("music").play();
  confetti();
}

function confetti() {
  for (let i = 0; i < 150; i++) {
    let el = document.createElement("div");
    el.style.position = "absolute";
    el.style.width = "8px";
    el.style.height = "8px";
    el.style.background = `hsl(${Math.random()*360},100%,50%)`;
    el.style.left = Math.random() * window.innerWidth + "px";
    el.style.top = "-10px";
    el.style.opacity = Math.random();
    el.style.transform = "rotate(" + Math.random()*360 + "deg)";
    el.style.transition = "top 3s linear";
    document.body.appendChild(el);

    setTimeout(() => {
      el.style.top = "100vh";
    }, 50);

    setTimeout(() => el.remove(), 3000);
  }
}

// PARTICLE BACKGROUND
const canvas = document.getElementById("bg");
const ctx = canvas.getContext("2d");
canvas.width = window.innerWidth;
canvas.height = window.innerHeight;

let particles = [];

for (let i = 0; i < 80; i++) {
  particles.push({
    x: Math.random() * canvas.width,
    y: Math.random() * canvas.height,
    r: Math.random() * 2,
    dx: Math.random() - 0.5,
    dy: Math.random() - 0.5
  });
}

function animate() {
  ctx.clearRect(0,0,canvas.width,canvas.height);
  particles.forEach(p => {
    p.x += p.dx;
    p.y += p.dy;

    if (p.x < 0 || p.x > canvas.width) p.dx *= -1;
    if (p.y < 0 || p.y > canvas.height) p.dy *= -1;

    ctx.beginPath();
    ctx.arc(p.x, p.y, p.r, 0, Math.PI*2);
    ctx.fillStyle = "white";
    ctx.fill();
  });

  requestAnimationFrame(animate);
}

animate();

window.addEventListener("resize", () => {
  canvas.width = window.innerWidth;
  canvas.height = window.innerHeight;
});

</script>

</body>
</html>


