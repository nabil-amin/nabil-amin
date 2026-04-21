<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Nabil Amin — Software Developer</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;700;800&family=DM+Mono:ital,wght@0,400;0,500;1,400&family=Instrument+Serif:ital@0;1&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --bg: #0a0a0f;
    --surface: #111118;
    --border: rgba(255,255,255,0.07);
    --accent: #7DF9C2;
    --accent2: #FF6B6B;
    --accent3: #C8A2FF;
    --text: #E8E8F0;
    --muted: #6B6B80;
    --card: #13131C;
  }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'DM Mono', monospace;
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* NOISE OVERLAY */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.04'/%3E%3C/svg%3E");
    pointer-events: none;
    z-index: 1000;
    opacity: 0.4;
  }

  /* AMBIENT GLOW */
  .glow-orb {
    position: fixed;
    border-radius: 50%;
    filter: blur(120px);
    pointer-events: none;
    z-index: 0;
    opacity: 0.12;
  }
  .glow-orb.g1 { width: 600px; height: 600px; background: var(--accent3); top: -200px; right: -100px; }
  .glow-orb.g2 { width: 400px; height: 400px; background: var(--accent); bottom: 100px; left: -100px; }

  /* LAYOUT */
  .wrapper {
    max-width: 900px;
    margin: 0 auto;
    padding: 0 32px;
    position: relative;
    z-index: 1;
  }

  /* HEADER */
  header {
    padding: 80px 0 60px;
    border-bottom: 1px solid var(--border);
    position: relative;
    overflow: hidden;
  }

  .header-tag {
    font-size: 11px;
    font-family: 'DM Mono', monospace;
    color: var(--accent);
    letter-spacing: 0.18em;
    text-transform: uppercase;
    margin-bottom: 20px;
    display: flex;
    align-items: center;
    gap: 10px;
    opacity: 0;
    animation: fadeUp 0.6s ease forwards 0.1s;
  }
  .header-tag::before { content: ''; display: block; width: 28px; height: 1px; background: var(--accent); }

  h1 {
    font-family: 'Syne', sans-serif;
    font-weight: 800;
    font-size: clamp(48px, 8vw, 88px);
    line-height: 0.95;
    letter-spacing: -0.03em;
    color: var(--text);
    opacity: 0;
    animation: fadeUp 0.7s ease forwards 0.2s;
  }

  h1 em {
    font-family: 'Instrument Serif', serif;
    font-style: italic;
    color: var(--accent);
    font-weight: 400;
  }

  .header-sub {
    margin-top: 24px;
    font-size: 14px;
    color: var(--muted);
    max-width: 420px;
    line-height: 1.8;
    opacity: 0;
    animation: fadeUp 0.7s ease forwards 0.35s;
  }

  .header-actions {
    margin-top: 36px;
    display: flex;
    gap: 14px;
    flex-wrap: wrap;
    opacity: 0;
    animation: fadeUp 0.7s ease forwards 0.5s;
  }

  .btn {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    padding: 10px 22px;
    border-radius: 2px;
    font-family: 'DM Mono', monospace;
    font-size: 12px;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    text-decoration: none;
    transition: all 0.2s ease;
    cursor: pointer;
    border: none;
  }
  .btn-primary {
    background: var(--accent);
    color: #0a0a0f;
    font-weight: 500;
  }
  .btn-primary:hover { background: #9cffd5; transform: translateY(-2px); box-shadow: 0 8px 30px rgba(125,249,194,0.25); }

  .btn-outline {
    background: transparent;
    color: var(--text);
    border: 1px solid var(--border);
  }
  .btn-outline:hover { border-color: rgba(255,255,255,0.25); background: rgba(255,255,255,0.04); }

  /* STATUS */
  .status-pill {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    font-size: 11px;
    color: var(--muted);
    border: 1px solid var(--border);
    padding: 6px 14px;
    border-radius: 100px;
    margin-top: 28px;
    opacity: 0;
    animation: fadeUp 0.7s ease forwards 0.65s;
  }
  .status-dot {
    width: 6px; height: 6px;
    border-radius: 50%;
    background: var(--accent);
    box-shadow: 0 0 8px var(--accent);
    animation: pulse 2s ease infinite;
  }
  @keyframes pulse { 0%,100%{opacity:1;} 50%{opacity:0.4;} }

  /* SECTIONS */
  section { padding: 70px 0; border-bottom: 1px solid var(--border); }
  section:last-child { border-bottom: none; }

  .section-label {
    font-size: 10px;
    letter-spacing: 0.22em;
    text-transform: uppercase;
    color: var(--muted);
    margin-bottom: 36px;
    display: flex;
    align-items: center;
    gap: 12px;
  }
  .section-label::after { content: ''; flex: 1; height: 1px; background: var(--border); }

  /* ABOUT GRID */
  .about-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 16px;
  }
  @media (max-width: 600px) { .about-grid { grid-template-columns: 1fr; } }

  .about-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 4px;
    padding: 24px;
    transition: border-color 0.2s ease, transform 0.2s ease;
    position: relative;
    overflow: hidden;
  }
  .about-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--accent), transparent);
    opacity: 0;
    transition: opacity 0.3s;
  }
  .about-card:hover { border-color: rgba(255,255,255,0.14); transform: translateY(-2px); }
  .about-card:hover::before { opacity: 1; }

  .about-card-icon { font-size: 20px; margin-bottom: 12px; }
  .about-card-title { font-size: 11px; letter-spacing: 0.12em; color: var(--muted); text-transform: uppercase; margin-bottom: 6px; }
  .about-card-value { font-size: 14px; color: var(--text); line-height: 1.6; }
  .about-card-value a { color: var(--accent); text-decoration: none; }
  .about-card-value a:hover { text-decoration: underline; }

  .about-card.span2 { grid-column: span 2; }
  @media (max-width: 600px) { .about-card.span2 { grid-column: span 1; } }

  /* SKILLS */
  .skills-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(100px, 1fr));
    gap: 10px;
  }

  .skill-chip {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 8px;
    padding: 18px 12px;
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 4px;
    font-size: 11px;
    color: var(--muted);
    text-align: center;
    transition: all 0.2s ease;
    cursor: default;
  }
  .skill-chip:hover {
    border-color: rgba(255,255,255,0.18);
    color: var(--text);
    transform: translateY(-3px);
    background: #1a1a28;
  }
  .skill-icon { font-size: 22px; line-height: 1; }

  /* SKILL GROUPS */
  .skill-group { margin-bottom: 32px; }
  .skill-group-title {
    font-size: 10px;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--accent3);
    margin-bottom: 12px;
    opacity: 0.8;
  }

  /* QUOTE */
  .quote-block {
    border-left: 2px solid var(--accent);
    padding: 20px 28px;
    background: var(--card);
    border-radius: 0 4px 4px 0;
    font-family: 'Instrument Serif', serif;
    font-style: italic;
    font-size: 20px;
    line-height: 1.6;
    color: rgba(232,232,240,0.7);
  }
  .quote-block cite {
    display: block;
    margin-top: 14px;
    font-family: 'DM Mono', monospace;
    font-style: normal;
    font-size: 11px;
    letter-spacing: 0.12em;
    color: var(--muted);
  }

  /* CONNECT */
  .connect-links {
    display: flex;
    flex-direction: column;
    gap: 12px;
  }
  .connect-link {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 18px 22px;
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 4px;
    text-decoration: none;
    color: var(--text);
    font-size: 13px;
    transition: all 0.22s ease;
    group: true;
  }
  .connect-link:hover {
    border-color: rgba(255,255,255,0.18);
    background: #1a1a28;
    transform: translateX(4px);
  }
  .connect-link-left { display: flex; align-items: center; gap: 14px; }
  .connect-link-icon {
    width: 36px; height: 36px;
    border-radius: 6px;
    display: flex; align-items: center; justify-content: center;
    font-size: 16px;
    flex-shrink: 0;
  }
  .connect-link-label { font-size: 10px; color: var(--muted); letter-spacing: 0.1em; text-transform: uppercase; margin-bottom: 2px; }
  .connect-link-value { font-size: 13px; }
  .connect-arrow { color: var(--muted); font-size: 16px; transition: transform 0.2s; }
  .connect-link:hover .connect-arrow { transform: translateX(4px); color: var(--text); }

  /* FOOTER */
  footer {
    padding: 40px 0;
    text-align: center;
    font-size: 11px;
    color: var(--muted);
    letter-spacing: 0.08em;
  }
  footer span { color: var(--accent); }

  /* ANIMATIONS */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
  }

  .reveal {
    opacity: 0;
    transform: translateY(16px);
    transition: opacity 0.6s ease, transform 0.6s ease;
  }
  .reveal.visible { opacity: 1; transform: none; }

  /* STAT ROW */
  .stat-row {
    display: flex;
    gap: 32px;
    margin-top: 40px;
    flex-wrap: wrap;
    opacity: 0;
    animation: fadeUp 0.7s ease forwards 0.8s;
  }
  .stat { }
  .stat-number {
    font-family: 'Syne', sans-serif;
    font-size: 32px;
    font-weight: 800;
    color: var(--text);
    line-height: 1;
  }
  .stat-label { font-size: 10px; color: var(--muted); letter-spacing: 0.14em; text-transform: uppercase; margin-top: 4px; }
</style>
</head>
<body>

<div class="glow-orb g1"></div>
<div class="glow-orb g2"></div>

<div class="wrapper">

  <!-- HEADER -->
  <header>
    <div class="header-tag">Software Developer</div>
    <h1>Nabil<br><em>Amin</em></h1>
    <p class="header-sub">React & React Native specialist. Building user-focused mobile and web experiences. Currently exploring Flutter.</p>

    <div class="header-actions">
      <a class="btn btn-primary" href="mailto:nabil.amin.samir@gmail.com">↗ Get in Touch</a>
      <a class="btn btn-outline" href="https://github.com/nabil-amin" target="_blank">GitHub Profile</a>
      <a class="btn btn-outline" href="https://www.linkedin.com/in/nabil-amin-6910602a6" target="_blank">LinkedIn</a>
    </div>

    <div class="status-pill">
      <span class="status-dot"></span>
      Available for new projects
    </div>

    <div class="stat-row">
      <div class="stat">
        <div class="stat-number">5+</div>
        <div class="stat-label">Years exp.</div>
      </div>
      <div class="stat">
        <div class="stat-number">13</div>
        <div class="stat-label">Tools & langs</div>
      </div>
      <div class="stat">
        <div class="stat-number">2</div>
        <div class="stat-label">Platforms</div>
      </div>
    </div>
  </header>

  <!-- ABOUT -->
  <section>
    <div class="section-label reveal">About</div>
    <div class="about-grid reveal">
      <div class="about-card">
        <div class="about-card-icon">📱</div>
        <div class="about-card-title">Specialty</div>
        <div class="about-card-value">React Native — cross-platform mobile development</div>
      </div>
      <div class="about-card">
        <div class="about-card-icon">🌱</div>
        <div class="about-card-title">Currently Learning</div>
        <div class="about-card-value">Flutter & Dart — expanding to another mobile ecosystem</div>
      </div>
      <div class="about-card">
        <div class="about-card-icon">⚡</div>
        <div class="about-card-title">Passion</div>
        <div class="about-card-value">Creating user-focused apps that feel native on every device</div>
      </div>
      <div class="about-card">
        <div class="about-card-icon">📬</div>
        <div class="about-card-title">Email</div>
        <div class="about-card-value"><a href="mailto:nabil.amin.samir@gmail.com">nabil.amin.samir@gmail.com</a></div>
      </div>
    </div>
  </section>

  <!-- SKILLS -->
  <section>
    <div class="section-label reveal">Stack</div>

    <div class="skill-group reveal">
      <div class="skill-group-title">// Core</div>
      <div class="skills-grid">
        <div class="skill-chip"><span class="skill-icon">⚛️</span>React Native</div>
        <div class="skill-chip"><span class="skill-icon">🌐</span>React.js</div>
        <div class="skill-chip"><span class="skill-icon">🔷</span>TypeScript</div>
        <div class="skill-chip"><span class="skill-icon">🟡</span>JavaScript</div>
      </div>
    </div>

    <div class="skill-group reveal">
      <div class="skill-group-title">// Mobile & Emerging</div>
      <div class="skills-grid">
        <div class="skill-chip"><span class="skill-icon">🐦</span>Flutter</div>
        <div class="skill-chip"><span class="skill-icon">🎯</span>Dart</div>
      </div>
    </div>

    <div class="skill-group reveal">
      <div class="skill-group-title">// Backend & Services</div>
      <div class="skills-grid">
        <div class="skill-chip"><span class="skill-icon">🔥</span>Firebase</div>
        <div class="skill-chip"><span class="skill-icon">📮</span>Postman</div>
      </div>
    </div>

    <div class="skill-group reveal">
      <div class="skill-group-title">// Frontend & Design</div>
      <div class="skills-grid">
        <div class="skill-chip"><span class="skill-icon">🏷️</span>HTML5</div>
        <div class="skill-chip"><span class="skill-icon">🎨</span>CSS3</div>
        <div class="skill-chip"><span class="skill-icon">💅</span>Sass</div>
        <div class="skill-chip"><span class="skill-icon">✏️</span>Figma</div>
        <div class="skill-chip"><span class="skill-icon">🔀</span>Git</div>
      </div>
    </div>
  </section>

  <!-- QUOTE -->
  <section>
    <div class="section-label reveal">Philosophy</div>
    <div class="quote-block reveal">
      Code is like humor. When you have to explain it, it's bad.
      <cite>— Nabil's guiding principle</cite>
    </div>
  </section>

  <!-- CONNECT -->
  <section>
    <div class="section-label reveal">Connect</div>
    <div class="connect-links reveal">
      <a href="mailto:nabil.amin.samir@gmail.com" class="connect-link">
        <div class="connect-link-left">
          <div class="connect-link-icon" style="background:#1e1e2e;">📧</div>
          <div>
            <div class="connect-link-label">Email</div>
            <div class="connect-link-value">nabil.amin.samir@gmail.com</div>
          </div>
        </div>
        <span class="connect-arrow">→</span>
      </a>
      <a href="https://www.linkedin.com/in/nabil-amin-6910602a6" target="_blank" class="connect-link">
        <div class="connect-link-left">
          <div class="connect-link-icon" style="background:#0a1628;">💼</div>
          <div>
            <div class="connect-link-label">LinkedIn</div>
            <div class="connect-link-value">nabil-amin-6910602a6</div>
          </div>
        </div>
        <span class="connect-arrow">→</span>
      </a>
      <a href="https://github.com/nabil-amin" target="_blank" class="connect-link">
        <div class="connect-link-left">
          <div class="connect-link-icon" style="background:#0d0d14;">🐙</div>
          <div>
            <div class="connect-link-label">GitHub</div>
            <div class="connect-link-value">github.com/nabil-amin</div>
          </div>
        </div>
        <span class="connect-arrow">→</span>
      </a>
    </div>
  </section>

  <!-- FOOTER -->
  <footer>
    <span>Nabil Amin</span> · React & React Native Developer · Cairo 🇪🇬
  </footer>

</div>

<script>
  // Scroll reveal
  const observer = new IntersectionObserver((entries) => {
    entries.forEach((entry, i) => {
      if (entry.isIntersecting) {
        setTimeout(() => entry.target.classList.add('visible'), i * 80);
        observer.unobserve(entry.target);
      }
    });
  }, { threshold: 0.1 });

  document.querySelectorAll('.reveal').forEach(el => observer.observe(el));
</script>
</body>
</html>
