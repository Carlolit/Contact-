<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<title>Контакты — Новый год</title>

<style>
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
        overflow: hidden;
    }

    @keyframes winterBG {
        0% {background-position: 0% 50%;}
        50% {background-position: 100% 50%;}
        100% {background-position: 0% 50%;}
    }

    .music-btn, .lang-switch {
        position: fixed;
        top: 20px;
        padding: 10px 18px;
        font-size: 16px;
        background: rgba(255,255,255,0.85);
        border-radius: 12px;
        cursor: pointer;
        box-shadow: 0 4px 15px rgba(0,0,0,0.2);
        backdrop-filter: blur(4px);
        border: 1px solid rgba(255,255,255,0.5);
        transition: 0.3s;
        z-index: 999;
    }

    .music-btn { left: 20px; }
    .lang-switch { right: 20px; }

    .music-btn:hover, .lang-switch:hover {
        transform: scale(1.05);
        background: rgba(255,255,255,1);
    }

    .container {
        max-width: 500px;
        width: 90%;
        background: rgba(255,255,255,0.85);
        padding: 40px 30px;
        border-radius: 25px;
        text-align: center;
        box-shadow: 0 15px 35px rgba(0,0,0,0.15);
        backdrop-filter: blur(4px);
        border: 2px solid rgba(255,255,255,0.6);
    }

    h1 { margin-bottom: 20px; font-size: 32px; color: #005cb2; }
    p { font-size: 17px; margin-bottom: 30px; }

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
    }

    .contacts a:hover {
        transform: scale(1.05);
        background: linear-gradient(90deg, #b71c1c, #d32f2f);
    }

    .snowflake {
        position: fixed;
        top: -10px;
        color: white;
        user-select: none;
        animation: snowfall linear infinite;
        opacity: 0.8;
    }

    @keyframes snowfall {
        to { transform: translateY(110vh); opacity: 0.2; }
    }
</style>
</head>

<body>

<!-- МУЗЫКА (обязательно в теле!) -->
<audio id="bgMusic" preload="auto" loop>
    <source src="https://cdn.pixabay.com/download/audio/2022/12/26/audio_7ebf05e400.mp3" type="audio/mpeg">
</audio>

<!-- Кнопки -->
<div class="music-btn" onclick="toggleMusic()">🔔 Музыка</div>
<div class="lang-switch" onclick="toggleLang()">RU / EN</div>

<!-- Контент -->
<div class="container">
    <h1 id="title">🎄 Привет! Я Карло 🎅</h1>
    <p id="subtitle">Тут собраны мои контакты. Желаю тебе волшебных праздников! ✨</p>

    <div class="contacts">
        <a href="https://t.me/" target="_blank">Telegram</a>
        <a href="https://vk.com/" target="_blank">VK</a>
        <a href="https://t.me/" target="_blank">Telegram Channel</a>
    </div>
</div>

<script>
    /* Снег */
    for (let i = 0; i < 40; i++) {
        let flake = document.createElement("div");
        flake.className = "snowflake";
        flake.textContent = "❄";
        flake.style.left = Math.random() * 100 + "vw";
        flake.style.fontSize = (Math.random() * 14 + 10) + "px";
        flake.style.animationDuration = (Math.random() * 8 + 6) + "s";
        flake.style.animationDelay = Math.random() * 5 + "s";
        document.body.appendChild(flake);
    }

    /* Музыка */
    let isPlaying = false;
    const music = document.getElementById("bgMusic");

    function toggleMusic() {
        if (isPlaying) {
            music.pause();
            isPlaying = false;
            document.querySelector(".music-btn").innerText = "🔔 Музыка";
        } else {
            music.volume = 0.7;
            music.play().then(() => {
                isPlaying = true;
                document.querySelector(".music-btn").innerText = "🔕 Выключить";
            }).catch(err => {
                console.log("Браузер заблокировал звук: ", err);
            });
        }
    }

    /* Переключатель языка */
    let currentLang = "ru";

    function toggleLang() {
        currentLang = currentLang === "ru" ? "en" : "ru";

        if (currentLang === "ru") {
            title.innerText = "🎄 Привет! Я Карло 🎅";
            subtitle.innerText = "Тут собраны мои контакты. Желаю тебе волшебных праздников! ✨";
        } else {
            title.innerText = "🎄 Hello! I’m Carlo 🎅";
            subtitle.innerText = "Here are my contacts. Wishing you magical holidays! ✨";
        }
    }
</script>

</body>
</html>