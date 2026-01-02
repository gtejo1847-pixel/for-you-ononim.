# for you ononim.
<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Untukmu</title>

<style>
body {
  margin: 0;
  min-height: 100vh;
  font-family: Georgia, serif;
  background: linear-gradient(135deg, #f9f6f2, #ffe6f0);
  display: flex;
  justify-content: center;
  align-items: center;
}

.card {
  background: white;
  max-width: 520px;
  padding: 32px;
  border-radius: 20px;
  box-shadow: 0 8px 30px rgba(0,0,0,.15);
  animation: fadeIn 1.5s ease;
}

h1 {
  text-align: center;
  color: #c94f7c;
  margin-bottom: 24px;
}

.poem {
  text-align: left;
  font-size: 18px;
  line-height: 1.7;
  color: #333;
  white-space: pre-line;
}

#play {
  margin-top: 20px;
  text-align: center;
  font-size: 14px;
  color: #888;
  cursor: pointer;
  animation: blink 1.5s infinite;
}

.signature {
  margin-top: 20px;
  text-align: center;
  font-style: italic;
  color: #666;
}

@keyframes fadeIn {
  from { opacity: 0; transform: scale(.95); }
  to { opacity: 1; transform: scale(1); }
}

@keyframes blink {
  0% {opacity:.4}
  50% {opacity:1}
  100% {opacity:.4}
}

.heart {
  position: fixed;
  top: -10px;
  color: #e63963;
  font-size: 20px;
  animation: fall linear infinite;
}

@keyframes fall {
  to {
    transform: translateY(110vh) rotate(360deg);
    opacity: 0;
  }
}
</style>
</head>

<body>

<div class="card">
  <h1>Untukmu</h1>

  <div class="poem">
Aku sudah sampai di titik
tidak berharap apa-apa dari siapa pun.
Bukan karena kuat,
tapi karena capek jatuh di lubang yang sama.

Aku sudah yakin
tidak ada lagi yang bisa menggeser perhatianku,
lalu kamu datang
dan merusak keyakinan itu dengan cara yang tenang.

Aku tidak minta janji,
tidak juga kepastian.
Kalau pun ini salah,
biarlah salah yang aku pilih dengan sadar.

Kalau kamu mau tinggal sebentar,
ajari aku pelan-pelan
bahwa percaya tidak selalu berakhir
dengan kehilangan.
  </div>

  <div id="play">Klik di sini untuk memunculkan sesuatu</div>
  <div class="signature">— Djati</div>
</div>

<audio id="music" loop>
  <source src="musik.mpeg" type="audio/mpeg">
</audio>

<script>
const btn = document.getElementById("play");
const music = document.getElementById("music");

btn.addEventListener("click", async () => {
  try {
    await music.play();
    btn.style.display = "none";
    startHearts();
  } catch {
    alert("Klik sekali lagi");
  }
});

function startHearts(){
  setInterval(() => {
    const h = document.createElement("div");
    h.className = "heart";
    h.innerHTML = "❤";
    h.style.left = Math.random()*100+"vw";
    h.style.animationDuration = (Math.random()*3+3)+"s";
    document.body.appendChild(h);
    setTimeout(()=>h.remove(),6000);
  },600);
}
</script>

</body>
</html>
