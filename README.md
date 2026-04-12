<!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Đàm Huy Mạnh — Automation Engineer</title>
<link href="https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&family=Syne:wght@400;600;700;800&family=Inter:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --bg: #070A12;
    --bg2: #0E1320;
    --bg3: #141926;
    --accent: #6C63FF;
    --accent2: #A78BFA;
    --accent3: #38BDF8;
    --text: #E8EAF0;
    --muted: #6B7280;
    --border: rgba(108,99,255,0.15);
    --glow: rgba(108,99,255,0.2);
  }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Inter', sans-serif;
    font-size: 15px;
    line-height: 1.7;
    overflow-x: hidden;
  }

  /* GRID BG */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(108,99,255,0.04) 1px, transparent 1px),
      linear-gradient(90deg, rgba(108,99,255,0.04) 1px, transparent 1px);
    background-size: 40px 40px;
    pointer-events: none;
    z-index: 0;
  }

  /* GLOW ORB */
  body::after {
    content: '';
    position: fixed;
    top: -200px;
    left: 50%;
    transform: translateX(-50%);
    width: 800px;
    height: 600px;
    background: radial-gradient(ellipse at center, rgba(108,99,255,0.12) 0%, transparent 70%);
    pointer-events: none;
    z-index: 0;
  }

  .container {
    max-width: 900px;
    margin: 0 auto;
    padding: 0 24px;
    position: relative;
    z-index: 1;
  }

  /* ===== HERO ===== */
  .hero {
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    text-align: center;
    padding: 80px 24px;
    position: relative;
  }

  .hero-inner { max-width: 700px; }

  .badge {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    background: rgba(108,99,255,0.1);
    border: 1px solid var(--border);
    border-radius: 100px;
    padding: 6px 16px;
    font-size: 12px;
    font-family: 'Space Mono', monospace;
    color: var(--accent2);
    margin-bottom: 32px;
    letter-spacing: 0.05em;
  }

  .badge::before {
    content: '';
    width: 6px; height: 6px;
    border-radius: 50%;
    background: #4ADE80;
    box-shadow: 0 0 8px #4ADE80;
    animation: pulse 2s infinite;
  }

  @keyframes pulse {
    0%, 100% { opacity: 1; }
    50% { opacity: 0.4; }
  }

  .hero h1 {
    font-family: 'Syne', sans-serif;
    font-size: clamp(42px, 8vw, 80px);
    font-weight: 800;
    line-height: 1.05;
    letter-spacing: -0.02em;
    margin-bottom: 8px;
  }

  .hero h1 span {
    background: linear-gradient(135deg, #6C63FF 0%, #A78BFA 50%, #38BDF8 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .hero-role {
    font-family: 'Space Mono', monospace;
    font-size: 14px;
    color: var(--muted);
    margin-bottom: 24px;
    letter-spacing: 0.08em;
  }

  .hero-role span { color: var(--accent); }

  .hero-desc {
    font-size: 16px;
    color: rgba(232,234,240,0.6);
    max-width: 480px;
    margin: 0 auto 40px;
    font-weight: 300;
  }

  .hero-cta {
    display: flex;
    gap: 12px;
    justify-content: center;
    flex-wrap: wrap;
  }

  .btn {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    padding: 12px 24px;
    border-radius: 8px;
    font-size: 14px;
    font-weight: 500;
    text-decoration: none;
    transition: all 0.2s;
    cursor: pointer;
    border: none;
  }

  .btn-primary {
    background: var(--accent);
    color: #fff;
  }
  .btn-primary:hover { background: #5752d4; transform: translateY(-2px); }

  .btn-outline {
    background: transparent;
    color: var(--text);
    border: 1px solid var(--border);
  }
  .btn-outline:hover { border-color: var(--accent); color: var(--accent); transform: translateY(-2px); }

  /* SCROLL INDICATOR */
  .scroll-hint {
    position: absolute;
    bottom: 40px;
    left: 50%;
    transform: translateX(-50%);
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 8px;
    color: var(--muted);
    font-size: 11px;
    font-family: 'Space Mono', monospace;
    letter-spacing: 0.1em;
  }

  .scroll-line {
    width: 1px;
    height: 40px;
    background: linear-gradient(to bottom, var(--accent), transparent);
    animation: scrollDown 1.5s infinite;
  }

  @keyframes scrollDown {
    0% { transform: scaleY(0); transform-origin: top; }
    50% { transform: scaleY(1); transform-origin: top; }
    51% { transform: scaleY(1); transform-origin: bottom; }
    100% { transform: scaleY(0); transform-origin: bottom; }
  }

  /* ===== SECTION ===== */
  section { padding: 100px 0; }

  .section-label {
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    color: var(--accent);
    letter-spacing: 0.2em;
    text-transform: uppercase;
    margin-bottom: 12px;
  }

  .section-title {
    font-family: 'Syne', sans-serif;
    font-size: clamp(28px, 4vw, 40px);
    font-weight: 700;
    margin-bottom: 48px;
    letter-spacing: -0.01em;
  }

  /* ===== ABOUT ===== */
  .about-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 40px;
    align-items: start;
  }

  .about-text p {
    color: rgba(232,234,240,0.7);
    margin-bottom: 16px;
    font-weight: 300;
  }

  .about-text p strong { color: var(--text); font-weight: 500; }

  .code-block {
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 12px;
    overflow: hidden;
  }

  .code-topbar {
    display: flex;
    align-items: center;
    gap: 6px;
    padding: 12px 16px;
    border-bottom: 1px solid var(--border);
    background: var(--bg3);
  }

  .dot { width: 10px; height: 10px; border-radius: 50%; }
  .dot-r { background: #FF5F57; }
  .dot-y { background: #FFBD2E; }
  .dot-g { background: #28CA41; }

  .code-filename {
    margin-left: auto;
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    color: var(--muted);
  }

  .code-body {
    padding: 20px;
    font-family: 'Space Mono', monospace;
    font-size: 12px;
    line-height: 1.9;
  }

  .c-purple { color: #C792EA; }
  .c-blue { color: #82AAFF; }
  .c-green { color: #C3E88D; }
  .c-yellow { color: #FFCB6B; }
  .c-orange { color: #F78C6C; }
  .c-muted { color: #546E7A; }

  /* ===== SKILLS ===== */
  .skills-groups {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 20px;
  }

  .skill-group {
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 24px;
    transition: border-color 0.2s, transform 0.2s;
  }

  .skill-group:hover {
    border-color: rgba(108,99,255,0.4);
    transform: translateY(-4px);
  }

  .skill-group-icon {
    width: 40px; height: 40px;
    background: rgba(108,99,255,0.1);
    border-radius: 10px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 18px;
    margin-bottom: 16px;
  }

  .skill-group-title {
    font-family: 'Syne', sans-serif;
    font-size: 14px;
    font-weight: 600;
    margin-bottom: 16px;
    color: var(--text);
    letter-spacing: 0.02em;
  }

  .skill-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
  }

  .tag {
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    padding: 4px 10px;
    border-radius: 6px;
    border: 1px solid;
    letter-spacing: 0.03em;
  }

  .tag-purple { color: #A78BFA; border-color: rgba(167,139,250,0.25); background: rgba(167,139,250,0.06); }
  .tag-blue { color: #60A5FA; border-color: rgba(96,165,250,0.25); background: rgba(96,165,250,0.06); }
  .tag-teal { color: #34D399; border-color: rgba(52,211,153,0.25); background: rgba(52,211,153,0.06); }
  .tag-orange { color: #FB923C; border-color: rgba(251,146,60,0.25); background: rgba(251,146,60,0.06); }

  /* ===== STATS ===== */
  .stats-row {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 16px;
    margin-bottom: 60px;
  }

  .stat-card {
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 24px 20px;
    text-align: center;
    transition: border-color 0.2s;
  }

  .stat-card:hover { border-color: rgba(108,99,255,0.4); }

  .stat-num {
    font-family: 'Syne', sans-serif;
    font-size: 32px;
    font-weight: 800;
    background: linear-gradient(135deg, #6C63FF, #A78BFA);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    line-height: 1;
    margin-bottom: 8px;
  }

  .stat-label {
    font-size: 12px;
    color: var(--muted);
    font-family: 'Space Mono', monospace;
    letter-spacing: 0.05em;
  }

  /* ===== CONNECT ===== */
  .connect-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 16px;
  }

  .social-card {
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 28px 24px;
    text-decoration: none;
    color: var(--text);
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 12px;
    transition: all 0.2s;
    text-align: center;
  }

  .social-card:hover {
    border-color: rgba(108,99,255,0.5);
    transform: translateY(-6px);
    background: rgba(108,99,255,0.08);
  }

  .social-icon {
    width: 52px; height: 52px;
    border-radius: 14px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 24px;
  }

  .social-name {
    font-family: 'Syne', sans-serif;
    font-size: 15px;
    font-weight: 600;
  }

  .social-handle { font-size: 13px; color: var(--muted); font-family: 'Space Mono', monospace; }

  /* ===== FOOTER ===== */
  footer {
    border-top: 1px solid var(--border);
    padding: 40px 0;
    text-align: center;
    color: var(--muted);
    font-size: 13px;
    font-family: 'Space Mono', monospace;
  }

  footer span { color: var(--accent); }

  /* ===== DIVIDER ===== */
  .divider {
    height: 1px;
    background: linear-gradient(to right, transparent, var(--border), transparent);
    margin: 0;
  }

  .c-text { color: #E8EAF0; }

  .tab-btn {
    background: transparent;
    border: 1px solid transparent;
    border-radius: 6px;
    color: var(--muted);
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    padding: 4px 10px;
    cursor: pointer;
    transition: all 0.15s;
    letter-spacing: 0.03em;
  }
  .tab-btn:hover { color: var(--text); }
  .tab-btn.active {
    background: rgba(108,99,255,0.15);
    border-color: rgba(108,99,255,0.3);
    color: var(--accent2);
  }
  .fade-up {
    opacity: 0;
    transform: translateY(30px);
    transition: opacity 0.6s, transform 0.6s;
  }
  .fade-up.visible { opacity: 1; transform: translateY(0); }

  @media (max-width: 700px) {
    .about-grid, .skills-groups { grid-template-columns: 1fr; }
    .stats-row { grid-template-columns: repeat(2, 1fr); }
    .connect-grid { grid-template-columns: 1fr; }
  }
</style>
</head>
<body>

<!-- HERO -->
<section class="hero">
  <div class="hero-inner">
    <div class="badge">available for work</div>
    <h1>Đàm Huy<br><span>Mạnh</span></h1>
    <p class="hero-role"><span>Automation Engineer</span> &amp; Backend Developer</p>
    <p class="hero-desc">
      Sinh viên HUFLIT — đam mê automation testing, web scraping và backend development. Ngu nhiều code ít, nhưng code là chất! 🔥
    </p>
    <div class="hero-cta">
      <a href="https://github.com/DamHuyManh" class="btn btn-primary">
        <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor"><path d="M12 0C5.37 0 0 5.37 0 12c0 5.31 3.435 9.795 8.205 11.385.6.105.825-.255.825-.57 0-.285-.015-1.23-.015-2.235-3.015.555-3.795-.735-4.035-1.41-.135-.345-.72-1.41-1.23-1.695-.42-.225-1.02-.78-.015-.795.945-.015 1.62.87 1.845 1.23 1.08 1.815 2.805 1.305 3.495.99.105-.78.42-1.305.765-1.605-2.67-.3-5.46-1.335-5.46-5.925 0-1.305.465-2.385 1.23-3.225-.12-.3-.54-1.53.12-3.18 0 0 1.005-.315 3.3 1.23.96-.27 1.98-.405 3-.405s2.04.135 3 .405c2.295-1.56 3.3-1.23 3.3-1.23.66 1.65.24 2.88.12 3.18.765.84 1.23 1.905 1.23 3.225 0 4.605-2.805 5.625-5.475 5.925.435.375.81 1.095.81 2.22 0 1.605-.015 2.895-.015 3.3 0 .315.225.69.825.57A12.02 12.02 0 0024 12c0-6.63-5.37-12-12-12z"/></svg>
        GitHub
      </a>
      <a href="https://www.facebook.com/md.fpoi" class="btn btn-outline">
        Facebook
      </a>
    </div>
  </div>
  <div class="scroll-hint">
    <span>scroll</span>
    <div class="scroll-line"></div>
  </div>
</section>

<div class="divider"></div>

<!-- ABOUT -->
<section>
  <div class="container fade-up">
    <p class="section-label">// 01 — about</p>
    <h2 class="section-title">Xin chào! 👋</h2>
    <div class="about-grid">
      <div class="about-text">
        <p>Mình là <strong>Đàm Huy Mạnh</strong>, sinh viên tại <strong>HUFLIT – ĐH Ngoại ngữ Tin học TP.HCM</strong>.</p>
        <p>Mình chuyên về <strong>Automation Testing</strong> và <strong>Backend Development</strong> — từ viết script Selenium/Appium cho đến xây dựng API và làm việc với database.</p>
        <p>Motto của mình: <em style="color: var(--accent2);">"Ngu nhiều code ít, nhưng code là chất!"</em> — không biết thì học, biết rồi thì build thôi.</p>
        <p>Hiện đang tìm kiếm cơ hội thực tập / junior position trong lĩnh vực automation hoặc backend.</p>
      </div>
      <div class="code-block">
        <div class="code-topbar">
          <div class="dot dot-r"></div>
          <div class="dot dot-y"></div>
          <div class="dot dot-g"></div>
          <div style="display:flex;gap:4px;margin-left:12px;">
            <button class="tab-btn active" onclick="switchTab('py')" id="tab-py">profile.py</button>
            <button class="tab-btn" onclick="switchTab('cs')" id="tab-cs">Profile.cs</button>
          </div>
        </div>

        <!-- PYTHON -->
        <div class="code-body" id="code-py">
<span class="c-muted"># Automation Engineer & Backend Dev</span><br>
<br>
<span class="c-purple">class</span> <span class="c-blue">DamHuyManh</span>:<br>
<br>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-purple">def</span> <span class="c-yellow">__init__</span>(<span class="c-orange">self</span>):<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-orange">self</span>.<span class="c-text">name</span>   <span class="c-muted">=</span> <span class="c-green">"Đàm Huy Mạnh"</span><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-orange">self</span>.<span class="c-text">school</span> <span class="c-muted">=</span> <span class="c-green">"HUFLIT"</span><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-orange">self</span>.<span class="c-text">role</span>   <span class="c-muted">=</span> [<span class="c-green">"Automation Eng"</span>, <span class="c-green">"Backend Dev"</span>]<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-orange">self</span>.<span class="c-text">motto</span>  <span class="c-muted">=</span> <span class="c-green">"Ngu nhiều code ít, nhưng code là chất 🔥"</span><br>
<br>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-purple">def</span> <span class="c-yellow">get_skills</span>(<span class="c-orange">self</span>) <span class="c-muted">-></span> <span class="c-blue">dict</span>:<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-purple">return</span> {<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-green">"languages"</span>  <span class="c-muted">:</span> [<span class="c-green">"C#"</span>, <span class="c-green">"Java"</span>, <span class="c-green">"PHP"</span>, <span class="c-green">"Python"</span>],<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-green">"automation"</span> <span class="c-muted">:</span> [<span class="c-green">"Selenium"</span>, <span class="c-green">"Appium"</span>, <span class="c-green">"ADB"</span>, <span class="c-green">"ATX"</span>],<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-green">"databases"</span>  <span class="c-muted">:</span> [<span class="c-green">"SQL Server"</span>, <span class="c-green">"MySQL"</span>, <span class="c-green">"MongoDB"</span>],<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}<br>
<br>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-purple">def</span> <span class="c-yellow">contact</span>(<span class="c-orange">self</span>) <span class="c-muted">-></span> <span class="c-blue">dict</span>:<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-purple">return</span> {<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-green">"facebook"</span> <span class="c-muted">:</span> <span class="c-green">"md.fpoi"</span>,<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-green">"tiktok"</span>  <span class="c-muted">:</span> <span class="c-green">"ngu.nhieu.code.it"</span>,<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}<br>
        </div>

        <!-- C# -->
        <div class="code-body" id="code-cs" style="display:none">
<span class="c-muted">// Automation Engineer & Backend Dev</span><br>
<br>
<span class="c-purple">public class</span> <span class="c-blue">DamHuyManh</span><br>
{<br>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-muted">// Properties</span><br>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-purple">public string</span> <span class="c-text">Name</span>   { <span class="c-purple">get</span>; } <span class="c-muted">=</span> <span class="c-green">"Đàm Huy Mạnh"</span>;<br>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-purple">public string</span> <span class="c-text">School</span> { <span class="c-purple">get</span>; } <span class="c-muted">=</span> <span class="c-green">"HUFLIT"</span>;<br>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-purple">public string</span> <span class="c-text">Motto</span>  { <span class="c-purple">get</span>; } <span class="c-muted">=</span> <span class="c-green">"Code là chất 🔥"</span>;<br>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-purple">public string[]</span> <span class="c-text">Role</span>  { <span class="c-purple">get</span>; } <span class="c-muted">=</span> { <span class="c-green">"Automation Eng"</span>, <span class="c-green">"Backend Dev"</span> };<br>
<br>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-muted">// Methods</span><br>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-purple">public</span> <span class="c-blue">Dictionary</span>&lt;<span class="c-purple">string</span>, <span class="c-purple">string[]</span>&gt; <span class="c-yellow">GetSkills</span>()<br>
&nbsp;&nbsp;&nbsp;&nbsp;{<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-purple">return new</span> ()<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{ <span class="c-green">"Languages"</span>  , [<span class="c-green">"C#"</span>, <span class="c-green">"Java"</span>, <span class="c-green">"PHP"</span>, <span class="c-green">"Python"</span>] },<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{ <span class="c-green">"Automation"</span> , [<span class="c-green">"Selenium"</span>, <span class="c-green">"Appium"</span>, <span class="c-green">"ADB"</span>] },<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{ <span class="c-green">"Databases"</span>  , [<span class="c-green">"SQL Server"</span>, <span class="c-green">"MySQL"</span>, <span class="c-green">"MongoDB"</span>] },<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;};<br>
&nbsp;&nbsp;&nbsp;&nbsp;}<br>
<br>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-purple">public</span> <span class="c-blue">Dictionary</span>&lt;<span class="c-purple">string</span>, <span class="c-purple">string</span>&gt; <span class="c-yellow">Contact</span>()<br>
&nbsp;&nbsp;&nbsp;&nbsp;{<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-purple">return new</span> ()<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{ <span class="c-green">"Facebook"</span> , <span class="c-green">"md.fpoi"</span> },<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{ <span class="c-green">"TikTok"</span>  , <span class="c-green">"ngu.nhieu.code.it"</span> },<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;};<br>
&nbsp;&nbsp;&nbsp;&nbsp;}<br>
}<br>
        </div>
      </div>
    </div>
  </div>
</section>

<div class="divider"></div>

<!-- SKILLS -->
<section>
  <div class="container fade-up">
    <p class="section-label">// 02 — tech stack</p>
    <h2 class="section-title">Kỹ năng & Công nghệ</h2>
    <div class="skills-groups">

      <div class="skill-group">
        <div class="skill-group-icon">💻</div>
        <div class="skill-group-title">Languages</div>
        <div class="skill-tags">
          <span class="tag tag-purple">C#</span>
          <span class="tag tag-purple">Java</span>
          <span class="tag tag-purple">PHP</span>
          <span class="tag tag-purple">Python</span>
        </div>
      </div>

      <div class="skill-group">
        <div class="skill-group-icon">🤖</div>
        <div class="skill-group-title">Automation & Testing</div>
        <div class="skill-tags">
          <span class="tag tag-teal">Selenium</span>
          <span class="tag tag-teal">Appium</span>
          <span class="tag tag-teal">ADB</span>
          <span class="tag tag-teal">ATX</span>
          <span class="tag tag-teal">Requests</span>
        </div>
      </div>

      <div class="skill-group">
        <div class="skill-group-icon">🗄️</div>
        <div class="skill-group-title">Databases</div>
        <div class="skill-tags">
          <span class="tag tag-blue">SQL Server</span>
          <span class="tag tag-blue">MySQL</span>
          <span class="tag tag-blue">MongoDB</span>
        </div>
      </div>

      <div class="skill-group">
        <div class="skill-group-icon">🔧</div>
        <div class="skill-group-title">Tools & Design</div>
        <div class="skill-tags">
          <span class="tag tag-orange">Git</span>
          <span class="tag tag-orange">Figma</span>
          <span class="tag tag-orange">VS Code</span>
        </div>
      </div>

    </div>
  </div>
</section>

<div class="divider"></div>

<!-- STATS -->
<section>
  <div class="container fade-up">
    <p class="section-label">// 03 — github stats</p>
    <h2 class="section-title">Hoạt động</h2>
    <div class="stats-row">
      <div class="stat-card">
        <div class="stat-num">4+</div>
        <div class="stat-label">languages</div>
      </div>
      <div class="stat-card">
        <div class="stat-num">5+</div>
        <div class="stat-label">automation tools</div>
      </div>
      <div class="stat-card">
        <div class="stat-num">3</div>
        <div class="stat-label">databases</div>
      </div>
      <div class="stat-card">
        <div class="stat-num">∞</div>
        <div class="stat-label">đang học</div>
      </div>
    </div>
    <div style="background: var(--bg2); border: 1px solid var(--border); border-radius: 12px; padding: 24px; text-align: center;">
      <p style="color: var(--muted); font-family: 'Space Mono', monospace; font-size: 13px; margin-bottom: 12px;">// github activity</p>
      <img src="https://github-readme-stats.vercel.app/api?username=DamHuyManh&show_icons=true&theme=tokyonight&hide_border=true&bg_color=0E1320&title_color=6C63FF&icon_color=6C63FF&text_color=C9D1D9" style="max-width: 100%; border-radius: 8px;" alt="GitHub Stats" onerror="this.style.display='none'"/>
    </div>
  </div>
</section>

<div class="divider"></div>

<!-- CONNECT -->
<section>
  <div class="container fade-up">
    <p class="section-label">// 04 — connect</p>
    <h2 class="section-title">Liên hệ</h2>
    <div class="connect-grid">

      <a href="https://github.com/DamHuyManh" class="social-card">
        <div class="social-icon" style="background: rgba(255,255,255,0.05);">
          <svg width="28" height="28" viewBox="0 0 24 24" fill="#e8eaf0"><path d="M12 0C5.37 0 0 5.37 0 12c0 5.31 3.435 9.795 8.205 11.385.6.105.825-.255.825-.57 0-.285-.015-1.23-.015-2.235-3.015.555-3.795-.735-4.035-1.41-.135-.345-.72-1.41-1.23-1.695-.42-.225-1.02-.78-.015-.795.945-.015 1.62.87 1.845 1.23 1.08 1.815 2.805 1.305 3.495.99.105-.78.42-1.305.765-1.605-2.67-.3-5.46-1.335-5.46-5.925 0-1.305.465-2.385 1.23-3.225-.12-.3-.54-1.53.12-3.18 0 0 1.005-.315 3.3 1.23.96-.27 1.98-.405 3-.405s2.04.135 3 .405c2.295-1.56 3.3-1.23 3.3-1.23.66 1.65.24 2.88.12 3.18.765.84 1.23 1.905 1.23 3.225 0 4.605-2.805 5.625-5.475 5.925.435.375.81 1.095.81 2.22 0 1.605-.015 2.895-.015 3.3 0 .315.225.69.825.57A12.02 12.02 0 0024 12c0-6.63-5.37-12-12-12z"/></svg>
        </div>
        <div class="social-name">GitHub</div>
        <div class="social-handle">@DamHuyManh</div>
      </a>

      <a href="https://www.facebook.com/md.fpoi" class="social-card">
        <div class="social-icon" style="background: rgba(24,119,242,0.1);">
          <svg width="28" height="28" viewBox="0 0 24 24" fill="#1877F2"><path d="M24 12.073C24 5.41 18.627 0 12 0S0 5.41 0 12.073C0 18.1 4.388 23.094 10.125 24v-8.437H7.078v-3.49h3.047V9.41c0-3.025 1.792-4.697 4.533-4.697 1.312 0 2.686.236 2.686.236v2.97h-1.513c-1.491 0-1.956.932-1.956 1.886v2.269h3.328l-.532 3.49h-2.796V24C19.612 23.094 24 18.1 24 12.073z"/></svg>
        </div>
        <div class="social-name">Facebook</div>
        <div class="social-handle">md.fpoi</div>
      </a>

      <a href="https://www.tiktok.com/@ngu.nhieu.code.it" class="social-card">
        <div class="social-icon" style="background: rgba(255,255,255,0.05);">
          <svg width="28" height="28" viewBox="0 0 24 24" fill="#e8eaf0"><path d="M12.525.02c1.31-.02 2.61-.01 3.91-.02.08 1.53.63 3.09 1.75 4.17 1.12 1.11 2.7 1.62 4.24 1.79v4.03c-1.44-.05-2.89-.35-4.2-.97-.57-.26-1.1-.59-1.62-.93-.01 2.92.01 5.84-.02 8.75-.08 1.4-.54 2.79-1.35 3.94-1.31 1.92-3.58 3.17-5.91 3.21-1.43.08-2.86-.31-4.08-1.03-2.02-1.19-3.44-3.37-3.65-5.71-.02-.5-.03-1-.01-1.49.18-1.9 1.12-3.72 2.58-4.96 1.66-1.44 3.98-2.13 6.15-1.72.02 1.48-.04 2.96-.04 4.44-.99-.32-2.15-.23-3.02.37-.63.41-1.11 1.04-1.36 1.75-.21.51-.15 1.07-.14 1.61.24 1.64 1.82 3.02 3.5 2.87 1.12-.01 2.19-.66 2.77-1.61.19-.33.4-.67.41-1.06.1-1.79.06-3.57.07-5.36.01-4.03-.01-8.05.02-12.07z"/></svg>
        </div>
        <div class="social-name">TikTok</div>
        <div class="social-handle">@ngu.nhieu.code.it</div>
      </a>

    </div>
  </div>
</section>

<footer>
  <div class="container">
    <p>made with <span>♥</span> by <span>DamHuyManh</span> · 2025</p>
    <p style="margin-top:8px; font-size:11px; opacity:0.5;">HUFLIT · Automation Engineer · Backend Dev</p>
  </div>
</footer>

<script>
  function switchTab(lang) {
    document.getElementById('code-py').style.display = lang === 'py' ? 'block' : 'none';
    document.getElementById('code-cs').style.display = lang === 'cs' ? 'block' : 'none';
    document.getElementById('tab-py').classList.toggle('active', lang === 'py');
    document.getElementById('tab-cs').classList.toggle('active', lang === 'cs');
  }

  const observer = new IntersectionObserver((entries) => {
    entries.forEach(e => {
      if (e.isIntersecting) {
        e.target.classList.add('visible');
        observer.unobserve(e.target);
      }
    });
  }, { threshold: 0.15 });

  document.querySelectorAll('.fade-up').forEach(el => observer.observe(el));
</script>
</body>
</html>
