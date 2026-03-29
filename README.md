[deepveer_resume (2).html](https://github.com/user-attachments/files/26332750/deepveer_resume.2.html)
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Deepveer — Resume</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=DM+Mono:ital,wght@0,300;0,400;0,500;1,300&family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;1,300&display=swap" rel="stylesheet">
<style>
  :root {
    --bg:       #131217;
    --surface:  #1A1820;
    --border:   #32243A;
    --maroon:   #C4193A;
    --lilac:    #C89FE8;
    --text:     #EDE5F5;
    --muted:    #8A7A96;
    --white:    #F8F2FF;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'DM Mono', monospace;
    font-size: 11px;
    line-height: 1.65;
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: flex-start;
    padding: 40px 20px;
    position: relative;
  }

  #matrix-canvas {
    position: fixed;
    top: 0; left: 0;
    width: 100%; height: 100%;
    z-index: 0;
    opacity: 0.18;
    pointer-events: none;
  }

  .page {
    position: relative;
    z-index: 1;
  }

  .page {
    width: 794px;
    min-height: 1123px;
    background: linear-gradient(135deg, #161419 0%, #131217 50%, #131319 100%);
    border: 1px solid var(--border);
    box-shadow: 0 0 0 1px rgba(196,25,58,0.08), inset 0 0 80px rgba(200,159,232,0.02);
    position: relative;
    overflow: hidden;
  }

  .corner { position: absolute; width: 20px; height: 20px; border-color: var(--maroon); border-style: solid; z-index: 10; }
  .corner.tl { top: 14px; left: 14px; border-width: 1px 0 0 1px; }
  .corner.tr { top: 14px; right: 14px; border-width: 1px 1px 0 0; }
  .corner.bl { bottom: 14px; left: 14px; border-width: 0 0 1px 1px; }
  .corner.br { bottom: 14px; right: 14px; border-width: 0 1px 1px 0; }

  /* ── HEADER ── */
  .header {
    padding: 44px 48px 32px;
    border-bottom: 1px solid var(--border);
    display: grid;
    grid-template-columns: 1fr auto;
    align-items: end;
    gap: 20px;
    position: relative;
    z-index: 1;
  }

  .header-glow {
    position: absolute;
    top: 0; left: 0;
    width: 360px; height: 180px;
    background: radial-gradient(ellipse at 25% 55%, rgba(196,25,58,0.15) 0%, transparent 70%);
    pointer-events: none;
  }

  .header-accent {
    position: absolute;
    bottom: -1px; left: 48px;
    width: 64px; height: 2px;
    background: var(--maroon);
    box-shadow: 0 0 10px rgba(196,25,58,0.6);
  }

  .label-row {
    display: flex;
    align-items: center;
    gap: 14px;
    margin-bottom: 6px;
  }

  .label-tag {
    font-size: 9px;
    letter-spacing: 0.22em;
    text-transform: uppercase;
    color: var(--maroon);
    border: 1px solid var(--maroon);
    padding: 2px 8px;
    line-height: 1.8;
  }

  .alias {
    font-size: 9px;
    letter-spacing: 0.18em;
    text-transform: uppercase;
    color: var(--lilac);
    opacity: 0.85;
  }

  .name {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 82px;
    letter-spacing: 0.04em;
    line-height: 0.88;
    color: var(--white);
  }
  .name span { color: var(--maroon); }

  .tagline {
    font-family: 'Cormorant Garamond', serif;
    font-style: italic;
    font-size: 13px;
    color: var(--muted);
    margin-top: 10px;
    letter-spacing: 0.03em;
  }

  .contact-block { text-align: right; }

  .contact-block a,
  .contact-block p {
    display: block;
    font-size: 9px;
    color: var(--muted);
    text-decoration: none;
    letter-spacing: 0.06em;
    line-height: 2;
  }

  .contact-block a:hover { color: var(--lilac); }
  .contact-block .hi { color: var(--lilac); font-size: 9.5px; margin-bottom: 2px; }

  /* ── BODY GRID ── */
  .body {
    display: grid;
    grid-template-columns: 218px 1fr;
    min-height: calc(1123px - 178px);
    position: relative;
    z-index: 1;
  }

  /* ── SIDEBAR ── */
  .sidebar {
    border-right: 1px solid var(--border);
    padding: 30px 26px;
    background: linear-gradient(175deg, rgba(196,25,58,0.04) 0%, transparent 40%, rgba(200,159,232,0.03) 100%);
  }

  .s-section { margin-bottom: 28px; }

  .s-title {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 10.5px;
    letter-spacing: 0.3em;
    color: var(--maroon);
    margin-bottom: 14px;
    display: flex;
    align-items: center;
    gap: 8px;
  }

  .s-title::after {
    content: '';
    flex: 1;
    height: 1px;
    background: var(--border);
  }

  .skill-item { margin-bottom: 11px; }

  .skill-name {
    font-size: 9.5px;
    color: var(--text);
    letter-spacing: 0.05em;
    margin-bottom: 4px;
    display: flex;
    justify-content: space-between;
  }
  .skill-name span { color: var(--muted); font-size: 8px; }

  .skill-bar {
    height: 2px;
    background: var(--border);
    position: relative;
  }

  .skill-fill {
    position: absolute;
    top: 0; left: 0;
    height: 100%;
    background: linear-gradient(90deg, var(--maroon), var(--lilac));
    box-shadow: 0 0 7px rgba(196,25,58,0.55);
  }

  .tool-grid { display: flex; flex-wrap: wrap; gap: 6px; }

  .tool-tag {
    font-size: 8.5px;
    letter-spacing: 0.07em;
    color: var(--lilac);
    border: 1px solid var(--border);
    padding: 3px 8px;
    background: var(--surface);
  }

  .stat-row {
    display: flex;
    justify-content: space-between;
    align-items: baseline;
    padding: 7px 0;
    border-bottom: 1px solid var(--border);
  }
  .stat-row:last-child { border-bottom: none; }

  .stat-label {
    font-size: 8.5px;
    color: var(--muted);
    letter-spacing: 0.08em;
    text-transform: uppercase;
  }

  .stat-value {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 17px;
    color: var(--white);
    letter-spacing: 0.04em;
  }

  .stat-unit {
    font-family: 'DM Mono', monospace;
    font-size: 8px;
    color: var(--maroon);
    margin-left: 2px;
  }

  /* ── MAIN ── */
  .main {
    padding: 30px 36px 30px 30px;
    display: flex;
    flex-direction: column;
    background: linear-gradient(210deg, rgba(200,159,232,0.05) 0%, transparent 35%);
  }

  .m-section { margin-bottom: 24px; }

  .m-title {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 10.5px;
    letter-spacing: 0.3em;
    color: var(--maroon);
    margin-bottom: 16px;
    display: flex;
    align-items: center;
    gap: 10px;
  }
  .m-title::after {
    content: '';
    flex: 1;
    height: 1px;
    background: var(--border);
  }

  .entry {
    margin-bottom: 16px;
    padding-left: 14px;
    border-left: 2px solid transparent;
    border-image: linear-gradient(180deg, var(--maroon) 0%, var(--border) 60%, transparent 100%) 1;
    position: relative;
  }

  .entry::before {
    content: '';
    position: absolute;
    left: -4px; top: 7px;
    width: 5px; height: 5px;
    background: var(--maroon);
    box-shadow: 0 0 7px rgba(196,25,58,0.8);
  }

  .entry-header {
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
    margin-bottom: 2px;
  }

  .entry-title {
    font-family: 'Cormorant Garamond', serif;
    font-size: 14px;
    font-weight: 600;
    color: var(--white);
    letter-spacing: 0.02em;
    line-height: 1.2;
  }

  .entry-date {
    font-size: 8.5px;
    color: var(--muted);
    letter-spacing: 0.1em;
    text-transform: uppercase;
    white-space: nowrap;
    margin-left: 12px;
    padding-top: 2px;
  }

  .entry-sub {
    font-size: 8.5px;
    color: var(--lilac);
    letter-spacing: 0.09em;
    margin-bottom: 6px;
    opacity: 0.9;
  }

  .entry-body {
    font-size: 9.5px;
    color: var(--muted);
    line-height: 1.7;
  }

  .entry-body li {
    list-style: none;
    padding-left: 12px;
    position: relative;
    margin-bottom: 2px;
  }

  .entry-body li::before {
    content: '—';
    position: absolute;
    left: 0;
    color: var(--maroon);
    font-size: 8px;
    top: 1px;
  }

  .hl { color: var(--text); }

  .footnote {
    margin-top: auto;
    padding-top: 18px;
    border-top: 1px solid var(--border);
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .fn-text {
    font-size: 8px;
    color: var(--muted);
    letter-spacing: 0.1em;
    text-transform: uppercase;
  }

  .fn-mark {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 13px;
    color: var(--maroon);
    letter-spacing: 0.22em;
  }

  @media print {
    body { background: var(--bg); padding: 0; }
    .page { width: 100%; border: none; }
  }
</style>
</head>
<body>
<div class="page">
  <div class="corner tl"></div>
  <div class="corner tr"></div>
  <div class="corner bl"></div>
  <div class="corner br"></div>

  <!-- HEADER -->
  <div class="header">
    <div class="header-glow"></div>
    <div class="name-block">
      <div class="label-row">
        <span class="label-tag">3D Generalist · Tech Artist</span>
        <span class="alias">D5 / Cube</span>
      </div>
      <div class="name">DEEP<span>VEER</span></div>
      <div class="tagline">Crafting worlds frame by frame — from raw mesh to final cut.</div>
    </div>
    <div class="contact-block">
      <p class="hi">India · Remote</p>
      <a href="https://github.com/CubingFun7">github.com/CubingFun7</a>
      <a href="https://www.instagram.com/deepveer.singh_3d/">instagram / deepveer.singh_3d</a>
      <a href="https://not-cube.itch.io">not-cube.itch.io</a>
      <p style="margin-top:6px;">Available for freelance · Worldwide</p>
    </div>
    <div class="header-accent"></div>
  </div>

  <!-- BODY -->
  <div class="body">

    <!-- SIDEBAR -->
    <div class="sidebar">

      <div class="s-section">
        <div class="s-title">Core Skills</div>
        <div class="skill-item">
          <div class="skill-name">Blender 3D <span>~4,000 hrs</span></div>
          <div class="skill-bar"><div class="skill-fill" style="width:96%"></div></div>
        </div>
        <div class="skill-item">
          <div class="skill-name">Shading & Rendering <span>EEVEE · Cycles</span></div>
          <div class="skill-bar"><div class="skill-fill" style="width:90%"></div></div>
        </div>
        <div class="skill-item">
          <div class="skill-name">Hard Surface Modelling</div>
          <div class="skill-bar"><div class="skill-fill" style="width:87%"></div></div>
        </div>
        <div class="skill-item">
          <div class="skill-name">Lighting & Cinematography</div>
          <div class="skill-bar"><div class="skill-fill" style="width:88%"></div></div>
        </div>
        <div class="skill-item">
          <div class="skill-name">Rigging & Animation</div>
          <div class="skill-bar"><div class="skill-fill" style="width:78%"></div></div>
        </div>
        <div class="skill-item">
          <div class="skill-name">DaVinci Resolve</div>
          <div class="skill-bar"><div class="skill-fill" style="width:82%"></div></div>
        </div>
        <div class="skill-item">
          <div class="skill-name">Procedural Shading</div>
          <div class="skill-bar"><div class="skill-fill" style="width:85%"></div></div>
        </div>
      </div>

      <div class="s-section">
        <div class="s-title">Tools</div>
        <div class="tool-grid">
          <span class="tool-tag">Blender</span>
          <span class="tool-tag">DaVinci Resolve</span>
          <span class="tool-tag">Adobe CC</span>
          <span class="tool-tag">Unreal Engine</span>
          <span class="tool-tag">Unity</span>
          <span class="tool-tag">Godot</span>
          <span class="tool-tag">Pepakura</span>
          <span class="tool-tag">Python (Blender API)</span>
        </div>
      </div>

      <div class="s-section">
        <div class="s-title">Expertise</div>
        <div class="tool-grid">
          <span class="tool-tag">Cinematic Lighting</span>
          <span class="tool-tag">Hard Surface</span>
          <span class="tool-tag">Colour Grading</span>
          <span class="tool-tag">Motion Graphics</span>
          <span class="tool-tag">3D for Games</span>
          <span class="tool-tag">Product Vis.</span>
          <span class="tool-tag">Social Media</span>
          <span class="tool-tag">Director's Vision</span>
        </div>
      </div>

      <div class="s-section">
        <div class="s-title">By the Numbers</div>
        <div class="stat-row">
          <span class="stat-label">Blender hours</span>
          <span class="stat-value">4K<span class="stat-unit">+</span></span>
        </div>
        <div class="stat-row">
          <span class="stat-label">Years practice</span>
          <span class="stat-value">3<span class="stat-unit">+</span></span>
        </div>
        <div class="stat-row">
          <span class="stat-label">Freelance earned</span>
          <span class="stat-value">$350<span class="stat-unit">+</span></span>
        </div>
        <div class="stat-row">
          <span class="stat-label">Active since</span>
          <span class="stat-value">2021</span>
        </div>
      </div>

    </div>

    <!-- MAIN -->
    <div class="main">

      <!-- EXPERIENCE -->
      <div class="m-section">
        <div class="m-title">Experience</div>

        <div class="entry">
          <div class="entry-header">
            <div class="entry-title">Citadel Immigration Services</div>
            <div class="entry-date">2026 — Present</div>
          </div>
          <div class="entry-sub">Creative Contractor · Social Media & Video Production</div>
          <ul class="entry-body">
            <li>End-to-end reel production: brief → colour grade in <span class="hl">DaVinci Resolve</span> → final delivery</li>
            <li>Designed social media thumbnails and promotional posters via <span class="hl">Adobe CC</span></li>
            <li>Sole creative resource; managed content calendar and client communication directly</li>
          </ul>
        </div>

        <div class="entry">
          <div class="entry-header">
            <div class="entry-title">Pehnava — Family Brand</div>
            <div class="entry-date">2025 — Present</div>
          </div>
          <div class="entry-sub">Brand Lead · Instagram & Content Strategy</div>
          <ul class="entry-body">
            <li>Built brand identity from scratch — logo, palette, photography direction</li>
            <li>Managed all Instagram content, publishing strategy, and audience growth</li>
          </ul>
        </div>

        <div class="entry">
          <div class="entry-header">
            <div class="entry-title">Fiverr — Freelance 3D & Video</div>
            <div class="entry-date">2024 — Present</div>
          </div>
          <div class="entry-sub">Independent · 3D Visualisation · Motion · Editing</div>
          <ul class="entry-body">
            <li>Delivered 3D renders and video edits to international clients; <span class="hl">$350+ earned</span> independently</li>
            <li>Managed briefs, revisions, and delivery end-to-end as a solo operator</li>
          </ul>
        </div>
      </div>

      <!-- PROJECTS -->
      <div class="m-section">
        <div class="m-title">Notable Projects</div>

        <div class="entry">
          <div class="entry-header">
            <div class="entry-title">Cinematic Knife Showreel</div>
            <div class="entry-date">2026 — WIP</div>
          </div>
          <div class="entry-sub">Blender · EEVEE · Procedural Shading · Cinematography</div>
          <ul class="entry-body">
            <li>36+ hours in; custom <span class="hl">damascus steel shader</span> + acrylic body, three-shot emotional arc</li>
            <li>VRAM-constrained pipeline (4GB): 720p renders upscaled to 2K via AI</li>
          </ul>
        </div>

        <div class="entry">
          <div class="entry-header">
            <div class="entry-title">V1 D R O W N I N G. vol4</div>
            <div class="entry-date">2025</div>
          </div>
          <div class="entry-sub">Blender · Fan Cinematic · ULTRAKILL</div>
          <ul class="entry-body">
            <li>Full 3D cinematic based on ULTRAKILL's V1; scene composition, lighting, character animation</li>
            <li>Demonstrates narrative direction and atmospheric world-building in a character-driven piece</li>
          </ul>
        </div>

        <div class="entry">
          <div class="entry-header">
            <div class="entry-title">F1 Concept Ring Showcase</div>
            <div class="entry-date">2025</div>
          </div>
          <div class="entry-sub">Blender · Product Visualisation · Cinematic Rendering</div>
          <ul class="entry-body">
            <li>Concept product render of an F1-inspired ring — studio lighting rig, precise material work</li>
            <li>Showcases capability for jewellery and luxury goods product visualisation</li>
          </ul>
        </div>

        <div class="entry">
          <div class="entry-header">
            <div class="entry-title">Mining Light — Game Jam</div>
            <div class="entry-date">2024</div>
          </div>
          <div class="entry-sub">Unreal Engine · 3D Environment Art · pocketpainter.itch.io/mining-light</div>
          <ul class="entry-body">
            <li>Environment art and 3D assets for a jam submission built in Unreal Engine</li>
            <li>Shipped a complete playable build; executed under competitive time constraints</li>
          </ul>
        </div>
      </div>

      <!-- EDUCATION -->
      <div class="m-section">
        <div class="m-title">Education</div>
        <div class="entry">
          <div class="entry-header">
            <div class="entry-title">ICSE — Grade 10</div>
            <div class="entry-date">2026 — 2027</div>
          </div>
          <div class="entry-sub">India · Entirely self-taught across all creative disciplines</div>
          <ul class="entry-body">
            <li>Full academic load alongside active freelance practice — no formal art or media school</li>
          </ul>
        </div>
      </div>

      <!-- FOOTER -->
      <div class="footnote">
        <span class="fn-text">Portfolio & references available on request</span>
        <span class="fn-mark">D5-2026</span>
      </div>

    </div>
  </div>
</div>

<canvas id="matrix-canvas"></canvas>
<script>
  const canvas = document.getElementById('matrix-canvas');
  const ctx = canvas.getContext('2d');

  function resize() {
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;
  }
  resize();
  window.addEventListener('resize', resize);

  const cols = () => Math.floor(canvas.width / 16);
  let drops = [];
  function initDrops() {
    drops = Array.from({ length: cols() }, () => Math.random() * -100);
  }
  initDrops();
  window.addEventListener('resize', initDrops);

  // Mix of katakana, latin, numbers — cinematic feel
  const chars = 'アイウエオカキクケコサシスセソタチツテトナニヌネノ0123456789ABCDEF∇∆⌘⚡';

  // Alternate between maroon and lilac per column
  const colColors = () => Array.from({ length: cols() }, (_, i) =>
    i % 3 === 0 ? '#C4193A' : i % 3 === 1 ? '#C89FE8' : '#6B3A7D'
  );
  let colors = colColors();
  window.addEventListener('resize', () => { colors = colColors(); });

  function draw() {
    ctx.fillStyle = 'rgba(19,18,23,0.2)';
    ctx.fillRect(0, 0, canvas.width, canvas.height);

    ctx.font = '13px "DM Mono", monospace';

    const numCols = cols();
    for (let i = 0; i < numCols; i++) {
      const ch = chars[Math.floor(Math.random() * chars.length)];
      const x = i * 16;
      const y = drops[i] * 16;

      // Lead character brighter
      ctx.fillStyle = '#F8F2FF';
      ctx.fillText(ch, x, y);

      // Trail character
      ctx.fillStyle = colors[i] || '#C4193A';
      const trailCh = chars[Math.floor(Math.random() * chars.length)];
      ctx.fillText(trailCh, x, y - 16);

      if (y > canvas.height && Math.random() > 0.975) {
        drops[i] = 0;
      }
      drops[i] += 0.5;
    }
  }

  setInterval(draw, 50);
</script>
</body>
</html>
