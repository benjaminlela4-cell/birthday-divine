<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Happy Birthday Divine</title>

<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;700&family=Lato:wght@300;400&display=swap" rel="stylesheet">

<style>

/* =========================
   GLOBAL
========================= */

*{
  margin:0;
  padding:0;
  box-sizing:border-box;
}

body{
  font-family:'Lato',sans-serif;
  background: radial-gradient(circle at top, #2a0f4a, #0b0614);
  height:100vh;
  overflow:hidden;
  color:white;
}

/* soft glowing background */
body::before{
  content:"";
  position:fixed;
  width:100%;
  height:100%;
  background:
    radial-gradient(circle at 30% 30%, rgba(255,255,255,0.08), transparent 60%),
    radial-gradient(circle at 70% 70%, rgba(255,182,255,0.06), transparent 60%);
  animation:pulseBg 6s ease-in-out infinite;
}

@keyframes pulseBg{
  0%,100%{opacity:0.7;}
  50%{opacity:1;}
}

/* =========================
   FLOATING HEARTS
========================= */

.heart{
  position:fixed;
  color:rgba(255,255,255,0.35);
  pointer-events:none;
  animation:floatUp linear infinite;
}

@keyframes floatUp{
  from{transform:translateY(100vh) scale(1);}
  to{transform:translateY(-10vh) scale(1.3);}
}

/* =========================
   SLIDES
========================= */

.slide{
  display:none;
  height:100vh;
  width:100%;
  align-items:center;
  justify-content:center;
  flex-direction:column;
  text-align:center;
  opacity:0;
  transform:translateY(20px);
  transition:1.2s ease;
}

.slide.active{
  display:flex;
  opacity:1;
  transform:translateY(0);
}

/* =========================
   INTRO CAKE
========================= */

.cake-wrap{
  position:relative;
  margin-bottom:30px;
}

.cake{
  width:200px;
  height:90px;
  background:#ffd6e0;
  border-radius:20px;
  position:relative;
}

.cake::before{
  content:"";
  position:absolute;
  top:-35px;
  left:20px;
  width:160px;
  height:40px;
  background:#ffe5ec;
  border-radius:20px;
}

.candle{
  position:absolute;
  top:-75px;
  left:95px;
  width:10px;
  height:45px;
  background:white;
  border-radius:5px;
}

.flame{
  position:absolute;
  top:-12px;
  left:-2px;
  width:14px;
  height:14px;
  background:radial-gradient(circle,#fff6b0,#ffcc33);
  border-radius:50%;
  cursor:pointer;
  animation:flicker 1.2s infinite;
  box-shadow:0 0 25px #ffcc33;
}

@keyframes flicker{
  0%,100%{transform:scale(1);}
  50%{transform:scale(1.15);}
}

/* =========================
   MAGIC PARTICLES
========================= */

.particle{
  position:absolute;
  width:4px;
  height:4px;
  background:white;
  border-radius:50%;
  opacity:0.4;
  animation:rise 10s linear infinite;
}

@keyframes rise{
  from{transform:translateY(100vh);}
  to{transform:translateY(-10vh);}
}

/* =========================
   INTRO / CONTENT TRANSITION
========================= */

.intro{
  position:fixed;
  width:100%;
  height:100vh;
  display:flex;
  align-items:center;
  justify-content:center;
  flex-direction:column;
  z-index:10;
  transition:2s ease;
  background: radial-gradient(circle at top, #2a0f4a, #0b0614);
}

.fade{
  position:fixed;
  width:100%;
  height:100vh;
  background:black;
  opacity:0;
  z-index:9;
  transition:2s ease;
}

/* =========================
   HERO / CONTENT
========================= */

.hero h1{
  font-family:'Playfair Display',serif;
  font-size:3rem;
  text-shadow:0 0 20px rgba(255,255,255,0.2);
}

p{
  max-width:340px;
  margin-top:15px;
  line-height:1.8;
  color:rgba(255,255,255,0.75);
}

/* BUTTON */
.btn{
  margin-top:25px;
  padding:12px 25px;
  background:transparent;
  border:1px solid rgba(255,255,255,0.3);
  color:white;
  cursor:pointer;
  opacity:0;
  pointer-events:none;
  transition:1s ease;
}

.btn.show-btn{
  opacity:1;
  pointer-events:auto;
}

/* =========================
   HEARTS STYLE
========================= */

.heart{
  position:fixed;
  animation:floatUp linear infinite;
}

</style>
</head>

<body>

<!-- BACKGROUND HEARTS -->
<div id="hearts"></div>

<!-- PARTICLES -->
<div id="particles"></div>

<!-- FADE LAYER -->
<div class="fade" id="fade"></div>

<!-- INTRO -->
<div class="intro" id="intro">

  <h2>Make a wish 💫</h2>

  <div class="cake-wrap">

    <div class="cake"></div>

    <div class="candle">
      <div class="flame" id="flame"></div>
    </div>

  </div>

</div>

<!-- SLIDE 2 -->
<div class="slide" id="slide2">

  <h1>Happy Birthday Divine 💛</h1>

  <p id="message"></p>

  <button class="btn" id="continueBtn" onclick="nextSlide(3)">
    Continue
  </button>

</div>

<!-- SLIDE 3 -->
<div class="slide" id="slide3">

  <h1>Stay Blessed 💫</h1>

  <p>
    Love from Big Bro 💛  
    Always proud of you. Always here for you.
  </p>

</div>

<script>

/* =========================
   FLOATING HEARTS
========================= */

const hearts = document.getElementById("hearts");

function createHearts(){

  const h = document.createElement("div");
  h.classList.add("heart");
  h.innerHTML = "❤";

  h.style.left = Math.random()*100 + "vw";
  h.style.fontSize = (10 + Math.random()*18) + "px";
  h.style.animationDuration = (6 + Math.random()*6) + "s";

  hearts.appendChild(h);

  setTimeout(()=>h.remove(),12000);
}

setInterval(createHearts, 2000);

/* =========================
   PARTICLES
========================= */

const particles = document.getElementById("particles");

for(let i=0;i<40;i++){

  const p = document.createElement("div");
  p.classList.add("particle");

  p.style.left = Math.random()*100 + "vw";
  p.style.animationDuration = (6 + Math.random()*8) + "s";

  particles.appendChild(p);

}

/* =========================
   TYPE MESSAGE
========================= */

const text = `Watching you grow has been one of the best parts of my life. You bring light into our family just by being you. I’m always proud of you, and I’ll always have your back. Keep shining sis, the world needs more of your kind heart.`;

let i = 0;
const messageEl = document.getElementById("message");
const btn = document.getElementById("continueBtn");

/* =========================
   CANDLE CLICK
========================= */

const flame = document.getElementById("flame");
const intro = document.getElementById("intro");
const fade = document.getElementById("fade");

flame.addEventListener("click",()=>{

  createMagicBurst();

  fade.style.opacity = "1";

  setTimeout(()=>{
    intro.style.opacity = "0";
  },800);

  setTimeout(()=>{

    intro.style.display = "none";
    fade.style.opacity = "0";

    nextSlide(2);
    setTimeout(typeText,800);

  },2000);

});

/* =========================
   MAGIC BURST
========================= */

function createMagicBurst(){

  for(let i=0;i<50;i++){

    const p = document.createElement("div");
    p.classList.add("particle");

    p.style.left = "50%";
    p.style.top = "50%";

    particles.appendChild(p);

    setTimeout(()=>p.remove(),1500);

  }

}

/* =========================
   TYPE EFFECT
========================= */

function typeText(){

  if(i < text.length){
    messageEl.innerHTML += text.charAt(i);
    i++;
    setTimeout(typeText,35);
  } else {
    setTimeout(()=>{
      btn.classList.add("show-btn");
    },800);
  }

}

/* =========================
   SLIDES
========================= */

function nextSlide(num){

  document.querySelectorAll('.slide')
  .forEach(s=>s.classList.remove('active'));

  document.getElementById('slide'+num)
  .classList.add('active');

}

</script>

</body>
</html>