<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Shivam Swaraj · full‑stack universe</title>
  <!-- Font Awesome 6 (free) -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
  <!-- Google Fonts: Inter + Fira Code for that dev vibe -->
  <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,400;14..32,600;14..32,800&family=Fira+Code:wght@400;500&display=swap" rel="stylesheet">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      background: #0a0c10;
      color: #e2e8f0;
      font-family: 'Inter', sans-serif;
      line-height: 1.6;
      scroll-behavior: smooth;
      overflow-x: hidden;
    }

    /* animated gradient orbs */
    .bg-orb {
      position: fixed;
      width: 70vmax;
      height: 70vmax;
      background: radial-gradient(circle at 30% 50%, rgba(0, 180, 255, 0.15) 0%, transparent 60%);
      border-radius: 50%;
      filter: blur(90px);
      z-index: -2;
      animation: floatOrb 25s infinite alternate ease-in-out;
    }
    .orb2 {
      width: 80vmax;
      height: 80vmax;
      background: radial-gradient(circle at 70% 80%, rgba(155, 93, 229, 0.12) 0%, transparent 70%);
      bottom: 0;
      right: 0;
      animation: floatOrb2 30s infinite alternate;
    }
    @keyframes floatOrb {
      0% { transform: translate(-10%, -10%) scale(1); opacity: 0.4; }
      100% { transform: translate(15%, 20%) scale(1.3); opacity: 0.8; }
    }
    @keyframes floatOrb2 {
      0% { transform: translate(5%, 5%) scale(1); }
      100% { transform: translate(-20%, -15%) scale(1.4); }
    }

    .container {
      max-width: 1300px;
      margin: 0 auto;
      padding: 2rem 2rem 3rem;
      position: relative;
      z-index: 10;
    }

    /* ===== GLASS CARD ===== */
    .glass {
      background: rgba(18, 22, 30, 0.7);
      backdrop-filter: blur(12px);
      -webkit-backdrop-filter: blur(12px);
      border: 1px solid rgba(80, 140, 255, 0.15);
      border-radius: 2.5rem;
      box-shadow: 0 30px 50px -20px rgba(0,0,0,0.8), 0 0 0 1px rgba(0, 255, 255, 0.05) inset;
    }

    /* ===== HEADER / TITLE ===== */
    .name-title {
      text-align: center;
      margin-bottom: 2.5rem;
    }
    .glitch-wrapper {
      font-size: clamp(2.8rem, 10vw, 5rem);
      font-weight: 800;
      letter-spacing: 6px;
      text-transform: uppercase;
      color: #b3f0ff;
      text-shadow: 0 0 8px #00e0ff, 0 0 20px #0044ff;
      animation: glitch 3s infinite;
    }
    @keyframes glitch {
      0%, 100% { transform: skew(0deg, 0deg); opacity: 1; text-shadow: 2px 0 #ff0080, -2px 0 #00ffff; }
      95% { transform: skew(2deg, 0.5deg); opacity: 0.9; text-shadow: -3px 1px #ff0080, 3px -1px #00ffff; }
      96% { transform: skew(-2deg, -0.8deg); }
      97% { transform: skew(0deg, 0deg); }
    }
    .subhead {
      font-size: 1.6rem;
      background: linear-gradient(135deg, #a5f0ff, #c57cff);
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
      font-weight: 600;
      margin-top: -0.2rem;
      filter: drop-shadow(0 0 10px #3a86ff);
    }

    /* TYPING SVG replaced with inline animated element */
    .typing-wrapper {
      min-height: 4rem;
      display: flex;
      justify-content: center;
      align-items: center;
      font-size: 1.7rem;
      font-family: 'Fira Code', monospace;
      margin: 1rem 0 1.5rem;
    }
    .typed-text {
      border-right: 3px solid #0ff;
      padding-right: 8px;
      animation: blinkCursor 1s step-end infinite;
      background: linear-gradient(145deg, #fff, #b0f0ff);
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
      font-weight: 500;
    }
    @keyframes blinkCursor {
      0%, 100% { border-color: #0ff; }
      50% { border-color: transparent; }
    }

    /* floating badges */
    .badge-cloud {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 1rem 1.3rem;
      margin: 2.2rem 0;
    }
    .tech-badge {
      background: rgba(0, 255, 255, 0.05);
      border: 1px solid rgba(0, 255, 255, 0.3);
      border-radius: 60px;
      padding: 0.5rem 1.5rem;
      font-weight: 500;
      backdrop-filter: blur(5px);
      box-shadow: 0 5px 15px rgba(0,200,255,0.2);
      transition: 0.2s;
      animation: floatBadge 4s infinite alternate;
    }
    .tech-badge:hover {
      background: #00e0ff20;
      border-color: cyan;
      box-shadow: 0 0 20px cyan;
      transform: scale(1.08);
    }
    @keyframes floatBadge {
      0% { transform: translateY(0px); }
      100% { transform: translateY(-6px); }
    }

    /* project cards */
    .project-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
      gap: 2rem;
      margin: 3rem 0;
    }
    .project-card {
      background: rgba(12, 18, 28, 0.7);
      backdrop-filter: blur(8px);
      border: 1px solid #2d374d;
      border-radius: 2rem;
      padding: 2rem 1.8rem;
      transition: all 0.25s;
      box-shadow: 0 15px 30px -15px #000;
      position: relative;
      overflow: hidden;
    }
    .project-card::after {
      content: '';
      position: absolute;
      inset: 0;
      border-radius: inherit;
      padding: 2px;
      background: linear-gradient(145deg, cyan, #ff66c0, #4d9eff);
      -webkit-mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
      mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
      -webkit-mask-composite: xor;
      mask-composite: exclude;
      pointer-events: none;
      opacity: 0;
      transition: opacity 0.4s;
    }
    .project-card:hover::after {
      opacity: 1;
    }
    .project-card:hover {
      transform: translateY(-10px) scale(1.02);
      border-color: transparent;
    }
    .project-icon {
      font-size: 2.5rem;
      margin-bottom: 1.5rem;
      color: #4df0ff;
      filter: drop-shadow(0 0 8px cyan);
    }
    .project-title {
      font-size: 1.9rem;
      font-weight: 700;
      background: linear-gradient(to right, #fff, #b2f0ff);
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
      margin-bottom: 0.8rem;
    }
    .project-links {
      margin-top: 1.7rem;
      display: flex;
      gap: 2rem;
      font-size: 1.1rem;
    }
    .project-links a {
      color: #b0e0ff;
      text-decoration: none;
      border-bottom: 1px dotted cyan;
      transition: 0.2s;
      display: inline-flex;
      align-items: center;
      gap: 6px;
    }
    .project-links a:hover {
      color: white;
      border-bottom: 1px solid white;
      text-shadow: 0 0 8px white;
    }

    /* GitHub stats with hover glow */
    .stats-wrapper {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 2rem;
      margin: 3rem 0 2rem;
    }
    .stat-item {
      background: #0f172a80;
      border-radius: 2rem;
      padding: 1.5rem 1.8rem;
      border: 1px solid #2c3c5e;
      backdrop-filter: blur(4px);
      transition: all 0.3s;
    }
    .stat-item:hover {
      border-color: #0ff;
      box-shadow: 0 0 30px #0ff3;
    }

    /* contribution graph area */
    .graph-embed {
      background: #0b1018;
      border-radius: 2rem;
      padding: 1.5rem;
      margin: 2.5rem 0;
      border: 1px solid cyan;
      box-shadow: 0 0 30px #00f7ff20;
      text-align: center;
    }
    .graph-placeholder {
      display: flex;
      align-items: flex-end;
      justify-content: center;
      gap: 5px;
      height: 140px;
    }
    .graph-bar {
      width: 18px;
      background: linear-gradient(to top, cyan, #4d79ff);
      border-radius: 10px 10px 4px 4px;
      animation: barGlow 2s infinite alternate;
      box-shadow: 0 -5px 15px cyan;
    }
    @keyframes barGlow {
      0% { opacity: 0.6; height: 20px; }
      100% { opacity: 1; height: 90px; }
    }
    /* many bars with different heights (simulate activity) */
    .bar1 { height: 40px; animation-delay: 0s; }
    .bar2 { height: 85px; animation-delay: 0.2s; }
    .bar3 { height: 62px; animation-delay: 0.4s; }
    .bar4 { height: 30px; animation-delay: 0.1s; }
    .bar5 { height: 95px; animation-delay: 0.5s; }
    .bar6 { height: 70px; animation-delay: 0.3s; }
    .bar7 { height: 48px; animation-delay: 0.6s; }
    .bar8 { height: 80px; animation-delay: 0.7s; }
    .bar9 { height: 55px; animation-delay: 0.25s; }
    .bar10 { height: 100px; animation-delay: 0.45s; }

    .quote {
      text-align: center;
      font-size: 1.6rem;
      font-weight: 300;
      font-style: italic;
      border-left: 4px solid #0ff;
      padding-left: 2rem;
      margin: 3rem 0 1rem;
      color: #ccd6f0;
      text-shadow: 0 0 5px cyan;
    }

    /* contact row */
    .contact-links {
      display: flex;
      justify-content: center;
      flex-wrap: wrap;
      gap: 3rem;
      margin: 2rem 0 0;
    }
    .contact-icon {
      font-size: 2.2rem;
      background: #15202b;
      width: 70px;
      height: 70px;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      border: 1px solid #0ff;
      transition: 0.2s;
      box-shadow: 0 0 15px #0ff5;
      color: #0ff;
      text-decoration: none;
    }
    .contact-icon:hover {
      transform: scale(1.2) rotate(5deg);
      background: #0ff1;
      box-shadow: 0 0 40px cyan;
      color: white;
    }

    hr {
      border: 0.5px solid #1f3348;
      margin: 2.5rem 0;
    }

    /* about me section with floating elements */
    .about-grid {
      display: flex;
      flex-wrap: wrap;
      gap: 2rem;
      margin: 2rem 0;
    }
    .about-text {
      flex: 2;
      min-width: 280px;
      background: rgba(0, 15, 25, 0.4);
      backdrop-filter: blur(4px);
      padding: 2rem;
      border-radius: 2.5rem;
      border: 1px solid #3d5a80;
    }
    .about-text p i {
      color: #0ff;
      width: 28px;
    }
    .skill-tag {
      display: inline-block;
      background: #0b1b2f;
      border: 1px solid cyan;
      border-radius: 40px;
      padding: 0.3rem 1.2rem;
      margin: 0.3rem;
      font-size: 0.9rem;
      font-family: 'Fira Code', monospace;
    }
  </style>
</head>
<body>
  <div class="bg-orb"></div>
  <div class="bg-orb orb2"></div>

  <div class="container">
    <!-- header with glitch -->
    <div class="name-title">
      <div class="glitch-wrapper">SHIVAM SWARAJ</div>
      <div class="subhead">⚡ full stack · ai · cloud ⚡</div>
    </div>

    <!-- typing animation (inline) -->
    <div class="typing-wrapper">
      <span class="typed-text" id="typed"></span>
    </div>

    <!-- badges / tech stack animated -->
    <div class="badge-cloud">
      <span class="tech-badge"><i class="fa-brands fa-react"></i> React</span>
      <span class="tech-badge"><i class="fa-brands fa-node"></i> Node.js</span>
      <span class="tech-badge"><i class="fa-solid fa-database"></i> MongoDB</span>
      <span class="tech-badge"><i class="fa-solid fa-database"></i> MySQL</span>
      <span class="tech-badge"><i class="fa-brands fa-python"></i> Python</span>
      <span class="tech-badge"><i class="fa-solid fa-code"></i> C++</span>
      <span class="tech-badge"><i class="fa-brands fa-js"></i> JavaScript</span>
      <span class="tech-badge"><i class="fa-brands fa-linux"></i> Linux</span>
      <span class="tech-badge"><i class="fa-brands fa-php"></i> PHP</span>
      <span class="tech-badge"><i class="fa-brands fa-tailwind"></i> Tailwind</span>
    </div>

    <!-- about me + extra info (compact) -->
    <div class="about-grid">
      <div class="about-text glass">
        <p style="font-size: 1.8rem; margin-bottom: 1rem;">👨‍💻 <span style="background: linear-gradient(145deg,#0ff,#a975ff); -webkit-background-clip:text; background-clip:text; color:transparent;">About me</span></p>
        <p><i class="fa-solid fa-graduation-cap"></i> BTech CSE @ LPU · <i class="fa-solid fa-microchip"></i> Diploma Mechatronics (ToolRoom Patna)</p>
        <p><i class="fa-solid fa-location-dot" style="color:#0ff;"></i> Patna, Bihar · India</p>
        <p><i class="fa-regular fa-compass"></i> Passion: AI & full‑stack · future software engineer</p>
        <p><i classfa-regular fa-cricket></i> <i class="fa-solid fa-gamepad"></i> Cricket · gaming</p>
        <div style="margin-top: 1.5rem;">
          <span class="skill-tag">#React</span>
          <span class="skill-tag">#Node</span>
          <span class="skill-tag">#MongoDB</span>
          <span class="skill-tag">#AI</span>
          <span class="skill-tag">#Tailwind</span>
        </div>
      </div>
      <!-- you can add a mini fun fact or image, but keep it clean -->
    </div>

    <!-- Featured projects -->
    <h2 style="font-size: 2.5rem; margin: 3rem 0 1rem; display: flex; gap: 15px; align-items: center;">
      <i class="fa-solid fa-cubes" style="color:#0ff;"></i> 
      <span style="background: linear-gradient(to right, #b2f0ff, white); -webkit-background-clip: text; background-clip: text; color: transparent;">featured builds</span>
    </h2>
    <div class="project-grid">
      <!-- FitNation card -->
      <div class="project-card">
        <div class="project-icon"><i class="fa-solid fa-heart-pulse"></i></div>
        <div class="project-title">FitNation</div>
        <p style="color: #b0c8e5;">Health & fitness with Google Fit API, streaks, anti‑cheat & BMI analytics.</p>
        <div class="project-links">
          <a href="https://fitnationproject.vercel.app/" target="_blank"><i class="fa-solid fa-up-right-from-screen"></i> Live</a>
          <a href="https://github.com/shiv578/Fitnationproject" target="_blank"><i class="fa-brands fa-github"></i> Repo</a>
        </div>
      </div>
      <!-- Property Management -->
      <div class="project-card">
        <div class="project-icon"><i class="fa-solid fa-building"></i></div>
        <div class="project-title">Property Management</div>
        <p style="color: #b0c8e5;">Full‑stack listing, auth, search & filters – PHP, MySQL, Tailwind.</p>
        <div class="project-links">
          <a href="https://github.com/shiv578/Property-Management" target="_blank"><i class="fa-brands fa-github"></i> GitHub</a>
        </div>
      </div>
      <!-- maybe a third card with future project / idea -->
      <div class="project-card">
        <div class="project-icon"><i class="fa-solid fa-brain"></i></div>
        <div class="project-title">AI playground</div>
        <p style="color: #b0c8e5;">Upcoming: AI integrations, cloud-based tools & smart dashboards.</p>
        <div class="project-links">
          <a href="#"><i class="fa-regular fa-star"></i> in progress</a>
        </div>
      </div>
    </div>

    <!-- GitHub stats with custom style (static but shiny) -->
    <div class="stats-wrapper">
      <div class="stat-item">
        <img src="https://github-readme-stats.vercel.app/api?username=shiv578&show_icons=true&theme=tokyonight&bg_color=0a0c10&border_color=00ffff&hide_border=false" alt="github stats" style="border-radius: 18px;">
      </div>
      <div class="stat-item">
        <img src="https://streak-stats.demolab.com/?user=shiv578&theme=tokyonight&border=00ffff&background=0a0c10" alt="streak" style="border-radius: 18px;">
      </div>
    </div>

    <!-- Contribution graph (animated custom) -->
    <div class="graph-embed">
      <p style="font-size: 1.8rem; margin-bottom: 1rem;"><i class="fa-regular fa-calendar"></i> contribution activity (live simulation)</p>
      <div class="graph-placeholder">
        <div class="graph-bar bar1"></div>
        <div class="graph-bar bar2"></div>
        <div class="graph-bar bar3"></div>
        <div class="graph-bar bar4"></div>
        <div class="graph-bar bar5"></div>
        <div class="graph-bar bar6"></div>
        <div class="graph-bar bar7"></div>
        <div class="graph-bar bar8"></div>
        <div class="graph-bar bar9"></div>
        <div class="graph-bar bar10"></div>
        <div class="graph-bar bar2"></div>
        <div class="graph-bar bar5"></div>
        <div class="graph-bar bar7"></div>
      </div>
      <p style="margin-top: 1rem; opacity: 0.7;">(real graph: <i class="fa-brands fa-github"></i> shiv578 · 500+ contributions)</p>
    </div>

    <!-- quote -->
    <div class="quote">
      “Good systems scale. Great systems scale reliably.”
    </div>

    <!-- contact & footer -->
    <div class="contact-links">
      <a href="mailto:swarajrkfl22@gmail.com" class="contact-icon"><i class="fa-regular fa-envelope"></i></a>
      <a href="https://www.linkedin.com/in/shivam-swaraj72" target="_blank" class="contact-icon"><i class="fa-brands fa-linkedin-in"></i></a>
      <a href="https://github.com/shiv578" target="_blank" class="contact-icon"><i class="fa-brands fa-github"></i></a>
      <span class="contact-icon" style="cursor: default; background: #0a1420;"><i class="fa-regular fa-map"></i></span>
    </div>
    <p style="text-align: center; margin-top: 1.2rem; color: #7f92b0;">
      <i class="fa-regular fa-copyright"></i> shivam swaraj · 2025 · full‑stack alchemy
    </p>

    <!-- hidden typing strings -->
  </div>

  <script>
    (function() {
      // professional typing effect (replaces svg)
      const words = [
        "Full Stack Developer",
        "React · Node · MongoDB",
        "AI & Cloud Learner",
        "Future Software Engineer",
        "FitNation creator"
      ];
      let i = 0;
      let j = 0;
      let currentWord = "";
      let isDeleting = false;
      const typedSpan = document.getElementById("typed");

      function typeEffect() {
        if (i < words.length) {
          if (!isDeleting && j <= words[i].length) {
            currentWord = words[i].substring(0, j);
            typedSpan.textContent = currentWord;
            j++;
            setTimeout(typeEffect, 100);
          } else if (isDeleting && j >= 0) {
            currentWord = words[i].substring(0, j);
            typedSpan.textContent = currentWord;
            j--;
            setTimeout(typeEffect, 50);
          } else {
            if (!isDeleting && j > words[i].length) {
              isDeleting = true;
              setTimeout(typeEffect, 1500); // pause before delete
            } else if (isDeleting && j < 0) {
              isDeleting = false;
              i = (i + 1) % words.length;
              j = 0;
              setTimeout(typeEffect, 200);
            } else {
              setTimeout(typeEffect, 50);
            }
          }
        }
      }
      typeEffect();

      // make graph bars animate randomly different heights (already set, fine)
    })();
  </script>

  <!-- subtle hover extras -->
  <style>
    /* make stat images responsive */
    @media (max-width: 600px) {
      .stat-item img { width: 100%; height: auto; }
      .container { padding: 1rem; }
    }
    /* animated glow on project icons */
    .project-card:hover .project-icon {
      animation: iconGlow 0.8s infinite alternate;
    }
    @keyframes iconGlow {
      from { filter: drop-shadow(0 0 5px cyan); }
      to { filter: drop-shadow(0 0 20px magenta); }
    }
    /* remove default underline from links */
    a { text-decoration: none; }
  </style>
</body>
</html>
