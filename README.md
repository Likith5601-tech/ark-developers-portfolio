<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>ARK Developers | AI Portfolio</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>

  <!-- HERO SECTION -->
  <section class="hero">
    <h1>Hi, I’m <span class="ai-name">ARK Developers</span></h1>
    <h2 class="typing"></h2>
  </section>

  <!-- ABOUT -->
  <section class="section reveal">
    <h2>About Me</h2>
    <p>
      I am a beginner web developer from India creating clean,
      responsive and AI-inspired websites using HTML and CSS.
    </p>
  </section>

  <!-- SKILLS -->
  <section class="section reveal">
    <h2>Skills</h2>
    <div class="skills">
      <div class="card">HTML5</div>
      <div class="card">CSS3</div>
      <div class="card">Responsive Design</div>
      <div class="card">AI Theme UI</div>
    </div>
  </section>

  <script src="script.js"></script>
</body>
</html>

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: Arial, Helvetica, sans-serif;
}

body {
  background: #000;
  color: #e0f7fa;
}

/* HERO */
.hero {
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.ai-name {
  color: #00ffcc;
  text-shadow: 0 0 15px #00ffcc;
}

.typing {
  margin-top: 10px;
  color: #00e5ff;
  border-right: 2px solid #00e5ff;
  padding-right: 5px;
}

/* SECTIONS */
.section {
  padding: 80px 10%;
  text-align: center;
}

.skills {
  display: flex;
  justify-content: center;
  gap: 20px;
  flex-wrap: wrap;
}

.card {
  padding: 20px 30px;
  border: 1px solid #00ffcc;
  box-shadow: 0 0 15px rgba(0, 255, 204, 0.4);
  border-radius: 10px;
}

/* SCROLL ANIMATION */
.reveal {
  opacity: 0;
  transform: translateY(50px);
  transition: all 1s ease;
}

.reveal.active {
  opacity: 1;
  transform: translateY(0);
}

const texts = [
  "AI-Inspired Web Developer",
  "HTML & CSS Freelancer",
  "Responsive Website Creator"
];

let textIndex = 0;
let charIndex = 0;
let deleting = false;

function typeEffect() {
  const currentText = texts[textIndex];
  const displayText = deleting
    ? currentText.substring(0, charIndex--)
    : currentText.substring(0, charIndex++);

  document.querySelector(".typing").textContent = displayText;

  if (!deleting && charIndex === currentText.length + 1) {
    deleting = true;
    setTimeout(typeEffect, 1200);
    return;
  }

  if (deleting && charIndex === 0) {
    deleting = false;
    textIndex = (textIndex + 1) % texts.length;
  }

  setTimeout(typeEffect, deleting ? 60 : 120);
}

typeEffect();

/* Scroll reveal */
window.addEventListener("scroll", () => {
  document.querySelectorAll(".reveal").forEach(section => {
    const top = section.getBoundingClientRect().top;
    if (top < window.innerHeight - 100) {
      section.classList.add("active");
    }
  });
});