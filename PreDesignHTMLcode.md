<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Vishwas Saini | Python Web Developer</title>

<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700&display=swap" rel="stylesheet">

<style>
html{scroll-behavior:smooth}
:root{
  --bg:#0b0f19;
  --card:rgba(255,255,255,0.08);
  --border:rgba(255,255,255,0.18);
  --text:#e6edf3;
  --accent:#00e5ff;
}
.light{
  --bg:#eef2f7;
  --card:rgba(255,255,255,0.75);
  --border:rgba(0,0,0,0.1);
  --text:#0f172a;
  --accent:#2563eb;
}
*{margin:0;padding:0;box-sizing:border-box}
body{
  font-family:Poppins,sans-serif;
  background:var(--bg);
  color:var(--text);
  overflow-x:hidden;
}

/* ===== PARALLAX BACKGROUND ===== */
.parallax{
  position:fixed;
  inset:0;
  z-index:-1;
  overflow:hidden;
}
.parallax span{
  position:absolute;
  width:340px;
  height:340px;
  background:radial-gradient(circle,var(--accent),transparent 70%);
  opacity:.12;
}
.parallax span:nth-child(1){top:10%;left:15%}
.parallax span:nth-child(2){top:60%;left:70%}
.parallax span:nth-child(3){top:30%;left:50%}

/* ===== MAGNETIC CURSOR ===== */
#cursor{
  position:fixed;
  width:18px;height:18px;
  background:var(--accent);
  border-radius:50%;
  pointer-events:none;
  transform:translate(-50%,-50%);
  z-index:5000;
  transition:.15s ease;
}

/* ===== HEADER ===== */
header{
  position:fixed;
  top:0;width:100%;
  backdrop-filter:blur(14px);
  background:rgba(0,0,0,.5);
  z-index:1000;
}
nav{
  max-width:1200px;
  margin:auto;
  padding:16px;
  display:flex;
  justify-content:space-between;
  align-items:center;
}
.nav-links{display:flex;gap:26px}
.menu-btn{display:none;font-size:26px;cursor:pointer}
.toggle{cursor:pointer}

/* ===== SECTIONS ===== */
section{
  max-width:1200px;
  margin:auto;
  padding:120px 20px;
  opacity:0;
  transform:translateY(60px) scale(.97);
  transition:1s cubic-bezier(.16,1,.3,1);
}
section.show{opacity:1;transform:none}

/* ===== HERO ===== */
.hero h1{font-size:52px}
.hero span{color:var(--accent)}
.hero p{max-width:760px;opacity:.85;margin-top:14px}

/* ===== BUTTON (MAGNETIC) ===== */
.btn{
  display:inline-block;
  padding:14px 34px;
  border-radius:40px;
  background:linear-gradient(135deg,var(--accent),#38bdf8);
  color:#000;
  font-weight:600;
  margin-top:30px;
  transition:.25s;
}

/* ===== FILTERS ===== */
.filters{display:flex;gap:14px;margin-bottom:30px}
.filter-btn{
  padding:10px 20px;
  border-radius:30px;
  border:none;
  cursor:pointer;
  background:var(--card);
  backdrop-filter:blur(14px);
  border:1px solid var(--border);
  color:var(--text);
}
.filter-btn.active{background:var(--accent);color:#000}

/* ===== PROJECT CARDS (GLASS + 3D) ===== */
.projects{
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(320px,1fr));
  gap:30px;
}
.project{
  background:var(--card);
  backdrop-filter:blur(20px);
  border:1px solid var(--border);
  border-radius:26px;
  padding:26px;
  transform-style:preserve-3d;
  transition:.4s cubic-bezier(.16,1,.3,1);
}
.project:hover{
  transform:rotateX(8deg) rotateY(-8deg) translateY(-12px);
  box-shadow:0 30px 80px rgba(0,0,0,.45);
}
.project.hide{
  opacity:0;
  transform:scale(.9);
  pointer-events:none;
}

/* ===== GALLERY ===== */
.gallery{
  display:grid;
  grid-template-columns:repeat(4,1fr);
  gap:10px;
  margin-top:16px;
}
.gallery img{
  width:100%;
  border-radius:12px;
  cursor:pointer;
  transition:.3s;
}
.gallery img:hover{transform:scale(1.08)}

/* ===== SKILLS ===== */
.skills{display:flex;flex-wrap:wrap;gap:14px}
.skill{
  padding:10px 18px;
  background:var(--card);
  backdrop-filter:blur(12px);
  border-radius:24px;
  border:1px solid var(--border);
}

/* ===== MODAL ===== */
#modal{
  position:fixed;
  inset:0;
  background:rgba(0,0,0,.85);
  display:none;
  justify-content:center;
  align-items:center;
  z-index:3000;
}
#modal img{max-width:92%;max-height:92%;border-radius:18px}

footer{text-align:center;padding:40px;opacity:.6}

/* ===== MOBILE ===== */
@media(max-width:768px){
  .nav-links{
    position:absolute;
    top:70px;left:0;right:0;
    background:var(--bg);
    flex-direction:column;
    display:none;
  }
  .nav-links.show{display:flex}
  .menu-btn{display:block}
  .hero h1{font-size:38px}
}
</style>
</head>

<body>

<div id="cursor"></div>
<div class="parallax"><span></span><span></span><span></span></div>

<header>
<nav>
  <strong>Vishwas Saini</strong>
  <div class="menu-btn" onclick="menu()">☰</div>
  <div class="nav-links" id="nav">
    <a href="#projects">Projects</a>
    <a href="#skills">Skills</a>
    <a href="#contact">Contact</a>
    <span class="toggle" onclick="theme()">🌙</span>
  </div>
</nav>
</header>

<section class="hero">
<h1>Hi, I’m <span>Vishwas Saini</span></h1>
<h2>Python Web Developer</h2>
<p>
I build modern, scalable web applications using Python, Flask, PostgreSQL, and AI integrations.
I focus on clean architecture, responsive design, smooth user experiences, and delivering
high-quality solutions with minimal operational cost.
</p>
<a class="btn" href="#projects">View My Work</a>
</section>

<section id="projects">
<h2>Projects</h2><br>

<div class="filters">
<button class="filter-btn active" onclick="filterProjects('all',this)">All</button>
<button class="filter-btn" onclick="filterProjects('web',this)">Web</button>
<button class="filter-btn" onclick="filterProjects('ai',this)">AI</button>
</div>

<div class="projects">
<div class="project web ai">
<h3>Clinic Management Website</h3>
<p>
A full-featured clinic management system enabling doctors to manage patient records,
appointments, communication, and AI-powered workflows efficiently.
</p>
<a class="btn" target="_blank" href="https://clinic-management-website.onrender.com/">Live Demo</a>

<div class="gallery">
<img src="screenshots/clinic-management-website/screenshot1.jpg" onclick="openModal(this)">
<img src="screenshots/clinic-management-website/screenshot2.jpg" onclick="openModal(this)">
<img src="screenshots/clinic-management-website/screenshot3.jpg" onclick="openModal(this)">
<img src="screenshots/clinic-management-website/screenshot4.jpg" onclick="openModal(this)">
</div>
</div>
</div>
</section>

<section id="skills">
<h2>Skills & Tools</h2><br>
<div class="skills">
<span class="skill">Python</span>
<span class="skill">Flask</span>
<span class="skill">PostgreSQL</span>
<span class="skill">HTML</span>
<span class="skill">CSS</span>
<span class="skill">JavaScript</span>
<span class="skill">Gemini AI</span>
<span class="skill">Mistral AI</span>
<span class="skill">Render</span>
<span class="skill">Email APIs</span>
</div>
</section>

<section id="contact">
<h2>Contact</h2><br>
<p>Email: <a href="mailto:vissaini744@gmail.com">vissaini744@gmail.com</a></p>
</section>

<footer>© 2026 Vishwas Saini</footer>

<div id="modal" onclick="closeModal()"><img id="modalImg"></div>

<script>
/* menu + theme */
function menu(){nav.classList.toggle("show")}
function theme(){document.body.classList.toggle("light")}

/* reveal */
const obs=new IntersectionObserver(e=>{
  e.forEach(x=>x.isIntersecting&&x.target.classList.add("show"))
},{threshold:.15})
document.querySelectorAll("section").forEach(s=>obs.observe(s))

/* modal */
function openModal(img){
  modal.style.display="flex"
  modalImg.src=img.src
}
function closeModal(){modal.style.display="none"}

/* filter */
function filterProjects(type,btn){
  document.querySelectorAll(".filter-btn").forEach(b=>b.classList.remove("active"))
  btn.classList.add("active")
  document.querySelectorAll(".project").forEach(p=>{
    p.classList.toggle("hide",type!=="all"&&!p.classList.contains(type))
  })
}

/* magnetic cursor + buttons */
const cursor=document.getElementById("cursor")
if(!("ontouchstart"in window)){
  document.addEventListener("mousemove",e=>{
    cursor.style.left=e.clientX+"px"
    cursor.style.top=e.clientY+"px"
  })
  document.querySelectorAll(".btn").forEach(btn=>{
    btn.addEventListener("mousemove",e=>{
      const r=btn.getBoundingClientRect()
      btn.style.transform=`translate(${(e.clientX-r.left-r.width/2)/6}px,${(e.clientY-r.top-r.height/2)/6}px)`
    })
    btn.addEventListener("mouseleave",()=>btn.style.transform="")
  })
}else cursor.style.display="none"

/* parallax */
window.addEventListener("scroll",()=>{
  document.querySelectorAll(".parallax span").forEach((el,i)=>{
    el.style.transform=`translateY(${scrollY*(0.15+i*0.07)}px)`
  })
})
</script>

</body>
</html>
