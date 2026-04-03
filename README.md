# AI-Ecosystem-Chart
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8"/>
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>AI Ecosystem for Creators – V3</title>
  <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700;800&display=swap" rel="stylesheet"/>
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    :root {
      --bg:       #0d0d1a;
      --card-bg:  #111127;
      --border:   rgba(255,255,255,0.07);
      --text:     #f1f5f9;
      --muted:    #6b7280;
      --purple:   #a855f7;
      --pink:     #ec4899;

      /* category accent palette (neon) */
      --c-writing:      #60a5fa;
      --c-image:        #c084fc;
      --c-video:        #f472b6;
      --c-audio:        #fbbf24;
      --c-avatars:      #34d399;
      --c-research:     #22d3ee;
      --c-productivity: #fb923c;
      --c-monetization: #a3e635;
    }

    body {
      font-family: 'Plus Jakarta Sans', sans-serif;
      background: var(--bg);
      color: var(--text);
    }

    /* ── HEADER ── */
    header {
      background: linear-gradient(135deg, #1a0a3d 0%, #2d0a4e 40%, #1a0a3d 100%);
      padding: 60px 24px 52px;
      text-align: center;
      position: relative;
      overflow: hidden;
      border-bottom: 1px solid rgba(168,85,247,0.2);
    }
    header::before {
      content: '';
      position: absolute;
      inset: 0;
      background: radial-gradient(ellipse at 50% -10%, rgba(168,85,247,0.35) 0%, transparent 65%);
      pointer-events: none;
    }
    header::after {
      content: '';
      position: absolute;
      bottom: 0; left: 0; right: 0;
      height: 1px;
      background: linear-gradient(90deg, transparent, #a855f7, #ec4899, transparent);
    }
    .header-eyebrow {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      background: rgba(168,85,247,0.15);
      border: 1px solid rgba(168,85,247,0.4);
      color: #c084fc;
      font-size: 11px;
      font-weight: 700;
      letter-spacing: 2px;
      text-transform: uppercase;
      padding: 6px 18px;
      border-radius: 50px;
      margin-bottom: 22px;
    }
    header h1 {
      font-size: clamp(2.4rem, 5vw, 4.2rem);
      font-weight: 800;
      line-height: 1.05;
      margin-bottom: 16px;
      background: linear-gradient(135deg, #fff 0%, #c084fc 50%, #f472b6 100%);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
    }
    header h1 span { opacity: 0.9; }
    header p {
      color: rgba(255,255,255,0.6);
      font-size: 1rem;
      max-width: 520px;
      margin: 0 auto;
      line-height: 1.7;
    }

    /* ── STATS BAR ── */
    .stats-bar {
      background: #0f0f22;
      border-bottom: 1px solid var(--border);
      display: flex;
      justify-content: center;
      flex-wrap: wrap;
    }
    .stat {
      padding: 18px 40px;
      text-align: center;
      border-right: 1px solid var(--border);
    }
    .stat:last-child { border-right: none; }
    .stat-num {
      font-size: 1.7rem;
      font-weight: 800;
      background: linear-gradient(135deg, #a855f7, #ec4899);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
      line-height: 1;
    }
    .stat-label {
      font-size: 0.7rem;
      font-weight: 600;
      color: var(--muted);
      text-transform: uppercase;
      letter-spacing: 1px;
      margin-top: 4px;
    }

    /* ── HUB ── */
    .hub-wrap {
      display: flex;
      justify-content: center;
      padding: 48px 20px 24px;
    }
    .hub-ring {
      width: 210px; height: 210px;
      border-radius: 50%;
      background: linear-gradient(135deg, #7c3aed, #ec4899);
      display: flex;
      align-items: center;
      justify-content: center;
      box-shadow:
        0 0 0 12px rgba(124,58,237,0.12),
        0 0 0 24px rgba(124,58,237,0.06),
        0 0 60px rgba(124,58,237,0.5),
        0 0 100px rgba(236,72,153,0.25);
    }
    .hub-inner {
      width: 178px; height: 178px;
      border-radius: 50%;
      background: var(--card-bg);
      border: 1px solid rgba(168,85,247,0.3);
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      text-align: center;
      padding: 18px;
    }
    .hub-emoji { font-size: 2.2rem; margin-bottom: 6px; }
    .hub-sub {
      font-size: 0.56rem;
      font-weight: 700;
      letter-spacing: 2px;
      text-transform: uppercase;
      color: #a855f7;
      margin-bottom: 3px;
    }
    .hub-title-text {
      font-size: 0.95rem;
      font-weight: 800;
      color: #fff;
      line-height: 1.25;
    }

    /* ── CATEGORIES GRID ── */
    .cats-wrap {
      max-width: 1360px;
      margin: 0 auto;
      padding: 16px 24px 56px;
    }
    .cats-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(290px, 1fr));
      gap: 20px;
    }

    .cat-card {
      background: var(--card-bg);
      border-radius: 20px;
      overflow: hidden;
      border: 1px solid var(--border);
      transition: transform 0.2s, box-shadow 0.2s;
      position: relative;
    }
    .cat-card::before {
      content: '';
      position: absolute;
      top: 0; left: 0; right: 0;
      height: 3px;
    }
    .cat-card:hover {
      transform: translateY(-4px);
    }

    /* Glow on hover per card */
    .c-writing:hover   { box-shadow: 0 16px 50px rgba(96,165,250,0.15); }
    .c-image:hover     { box-shadow: 0 16px 50px rgba(192,132,252,0.15); }
    .c-video:hover     { box-shadow: 0 16px 50px rgba(244,114,182,0.15); }
    .c-audio:hover     { box-shadow: 0 16px 50px rgba(251,191,36,0.15); }
    .c-avatars:hover   { box-shadow: 0 16px 50px rgba(52,211,153,0.15); }
    .c-research:hover  { box-shadow: 0 16px 50px rgba(34,211,238,0.15); }
    .c-productivity:hover { box-shadow: 0 16px 50px rgba(251,146,60,0.15); }
    .c-monetization:hover { box-shadow: 0 16px 50px rgba(163,230,53,0.15); }

    /* Top accent bars */
    .c-writing::before       { background: linear-gradient(90deg, #3b82f6, #60a5fa); }
    .c-image::before         { background: linear-gradient(90deg, #9333ea, #c084fc); }
    .c-video::before         { background: linear-gradient(90deg, #db2777, #f472b6); }
    .c-audio::before         { background: linear-gradient(90deg, #d97706, #fbbf24); }
    .c-avatars::before       { background: linear-gradient(90deg, #059669, #34d399); }
    .c-research::before      { background: linear-gradient(90deg, #0891b2, #22d3ee); }
    .c-productivity::before  { background: linear-gradient(90deg, #ea580c, #fb923c); }
    .c-monetization::before  { background: linear-gradient(90deg, #65a30d, #a3e635); }

    .cat-header {
      padding: 20px 20px 14px;
      display: flex;
      align-items: center;
      gap: 14px;
      border-bottom: 1px solid var(--border);
    }
    .cat-icon-wrap {
      width: 46px; height: 46px;
      border-radius: 13px;
      display: flex; align-items: center; justify-content: center;
      font-size: 1.35rem;
      flex-shrink: 0;
    }
    .c-writing .cat-icon-wrap       { background: rgba(96,165,250,0.12); border: 1px solid rgba(96,165,250,0.2); }
    .c-image .cat-icon-wrap         { background: rgba(192,132,252,0.12); border: 1px solid rgba(192,132,252,0.2); }
    .c-video .cat-icon-wrap         { background: rgba(244,114,182,0.12); border: 1px solid rgba(244,114,182,0.2); }
    .c-audio .cat-icon-wrap         { background: rgba(251,191,36,0.12); border: 1px solid rgba(251,191,36,0.2); }
    .c-avatars .cat-icon-wrap       { background: rgba(52,211,153,0.12); border: 1px solid rgba(52,211,153,0.2); }
    .c-research .cat-icon-wrap      { background: rgba(34,211,238,0.12); border: 1px solid rgba(34,211,238,0.2); }
    .c-productivity .cat-icon-wrap  { background: rgba(251,146,60,0.12); border: 1px solid rgba(251,146,60,0.2); }
    .c-monetization .cat-icon-wrap  { background: rgba(163,230,53,0.12); border: 1px solid rgba(163,230,53,0.2); }

    .cat-meta { flex: 1; min-width: 0; }
    .cat-title { font-size: 0.95rem; font-weight: 800; }
    .c-writing .cat-title       { color: var(--c-writing); }
    .c-image .cat-title         { color: var(--c-image); }
    .c-video .cat-title         { color: var(--c-video); }
    .c-audio .cat-title         { color: var(--c-audio); }
    .c-avatars .cat-title       { color: var(--c-avatars); }
    .c-research .cat-title      { color: var(--c-research); }
    .c-productivity .cat-title  { color: var(--c-productivity); }
    .c-monetization .cat-title  { color: var(--c-monetization); }

    .cat-subtitle { font-size: 0.68rem; font-weight: 500; color: var(--muted); margin-top: 2px; }
    .cat-num-badge {
      font-size: 0.65rem;
      font-weight: 700;
      padding: 3px 10px;
      border-radius: 50px;
      flex-shrink: 0;
    }
    .c-writing .cat-num-badge       { background: rgba(96,165,250,0.12); color: var(--c-writing); border: 1px solid rgba(96,165,250,0.2); }
    .c-image .cat-num-badge         { background: rgba(192,132,252,0.12); color: var(--c-image); border: 1px solid rgba(192,132,252,0.2); }
    .c-video .cat-num-badge         { background: rgba(244,114,182,0.12); color: var(--c-video); border: 1px solid rgba(244,114,182,0.2); }
    .c-audio .cat-num-badge         { background: rgba(251,191,36,0.12); color: var(--c-audio); border: 1px solid rgba(251,191,36,0.2); }
    .c-avatars .cat-num-badge       { background: rgba(52,211,153,0.12); color: var(--c-avatars); border: 1px solid rgba(52,211,153,0.2); }
    .c-research .cat-num-badge      { background: rgba(34,211,238,0.12); color: var(--c-research); border: 1px solid rgba(34,211,238,0.2); }
    .c-productivity .cat-num-badge  { background: rgba(251,146,60,0.12); color: var(--c-productivity); border: 1px solid rgba(251,146,60,0.2); }
    .c-monetization .cat-num-badge  { background: rgba(163,230,53,0.12); color: var(--c-monetization); border: 1px solid rgba(163,230,53,0.2); }

    /* Tool rows */
    .tools-body { padding: 12px 16px 16px; display: flex; flex-direction: column; gap: 6px; }
    .tool-row {
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 10px 13px;
      border-radius: 10px;
      background: rgba(255,255,255,0.03);
      border: 1px solid rgba(255,255,255,0.06);
      transition: background 0.15s, border-color 0.15s;
    }
    .tool-row:hover {
      background: rgba(255,255,255,0.07);
      border-color: rgba(255,255,255,0.12);
    }
    .tool-name { font-size: 0.87rem; font-weight: 700; color: #e2e8f0; }
    .tool-badges { display: flex; gap: 4px; flex-shrink: 0; }
    .badge {
      font-size: 0.58rem;
      font-weight: 700;
      letter-spacing: 0.5px;
      text-transform: uppercase;
      padding: 3px 8px;
      border-radius: 50px;
    }
    .b-free     { background: rgba(34,197,94,0.15);  color: #4ade80; border: 1px solid rgba(34,197,94,0.3); }
    .b-beginner { background: rgba(59,130,246,0.15);  color: #60a5fa; border: 1px solid rgba(59,130,246,0.3); }
    .b-inter    { background: rgba(249,115,22,0.15);  color: #fb923c; border: 1px solid rgba(249,115,22,0.3); }
    .b-advanced { background: rgba(239,68,68,0.15);   color: #f87171; border: 1px solid rgba(239,68,68,0.3); }

    /* ── WORKFLOW ── */
    .workflow-wrap {
      background: linear-gradient(135deg, #1a0a3d 0%, #2d0a4e 50%, #1a0a3d 100%);
      padding: 56px 24px;
      position: relative;
      overflow: hidden;
      border-top: 1px solid rgba(168,85,247,0.15);
      border-bottom: 1px solid rgba(168,85,247,0.15);
    }
    .workflow-wrap::before {
      content: '';
      position: absolute;
      inset: 0;
      background: radial-gradient(ellipse at 50% 50%, rgba(168,85,247,0.12) 0%, transparent 70%);
      pointer-events: none;
    }
    .section-heading {
      text-align: center;
      font-size: 1.8rem;
      font-weight: 800;
      margin-bottom: 8px;
      background: linear-gradient(135deg, #fff 0%, #c084fc 50%, #f472b6 100%);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
    }
    .section-sub {
      text-align: center;
      font-size: 0.88rem;
      color: rgba(255,255,255,0.5);
      margin-bottom: 44px;
    }

    .workflow-track {
      max-width: 980px;
      margin: 0 auto;
      display: flex;
      align-items: flex-start;
      justify-content: center;
      flex-wrap: wrap;
      gap: 6px;
    }
    .wf-step {
      display: flex;
      flex-direction: column;
      align-items: center;
      text-align: center;
      width: 160px;
    }
    .wf-circle {
      width: 72px; height: 72px;
      border-radius: 50%;
      background: rgba(255,255,255,0.06);
      border: 1.5px solid rgba(168,85,247,0.35);
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      margin-bottom: 14px;
      position: relative;
    }
    .wf-num {
      font-size: 0.55rem;
      font-weight: 700;
      color: #a855f7;
      letter-spacing: 1px;
      text-transform: uppercase;
    }
    .wf-icon { font-size: 1.6rem; line-height: 1; }
    .wf-label { font-size: 0.8rem; font-weight: 700; color: #f1f5f9; margin-bottom: 4px; }
    .wf-tool  { font-size: 0.7rem; color: rgba(255,255,255,0.55); line-height: 1.4; }

    .wf-arrow {
      color: rgba(168,85,247,0.6);
      font-size: 1.8rem;
      margin-top: 22px;
      flex-shrink: 0;
      align-self: flex-start;
    }

    /* Step glow colors */
    .ws1 .wf-circle { box-shadow: 0 0 20px rgba(168,85,247,0.4); border-color: rgba(168,85,247,0.5); }
    .ws2 .wf-circle { box-shadow: 0 0 20px rgba(96,165,250,0.35); border-color: rgba(96,165,250,0.4); }
    .ws3 .wf-circle { box-shadow: 0 0 20px rgba(251,191,36,0.35); border-color: rgba(251,191,36,0.4); }
    .ws4 .wf-circle { box-shadow: 0 0 20px rgba(244,114,182,0.35); border-color: rgba(244,114,182,0.4); }
    .ws5 .wf-circle { box-shadow: 0 0 20px rgba(52,211,153,0.35); border-color: rgba(52,211,153,0.4); }

    /* ── LEGEND ── */
    .legend-wrap {
      background: #0f0f22;
      padding: 52px 24px 64px;
      border-top: 1px solid var(--border);
    }
    .legend-heading {
      text-align: center;
      font-size: 1.6rem;
      font-weight: 800;
      color: #fff;
      margin-bottom: 6px;
    }
    .legend-desc {
      text-align: center;
      font-size: 0.85rem;
      color: var(--muted);
      margin-bottom: 34px;
    }
    .legend-cards {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 16px;
      max-width: 860px;
      margin: 0 auto;
    }
    .legend-card {
      display: flex;
      align-items: center;
      gap: 14px;
      padding: 18px 24px;
      border-radius: 14px;
      border: 1px solid;
      width: 200px;
      background: var(--card-bg);
    }
    .lc-green  { border-color: rgba(74,222,128,0.3); }
    .lc-blue   { border-color: rgba(96,165,250,0.3); }
    .lc-orange { border-color: rgba(251,146,60,0.3); }
    .lc-red    { border-color: rgba(248,113,113,0.3); }

    .legend-dot {
      width: 18px; height: 18px;
      border-radius: 50%;
      flex-shrink: 0;
    }
    .ld-green  { background: #4ade80; box-shadow: 0 0 10px rgba(74,222,128,0.6); }
    .ld-blue   { background: #60a5fa; box-shadow: 0 0 10px rgba(96,165,250,0.6); }
    .ld-orange { background: #fb923c; box-shadow: 0 0 10px rgba(251,146,60,0.6); }
    .ld-red    { background: #f87171; box-shadow: 0 0 10px rgba(248,113,113,0.6); }

    .legend-tag-label {
      font-size: 0.7rem;
      font-weight: 800;
      text-transform: uppercase;
      letter-spacing: 0.8px;
      margin-bottom: 2px;
    }
    .lc-green .legend-tag-label  { color: #4ade80; }
    .lc-blue .legend-tag-label   { color: #60a5fa; }
    .lc-orange .legend-tag-label { color: #fb923c; }
    .lc-red .legend-tag-label    { color: #f87171; }

    .legend-meaning { font-size: 0.72rem; color: var(--muted); line-height: 1.3; }

    /* ── FOOTER ── */
    footer {
      background: #080812;
      text-align: center;
      padding: 28px 20px;
      color: rgba(255,255,255,0.25);
      font-size: 0.78rem;
      border-top: 1px solid var(--border);
    }
    footer strong { color: rgba(255,255,255,0.5); }

    @media (max-width: 600px) {
      .wf-arrow { display: none; }
      .legend-card { width: 100%; max-width: 320px; }
      .stat { padding: 14px 20px; }
    }
  </style>
</head>
<body>

<!-- ── HEADER ── -->
<header>
  <div class="header-eyebrow">✦ Visual Reference Guide for Creators</div>
  <h1>AI Ecosystem<br/><span>for Creators</span></h1>
  <p>A complete, organized map of the AI tools powering today's content creators and digital entrepreneurs — from ideation to income.</p>
</header>

<!-- ── STATS BAR ── -->
<div class="stats-bar">
  <div class="stat"><div class="stat-num">8</div><div class="stat-label">Categories</div></div>
  <div class="stat"><div class="stat-num">36</div><div class="stat-label">AI Tools</div></div>
  <div class="stat"><div class="stat-num">5</div><div class="stat-label">Workflow Steps</div></div>
  <div class="stat"><div class="stat-num">4</div><div class="stat-label">Skill Levels</div></div>
</div>

<!-- ── HUB ── -->
<div class="hub-wrap">
  <div class="hub-ring">
    <div class="hub-inner">
      <div class="hub-emoji">🤖</div>
      <div class="hub-sub">Center Hub</div>
      <div class="hub-title-text">AI Creator<br/>Ecosystem</div>
    </div>
  </div>
</div>

<!-- ── CATEGORIES ── -->
<div class="cats-wrap">
  <div class="cats-grid">

    <!-- Writing AI -->
    <div class="cat-card c-writing">
      <div class="cat-header">
        <div class="cat-icon-wrap">✍️</div>
        <div class="cat-meta">
          <div class="cat-title">Writing AI</div>
          <div class="cat-subtitle">Content & copywriting tools</div>
        </div>
        <div class="cat-num-badge">5 tools</div>
      </div>
      <div class="tools-body">
        <div class="tool-row"><span class="tool-name">ChatGPT</span><span class="tool-badges"><span class="badge b-free">Free</span><span class="badge b-beginner">Beginner</span></span></div>
        <div class="tool-row"><span class="tool-name">Claude</span><span class="tool-badges"><span class="badge b-free">Free</span><span class="badge b-beginner">Beginner</span></span></div>
        <div class="tool-row"><span class="tool-name">Gemini</span><span class="tool-badges"><span class="badge b-free">Free</span><span class="badge b-beginner">Beginner</span></span></div>
        <div class="tool-row"><span class="tool-name">Jasper</span><span class="tool-badges"><span class="badge b-inter">Intermediate</span></span></div>
        <div class="tool-row"><span class="tool-name">Copy.ai</span><span class="tool-badges"><span class="badge b-free">Free</span><span class="badge b-beginner">Beginner</span></span></div>
      </div>
    </div>

    <!-- Image Generation AI -->
    <div class="cat-card c-image">
      <div class="cat-header">
        <div class="cat-icon-wrap">🎨</div>
        <div class="cat-meta">
          <div class="cat-title">Image Generation AI</div>
          <div class="cat-subtitle">Visual creation tools</div>
        </div>
        <div class="cat-num-badge">5 tools</div>
      </div>
      <div class="tools-body">
        <div class="tool-row"><span class="tool-name">Midjourney</span><span class="tool-badges"><span class="badge b-inter">Intermediate</span></span></div>
        <div class="tool-row"><span class="tool-name">DALL·E</span><span class="tool-badges"><span class="badge b-free">Free</span><span class="badge b-beginner">Beginner</span></span></div>
        <div class="tool-row"><span class="tool-name">Leonardo AI</span><span class="tool-badges"><span class="badge b-free">Free</span><span class="badge b-beginner">Beginner</span></span></div>
        <div class="tool-row"><span class="tool-name">Playground AI</span><span class="tool-badges"><span class="badge b-free">Free</span><span class="badge b-beginner">Beginner</span></span></div>
        <div class="tool-row"><span class="tool-name">Ideogram</span><span class="tool-badges"><span class="badge b-free">Free</span><span class="badge b-beginner">Beginner</span></span></div>
      </div>
    </div>

    <!-- Video Creation AI -->
    <div class="cat-card c-video">
      <div class="cat-header">
        <div class="cat-icon-wrap">🎬</div>
        <div class="cat-meta">
          <div class="cat-title">Video Creation AI</div>
          <div class="cat-subtitle">Video editing & generation</div>
        </div>
        <div class="cat-num-badge">5 tools</div>
      </div>
      <div class="tools-body">
        <div class="tool-row"><span class="tool-name">CapCut AI</span><span class="tool-badges"><span class="badge b-free">Free</span><span class="badge b-beginner">Beginner</span></span></div>
        <div class="tool-row"><span class="tool-name">Runway ML</span><span class="tool-badges"><span class="badge b-inter">Intermediate</span></span></div>
        <div class="tool-row"><span class="tool-name">Pika</span><span class="tool-badges"><span class="badge b-free">Free</span><span class="badge b-beginner">Beginner</span></span></div>
        <div class="tool-row"><span class="tool-name">InVideo AI</span><span class="tool-badges"><span class="badge b-free">Free</span><span class="badge b-beginner">Beginner</span></span></div>
        <div class="tool-row"><span class="tool-name">Descript</span><span class="tool-badges"><span class="badge b-inter">Intermediate</span></span></div>
      </div>
    </div>

    <!-- Audio & Voice AI -->
    <div class="cat-card c-audio">
      <div class="cat-header">
        <div class="cat-icon-wrap">🎙️</div>
        <div class="cat-meta">
          <div class="cat-title">Audio & Voice AI</div>
          <div class="cat-subtitle">Voice cloning & audio tools</div>
        </div>
        <div class="cat-num-badge">4 tools</div>
      </div>
      <div class="tools-body">
        <div class="tool-row"><span class="tool-name">ElevenLabs</span><span class="tool-badges"><span class="badge b-free">Free</span><span class="badge b-beginner">Beginner</span></span></div>
        <div class="tool-row"><span class="tool-name">PlayHT</span><span class="tool-badges"><span class="badge b-free">Free</span><span class="badge b-inter">Intermediate</span></span></div>
        <div class="tool-row"><span class="tool-name">Murf AI</span><span class="tool-badges"><span class="badge b-inter">Intermediate</span></span></div>
        <div class="tool-row"><span class="tool-name">Adobe Podcast</span><span class="tool-badges"><span class="badge b-free">Free</span><span class="badge b-beginner">Beginner</span></span></div>
      </div>
    </div>

    <!-- AI Avatars -->
    <div class="cat-card c-avatars">
      <div class="cat-header">
        <div class="cat-icon-wrap">🧑‍💻</div>
        <div class="cat-meta">
          <div class="cat-title">AI Avatars</div>
          <div class="cat-subtitle">Digital human & avatar tools</div>
        </div>
        <div class="cat-num-badge">4 tools</div>
      </div>
      <div class="tools-body">
        <div class="tool-row"><span class="tool-name">HeyGen</span><span class="tool-badges"><span class="badge b-inter">Intermediate</span></span></div>
        <div class="tool-row"><span class="tool-name">Synthesia</span><span class="tool-badges"><span class="badge b-advanced">Advanced</span></span></div>
        <div class="tool-row"><span class="tool-name">D-ID</span><span class="tool-badges"><span class="badge b-inter">Intermediate</span></span></div>
        <div class="tool-row"><span class="tool-name">Colossyan</span><span class="tool-badges"><span class="badge b-advanced">Advanced</span></span></div>
      </div>
    </div>

    <!-- Research AI -->
    <div class="cat-card c-research">
      <div class="cat-header">
        <div class="cat-icon-wrap">🔍</div>
        <div class="cat-meta">
          <div class="cat-title">Research AI</div>
          <div class="cat-subtitle">Search & knowledge tools</div>
        </div>
        <div class="cat-num-badge">4 tools</div>
      </div>
      <div class="tools-body">
        <div class="tool-row"><span class="tool-name">Perplexity</span><span class="tool-badges"><span class="badge b-free">Free</span><span class="badge b-beginner">Beginner</span></span></div>
        <div class="tool-row"><span class="tool-name">Elicit</span><span class="tool-badges"><span class="badge b-free">Free</span><span class="badge b-beginner">Beginner</span></span></div>
        <div class="tool-row"><span class="tool-name">Consensus</span><span class="tool-badges"><span class="badge b-free">Free</span><span class="badge b-beginner">Beginner</span></span></div>
        <div class="tool-row"><span class="tool-name">ChatGPT Browsing</span><span class="tool-badges"><span class="badge b-free">Free</span></span></div>
      </div>
    </div>

    <!-- Productivity AI -->
    <div class="cat-card c-productivity">
      <div class="cat-header">
        <div class="cat-icon-wrap">⚡</div>
        <div class="cat-meta">
          <div class="cat-title">Productivity AI</div>
          <div class="cat-subtitle">Automation & organization</div>
        </div>
        <div class="cat-num-badge">4 tools</div>
      </div>
      <div class="tools-body">
        <div class="tool-row"><span class="tool-name">Notion AI</span><span class="tool-badges"><span class="badge b-inter">Intermediate</span></span></div>
        <div class="tool-row"><span class="tool-name">Taskade</span><span class="tool-badges"><span class="badge b-free">Free</span><span class="badge b-beginner">Beginner</span></span></div>
        <div class="tool-row"><span class="tool-name">Zapier</span><span class="tool-badges"><span class="badge b-inter">Intermediate</span></span></div>
        <div class="tool-row"><span class="tool-name">Make.com</span><span class="tool-badges"><span class="badge b-inter">Intermediate</span></span></div>
      </div>
    </div>

    <!-- Creator Monetization -->
    <div class="cat-card c-monetization">
      <div class="cat-header">
        <div class="cat-icon-wrap">💰</div>
        <div class="cat-meta">
          <div class="cat-title">Creator Monetization</div>
          <div class="cat-subtitle">Sell & earn platforms</div>
        </div>
        <div class="cat-num-badge">5 tools</div>
      </div>
      <div class="tools-body">
        <div class="tool-row"><span class="tool-name">Shopify</span><span class="tool-badges"><span class="badge b-inter">Intermediate</span></span></div>
        <div class="tool-row"><span class="tool-name">Gumroad</span><span class="tool-badges"><span class="badge b-free">Free</span><span class="badge b-beginner">Beginner</span></span></div>
        <div class="tool-row"><span class="tool-name">Stan Store</span><span class="tool-badges"><span class="badge b-beginner">Beginner</span></span></div>
        <div class="tool-row"><span class="tool-name">Lemon Squeezy</span><span class="tool-badges"><span class="badge b-free">Free</span></span></div>
        <div class="tool-row"><span class="tool-name">Etsy</span><span class="tool-badges"><span class="badge b-free">Free</span><span class="badge b-beginner">Beginner</span></span></div>
      </div>
    </div>

  </div>
</div>

<!-- ── WORKFLOW ── -->
<div class="workflow-wrap">
  <div class="section-heading">🚀 Creator Workflow Example</div>
  <div class="section-sub">See how AI tools connect from idea to published content</div>
  <div class="workflow-track">
    <div class="wf-step ws1">
      <div class="wf-circle"><div class="wf-num">Step 1</div><div class="wf-icon">💡</div></div>
      <div class="wf-label">Idea Generation</div>
      <div class="wf-tool">ChatGPT or Claude</div>
    </div>
    <div class="wf-arrow">›</div>
    <div class="wf-step ws2">
      <div class="wf-circle"><div class="wf-num">Step 2</div><div class="wf-icon">📝</div></div>
      <div class="wf-label">Script Writing</div>
      <div class="wf-tool">ChatGPT or Claude</div>
    </div>
    <div class="wf-arrow">›</div>
    <div class="wf-step ws3">
      <div class="wf-circle"><div class="wf-num">Step 3</div><div class="wf-icon">🎙️</div></div>
      <div class="wf-label">Voiceover Creation</div>
      <div class="wf-tool">ElevenLabs</div>
    </div>
    <div class="wf-arrow">›</div>
    <div class="wf-step ws4">
      <div class="wf-circle"><div class="wf-num">Step 4</div><div class="wf-icon">🎬</div></div>
      <div class="wf-label">Video Editing</div>
      <div class="wf-tool">CapCut AI</div>
    </div>
    <div class="wf-arrow">›</div>
    <div class="wf-step ws5">
      <div class="wf-circle"><div class="wf-num">Step 5</div><div class="wf-icon">📱</div></div>
      <div class="wf-label">Publishing</div>
      <div class="wf-tool">TikTok or YouTube</div>
    </div>
  </div>
</div>

<!-- ── LEGEND ── -->
<div class="legend-wrap">
  <div class="legend-heading">🎨 Color Legend</div>
  <div class="legend-desc">Each tool is labeled to help you choose the right fit for your skill level and budget</div>
  <div class="legend-cards">
    <div class="legend-card lc-green">
      <div class="legend-dot ld-green"></div>
      <div>
        <div class="legend-tag-label">Green</div>
        <div class="legend-meaning">Free tier available</div>
      </div>
    </div>
    <div class="legend-card lc-blue">
      <div class="legend-dot ld-blue"></div>
      <div>
        <div class="legend-tag-label">Blue</div>
        <div class="legend-meaning">Beginner friendly</div>
      </div>
    </div>
    <div class="legend-card lc-orange">
      <div class="legend-dot ld-orange"></div>
      <div>
        <div class="legend-tag-label">Orange</div>
        <div class="legend-meaning">Intermediate tools</div>
      </div>
    </div>
    <div class="legend-card lc-red">
      <div class="legend-dot ld-red"></div>
      <div>
        <div class="legend-tag-label">Red</div>
        <div class="legend-meaning">Advanced / technical tools</div>
      </div>
    </div>
  </div>
</div>

<footer>
  <strong>AI Ecosystem Chart for Creators</strong> &nbsp;·&nbsp; 8 Categories · 36 Tools · 5-Step Workflow
</footer>

</body>
</html>
