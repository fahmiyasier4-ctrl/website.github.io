# website.github.io

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>TECHSOLUTION</title>
<link href="https://fonts.googleapis.com/css2?family=Rajdhani:wght@500;600;700&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #0a0c10;
    --surface: #111318;
    --card: #161a22;
    --border: #1e2430;
    --accent: #00d4ff;
    --accent2: #7b61ff;
    --accent3: #00ff9d;
    --text: #e8eaf0;
    --muted: #6b7280;
    --danger: #ff6b35;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    font-family: 'DM Sans', sans-serif;
    background: var(--bg);
    color: var(--text);
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* Grid background */
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

  /* ---- NAVBAR ---- */
  nav {
    position: fixed;
    top: 0; left: 0; right: 0;
    z-index: 100;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 18px 40px;
    background: rgba(10,12,16,0.85);
    backdrop-filter: blur(12px);
    border-bottom: 1px solid var(--border);
  }

  .logo {
    font-family: 'Rajdhani', sans-serif;
    font-size: 26px;
    font-weight: 700;
    letter-spacing: 3px;
    color: var(--accent);
    text-shadow: 0 0 20px rgba(0,212,255,0.4);
  }

  .logo span { color: var(--text); }

  nav a {
    color: var(--muted);
    text-decoration: none;
    font-size: 14px;
    font-weight: 500;
    letter-spacing: 1px;
    text-transform: uppercase;
    transition: color 0.2s;
  }
  nav a:hover { color: var(--accent); }

  /* ---- HERO ---- */
  .hero {
    position: relative;
    z-index: 1;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    text-align: center;
    padding: 100px 20px 60px;
  }

  .hero-tag {
    display: inline-block;
    font-size: 11px;
    font-weight: 500;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: var(--accent);
    border: 1px solid rgba(0,212,255,0.3);
    padding: 6px 16px;
    border-radius: 20px;
    margin-bottom: 28px;
    background: rgba(0,212,255,0.05);
  }

  .hero h1 {
    font-family: 'Rajdhani', sans-serif;
    font-size: clamp(52px, 10vw, 96px);
    font-weight: 700;
    letter-spacing: 6px;
    line-height: 1;
    margin-bottom: 20px;
    background: linear-gradient(135deg, #fff 0%, var(--accent) 50%, var(--accent2) 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    animation: fadeUp 0.8s ease both;
  }

  .hero p {
    font-size: 16px;
    color: var(--muted);
    max-width: 520px;
    line-height: 1.7;
    margin-bottom: 12px;
    animation: fadeUp 0.8s ease 0.15s both;
  }

  .hero-info {
    display: flex;
    gap: 24px;
    align-items: center;
    justify-content: center;
    flex-wrap: wrap;
    margin-top: 20px;
    margin-bottom: 60px;
    animation: fadeUp 0.8s ease 0.25s both;
  }

  .hero-info span {
    font-size: 13px;
    color: var(--muted);
    display: flex;
    align-items: center;
    gap: 6px;
  }

  .dot {
    width: 6px; height: 6px;
    border-radius: 50%;
    background: var(--accent3);
    box-shadow: 0 0 8px var(--accent3);
    animation: pulse 2s ease-in-out infinite;
  }

  @keyframes pulse {
    0%,100% { opacity: 1; }
    50% { opacity: 0.4; }
  }

  .scroll-hint {
    font-size: 12px;
    color: var(--muted);
    letter-spacing: 2px;
    text-transform: uppercase;
    animation: fadeUp 0.8s ease 0.4s both;
  }

  /* ---- SERVICES SECTION ---- */
  .services {
    position: relative;
    z-index: 1;
    padding: 80px 20px 100px;
    max-width: 1100px;
    margin: 0 auto;
  }

  .section-label {
    font-size: 11px;
    font-weight: 500;
    letter-spacing: 4px;
    text-transform: uppercase;
    color: var(--accent);
    text-align: center;
    margin-bottom: 12px;
  }

  .section-title {
    font-family: 'Rajdhani', sans-serif;
    font-size: clamp(28px, 4vw, 42px);
    font-weight: 700;
    text-align: center;
    letter-spacing: 2px;
    margin-bottom: 60px;
    color: var(--text);
  }

  .cards-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 24px;
  }

  .card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 36px 30px;
    cursor: pointer;
    transition: transform 0.3s ease, border-color 0.3s ease, box-shadow 0.3s ease;
    position: relative;
    overflow: hidden;
    text-decoration: none;
    display: block;
  }

  .card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 3px;
    border-radius: 16px 16px 0 0;
    transition: opacity 0.3s;
    opacity: 0;
  }

  .card:hover {
    transform: translateY(-6px);
    box-shadow: 0 24px 48px rgba(0,0,0,0.4);
  }

  .card:hover::before { opacity: 1; }

  .card-1::before { background: linear-gradient(90deg, var(--accent), var(--accent2)); }
  .card-2::before { background: linear-gradient(90deg, var(--accent2), #ff6fcf); }
  .card-3::before { background: linear-gradient(90deg, var(--accent3), var(--accent)); }

  .card-1:hover { border-color: rgba(0,212,255,0.3); box-shadow: 0 24px 48px rgba(0,212,255,0.08); }
  .card-2:hover { border-color: rgba(123,97,255,0.3); box-shadow: 0 24px 48px rgba(123,97,255,0.08); }
  .card-3:hover { border-color: rgba(0,255,157,0.3); box-shadow: 0 24px 48px rgba(0,255,157,0.08); }

  .card-icon {
    width: 52px; height: 52px;
    border-radius: 12px;
    display: flex; align-items: center; justify-content: center;
    font-size: 24px;
    margin-bottom: 22px;
  }

  .icon-1 { background: rgba(0,212,255,0.1); }
  .icon-2 { background: rgba(123,97,255,0.1); }
  .icon-3 { background: rgba(0,255,157,0.1); }

  .card-num {
    position: absolute;
    top: 28px; right: 28px;
    font-family: 'Rajdhani', sans-serif;
    font-size: 13px;
    font-weight: 600;
    letter-spacing: 2px;
    color: var(--border);
  }

  .card h3 {
    font-family: 'Rajdhani', sans-serif;
    font-size: 22px;
    font-weight: 700;
    letter-spacing: 1px;
    margin-bottom: 10px;
    color: var(--text);
  }

  .card p {
    font-size: 14px;
    color: var(--muted);
    line-height: 1.6;
    margin-bottom: 28px;
  }

  .card-arrow {
    display: flex;
    align-items: center;
    gap: 8px;
    font-size: 13px;
    font-weight: 500;
    letter-spacing: 1px;
    text-transform: uppercase;
    transition: gap 0.2s;
  }

  .c1 .card-arrow { color: var(--accent); }
  .c2 .card-arrow { color: var(--accent2); }
  .c3 .card-arrow { color: var(--accent3); }

  .card:hover .card-arrow { gap: 14px; }

  /* ---- SERVICE DETAIL PAGES ---- */
  .service-page {
    display: none;
    position: relative;
    z-index: 1;
    min-height: 100vh;
    padding: 120px 20px 80px;
    max-width: 800px;
    margin: 0 auto;
    animation: fadeUp 0.5s ease both;
  }

  .service-page.active { display: block; }

  .back-btn {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    font-size: 13px;
    color: var(--muted);
    cursor: pointer;
    margin-bottom: 48px;
    transition: color 0.2s;
    letter-spacing: 1px;
    text-transform: uppercase;
    background: none;
    border: none;
    font-family: 'DM Sans', sans-serif;
  }
  .back-btn:hover { color: var(--accent); }

  .service-header {
    margin-bottom: 48px;
  }

  .service-header .badge {
    display: inline-block;
    font-size: 11px;
    font-weight: 500;
    letter-spacing: 3px;
    text-transform: uppercase;
    padding: 5px 14px;
    border-radius: 20px;
    margin-bottom: 20px;
  }

  .b1 { color: var(--accent); background: rgba(0,212,255,0.08); border: 1px solid rgba(0,212,255,0.2); }
  .b2 { color: var(--accent2); background: rgba(123,97,255,0.08); border: 1px solid rgba(123,97,255,0.2); }
  .b3 { color: var(--accent3); background: rgba(0,255,157,0.08); border: 1px solid rgba(0,255,157,0.2); }

  .service-header h2 {
    font-family: 'Rajdhani', sans-serif;
    font-size: clamp(32px, 6vw, 52px);
    font-weight: 700;
    letter-spacing: 2px;
    margin-bottom: 14px;
    color: var(--text);
  }

  .service-header p {
    font-size: 15px;
    color: var(--muted);
    line-height: 1.7;
    max-width: 560px;
  }

  .tech-label {
    font-size: 11px;
    font-weight: 500;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: var(--muted);
    margin-bottom: 20px;
  }

  .tech-cards {
    display: grid;
    gap: 16px;
  }

  .tech-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 24px 28px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 16px;
    transition: border-color 0.2s;
  }

  .tech-card:hover { border-color: rgba(255,255,255,0.1); }

  .tech-info { display: flex; align-items: center; gap: 16px; }

  .tech-avatar {
    width: 44px; height: 44px;
    border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    font-family: 'Rajdhani', sans-serif;
    font-size: 18px;
    font-weight: 700;
    flex-shrink: 0;
  }

  .av1 { background: rgba(0,212,255,0.12); color: var(--accent); }
  .av2 { background: rgba(123,97,255,0.12); color: var(--accent2); }
  .av3 { background: rgba(0,255,157,0.12); color: var(--accent3); }

  .tech-name {
    font-size: 16px;
    font-weight: 500;
    color: var(--text);
    margin-bottom: 4px;
  }

  .tech-role {
    font-size: 12px;
    color: var(--muted);
    letter-spacing: 0.5px;
  }

  .call-btn {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    padding: 10px 20px;
    border-radius: 8px;
    font-size: 13px;
    font-weight: 500;
    text-decoration: none;
    transition: opacity 0.2s, transform 0.2s;
    white-space: nowrap;
    flex-shrink: 0;
  }

  .call-btn:hover { opacity: 0.85; transform: scale(1.03); }

  .btn-1 { background: rgba(0,212,255,0.12); color: var(--accent); border: 1px solid rgba(0,212,255,0.25); }
  .btn-2 { background: rgba(123,97,255,0.12); color: var(--accent2); border: 1px solid rgba(123,97,255,0.25); }
  .btn-3 { background: rgba(0,255,157,0.12); color: var(--accent3); border: 1px solid rgba(0,255,157,0.25); }

  /* ---- FOOTER / INFO ---- */
  .info-strip {
    position: relative;
    z-index: 1;
    background: var(--surface);
    border-top: 1px solid var(--border);
    padding: 48px 40px;
    display: flex;
    flex-wrap: wrap;
    gap: 32px;
    justify-content: space-between;
    align-items: flex-start;
  }

  .info-block h4 {
    font-size: 11px;
    font-weight: 500;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: var(--accent);
    margin-bottom: 10px;
  }

  .info-block p {
    font-size: 14px;
    color: var(--muted);
    line-height: 1.7;
    max-width: 320px;
  }

  .footer-logo {
    font-family: 'Rajdhani', sans-serif;
    font-size: 13px;
    font-weight: 600;
    letter-spacing: 3px;
    color: var(--muted);
    text-align: center;
    padding: 20px;
    border-top: 1px solid var(--border);
    position: relative;
    z-index: 1;
  }

  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(20px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  /* ---- HOMEPAGE ---- */
  #home { display: block; }

  @media (max-width: 600px) {
    nav { padding: 16px 20px; }
    .info-strip { padding: 36px 20px; }
    .tech-card { flex-direction: column; align-items: flex-start; }
  }
</style>
</head>
<body>

<nav>
  <div class="logo">TECH<span>SOLUTION</span></div>
  <a href="#" onclick="showHome()">Home</a>
</nav>

<!-- HOME PAGE -->
<div id="home">
  <section class="hero">
    <div class="hero-tag">Trusted Tech Service — Beranang, Selangor</div>
    <h1>TECHSOLUTION</h1>
    <p>We provide professional repair and electronic services. Choose a service below to meet your technician.</p>
    <div class="hero-info">
      <span><span class="dot"></span> Open Everyday</span>
      <span>⏰ 8:00 AM – 11:00 PM</span>
      <span>📍 Bandar Kesuma, Beranang</span>
    </div>
    <div class="scroll-hint">↓ Select a service</div>
  </section>

  <section class="services">
    <div class="section-label">What We Do</div>
    <div class="section-title">OUR SERVICES</div>
    <div class="cards-grid">

      <a class="card card-1 c1" href="#" onclick="showService('s1'); return false;">
        <div class="card-num">01</div>
        <div class="card-icon icon-1">📱</div>
        <h3>LCD Replacement</h3>
        <p>Professional mobile phone screen replacement with quality parts and fast turnaround.</p>
        <div class="card-arrow">View Technicians <span>→</span></div>
      </a>

      <a class="card card-2 c2" href="#" onclick="showService('s2'); return false;">
        <div class="card-num">02</div>
        <div class="card-icon icon-2">💻</div>
        <h3>Laptop Cleaning</h3>
        <p>Deep cleaning and maintenance for laptops to improve performance and extend lifespan.</p>
        <div class="card-arrow">View Technicians <span>→</span></div>
      </a>

      <a class="card card-3 c3" href="#" onclick="showService('s3'); return false;">
        <div class="card-num">03</div>
        <div class="card-icon icon-3">🔌</div>
        <h3>Electronic Components</h3>
        <p>Supplier of quality electronic components for repairs, projects, and replacements.</p>
        <div class="card-arrow">View Technicians <span>→</span></div>
      </a>

    </div>
  </section>

  <div class="info-strip">
    <div class="info-block">
      <h4>Address</h4>
      <p>Lot 2333, Jalan Kajang/Seremban,<br>Bandar Sri Kesuma, 43700 Beranang, Selangor</p>
    </div>
    <div class="info-block">
      <h4>Opening Hours</h4>
      <p>Every Day<br>8:00 AM – 11:00 PM</p>
    </div>
    <div class="info-block">
      <h4>Services</h4>
      <p>LCD Replacement (Mobile)<br>Laptop Cleaning<br>Electronic Component Provider</p>
    </div>
  </div>
  <div class="footer-logo">© 2025 TECHSOLUTION · ALL RIGHTS RESERVED</div>
</div>

<!-- SERVICE 1: LCD Replacement -->
<div id="s1" class="service-page">
  <button class="back-btn" onclick="showHome()">← Back to Services</button>
  <div class="service-header">
    <div class="badge b1">Service 01</div>
    <h2>LCD Replacement</h2>
    <p>Expert mobile phone screen replacement. Our technicians use quality parts to restore your display to perfect condition.</p>
  </div>
  <div class="tech-label">Our Technicians</div>
  <div class="tech-cards">
    <div class="tech-card">
      <div class="tech-info">
        <div class="tech-avatar av1">YZ</div>
        <div>
          <div class="tech-name">Yazid Zaidan</div>
          <div class="tech-role">LCD Replacement Specialist</div>
        </div>
      </div>
      <a class="call-btn btn-1" href="tel:01111111111">📞 011-1111111</a>
    </div>
    <div class="tech-card">
      <div class="tech-info">
        <div class="tech-avatar av1">YF</div>
        <div>
          <div class="tech-name">Yasier Fahmi</div>
          <div class="tech-role">LCD Replacement Specialist</div>
        </div>
      </div>
      <a class="call-btn btn-1" href="tel:0149473982">📞 014-9473982</a>
    </div>
  </div>
</div>

<!-- SERVICE 2: Laptop Cleaning -->
<div id="s2" class="service-page">
  <button class="back-btn" onclick="showHome()">← Back to Services</button>
  <div class="service-header">
    <div class="badge b2">Service 02</div>
    <h2>Laptop Cleaning</h2>
    <p>Professional deep cleaning and internal maintenance service to keep your laptop running cool and efficiently.</p>
  </div>
  <div class="tech-label">Our Technician</div>
  <div class="tech-cards">
    <div class="tech-card">
      <div class="tech-info">
        <div class="tech-avatar av2">DJ</div>
        <div>
          <div class="tech-name">Denish Jeffry</div>
          <div class="tech-role">Laptop Cleaning Specialist</div>
        </div>
      </div>
      <a class="call-btn btn-2" href="tel:01112111111">📞 011-1211111</a>
    </div>
  </div>
</div>

<!-- SERVICE 3: Electronic Components -->
<div id="s3" class="service-page">
  <button class="back-btn" onclick="showHome()">← Back to Services</button>
  <div class="service-header">
    <div class="badge b3">Service 03</div>
    <h2>Electronic Components</h2>
    <p>We supply quality electronic components for all types of repair works, DIY projects, and replacements.</p>
  </div>
  <div class="tech-label">Our Technicians</div>
  <div class="tech-cards">
    <div class="tech-card">
      <div class="tech-info">
        <div class="tech-avatar av3">AH</div>
        <div>
          <div class="tech-name">Afiq Hakimi</div>
          <div class="tech-role">Component Specialist</div>
        </div>
      </div>
      <a class="call-btn btn-3" href="tel:01111112111">📞 011-1112111</a>
    </div>
    <div class="tech-card">
      <div class="tech-info">
        <div class="tech-avatar av3">RA</div>
        <div>
          <div class="tech-name">Raif Adham</div>
          <div class="tech-role">Component Specialist</div>
        </div>
      </div>
      <a class="call-btn btn-3" href="tel:0141111111">📞 014-1111111</a>
    </div>
  </div>
</div>

<script>
  function showService(id) {
    document.getElementById('home').style.display = 'none';
    document.querySelectorAll('.service-page').forEach(p => p.classList.remove('active'));
    document.getElementById(id).classList.add('active');
    window.scrollTo({ top: 0, behavior: 'smooth' });
  }

  function showHome() {
    document.querySelectorAll('.service-page').forEach(p => p.classList.remove('active'));
    document.getElementById('home').style.display = 'block';
    window.scrollTo({ top: 0, behavior: 'smooth' });
  }
</script>
</body>
</html>
