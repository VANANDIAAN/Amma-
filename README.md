<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8"/>
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Happy Birthday Mom! 🌸</title>
  <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,400;0,600;0,700;1,400;1,600&family=Dancing+Script:wght@600;700&family=Nunito:wght@300;400;600;700&display=swap" rel="stylesheet"/>
  <style>
    :root {
      --rose:#E8637A; --blush:#F2A7B5; --gold:#D4A853;
      --teal:#4BACB8; --sand:#C8A97E; --sky:#7EB8C9;
      --lavender:#9B7EC8; --cream:#FDF6EE; --deep:#2C1A3A; --warm:#7A4F3A;
    }
    *,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
    html{scroll-behavior:smooth}
    body{background:var(--cream);font-family:'Nunito',sans-serif;color:var(--deep);overflow-x:hidden}

    #confetti-canvas{position:fixed;top:0;left:0;width:100%;height:100%;pointer-events:none;z-index:999}

    /* HERO */
    .hero{min-height:100vh;position:relative;display:flex;flex-direction:column;align-items:center;justify-content:center;text-align:center;padding:3rem 2rem 5rem;overflow:hidden}
    .hero-bg{position:absolute;inset:0;background:linear-gradient(160deg,#7EB8C9 0%,#9B7EC8 30%,#E8637A 60%,#D4A853 100%);z-index:0}
    .bokeh{position:absolute;inset:0;z-index:1;overflow:hidden}
    .bokeh span{position:absolute;border-radius:50%;background:rgba(255,255,255,0.12);animation:drift linear infinite}
    @keyframes drift{0%{transform:translateY(110vh) scale(.5);opacity:0}10%{opacity:1}90%{opacity:.6}100%{transform:translateY(-20vh) scale(1.3);opacity:0}}
    .hero-content{position:relative;z-index:2}
    .hero-icon{font-size:4rem;animation:float 3s ease-in-out infinite;display:block;margin-bottom:1rem}
    @keyframes float{0%,100%{transform:translateY(0) rotate(-5deg)}50%{transform:translateY(-16px) rotate(5deg)}}
    .hero h1{font-family:'Dancing Script',cursive;font-size:clamp(3.5rem,11vw,7.5rem);color:#fff;text-shadow:2px 4px 20px rgba(0,0,0,.2);line-height:1.05;animation:rise 1s ease both}
    @keyframes rise{from{opacity:0;transform:translateY(40px)}to{opacity:1;transform:translateY(0)}}
    .hero-sub{font-family:'Cormorant Garamond',serif;font-style:italic;font-size:clamp(1.1rem,3vw,1.7rem);color:rgba(255,255,255,.9);margin-top:1.2rem;animation:rise 1s .25s ease both}
    .hero-divider{width:120px;height:2px;background:rgba(255,255,255,.5);margin:1.5rem auto;animation:rise 1s .4s ease both}
    .hero-place{font-size:1rem;color:rgba(255,255,255,.75);letter-spacing:.18em;text-transform:uppercase;animation:rise 1s .5s ease both}
    .scroll-cue{position:absolute;bottom:2rem;left:50%;transform:translateX(-50%);z-index:2;display:flex;flex-direction:column;align-items:center;gap:.3rem;color:rgba(255,255,255,.6);font-size:.8rem;letter-spacing:.1em;animation:bounce 2s infinite}
    @keyframes bounce{0%,100%{transform:translateX(-50%) translateY(0)}50%{transform:translateX(-50%) translateY(8px)}}

    /* CHAPTER HEADERS */
    .chapter{display:flex;align-items:center;gap:1.2rem;padding:3.5rem 2rem 1.5rem;max-width:1200px;margin:0 auto}
    .chapter-line{flex:1;height:1px;background:linear-gradient(90deg,transparent,var(--blush),transparent)}
    .chapter h2{font-family:'Dancing Script',cursive;font-size:clamp(1.8rem,5vw,2.8rem);background:linear-gradient(135deg,var(--rose),var(--lavender));-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;white-space:nowrap}

    /* FEATURE PHOTO */
    .feature-wrap{max-width:700px;margin:0 auto 1rem;padding:0 1.5rem}
    .feature-photo{border-radius:24px;overflow:hidden;box-shadow:0 20px 60px rgba(0,0,0,.2);position:relative;cursor:zoom-in}
    .feature-photo img{width:100%;display:block;max-height:600px;object-fit:cover;object-position:top}
    .overlay-badge{position:absolute;bottom:1.5rem;left:50%;transform:translateX(-50%);background:rgba(255,255,255,.92);border-radius:50px;padding:.5rem 1.5rem;font-family:'Cormorant Garamond',serif;font-style:italic;font-size:1.1rem;color:var(--warm);white-space:nowrap;backdrop-filter:blur(10px)}

    /* MASONRY */
    .grid-wrap{max-width:1200px;margin:0 auto;padding:0 1.2rem 3rem}
    .masonry{columns:3;column-gap:1rem}
    @media(max-width:800px){.masonry{columns:2}}
    @media(max-width:480px){.masonry{columns:1}}
    .tile{break-inside:avoid;margin-bottom:1rem;border-radius:16px;overflow:hidden;position:relative;box-shadow:0 6px 24px rgba(0,0,0,.12);transition:transform .35s cubic-bezier(.34,1.56,.64,1),box-shadow .35s;animation:popUp .6s var(--d,0s) ease both;cursor:zoom-in}
    @keyframes popUp{from{opacity:0;transform:scale(.85) translateY(20px)}to{opacity:1;transform:scale(1) translateY(0)}}
    .tile:hover{transform:scale(1.03) translateY(-4px);box-shadow:0 18px 50px rgba(0,0,0,.22);z-index:10}
    .tile img{width:100%;display:block}
    .tile .cap{padding:.6rem 1rem;font-size:.8rem;font-weight:700;letter-spacing:.04em;text-align:center;color:#fff}

    /* QUOTE */
    .quote-section{padding:6rem 2rem;text-align:center;position:relative;overflow:hidden;background:linear-gradient(135deg,#2C1A3A 0%,#4A2060 50%,#7A3050 100%)}
    .quote-section::before{content:'❤';position:absolute;font-size:28rem;opacity:.05;top:50%;left:50%;transform:translate(-50%,-50%);color:white;pointer-events:none}
    .quote-section blockquote{font-family:'Cormorant Garamond',serif;font-style:italic;font-size:clamp(1.3rem,3.5vw,2.2rem);color:rgba(255,255,255,.93);max-width:750px;margin:0 auto 2rem;line-height:1.8;position:relative;z-index:1}
    .quote-section blockquote::before{content:'\201C';font-size:4rem;color:var(--blush);line-height:0;vertical-align:-1.5rem;margin-right:.2rem}
    .quote-section blockquote::after{content:'\201D';font-size:4rem;color:var(--blush);line-height:0;vertical-align:-1.5rem;margin-left:.2rem}
    .quote-sig{font-family:'Dancing Script',cursive;font-size:2rem;color:var(--gold);position:relative;z-index:1}

    /* WISHES */
    .wishes{max-width:860px;margin:0 auto;padding:1rem 1.5rem 4rem;display:grid;grid-template-columns:repeat(auto-fill,minmax(240px,1fr));gap:1.2rem}
    .wish-card{background:#fff;border-radius:18px;padding:1.6rem 1.4rem;box-shadow:0 4px 20px rgba(0,0,0,.08);text-align:center;border-top:4px solid var(--c,var(--rose));transition:transform .3s}
    .wish-card:hover{transform:translateY(-6px)}
    .wish-card .wish-icon{font-size:2.2rem;margin-bottom:.6rem;display:block}
    .wish-card p{font-family:'Cormorant Garamond',serif;font-style:italic;font-size:1.05rem;color:var(--warm);line-height:1.5}

    /* CAKE */
    .cake-section{text-align:center;background:linear-gradient(180deg,#FDF6EE 0%,#FEE8EF 100%);padding:4rem 2rem 5rem}
    .cake-emoji{font-size:7rem;display:block;animation:float 2.5s ease-in-out infinite}
    .candles{font-size:3rem;letter-spacing:.2rem;margin-top:.5rem}
    .cake-msg{font-family:'Cormorant Garamond',serif;font-style:italic;font-size:1.5rem;color:var(--warm);margin-top:1.5rem}

    /* FOOTER */
    footer{background:var(--deep);color:rgba(255,255,255,.6);text-align:center;padding:2.5rem 1rem;font-size:.9rem}
    footer .heart{color:var(--rose);font-size:1.1rem}

    /* LIGHTBOX */
    .lightbox{display:none;position:fixed;inset:0;background:rgba(0,0,0,.92);z-index:1000;align-items:center;justify-content:center;cursor:zoom-out}
    .lightbox.open{display:flex}
    .lightbox img{max-width:92vw;max-height:92vh;border-radius:12px;box-shadow:0 0 80px rgba(0,0,0,.6);animation:zoomIn .25s ease}
    @keyframes zoomIn{from{opacity:0;transform:scale(.85)}to{opacity:1;transform:scale(1)}}
    .lb-close{position:fixed;top:1.2rem;right:1.5rem;color:white;font-size:2rem;cursor:pointer;background:rgba(255,255,255,.12);border-radius:50%;width:2.5rem;height:2.5rem;display:flex;align-items:center;justify-content:center;transition:background .2s}
    .lb-close:hover{background:rgba(255,255,255,.25)}
  </style>
</head>
<body>

<canvas id="confetti-canvas"></canvas>

<div class="lightbox" id="lightbox">
  <span class="lb-close" id="lb-close">✕</span>
  <img id="lb-img" src="" alt=""/>
</div>

<!-- HERO -->
<section class="hero">
  <div class="hero-bg"></div>
  <div class="bokeh" id="bokeh"></div>
  <div class="hero-content">
    <span class="hero-icon">🌸</span>
    <h1>Happy Birthday,<br>Mom!</h1>
    <div class="hero-divider"></div>
    <p class="hero-sub">You are our sunshine, our strength, our everything.</p>
    <p class="hero-place">📍 Mahabalipuram · A Day to Remember</p>
  </div>
  <div class="scroll-cue">scroll ↓</div>
</section>

<!-- SPOTLIGHT -->
<div class="chapter"><div class="chapter-line"></div><h2>✨ Our Radiant Queen ✨</h2><div class="chapter-line"></div></div>
<div class="feature-wrap">
  <div class="feature-photo" onclick="openLightbox('IMG_1011.jpeg')">
    <img src="IMG_1011.jpeg" alt="Mom at the Shore Temple"/>
    <div class="overlay-badge">Grace in every step 🌊</div>
  </div>
</div>

<!-- BEACH -->
<div class="chapter"><div class="chapter-line"></div><h2>🌊 By the Sea</h2><div class="chapter-line"></div></div>
<div class="grid-wrap"><div class="masonry" id="beach-grid"></div></div>

<!-- TEMPLE -->
<div class="chapter"><div class="chapter-line"></div><h2>🛕 Shore Temple Moments</h2><div class="chapter-line"></div></div>
<div class="grid-wrap"><div class="masonry" id="temple-grid"></div></div>

<!-- QUOTE -->
<section class="quote-section">
  <blockquote>A mother is she who can take the place of all others,<br>but whose place no one else can ever take.</blockquote>
  <p class="quote-sig">— With all our love 💕</p>
</section>

<!-- WISHES -->
<div class="chapter"><div class="chapter-line"></div><h2>🎁 Our Wishes for You</h2><div class="chapter-line"></div></div>
<div class="wishes">
  <div class="wish-card" style="--c:#E8637A"><span class="wish-icon">🌺</span><p>May every day bloom with as much beauty as you bring to ours.</p></div>
  <div class="wish-card" style="--c:#4BACB8"><span class="wish-icon">🌊</span><p>May your life always flow as freely as the waves at Mahabalipuram.</p></div>
  <div class="wish-card" style="--c:#D4A853"><span class="wish-icon">☀️</span><p>May your smile never fade — it lights up every room and every heart.</p></div>
  <div class="wish-card" style="--c:#9B7EC8"><span class="wish-icon">🫶</span><p>Thank you for your endless love, patience, and warmth. We are so lucky.</p></div>
  <div class="wish-card" style="--c:#C8A97E"><span class="wish-icon">✈️</span><p>Wishing you adventures, joy, and many more beautiful photoshoots together!</p></div>
  <div class="wish-card" style="--c:#E8637A"><span class="wish-icon">👑</span><p>Today is YOUR day, Queen. Eat cake, feel loved, and soak it all in!</p></div>
</div>

<!-- CAKE -->
<section class="cake-section">
  <div class="chapter" style="padding-top:0"><div class="chapter-line"></div><h2>🎂 Make a Wish!</h2><div class="chapter-line"></div></div>
  <span class="cake-emoji">🎂</span>
  <div class="candles">🕯🕯🕯🕯🕯🕯🕯🕯🕯🕯</div>
  <p class="cake-msg">Close your eyes, make a wish, and blow! 💫</p>
</section>

<footer>
  <p>Made with <span class="heart">♥</span> by your family &nbsp;·&nbsp; Happy Birthday, Mom! 🎉</p>
  <p style="margin-top:.5rem;opacity:.4;font-size:.8rem;">Mahabalipuram · Shore Temple · Our Forever Memories</p>
</footer>

<script>
const beachPhotos = [
  { file:'IMG_1019.jpeg', cap:'Walking together 🌊',    color:'#4BACB8' },
  { file:'IMG_1018.jpeg', cap:'Hand in hand 💕',        color:'#E8637A' },
  { file:'IMG_1017.jpeg', cap:'Sandy shores 🏖️',        color:'#D4A853' },
  { file:'IMG_1016.jpeg', cap:'The whole squad 🌟',     color:'#9B7EC8' },
  { file:'IMG_1015.jpeg', cap:'Dreaming by the sea 🌅', color:'#7EB8C9' },
  { file:'IMG_1014.jpeg', cap:'Sunshine portrait ☀️',   color:'#E8637A' },
  { file:'IMG_1013.jpeg', cap:'Waves & smiles 🐚',      color:'#4BACB8' },
];

const templePhotos = [
  { file:'IMG_1010.jpeg', cap:'Ancient wonders 🛕',     color:'#C8A97E' },
  { file:'IMG_1009.jpeg', cap:'Family forever 💞',      color:'#E8637A' },
  { file:'IMG_1003.jpeg', cap:'Together always 🌸',     color:'#9B7EC8' },
  { file:'IMG_1002.jpeg', cap:'Golden hour 🌇',         color:'#D4A853' },
  { file:'IMG_1008.jpeg', cap:'Pure joy 😄',            color:'#4BACB8' },
  { file:'IMG_1007.jpeg', cap:'Hugs & laughter 🤗',     color:'#E8637A' },
  { file:'IMG_1001.jpeg', cap:'Walking into history ✨', color:'#C8A97E' },
  { file:'IMG_0999.jpeg', cap:'Beautiful family 💖',    color:'#9B7EC8' },
  { file:'IMG_1005.jpeg', cap:'Sunset vibes 🌆',        color:'#7EB8C9' },
  { file:'IMG_1004.jpeg', cap:'Looking up 🌤️',          color:'#D4A853' },
  { file:'IMG_0998.jpeg', cap:'The whole world 🌏',     color:'#E8637A' },
  { file:'IMG_1012.jpeg', cap:'Timeless moments ⏳',    color:'#4BACB8' },
];

function buildGrid(photos, id) {
  const c = document.getElementById(id);
  photos.forEach((p, i) => {
    const t = document.createElement('div');
    t.className = 'tile';
    t.style.setProperty('--d', `${i*.07}s`);
    t.innerHTML = `<img src="${p.file}" alt="${p.cap}" loading="lazy"/><div class="cap" style="background:${p.color}">${p.cap}</div>`;
    t.addEventListener('click', () => openLightbox(p.file));
    c.appendChild(t);
  });
}
buildGrid(beachPhotos, 'beach-grid');
buildGrid(templePhotos, 'temple-grid');

// Lightbox
const lb = document.getElementById('lightbox');
const lbImg = document.getElementById('lb-img');
function openLightbox(src) { lbImg.src = src; lb.classList.add('open'); }
lb.addEventListener('click', () => lb.classList.remove('open'));
document.getElementById('lb-close').addEventListener('click', e => { e.stopPropagation(); lb.classList.remove('open'); });

// Bokeh
const bokeh = document.getElementById('bokeh');
for (let i = 0; i < 18; i++) {
  const s = document.createElement('span');
  const sz = 40 + Math.random()*120;
  s.style.cssText = `width:${sz}px;height:${sz}px;left:${Math.random()*100}%;animation-duration:${8+Math.random()*12}s;animation-delay:${Math.random()*10}s;`;
  bokeh.appendChild(s);
}

// Confetti
const canvas = document.getElementById('confetti-canvas');
const ctx = canvas.getContext('2d');
const COLORS = ['#E8637A','#D4A853','#4BACB8','#9B7EC8','#F2A7B5','#7EB8C9','#C8A97E'];
let pieces = [];
function resize(){ canvas.width=window.innerWidth; canvas.height=window.innerHeight; }
resize(); window.addEventListener('resize', resize);
function spawn(n){
  for(let i=0;i<n;i++){
    const shape=Math.random()>.5?'rect':'circle';
    pieces.push({x:Math.random()*canvas.width,y:-10,w:6+Math.random()*10,h:4+Math.random()*8,r:Math.random()*Math.PI*2,vx:(Math.random()-.5)*2.5,vy:1.5+Math.random()*3,vr:(Math.random()-.5)*.15,color:COLORS[Math.floor(Math.random()*COLORS.length)],alpha:1,shape});
  }
}
function draw(){
  ctx.clearRect(0,0,canvas.width,canvas.height);
  pieces=pieces.filter(p=>p.alpha>.05);
  pieces.forEach(p=>{
    p.x+=p.vx;p.y+=p.vy;p.r+=p.vr;
    if(p.y>canvas.height*.75)p.alpha-=.015;
    ctx.save();ctx.globalAlpha=p.alpha;ctx.translate(p.x,p.y);ctx.rotate(p.r);ctx.fillStyle=p.color;
    if(p.shape==='circle'){ctx.beginPath();ctx.arc(0,0,p.w/2,0,Math.PI*2);ctx.fill();}
    else{ctx.fillRect(-p.w/2,-p.h/2,p.w,p.h);}
    ctx.restore();
  });
  requestAnimationFrame(draw);
}
draw(); spawn(180); setInterval(()=>spawn(6),1200);
</script>
</body>
</html>
</html>
