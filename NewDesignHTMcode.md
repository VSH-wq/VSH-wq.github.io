<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>Vishwas Saini — Python Web Developer</title>
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700&display=swap" rel="stylesheet">

<style>
/* ===========================
   Theme variables
   =========================== */
:root{
  --bg:#05060a;
  --surface: rgba(255,255,255,0.04);
  --muted: rgba(255,255,255,0.65);
  --text:#eaf2ff;
  --accent:#00e5ff;
  --glass-border: rgba(255,255,255,0.08);
  --glass-shadow: rgba(0,0,0,0.6);
}
.light{
  --bg:#f4f7fb;
  --surface: rgba(255,255,255,0.8);
  --muted: #344154;
  --text:#0b1220;
  --accent:#2563eb;
  --glass-border: rgba(0,0,0,0.06);
  --glass-shadow: rgba(0,0,0,0.08);
}

/* Reset & basics */
*{box-sizing:border-box;margin:0;padding:0}
html,body{height:100%}
body{
  font-family:"Poppins",system-ui,-apple-system,Segoe UI,Roboto,"Helvetica Neue",Arial;
  background:var(--bg);
  color:var(--text);
  -webkit-font-smoothing:antialiased;
  -moz-osx-font-smoothing:grayscale;
  overflow-x:hidden;
}

/* Parallax decorative blobs (behind everything) */
.parallax{
  position:fixed;inset:0;pointer-events:none;z-index:0;overflow:hidden;
}
.parallax span{
  position:absolute;
  width:520px;height:520px;
  background:radial-gradient(circle,var(--accent),transparent 40%);
  opacity:.10;
  filter:blur(36px);
  transform:translateZ(0);
}
.parallax span.a{top:6%;left:6%;animation:floatA 26s linear infinite}
.parallax span.b{top:55%;left:72%;animation:floatB 34s linear infinite}
.parallax span.c{top:30%;left:46%;animation:floatC 38s linear infinite}
@keyframes floatA{from{transform:translateY(0)}to{transform:translateY(-220px)}}
@keyframes floatB{from{transform:translateY(0)}to{transform:translateY(-320px)}}
@keyframes floatC{from{transform:translateY(0)}to{transform:translateY(-260px)}}

/* Magnetic custom cursor */
#cursor{
  position:fixed;left:0;top:0;
  width:18px;height:18px;border-radius:50%;
  background:var(--accent);mix-blend-mode:screen;
  transform:translate(-50%,-50%);pointer-events:none;z-index:6000;
  transition:width .12s ease,height .12s ease,transform .12s ease,opacity .2s;
  will-change:transform;
}
.hide-cursor #cursor{opacity:0;}

/* Header / nav */
header{
  position:fixed;top:12px;left:0;right:0;z-index:2000;pointer-events:auto;
  display:flex;justify-content:center;
}
.navwrap{
  width:100%;max-width:1200px;padding:8px 20px;display:flex;
  align-items:center;justify-content:space-between;
  gap:12px;
  margin:auto;
}
.brand{
  display:flex;align-items:center;gap:10px;font-weight:600;color:var(--text);
  text-decoration:none;
}
.brand .logo{
  width:36px;height:36px;border-radius:8px;
  background:linear-gradient(135deg,var(--accent),#5ee7ff);
  display:flex;align-items:center;justify-content:center;font-weight:700;color:#021;
  box-shadow: 0 6px 18px rgba(0,0,0,0.35);
}
.nav{
  display:flex;align-items:center;gap:18px;
}
.nav a{color:var(--muted);text-decoration:none;font-weight:600;font-size:14px;opacity:.95}
.iconlink{display:inline-flex;gap:10px;align-items:center;padding:8px;border-radius:10px}
.smallbtn{
  background:transparent;border:1px solid var(--glass-border);padding:8px 12px;border-radius:12px;
  color:var(--muted);backdrop-filter:blur(6px);
}

/* Mobile */
.menu-btn{display:none}
@media (max-width:880px){
  .nav a{display:none}
  .menu-btn{display:inline-flex}
}

/* Cinematic Hero */
.hero{
  position:relative;z-index:10;padding:110px 20px 40px;min-height:68vh;display:flex;align-items:center;
}
.hero-inner{max-width:1200px;margin:auto;display:grid;grid-template-columns:1fr 520px;gap:40px;align-items:center}
.hero-content h1{font-size:46px;line-height:1.02;margin-bottom:14px}
.hero-content h1 .accent{color:var(--accent)}
.hero-content p{color:var(--muted);font-size:17px;max-width:720px;margin-bottom:18px}
.hero-cta{display:flex;gap:14px;align-items:center;margin-top:8px}

/* Cinematic project image (blurred background + ken-burns) */
.hero-shot{
  width:100%;height:380px;border-radius:18px;overflow:hidden;position:relative;
  box-shadow:0 30px 60px rgba(0,0,0,0.6);
  border:1px solid var(--glass-border);
  background:linear-gradient(180deg,rgba(0,0,0,0.08),rgba(0,0,0,0.12));
}
.hero-shot img{
  width:100%;height:100%;object-fit:cover;display:block;transform-origin:center center;
  animation:kenburns 18s ease-in-out infinite alternate;
  filter:contrast(1.02) saturate(1.06);
}
.hero-shot::after{
  content:"";position:absolute;inset:0;
  background:linear-gradient(180deg,rgba(3,6,12,0.00) 0%, rgba(3,6,12,0.35) 70%);
}
@keyframes kenburns{from{transform:scale(1) translateY(0)}to{transform:scale(1.08) translateY(-18px)}}

/* Glassmorphism project card (featured) */
.feature{
  margin-top:22px;padding:20px;border-radius:14px;background:var(--surface);
  border:1px solid var(--glass-border);backdrop-filter:blur(8px);
  box-shadow:0 10px 30px var(--glass-shadow);
}

/* Projects grid */
.section{
  padding:70px 20px 120px;max-width:1200px;margin:0 auto;position:relative;z-index:10;
}
.filters{display:flex;gap:12px;margin-bottom:22px;flex-wrap:wrap}
.filter-btn{
  padding:10px 16px;border-radius:14px;border:none;background:transparent;border:1px solid var(--glass-border);
  color:var(--muted);cursor:pointer;font-weight:600;backdrop-filter:blur(8px)
}
.filter-btn.active{background:linear-gradient(90deg,var(--accent),#7ee8ff);color:#021}

/* cards grid */
.cards{display:grid;grid-template-columns:repeat(auto-fit,minmax(280px,1fr));gap:22px}
.card{
  perspective:1200px; /* needed for 3D effect */
}
.card-inner{
  background:var(--surface);border-radius:16px;padding:18px;border:1px solid var(--glass-border);
  transition:transform .35s cubic-bezier(.16,1,.3,1),box-shadow .35s;
  transform-style:preserve-3d;
  box-shadow:0 8px 26px rgba(0,0,0,0.45);
}
.card-inner:hover{transform:translateY(-10px) rotateX(6deg) rotateY(-6deg)}
.card-thumb{width:100%;height:160px;border-radius:10px;overflow:hidden;margin-bottom:12px}
.card-thumb img{width:100%;height:100%;object-fit:cover}

/* skills row / contact */
.skills{display:flex;flex-wrap:wrap;gap:10px;margin-top:10px}
.skill-pill{padding:8px 12px;border-radius:999px;background:var(--surface);border:1px solid var(--glass-border);color:var(--muted);font-weight:600}

/* modal viewer */
#modal{position:fixed;inset:0;background:rgba(0,0,0,0.86);display:none;align-items:center;justify-content:center;z-index:9999}
#modal img{max-width:94%;max-height:92%;border-radius:14px;box-shadow:0 20px 80px rgba(0,0,0,0.8)}

/* footer / socials */
.footer{padding:40px 20px;text-align:center;color:var(--muted);opacity:.95}
.socials{display:flex;gap:12px;justify-content:center;margin-top:8px}

@media (max-width:1000px){
  .hero-inner{grid-template-columns:1fr;gap:20px}
  .hero-shot{height:300px}
  .parallax span{display:none}
  .cards{grid-template-columns:repeat(auto-fit,minmax(240px,1fr))}
}
@media (max-width:520px){
  .hero-content h1{font-size:28px}
  header{top:8px}
}

/* small utility */
.center{text-align:center}
.muted{color:var(--muted);font-size:14px}
</style>
</head>
<body>

<!-- Parallax decorative blobs -->
<div class="parallax" aria-hidden="true">
  <span class="a"></span>
  <span class="b"></span>
  <span class="c"></span>
</div>

<!-- Magnetic custom cursor -->
<div id="cursor" aria-hidden="true"></div>

<!-- Header -->
<header>
  <div class="navwrap">
    <a class="brand" href="#">
      <div class="logo">VS</div>
      <div style="display:flex;flex-direction:column;line-height:1">
        <div style="font-weight:700">Vishwas Saini</div>
        <div style="font-size:12px;color:var(--muted)">Python Web Developer</div>
      </div>
    </a>

    <nav class="nav">
      <a href="#projects">Projects</a>
      <a href="#skills">Skills</a>
      <a href="#contact">Contact</a>
      <a class="iconlink" href="https://vishwassaini.itch.io/" target="_blank" rel="noopener">
        <!-- itch icon simple -->
        <svg width="18" height="18" viewBox="0 0 24 24" fill="none"><path d="M4 7h16M4 13h16M4 19h16" stroke="currentColor" stroke-width="1.6" stroke-linecap="round"/></svg>
        <span style="font-size:13px;color:var(--muted)">Itch</span>
      </a>
      <a class="iconlink" href="https://www.reddit.com/user/FeelingBullfrog5749/" target="_blank" rel="noopener">
        <svg width="18" height="18" viewBox="0 0 24 24" fill="none"><path d="M6 12a6 6 0 0012 0" stroke="currentColor" stroke-width="1.4" stroke-linecap="round"/></svg>
        <span style="font-size:13px;color:var(--muted)">Reddit</span>
      </a>
      <button class="smallbtn" onclick="toggleTheme()">Theme</button>
    </nav>
  </div>
</header>

<!-- Cinematic Hero -->
<section class="hero" id="top">
  <div class="hero-inner">
    <div class="hero-content">
      <h1>Hi, I’m <span class="accent">Vishwas Saini</span></h1>
      <p>I build modern, scalable web applications using Python, Flask, PostgreSQL, and AI integrations. I focus on clean architecture, responsive design, smooth user experiences, and delivering high-quality solutions with minimal operational cost.</p>

      <div class="hero-cta">
        <a class="btn" href="#projects">View Projects</a>
        <a class="btn" href="https://vishwassaini.itch.io/" target="_blank" style="background:transparent;border:1px solid var(--glass-border;color:var(--text)">Visit Itch</a>
      </div>

      <div class="feature" style="margin-top:18px">
        <div style="display:flex;align-items:center;gap:12px">
          <div style="width:56px;height:56px;border-radius:10px;overflow:hidden;flex-shrink:0">
            <img src="screenshots/clinic-management-website/screenshot6.png" style="width:100%;height:100%;object-fit:cover" alt="Clinic screenshot">
          </div>
          <div>
            <div style="font-weight:700">Clinic Management System</div>
            <div class="muted" style="font-size:13px">Full clinic management, appointments, records, email & AI features</div>
          </div>
        </div>
      </div>
    </div>

    <div class="hero-shot" aria-hidden="true">
      <!-- cinematic background comes from the screenshot -->
      <img src="screenshots/clinic-management-website/screenshot6.png" alt="Clinic management screenshot hero">
    </div>
  </div>
</section>

<!-- Projects -->
<section id="projects" class="section">
  <div style="display:flex;align-items:center;justify-content:space-between;gap:12px;flex-wrap:wrap">
    <div>
      <h2 style="margin-bottom:6px">Featured Projects</h2>
      <div class="muted">Selected work — web apps, admin tools, and AI integrations</div>
    </div>
  </div>

  <div style="height:18px"></div>
  <div class="filters" role="toolbar" aria-label="Project filters">
    <button class="filter-btn active" onclick="filter('all', this)">All</button>
    <button class="filter-btn" onclick="filter('web', this)">Web</button>
    <button class="filter-btn" onclick="filter('ai', this)">AI</button>
  </div>

  <div class="cards" role="list" aria-label="Project list">
    <!-- single featured card (you can duplicate for more projects) -->
    <article class="card" role="listitem" data-tags="web ai">
      <div class="card-inner">
        <div class="card-thumb">
          <img src="screenshots/clinic-management-website/screenshot6.png" alt="Clinic Management screenshot" onclick="openModal(this)" loading="lazy">
        </div>
        <h3 style="margin-bottom:6px">Clinic Management Website</h3>
        <p class="muted" style="margin-bottom:10px">A full-featured Clinic Management System designed to help doctors efficiently manage patient information, appointments, records and communications. Integrated with secure authentication, email automation (Brevo), and AI-assisted features for insights and workflow improvements.</p>

        <div style="display:flex;gap:10px;align-items:center;flex-wrap:wrap">
          <a class="btn" href="https://clinic-management-website.onrender.com/" target="_blank">Live Demo</a>
          <button class="filter-btn" onclick="window.open('https://vishwassaini.itch.io/','_blank')">Buy / Download</button>
          <div style="margin-left:auto" class="muted">Tech: Python • Flask • Neon PG • Brevo • Gemini • Mistral</div>
        </div>
      </div>
    </article>
  </div>
</section>

<!-- Skills -->
<section id="skills" class="section center">
  <h2>Skills & Tools</h2>
  <div class="muted" style="margin-top:8px">Technologies I use every day</div>
  <div class="skills" style="justify-content:center;margin-top:14px">
    <span class="skill-pill">Python</span>
    <span class="skill-pill">Flask</span>
    <span class="skill-pill">PostgreSQL</span>
    <span class="skill-pill">HTML & CSS</span>
    <span class="skill-pill">JavaScript</span>
    <span class="skill-pill">Bootstrap</span>
    <span class="skill-pill">Gemini AI</span>
    <span class="skill-pill">Mistral AI</span>
    <span class="skill-pill">Render</span>
    <span class="skill-pill">Brevo (Email)</span>
  </div>
</section>

<!-- Contact -->
<section id="contact" class="section center">
  <h2>Contact</h2>
  <p class="muted" style="max-width:760px;margin:auto">For project inquiries, custom development, or deployment & hosting packages, email me or message via Reddit / itch.io.</p>
  <div style="margin-top:16px">
    <a class="btn" href="mailto:vissaini744@gmail.com">Email: vissaini744@gmail.com</a>
  </div>

  <div class="socials" style="margin-top:18px">
    <a class="iconlink" href="https://vishwassaini.itch.io/" target="_blank" rel="noopener noreferrer">Itch.io • vishwassaini</a>
    <a class="iconlink" href="https://www.reddit.com/user/FeelingBullfrog5749/" target="_blank" rel="noopener noreferrer">Reddit • FeelingBullfrog5749</a>
  </div>
</section>

<!-- Modal viewer -->
<div id="modal" role="dialog" aria-hidden="true" onclick="closeModal(event)">
  <img id="modal-img" alt="Expanded screenshot">
</div>

<!-- Footer -->
<footer class="footer">
  <div>© 2026 Vishwas Saini — Python Web Developer</div>
  <div class="muted" style="margin-top:6px">Portfolio • Clinic Management Website • Render & Neon Deployment</div>
</footer>

<script>
/* ---------------------------
   Helpers & initial state
   --------------------------- */
const cursor = document.getElementById('cursor');
const prefersTouch = 'ontouchstart' in window || navigator.maxTouchPoints > 0;
if(prefersTouch){ document.body.classList.add('hide-cursor'); cursor.style.display='none'; }

/* Magnetic cursor follow */
if(!prefersTouch){
  window.addEventListener('mousemove', (e) => {
    cursor.style.left = e.clientX + 'px';
    cursor.style.top  = e.clientY + 'px';
  });
}

/* Magnetic buttons (pull effect) */
document.querySelectorAll('.btn, .filter-btn, .smallbtn, .iconlink').forEach(el=>{
  el.addEventListener('mousemove', (ev)=>{
    const r = el.getBoundingClientRect();
    const dx = (ev.clientX - (r.left + r.width/2))/8;
    const dy = (ev.clientY - (r.top + r.height/2))/8;
    el.style.transform = `translate(${dx}px, ${dy}px)`;
    cursor.style.transform = `translate(${ev.clientX - 6}px, ${ev.clientY - 6}px) scale(1.9)`;
  });
  el.addEventListener('mouseleave', ()=>{ el.style.transform=''; cursor.style.transform='translate(-50%,-50%) scale(1)'; });
});

/* Parallax blobs on scroll */
window.addEventListener('scroll', () => {
  const y = window.scrollY;
  document.querySelectorAll('.parallax span').forEach((el,i)=>{
    el.style.transform = `translateY(${y * (0.06 + i*0.02)}px)`;
  });
});

/* Smooth reveal animations (GSAP-like but tiny) */
const sections = document.querySelectorAll('section');
const io = new IntersectionObserver(entries => {
  entries.forEach(entry => {
    if(entry.isIntersecting){
      entry.target.classList.add('show');
    }
  });
},{threshold:0.18});
sections.forEach(s => io.observe(s));

/* Modal viewer for gallery images */
function openModal(imgEl){ 
  const modal = document.getElementById('modal');
  const mimg = document.getElementById('modal-img');
  mimg.src = imgEl.src;
  modal.style.display = 'flex';
  modal.setAttribute('aria-hidden','false');
}
function closeModal(e){
  if(e.target.id === 'modal' || e.target.id === 'modal-img') {
    document.getElementById('modal').style.display='none';
    document.getElementById('modal').setAttribute('aria-hidden','true');
  } else if(e.type === 'keydown' && e.key === 'Escape'){
    document.getElementById('modal').style.display='none';
    document.getElementById('modal').setAttribute('aria-hidden','true');
  }
}
document.addEventListener('keydown', closeModal);

/* Filter projects (simple) */
function filter(tag, btn){
  document.querySelectorAll('.filter-btn').forEach(b=>b.classList.remove('active'));
  if(btn) btn.classList.add('active');
  document.querySelectorAll('.card').forEach(card=>{
    const tags = card.getAttribute('data-tags') || '';
    if(tag === 'all') card.style.display = '';
    else card.style.display = tags.includes(tag) ? '' : 'none';
  });
}

/* Theme toggle (light/dark) */
function toggleTheme(){
  document.body.classList.toggle('light');
}

/* Mobile menu toggle - simple */
function menuToggle(){
  const nav = document.querySelector('.nav');
  nav.classList.toggle('open');
}

/* improve accessibility: focus outlines for keyboard users */
document.addEventListener('keydown', (e)=>{
  if(e.key === 'Tab') document.body.classList.add('show-focus');
});
</script>

</body>
</html>
