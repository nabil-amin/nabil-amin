<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Nabil Amin — GitHub README</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    font-family: 'Inter', -apple-system, sans-serif;
    background: #0d1117;
    color: #e6edf3;
    padding: 40px 20px;
    min-height: 100vh;
  }

  .readme {
    max-width: 780px;
    margin: 0 auto;
    background: #161b22;
    border: 1px solid #30363d;
    border-radius: 12px;
    padding: 48px 52px;
    line-height: 1.6;
  }

  h1 { font-size: 28px; font-weight: 700; text-align: center; margin-bottom: 6px; }
  h3 { font-size: 15px; font-weight: 500; text-align: center; color: #8b949e; margin-bottom: 20px; }

  .views-badge { text-align: center; margin-bottom: 12px; }

  hr { border: none; border-top: 1px solid #30363d; margin: 28px 0; }

  h2 { font-size: 17px; font-weight: 600; margin-bottom: 16px; color: #e6edf3; }

  /* ABOUT LIST */
  .about-list { list-style: none; display: flex; flex-direction: column; gap: 8px; }
  .about-list li { font-size: 14px; color: #c9d1d9; }

  /* ── CONNECT ROW ── */
  .connect-row {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    align-items: center;
    gap: 12px;
  }

  .connect-row a {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    padding: 8px 16px;
    border-radius: 6px;
    text-decoration: none;
    font-size: 13px;
    font-weight: 500;
    transition: opacity 0.2s;
  }
  .connect-row a:hover { opacity: 0.8; }

  .connect-row .linkedin {
    background: #0a66c2;
    color: #fff;
  }
  .connect-row .gmail {
    background: #d14836;
    color: #fff;
  }

  .connect-row a img { width: 18px; height: 18px; object-fit: contain; vertical-align: middle; }

  /* ── TOOLS ROW ── */
  .tools-row {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    align-items: center;
    gap: 10px;
  }

  .tools-row a {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    width: 52px;
    height: 52px;
    border-radius: 8px;
    background: #1c2128;
    border: 1px solid #30363d;
    transition: border-color 0.2s, background 0.2s, transform 0.15s;
    text-decoration: none;
  }
  .tools-row a:hover {
    border-color: #58a6ff;
    background: #21262d;
    transform: translateY(-2px);
  }
  .tools-row a img { width: 30px; height: 30px; object-fit: contain; }

  /* GITHUB STATS */
  .stats-center { text-align: center; margin-bottom: 14px; }
  .stats-center img { max-width: 100%; border-radius: 6px; }

  .repos-center { text-align: center; }

  /* QUOTE */
  .quote {
    text-align: center;
    font-style: italic;
    color: #8b949e;
    font-size: 14px;
    margin-top: 4px;
  }
  .quote::before { content: '⭐️ '; }
</style>
</head>
<body>
<div class="readme">

  <h1>Hi 👋, I'm Nabil Amin</h1>
  <h3>Experienced Software Developer | React &amp; React Native Specialist</h3>

  <div class="views-badge">
    <img src="https://komarev.com/ghpvc/?username=nabil-amin&label=Profile%20views&color=0e75b6&style=flat" alt="profile views"/>
  </div>

  <hr/>

  <h2>👨‍💻 About Me</h2>
  <ul class="about-list">
    <li>🌱 Currently learning <strong>Flutter</strong></li>
    <li>💬 Ask me about <strong>React Native</strong></li>
    <li>📫 Reach me at <strong>nabil.amin.samir@gmail.com</strong></li>
    <li>⚡ Passionate about creating <strong>user-focused mobile and web apps</strong></li>
  </ul>

  <hr/>

  <h2>🤝 Connect With Me</h2>
  <!-- Items in a horizontal ROW -->
  <div class="connect-row">
    <a href="https://www.linkedin.com/in/nabil-amin-6910602a6" target="_blank" class="linkedin">
      <img src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/linked-in-alt.svg" alt="LinkedIn"/>
      LinkedIn
    </a>
    <a href="mailto:nabil.amin.samir@gmail.com" class="gmail">
      <img src="https://upload.wikimedia.org/wikipedia/commons/7/7e/Gmail_icon_%282020%29.svg" alt="Gmail"/>
      Gmail
    </a>
  </div>

  <hr/>

  <h2>🛠️ Languages and Tools</h2>
  <!-- Icons in a horizontal ROW with wrapping -->
  <div class="tools-row">
    <a href="https://reactnative.dev/" title="React Native"><img src="https://reactnative.dev/img/header_logo.svg" alt="React Native"/></a>
    <a href="https://reactjs.org/" title="React"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/react/react-original-wordmark.svg" alt="React"/></a>
    <a href="https://www.typescriptlang.org/" title="TypeScript"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/typescript/typescript-original.svg" alt="TypeScript"/></a>
    <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript" title="JavaScript"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/javascript/javascript-original.svg" alt="JavaScript"/></a>
    <a href="https://flutter.dev" title="Flutter"><img src="https://www.vectorlogo.zone/logos/flutterio/flutterio-icon.svg" alt="Flutter"/></a>
    <a href="https://dart.dev" title="Dart"><img src="https://www.vectorlogo.zone/logos/dartlang/dartlang-icon.svg" alt="Dart"/></a>
    <a href="https://firebase.google.com/" title="Firebase"><img src="https://www.vectorlogo.zone/logos/firebase/firebase-icon.svg" alt="Firebase"/></a>
    <a href="https://git-scm.com/" title="Git"><img src="https://www.vectorlogo.zone/logos/git-scm/git-scm-icon.svg" alt="Git"/></a>
    <a href="https://postman.com" title="Postman"><img src="https://www.vectorlogo.zone/logos/getpostman/getpostman-icon.svg" alt="Postman"/></a>
    <a href="https://www.figma.com/" title="Figma"><img src="https://www.vectorlogo.zone/logos/figma/figma-icon.svg" alt="Figma"/></a>
    <a href="https://www.w3.org/html/" title="HTML5"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/html5/html5-original-wordmark.svg" alt="HTML5"/></a>
    <a href="https://www.w3schools.com/css/" title="CSS3"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/css3/css3-original-wordmark.svg" alt="CSS3"/></a>
    <a href="https://sass-lang.com" title="Sass"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/sass/sass-original.svg" alt="Sass"/></a>
  </div>

  <hr/>

  <h2>📊 GitHub Stats</h2>
  <div class="stats-center">
    <img src="https://github-readme-streak-stats.herokuapp.com/?user=nabil-amin&theme=tokyonight&hide_border=true" alt="streak stats"/>
  </div>
  <div class="repos-center">
    <a href="https://github.com/nabil-amin?tab=repositories">
      <img src="https://img.shields.io/badge/View%20My%20Repos-%230D1117?style=for-the-badge&logo=github&logoColor=white" alt="View Repos"/>
    </a>
  </div>

  <hr/>

  <p class="quote">"Code is like humor. When you have to explain it, it's bad."</p>

</div>
</body>
</html>
