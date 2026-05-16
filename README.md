<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>TB Digital Solutions — Taimoor Butt</title>
  <link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Sans:ital,wght@0,300;0,400;0,500;1,300&display=swap" rel="stylesheet"/>
  <style>
    :root {
      --bg: #080b10;
      --bg2: #0d1117;
      --surface: #111620;
      --border: rgba(255,255,255,0.07);
      --accent: #00e5ff;
      --accent2: #7b61ff;
      --text: #e8edf5;
      --muted: #6b7a99;
      --white: #ffffff;
      --grad: linear-gradient(135deg, #00e5ff, #7b61ff);
    }

    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    html { scroll-behavior: smooth; }

    body {
      background: var(--bg);
      color: var(--text);
      font-family: 'DM Sans', sans-serif;
      font-weight: 400;
      overflow-x: hidden;
      cursor: none;
    }

    /* Custom cursor */
    .cursor {
      width: 10px; height: 10px;
      background: var(--accent);
      border-radius: 50%;
      position: fixed;
      pointer-events: none;
      z-index: 9999;
      transform: translate(-50%, -50%);
      transition: transform 0.1s;
    }
    .cursor-ring {
      width: 36px; height: 36px;
      border: 1px solid rgba(0,229,255,0.4);
      border-radius: 50%;
      position: fixed;
      pointer-events: none;
      z-index: 9998;
      transform: translate(-50%, -50%);
      transition: all 0.15s ease;
    }

    /* Grid noise overlay */
    body::before {
      content: '';
      position: fixed; inset: 0;
      background-image:
        linear-gradient(rgba(255,255,255,0.015) 1px, transparent 1px),
        linear-gradient(90deg, rgba(255,255,255,0.015) 1px, transparent 1px);
      background-size: 60px 60px;
      pointer-events: none;
      z-index: 0;
    }

    /* ── NAVBAR ── */
    nav {
      position: fixed; top: 0; left: 0; right: 0;
      z-index: 100;
      display: flex; align-items: center; justify-content: space-between;
      padding: 22px 60px;
      background: rgba(8,11,16,0.85);
      backdrop-filter: blur(20px);
      border-bottom: 1px solid var(--border);
      animation: slideDown 0.8s ease both;
    }

    .logo {
      font-family: 'Syne', sans-serif;
      font-weight: 800;
      font-size: 22px;
      background: var(--grad);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
      letter-spacing: -0.5px;
    }

    .nav-links {
      display: flex; gap: 36px;
      list-style: none;
    }

    .nav-links a {
      font-size: 14px;
      font-weight: 500;
      color: var(--muted);
      text-decoration: none;
      letter-spacing: 0.5px;
      transition: color 0.3s;
      position: relative;
    }
    .nav-links a::after {
      content: '';
      position: absolute; bottom: -4px; left: 0; right: 0;
      height: 1px;
      background: var(--accent);
      transform: scaleX(0);
      transition: transform 0.3s;
    }
    .nav-links a:hover { color: var(--white); }
    .nav-links a:hover::after { transform: scaleX(1); }

    .nav-cta {
      background: var(--grad);
      color: var(--bg) !important;
      padding: 10px 24px;
      border-radius: 4px;
      font-weight: 700 !important;
      font-size: 13px !important;
      text-decoration: none;
      transition: opacity 0.3s, transform 0.3s !important;
    }
    .nav-cta:hover { opacity: 0.88; transform: translateY(-1px); }
    .nav-cta::after { display: none !important; }

    /* ── HERO ── */
    #home {
      min-height: 100vh;
      display: flex; align-items: center;
      padding: 140px 60px 80px;
      position: relative;
      z-index: 1;
      overflow: hidden;
    }

    .hero-glow {
      position: absolute;
      width: 700px; height: 700px;
      border-radius: 50%;
      background: radial-gradient(circle, rgba(0,229,255,0.07) 0%, transparent 70%);
      top: -100px; right: -200px;
      pointer-events: none;
      animation: breathe 6s ease-in-out infinite;
    }
    .hero-glow2 {
      position: absolute;
      width: 500px; height: 500px;
      border-radius: 50%;
      background: radial-gradient(circle, rgba(123,97,255,0.07) 0%, transparent 70%);
      bottom: -100px; left: -100px;
      pointer-events: none;
      animation: breathe 8s ease-in-out infinite reverse;
    }

    @keyframes breathe {
      0%, 100% { transform: scale(1); opacity: 0.7; }
      50% { transform: scale(1.12); opacity: 1; }
    }

    .hero-content { max-width: 760px; position: relative; z-index: 2; }

    .hero-badge {
      display: inline-flex; align-items: center; gap: 8px;
      background: rgba(0,229,255,0.08);
      border: 1px solid rgba(0,229,255,0.2);
      color: var(--accent);
      font-size: 12px;
      font-weight: 500;
      letter-spacing: 2px;
      text-transform: uppercase;
      padding: 8px 18px;
      border-radius: 20px;
      margin-bottom: 32px;
      animation: fadeUp 0.8s ease 0.2s both;
    }
    .badge-dot {
      width: 6px; height: 6px;
      background: var(--accent);
      border-radius: 50%;
      animation: pulse-dot 1.5s ease-in-out infinite;
    }
    @keyframes pulse-dot {
      0%, 100% { opacity: 1; transform: scale(1); }
      50% { opacity: 0.4; transform: scale(0.6); }
    }

    .hero-title {
      font-family: 'Syne', sans-serif;
      font-weight: 800;
      font-size: clamp(42px, 6vw, 80px);
      line-height: 1.05;
      letter-spacing: -2px;
      margin-bottom: 28px;
      animation: fadeUp 0.8s ease 0.4s both;
    }

    .hero-title span {
      background: var(--grad);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
    }

    .hero-desc {
      font-size: 18px;
      line-height: 1.8;
      color: var(--muted);
      max-width: 560px;
      margin-bottom: 44px;
      font-weight: 300;
      animation: fadeUp 0.8s ease 0.6s both;
    }

    .hero-actions {
      display: flex; gap: 16px; flex-wrap: wrap;
      animation: fadeUp 0.8s ease 0.8s both;
    }

    .btn-primary {
      background: var(--grad);
      color: var(--bg);
      font-family: 'Syne', sans-serif;
      font-weight: 700;
      font-size: 15px;
      padding: 16px 36px;
      border-radius: 4px;
      text-decoration: none;
      transition: transform 0.3s, box-shadow 0.3s;
      letter-spacing: 0.3px;
    }
    .btn-primary:hover {
      transform: translateY(-3px);
      box-shadow: 0 20px 40px rgba(0,229,255,0.25);
    }

    .btn-secondary {
      background: transparent;
      color: var(--text);
      font-family: 'Syne', sans-serif;
      font-weight: 600;
      font-size: 15px;
      padding: 16px 36px;
      border-radius: 4px;
      border: 1px solid var(--border);
      text-decoration: none;
      transition: border-color 0.3s, color 0.3s, transform 0.3s;
    }
    .btn-secondary:hover {
      border-color: var(--accent);
      color: var(--accent);
      transform: translateY(-3px);
    }

    /* Stats bar */
    .stats-bar {
      display: flex; gap: 48px;
      margin-top: 72px;
      padding-top: 40px;
      border-top: 1px solid var(--border);
      animation: fadeUp 0.8s ease 1s both;
      flex-wrap: wrap;
    }
    .stat-item {}
    .stat-num {
      font-family: 'Syne', sans-serif;
      font-weight: 800;
      font-size: 36px;
      background: var(--grad);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
    }
    .stat-label {
      font-size: 13px;
      color: var(--muted);
      margin-top: 4px;
      letter-spacing: 0.5px;
    }

    /* ── SECTION COMMON ── */
    section { position: relative; z-index: 1; }

    .section-wrap {
      max-width: 1100px;
      margin: 0 auto;
      padding: 100px 60px;
    }

    .section-tag {
      display: inline-block;
      font-size: 11px;
      font-weight: 700;
      letter-spacing: 3px;
      text-transform: uppercase;
      color: var(--accent);
      margin-bottom: 16px;
    }

    .section-title {
      font-family: 'Syne', sans-serif;
      font-weight: 800;
      font-size: clamp(30px, 4vw, 48px);
      letter-spacing: -1px;
      line-height: 1.1;
      margin-bottom: 20px;
    }

    .section-desc {
      font-size: 17px;
      color: var(--muted);
      line-height: 1.8;
      max-width: 520px;
      font-weight: 300;
    }

    .divider-line {
      height: 1px;
      background: var(--border);
      margin: 0 60px;
    }

    /* ── SERVICES ── */
    #services { background: var(--bg2); }

    .services-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 1px;
      background: var(--border);
      border: 1px solid var(--border);
      border-radius: 8px;
      overflow: hidden;
      margin-top: 60px;
    }

    .service-card {
      background: var(--surface);
      padding: 40px 36px;
      transition: background 0.3s;
      position: relative;
      overflow: hidden;
    }
    .service-card::before {
      content: '';
      position: absolute;
      top: 0; left: 0; right: 0;
      height: 2px;
      background: var(--grad);
      transform: scaleX(0);
      transition: transform 0.4s;
    }
    .service-card:hover { background: #161d2a; }
    .service-card:hover::before { transform: scaleX(1); }

    .service-icon {
      width: 48px; height: 48px;
      border-radius: 10px;
      background: rgba(0,229,255,0.08);
      border: 1px solid rgba(0,229,255,0.15);
      display: flex; align-items: center; justify-content: center;
      font-size: 22px;
      margin-bottom: 20px;
      transition: transform 0.3s;
    }
    .service-card:hover .service-icon { transform: scale(1.1) rotate(-5deg); }

    .service-title {
      font-family: 'Syne', sans-serif;
      font-weight: 700;
      font-size: 18px;
      margin-bottom: 12px;
      color: var(--white);
    }

    .service-desc {
      font-size: 14px;
      color: var(--muted);
      line-height: 1.8;
    }

    /* ── ABOUT ── */
    #about { background: var(--bg); }

    .about-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 80px;
      align-items: center;
      margin-top: 60px;
    }

    .about-visual {
      position: relative;
    }

    .about-card {
      background: var(--surface);
      border: 1px solid var(--border);
      border-radius: 8px;
      padding: 48px 44px;
      position: relative;
      overflow: hidden;
    }
    .about-card::after {
      content: '';
      position: absolute;
      inset: 0;
      background: var(--grad);
      opacity: 0.03;
      pointer-events: none;
    }

    .founder-name {
      font-family: 'Syne', sans-serif;
      font-weight: 800;
      font-size: 32px;
      background: var(--grad);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
      margin-bottom: 6px;
    }

    .founder-role {
      font-size: 13px;
      color: var(--muted);
      letter-spacing: 2px;
      text-transform: uppercase;
      margin-bottom: 28px;
    }

    .skill-tags {
      display: flex; flex-wrap: wrap; gap: 8px;
      margin-top: 24px;
    }

    .skill-tag {
      background: rgba(0,229,255,0.07);
      border: 1px solid rgba(0,229,255,0.15);
      color: var(--accent);
      font-size: 12px;
      padding: 5px 14px;
      border-radius: 20px;
      font-weight: 500;
    }

    .about-text p {
      font-size: 16px;
      color: var(--muted);
      line-height: 1.9;
      margin-bottom: 20px;
      font-weight: 300;
    }

    .about-highlight {
      background: rgba(0,229,255,0.05);
      border-right: 3px solid var(--accent);
      padding: 16px 20px;
      border-radius: 0 6px 6px 0;
      font-size: 16px;
      color: var(--text);
      line-height: 1.7;
      margin: 24px 0;
      font-style: italic;
    }

    /* ── CONTACT ── */
    #contact { background: var(--bg2); }

    .contact-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 60px;
      margin-top: 60px;
      align-items: start;
    }

    .contact-info { }

    .contact-item {
      display: flex; align-items: flex-start; gap: 16px;
      margin-bottom: 28px;
    }

    .contact-icon {
      width: 44px; height: 44px;
      border-radius: 8px;
      background: rgba(0,229,255,0.08);
      border: 1px solid rgba(0,229,255,0.15);
      display: flex; align-items: center; justify-content: center;
      font-size: 18px;
      flex-shrink: 0;
    }

    .contact-label {
      font-size: 11px;
      font-weight: 700;
      letter-spacing: 2px;
      text-transform: uppercase;
      color: var(--muted);
      margin-bottom: 4px;
    }

    .contact-value {
      font-size: 15px;
      color: var(--text);
      font-weight: 500;
    }

    /* Form */
    .contact-form {
      background: var(--surface);
      border: 1px solid var(--border);
      border-radius: 8px;
      padding: 40px;
    }

    .form-group { margin-bottom: 20px; }

    .form-label {
      display: block;
      font-size: 12px;
      font-weight: 600;
      letter-spacing: 1px;
      text-transform: uppercase;
      color: var(--muted);
      margin-bottom: 8px;
    }

    .form-input, .form-textarea {
      width: 100%;
      background: var(--bg);
      border: 1px solid var(--border);
      border-radius: 4px;
      padding: 14px 18px;
      color: var(--text);
      font-family: 'DM Sans', sans-serif;
      font-size: 15px;
      outline: none;
      transition: border-color 0.3s, box-shadow 0.3s;
    }
    .form-input:focus, .form-textarea:focus {
      border-color: var(--accent);
      box-shadow: 0 0 0 3px rgba(0,229,255,0.08);
    }

    .form-textarea { height: 130px; resize: none; }

    .form-btn {
      width: 100%;
      background: var(--grad);
      color: var(--bg);
      font-family: 'Syne', sans-serif;
      font-weight: 700;
      font-size: 15px;
      padding: 16px;
      border-radius: 4px;
      border: none;
      cursor: none;
      letter-spacing: 0.5px;
      transition: transform 0.3s, box-shadow 0.3s;
    }
    .form-btn:hover {
      transform: translateY(-2px);
      box-shadow: 0 16px 40px rgba(0,229,255,0.25);
    }

    /* ── FOOTER ── */
    footer {
      background: var(--bg);
      border-top: 1px solid var(--border);
      padding: 40px 60px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      flex-wrap: wrap;
      gap: 16px;
      position: relative; z-index: 1;
    }

    .footer-logo {
      font-family: 'Syne', sans-serif;
      font-weight: 800;
      font-size: 18px;
      background: var(--grad);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
    }

    .footer-copy {
      font-size: 13px;
      color: var(--muted);
    }

    .footer-links {
      display: flex; gap: 24px;
    }
    .footer-links a {
      font-size: 13px;
      color: var(--muted);
      text-decoration: none;
      transition: color 0.3s;
    }
    .footer-links a:hover { color: var(--accent); }

    /* ── ANIMATIONS ── */
    @keyframes slideDown {
      from { opacity: 0; transform: translateY(-20px); }
      to   { opacity: 1; transform: translateY(0); }
    }
    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(30px); }
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
      nav { padding: 18px 24px; }
      .nav-links { display: none; }
      #home { padding: 120px 24px 60px; }
      .section-wrap { padding: 70px 24px; }
      .services-grid { grid-template-columns: 1fr; }
      .about-grid { grid-template-columns: 1fr; gap: 40px; }
      .contact-grid { grid-template-columns: 1fr; }
      .divider-line { margin: 0 24px; }
      footer { padding: 30px 24px; flex-direction: column; text-align: center; }
      .stats-bar { gap: 28px; }
    }
  </style>
</head>
<body>

<!-- Custom Cursor -->
<div class="cursor" id="cursor"></div>
<div class="cursor-ring" id="cursorRing"></div>

<!-- ── NAVBAR ── -->
<nav>
  <div class="logo">TB Digital</div>
  <ul class="nav-links">
    <li><a href="#home">Home</a></li>
    <li><a href="#services">Services</a></li>
    <li><a href="#about">About</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#contact" class="nav-cta">Get Started</a></li>
  </ul>
</nav>

<!-- ── HERO ── -->
<section id="home">
  <div class="hero-glow"></div>
  <div class="hero-glow2"></div>
  <div class="hero-content">
    <div class="hero-badge">
      <div class="badge-dot"></div>
      Digital Marketing Agency · Pakistan
    </div>
    <h1 class="hero-title">
      We Grow Your<br/>
      Brand <span>Digitally.</span>
    </h1>
    <p class="hero-desc">
      TB Digital Solutions delivers data-driven marketing strategies that connect your brand with the right audience — and turn online presence into real business growth.
    </p>
    <div class="hero-actions">
      <a href="#services" class="btn-primary">Explore Services</a>
      <a href="#contact" class="btn-secondary">Talk to Us</a>
    </div>
    <div class="stats-bar">
      <div class="stat-item">
        <div class="stat-num">150+</div>
        <div class="stat-label">Clients Served</div>
      </div>
      <div class="stat-item">
        <div class="stat-num">5×</div>
        <div class="stat-label">Average ROI</div>
      </div>
      <div class="stat-item">
        <div class="stat-num">98%</div>
        <div class="stat-label">Client Satisfaction</div>
      </div>
      <div class="stat-item">
        <div class="stat-num">3+</div>
        <div class="stat-label">Years Experience</div>
      </div>
    </div>
  </div>
</section>

<div class="divider-line"></div>

<!-- ── SERVICES ── -->
<section id="services">
  <div class="section-wrap">
    <span class="section-tag reveal">What We Do</span>
    <h2 class="section-title reveal">Our Digital Marketing<br/>Services</h2>
    <p class="section-desc reveal">From brand awareness to lead generation — we cover every dimension of your digital presence.</p>

    <div class="services-grid reveal">
      <div class="service-card">
        <div class="service-icon">🔍</div>
        <div class="service-title">Search Engine Optimization</div>
        <div class="service-desc">Rank higher on Google with proven SEO strategies — on-page, off-page, and technical optimization tailored to your niche.</div>
      </div>
      <div class="service-card">
        <div class="service-icon">📱</div>
        <div class="service-title">Social Media Management</div>
        <div class="service-desc">Build a loyal community across Instagram, Facebook, LinkedIn & more. We create, schedule, and manage content that converts.</div>
      </div>
      <div class="service-card">
        <div class="service-icon">📣</div>
        <div class="service-title">Paid Advertising (PPC)</div>
        <div class="service-desc">Get immediate results with targeted Google Ads and Meta Ads campaigns — optimized for maximum return on every rupee spent.</div>
      </div>
      <div class="service-card">
        <div class="service-icon">✍️</div>
        <div class="service-title">Content Marketing</div>
        <div class="service-desc">Compelling blogs, videos, and copy that tell your brand story and establish you as an authority in your industry.</div>
      </div>
      <div class="service-card">
        <div class="service-icon">📧</div>
        <div class="service-title">Email Marketing</div>
        <div class="service-desc">Nurture your leads and retain customers with strategic email campaigns that deliver the right message at the right time.</div>
      </div>
      <div class="service-card">
        <div class="service-icon">📊</div>
        <div class="service-title">Analytics & Reporting</div>
        <div class="service-desc">Clear, actionable insights from your data. We track every campaign metric so you always know where your money is going.</div>
      </div>
    </div>
  </div>
</section>

<div class="divider-line"></div>

<!-- ── ABOUT ── -->
<section id="about">
  <div class="section-wrap">
    <span class="section-tag reveal">Who We Are</span>
    <h2 class="section-title reveal">Built on Strategy,<br/>Driven by Results</h2>

    <div class="about-grid">
      <div class="about-visual reveal">
        <div class="about-card">
          <div class="founder-name">Taimoor Butt</div>
          <div class="founder-role">Founder & CEO · TB Digital Solutions</div>
          <p style="font-size:15px; color:var(--muted); line-height:1.9; font-weight:300;">
            A passionate digital marketing strategist with a vision to help businesses across Pakistan and beyond build powerful, impactful online presences.
          </p>
          <div class="skill-tags">
            <span class="skill-tag">SEO Strategy</span>
            <span class="skill-tag">Paid Ads</span>
            <span class="skill-tag">Brand Building</span>
            <span class="skill-tag">Social Media</span>
            <span class="skill-tag">Growth Hacking</span>
          </div>
        </div>
      </div>

      <div class="about-text reveal">
        <p>
          TB Digital Solutions was founded with one clear mission — to make world-class digital marketing accessible to every business, from startups in Lahore to enterprises across Pakistan.
        </p>
        <div class="about-highlight">
          "We don't just run campaigns — we build digital ecosystems that generate consistent, sustainable growth for our clients."
        </div>
        <p>
          We combine creativity with data, storytelling with strategy, and passion with performance. Every client is a long-term partner, and every campaign is treated as our own.
        </p>
        <p>
          Whether you're launching a new brand or scaling an established business, we bring the expertise, tools, and dedication to take you where you want to go.
        </p>
        <a href="#contact" class="btn-primary" style="display:inline-block; margin-top:12px;">Work With Us</a>
      </div>
    </div>
  </div>
</section>

<div class="divider-line"></div>

<!-- ── CONTACT ── -->
<section id="contact">
  <div class="section-wrap">
    <span class="section-tag reveal">Get In Touch</span>
    <h2 class="section-title reveal">Let's Build Something<br/>Great Together</h2>
    <p class="section-desc reveal">Ready to grow your brand? Send us a message and we'll get back to you within 24 hours.</p>

    <div class="contact-grid">
      <div class="contact-info reveal">
        <div class="contact-item">
          <div class="contact-icon">📍</div>
          <div>
            <div class="contact-label">Location</div>
            <div class="contact-value">Lahore, Punjab, Pakistan</div>
          </div>
        </div>
        <div class="contact-item">
          <div class="contact-icon">📧</div>
          <div>
            <div class="contact-label">Email</div>
            <div class="contact-value">taimoor@tbdigital.pk</div>
          </div>
        </div>
        <div class="contact-item">
          <div class="contact-icon">📞</div>
          <div>
            <div class="contact-label">Phone / WhatsApp</div>
            <div class="contact-value">+92 300 000 0000</div>
          </div>
        </div>
        <div class="contact-item">
          <div class="contact-icon">🕐</div>
          <div>
            <div class="contact-label">Working Hours</div>
            <div class="contact-value">Mon – Sat, 9:00 AM – 7:00 PM</div>
          </div>
        </div>
      </div>

      <div class="contact-form reveal">
        <div class="form-group">
          <label class="form-label">Your Name</label>
          <input type="text" class="form-input" placeholder="John Doe" />
        </div>
        <div class="form-group">
          <label class="form-label">Email Address</label>
          <input type="email" class="form-input" placeholder="you@example.com" />
        </div>
        <div class="form-group">
          <label class="form-label">Service Needed</label>
          <input type="text" class="form-input" placeholder="e.g. SEO, Social Media..." />
        </div>
        <div class="form-group">
          <label class="form-label">Message</label>
          <textarea class="form-textarea" placeholder="Tell us about your project..."></textarea>
        </div>
        <button class="form-btn">Send Message →</button>
      </div>
    </div>
  </div>
</section>

<!-- ── FOOTER ── -->
<footer>
  <div class="footer-logo">TB Digital Solutions</div>
  <div class="footer-copy">© 2026 Taimoor Butt. All rights reserved.</div>
  <div class="footer-links">
    <a href="#home">Home</a>
    <a href="#services">Services</a>
    <a href="#about">About</a>
    <a href="#contact">Contact</a>
  </div>
</footer>

<script>
  // Custom cursor
  const cursor = document.getElementById('cursor');
  const ring = document.getElementById('cursorRing');
  let mx = 0, my = 0, rx = 0, ry = 0;
  document.addEventListener('mousemove', e => { mx = e.clientX; my = e.clientY; });
  function animCursor() {
    cursor.style.left = mx + 'px'; cursor.style.top = my + 'px';
    rx += (mx - rx) * 0.12; ry += (my - ry) * 0.12;
    ring.style.left = rx + 'px'; ring.style.top = ry + 'px';
    requestAnimationFrame(animCursor);
  }
  animCursor();

  // Scroll reveal
  const reveals = document.querySelectorAll('.reveal');
  const io = new IntersectionObserver((entries) => {
    entries.forEach((e, i) => {
      if (e.isIntersecting) {
        setTimeout(() => e.target.classList.add('visible'), i * 80);
        io.unobserve(e.target);
      }
    });
  }, { threshold: 0.1 });
  reveals.forEach(el => io.observe(el));

  // Smooth nav highlight
  document.querySelectorAll('.nav-links a').forEach(a => {
    a.addEventListener('mouseenter', () => ring.style.transform = 'translate(-50%,-50%) scale(1.5)');
    a.addEventListener('mouseleave', () => ring.style.transform = 'translate(-50%,-50%) scale(1)');
  });
</script>
</body>
</html>
