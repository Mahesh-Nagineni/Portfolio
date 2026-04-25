<!DOCTYPE html>

<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Mahesh Nagineni | Portfolio</title>

<style>
*{margin:0;padding:0;box-sizing:border-box}

body{
    font-family:'Segoe UI',sans-serif;
    background:#0f172a;
    color:white;
    scroll-behavior:smooth;
}
.profile-pic{
    width:150px;
    height:150px;
    border-radius:50%;
    object-fit:cover;
    display:block;
    margin:0 auto 20px;
    
    border:3px solid #38bdf8;

    /* glow effect */
    box-shadow:0 0 15px #38bdf8;

    /* smooth hover effect */
    transition:0.3s;
}

.profile-pic:hover{
    transform:scale(1.05);
    box-shadow:0 0 25px #38bdf8;
}
/* NAVBAR */
nav{
    position:fixed;
    width:100%;
    top:0;
    background:#020617;
    padding:10px;
    display:flex;
    justify-content:center;
    gap:15px;
    z-index:1000;
}

nav a{
    color:#38bdf8;
    text-decoration:none;
    padding:6px 10px;
    border:2px solid transparent;
    border-radius:8px;
    transition:0.3s;
}

/* CLICK + ACTIVE BORDER EFFECT */
nav a.active{
    border:2px solid #38bdf8;
    background:rgba(56,189,248,0.15);
    color:white;
}

/* HEADER */
header{
    text-align:center;
    padding:120px 20px 60px;
}

#typing{
    color:#38bdf8;
    font-size:20px;
}

/* SECTION */
section{
    max-width:900px;
    margin:auto;
    padding:50px 20px;
}

h2{
    border-left:4px solid #38bdf8;
    padding-left:10px;
}

/* CARD */
.card{
    background:#1e293b;
    padding:20px;
    margin-top:15px;
    border-radius:10px;
    transition:0.3s;
    cursor:pointer;
}

.card:hover{
    transform:translateY(-5px);
}

/* SKILLS */
.bar{height:8px;background:#334155;border-radius:10px}
.fill{height:100%;width:0;background:#38bdf8;border-radius:10px}

/* MODAL */
#modal{
    display:none;
    position:fixed;
    top:0;left:0;
    width:100%;height:100%;
    background:rgba(0,0,0,0.8);
    justify-content:center;
    align-items:center;
}

#modalBox{
    background:#1e293b;
    padding:25px;
    border-radius:10px;
    max-width:500px;
}

/* BUTTON */
button{
    margin-top:10px;
    padding:8px 15px;
    cursor:pointer;
}
.highlight {
    animation: glow 1s ease;
}

@keyframes glow {
    0% {
        box-shadow: 0 0 0px #38bdf8;
    }
    50% {
        box-shadow: 0 0 25px #38bdf8;
    }
    100% {
        box-shadow: 0 0 0px #38bdf8;
    }
}
</style>

</head>

<body>

<nav>
<a href="#about">About</a>
<a href="#skills">Skills</a>
<a href="#projects">Projects</a>
<a href="#internship">Internship</a>
<a href="#certifications">Certifications</a>
<a href="#languages">Languages</a>
<a href="#contact">Contact</a>
</nav>

<header>
 <img src="/Meee.jpg" alt="Mahesh" class="profile-pic">
<h1>Mahesh Nagineni</h1>
<div id="typing"></div>
<p>Nellore, Andhra Pradesh</p>
</header>

<section id="about">
<h2>About</h2>
<div class="card">
Motivated Computer Science fresher with strong Java, SQL, and ML basics. Passionate about building real-world applications.
</div>
</section>

<section id="skills">
<h2>Skills</h2>
<div class="card">
Java<div class="bar"><div class="fill" data-width="90%"></div></div>
JavaScript<div class="bar"><div class="fill" data-width="80%"></div></div>
MySQL<div class="bar"><div class="fill" data-width="85%"></div></div>
HTML/CSS<div class="bar"><div class="fill" data-width="85%"></div></div>
</div>
</section>

<section id="projects">
<h2>Projects</h2>

<div class="card" onclick="openModal('sentiment')">
<h3>Sentiment Analysis</h3>
<p>Click for details</p>
</div>

<div class="card" onclick="openModal('employee')">
<h3>Employee Management System</h3>
<p>Click for details</p>
</div>

<div class="card" onclick="openModal('cart')">
<h3>Shopping Cart</h3>
<p>Click for details</p>
</div>

</section>

<section id="internship">
<h2>Internship</h2>
<div class="card">
<b>Brian O Vision (Dec 2024 – Apr 2025)</b>
<ul>
<li>Worked on machine learning project</li>
<li>Developed Java programs using OOP concepts</li>
<li>Learned data structures and file handling</li>
</ul>
</div>
</section>

<section id="certifications">
<h2>Certifications</h2>
<div class="card">
<ul>
<li>NPTEL – Cloud Computing</li>
<li>EdX – Communication Skills and Teamwork</li>
</ul>
</div>
</section>

<section id="languages">
<h2>Languages Known</h2>
<div class="card">Telugu, English</div>
</section>

<section id="contact">
<h2>Contact</h2>
<div class="card">
📞 8978067036<br>
📧 maheshnagineni74@gmail.com<br>
🔗 github.com/Mahesh-Nagineni
</div>
</section>

<!-- MODAL -->

<div id="modal">
<div id="modalBox">
<h3 id="title"></h3>
<p id="content"></p>
<button onclick="closeModal()">Close</button>
</div>
</div>

<script>

/* NAV ACTIVE HIGHLIGHT */
const links=document.querySelectorAll("nav a");
const sections=document.querySelectorAll("section");

window.addEventListener("scroll",()=>{
 let current="";
 sections.forEach(sec=>{
  if(scrollY>=sec.offsetTop-120){
    current=sec.id;
  }
 });
/* SECTION CLICK HIGHLIGHT */
document.querySelectorAll("nav a").forEach(link => {
    link.addEventListener("click", function() {
        const targetId = this.getAttribute("href").substring(1);
        const section = document.getElementById(targetId);

        // remove existing highlight first
        section.classList.remove("highlight");

        // trigger again (important trick)
        void section.offsetWidth;

        section.classList.add("highlight");
    });
});
 links.forEach(link=>{
  link.classList.remove("active");
  if(link.getAttribute("href")==="#"+current){
    link.classList.add("active");
  }
 });
});

/* TYPING */
let text="Java Full Stack Developer";
let i=0;
(function type(){
 if(i<text.length){
  document.getElementById("typing").innerHTML+=text[i++];
  setTimeout(type,80);
 }
})();

/* SKILL ANIMATION */
window.addEventListener("scroll",()=>{
 document.querySelectorAll(".fill").forEach(f=>{
  if(f.getBoundingClientRect().top<window.innerHeight){
   f.style.width=f.dataset.width;
  }
 });
});

/* PROJECT MODAL */
function openModal(p){
 let t=document.getElementById("title");
 let c=document.getElementById("content");

 if(p==="sentiment"){
  t.innerText="Sentiment Analysis Project";
  c.innerHTML=`
  • NLP-based review classification<br>
  • Used TF-IDF feature extraction<br>
  • Text preprocessing techniques<br>
  • Implemented in Python with OOP<br>
  • Data handled using MySQL
  `;
 }

 if(p==="employee"){
  t.innerText="Employee Management System";
  c.innerHTML=`
  • CRUD operations system<br>
  • Built with Java, JDBC, MySQL<br>
  • OOP-based design<br>
  • Database integration<br>
  • User-friendly interface
  `;
 }

 if(p==="cart"){
  t.innerText="Shopping Cart";
  c.innerHTML=`
  • Dynamic cart using JavaScript<br>
  • Add/remove items functionality<br>
  • Price calculation<br>
  • Interactive UI design
  `;
 }

 document.getElementById("modal").style.display="flex";
}

function closeModal(){
 document.getElementById("modal").style.display="none";
}

</script>

</body>
</html>
