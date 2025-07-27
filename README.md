<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Te amo chiquitita</title>
  <style>
    html, body {
      margin: 0;
      padding: 0;
      overflow: hidden;
      height: 100%;
      background: radial-gradient(circle at center, #ffdde1, #ee9ca7);
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }

    h1 {
      position: absolute;
      top: 40%;
      width: 100%;
      text-align: center;
      font-size: 3em;
      color: #fff;
      animation: pulse 2s infinite ease-in-out;
      z-index: 10;
      text-shadow: 2px 2px 8px rgba(0, 0, 0, 0.2);
    }

    @keyframes pulse {
      0% { transform: scale(1); opacity: 1; }
      50% { transform: scale(1.1); opacity: 0.8; }
      100% { transform: scale(1); opacity: 1; }
    }

    .heart {
      position: absolute;
      width: 20px;
      height: 20px;
      background-color: red;
      transform: rotate(45deg);
      animation: fall linear infinite;
    }

    .heart::before,
    .heart::after {
      content: "";
      position: absolute;
      width: 20px;
      height: 20px;
      background-color: red;
      border-radius: 50%;
    }

    .heart::before {
      top: -10px;
      left: 0;
    }

    .heart::after {
      left: -10px;
      top: 0;
    }

    @keyframes fall {
      0% {
        transform: translateY(-10vh) rotate(45deg);
        opacity: 1;
      }
      100% {
        transform: translateY(100vh) rotate(45deg);
        opacity: 0;
      }
    }
  </style>
</head>
<body>
  <h1>Te amo chiquitita</h1>

  <script>
    const createHeart = () => {
      const heart = document.createElement('div');
      heart.className = 'heart';

      // Posición inicial aleatoria
      heart.style.left = Math.random() * 100 + 'vw';
      heart.style.animationDuration = 3 + Math.random() * 2 + 's';
      heart.style.opacity = Math.random();
      heart.style.transform = 'rotate(45deg) scale(' + (0.5 + Math.random()) + ')';

      document.body.appendChild(heart);

      setTimeout(() => {
        heart.remove();
      }, 5000);
    };

    setInterval(createHeart, 150);

    // Efecto interactivo al hacer clic
    document.addEventListener('click', (e) => {
      for (let i = 0; i < 10; i++) {
        setTimeout(() => {
          const heart = document.createElement('div');
          heart.className = 'heart';
          heart.style.left = (e.clientX - 10 + Math.random() * 20) + 'px';
          heart.style.top = (e.clientY - 10 + Math.random() * 20) + 'px';
          heart.style.animationDuration = 2 + Math.random() * 2 + 's';
          heart.style.opacity = 0.8;
          heart.style.transform = 'rotate(45deg) scale(' + (0.5 + Math.random() * 0.8) + ')';
          document.body.appendChild(heart);
          setTimeout(() => heart.remove(), 4000);
        }, i * 50);
      }
    });
  </script>
</body>
</html>
