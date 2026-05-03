<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Amit Kumar Verma — Full Stack Engineer</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Clash+Display:wght@400;500;600;700&family=DM+Sans:ital,wght@0,300;0,400;0,500;1,300&family=JetBrains+Mono:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  :root {
    --bg:         #0b0f1a;
    --bg2:        #111827;
    --surface:    #151d2e;
    --border:     rgba(99,179,237,0.10);
    --accent:     #63b3ed;
    --accent2:    #7ee8a2;
    --accent3:    #f6ad55;
    --muted:      #8899aa;
    --text:       #dce8f5;
    --heading:    #eaf4ff;
    --glow:       rgba(99,179,237,0.15);
    --r:          14px;
    --transition: 0.35s cubic-bezier(.4,0,.2,1);
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'DM Sans', sans-serif;
    font-weight: 300;
    line-height: 1.7;
    overflow-x: hidden;
  }

  /* ── NOISE OVERLAY ── */
  body::before {
    content: '';
    position: fixed; inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.035'/%3E%3C/svg%3E");
    pointer-events: none;
    z-index: 999;
    opacity: .4;
  }

  /* ── SCROLLBAR ── */
  ::-webkit-scrollbar { width: 4px; }
  ::-webkit-scrollbar-track { background: var(--bg); }
  ::-webkit-scrollbar-thumb { background: var(--accent); border-radius: 2px; }

  /* ── TYPOGRAPHY ── */
  h1,h2,h3,h4 {
    font-family: 'Clash Display', sans-serif;
    color: var(--heading);
    line-height: 1.15;
    letter-spacing: -0.02em;
  }

  code, .mono {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.85em;
  }

  a { color: inherit; text-decoration: none; }

  /* ── LAYOUT ── */
  .container {
    max-width: 980px;
    margin: 0 auto;
    padding: 0 28px;
  }

  section { padding: 80px 0; }

  /* ── GRADIENT BLOBS ── */
  .blob {
    position: fixed;
    border-radius: 50%;
    filter: blur(120px);
    pointer-events: none;
    z-index: 0;
  }
  .blob-1 {
    width: 500px; height: 500px;
    background: radial-gradient(circle, rgba(99,179,237,.12) 0%, transparent 70%);
    top: -100px; left: -150px;
  }
  .blob-2 {
    width: 400px; height: 400px;
    background: radial-gradient(circle, rgba(126,232,162,.08) 0%, transparent 70%);
    bottom: 100px; right: -100px;
  }
  .blob-3 {
    width: 350px; height: 350px;
    background: radial-gradient(circle, rgba(246,173,85,.07) 0%, transparent 70%);
    top: 50%; left: 60%;
  }

  /* ── NAV ── */
  nav {
    position: fixed; top: 0; left: 0; right: 0;
    z-index: 100;
    backdrop-filter: blur(18px);
    -webkit-backdrop-filter: blur(18px);
    background: rgba(11,15,26,.7);
    border-bottom: 1px solid var(--border);
    padding: 16px 0;
    transition: var(--transition);
  }

  .nav-inner {
    display: flex;
    align-items: center;
    justify-content: space-between;
    max-width: 980px;
    margin: 0 auto;
    padding: 0 28px;
  }

  .nav-logo {
    font-family: 'Clash Display', sans-serif;
    font-size: 1.1rem;
    font-weight: 600;
    color: var(--heading);
    letter-spacing: -0.01em;
  }

  .nav-logo span { color: var(--accent); }

  .nav-links {
    display: flex; gap: 32px;
    list-style: none;
  }

  .nav-links a {
    font-size: 0.82rem;
    font-weight: 400;
    color: var(--muted);
    letter-spacing: 0.08em;
    text-transform: uppercase;
    transition: color var(--transition);
  }
  .nav-links a:hover { color: var(--accent); }

  /* ── HERO ── */
  .hero {
    min-height: 100vh;
    display: flex;
    align-items: center;
    padding-top: 80px;
    position: relative;
    overflow: hidden;
  }

  .hero-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 60px;
    align-items: center;
  }

  .hero-badge {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    background: rgba(99,179,237,.08);
    border: 1px solid rgba(99,179,237,.2);
    border-radius: 100px;
    padding: 6px 16px;
    font-size: 0.75rem;
    font-family: 'JetBrains Mono', monospace;
    color: var(--accent);
    margin-bottom: 24px;
    animation: fadeSlideUp 0.6s ease both;
  }

  .hero-badge::before {
    content: '';
    width: 7px; height: 7px;
    border-radius: 50%;
    background: var(--accent2);
    box-shadow: 0 0 8px var(--accent2);
    animation: pulse 2s infinite;
  }

  @keyframes pulse {
    0%, 100% { opacity: 1; }
    50% { opacity: .3; }
  }

  .hero h1 {
    font-size: clamp(2.8rem, 5vw, 4.2rem);
    margin-bottom: 20px;
    animation: fadeSlideUp 0.7s ease 0.1s both;
  }

  .hero h1 .highlight {
    background: linear-gradient(135deg, var(--accent) 0%, var(--accent2) 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .hero-desc {
    color: var(--muted);
    font-size: 1rem;
    max-width: 480px;
    margin-bottom: 36px;
    animation: fadeSlideUp 0.7s ease 0.2s both;
  }

  .hero-actions {
    display: flex; gap: 14px; flex-wrap: wrap;
    animation: fadeSlideUp 0.7s ease 0.3s both;
  }

  .btn {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    padding: 12px 26px;
    border-radius: 100px;
    font-size: 0.85rem;
    font-weight: 500;
    transition: var(--transition);
    cursor: pointer;
    border: none;
  }

  .btn-primary {
    background: var(--accent);
    color: var(--bg);
  }
  .btn-primary:hover {
    background: #90cdf4;
    transform: translateY(-1px);
    box-shadow: 0 8px 30px rgba(99,179,237,.25);
  }

  .btn-ghost {
    background: transparent;
    border: 1px solid var(--border);
    color: var(--text);
  }
  .btn-ghost:hover {
    border-color: var(--accent);
    color: var(--accent);
    transform: translateY(-1px);
  }

  .hero-code-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: var(--r);
    overflow: hidden;
    animation: fadeSlideLeft 0.8s ease 0.2s both;
    position: relative;
  }

  .code-header {
    display: flex;
    align-items: center;
    gap: 8px;
    padding: 12px 16px;
    border-bottom: 1px solid var(--border);
    background: rgba(0,0,0,.2);
  }

  .dot { width: 10px; height: 10px; border-radius: 50%; }
  .dot-r { background: #ff5f57; }
  .dot-y { background: #febc2e; }
  .dot-g { background: #28c840; }

  .code-file { font-family: 'JetBrains Mono', monospace; font-size: 0.73rem; color: var(--muted); margin-left: auto; }

  .code-body {
    padding: 20px;
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.78rem;
    line-height: 1.8;
    overflow-x: auto;
  }

  .c-kw { color: #7ee8a2; }
  .c-var { color: #63b3ed; }
  .c-str { color: #f6ad55; }
  .c-key { color: #dce8f5; }
  .c-arr { color: #b794f4; }
  .c-muted { color: #6b7a8d; }

  /* ── STATS ── */
  .stats-row {
    display: flex;
    gap: 0;
    border: 1px solid var(--border);
    border-radius: var(--r);
    overflow: hidden;
    background: var(--surface);
    animation: fadeSlideUp 0.7s ease 0.4s both;
  }

  .stat-item {
    flex: 1;
    padding: 22px 20px;
    text-align: center;
    border-right: 1px solid var(--border);
    transition: background var(--transition);
  }
  .stat-item:last-child { border-right: none; }
  .stat-item:hover { background: rgba(99,179,237,.05); }

  .stat-num {
    font-family: 'Clash Display', sans-serif;
    font-size: 1.8rem;
    color: var(--accent);
    display: block;
    line-height: 1;
    margin-bottom: 4px;
  }
  .stat-label { font-size: 0.72rem; color: var(--muted); text-transform: uppercase; letter-spacing: .06em; }

  /* ── SECTION HEADER ── */
  .section-label {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.72rem;
    color: var(--accent);
    letter-spacing: .12em;
    text-transform: uppercase;
    margin-bottom: 12px;
    display: flex;
    align-items: center;
    gap: 10px;
  }
  .section-label::after {
    content: '';
    flex: 1;
    max-width: 60px;
    height: 1px;
    background: var(--accent);
    opacity: .3;
  }

  .section-title {
    font-size: clamp(2rem, 4vw, 2.8rem);
    margin-bottom: 48px;
  }

  .section-title em {
    font-style: normal;
    background: linear-gradient(135deg, var(--accent), var(--accent2));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  /* ── TECH GRID ── */
  .tech-section { background: var(--bg2); }

  .tech-categories { display: grid; gap: 28px; }

  .tech-category {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: var(--r);
    padding: 24px 28px;
    transition: border-color var(--transition), box-shadow var(--transition);
  }
  .tech-category:hover {
    border-color: rgba(99,179,237,.3);
    box-shadow: 0 0 40px rgba(99,179,237,.05);
  }

  .tech-cat-label {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.7rem;
    color: var(--muted);
    text-transform: uppercase;
    letter-spacing: .1em;
    margin-bottom: 14px;
  }

  .tech-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
  }

  .tag {
    padding: 5px 14px;
    border-radius: 100px;
    font-size: 0.78rem;
    font-weight: 500;
    border: 1px solid;
    transition: var(--transition);
  }
  .tag:hover { transform: translateY(-2px); }

  .tag-blue { color: #63b3ed; border-color: rgba(99,179,237,.25); background: rgba(99,179,237,.07); }
  .tag-green { color: #7ee8a2; border-color: rgba(126,232,162,.25); background: rgba(126,232,162,.07); }
  .tag-orange { color: #f6ad55; border-color: rgba(246,173,85,.25); background: rgba(246,173,85,.07); }
  .tag-purple { color: #b794f4; border-color: rgba(183,148,244,.25); background: rgba(183,148,244,.07); }

  /* ── PROJECTS ── */
  .projects-grid { display: grid; gap: 22px; }

  .project-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: var(--r);
    padding: 32px;
    transition: var(--transition);
    position: relative;
    overflow: hidden;
  }

  .project-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--accent), transparent);
    opacity: 0;
    transition: opacity var(--transition);
  }

  .project-card:hover {
    border-color: rgba(99,179,237,.25);
    transform: translateY(-3px);
    box-shadow: 0 20px 60px rgba(0,0,0,.3);
  }
  .project-card:hover::before { opacity: 1; }

  .project-header {
    display: flex;
    align-items: flex-start;
    justify-content: space-between;
    margin-bottom: 16px;
    gap: 16px;
  }

  .project-icon {
    width: 44px; height: 44px;
    border-radius: 10px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 1.3rem;
    flex-shrink: 0;
  }

  .icon-blue { background: rgba(99,179,237,.12); }
  .icon-green { background: rgba(126,232,162,.12); }
  .icon-orange { background: rgba(246,173,85,.12); }
  .icon-purple { background: rgba(183,148,244,.12); }
  .icon-pink { background: rgba(252,129,147,.12); }
  .icon-teal { background: rgba(79,209,197,.12); }
  .icon-amber { background: rgba(252,211,77,.12); }
  .icon-sky { background: rgba(56,189,248,.12); }

  .project-live-badge {
    display: inline-flex;
    align-items: center;
    gap: 5px;
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.68rem;
    color: var(--accent2);
    background: rgba(126,232,162,.08);
    border: 1px solid rgba(126,232,162,.2);
    border-radius: 100px;
    padding: 4px 10px;
    white-space: nowrap;
  }

  .project-live-badge::before {
    content: '';
    width: 5px; height: 5px;
    border-radius: 50%;
    background: var(--accent2);
    box-shadow: 0 0 6px var(--accent2);
    animation: pulse 2s infinite;
  }

  .project-name {
    font-family: 'Clash Display', sans-serif;
    font-size: 1.35rem;
    color: var(--heading);
    margin-bottom: 4px;
    letter-spacing: -0.01em;
  }

  .project-subtitle {
    font-size: 0.8rem;
    color: var(--muted);
    margin-bottom: 14px;
    font-style: italic;
  }

  .project-desc {
    font-size: 0.9rem;
    color: var(--muted);
    line-height: 1.75;
    margin-bottom: 20px;
  }

  .project-stack-table {
    width: 100%;
    border-collapse: collapse;
    margin-bottom: 20px;
    font-size: 0.82rem;
  }

  .project-stack-table tr {
    border-bottom: 1px solid var(--border);
  }
  .project-stack-table tr:last-child { border-bottom: none; }

  .project-stack-table td {
    padding: 8px 0;
    vertical-align: top;
  }

  .stack-key {
    color: var(--muted);
    font-weight: 400;
    width: 150px;
    padding-right: 16px;
    white-space: nowrap;
  }

  .stack-val {
    color: var(--text);
    display: flex;
    flex-wrap: wrap;
    gap: 5px;
  }

  .pill {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.72rem;
    padding: 2px 9px;
    border-radius: 4px;
    background: rgba(99,179,237,.08);
    color: var(--accent);
    border: 1px solid rgba(99,179,237,.15);
  }

  .project-link {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    font-size: 0.8rem;
    color: var(--accent);
    font-family: 'JetBrains Mono', monospace;
    transition: gap var(--transition);
  }
  .project-link:hover { gap: 10px; }

  /* ── PHILOSOPHY ── */
  .philosophy-section { background: var(--bg2); }

  .philosophy-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
    gap: 16px;
  }

  .philo-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: var(--r);
    padding: 22px;
    transition: var(--transition);
  }
  .philo-card:hover {
    border-color: rgba(99,179,237,.25);
    transform: translateY(-2px);
  }

  .philo-icon {
    font-size: 1.2rem;
    margin-bottom: 12px;
  }

  .philo-title {
    font-family: 'Clash Display', sans-serif;
    font-size: 0.95rem;
    color: var(--heading);
    margin-bottom: 6px;
  }

  .philo-desc {
    font-size: 0.82rem;
    color: var(--muted);
    line-height: 1.65;
  }

  /* ── CONTACT ── */
  .contact-wrapper {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 48px;
    align-items: center;
  }

  .contact-card {
    display: flex;
    align-items: center;
    gap: 16px;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: var(--r);
    padding: 20px;
    transition: var(--transition);
    cursor: pointer;
    margin-bottom: 12px;
  }
  .contact-card:hover {
    border-color: rgba(99,179,237,.25);
    transform: translateX(4px);
  }

  .contact-icon-wrap {
    width: 42px; height: 42px;
    border-radius: 10px;
    background: rgba(99,179,237,.1);
    display: flex; align-items: center; justify-content: center;
    font-size: 1.1rem;
    flex-shrink: 0;
  }

  .contact-label { font-size: 0.72rem; color: var(--muted); margin-bottom: 2px; text-transform: uppercase; letter-spacing: .06em; }
  .contact-value { font-size: 0.88rem; color: var(--heading); font-weight: 500; }

  .open-to {
    display: flex; gap: 8px; flex-wrap: wrap; margin-top: 12px;
  }

  /* ── FOOTER ── */
  footer {
    border-top: 1px solid var(--border);
    padding: 32px 0;
    text-align: center;
    font-size: 0.78rem;
    color: var(--muted);
  }

  footer strong { color: var(--accent); }

  /* ── QUOTE ── */
  .quote-banner {
    background: linear-gradient(135deg, rgba(99,179,237,.06), rgba(126,232,162,.04));
    border: 1px solid rgba(99,179,237,.12);
    border-radius: var(--r);
    padding: 32px 36px;
    margin: 48px 0 0;
    position: relative;
    overflow: hidden;
  }

  .quote-banner::before {
    content: '"';
    font-family: 'Clash Display', sans-serif;
    font-size: 8rem;
    color: var(--accent);
    opacity: .07;
    position: absolute;
    top: -20px; left: 16px;
    line-height: 1;
  }

  .quote-text {
    font-family: 'Clash Display', sans-serif;
    font-size: 1.15rem;
    color: var(--heading);
    font-weight: 500;
    position: relative;
  }

  /* ── ANIMATIONS ── */
  @keyframes fadeSlideUp {
    from { opacity: 0; transform: translateY(20px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  @keyframes fadeSlideLeft {
    from { opacity: 0; transform: translateX(30px); }
    to   { opacity: 1; transform: translateX(0); }
  }

  .reveal {
    opacity: 0;
    transform: translateY(24px);
    transition: opacity 0.6s ease, transform 0.6s ease;
  }
  .reveal.visible {
    opacity: 1;
    transform: translateY(0);
  }

  /* ── RESPONSIVE ── */
  @media (max-width: 768px) {
    .hero-grid { grid-template-columns: 1fr; gap: 40px; }
    .contact-wrapper { grid-template-columns: 1fr; }
    .nav-links { display: none; }
    .stats-row { flex-wrap: wrap; }
    .stat-item { flex: 1 1 45%; }
    .hero-code-card { display: none; }
  }
</style>
</head>
<body>

<!-- BLOBS -->
<div class="blob blob-1"></div>
<div class="blob blob-2"></div>
<div class="blob blob-3"></div>

<!-- NAV -->
<nav>
  <div class="nav-inner">
    <div class="nav-logo">AKV<span>.</span></div>
    <ul class="nav-links">
      <li><a href="#about">About</a></li>
      <li><a href="#stack">Stack</a></li>
      <li><a href="#work">Work</a></li>
      <li><a href="#philosophy">Philosophy</a></li>
      <li><a href="#contact">Contact</a></li>
    </ul>
  </div>
</nav>

<!-- HERO -->
<section class="hero" id="about">
  <div class="container">
    <div class="hero-grid">
      <div>
        <div class="hero-badge">Available for Opportunities</div>
        <h1>
          Amit Kumar<br/>
          <span class="highlight">Verma</span>
        </h1>
        <p class="hero-desc">
          Full Stack Engineer crafting high-performance systems, immersive UIs, and scalable backends —
          from 60fps animations to sub-100ms APIs.
          Based in Bihar, India 🇮🇳
        </p>
        <div class="hero-actions">
          <a href="#work" class="btn btn-primary">View Work →</a>
          <a href="mailto:amitkrverma.k@gmail.com" class="btn btn-ghost">Get in touch</a>
        </div>

        <div class="stats-row" style="margin-top:36px;">
          <div class="stat-item">
            <span class="stat-num">8+</span>
            <span class="stat-label">Live Projects</span>
          </div>
          <div class="stat-item">
            <span class="stat-num">4+</span>
            <span class="stat-label">Years Building</span>
          </div>
          <div class="stat-item">
            <span class="stat-num">60fps</span>
            <span class="stat-label">UI Target</span>
          </div>
          <div class="stat-item">
            <span class="stat-num">&lt;100ms</span>
            <span class="stat-label">API Target</span>
          </div>
        </div>
      </div>

      <!-- CODE CARD -->
      <div class="hero-code-card">
        <div class="code-header">
          <div class="dot dot-r"></div>
          <div class="dot dot-y"></div>
          <div class="dot dot-g"></div>
          <span class="code-file">amit.ts</span>
        </div>
        <div class="code-body">
<span class="c-kw">const</span> <span class="c-var">amit</span> = {<br/>
&nbsp;&nbsp;<span class="c-key">role</span>     : <span class="c-str">"Full Stack Engineer"</span>,<br/>
&nbsp;&nbsp;<span class="c-key">location</span> : <span class="c-str">"India 🇮🇳"</span>,<br/>
&nbsp;&nbsp;<span class="c-key">focus</span>    : [<span class="c-str">"Web"</span>, <span class="c-str">"Mobile"</span>, <span class="c-str">"DevOps"</span>],<br/>
<br/>
&nbsp;&nbsp;<span class="c-key">engineers</span>  : [<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-str">"REST APIs"</span>,<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-str">"WebSockets"</span>,<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-str">"cloud-native backends"</span>,<br/>
&nbsp;&nbsp;],<br/>
&nbsp;&nbsp;<span class="c-key">crafts</span>     : [<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-str">"immersive UIs"</span>,<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-str">"GSAP animations"</span>,<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-str">"60fps experiences"</span>,<br/>
&nbsp;&nbsp;],<br/>
&nbsp;&nbsp;<span class="c-key">ships_with</span> : [<span class="c-str">"Docker"</span>, <span class="c-str">"CI/CD"</span>],<br/>
<br/>
&nbsp;&nbsp;<span class="c-key">belief</span>: <span class="c-str">"Great software is felt."</span><br/>
};
        </div>
      </div>
    </div>
  </div>
</section>

<!-- TECH STACK -->
<section class="tech-section" id="stack">
  <div class="container">
    <div class="section-label">Tech Arsenal</div>
    <h2 class="section-title">Built with the <em>right tools</em></h2>

    <div class="tech-categories reveal">
      <div class="tech-category">
        <div class="tech-cat-label">// Languages & Runtimes</div>
        <div class="tech-tags">
          <span class="tag tag-blue">JavaScript</span>
          <span class="tag tag-blue">TypeScript</span>
          <span class="tag tag-orange">Python</span>
          <span class="tag tag-blue">Dart</span>
          <span class="tag tag-green">Node.js</span>
        </div>
      </div>

      <div class="tech-category">
        <div class="tech-cat-label">// Frontend & Animation</div>
        <div class="tech-tags">
          <span class="tag tag-blue">React.js</span>
          <span class="tag tag-blue">Next.js</span>
          <span class="tag tag-blue">Tailwind CSS</span>
          <span class="tag tag-green">GSAP</span>
          <span class="tag tag-purple">Framer Motion</span>
        </div>
      </div>

      <div class="tech-category">
        <div class="tech-cat-label">// Backend & APIs</div>
        <div class="tech-tags">
          <span class="tag tag-green">Express.js</span>
          <span class="tag tag-orange">REST API</span>
          <span class="tag tag-green">WebSockets</span>
          <span class="tag tag-blue">Socket.io</span>
          <span class="tag tag-orange">Apps Script</span>
        </div>
      </div>

      <div class="tech-category">
        <div class="tech-cat-label">// Databases & Storage</div>
        <div class="tech-tags">
          <span class="tag tag-green">MongoDB</span>
          <span class="tag tag-orange">Firebase</span>
          <span class="tag tag-orange">Redis</span>
          <span class="tag tag-green">Google Sheets API</span>
        </div>
      </div>

      <div class="tech-category">
        <div class="tech-cat-label">// DevOps & Infrastructure</div>
        <div class="tech-tags">
          <span class="tag tag-blue">Docker</span>
          <span class="tag tag-blue">GitHub Actions</span>
          <span class="tag tag-orange">Linux</span>
          <span class="tag tag-orange">Git</span>
          <span class="tag tag-green">CI/CD</span>
        </div>
      </div>

      <div class="tech-category">
        <div class="tech-cat-label">// Mobile</div>
        <div class="tech-tags">
          <span class="tag tag-blue">Flutter</span>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- PROJECTS -->
<section id="work">
  <div class="container">
    <div class="section-label">Featured Work</div>
    <h2 class="section-title">Production <em>deployments</em></h2>
    <p style="color:var(--muted); margin-top:-32px; margin-bottom:48px; font-size:0.9rem; font-style:italic;">Every project below serves real users — not a demo, not a tutorial clone.</p>

    <div class="projects-grid">

      <!-- COLLEGE CLUB -->
      <div class="project-card reveal">
        <div class="project-header">
          <div style="display:flex;align-items:center;gap:14px;">
            <div class="project-icon icon-blue">🎓</div>
            <div>
              <div class="project-name">College Club</div>
              <div class="project-subtitle">Full-Stack Student Community Platform</div>
            </div>
          </div>
          <a href="https://collegeclub.io" target="_blank" class="project-live-badge">LIVE</a>
        </div>
        <table class="project-stack-table">
          <tr>
            <td class="stack-key">Frontend</td>
            <td class="stack-val">
              <span class="pill">React.js</span><span class="pill">Tailwind CSS</span>
            </td>
          </tr>
          <tr>
            <td class="stack-key">Backend</td>
            <td class="stack-val">
              <span class="pill">Node.js</span><span class="pill">Express.js</span><span class="pill">WebSockets</span>
            </td>
          </tr>
          <tr>
            <td class="stack-key">Database</td>
            <td class="stack-val">
              <span class="pill">MongoDB</span><span class="pill">Redis</span>
            </td>
          </tr>
          <tr>
            <td class="stack-key">Auth & RT</td>
            <td class="stack-val">
              <span class="pill">Firebase</span><span class="pill">JWT</span><span class="pill">Socket.io</span>
            </td>
          </tr>
          <tr>
            <td class="stack-key">Infra</td>
            <td class="stack-val">
              <span class="pill">Docker</span><span class="pill">Docker Compose</span><span class="pill">GitHub Actions</span>
            </td>
          </tr>
        </table>
        <p class="project-desc">
          My most technically demanding project. Real-time messaging via WebSockets, Firebase push notifications,
          AI-powered content moderation, JWT + Firebase dual-auth, Redis caching, and a fully containerized
          production deployment. Every engineering decision I've ever made lives somewhere in this codebase.
        </p>
        <a href="https://collegeclub.io" target="_blank" class="project-link">collegeclub.io →</a>
      </div>

      <!-- SONI INFRASTRUCTURE -->
      <div class="project-card reveal">
        <div class="project-header">
          <div style="display:flex;align-items:center;gap:14px;">
            <div class="project-icon icon-amber">🏗️</div>
            <div>
              <div class="project-name">Soni Infrastructure</div>
              <div class="project-subtitle">Civil Construction & Infrastructure Company Website</div>
            </div>
          </div>
          <a href="https://soniinfrastructure.com" target="_blank" class="project-live-badge">LIVE</a>
        </div>
        <table class="project-stack-table">
          <tr>
            <td class="stack-key">Frontend</td>
            <td class="stack-val">
              <span class="pill">Next.js</span><span class="pill">Tailwind CSS</span>
            </td>
          </tr>
          <tr>
            <td class="stack-key">Animation</td>
            <td class="stack-val">
              <span class="pill">GSAP ScrollTrigger</span><span class="pill">GSAP Timeline</span><span class="pill">Framer Motion</span>
            </td>
          </tr>
          <tr>
            <td class="stack-key">UX</td>
            <td class="stack-val">
              <span class="pill">Parallax</span><span class="pill">Counter Animations</span><span class="pill">Smooth Scroll</span>
            </td>
          </tr>
        </table>
        <p class="project-desc">
          A full corporate presence for Soni Infrastructure — a civil construction firm delivering projects
          across Jharkhand and beyond, trusted by Indus Towers. The engineering challenge was translating
          the weight and scale of physical infrastructure into a digital experience. GSAP ScrollTrigger
          drives immersive hero reveals, animated stats counters surface the company's track record
          (15+ years, 200+ projects, 12 states), and smooth scroll choreography gives the site the
          gravitas the brand demands. Built to convert prospects — not just impress them.
        </p>
        <a href="https://soniinfrastructure.com" target="_blank" class="project-link">soniinfrastructure.com →</a>
      </div>

      <!-- MOUNTAIN BLISS -->
      <div class="project-card reveal">
        <div class="project-header">
          <div style="display:flex;align-items:center;gap:14px;">
            <div class="project-icon icon-teal">🏔️</div>
            <div>
              <div class="project-name">Mountain Bliss Travel & Stay</div>
              <div class="project-subtitle">Hospitality & Booking Platform</div>
            </div>
          </div>
          <a href="https://mountainblisstravelandstay.com" target="_blank" class="project-live-badge">LIVE</a>
        </div>
        <table class="project-stack-table">
          <tr>
            <td class="stack-key">Frontend</td>
            <td class="stack-val">
              <span class="pill">React.js</span><span class="pill">Tailwind CSS</span>
            </td>
          </tr>
          <tr>
            <td class="stack-key">Animation</td>
            <td class="stack-val">
              <span class="pill">GSAP ScrollTrigger</span><span class="pill">GSAP Parallax</span><span class="pill">GSAP Timeline</span>
            </td>
          </tr>
          <tr>
            <td class="stack-key">Backend</td>
            <td class="stack-val">
              <span class="pill">Google Apps Script</span><span class="pill">Sheets API</span>
            </td>
          </tr>
        </table>
        <p class="project-desc">
          Heavy GSAP orchestration — ScrollTrigger-pinned parallax sections, timeline-sequenced hero reveals,
          and scroll-velocity-aware image transitions that carry the user into the mountains before they book.
          Backend uses Google Apps Script + Sheets: pragmatic, cost-zero, production-grade at this scale.
        </p>
        <a href="https://mountainblisstravelandstay.com" target="_blank" class="project-link">mountainblisstravelandstay.com →</a>
      </div>

      <!-- EARTHENSHELL -->
      <div class="project-card reveal">
        <div class="project-header">
          <div style="display:flex;align-items:center;gap:14px;">
            <div class="project-icon icon-purple">🏛️</div>
            <div>
              <div class="project-name">Earthenshell</div>
              <div class="project-subtitle">Architecture Studio</div>
            </div>
          </div>
          <a href="https://earthenshell.com" target="_blank" class="project-live-badge">LIVE</a>
        </div>
        <table class="project-stack-table">
          <tr>
            <td class="stack-key">Frontend</td>
            <td class="stack-val">
              <span class="pill">React.js</span><span class="pill">Tailwind CSS</span>
            </td>
          </tr>
          <tr>
            <td class="stack-key">Animation</td>
            <td class="stack-val">
              <span class="pill">GSAP SplitText</span><span class="pill">GSAP Magnetic</span><span class="pill">GSAP Stagger</span>
            </td>
          </tr>
        </table>
        <p class="project-desc">
          The heaviest GSAP choreography in my portfolio: SplitText character-by-character heading reveals,
          magnetic cursor on project cards, staggered gallery entrances with custom easing, and
          ScrollTrigger-pinned horizontal scrollers. The site doesn't just show architecture — it performs it.
        </p>
        <a href="https://earthenshell.com" target="_blank" class="project-link">earthenshell.com →</a>
      </div>

      <!-- TRULYWEB -->
      <div class="project-card reveal">
        <div class="project-header">
          <div style="display:flex;align-items:center;gap:14px;">
            <div class="project-icon icon-green">🎨</div>
            <div>
              <div class="project-name">TrulyWeb</div>
              <div class="project-subtitle">Digital Design Agency</div>
            </div>
          </div>
          <a href="https://trulyweb.in" target="_blank" class="project-live-badge">LIVE</a>
        </div>
        <table class="project-stack-table">
          <tr>
            <td class="stack-key">Frontend</td>
            <td class="stack-val">
              <span class="pill">React.js</span><span class="pill">Tailwind CSS</span>
            </td>
          </tr>
          <tr>
            <td class="stack-key">Animation</td>
            <td class="stack-val">
              <span class="pill">GSAP</span><span class="pill">Framer Motion</span>
            </td>
          </tr>
        </table>
        <p class="project-desc">
          GSAP handles macro-level hero sequences and scroll-driven reveals. Framer Motion owns component-level
          micro-interactions — hover states, card lifts, button presses. Two libraries complementing each other:
          GSAP for the big stage, Framer for the detail. The site sells creativity through its own creativity.
        </p>
        <a href="https://trulyweb.in" target="_blank" class="project-link">trulyweb.in →</a>
      </div>

      <!-- MOTIFS -->
      <div class="project-card reveal">
        <div class="project-header">
          <div style="display:flex;align-items:center;gap:14px;">
            <div class="project-icon icon-pink">🖌️</div>
            <div>
              <div class="project-name">Motifs</div>
              <div class="project-subtitle">UI/UX & Branding Studio</div>
            </div>
          </div>
          <a href="https://motifs.in" target="_blank" class="project-live-badge">LIVE</a>
        </div>
        <table class="project-stack-table">
          <tr>
            <td class="stack-key">Frontend</td>
            <td class="stack-val">
              <span class="pill">React.js</span><span class="pill">Tailwind CSS</span>
            </td>
          </tr>
          <tr>
            <td class="stack-key">Animation</td>
            <td class="stack-val">
              <span class="pill">Framer Motion</span><span class="pill">GSAP</span>
            </td>
          </tr>
        </table>
        <p class="project-desc">
          The challenge: build a site that is itself a portfolio piece for a UI/UX studio. Framer Motion's
          layout animations handle fluid page transitions and shared element morphing. GSAP drives kinetic
          typography and hover-reactive project card distortions. Every interaction is a deliberate design statement.
        </p>
        <a href="https://motifs.in" target="_blank" class="project-link">motifs.in →</a>
      </div>

      <!-- CUREFRIEND -->
      <div class="project-card reveal">
        <div class="project-header">
          <div style="display:flex;align-items:center;gap:14px;">
            <div class="project-icon icon-sky">🏥</div>
            <div>
              <div class="project-name">CureFriend</div>
              <div class="project-subtitle">Health & Well-being Companion</div>
            </div>
          </div>
          <a href="https://curefriend.com" target="_blank" class="project-live-badge">LIVE</a>
        </div>
        <table class="project-stack-table">
          <tr>
            <td class="stack-key">Frontend</td>
            <td class="stack-val">
              <span class="pill">React.js</span><span class="pill">Tailwind CSS</span>
            </td>
          </tr>
          <tr>
            <td class="stack-key">Animation</td>
            <td class="stack-val">
              <span class="pill">GSAP</span><span class="pill">Framer Motion</span>
            </td>
          </tr>
        </table>
        <p class="project-desc">
          In a sensitive product space, I made a conscious engineering choice: calm, purposeful animation over
          spectacle. GSAP handles gentle section reveals and smooth transitions. Framer Motion drives soft page
          transitions — because the UX had to feel safe and trustworthy. Good engineering knows when not to show off.
        </p>
        <a href="https://curefriend.com" target="_blank" class="project-link">curefriend.com →</a>
      </div>

      <!-- STARTUP BIHAR -->
      <div class="project-card reveal">
        <div class="project-header">
          <div style="display:flex;align-items:center;gap:14px;">
            <div class="project-icon icon-orange">🚀</div>
            <div>
              <div class="project-name">Startup Bihar</div>
              <div class="project-subtitle">Entrepreneurship & Innovation Hub</div>
            </div>
          </div>
          <a href="https://startupbihar.in" target="_blank" class="project-live-badge">LIVE</a>
        </div>
        <table class="project-stack-table">
          <tr>
            <td class="stack-key">Frontend</td>
            <td class="stack-val">
              <span class="pill">React.js</span><span class="pill">Tailwind CSS</span><span class="pill">Framer Motion</span>
            </td>
          </tr>
          <tr>
            <td class="stack-key">Backend</td>
            <td class="stack-val">
              <span class="pill">Node.js</span><span class="pill">REST API</span>
            </td>
          </tr>
        </table>
        <p class="project-desc">
          A digital ecosystem for Bihar's entrepreneurship community — connecting founders, mentors, and resources.
          Node.js + REST API serves structured startup and event data dynamically. Framer Motion powers animated
          statistics counters and smooth section transitions that make community impact feel real and quantifiable.
        </p>
        <a href="https://startupbihar.in" target="_blank" class="project-link">startupbihar.in →</a>
      </div>

    </div><!-- /projects-grid -->
  </div>
</section>

<!-- PHILOSOPHY -->
<section class="philosophy-section" id="philosophy">
  <div class="container">
    <div class="section-label">Engineering Philosophy</div>
    <h2 class="section-title">How I <em>think</em></h2>

    <div class="philosophy-grid reveal">
      <div class="philo-card">
        <div class="philo-icon">🧠</div>
        <div class="philo-title">Systems Thinking</div>
        <div class="philo-desc">Design for scale before you need it. Every decision has downstream consequences.</div>
      </div>
      <div class="philo-card">
        <div class="philo-icon">🎬</div>
        <div class="philo-title">Animation as UX</div>
        <div class="philo-desc">Motion communicates — it doesn't decorate. Every frame must earn its place.</div>
      </div>
      <div class="philo-card">
        <div class="philo-icon">📡</div>
        <div class="philo-title">API-First Development</div>
        <div class="philo-desc">Contract-driven, versioned, documented. The contract is the product.</div>
      </div>
      <div class="philo-card">
        <div class="philo-icon">🏗️</div>
        <div class="philo-title">Clean Architecture</div>
        <div class="philo-desc">SOLID principles, separation of concerns, zero magic dependencies.</div>
      </div>
      <div class="philo-card">
        <div class="philo-icon">🐳</div>
        <div class="philo-title">DevOps Mindset</div>
        <div class="philo-desc">Ship with confidence via Docker & CI/CD. If it's not automated, it's broken.</div>
      </div>
      <div class="philo-card">
        <div class="philo-icon">🔒</div>
        <div class="philo-title">Security by Default</div>
        <div class="philo-desc">Auth, rate limiting, validation — always. Security is not a feature, it's a foundation.</div>
      </div>
      <div class="philo-card">
        <div class="philo-icon">⚡</div>
        <div class="philo-title">Performance Obsession</div>
        <div class="philo-desc">Sub-100ms APIs · 60fps UIs · lean bundles. Speed is a feature users feel.</div>
      </div>
      <div class="philo-card">
        <div class="philo-icon">🎯</div>
        <div class="philo-title">Pragmatic Engineering</div>
        <div class="philo-desc">Right tool, right scale — no over-building. Complexity must always justify itself.</div>
      </div>
    </div>

    <div class="quote-banner reveal">
      <div class="quote-text">"The best engineers I know don't just solve problems — they dissolve them."</div>
    </div>
  </div>
</section>

<!-- CONTACT -->
<section id="contact">
  <div class="container">
    <div class="section-label">Let's Connect</div>
    <h2 class="section-title">Build something <em>that matters</em></h2>

    <div class="contact-wrapper">
      <div>
        <a href="mailto:amitkrverma.k@gmail.com" class="contact-card">
          <div class="contact-icon-wrap">📧</div>
          <div>
            <div class="contact-label">Email</div>
            <div class="contact-value">amitkrverma.k@gmail.com</div>
          </div>
        </a>
        <a href="https://www.linkedin.com/in/amit-kumar-verma-50b236266/" target="_blank" class="contact-card">
          <div class="contact-icon-wrap">💼</div>
          <div>
            <div class="contact-label">LinkedIn</div>
            <div class="contact-value">Amit Kumar Verma</div>
          </div>
        </a>
        <a href="https://github.com/Amitkr-v" target="_blank" class="contact-card">
          <div class="contact-icon-wrap">🐙</div>
          <div>
            <div class="contact-label">GitHub</div>
            <div class="contact-value">@Amitkr-v</div>
          </div>
        </a>
      </div>

      <div>
        <h3 style="font-size:1.1rem; margin-bottom:12px; color:var(--muted); font-family:'DM Sans',sans-serif; font-weight:300;">Open to</h3>
        <div class="open-to">
          <span class="tag tag-blue">Full-time roles</span>
          <span class="tag tag-green">Freelance & contract</span>
          <span class="tag tag-purple">Open source</span>
          <span class="tag tag-orange">Consulting</span>
        </div>
        <p style="color:var(--muted); font-size:0.88rem; margin-top:28px; line-height:1.8;">
          I build production systems, not prototypes. If you need an engineer who sweats every
          architectural decision and ships with confidence — let's talk.
        </p>
        <div style="margin-top: 24px;">
          <a href="mailto:amitkrverma.k@gmail.com" class="btn btn-primary">Send me a message →</a>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="container">
    <p>Designed & built by <strong>Amit Kumar Verma</strong> · Bihar, India 🇮🇳</p>
    <p style="margin-top:6px; opacity:.5;">© 2026 · All rights reserved</p>
  </div>
</footer>

<script>
  // Intersection Observer for scroll reveals
  const reveals = document.querySelectorAll('.reveal');
  const observer = new IntersectionObserver((entries) => {
    entries.forEach((entry, i) => {
      if (entry.isIntersecting) {
        setTimeout(() => {
          entry.target.classList.add('visible');
        }, i * 60);
        observer.unobserve(entry.target);
      }
    });
  }, { threshold: 0.1 });

  reveals.forEach(el => observer.observe(el));

  // Stagger project cards
  const cards = document.querySelectorAll('.project-card.reveal');
  const cardObserver = new IntersectionObserver((entries) => {
    entries.forEach((entry, i) => {
      if (entry.isIntersecting) {
        setTimeout(() => {
          entry.target.classList.add('visible');
        }, i * 80);
        cardObserver.unobserve(entry.target);
      }
    });
  }, { threshold: 0.05, rootMargin: '0px 0px -40px 0px' });

  cards.forEach(el => cardObserver.observe(el));
</script>
</body>
</html>
