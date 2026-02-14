[portfolio.html](https://github.com/user-attachments/files/25310807/portfolio.html)
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Portfolio — Robotics Engineer</title>
  <link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;700;800&family=IBM+Plex+Mono:wght@300;400;500&display=swap" rel="stylesheet"/>
  <style>
    :root {
      --bg: #0a0c10;
      --surface: #111318;
      --border: #1e2230;
      --accent: #00e5ff;
      --accent2: #ff3d71;
      --text: #e8eaf0;
      --muted: #5a6080;
      --grid: #131820;
    }

    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    html { scroll-behavior: smooth; }

    body {
      background: var(--bg);
      color: var(--text);
      font-family: 'IBM Plex Mono', monospace;
      overflow-x: hidden;
    }

    /* ── GRID BACKGROUND ── */
    body::before {
      content: '';
      position: fixed;
      inset: 0;
      background-image:
        linear-gradient(rgba(0,229,255,0.03) 1px, transparent 1px),
        linear-gradient(90deg, rgba(0,229,255,0.03) 1px, transparent 1px);
      background-size: 40px 40px;
      pointer-events: none;
      z-index: 0;
    }

    /* ── CURSOR GLOW ── */
    #cursor-glow {
      position: fixed;
      width: 400px;
      height: 400px;
      border-radius: 50%;
      background: radial-gradient(circle, rgba(0,229,255,0.06) 0%, transparent 70%);
      pointer-events: none;
      transform: translate(-50%, -50%);
      transition: left 0.12s ease, top 0.12s ease;
      z-index: 1;
    }

    /* ── NAV ── */
    nav {
      position: fixed;
      top: 0; left: 0; right: 0;
      z-index: 100;
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 1.2rem 3rem;
      background: rgba(10,12,16,0.85);
      backdrop-filter: blur(14px);
      border-bottom: 1px solid var(--border);
    }

    .nav-logo {
      font-family: 'Syne', sans-serif;
      font-weight: 800;
      font-size: 1.1rem;
      color: var(--accent);
      letter-spacing: 0.04em;
    }

    .nav-links {
      display: flex;
      gap: 2.5rem;
      list-style: none;
    }

    .nav-links a {
      color: var(--muted);
      text-decoration: none;
      font-size: 0.78rem;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      transition: color 0.2s;
    }

    .nav-links a:hover { color: var(--accent); }

    /* ── HERO ── */
    .hero {
      position: relative;
      min-height: 100vh;
      display: flex;
      align-items: center;
      padding: 8rem 3rem 4rem;
      overflow: hidden;
      z-index: 2;
    }

    .hero-content { max-width: 700px; }

    .hero-tag {
      display: inline-flex;
      align-items: center;
      gap: 0.5rem;
      font-size: 0.72rem;
      letter-spacing: 0.2em;
      text-transform: uppercase;
      color: var(--accent);
      border: 1px solid rgba(0,229,255,0.3);
      padding: 0.35rem 0.9rem;
      border-radius: 2px;
      margin-bottom: 2rem;
      animation: fadeUp 0.6s ease both;
    }

    .hero-tag::before {
      content: '';
      width: 6px; height: 6px;
      background: var(--accent);
      border-radius: 50%;
      animation: pulse 2s infinite;
    }

    @keyframes pulse {
      0%, 100% { opacity: 1; }
      50% { opacity: 0.3; }
    }

    .hero h1 {
      font-family: 'Syne', sans-serif;
      font-size: clamp(3rem, 7vw, 5.5rem);
      font-weight: 800;
      line-height: 1.0;
      letter-spacing: -0.02em;
      animation: fadeUp 0.6s 0.1s ease both;
    }

    .hero h1 span {
      display: block;
      color: transparent;
      -webkit-text-stroke: 1px rgba(0,229,255,0.5);
    }

    .hero-desc {
      margin-top: 1.8rem;
      font-size: 0.88rem;
      line-height: 1.9;
      color: var(--muted);
      max-width: 500px;
      animation: fadeUp 0.6s 0.2s ease both;
    }

    .hero-cta {
      margin-top: 2.5rem;
      display: flex;
      gap: 1rem;
      flex-wrap: wrap;
      animation: fadeUp 0.6s 0.3s ease both;
    }

    .btn {
      display: inline-flex;
      align-items: center;
      gap: 0.5rem;
      padding: 0.8rem 1.8rem;
      font-family: 'IBM Plex Mono', monospace;
      font-size: 0.78rem;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      text-decoration: none;
      border-radius: 2px;
      cursor: pointer;
      transition: all 0.2s;
    }

    .btn-primary {
      background: var(--accent);
      color: #000;
      font-weight: 500;
    }

    .btn-primary:hover {
      background: #fff;
      transform: translateY(-2px);
      box-shadow: 0 8px 30px rgba(0,229,255,0.3);
    }

    .btn-outline {
      background: transparent;
      color: var(--text);
      border: 1px solid var(--border);
    }

    .btn-outline:hover {
      border-color: var(--accent);
      color: var(--accent);
    }

    /* ── ROBOT SVG ── */
    .hero-visual {
      position: absolute;
      right: 5%;
      top: 50%;
      transform: translateY(-50%);
      opacity: 0.18;
      pointer-events: none;
      animation: float 6s ease-in-out infinite;
    }

    @keyframes float {
      0%, 100% { transform: translateY(-50%) rotate(-2deg); }
      50% { transform: translateY(calc(-50% - 20px)) rotate(2deg); }
    }

    /* ── SECTION BASE ── */
    section {
      position: relative;
      z-index: 2;
      padding: 6rem 3rem;
    }

    .section-label {
      font-size: 0.7rem;
      letter-spacing: 0.25em;
      text-transform: uppercase;
      color: var(--accent);
      margin-bottom: 0.6rem;
    }

    .section-title {
      font-family: 'Syne', sans-serif;
      font-size: clamp(2rem, 4vw, 3rem);
      font-weight: 800;
      letter-spacing: -0.02em;
      line-height: 1.1;
      margin-bottom: 3rem;
    }

    /* ── DIVIDER ── */
    .divider {
      height: 1px;
      background: linear-gradient(90deg, var(--accent), transparent);
      opacity: 0.2;
      margin: 0 3rem;
    }

    /* ── STATS ── */
    .stats {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
      gap: 1px;
      background: var(--border);
      border: 1px solid var(--border);
      margin-top: 4rem;
      animation: fadeUp 0.6s 0.4s ease both;
    }

    .stat {
      background: var(--bg);
      padding: 2rem 1.5rem;
      text-align: center;
      transition: background 0.2s;
    }

    .stat:hover { background: var(--surface); }

    .stat-num {
      font-family: 'Syne', sans-serif;
      font-size: 2.2rem;
      font-weight: 800;
      color: var(--accent);
    }

    .stat-label {
      font-size: 0.7rem;
      color: var(--muted);
      letter-spacing: 0.1em;
      margin-top: 0.3rem;
    }

    /* ── SKILLS ── */
    .skills-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
      gap: 1.5rem;
    }

    .skill-card {
      background: var(--surface);
      border: 1px solid var(--border);
      padding: 2rem;
      border-radius: 4px;
      transition: border-color 0.2s, transform 0.2s;
      position: relative;
      overflow: hidden;
    }

    .skill-card::before {
      content: '';
      position: absolute;
      top: 0; left: 0;
      width: 3px; height: 100%;
      background: var(--accent);
      transform: scaleY(0);
      transform-origin: bottom;
      transition: transform 0.3s;
    }

    .skill-card:hover::before { transform: scaleY(1); }
    .skill-card:hover { border-color: rgba(0,229,255,0.3); transform: translateX(4px); }

    .skill-icon {
      font-size: 1.6rem;
      margin-bottom: 1rem;
    }

    .skill-name {
      font-family: 'Syne', sans-serif;
      font-size: 1rem;
      font-weight: 700;
      margin-bottom: 0.5rem;
    }

    .skill-desc {
      font-size: 0.78rem;
      color: var(--muted);
      line-height: 1.7;
    }

    .skill-tags {
      display: flex;
      flex-wrap: wrap;
      gap: 0.4rem;
      margin-top: 1rem;
    }

    .tag {
      font-size: 0.65rem;
      padding: 0.25rem 0.6rem;
      background: rgba(0,229,255,0.08);
      border: 1px solid rgba(0,229,255,0.2);
      color: var(--accent);
      border-radius: 2px;
      letter-spacing: 0.06em;
    }

    /* ── PROJECT ── */
    .project-card {
      background: var(--surface);
      border: 1px solid var(--border);
      border-radius: 4px;
      padding: 2.5rem;
      display: grid;
      grid-template-columns: 1fr auto;
      gap: 2rem;
      transition: border-color 0.2s;
      margin-bottom: 1.5rem;
    }

    .project-card:hover { border-color: rgba(0,229,255,0.4); }

    .project-meta {
      font-size: 0.7rem;
      color: var(--muted);
      letter-spacing: 0.12em;
      text-transform: uppercase;
      margin-bottom: 0.8rem;
    }

    .project-title {
      font-family: 'Syne', sans-serif;
      font-size: 1.5rem;
      font-weight: 800;
      margin-bottom: 1rem;
    }

    .project-desc {
      font-size: 0.82rem;
      color: var(--muted);
      line-height: 1.8;
      margin-bottom: 1.5rem;
    }

    .project-highlights {
      list-style: none;
      display: flex;
      flex-direction: column;
      gap: 0.5rem;
    }

    .project-highlights li {
      font-size: 0.78rem;
      color: var(--text);
      display: flex;
      align-items: flex-start;
      gap: 0.6rem;
    }

    .project-highlights li::before {
      content: '▸';
      color: var(--accent);
      flex-shrink: 0;
    }

    .project-badge {
      align-self: start;
      background: rgba(0,229,255,0.08);
      border: 1px solid rgba(0,229,255,0.2);
      border-radius: 4px;
      padding: 1.5rem;
      text-align: center;
      min-width: 120px;
    }

    .project-badge-icon {
      font-size: 2.5rem;
      display: block;
      margin-bottom: 0.5rem;
    }

    .project-badge-label {
      font-size: 0.65rem;
      color: var(--accent);
      letter-spacing: 0.1em;
      text-transform: uppercase;
    }

    /* ── PROGRESS BARS ── */
    .proficiency-list {
      display: flex;
      flex-direction: column;
      gap: 1.2rem;
    }

    .proficiency-item { }

    .proficiency-header {
      display: flex;
      justify-content: space-between;
      font-size: 0.78rem;
      margin-bottom: 0.5rem;
    }

    .proficiency-pct { color: var(--accent); }

    .bar-track {
      height: 3px;
      background: var(--border);
      border-radius: 2px;
      overflow: hidden;
    }

    .bar-fill {
      height: 100%;
      background: linear-gradient(90deg, var(--accent), #00b4d8);
      border-radius: 2px;
      transform-origin: left;
      animation: barGrow 1.2s ease both;
    }

    @keyframes barGrow {
      from { transform: scaleX(0); }
      to { transform: scaleX(1); }
    }

    /* ── CONTACT ── */
    .contact-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 3rem;
    }

    .contact-info { display: flex; flex-direction: column; gap: 1.2rem; }

    .contact-item {
      display: flex;
      align-items: center;
      gap: 1rem;
      padding: 1.2rem 1.5rem;
      background: var(--surface);
      border: 1px solid var(--border);
      border-radius: 4px;
      font-size: 0.82rem;
      transition: border-color 0.2s;
    }

    .contact-item:hover { border-color: var(--accent); }

    .contact-item-icon {
      font-size: 1.2rem;
      width: 40px;
      text-align: center;
    }

    .contact-item-label {
      font-size: 0.65rem;
      color: var(--muted);
      letter-spacing: 0.1em;
      text-transform: uppercase;
    }

    .contact-form { display: flex; flex-direction: column; gap: 1rem; }

    .form-field {
      background: var(--surface);
      border: 1px solid var(--border);
      border-radius: 4px;
      padding: 1rem 1.2rem;
      color: var(--text);
      font-family: 'IBM Plex Mono', monospace;
      font-size: 0.82rem;
      outline: none;
      transition: border-color 0.2s;
      resize: none;
    }

    .form-field::placeholder { color: var(--muted); }
    .form-field:focus { border-color: var(--accent); }

    /* ── FOOTER ── */
    footer {
      position: relative;
      z-index: 2;
      border-top: 1px solid var(--border);
      padding: 2rem 3rem;
      display: flex;
      justify-content: space-between;
      align-items: center;
      font-size: 0.72rem;
      color: var(--muted);
    }

    /* ── ANIMATIONS ── */
    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(24px); }
      to   { opacity: 1; transform: translateY(0); }
    }

    .reveal {
      opacity: 0;
      transform: translateY(30px);
      transition: opacity 0.7s ease, transform 0.7s ease;
    }

    .reveal.visible {
      opacity: 1;
      transform: translateY(0);
    }

    /* ── RESPONSIVE ── */
    @media (max-width: 768px) {
      nav { padding: 1rem 1.5rem; }
      .nav-links { display: none; }
      section { padding: 4rem 1.5rem; }
      .hero { padding: 7rem 1.5rem 4rem; }
      .hero-visual { display: none; }
      .project-card { grid-template-columns: 1fr; }
      .contact-grid { grid-template-columns: 1fr; }
      .divider { margin: 0 1.5rem; }
      footer { flex-direction: column; gap: 0.5rem; text-align: center; }
    }
  </style>
</head>
<body>

<div id="cursor-glow"></div>

<!-- NAV -->
<nav>
  <div class="nav-logo">ROBO.DEV</div>
  <ul class="nav-links">
    <li><a href="#about">About</a></li>
    <li><a href="#skills">Skills</a></li>
    <li><a href="#projects">Projects</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
</nav>

<!-- HERO -->
<section class="hero" id="about">
  <div class="hero-content">
    <div class="hero-tag">Mechanical Engineering · Robot Control Systems</div>
    <h1>
      Building<br/>
      Smarter<br/>
      <span>Machines.</span>
    </h1>
    <p class="hero-desc">
      // 기계공학 전공 · 로봇 제어 시스템 연구<br/>
      로봇암 제어 프로그래밍 경험을 바탕으로 정밀하고 반응적인 로봇 시스템을 설계합니다.
    </p>
    <div class="hero-cta">
      <a href="#projects" class="btn btn-primary">▸ 프로젝트 보기</a>
      <a href="#contact" class="btn btn-outline">연락하기</a>
    </div>
  </div>

  <!-- Robot SVG -->
  <svg class="hero-visual" width="520" height="520" viewBox="0 0 520 520" fill="none" xmlns="http://www.w3.org/2000/svg">
    <!-- Body -->
    <rect x="160" y="200" width="200" height="180" rx="12" stroke="#00e5ff" stroke-width="2"/>
    <!-- Head -->
    <rect x="185" y="130" width="150" height="80" rx="10" stroke="#00e5ff" stroke-width="2"/>
    <!-- Eyes -->
    <circle cx="225" cy="168" r="14" stroke="#00e5ff" stroke-width="2"/>
    <circle cx="225" cy="168" r="6" fill="#00e5ff" opacity="0.8"/>
    <circle cx="295" cy="168" r="14" stroke="#00e5ff" stroke-width="2"/>
    <circle cx="295" cy="168" r="6" fill="#00e5ff" opacity="0.8"/>
    <!-- Mouth -->
    <rect x="215" y="192" width="90" height="6" rx="3" fill="#00e5ff" opacity="0.5"/>
    <!-- Neck -->
    <rect x="243" y="210" width="34" height="18" stroke="#00e5ff" stroke-width="1.5" opacity="0.6"/>
    <!-- Arm Left -->
    <rect x="80" y="210" width="80" height="24" rx="12" stroke="#00e5ff" stroke-width="2"/>
    <rect x="60" y="234" width="24" height="70" rx="10" stroke="#00e5ff" stroke-width="2"/>
    <!-- Arm Right -->
    <rect x="360" y="210" width="80" height="24" rx="12" stroke="#00e5ff" stroke-width="2"/>
    <rect x="436" y="234" width="24" height="70" rx="10" stroke="#00e5ff" stroke-width="2"/>
    <!-- Legs -->
    <rect x="190" y="380" width="40" height="90" rx="10" stroke="#00e5ff" stroke-width="2"/>
    <rect x="290" y="380" width="40" height="90" rx="10" stroke="#00e5ff" stroke-width="2"/>
    <!-- Body Details -->
    <rect x="195" y="240" width="130" height="3" rx="2" fill="#00e5ff" opacity="0.3"/>
    <rect x="195" y="260" width="80" height="3" rx="2" fill="#00e5ff" opacity="0.3"/>
    <circle cx="260" cy="300" r="28" stroke="#00e5ff" stroke-width="2" opacity="0.6"/>
    <circle cx="260" cy="300" r="16" stroke="#00e5ff" stroke-width="1.5" opacity="0.4"/>
    <circle cx="260" cy="300" r="6" fill="#00e5ff" opacity="0.7"/>
    <!-- Signal -->
    <path d="M260 100 Q260 80 270 70" stroke="#00e5ff" stroke-width="1.5" opacity="0.4" stroke-dasharray="4 4"/>
    <circle cx="273" cy="67" r="4" fill="#00e5ff" opacity="0.6"/>
  </svg>

  <!-- Stats bar -->
  <div class="stats" style="position:absolute; bottom:0; left:0; right:0; grid-template-columns: repeat(4,1fr); margin:0; border-left:0; border-right:0; border-bottom:0;">
    <div class="stat"><div class="stat-num">3+</div><div class="stat-label">Years Study</div></div>
    <div class="stat"><div class="stat-num">1</div><div class="stat-label">Robot Arm Project</div></div>
    <div class="stat"><div class="stat-num">6DOF</div><div class="stat-label">Control System</div></div>
    <div class="stat"><div class="stat-num">∞</div><div class="stat-label">Curiosity</div></div>
  </div>
</section>

<div class="divider"></div>

<!-- SKILLS -->
<section id="skills">
  <p class="section-label reveal">// 02 — Skills</p>
  <h2 class="section-title reveal">전문 역량</h2>

  <div class="skills-grid reveal">
    <div class="skill-card">
      <div class="skill-icon">⚙️</div>
      <div class="skill-name">로봇 제어 시스템</div>
      <div class="skill-desc">로봇암의 정밀한 움직임 제어를 위한 알고리즘 설계 및 구현. 역기구학(IK) 계산 및 경로 계획.</div>
      <div class="skill-tags">
        <span class="tag">Kinematics</span>
        <span class="tag">Path Planning</span>
        <span class="tag">PID Control</span>
      </div>
    </div>

    <div class="skill-card">
      <div class="skill-icon">💻</div>
      <div class="skill-name">임베디드 프로그래밍</div>
      <div class="skill-desc">마이크로컨트롤러 기반 실시간 제어 시스템 개발. 센서 데이터 처리 및 액추에이터 제어.</div>
      <div class="skill-tags">
        <span class="tag">C/C++</span>
        <span class="tag">Python</span>
        <span class="tag">Arduino</span>
        <span class="tag">ROS</span>
      </div>
    </div>

    <div class="skill-card">
      <div class="skill-icon">📐</div>
      <div class="skill-name">기계공학 설계</div>
      <div class="skill-desc">기구학 분석, 동역학 모델링, CAD 설계. 구조 해석을 통한 최적 설계 구현.</div>
      <div class="skill-tags">
        <span class="tag">SolidWorks</span>
        <span class="tag">MATLAB</span>
        <span class="tag">Simulink</span>
      </div>
    </div>

    <div class="skill-card">
      <div class="skill-icon">🔬</div>
      <div class="skill-name">센서 & 비전 시스템</div>
      <div class="skill-desc">다양한 센서 인터페이스 및 컴퓨터 비전을 활용한 로봇의 환경 인식 및 피드백 제어.</div>
      <div class="skill-tags">
        <span class="tag">OpenCV</span>
        <span class="tag">IMU</span>
        <span class="tag">Force Sensor</span>
      </div>
    </div>
  </div>

  <!-- Proficiency bars -->
  <div style="margin-top: 4rem; display: grid; grid-template-columns: 1fr 1fr; gap: 3rem;" class="reveal">
    <div>
      <h3 style="font-family:'Syne',sans-serif; font-size:1.1rem; font-weight:700; margin-bottom:1.5rem;">Technical Proficiency</h3>
      <div class="proficiency-list">
        <div class="proficiency-item">
          <div class="proficiency-header"><span>Robot Control Systems</span><span class="proficiency-pct">85%</span></div>
          <div class="bar-track"><div class="bar-fill" style="width:85%"></div></div>
        </div>
        <div class="proficiency-item">
          <div class="proficiency-header"><span>C / C++ Programming</span><span class="proficiency-pct">78%</span></div>
          <div class="bar-track"><div class="bar-fill" style="width:78%; animation-delay:0.1s"></div></div>
        </div>
        <div class="proficiency-item">
          <div class="proficiency-header"><span>Python / ROS</span><span class="proficiency-pct">75%</span></div>
          <div class="bar-track"><div class="bar-fill" style="width:75%; animation-delay:0.2s"></div></div>
        </div>
        <div class="proficiency-item">
          <div class="proficiency-header"><span>MATLAB / Simulink</span><span class="proficiency-pct">70%</span></div>
          <div class="bar-track"><div class="bar-fill" style="width:70%; animation-delay:0.3s"></div></div>
        </div>
        <div class="proficiency-item">
          <div class="proficiency-header"><span>CAD Design</span><span class="proficiency-pct">65%</span></div>
          <div class="bar-track"><div class="bar-fill" style="width:65%; animation-delay:0.4s"></div></div>
        </div>
      </div>
    </div>
    <div>
      <h3 style="font-family:'Syne',sans-serif; font-size:1.1rem; font-weight:700; margin-bottom:1.5rem;">Education</h3>
      <div style="background:var(--surface); border:1px solid var(--border); border-radius:4px; padding:2rem; border-left: 3px solid var(--accent);">
        <div style="font-size:0.7rem; color:var(--muted); letter-spacing:0.12em; text-transform:uppercase; margin-bottom:0.5rem;">현재 재학 중</div>
        <div style="font-family:'Syne',sans-serif; font-size:1.2rem; font-weight:700; margin-bottom:0.4rem;">기계공학과</div>
        <div style="font-size:0.82rem; color:var(--muted); margin-bottom:1rem;">로봇제어시스템 전공 연구</div>
        <div style="display:flex; flex-direction:column; gap:0.5rem;">
          <div style="font-size:0.75rem; color:var(--text); display:flex; gap:0.6rem; align-items:center;">
            <span style="color:var(--accent);">✓</span> 로봇 공학 이론 및 실습
          </div>
          <div style="font-size:0.75rem; color:var(--text); display:flex; gap:0.6rem; align-items:center;">
            <span style="color:var(--accent);">✓</span> 제어 시스템 설계
          </div>
          <div style="font-size:0.75rem; color:var(--text); display:flex; gap:0.6rem; align-items:center;">
            <span style="color:var(--accent);">✓</span> 임베디드 시스템 개발
          </div>
          <div style="font-size:0.75rem; color:var(--text); display:flex; gap:0.6rem; align-items:center;">
            <span style="color:var(--accent);">✓</span> 팀 프로젝트 참여 경험
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<div class="divider"></div>

<!-- PROJECTS -->
<section id="projects">
  <p class="section-label reveal">// 03 — Projects</p>
  <h2 class="section-title reveal">프로젝트</h2>

  <div class="project-card reveal">
    <div>
      <div class="project-meta">2024 · 팀 프로젝트 · 프로그래머 역할</div>
      <h3 class="project-title">🦾 로봇암 정밀 제어 시스템</h3>
      <p class="project-desc">
        다관절 로봇암 제작 프로젝트에서 소프트웨어 파트를 담당. 기존 대비 더욱 세심하고 정밀한 팔 동작 제어를 위해 제어 알고리즘을 직접 설계 및 구현하였습니다.
      </p>
      <ul class="project-highlights">
        <li>역기구학(Inverse Kinematics) 알고리즘 구현으로 엔드 이펙터 정밀 위치 제어 달성</li>
        <li>PID 제어 튜닝을 통한 관절 모터의 오버슈트 최소화 및 응답 속도 최적화</li>
        <li>실시간 센서 피드백 루프 구성으로 외란(disturbance)에 대한 강인한 제어 실현</li>
        <li>팀원과의 협업을 통해 하드웨어-소프트웨어 인터페이스 설계 및 통합 테스트 수행</li>
      </ul>
      <div class="skill-tags" style="margin-top:1.5rem;">
        <span class="tag">C++</span>
        <span class="tag">Inverse Kinematics</span>
        <span class="tag">PID Control</span>
        <span class="tag">Servo Motor</span>
        <span class="tag">Embedded System</span>
        <span class="tag">Team Project</span>
      </div>
    </div>
    <div class="project-badge">
      <span class="project-badge-icon">🤖</span>
      <div class="project-badge-label">Robot Arm</div>
      <div style="margin-top:1rem; font-size:0.65rem; color:var(--muted);">6-DOF</div>
      <div style="margin-top:0.3rem; font-size:0.65rem; color:var(--accent);">Completed</div>
    </div>
  </div>

  <!-- Placeholder for future project -->
  <div class="project-card reveal" style="border-style: dashed; opacity:0.5;">
    <div>
      <div class="project-meta">Coming Soon</div>
      <h3 class="project-title">🚀 Next Project</h3>
      <p class="project-desc">현재 준비 중인 프로젝트입니다. 더 많은 내용이 곧 추가될 예정입니다.</p>
    </div>
    <div class="project-badge">
      <span class="project-badge-icon">⏳</span>
      <div class="project-badge-label">In Progress</div>
    </div>
  </div>
</section>

<div class="divider"></div>

<!-- CONTACT -->
<section id="contact">
  <p class="section-label reveal">// 04 — Contact</p>
  <h2 class="section-title reveal">연락하기</h2>

  <div class="contact-grid reveal">
    <div class="contact-info">
      <p style="font-size:0.85rem; color:var(--muted); line-height:1.8; margin-bottom:1rem;">
        로봇 공학, 제어 시스템, 또는 협업에 관심이 있으시다면 언제든지 연락주세요. 함께 더 나은 기계를 만들어갑시다.
      </p>
      <div class="contact-item">
        <span class="contact-item-icon">📧</span>
        <div>
          <div class="contact-item-label">Email</div>
          <div>your.email@example.com</div>
        </div>
      </div>
      <div class="contact-item">
        <span class="contact-item-icon">🐙</span>
        <div>
          <div class="contact-item-label">GitHub</div>
          <div>github.com/yourusername</div>
        </div>
      </div>
      <div class="contact-item">
        <span class="contact-item-icon">💼</span>
        <div>
          <div class="contact-item-label">LinkedIn</div>
          <div>linkedin.com/in/yourprofile</div>
        </div>
      </div>
      <div class="contact-item">
        <span class="contact-item-icon">📍</span>
        <div>
          <div class="contact-item-label">Location</div>
          <div>대한민국</div>
        </div>
      </div>
    </div>

    <div class="contact-form">
      <input class="form-field" type="text" placeholder="// 이름" />
      <input class="form-field" type="email" placeholder="// 이메일" />
      <textarea class="form-field" rows="5" placeholder="// 메시지를 입력하세요..."></textarea>
      <button class="btn btn-primary" style="border:none; justify-content:center;">▸ 메시지 전송</button>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <span>© 2025 — Robotics Engineer Portfolio</span>
  <span style="color:var(--accent);">Built with precision · 정밀하게 제작됨</span>
</footer>

<script>
  // Cursor glow
  const glow = document.getElementById('cursor-glow');
  document.addEventListener('mousemove', e => {
    glow.style.left = e.clientX + 'px';
    glow.style.top  = e.clientY + 'px';
  });

  // Scroll reveal
  const reveals = document.querySelectorAll('.reveal');
  const observer = new IntersectionObserver(entries => {
    entries.forEach((entry, i) => {
      if (entry.isIntersecting) {
        setTimeout(() => entry.target.classList.add('visible'), i * 80);
      }
    });
  }, { threshold: 0.1 });
  reveals.forEach(el => observer.observe(el));

  // Smooth nav links
  document.querySelectorAll('a[href^="#"]').forEach(a => {
    a.addEventListener('click', e => {
      e.preventDefault();
      document.querySelector(a.getAttribute('href'))?.scrollIntoView({ behavior: 'smooth' });
    });
  });
</script>
</body>
</html>
