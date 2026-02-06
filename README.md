<!DOCTYPE html>
<html>
<head>
    <title>Happy Birthday Geeta 🎂</title>
    <style>
        body {
            margin: 0;
            background: radial-gradient(circle, #ff758c, #ff7eb3);
            overflow: hidden;
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            color: white;
            text-align: center;
        }

        .card {
            animation: fadeIn 3s ease-in-out;
            z-index: 2;
        }

        h1 {
            font-size: 50px;
            animation: glow 2s infinite alternate;
        }

        #name {
            font-size: 40px;
            color: yellow;
            animation: pop 1.5s ease-in-out infinite;
        }

        @keyframes fadeIn {
            from {opacity: 0;}
            to {opacity: 1;}
        }

        @keyframes glow {
            from {text-shadow: 0 0 10px white;}
            to {text-shadow: 0 0 25px gold;}
        }

        @keyframes pop {
            0% {transform: scale(1);}
            50% {transform: scale(1.2);}
            100% {transform: scale(1);}
        }

        .heart {
            position: absolute;
            color: red;
            animation: float 5s linear infinite;
        }

        @keyframes float {
            from {transform: translateY(100vh);}
            to {transform: translateY(-10vh);}
        }

        canvas {
            position: absolute;
            top: 0;
            left: 0;
            z-index: 1;
        }
    </style>
</head>
<body>

<canvas id="fireworks"></canvas>

<div class="card">
    <h1>Happy Birthday 🎂</h1>
    <div id="name">GEETA ❤️</div>
    <p>Even if our story changed, my good wishes for you never will.</p>
    <p>May your life shine brighter than these fireworks ✨</p>
</div>

<!-- 🎵 Background Music -->
<audio autoplay loop>
    <source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" type="audio/mpeg">
</audio>

<script>
    // Floating Hearts
    setInterval(() => {
        let heart = document.createElement("div");
        heart.innerHTML = "❤️";
        heart.className = "heart";
        heart.style.left = Math.random() * 100 + "vw";
        heart.style.fontSize = (20 + Math.random() * 20) + "px";
        document.body.appendChild(heart);
        setTimeout(() => heart.remove(), 5000);
    }, 300);

    // Fireworks
    const canvas = document.getElementById("fireworks");
    const ctx = canvas.getContext("2d");
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;

    let particles = [];

    function createFirework() {
        let x = Math.random() * canvas.width;
        let y = Math.random() * canvas.height / 2;
        for (let i = 0; i < 50; i++) {
            particles.push({
                x: x,
                y: y,
                angle: Math.random() * 2 * Math.PI,
                speed: Math.random() * 5 + 2,
                radius: 2,
                color: `hsl(${Math.random()*360}, 100%, 50%)`
            });
        }
    }

    function update() {
        ctx.clearRect(0, 0, canvas.width, canvas.height);
        particles.forEach((p, i) => {
            p.x += Math.cos(p.angle) * p.speed;
            p.y += Math.sin(p.angle) * p.speed;
            p.speed *= 0.98;
            ctx.beginPath();
            ctx.arc(p.x, p.y, p.radius, 0, Math.PI * 2);
            ctx.fillStyle = p.color;
            ctx.fill();
        });
        requestAnimationFrame(update);
    }

    setInterval(createFirework, 1000);
    update();
</script>

</body>
</html>
