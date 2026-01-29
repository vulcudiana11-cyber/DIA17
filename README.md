# DIA17
Cadou pentru iubitul meu❤️
<!DOCTYPE html>
<html lang="ro">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Diana ❤️ Sergiu</title>

<style>
body {
    margin: 0;
    font-family: Arial, sans-serif;
    background: linear-gradient(135deg, #ff9acb, #ffe0ee);
    text-align: center;
    overflow: hidden;
}

.container {
    max-width: 600px;
    margin: auto;
    padding: 40px;
    background: rgba(255,255,255,0.88);
    border-radius: 25px;
    margin-top: 60px;
    box-shadow: 0 10px 30px rgba(0,0,0,0.15);
}

h1 {
    color: #d63384;
    font-size: 2.3rem;
}

p {
    font-size: 1.35rem;
    color: #444;
}

button {
    padding: 15px 30px;
    font-size: 1.15rem;
    border: none;
    border-radius: 12px;
    margin: 10px;
    cursor: pointer;
    transition: 0.3s;
}

button:hover {
    transform: scale(1.1);
}

.yes {
    background: #ff4fa3;
    color: white;
}

.no {
    background: #aaa;
    color: white;
    position: relative;
}

#timer {
    font-size: 1.2rem;
    color: #ff2f92;
    margin-bottom: 15px;
    font-weight: bold;
}

canvas {
    position: fixed;
    top: 0;
    left: 0;
    pointer-events: none;
}
</style>
</head>

<body>

<canvas id="confetti"></canvas>

<div class="container" id="app">
    <h1>Diana ❤️ Sergiu</h1>
    <p>Am câteva întrebări SUPER importante pentru tine…</p>
    <button class="yes" onclick="next()">Sunt pregătit 😏</button>
</div>

<script>
let step = 0;
let timeLeft = 10;
let timerInterval;
let secretShown = false;

function startTimer() {
    timeLeft = 10;
    clearInterval(timerInterval);
    timerInterval = setInterval(() => {
        document.getElementById("timer").innerText =
            "⏰ Mai ai " + timeLeft + " secunde!";
        timeLeft--;
        if (timeLeft < 0) {
            clearInterval(timerInterval);
            next();
        }
    }, 1000);
}

function next() {
    step++;
    clearInterval(timerInterval);
    const app = document.getElementById("app");

    if (step === 1) {
        app.innerHTML = `
        <div id="timer"></div>
        <h1>Întrebarea 1 💕</h1>
        <p>Îți place să fii cu mine?</p>
        <button class="yes" onclick="next()">DA 😍</button>
        <button class="no" onclick="move(this)">NU 😅</button>`;
        startTimer();
    }

    else if (step === 2) {
        app.innerHTML = `
        <div id="timer"></div>
        <h1>Întrebarea 2 💗</h1>
        <p>Mă iubești chiar și când sunt dramatică?</p>
        <button class="yes" onclick="next()">Evident 🥰</button>
        <button class="no" onclick="move(this)">Hmm…</button>`;
        startTimer();
    }

    else if (step === 3) {
        app.innerHTML = `
        <div id="timer"></div>
        <h1>Întrebarea 3 💞</h1>
        <p>Promiți să rămâi cu mine?</p>
        <button class="yes" onclick="next()">Promit 💖</button>
        <button class="no" onclick="move(this)">Nu știu…</button>`;
        startTimer();
    }

    else if (step === 4) {
        app.innerHTML = `
        <div id="timer"></div>
        <h1>Întrebare specială 🧠💘</h1>
        <p>Care este data care ți-a schimbat viața?</p>
        <p><em>(indiciu: m-ai cunoscut pe mine 😌)</em></p>
        <button class="yes" onclick="next()">14 septembrie 2025 💗</button>
        <button class="no" onclick="move(this)">Nu mai știu 😬</button>`;
        startTimer();
    }

    else if (step === 5) {
        app.innerHTML = `
        <div id="timer"></div>
        <h1>ULTIMA ÎNTREBARE ❤️</h1>
        <p>Sergiu… vrei să fii Valentine-ul meu?</p>
        <button class="yes" onclick="final()">DAAA 💘</button>
        <button class="no" onclick="move(this)">NU 😢</button>`;
        startTimer();
    }
}

function move(btn) {
    if (!secretShown && step === 4) {
        alert("Butonul ăsta nu funcționează… la fel ca ideea de a nu mă iubi 😏");
        secretShown = true;
    }
    const x = Math.random() * 300 - 150;
    const y = Math.random() * 300 - 150;
    btn.style.transform = `translate(${x}px, ${y}px)`;
}

function final() {
    document.getElementById("app").innerHTML = `
        <h1>YEEEEY 🎉💖</h1>
        <p>Diana & Sergiu</p>
        <p>Pentru totdeauna 💕</p>`;
    startConfetti();
}

/* CONFETTI */
const canvas = document.getElementById("confetti");
const ctx = canvas.getContext("2d");
canvas.width = window.innerWidth;
canvas.height = window.innerHeight;

let confetti = [];

function startConfetti() {
    for (let i = 0; i < 200; i++) {
        confetti.push({
            x: Math.random() * canvas.width,
            y: Math.random() * canvas.height,
            r: Math.random() * 6 + 4,
            d: Math.random() * 5 + 2,
            color: `hsl(${Math.random()*360},100%,70%)`
        });
    }
    animateConfetti();
}

function animateConfetti() {
    ctx.clearRect(0,0,canvas.width,canvas.height);
    confetti.forEach(c => {
        ctx.beginPath();
        ctx.arc(c.x, c.y, c.r, 0, Math.PI * 2);
        ctx.fillStyle = c.color;
        ctx.fill();
        c.y += c.d;
        if (c.y > canvas.height) c.y = 0;
    });
    requestAnimationFrame(animateConfetti);
}
</script>

</body>
</html>
