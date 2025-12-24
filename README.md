<!doctype html>
<html lang="id">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Selamat Tahun Baru — Untuk Sayangku</title>

  <!-- Google Fonts -->
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;700&family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">

  <link rel="stylesheet" href="styles.css">
  <meta name="theme-color" content="#0f1112">
</head>
<body>
  <main class="page">
    <div class="card" role="article" aria-labelledby="title">
      <div class="card-decor top-left"></div>
      <div class="card-decor bottom-right"></div>

      <header class="card-header">
        <!-- Portrait image: letakkan file photo.jpg / photo.webp di folder yang sama -->
        <div class="portrait" aria-hidden="false">
          <img src="photo.jpg" alt="Foto untuk Sayangku" loading="lazy" />
        </div>

        <h1 id="title" class="headline">Selamat Tahun Baru, Sayangku</h1>
        <p class="subhead">31 Desember 2025 — Dari, <strong>deajusss</strong></p>
      </header>

      <section class="card-body">
        <p class="message">Semoga tahun baru membawa cinta, kebahagiaan, dan segala yang terbaik untukmu. Aku mencintaimu, sekarang dan selamanya.</p>

        <div class="countdown" aria-live="polite">
          <div class="time" id="days"><span class="num">--</span><span class="label">hari</span></div>
          <div class="time" id="hours"><span class="num">--</span><span class="label">jam</span></div>
          <div class="time" id="minutes"><span class="num">--</span><span class="label">menit</span></div>
          <div class="time" id="seconds"><span class="num">--</span><span class="label">detik</span></div>
        </div>

        <div class="actions">
          <button id="celebrateBtn" class="btn" aria-pressed="false">Rayakan Sekarang</button>
          <button id="audioBtn" class="btn btn-ghost" aria-pressed="false" title="Putar / Jeda musik">Putar Musik</button>
          <a class="btn btn-ghost" href="#" id="shareBtn" onclick="navigator.share && navigator.share({title: 'Selamat Tahun Baru', text: 'Selamat Tahun Baru, Sayangku — dari deajusss', url: location.href}); return false;">Bagikan</a>
        </div>

        <div class="audio-controls" aria-hidden="false">
          <label for="volume" class="visually-hidden">Volume</label>
          <input id="volume" type="range" min="0" max="1" step="0.01" value="0.7" />
          <button id="muteBtn" class="btn btn-ghost" title="Mode bisu">🔈</button>
        </div>
      </section>
    </div>

    <!-- Subtle floating sparkles -->
    <div class="sparkles" aria-hidden="true"></div>
  </main>

  <canvas id="confettiCanvas" class="confetti-canvas" aria-hidden="true"></canvas>

  <!-- Background audio: ganti background.mp3 dengan file Anda -->
  <audio id="bgAudio" src="background.mp3" loop preload="metadata"></audio>

  <script src="script.js"></script>
</body>
</html>
:root{
  --bg:#0b0b0c;
  --card-bg: rgba(255,255,255,0.03);
  --gold: #D9B84A;
  --muted: rgba(255,255,255,0.65);
  --radius: 18px;
  --card-padding: clamp(24px, 4vw, 48px);
  font-family: 'Poppins', system-ui, -apple-system, 'Segoe UI', Roboto, 'Helvetica Neue', Arial;
  color-scheme: dark;
}

*{box-sizing:border-box}
html,body,#root{height:100%}
body{
  margin:0;
  background:
    radial-gradient(1200px 800px at 10% 10%, rgba(217,184,74,0.06), transparent 8%),
    radial-gradient(800px 600px at 90% 90%, rgba(217,184,74,0.04), transparent 6%),
    var(--bg);
  font-size:16px;
  -webkit-font-smoothing:antialiased;
  -moz-osx-font-smoothing:grayscale;
  display:flex;
  align-items:center;
  justify-content:center;
  min-height:100vh;
  padding:32px;
}

/* Page layout */
.page{
  width:100%;
  max-width:980px;
  margin:0 auto;
  padding:20px;
}

/* Card */
.card{
  background: linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));
  border-radius:var(--radius);
  padding:var(--card-padding);
  box-shadow:
    0 6px 30px rgba(2,6,23,0.6),
    inset 0 1px 0 rgba(255,255,255,0.02);
  border: 1px solid rgba(217,184,74,0.12);
  position:relative;
  overflow:hidden;
}

/* Decorative corners */
.card-decor{
  position:absolute;
  width:220px;
  height:220px;
  pointer-events:none;
  opacity:0.12;
  filter: blur(18px);
  background: conic-gradient(from 0deg, rgba(217,184,74,0.9), rgba(255,255,255,0.02));
}
.card-decor.top-left{ top:-60px; left:-80px; transform: rotate(-25deg); }
.card-decor.bottom-right{ bottom:-60px; right:-80px; transform: rotate(160deg); }

/* Header */
.card-header{
  text-align:center;
  margin-bottom:18px;
}

/* Portrait */
.portrait{
  width:120px;
  height:120px;
  border-radius:50%;
  overflow:hidden;
  margin:0 auto 12px;
  border:4px solid rgba(217,184,74,0.12);
  box-shadow: 0 8px 30px rgba(2,6,23,0.6);
}
.portrait img{
  width:100%;
  height:100%;
  object-fit:cover;
  display:block;
}

/* Headline */
.headline{
  font-family: 'Playfair Display', Georgia, serif;
  color: white;
  margin:0 0 6px 0;
  font-size: clamp(1.6rem, 3.4vw, 2.6rem);
  letter-spacing: -0.02em;
  text-shadow: 0 2px 18px rgba(217,184,74,0.06);
}
.subhead{
  margin:0;
  color: var(--muted);
  font-size:0.95rem;
  font-weight:500;
}

/* Body */
.card-body{
  display:flex;
  flex-direction:column;
  gap:18px;
  align-items:center;
  padding-top:6px;
}
.message{
  color: rgba(255,255,255,0.9);
  font-size:1.05rem;
  line-height:1.5;
  max-width:720px;
  text-align:center;
  font-weight:300;
}

/* Countdown */
.countdown{
  display:flex;
  gap:12px;
  margin-top:4px;
  align-items:center;
  justify-content:center;
  flex-wrap:wrap;
}
.time{
  background: linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));
  padding:10px 14px;
  border-radius:12px;
  min-width:84px;
  text-align:center;
  border:1px solid rgba(217,184,74,0.07);
  box-shadow: 0 6px 20px rgba(2,6,23,0.5);
}
.time .num{
  display:block;
  font-weight:700;
  font-size:1.15rem;
  color:#fff;
  font-family: 'Poppins', sans-serif;
}
.time .label{
  font-size:0.75rem;
  color:var(--muted);
  display:block;
}

/* Buttons */
.actions{
  display:flex;
  gap:12px;
  margin-top:6px;
  align-items:center;
  justify-content:center;
  flex-wrap:wrap;
}
.btn{
  appearance:none;
  border:0;
  padding:10px 18px;
  background: linear-gradient(90deg,#f6d365,#fda085);
  color:#111;
  border-radius:999px;
  font-weight:600;
  cursor:pointer;
  box-shadow: 0 6px 20px rgba(253,160,133,0.12);
  transition: transform .16s ease, box-shadow .16s ease;
}
.btn:hover{ transform: translateY(-3px); box-shadow: 0 14px 36px rgba(253,160,133,0.14); }
.btn:active{ transform: translateY(-1px); }
.btn-ghost{
  background:transparent;
  border:1px solid rgba(255,255,255,0.06);
  color:var(--muted);
  box-shadow:none;
}

/* Audio controls */
.audio-controls{
  display:flex;
  gap:8px;
  align-items:center;
  margin-top:4px;
}
.audio-controls input[type="range"]{
  width:140px;
  appearance:none;
  height:6px;
  background: rgba(255,255,255,0.06);
  border-radius:6px;
}
.audio-controls input[type="range"]::-webkit-slider-thumb{
  appearance:none;
  width:14px;
  height:14px;
  border-radius:50%;
  background:var(--gold);
  box-shadow: 0 2px 6px rgba(217,184,74,0.2);
  border: none;
}

/* Sparkles background */
.sparkles{
  position:fixed;
  inset:0;
  pointer-events:none;
  background-image:
    radial-gradient(circle at 20% 10%, rgba(217,184,74,0.06) 0 1px, transparent 2px),
    radial-gradient(circle at 80% 70%, rgba(255,255,255,0.03) 0 2px, transparent 6px);
  mix-blend-mode: screen;
  opacity:0.9;
}

/* Confetti canvas */
.confetti-canvas{
  position:fixed;
  left:0;
  top:0;
  width:100%;
  height:100%;
  pointer-events:none;
  z-index:60;
}

/* Responsive tweaks */
@media (max-width:600px){
  .card{ padding:20px; border-radius:14px; }
  .time{ min-width:64px; padding:8px 10px; }
  .message{ font-size:0.98rem; }
}

/* Lux small accent underline */
.headline::after{
  content:'';
  display:block;
  width:74px;
  height:3px;
  margin:12px auto 0;
  border-radius:2px;
  background: linear-gradient(90deg, rgba(217,184,74,1), rgba(255,255,255,0.12));
  box-shadow: 0 4px 18px rgba(217,184,74,0.08);
}

/* Accessibility helper */
.visually-hidden{
  position:absolute !important;
  height:1px; width:1px;
  overflow:hidden;
  clip:rect(1px, 1px, 1px, 1px);
  white-space:nowrap;
}
// Target date: 31 December 2025 00:00:00 local time
const target = new Date('2025-12-31T00:00:00');

const daysEl = document.getElementById('days');
const hoursEl = document.getElementById('hours');
const minutesEl = document.getElementById('minutes');
const secondsEl = document.getElementById('seconds');
const celebrateBtn = document.getElementById('celebrateBtn');
const confettiCanvas = document.getElementById('confettiCanvas');

const audio = document.getElementById('bgAudio');
const audioBtn = document.getElementById('audioBtn');
const muteBtn = document.getElementById('muteBtn');
const volumeSlider = document.getElementById('volume');

let confettiActive = false;

// Initialize audio defaults
audio.volume = parseFloat(volumeSlider.value) || 0.7;
audio.preload = 'metadata';

// Update audio UI
function setAudioPlayingUI(isPlaying) {
  audioBtn.textContent = isPlaying ? 'Jeda Musik' : 'Putar Musik';
  audioBtn.setAttribute('aria-pressed', String(isPlaying));
}
function setMutedUI(isMuted) {
  muteBtn.textContent = isMuted ? '🔇' : '🔈';
}

// Toggle audio playback (call on user gesture)
async function toggleAudio() {
  try {
    if (audio.paused) {
      await audio.play();
      setAudioPlayingUI(true);
    } else {
      audio.pause();
      setAudioPlayingUI(false);
    }
  } catch (err) {
    // play failed (browser autoplay policies), keep UI consistent
    console.warn('Audio play failed:', err);
  }
}

// Mute / unmute
function toggleMute() {
  audio.muted = !audio.muted;
  setMutedUI(audio.muted);
  muteBtn.setAttribute('aria-pressed', String(audio.muted));
}

// Volume control
volumeSlider.addEventListener('input', (e) => {
  audio.volume = parseFloat(e.target.value);
  if (audio.volume === 0) {
    audio.muted = true;
    setMutedUI(true);
  } else {
    if (audio.muted) {
      audio.muted = false;
      setMutedUI(false);
    }
  }
});

// Wire buttons
audioBtn.addEventListener('click', (e) => {
  e.preventDefault();
  toggleAudio();
});
muteBtn.addEventListener('click', (e) => {
  e.preventDefault();
  toggleMute();
});

// Countdown update
function updateCountdown(){
  const now = new Date();
  let diff = Math.max(0, target - now);

  const sec = Math.floor(diff / 1000) % 60;
  const min = Math.floor(diff / (1000*60)) % 60;
  const hr = Math.floor(diff / (1000*60*60)) % 24;
  const day = Math.floor(diff / (1000*60*60*24));

  daysEl.querySelector('.num').textContent = String(day).padStart(2,'0');
  hoursEl.querySelector('.num').textContent = String(hr).padStart(2,'0');
  minutesEl.querySelector('.num').textContent = String(min).padStart(2,'0');
  secondsEl.querySelector('.num').textContent = String(sec).padStart(2,'0');

  if(diff <= 0){
    onCelebrate();
    clearInterval(intervalId);
  }
}

const intervalId = setInterval(updateCountdown, 250);
updateCountdown();

// Simple confetti (lightweight) ------------------------------------------------
function createConfetti() {
  if(confettiActive) return;
  confettiActive = true;

  const ctx = confettiCanvas.getContext('2d');
  const w = confettiCanvas.width = innerWidth;
  const h = confettiCanvas.height = innerHeight;

  const pieces = [];
  const colors = ['#D9B84A','#F4E1B1','#FFD9A6','#FFFFFF','#F6D365'];

  for(let i=0;i<120;i++){
    pieces.push({
      x: Math.random()*w,
      y: Math.random()*h - h,
      r: Math.random()*8 + 4,
      d: Math.random()*50 + 5,
      color: colors[Math.floor(Math.random()*colors.length)],
      tilt: Math.floor(Math.random()*20)-10,
      tiltSpeed: Math.random()*0.1+0.05
    });
  }

  let t = 0;
  function draw(){
    ctx.clearRect(0,0,w,h);
    for(const p of pieces){
      p.y += Math.cos(t + p.d) + 3 + p.r/2;
      p.x += Math.sin(t);
      p.tilt += p.tiltSpeed;

      ctx.save();
      ctx.translate(p.x, p.y);
      ctx.rotate(p.tilt * Math.PI / 180);
      ctx.fillStyle = p.color;
      ctx.fillRect(-p.r/2, -p.r/2, p.r, p.r*0.6);
      ctx.restore();

      if(p.y > h + 50){
        p.y = -10;
        p.x = Math.random()*w;
      }
    }
    t += 0.02;
    if(confettiActive) requestAnimationFrame(draw);
  }
  draw();

  // stop after a while
  setTimeout(()=> {
    confettiActive = false;
    ctx.clearRect(0,0,w,h);
  }, 10000);
}

// Celebrate handler
function onCelebrate(){
  // Change headline and show confetti
  document.querySelector('.headline').textContent = 'Selamat Tahun Baru!';
  document.querySelector('.subhead').textContent = '31 Desember 2025 — Dengan Cinta, deajusss';
  createConfetti();

  // Try to play audio (must be triggered by user gesture ideally)
  audio.play().then(()=> {
    setAudioPlayingUI(true);
  }).catch((err)=> {
    // autoplay without gesture blocked — keep silence until user interacts
    console.warn('Audio play blocked until user interacts:', err);
  });
}

// Button to trigger confetti anytime
celebrateBtn.addEventListener('click', ()=> {
  onCelebrate();
});

// Resize canvas on window resize
window.addEventListener('resize', ()=> {
  if(confettiCanvas.width !== innerWidth || confettiCanvas.height !== innerHeight){
    confettiCanvas.width = innerWidth;
    confettiCanvas.height = innerHeight;
  }
});

// On page load set UI according to state
document.addEventListener('DOMContentLoaded', ()=> {
  setAudioPlayingUI(!audio.paused && !audio.ended);
  setMutedUI(audio.muted);
});
