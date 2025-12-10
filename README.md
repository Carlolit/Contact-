<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Контакты — Новый год</title>

<style>
  /* === Анимированный зимний фон === */
  body {
    margin: 0;
    padding: 0;
    font-family: 'Rubik', sans-serif;
    background: linear-gradient(-45deg, #9dd2ff, #cfe9ff, #f0faff, #b4e3ff);
    background-size: 400% 400%;
    animation: winterBG 15s ease infinite;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    color: #333;
    overflow: hidden;
  }

  @keyframes winterBG {
    0% {background-position: 0% 50%;}
    50% {background-position: 100% 50%;}
    100% {background-position: 0% 50%;}
  }

  /* === Переключатель языка === */
  .lang-switch {
    position: fixed;
    top: 20px;
    right: 20px;
    background: rgba(255,255,255,0.85);
    border-radius: 12px;
    padding: 10px 18px;
    font-size: 16px;
    cursor: pointer;
    box-shadow: 0 4px 15px rgba(0,0,0,0.2);
    transition: 0.3s;
    backdrop-filter: blur(4px);
    border: 1px solid rgba(255,255,255,0.5);
  }
  .lang-switch:hover {
    transform: scale(1.05);
    background: rgba(255,255,255,1);
  }

  /* === Контейнер === */
  .container {
    max-width: 500px;
    width: 90%;
    background: rgba(255,255,255,0.85);
    padding: 40px 30px;
    border-radius: 25px;
    text-align: center;
    box-shadow: 0 15px 35px rgba(0,0,0,0.15);
    animation: fadeIn 1.5s ease forwards;
    backdrop-filter: blur(4px);
    border: 2px solid rgba(255,255,255,0.6);
  }

  @keyframes fadeIn {
    from {opacity: 0; transform: translateY(-20px);}
    to {opacity: 1; transform: translateY(0);}
  }

  h1 {
    margin-bottom: 20px;
    font-size: 32px;
    color: #005cb2;
    text-shadow: 0 0 8px rgba(255,255,255,0.8);
  }

  p {
    font-size: 17px;
    margin-bottom: 30px;
  }

  /* === Новогодние кнопки === */
  .contacts a {
    display: block;
    margin: 12px 0;
    text-decoration: none;
    color: #fff;
    background: linear-gradient(90deg, #e53935, #d32f2f);
    padding: 14px 0;
    border-radius: 15px;
    font-size: 19px;
    font-weight: 500;
    transition: 0.3s;
    box-shadow: 0 5px 15px rgba(0,0,0,0.15);

    opacity: 0;
    transform: translateY(20px);
    animation: slideUp 0.5s forwards;
  }

  .contacts a:hover {
    background: linear-gradient(90deg, #b71c1c, #d32f2f);
    transform: scale(1.05);
    box-shadow: 0 8px 20px rgba(0,0,0,0.2);
  }

  .contacts a:nth-child(1) {animation-delay: 0.2s;}
  .contacts a:nth-child(2) {animation-delay: 0.4s;}
  .contacts a:nth-child(3) {animation-delay: 0.6s;}

  @keyframes slideUp {
    to {opacity: 1; transform: translateY(0);}
  }

  /* === Снегопад === */
  .snowflake {
    position: fixed;
    top: -10px;
    color: white;
    font-size: 1em;
    user-select: none;
    animation: snowfall linear infinite;
    opacity: 0.8;
  }

  @keyframes snowfall {
    to {
      transform: translateY(110vh);
      opacity: 0.2;
    }
  }
</style>
.music-btn {
  position: fixed;
  top: 20px;
  left: 20px;
  background: rgba(255,255,255,0.85);
  border-radius: 12px;
  padding: 10px 18px;
  font-size: 16px;
  cursor: pointer;
  box-shadow: 0 4px 15px rgba(0,0,0,0.2);
  transition: 0.3s;
  backdrop-filter: blur(4px);
  border: 1px solid rgba(255,255,255,0.5);
  z-index: 2000;
}

.music-btn:hover {
  transform: scale(1.05);
  background: rgba(255,255,255,1);
}
</head>

<body>
<!-- 🔔 КНОПКА МУЗЫКИ -->
<div class="music-btn" onclick="toggleMusic()">🔔 Музыка</div>

<!-- 🎵 НОВОГОДНЯЯ МЕЛОДИЯ -->
<audio id="bgMusic" loop>
  <source src="https://cdn.jsdelivr.net/gh/CarloLit/music/christmas.mp3" type="audio/mpeg">
</audio>
<!-- ❄️ КНОПКА ПЕРЕКЛЮЧЕНИЯ ЯЗЫКА ❄️ -->
<div class="lang-switch" onclick="toggleLang()">RU / EN</div>
<script>
  let isPlaying = false;
  const music = document.getElementById("bgMusic");

  function toggleMusic() {
    if (isPlaying) {
      music.pause();
      isPlaying = false;
      document.querySelector(".music-btn").innerHTML = "🔔 Музыка";
    } else {
      music.volume = 0.7;
      music.play();
      isPlaying = true;
      document.querySelector(".music-btn").innerHTML = "🔕 Выключить";
    }
  }
</script>
<!-- ❄️ СНЕЖИНКИ ❄️ -->
<script>
  const snowflakes = 40;

  for (let i = 0; i < snowflakes; i++) {
    let flake = document.createElement("div");
    flake.className = "snowflake";
    flake.textContent = "❄";
    flake.style.left = Math.random() * 100 + "vw";
    flake.style.fontSize = (Math.random() * 14 + 10) + "px";
    flake.style.animationDuration = (Math.random() * 8 + 6) + "s";
    flake.style.animationDelay = Math.random() * 5 + "s";
    document.body.appendChild(flake);
  }

  /* === ЛОГИКА ПЕРЕКЛЮЧЕНИЯ ЯЗЫКА === */
  let currentLang = "ru";

  function toggleLang() {
    currentLang = currentLang === "ru" ? "en" : "ru";

    if (currentLang === "ru") {
      document.getElementById("title").innerHTML = "🎄 Привет! Я Карло 🎅";
      document.getElementById("subtitle").innerHTML = "Тут собраны мои контакты и ссылки.";
    } else {
      document.getElementById("title").innerHTML = "🎄 Hello! I’m Carlo 🎅";
      document.getElementById("subtitle").innerHTML = "Here are my contacts and links.";
    }
  }
</script>

<div class="container">
  <h1 id="title">🎄 Привет! Я Карло 🎅</h1>
  <p id="subtitle">Тут собраны мои контакты. Желаю тебе волшебных праздников! ✨</p>

  <div class="contacts">
    <a href="https://t.me/M4aka" target="_blank">Telegram</a>
    <a href="https://vk.com/kak_dela_carlo" target="_blank">VK</a>
    <a href="https://t.me/CarloLitvinenko" target="_blank">Telegram Channel</a>
  </div>
</div>

</body>
</html>
