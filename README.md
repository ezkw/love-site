# love-site
for Vlada ❤️
<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>💖</title>

<style>
body {
    margin:0;
    height:100vh;
    display:flex;
    justify-content:center;
    align-items:center;
    font-family:sans-serif;
    background: linear-gradient(135deg,#ff758c,#ff7eb3);
    overflow:hidden;
}

/* падающие сердечки */
.heart {
    position: fixed;
    top: -10px;
    font-size: 20px;
    animation: fall linear infinite;
}

@keyframes fall {
    to {
        transform: translateY(100vh);
    }
}

#box {
    background:white;
    padding:25px;
    border-radius:20px;
    text-align:center;
    width:90%;
    max-width:320px;
}

button {
    margin:10px;
    padding:12px 20px;
    border:none;
    border-radius:12px;
    font-size:16px;
}

#yes {
    background:#ff4d6d;
    color:white;
}

#no {
    background:#ddd;
    position:fixed;
}

#result {
    display:none;
    text-align:center;
    color:white;
    font-size:26px;
}
</style>
</head>

<body>

<div id="box">
<h2>Влада, ты меня любишь? 💖</h2>
<button id="yes">Да 💘</button>
<button id="no">Нет 😢</button>
</div>

<div id="result">
<h1>Я тебя тоже люблю ❤️</h1>
</div>

<script>
const noBtn = document.getElementById("no");
const yesBtn = document.getElementById("yes");
const box = document.getElementById("box");
const result = document.getElementById("result");

let scale = 1;

// убегающая кнопка
function move() {
    const x = Math.random() * (window.innerWidth - 100);
    const y = Math.random() * (window.innerHeight - 60);

    noBtn.style.left = x + "px";
    noBtn.style.top = y + "px";

    scale -= 0.1;
    if (scale < 0.4) scale = 0.4;

    noBtn.style.transform = "scale(" + scale + ")";
}

noBtn.addEventListener("touchstart", move);
noBtn.addEventListener("mouseover", move);

// кнопка да
yesBtn.onclick = () => {
    box.style.display = "none";
    result.style.display = "block";
};

// сердечки
setInterval(() => {
    const heart = document.createElement("div");
    heart.classList.add("heart");
    heart.innerHTML = "💖";
    heart.style.left = Math.random() * 100 + "vw";
    heart.style.animationDuration = (Math.random() * 3 + 2) + "s";
    document.body.appendChild(heart);

    setTimeout(() => {
        heart.remove();
    }, 5000);
}, 300);
</script>

</body>
</html>
