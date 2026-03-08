<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Nabil Amin – Developer Profile</title>
<link href="https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&family=Syne:wght@400;600;700;800&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #0a0e1a;
    --surface: #111827;
    --surface2: #1a2235;
    --border: #1f2d45;
    --accent: #00d4ff;
    --accent2: #7c3aed;
    --accent3: #f59e0b;
    --text: #e2e8f0;
    --muted: #64748b;
    --green: #10b981;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Syne', sans-serif;
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* Animated grid background */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(0,212,255,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(0,212,255,0.03) 1px, transparent 1px);
    background-size: 40px 40px;
    pointer-events: none;
    z-index: 0;
  }

  .container {
    max-width: 860px;
    margin: 0 auto;
    padding: 48px 24px;
    position: relative;
    z-index: 1;
  }

  /* ── HEADER ── */
  .header {
    text-align: center;
    margin-bottom: 56px;
    position: relative;
  }

  .header-glow {
    position: absolute;
    top: -60px;
    left: 50%;
    transform: translateX(-50%);
    width: 400px;
    height: 400px;
    background: radial-gradient(circle, rgba(0,212,255,0.08) 0%, transparent 70%);
    pointer-events: none;
  }

  .greeting {
    font-family: 'Space Mono', monospace;
    font-size: 13px;
    color: var(--accent);
    letter-spacing: 4px;
    text-transform: uppercase;
    margin-bottom: 16px;
    opacity: 0;
    animation: fadeUp 0.6s ease forwards 0.1s;
  }

  .name {
    font-size: clamp(2.4rem, 6vw, 4rem);
    font-weight: 800;
    line-height: 1.05;
    background: linear-gradient(135deg, #fff 30%, var(--accent) 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    margin-bottom: 12px;
    opacity: 0;
    animation: fadeUp 0.6s ease forwards 0.2s;
  }

  .title {
    font-size: 1rem;
    color: var(--muted);
    font-weight: 400;
    letter-spacing: 1px;
    opacity: 0;
    animation: fadeUp 0.6s ease forwards 0.3s;
  }

  .title span {
    color: var(--accent);
    font-weight: 600;
  }

  /* ── DIVIDER ── */
  .divider {
    display: flex;
    align-items: center;
    gap: 16px;
    margin: 40px 0;
    opacity: 0;
    animation: fadeUp 0.6s ease forwards 0.4s;
  }

  .divider::before, .divider::after {
    content: '';
    flex: 1;
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--border), transparent);
  }

  .divider-dot {
    width: 6px; height: 6px;
    border-radius: 50%;
    background: var(--accent);
    box-shadow: 0 0 12px var(--accent);
  }

  /* ── SECTION ── */
  .section {
    margin-bottom: 48px;
    opacity: 0;
    animation: fadeUp 0.6s ease forwards;
  }

  .section:nth-child(1) { animation-delay: 0.5s; }
  .section:nth-child(2) { animation-delay: 0.6s; }
  .section:nth-child(3) { animation-delay: 0.7s; }
  .section:nth-child(4) { animation-delay: 0.8s; }
  .section:nth-child(5) { animation-delay: 0.9s; }

  .section-label {
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    color: var(--accent);
    letter-spacing: 3px;
    text-transform: uppercase;
    margin-bottom: 20px;
    display: flex;
    align-items: center;
    gap: 10px;
  }

  .section-label::after {
    content: '';
    flex: 1;
    height: 1px;
    background: var(--border);
  }

  /* ── ABOUT CARDS ── */
  .about-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 12px;
  }

  .about-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 16px 20px;
    display: flex;
    align-items: center;
    gap: 12px;
    transition: border-color 0.2s, transform 0.2s;
  }

  .about-card:hover {
    border-color: var(--accent);
    transform: translateY(-2px);
  }

  .about-icon {
    font-size: 1.4rem;
    flex-shrink: 0;
  }

  .about-card p {
    font-size: 0.85rem;
    color: var(--muted);
    line-height: 1.4;
  }

  .about-card p strong {
    display: block;
    color: var(--text);
    font-size: 0.9rem;
    margin-bottom: 2px;
  }

  /* ── CONNECT ── */
  .connect-row {
    display: flex;
    gap: 12px;
    flex-wrap: wrap;
  }

  .connect-btn {
    display: inline-flex;
    align-items: center;
    gap: 10px;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 12px 20px;
    text-decoration: none;
    color: var(--text);
    font-size: 0.9rem;
    font-weight: 600;
    transition: all 0.2s;
  }

  .connect-btn:hover {
    border-color: #0077b5;
    background: rgba(0,119,181,0.1);
    color: #0ea5e9;
    transform: translateY(-2px);
  }

  .connect-btn svg {
    width: 18px; height: 18px;
    fill: currentColor;
  }

  .email-btn:hover {
    border-color: var(--accent);
    background: rgba(0,212,255,0.08);
    color: var(--accent);
  }

  /* ── TECH GRID ── */
  .tech-grid {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
  }

  .tech-pill {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 8px 16px;
    font-size: 0.82rem;
    font-family: 'Space Mono', monospace;
    color: var(--muted);
    display: flex;
    align-items: center;
    gap: 8px;
    transition: all 0.2s;
    cursor: default;
  }

  .tech-pill:hover {
    border-color: var(--accent);
    color: var(--accent);
    background: rgba(0,212,255,0.05);
  }

  .tech-pill .dot {
    width: 6px; height: 6px;
    border-radius: 50%;
    background: var(--accent);
    flex-shrink: 0;
  }

  .tech-pill.primary .dot { background: #61dafb; }
  .tech-pill.primary { border-color: rgba(97,218,251,0.2); }
  .tech-pill.primary:hover { border-color: #61dafb; color: #61dafb; background: rgba(97,218,251,0.05); }

  .tech-pill.ts .dot { background: #3178c6; }
  .tech-pill.ts:hover { border-color: #3178c6; color: #3178c6; background: rgba(49,120,198,0.05); }

  .tech-pill.flutter .dot { background: #54c5f8; }
  .tech-pill.flutter:hover { border-color: #54c5f8; color: #54c5f8; background: rgba(84,197,248,0.05); }

  .tech-pill.fire .dot { background: #ffa611; }
  .tech-pill.fire:hover { border-color: #ffa611; color: #ffa611; background: rgba(255,166,17,0.05); }

  /* ── STATS ── */
  .stats-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
    gap: 16px;
  }

  .stat-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 24px;
    text-align: center;
    position: relative;
    overflow: hidden;
    transition: transform 0.2s, border-color 0.2s;
  }

  .stat-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 2px;
    background: linear-gradient(90deg, var(--accent2), var(--accent));
  }

  .stat-card:hover {
    transform: translateY(-3px);
    border-color: rgba(0,212,255,0.3);
  }

  .stat-value {
    font-size: 2rem;
    font-weight: 800;
    font-family: 'Space Mono', monospace;
    background: linear-gradient(135deg, #fff, var(--accent));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    line-height: 1;
    margin-bottom: 8px;
  }

  .stat-label {
    font-size: 0.78rem;
    color: var(--muted);
    letter-spacing: 1.5px;
    text-transform: uppercase;
    font-family: 'Space Mono', monospace;
  }

  /* Language bars */
  .lang-section {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 28px;
  }

  .lang-title {
    font-size: 0.85rem;
    font-family: 'Space Mono', monospace;
    color: var(--muted);
    margin-bottom: 20px;
    letter-spacing: 2px;
    text-transform: uppercase;
  }

  .lang-item {
    margin-bottom: 14px;
  }

  .lang-row {
    display: flex;
    justify-content: space-between;
    margin-bottom: 6px;
    font-size: 0.85rem;
  }

  .lang-name { color: var(--text); font-weight: 600; }
  .lang-pct { color: var(--muted); font-family: 'Space Mono', monospace; font-size: 0.8rem; }

  .lang-bar-bg {
    height: 6px;
    background: var(--surface2);
    border-radius: 100px;
    overflow: hidden;
  }

  .lang-bar {
    height: 100%;
    border-radius: 100px;
    transition: width 1.2s cubic-bezier(0.23, 1, 0.32, 1);
  }

  /* ── QUOTE ── */
  .quote-block {
    background: var(--surface);
    border: 1px solid var(--border);
    border-left: 3px solid var(--accent);
    border-radius: 0 12px 12px 0;
    padding: 20px 28px;
    font-style: italic;
    color: var(--muted);
    font-size: 0.95rem;
    line-height: 1.6;
  }

  .quote-block::before {
    content: '"';
    font-size: 3rem;
    color: var(--accent);
    line-height: 0;
    vertical-align: -0.6em;
    margin-right: 4px;
    font-style: normal;
  }

  /* ── ANIMATIONS ── */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(20px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  /* Bar animation on load */
  .lang-bar { width: 0; }
  .lang-bar.animate { width: var(--w); }
</style>
</head>
<body>
<div class="container">

  <!-- HEADER -->
  <div class="header">
    <div class="header-glow"></div>
    <div class="greeting">Hi 👋</div>
    <h1 class="name">Nabil Amin</h1>
    <p class="title">Experienced Software Developer &nbsp;·&nbsp; <span>React & React Native Specialist</span></p>
  </div>

  <div class="divider"><div class="divider-dot"></div></div>

  <!-- ABOUT -->
  <div class="section">
    <div class="section-label">👨‍💻 About Me</div>
    <div class="about-grid">
      <div class="about-card">
        <div class="about-icon">🌱</div>
        <p><strong>Currently Learning</strong>Flutter & Dart</p>
      </div>
      <div class="about-card">
        <div class="about-icon">💬</div>
        <p><strong>Ask Me About</strong>React Native</p>
      </div>
      <div class="about-card">
        <div class="about-icon">⚡</div>
        <p><strong>Passion</strong>User-focused mobile & web apps</p>
      </div>
    </div>
  </div>

  <!-- CONNECT -->
  <div class="section">
    <div class="section-label">🤝 Connect With Me</div>
    <div class="connect-row">
      <a href="https://www.linkedin.com/in/nabil-amin-6910602a6" target="_blank" class="connect-btn">
        <svg viewBox="0 0 24 24"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 01-2.063-2.065 2.064 2.064 0 112.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>
        LinkedIn
      </a>
      <a href="mailto:nabil.amin.samir@gmail.com" class="connect-btn email-btn">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" style="fill:none"><rect width="20" height="16" x="2" y="4" rx="2"/><path d="m22 7-8.97 5.7a1.94 1.94 0 0 1-2.06 0L2 7"/></svg>
        nabil.amin.samir@gmail.com
      </a>
    </div>
  </div>

  <!-- TOOLS -->
  <div class="section">
    <div class="section-label">🛠️ Languages & Tools</div>
    <div class="tech-grid">
      <div class="tech-pill primary"><span class="dot"></span>React Native</div>
      <div class="tech-pill primary"><span class="dot"></span>React.js</div>
      <div class="tech-pill ts"><span class="dot"></span>TypeScript</div>
      <div class="tech-pill"><span class="dot"></span>JavaScript</div>
      <div class="tech-pill flutter"><span class="dot"></span>Flutter</div>
      <div class="tech-pill flutter"><span class="dot"></span>Dart</div>
      <div class="tech-pill fire"><span class="dot"></span>Firebase</div>
      <div class="tech-pill"><span class="dot"></span>Git</div>
      <div class="tech-pill"><span class="dot"></span>Postman</div>
      <div class="tech-pill"><span class="dot"></span>Figma</div>
      <div class="tech-pill"><span class="dot"></span>HTML5</div>
      <div class="tech-pill"><span class="dot"></span>CSS3</div>
      <div class="tech-pill"><span class="dot"></span>Sass</div>
    </div>
  </div>

  <!-- QUOTE -->
  <div class="section">
    <div class="quote-block">
      Code is like humor. When you have to explain it, it's bad.
    </div>
  </div>

</div>

<script>
const COLORS = [
  '#61dafb','#3178c6','#f7df1e','#54c5f8','#ff6b6b','#10b981','#a78bfa','#fbbf24'
];

async function fetchGitHub() {
  try {
    const [userRes, reposRes] = await Promise.all([
      fetch('https://api.github.com/users/nabil-amin'),
      fetch('https://api.github.com/users/nabil-amin/repos?per_page=100')
    ]);

    if (userRes.ok) {
      const u = await userRes.json();
      animateCount('repos', u.public_repos ?? 0);
      animateCount('followers', u.followers ?? 0);
      animateCount('following', u.following ?? 0);
    }

    if (reposRes.ok) {
      const repos = await reposRes.json();
      // Tally languages
      const langMap = {};
      const langFetches = repos
        .filter(r => !r.fork)
        .map(r => fetch(r.languages_url).then(res => res.json()).then(langs => {
          for (const [lang, bytes] of Object.entries(langs)) {
            langMap[lang] = (langMap[lang] || 0) + bytes;
          }
        }).catch(() => {}));

      await Promise.all(langFetches);

      const total = Object.values(langMap).reduce((a, b) => a + b, 0);
      const sorted = Object.entries(langMap)
        .sort((a, b) => b[1] - a[1])
        .slice(0, 6);

      renderLangs(sorted, total);
    }
  } catch(e) {
    document.getElementById('lang-loading').textContent = '// Could not reach GitHub API';
  }
}

function animateCount(id, target) {
  const el = document.getElementById(id);
  let start = 0;
  const duration = 1200;
  const step = (ts) => {
    if (!start) start = ts;
    const progress = Math.min((ts - start) / duration, 1);
    const eased = 1 - Math.pow(1 - progress, 3);
    el.textContent = Math.round(eased * target);
    if (progress < 1) requestAnimationFrame(step);
  };
  requestAnimationFrame(step);
}

function renderLangs(sorted, total) {
  const container = document.getElementById('langs-container');
  container.innerHTML = '';
  sorted.forEach(([lang, bytes], i) => {
    const pct = ((bytes / total) * 100).toFixed(1);
    const color = COLORS[i % COLORS.length];
    const item = document.createElement('div');
    item.className = 'lang-item';
    item.innerHTML = `
      <div class="lang-row">
        <span class="lang-name">${lang}</span>
        <span class="lang-pct">${pct}%</span>
      </div>
      <div class="lang-bar-bg">
        <div class="lang-bar" style="--w:${pct}%; background:${color};"></div>
      </div>`;
    container.appendChild(item);
    // Trigger animation next frame
    requestAnimationFrame(() => {
      requestAnimationFrame(() => {
        item.querySelector('.lang-bar').classList.add('animate');
      });
    });
  });
  if (sorted.length === 0) {
    container.innerHTML = '<div style="color:var(--muted);font-size:0.85rem;font-family:\'Space Mono\',monospace;">// No public language data found</div>';
  }
}

fetchGitHub();
</script>
</body>
</html>
