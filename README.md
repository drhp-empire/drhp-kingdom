# drhp-kingdom<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>DRHP EMPIRE — Audio Premium</title>
  <link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=DM+Sans:ital,wght@0,300;0,400;0,500;0,700;1,300&display=swap" rel="stylesheet"/>
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    :root {
      --black: #080808;
      --dark: #111111;
      --card: #161616;
      --border: #252525;
      --accent: #FF6B00;
      --accent2: #FFB347;
      --white: #F5F5F5;
      --muted: #888;
      --success: #22c55e;
    }

    html { scroll-behavior: smooth; }

    body {
      background: var(--black);
      color: var(--white);
      font-family: 'DM Sans', sans-serif;
      font-weight: 300;
      overflow-x: hidden;
      cursor: none;
    }

    /* CUSTOM CURSOR */
    .cursor {
      width: 12px; height: 12px;
      background: var(--accent);
      border-radius: 50%;
      position: fixed; top: 0; left: 0;
      pointer-events: none;
      z-index: 9999;
      transition: transform 0.15s ease;
      mix-blend-mode: difference;
    }
    .cursor-ring {
      width: 36px; height: 36px;
      border: 1px solid var(--accent);
      border-radius: 50%;
      position: fixed; top: 0; left: 0;
      pointer-events: none;
      z-index: 9998;
      transition: transform 0.35s ease, width 0.2s, height 0.2s;
      opacity: 0.5;
    }

    /* SCROLLBAR */
    ::-webkit-scrollbar { width: 4px; }
    ::-webkit-scrollbar-track { background: var(--black); }
    ::-webkit-scrollbar-thumb { background: var(--accent); border-radius: 2px; }

    /* NOISE OVERLAY */
    body::before {
      content: '';
      position: fixed; inset: 0;
      background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='1'/%3E%3C/svg%3E");
      opacity: 0.025;
      pointer-events: none;
      z-index: 1000;
    }

    /* NAV */
    nav {
      position: fixed; top: 0; left: 0; right: 0;
      z-index: 100;
      display: flex; align-items: center; justify-content: space-between;
      padding: 1.2rem 3rem;
      background: rgba(8,8,8,0.85);
      backdrop-filter: blur(20px);
      border-bottom: 1px solid var(--border);
    }
    .logo {
      font-family: 'Bebas Neue', sans-serif;
      font-size: 1.8rem;
      letter-spacing: 0.12em;
      color: var(--white);
    }
    .logo span { color: var(--accent); }
    .nav-links { display: flex; gap: 2rem; list-style: none; }
    .nav-links a {
      color: var(--muted);
      text-decoration: none;
      font-size: 0.82rem;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      font-weight: 500;
      transition: color 0.2s;
    }
    .nav-links a:hover { color: var(--white); }

    /* HERO */
    .hero {
      min-height: 100vh;
      display: flex; align-items: center;
      padding: 8rem 3rem 4rem;
      position: relative;
      overflow: hidden;
    }
    .hero-bg {
      position: absolute; inset: 0;
      background: radial-gradient(ellipse at 70% 50%, rgba(255,107,0,0.08) 0%, transparent 65%),
                  radial-gradient(ellipse at 20% 80%, rgba(255,107,0,0.04) 0%, transparent 50%);
    }
    .hero-grid {
      position: absolute; inset: 0;
      background-image: linear-gradient(var(--border) 1px, transparent 1px),
                        linear-gradient(90deg, var(--border) 1px, transparent 1px);
      background-size: 60px 60px;
      opacity: 0.3;
    }
    .hero-content { position: relative; z-index: 2; max-width: 700px; }
    .hero-tag {
      display: inline-flex; align-items: center; gap: 0.5rem;
      background: rgba(255,107,0,0.1);
      border: 1px solid rgba(255,107,0,0.3);
      padding: 0.3rem 1rem;
      border-radius: 100px;
      font-size: 0.75rem;
      letter-spacing: 0.15em;
      text-transform: uppercase;
      color: var(--accent);
      margin-bottom: 2rem;
      animation: fadeUp 0.6s ease both;
    }
    .hero-tag::before { content: '●'; font-size: 0.5rem; animation: pulse 2s infinite; }
    @keyframes pulse { 0%,100%{opacity:1} 50%{opacity:0.3} }

    .hero h1 {
      font-family: 'Bebas Neue', sans-serif;
      font-size: clamp(4rem, 9vw, 8rem);
      line-height: 0.92;
      letter-spacing: 0.02em;
      animation: fadeUp 0.6s 0.1s ease both;
    }
    .hero h1 .accent { color: var(--accent); }
    .hero p {
      margin-top: 1.5rem;
      color: var(--muted);
      font-size: 1.05rem;
      line-height: 1.7;
      max-width: 480px;
      animation: fadeUp 0.6s 0.2s ease both;
    }
    .hero-cta {
      margin-top: 2.5rem;
      display: flex; gap: 1rem; flex-wrap: wrap;
      animation: fadeUp 0.6s 0.3s ease both;
    }
    .btn-primary {
      background: var(--accent);
      color: var(--black);
      border: none;
      padding: 0.85rem 2.2rem;
      font-family: 'DM Sans', sans-serif;
      font-size: 0.88rem;
      font-weight: 700;
      letter-spacing: 0.08em;
      text-transform: uppercase;
      cursor: none;
      border-radius: 4px;
      text-decoration: none;
      display: inline-block;
      transition: transform 0.2s, box-shadow 0.2s;
    }
    .btn-primary:hover {
      transform: translateY(-2px);
      box-shadow: 0 8px 30px rgba(255,107,0,0.4);
    }
    .btn-outline {
      background: transparent;
      color: var(--white);
      border: 1px solid var(--border);
      padding: 0.85rem 2.2rem;
      font-family: 'DM Sans', sans-serif;
      font-size: 0.88rem;
      font-weight: 500;
      letter-spacing: 0.08em;
      text-transform: uppercase;
      cursor: none;
      border-radius: 4px;
      text-decoration: none;
      display: inline-block;
      transition: border-color 0.2s, color 0.2s;
    }
    .btn-outline:hover { border-color: var(--accent); color: var(--accent); }

    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(24px); }
      to { opacity: 1; transform: translateY(0); }
    }

    /* HERO FLOATERS */
    .hero-floaters {
      position: absolute; inset: 0;
      z-index: 1;
      pointer-events: none;
    }
    .floater {
      position: absolute;
      border-radius: 16px;
      overflow: hidden;
      box-shadow: 0 24px 60px rgba(0,0,0,0.7);
      border: 1px solid rgba(255,107,0,0.15);
      background: rgba(20,20,20,0.6);
      backdrop-filter: blur(4px);
    }
    .floater img {
      width: 100%; height: 100%;
      object-fit: cover;
      display: block;
      filter: brightness(0.9);
    }
    .f1 {
      width: 140px; height: 160px;
      right: 8%; top: 15%;
      animation: float1 7s ease-in-out infinite;
    }
    .f2 {
      width: 180px; height: 180px;
      right: 22%; top: 40%;
      animation: float2 9s ease-in-out infinite;
    }
    .f3 {
      width: 130px; height: 130px;
      right: 5%; bottom: 20%;
      animation: float3 8s ease-in-out infinite;
    }
    .f4 {
      width: 120px; height: 120px;
      right: 30%; top: 12%;
      animation: float1 10s ease-in-out infinite reverse;
    }
    @keyframes float1 {
      0%,100% { transform: translateY(0px) rotate(-2deg); }
      50% { transform: translateY(-22px) rotate(2deg); }
    }
    @keyframes float2 {
      0%,100% { transform: translateY(0px) rotate(1deg); }
      50% { transform: translateY(-18px) rotate(-3deg); }
    }
    @keyframes float3 {
      0%,100% { transform: translateY(0px) rotate(3deg); }
      50% { transform: translateY(-26px) rotate(-1deg); }
    }
    @media (max-width: 768px) {
      .floater { display: none; }
    }

    /* STATS BAR */
    .stats {
      display: flex; gap: 0;
      border-top: 1px solid var(--border);
      border-bottom: 1px solid var(--border);
      background: var(--dark);
    }
    .stat {
      flex: 1;
      padding: 1.8rem 2rem;
      border-right: 1px solid var(--border);
      text-align: center;
    }
    .stat:last-child { border-right: none; }
    .stat-num {
      font-family: 'Bebas Neue', sans-serif;
      font-size: 2.4rem;
      color: var(--accent);
      line-height: 1;
    }
    .stat-label {
      font-size: 0.72rem;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      color: var(--muted);
      margin-top: 0.3rem;
    }

    /* SECTION HEADER */
    .section-header {
      text-align: center;
      padding: 5rem 2rem 3rem;
    }
    .section-eyebrow {
      font-size: 0.72rem;
      letter-spacing: 0.2em;
      text-transform: uppercase;
      color: var(--accent);
      margin-bottom: 1rem;
    }
    .section-title {
      font-family: 'Bebas Neue', sans-serif;
      font-size: clamp(2.5rem, 5vw, 4.5rem);
      letter-spacing: 0.04em;
      line-height: 1;
    }

    /* PRODUCTS */
    .products-section { padding: 0 2rem 6rem; }
    .products-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
      gap: 1.5px;
      max-width: 1300px;
      margin: 0 auto;
      border: 1.5px solid var(--border);
    }

    .product-card {
      background: var(--card);
      border: none;
      position: relative;
      overflow: hidden;
      display: flex;
      flex-direction: column;
      cursor: none;
      transition: background 0.3s;
    }
    .product-card::after {
      content: '';
      position: absolute; inset: 0;
      border: 2px solid var(--accent);
      opacity: 0;
      transition: opacity 0.3s;
      pointer-events: none;
    }
    .product-card:hover { background: #1a1a1a; }
    .product-card:hover::after { opacity: 1; }

    .product-badge {
      position: absolute; top: 1rem; left: 1rem;
      background: var(--accent);
      color: var(--black);
      font-size: 0.65rem;
      font-weight: 700;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      padding: 0.25rem 0.6rem;
      border-radius: 2px;
      z-index: 2;
    }

    .product-img-wrap {
      background: #1c1c1c;
      padding: 3rem 2.5rem;
      display: flex; align-items: center; justify-content: center;
      min-height: 240px;
      position: relative;
      overflow: hidden;
    }
    .product-img-wrap::before {
      content: '';
      position: absolute; inset: 0;
      background: radial-gradient(circle at 50% 50%, rgba(255,107,0,0.06), transparent 70%);
      opacity: 0;
      transition: opacity 0.3s;
    }
    .product-card:hover .product-img-wrap::before { opacity: 1; }

    .product-img {
      width: 100%; max-height: 180px;
      object-fit: contain;
      transition: transform 0.5s cubic-bezier(0.34,1.56,0.64,1);
      filter: drop-shadow(0 20px 40px rgba(0,0,0,0.6));
    }
    .product-card:hover .product-img { transform: scale(1.06) translateY(-4px); }

    .product-info {
      padding: 1.5rem;
      flex: 1;
      display: flex;
      flex-direction: column;
      border-top: 1px solid var(--border);
    }
    .product-category {
      font-size: 0.68rem;
      letter-spacing: 0.15em;
      text-transform: uppercase;
      color: var(--accent);
      margin-bottom: 0.5rem;
    }
    .product-name {
      font-family: 'Bebas Neue', sans-serif;
      font-size: 1.6rem;
      letter-spacing: 0.04em;
      line-height: 1.1;
      margin-bottom: 0.5rem;
    }
    .product-desc {
      font-size: 0.83rem;
      color: var(--muted);
      line-height: 1.6;
      flex: 1;
      margin-bottom: 1.2rem;
    }
    .product-footer {
      display: flex;
      align-items: center;
      justify-content: space-between;
    }
    .product-price {
      font-family: 'Bebas Neue', sans-serif;
      font-size: 2rem;
      color: var(--white);
      letter-spacing: 0.04em;
    }
    .product-price span {
      font-family: 'DM Sans', sans-serif;
      font-size: 0.75rem;
      color: var(--muted);
      font-weight: 300;
      margin-left: 0.2rem;
    }
    .btn-buy {
      background: transparent;
      border: 1px solid var(--accent);
      color: var(--accent);
      padding: 0.55rem 1.2rem;
      font-size: 0.78rem;
      font-weight: 600;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      border-radius: 3px;
      cursor: none;
      transition: background 0.2s, color 0.2s, transform 0.2s;
      font-family: 'DM Sans', sans-serif;
    }
    .btn-buy:hover {
      background: var(--accent);
      color: var(--black);
      transform: scale(1.04);
    }

    /* FEATURES STRIP */
    .features-strip {
      display: flex;
      gap: 0;
      background: var(--dark);
      border-top: 1px solid var(--border);
      border-bottom: 1px solid var(--border);
      overflow: hidden;
    }
    .feature {
      flex: 1;
      padding: 2rem;
      border-right: 1px solid var(--border);
      display: flex;
      align-items: center;
      gap: 1rem;
    }
    .feature:last-child { border-right: none; }
    .feature-icon {
      font-size: 1.6rem;
      flex-shrink: 0;
    }
    .feature-title {
      font-size: 0.85rem;
      font-weight: 700;
      margin-bottom: 0.2rem;
    }
    .feature-desc {
      font-size: 0.75rem;
      color: var(--muted);
    }

    /* ORDER FORM */
    .order-section {
      padding: 6rem 2rem;
      max-width: 900px;
      margin: 0 auto;
    }
    .form-card {
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: 8px;
      overflow: hidden;
      box-shadow: 0 40px 80px rgba(0,0,0,0.5);
    }
    .form-header {
      background: linear-gradient(135deg, #1a1a1a, #111);
      padding: 2.5rem 3rem;
      border-bottom: 1px solid var(--border);
      position: relative;
      overflow: hidden;
    }
    .form-header::after {
      content: '';
      position: absolute; right: -60px; top: -60px;
      width: 200px; height: 200px;
      background: radial-gradient(circle, rgba(255,107,0,0.12), transparent 70%);
      border-radius: 50%;
    }
    .form-header h2 {
      font-family: 'Bebas Neue', sans-serif;
      font-size: 2.4rem;
      letter-spacing: 0.06em;
    }
    .form-header p { color: var(--muted); font-size: 0.88rem; margin-top: 0.3rem; }

    .form-body { padding: 2.5rem 3rem; }

    .form-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 1.2rem;
    }
    .form-group { display: flex; flex-direction: column; }
    .form-group.full { grid-column: 1 / -1; }

    label {
      font-size: 0.72rem;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      color: var(--muted);
      margin-bottom: 0.5rem;
      font-weight: 500;
    }
    input, select, textarea {
      background: var(--dark);
      border: 1px solid var(--border);
      color: var(--white);
      padding: 0.85rem 1rem;
      font-family: 'DM Sans', sans-serif;
      font-size: 0.9rem;
      border-radius: 4px;
      outline: none;
      transition: border-color 0.2s, box-shadow 0.2s;
      width: 100%;
      cursor: none;
    }
    input::placeholder, textarea::placeholder { color: #444; }
    input:focus, select:focus, textarea:focus {
      border-color: var(--accent);
      box-shadow: 0 0 0 3px rgba(255,107,0,0.1);
    }
    select { appearance: none; cursor: none; }
    select option { background: var(--dark); }
    textarea { resize: vertical; min-height: 80px; }

    .form-divider {
      font-family: 'Bebas Neue', sans-serif;
      font-size: 1rem;
      letter-spacing: 0.15em;
      color: var(--accent);
      margin: 1.8rem 0 1.2rem;
      display: flex; align-items: center; gap: 1rem;
    }
    .form-divider::after {
      content: '';
      flex: 1;
      height: 1px;
      background: var(--border);
    }

    .product-select-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 0.8rem;
      margin-bottom: 1.5rem;
    }
    .product-option {
      border: 1px solid var(--border);
      border-radius: 4px;
      padding: 1rem;
      cursor: none;
      transition: border-color 0.2s, background 0.2s;
      display: flex; align-items: center; gap: 0.8rem;
      position: relative;
    }
    .product-option:hover { border-color: rgba(255,107,0,0.4); background: rgba(255,107,0,0.03); }
    .product-option.selected { border-color: var(--accent); background: rgba(255,107,0,0.06); }
    .product-option input[type="checkbox"] {
      position: absolute; opacity: 0; width: 0; height: 0;
    }
    .checkbox-custom {
      width: 18px; height: 18px;
      border: 1px solid var(--border);
      border-radius: 3px;
      display: flex; align-items: center; justify-content: center;
      flex-shrink: 0;
      transition: background 0.2s, border-color 0.2s;
      font-size: 0.7rem;
    }
    .product-option.selected .checkbox-custom {
      background: var(--accent);
      border-color: var(--accent);
      color: var(--black);
    }
    .opt-info { flex: 1; }
    .opt-name { font-size: 0.82rem; font-weight: 500; line-height: 1.2; }
    .opt-price { font-size: 0.78rem; color: var(--accent); font-weight: 700; margin-top: 0.2rem; }

    .order-summary {
      background: var(--dark);
      border: 1px solid var(--border);
      border-radius: 4px;
      padding: 1.2rem 1.5rem;
      margin-bottom: 1.5rem;
    }
    .summary-row {
      display: flex; justify-content: space-between;
      font-size: 0.85rem;
      color: var(--muted);
      padding: 0.3rem 0;
    }
    .summary-total {
      display: flex; justify-content: space-between;
      font-size: 1.1rem;
      font-weight: 700;
      padding-top: 0.8rem;
      margin-top: 0.8rem;
      border-top: 1px solid var(--border);
      color: var(--white);
    }
    .summary-total .price { color: var(--accent); font-family: 'Bebas Neue', sans-serif; font-size: 1.5rem; }

    .btn-submit {
      width: 100%;
      background: var(--accent);
      color: var(--black);
      border: none;
      padding: 1.1rem;
      font-family: 'DM Sans', sans-serif;
      font-size: 0.92rem;
      font-weight: 700;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      border-radius: 4px;
      cursor: none;
      transition: transform 0.2s, box-shadow 0.2s, background 0.2s;
    }
    .btn-submit:hover {
      transform: translateY(-2px);
      box-shadow: 0 12px 40px rgba(255,107,0,0.5);
      background: var(--accent2);
    }

    /* SUCCESS MESSAGE */
    .success-overlay {
      display: none;
      position: fixed; inset: 0;
      background: rgba(0,0,0,0.85);
      z-index: 500;
      align-items: center;
      justify-content: center;
      backdrop-filter: blur(8px);
    }
    .success-overlay.show { display: flex; }
    .success-box {
      background: var(--card);
      border: 1px solid var(--success);
      border-radius: 12px;
      padding: 3rem;
      text-align: center;
      max-width: 420px;
      animation: popIn 0.4s cubic-bezier(0.34,1.56,0.64,1) both;
    }
    @keyframes popIn {
      from { opacity: 0; transform: scale(0.8); }
      to { opacity: 1; transform: scale(1); }
    }
    .success-icon { font-size: 4rem; margin-bottom: 1rem; }
    .success-box h3 { font-family: 'Bebas Neue', sans-serif; font-size: 2rem; color: var(--success); margin-bottom: 0.5rem; }
    .success-box p { color: var(--muted); font-size: 0.9rem; line-height: 1.6; }
    .success-box button {
      margin-top: 1.5rem;
      background: var(--success);
      color: var(--black);
      border: none;
      padding: 0.8rem 2rem;
      font-family: 'DM Sans', sans-serif;
      font-weight: 700;
      font-size: 0.85rem;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      border-radius: 4px;
      cursor: none;
    }

    /* FOOTER */
    footer {
      border-top: 1px solid var(--border);
      padding: 2.5rem 3rem;
      display: flex;
      align-items: center;
      justify-content: space-between;
      background: var(--dark);
    }
    .footer-logo {
      font-family: 'Bebas Neue', sans-serif;
      font-size: 1.4rem;
      letter-spacing: 0.1em;
    }
    .footer-logo span { color: var(--accent); }
    footer p { color: var(--muted); font-size: 0.78rem; }
    .footer-social { display: flex; gap: 1rem; }
    .social-btn {
      width: 36px; height: 36px;
      border: 1px solid var(--border);
      border-radius: 50%;
      display: flex; align-items: center; justify-content: center;
      color: var(--muted);
      text-decoration: none;
      font-size: 0.8rem;
      transition: border-color 0.2s, color 0.2s;
      cursor: none;
    }
    .social-btn:hover { border-color: var(--accent); color: var(--accent); }

    /* TICKER */
    .ticker-wrap {
      overflow: hidden;
      background: var(--accent);
      padding: 0.6rem 0;
    }
    .ticker {
      display: flex;
      width: max-content;
      animation: ticker 18s linear infinite;
    }
    .ticker-item {
      white-space: nowrap;
      padding: 0 2rem;
      font-family: 'Bebas Neue', sans-serif;
      font-size: 0.9rem;
      letter-spacing: 0.15em;
      color: var(--black);
    }
    .ticker-sep { color: rgba(0,0,0,0.4); }
    @keyframes ticker {
      from { transform: translateX(0); }
      to { transform: translateX(-50%); }
    }

    .product-price-old {
      font-size: 0.82rem;
      color: var(--muted);
      text-decoration: line-through;
      margin-bottom: 0.1rem;
    }
    .product-footer { align-items: flex-end; }
    /* MERCADO PAGO */
    .mp-banner {
      background: linear-gradient(135deg, rgba(0,158,227,0.08), rgba(0,158,227,0.03));
      border: 1px solid rgba(0,158,227,0.25);
      border-radius: 6px;
      padding: 1rem 1.4rem;
      display: flex;
      align-items: center;
      gap: 1.2rem;
      margin-bottom: 1.2rem;
      flex-wrap: wrap;
    }
    .mp-logo {
      display: flex;
      align-items: center;
      gap: 0.6rem;
      flex-shrink: 0;
    }
    .mp-logo span {
      font-weight: 700;
      font-size: 0.95rem;
      color: #009EE3;
    }
    .mp-banner p {
      font-size: 0.8rem;
      color: var(--muted);
    }

    .mp-products-label {
      font-size: 0.72rem;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      color: var(--muted);
      margin-bottom: 0.75rem;
      font-weight: 500;
    }

    .mp-links-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 0.8rem;
      margin-bottom: 1rem;
    }

    .mp-link-card {
      display: flex;
      align-items: center;
      gap: 0.9rem;
      background: var(--dark);
      border: 1px solid var(--border);
      border-radius: 6px;
      padding: 1rem 1.1rem;
      text-decoration: none;
      color: var(--white);
      transition: border-color 0.2s, background 0.2s, transform 0.2s, box-shadow 0.2s;
      position: relative;
      overflow: hidden;
    }
    .mp-link-card::before {
      content: '';
      position: absolute; left: 0; top: 0; bottom: 0;
      width: 3px;
      background: #009EE3;
      border-radius: 6px 0 0 6px;
      opacity: 0;
      transition: opacity 0.2s;
    }
    .mp-link-card:hover {
      border-color: #009EE3;
      background: rgba(0,158,227,0.06);
      transform: translateY(-2px);
      box-shadow: 0 8px 24px rgba(0,158,227,0.15);
    }
    .mp-link-card:hover::before { opacity: 1; }
    .mp-link-card:hover .mp-link-arrow { color: #009EE3; transform: translateX(3px); }

    .mp-link-icon { font-size: 1.5rem; flex-shrink: 0; }
    .mp-link-info { flex: 1; }
    .mp-link-name { font-size: 0.88rem; font-weight: 600; }
    .mp-link-price { font-size: 0.82rem; color: #009EE3; font-weight: 700; margin-top: 0.15rem; }
    .mp-link-arrow {
      color: var(--muted);
      flex-shrink: 0;
      transition: color 0.2s, transform 0.2s;
    }

    .mp-note {
      display: flex;
      align-items: flex-start;
      gap: 0.5rem;
      background: rgba(255,255,255,0.03);
      border: 1px solid var(--border);
      border-radius: 4px;
      padding: 0.8rem 1rem;
      font-size: 0.78rem;
      color: var(--muted);
      line-height: 1.5;
    }
    .mp-note span { flex-shrink: 0; }

    /* RESPONSIVE */
    @media (max-width: 768px) {
      nav { padding: 1rem 1.5rem; }
      .nav-links { display: none; }
      .hero { padding: 7rem 1.5rem 3rem; }
      .stat { padding: 1.2rem 1rem; }
      .stat-num { font-size: 1.8rem; }
      .form-body { padding: 1.5rem; }
      .form-header { padding: 1.5rem; }
      .form-grid { grid-template-columns: 1fr; }
      .product-select-grid { grid-template-columns: 1fr; }
      .mp-links-grid { grid-template-columns: 1fr; }
      .features-strip { flex-direction: column; }
      .feature { border-right: none; border-bottom: 1px solid var(--border); }
      footer { flex-direction: column; gap: 1rem; text-align: center; }
      .products-grid { grid-template-columns: 1fr; }
    }

    /* WHATSAPP FLOTANTE */
    .wa-float {
      position: fixed;
      bottom: 2rem;
      right: 2rem;
      z-index: 999;
      display: flex;
      align-items: center;
      gap: 0.7rem;
      background: #25D366;
      color: white;
      text-decoration: none;
      padding: 0.75rem 1.2rem 0.75rem 0.85rem;
      border-radius: 100px;
      box-shadow: 0 8px 32px rgba(37,211,102,0.45), 0 2px 8px rgba(0,0,0,0.3);
      font-family: 'DM Sans', sans-serif;
      font-size: 0.88rem;
      font-weight: 700;
      transition: transform 0.25s cubic-bezier(0.34,1.56,0.64,1), box-shadow 0.25s;
      animation: waPop 0.6s 1.5s cubic-bezier(0.34,1.56,0.64,1) both;
    }
    .wa-float:hover {
      transform: scale(1.08) translateY(-3px);
      box-shadow: 0 16px 48px rgba(37,211,102,0.55), 0 4px 12px rgba(0,0,0,0.3);
    }
    .wa-icon {
      width: 32px; height: 32px;
      display: flex; align-items: center; justify-content: center;
      flex-shrink: 0;
      animation: waPulse 2.5s ease-in-out 2s infinite;
    }
    .wa-label { white-space: nowrap; }
    @keyframes waPop {
      from { opacity: 0; transform: scale(0.5) translateY(20px); }
      to   { opacity: 1; transform: scale(1) translateY(0); }
    }
    @keyframes waPulse {
      0%,100% { transform: scale(1); }
      50%      { transform: scale(1.15); }
    }
    @media (max-width: 768px) {
      .wa-float { bottom: 1.2rem; right: 1.2rem; padding: 0.7rem; border-radius: 50%; }
      .wa-label { display: none; }
    }

    a { cursor: none; }
    * { cursor: none !important; }
  </style>
</head>
<body>

  <div class="cursor" id="cursor"></div>
  <div class="cursor-ring" id="cursor-ring"></div>

  <!-- NAV -->
  <nav>
    <div class="logo">DRHP<span>.</span>EMPIRE</div>
    <ul class="nav-links">
      <li><a href="#productos">Productos</a></li>
      <li><a href="#pedido">Comprar</a></li>
      <li><a href="#pedido">Contacto</a></li>
    </ul>
    <a href="#pedido" class="btn-primary" style="font-size:0.78rem;padding:0.6rem 1.4rem;">Ordenar ahora</a>
  </nav>

  <!-- HERO -->
  <section class="hero">
    <div class="hero-bg"></div>
    <div class="hero-grid"></div>

    <!-- ANIMATED CANVAS BACKGROUND -->
    <canvas id="heroCanvas" style="position:absolute;inset:0;width:100%;height:100%;z-index:1;pointer-events:none;opacity:0.55;"></canvas>

    <!-- FLOATING PRODUCT IMAGES -->
    <div class="hero-floaters">
      <div class="floater f1"><img src="IMG_2442.webp" alt="JBL"/></div>
      <div class="floater f2"><img src="IMG_2423.jpeg" alt="AirPods Max"/></div>
      <div class="floater f3"><img src="IMG_2396.jpeg" alt="AirPods"/></div>
      <div class="floater f4"><img src="IMG_2375.jpeg" alt="Buds"/></div>
    </div>

    <div class="hero-content">
      <div class="hero-tag">Audio de próxima generación</div>
      <h1>SONIDO <span class="accent">SIN<br>LÍMITES</span></h1>
      <p>Tecnología de audio premium para quienes exigen lo mejor. Entrega rápida, garantía total y el sonido que cambia todo.</p>
      <div class="hero-cta">
        <a href="#productos" class="btn-primary">Ver productos</a>
        <a href="#pedido" class="btn-outline">Hacer pedido</a>
      </div>
    </div>
  </section>

  <!-- TICKER -->
  <div class="ticker-wrap">
    <div class="ticker">
      <span class="ticker-item">ENVÍO GRATIS A BOGOTÁ <span class="ticker-sep">✦</span></span>
      <span class="ticker-item">PRODUCTOS ORIGINALES <span class="ticker-sep">✦</span></span>
      <span class="ticker-item">GARANTÍA 1 AÑO <span class="ticker-sep">✦</span></span>
      <span class="ticker-item">PAGO SEGURO CON MERCADO PAGO <span class="ticker-sep">✦</span></span>
      <span class="ticker-item">SOPORTE 24/7 · 321 304 7416 <span class="ticker-sep">✦</span></span>
      <span class="ticker-item">ENVÍO GRATIS A BOGOTÁ <span class="ticker-sep">✦</span></span>
      <span class="ticker-item">PRODUCTOS ORIGINALES <span class="ticker-sep">✦</span></span>
      <span class="ticker-item">GARANTÍA 1 AÑO <span class="ticker-sep">✦</span></span>
      <span class="ticker-item">PAGO SEGURO CON MERCADO PAGO <span class="ticker-sep">✦</span></span>
      <span class="ticker-item">SOPORTE 24/7 · 321 304 7416 <span class="ticker-sep">✦</span></span>
    </div>
  </div>

  <!-- STATS -->
  <div class="stats">
    <div class="stat">
      <div class="stat-num">500+</div>
      <div class="stat-label">Clientes felices</div>
    </div>
    <div class="stat">
      <div class="stat-num">4.9★</div>
      <div class="stat-label">Calificación promedio</div>
    </div>
    <div class="stat">
      <div class="stat-num">24h</div>
      <div class="stat-label">Tiempo de envío</div>
    </div>
    <div class="stat">
      <div class="stat-num">100%</div>
      <div class="stat-label">Productos originales</div>
    </div>
  </div>

  <!-- PRODUCTS -->
  <section id="productos">
    <div class="section-header">
      <div class="section-eyebrow">Nuestro catálogo</div>
      <h2 class="section-title">PRODUCTOS DESTACADOS</h2>
    </div>
    <div class="products-section">
      <div class="products-grid">

        <div class="product-card">
          <div class="product-badge">🔥 Popular</div>
          <div class="product-img-wrap">
            <img src="IMG_2442.webp" alt="JBL Clip 5" class="product-img" onerror="this.style.display='none'"/>
            <div style="font-size:5rem;display:none" class="emoji-fallback">🔊</div>
          </div>
          <div class="product-info">
            <div class="product-category">Bluetooth Speaker</div>
            <div class="product-name">JBL CLIP 5</div>
            <div class="product-desc">Sonido potente en formato ultraportátil. Resistente al agua IP67, mosquetón integrado y 12h de batería. Llévalo a todos lados.</div>
            <div class="product-footer">
              <div>
                <div class="product-price-old">$120.000 COP</div>
                <div class="product-price">$90.000 <span>COP</span></div>
              </div>
              <button class="btn-buy" onclick="selectProduct('JBL Clip 5', 90000)">Comprar</button>
            </div>
          </div>
        </div>

        <div class="product-card">
          <div class="product-badge">⭐ Premium</div>
          <div class="product-img-wrap">
            <img src="IMG_2423.jpeg" alt="AirPods Max" class="product-img" onerror="this.style.display='none'"/>
          </div>
          <div class="product-info">
            <div class="product-category">Over-ear Headphones</div>
            <div class="product-name">AIRPODS MAX</div>
            <div class="product-desc">Cancelación de ruido activa de clase mundial. Sonido espacial personalizado y diseño de aluminio premium. La experiencia definitiva.</div>
            <div class="product-footer">
              <div>
                <div class="product-price-old">$160.000 COP</div>
                <div class="product-price">$119.900 <span>COP</span></div>
              </div>
              <button class="btn-buy" onclick="selectProduct('AirPods Max', 119900)">Comprar</button>
            </div>
          </div>
        </div>

        <div class="product-card">
          <div class="product-badge">🆕 Nuevo</div>
          <div class="product-img-wrap">
            <img src="IMG_2396.jpeg" alt="AirPods 4" class="product-img" onerror="this.style.display='none'"/>
          </div>
          <div class="product-info">
            <div class="product-category">True Wireless</div>
            <div class="product-name">AIRPODS 3RA GEN</div>
            <div class="product-desc">La nueva generación de AirPods. Ajuste personalizado, audio adaptativo y hasta 30 horas de reproducción total con el estuche.</div>
            <div class="product-footer">
              <div>
                <div class="product-price-old">$85.000 COP</div>
                <div class="product-price">$60.000 <span>COP</span></div>
              </div>
              <button class="btn-buy" onclick="selectProduct('AirPods 3ra Gen', 60000)">Comprar</button>
            </div>
          </div>
        </div>

        <div class="product-card">
          <div class="product-img-wrap">
            <img src="IMG_2375.jpeg" alt="Samsung Galaxy Buds2 Pro" class="product-img" onerror="this.style.display='none'"/>
          </div>
          <div class="product-info">
            <div class="product-category">True Wireless ANC</div>
            <div class="product-name">GALAXY BUDS2 PRO</div>
            <div class="product-desc">Sonido Hi-Fi de 24 bits, cancelación de ruido inteligente y diseño ergonómico. La mejor opción para el ecosistema Samsung.</div>
            <div class="product-footer">
              <div>
                <div class="product-price-old">$130.000 COP</div>
                <div class="product-price">$95.000 <span>COP</span></div>
              </div>
              <button class="btn-buy" onclick="selectProduct('Galaxy Buds2 Pro', 95000)">Comprar</button>
            </div>
          </div>
        </div>

      </div>
    </div>
  </section>

  <!-- FEATURES -->
  <div class="features-strip">
    <div class="feature">
      <div class="feature-icon">🚀</div>
      <div>
        <div class="feature-title">Envío Gratis a Bogotá</div>
        <div class="feature-desc">Domicilio sin costo en toda la ciudad</div>
      </div>
    </div>
    <div class="feature">
      <div class="feature-icon">🛡️</div>
      <div>
        <div class="feature-title">Garantía Oficial</div>
        <div class="feature-desc">1 año de garantía en todos los productos</div>
      </div>
    </div>
    <div class="feature">
      <div class="feature-icon">💳</div>
      <div>
        <div class="feature-title">Pago Seguro</div>
        <div class="feature-desc">Múltiples métodos de pago disponibles</div>
      </div>
    </div>
    <div class="feature">
      <div class="feature-icon">🔄</div>
      <div>
        <div class="feature-title">Devoluciones</div>
        <div class="feature-desc">30 días para cambios sin preguntas</div>
      </div>
    </div>
  </div>

  <!-- ORDER FORM -->
  <section id="pedido" class="order-section">
    <div class="section-header" style="padding-top:0;">
      <div class="section-eyebrow">Formulario de compra</div>
      <h2 class="section-title">HACER MI PEDIDO</h2>
    </div>

    <div class="form-card">
      <div class="form-header">
        <h2>Datos de tu pedido</h2>
        <p>Completa el formulario y nos ponemos en contacto contigo en menos de 2 horas.</p>
      </div>
      <div class="form-body">

        <!-- PRODUCT SELECTION -->
        <div class="form-divider">Selecciona tu producto</div>
        <div class="product-select-grid" id="productSelectGrid">
          <div class="product-option" id="opt-0" onclick="toggleProduct(0, 'JBL Clip 5', 90000)">
            <input type="checkbox" id="chk-0"/>
            <div class="checkbox-custom" id="chk-visual-0">✓</div>
            <div class="opt-info">
              <div class="opt-name">JBL Clip 5</div>
              <div class="opt-price">$90.000 COP</div>
            </div>
          </div>
          <div class="product-option" id="opt-1" onclick="toggleProduct(1, 'AirPods Max', 119900)">
            <input type="checkbox" id="chk-1"/>
            <div class="checkbox-custom" id="chk-visual-1">✓</div>
            <div class="opt-info">
              <div class="opt-name">AirPods Max</div>
              <div class="opt-price">$119.900 COP</div>
            </div>
          </div>
          <div class="product-option" id="opt-2" onclick="toggleProduct(2, 'AirPods 3ra Gen', 60000)">
            <input type="checkbox" id="chk-2"/>
            <div class="checkbox-custom" id="chk-visual-2">✓</div>
            <div class="opt-info">
              <div class="opt-name">AirPods 3ra Gen</div>
              <div class="opt-price">$60.000 COP</div>
            </div>
          </div>
          <div class="product-option" id="opt-3" onclick="toggleProduct(3, 'Galaxy Buds2 Pro', 95000)">
            <input type="checkbox" id="chk-3"/>
            <div class="checkbox-custom" id="chk-visual-3">✓</div>
            <div class="opt-info">
              <div class="opt-name">Galaxy Buds2 Pro</div>
              <div class="opt-price">$95.000 COP</div>
            </div>
          </div>
        </div>

        <!-- RESUMEN -->
        <div class="order-summary">
          <div id="summaryItems">
            <div class="summary-row"><span style="color:#555;font-style:italic;">Selecciona al menos un producto</span></div>
          </div>
          <div class="summary-total">
            <span>Total estimado</span>
            <span class="price" id="summaryTotal">$0 USD</span>
          </div>
        </div>

        <!-- DATOS PERSONALES -->
        <div class="form-divider">Datos personales</div>
        <div class="form-grid">
          <div class="form-group">
            <label>Nombre *</label>
            <input type="text" id="nombre" placeholder="Tu nombre" required/>
          </div>
          <div class="form-group">
            <label>Apellido *</label>
            <input type="text" id="apellido" placeholder="Tu apellido" required/>
          </div>
          <div class="form-group">
            <label>Correo electrónico *</label>
            <input type="email" id="email" placeholder="correo@ejemplo.com" required/>
          </div>
          <div class="form-group">
            <label>Teléfono / WhatsApp *</label>
            <input type="tel" id="telefono" placeholder="+57 321 304 7416" required/>
          </div>
        </div>

        <!-- DATOS DE ENVÍO -->
        <div class="form-divider">Dirección de envío</div>
        <div class="form-grid">
          <div class="form-group full">
            <label>Calle y número *</label>
            <input type="text" id="calle" placeholder="Ej: Av. Insurgentes 1234, Col. Centro" required/>
          </div>
          <div class="form-group">
            <label>Ciudad *</label>
            <input type="text" id="ciudad" placeholder="Bogotá" required/>
          </div>
          <div class="form-group">
            <label>Estado / Provincia *</label>
            <input type="text" id="estado" placeholder="Cundinamarca" required/>
          </div>
          <div class="form-group">
            <label>Código postal *</label>
            <input type="text" id="cp" placeholder="06600" required/>
          </div>
          <div class="form-group">
            <label>País *</label>
            <select id="pais">
              <option value="MX">México</option>
              <option value="CO" selected>Colombia</option>
              <option value="AR">Argentina</option>
              <option value="CL">Chile</option>
              <option value="PE">Perú</option>
              <option value="VE">Venezuela</option>
              <option value="EC">Ecuador</option>
              <option value="US">Estados Unidos</option>
              <option value="ES">España</option>
              <option value="Otro">Otro</option>
            </select>
          </div>
          <div class="form-group full">
            <label>Referencias / Instrucciones de entrega</label>
            <textarea id="referencias" placeholder="Ej: Edificio azul, 3er piso, tocar timbre dos veces..."></textarea>
          </div>
        </div>

        <!-- MÉTODO DE PAGO -->
        <div class="form-divider">Método de pago</div>

        <!-- MERCADO PAGO BANNER -->
        <div class="mp-banner">
          <div class="mp-logo">
            <svg width="28" height="28" viewBox="0 0 48 48" fill="none"><circle cx="24" cy="24" r="24" fill="#009EE3"/><path d="M10 24c0-7.732 6.268-14 14-14s14 6.268 14 14" stroke="#fff" stroke-width="3.5" stroke-linecap="round"/><circle cx="24" cy="31" r="5" fill="#fff"/></svg>
            <span>Mercado Pago</span>
          </div>
          <p>Pago 100% seguro · Tarjeta, débito, transferencia y más</p>
        </div>

        <!-- MP PRODUCT LINKS -->
        <div class="mp-products-label">Selecciona el producto para ir a pagar:</div>
        <div class="mp-links-grid">
          <a class="mp-link-card" href="https://mpago.li/1oHZ96K" target="_blank" id="mp-0">
            <div class="mp-link-icon">🔊</div>
            <div class="mp-link-info">
              <div class="mp-link-name">JBL Clip 5</div>
              <div class="mp-link-price">$90.000 COP</div>
            </div>
            <div class="mp-link-arrow">
              <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M5 12h14M12 5l7 7-7 7"/></svg>
            </div>
          </a>
          <a class="mp-link-card" href="https://mpago.li/2mGJray" target="_blank" id="mp-1">
            <div class="mp-link-icon">🎧</div>
            <div class="mp-link-info">
              <div class="mp-link-name">AirPods Max</div>
              <div class="mp-link-price">$119.900 COP</div>
            </div>
            <div class="mp-link-arrow">
              <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M5 12h14M12 5l7 7-7 7"/></svg>
            </div>
          </a>
          <a class="mp-link-card" href="https://mpago.li/142YPcw" target="_blank" id="mp-2">
            <div class="mp-link-icon">🎵</div>
            <div class="mp-link-info">
              <div class="mp-link-name">AirPods 3ra Gen</div>
              <div class="mp-link-price">$60.000 COP</div>
            </div>
            <div class="mp-link-arrow">
              <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M5 12h14M12 5l7 7-7 7"/></svg>
            </div>
          </a>
          <a class="mp-link-card" href="https://mpago.li/1dBGNPG" target="_blank" id="mp-3">
            <div class="mp-link-icon">🎶</div>
            <div class="mp-link-info">
              <div class="mp-link-name">Galaxy Buds2 Pro</div>
              <div class="mp-link-price">$95.000 COP</div>
            </div>
            <div class="mp-link-arrow">
              <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M5 12h14M12 5l7 7-7 7"/></svg>
            </div>
          </a>
        </div>

        <div class="mp-note">
          <span>ℹ️</span> Al hacer clic serás redirigido a Mercado Pago para completar tu pago de forma segura. Luego completa tus datos de envío y confirma tu pedido.
        </div>

        <div class="form-group full" style="margin-top:1.2rem;">
          <label>Notas adicionales</label>
          <textarea id="notas" placeholder="¿Algún comentario especial sobre tu pedido?"></textarea>
        </div>

        <!-- HIDDEN FIELD para compatibilidad con validación -->
        <input type="hidden" id="pago" value="Mercado Pago"/>

        <div style="height:1.5rem;"></div>
        <button class="btn-submit" onclick="submitOrder()">✦ CONFIRMAR DATOS DE ENVÍO</button>
        <p style="text-align:center;color:var(--muted);font-size:0.75rem;margin-top:1rem;">
          Confirma tus datos y luego realiza el pago en Mercado Pago. Te contactaremos por WhatsApp en menos de 2h.
        </p>
      </div>
    </div>
  </section>

  <!-- FOOTER -->
  <footer>
    <div class="footer-logo">DRHP<span>.</span>EMPIRE</div>
    <div style="text-align:center;">
      <p style="color:var(--muted);font-size:0.78rem;">© 2026 DRHP EMPIRE — Todos los derechos reservados</p>
      <p style="color:var(--muted);font-size:0.78rem;margin-top:0.3rem;">📞 321 304 7416 &nbsp;·&nbsp; ✉️ tiben.gr@gmail.com</p>
    </div>
    <div class="footer-social">
      <a class="social-btn" href="https://wa.me/573213047416" target="_blank" title="WhatsApp">WA</a>
      <a class="social-btn" href="mailto:tiben.gr@gmail.com" title="Email">✉</a>
      <a class="social-btn" href="#" title="Instagram">IG</a>
    </div>
  </footer>

  <!-- SUCCESS OVERLAY -->
  <div class="success-overlay" id="successOverlay">
    <div class="success-box">
      <div class="success-icon">🎉</div>
      <h3>¡PEDIDO RECIBIDO!</h3>
      <p>Gracias por tu compra. Nuestro equipo se pondrá en contacto contigo en las próximas <strong>2 horas</strong> para confirmar los detalles de pago y envío.</p>
      <button onclick="closeSuccess()">Cerrar</button>
    </div>
  </div>

  <script>
    // ANIMATED CANVAS — sound waves + particles
    const canvas = document.getElementById('heroCanvas');
    const ctx = canvas.getContext('2d');
    let W, H, particles = [], waves = [];

    function resize() {
      W = canvas.width = canvas.offsetWidth;
      H = canvas.height = canvas.offsetHeight;
    }
    resize();
    window.addEventListener('resize', resize);

    // Particles
    for (let i = 0; i < 60; i++) {
      particles.push({
        x: Math.random() * 2000,
        y: Math.random() * 1000,
        r: Math.random() * 2 + 0.5,
        vx: (Math.random() - 0.5) * 0.4,
        vy: (Math.random() - 0.5) * 0.3,
        alpha: Math.random() * 0.5 + 0.1,
        pulse: Math.random() * Math.PI * 2
      });
    }

    // Sound wave rings
    for (let i = 0; i < 4; i++) {
      waves.push({ r: 80 + i * 140, alpha: 0.18 - i * 0.03, speed: 0.4 + i * 0.15 });
    }

    let t = 0;
    function drawFrame() {
      ctx.clearRect(0, 0, W, H);
      t += 0.012;

      // Animated sound wave rings (right side)
      const cx = W * 0.72, cy = H * 0.5;
      waves.forEach((w, i) => {
        const r = ((w.r + t * w.speed * 60) % (W * 0.55)) + 20;
        ctx.beginPath();
        ctx.arc(cx, cy, r, 0, Math.PI * 2);
        ctx.strokeStyle = `rgba(255,107,0,${Math.max(0, w.alpha - r / (W * 0.6))})`;
        ctx.lineWidth = 1.2;
        ctx.stroke();
      });

      // Floating particles
      particles.forEach(p => {
        p.x += p.vx;
        p.y += p.vy;
        p.pulse += 0.02;
        if (p.x < 0) p.x = W;
        if (p.x > W) p.x = 0;
        if (p.y < 0) p.y = H;
        if (p.y > H) p.y = 0;
        const a = p.alpha * (0.6 + 0.4 * Math.sin(p.pulse));
        ctx.beginPath();
        ctx.arc(p.x % W, p.y % H, p.r, 0, Math.PI * 2);
        ctx.fillStyle = `rgba(255,107,0,${a})`;
        ctx.fill();
      });

      // Horizontal scan line
      const scanY = ((t * 60) % H);
      const grad = ctx.createLinearGradient(0, scanY - 2, 0, scanY + 2);
      grad.addColorStop(0, 'transparent');
      grad.addColorStop(0.5, 'rgba(255,107,0,0.06)');
      grad.addColorStop(1, 'transparent');
      ctx.fillStyle = grad;
      ctx.fillRect(0, scanY - 2, W, 4);

      requestAnimationFrame(drawFrame);
    }
    drawFrame();
  </script>

  <script>
    // CUSTOM CURSOR
    const cursor = document.getElementById('cursor');
    const ring = document.getElementById('cursor-ring');
    let mx = 0, my = 0, rx = 0, ry = 0;
    document.addEventListener('mousemove', e => {
      mx = e.clientX; my = e.clientY;
      cursor.style.transform = `translate(${mx - 6}px, ${my - 6}px)`;
    });
    function animateRing() {
      rx += (mx - rx - 18) * 0.12;
      ry += (my - ry - 18) * 0.12;
      ring.style.transform = `translate(${rx}px, ${ry}px)`;
      requestAnimationFrame(animateRing);
    }
    animateRing();

    // PRODUCT SELECTION
    const products = [
      { name: 'JBL Clip 5', price: 90000 },
      { name: 'AirPods Max', price: 119900 },
      { name: 'AirPods 3ra Gen', price: 60000 },
      { name: 'Galaxy Buds2 Pro', price: 95000 }
    ];
    const selected = new Set();

    function toggleProduct(idx, name, price) {
      const opt = document.getElementById(`opt-${idx}`);
      const vis = document.getElementById(`chk-visual-${idx}`);
      if (selected.has(idx)) {
        selected.delete(idx);
        opt.classList.remove('selected');
      } else {
        selected.add(idx);
        opt.classList.add('selected');
      }
      updateSummary();
    }

    function updateSummary() {
      const container = document.getElementById('summaryItems');
      if (selected.size === 0) {
        container.innerHTML = '<div class="summary-row"><span style="color:#555;font-style:italic;">Selecciona al menos un producto</span></div>';
        document.getElementById('summaryTotal').textContent = '$0 COP';
        return;
      }
      let total = 0;
      let html = '';
      selected.forEach(idx => {
        const p = products[idx];
        total += p.price;
        html += `<div class="summary-row"><span>${p.name}</span><span>$${p.price.toLocaleString('es-CO')} COP</span></div>`;
      });
      container.innerHTML = html;
      document.getElementById('summaryTotal').textContent = `$${total.toLocaleString('es-CO')} COP`;
    }

    function selectProduct(name, price) {
      const idx = products.findIndex(p => p.name === name);
      if (idx !== -1) {
        document.getElementById('pedido').scrollIntoView({ behavior: 'smooth' });
        setTimeout(() => {
          if (!selected.has(idx)) toggleProduct(idx, name, price);
        }, 600);
      }
    }

    // FORM SUBMIT
    function submitOrder() {
      const required = ['nombre', 'apellido', 'email', 'telefono', 'calle', 'ciudad', 'estado', 'cp'];
      let valid = true;
      required.forEach(id => {
        const el = document.getElementById(id);
        if (!el.value.trim()) {
          el.style.borderColor = '#ff4444';
          valid = false;
          setTimeout(() => el.style.borderColor = 'var(--border)', 2000);
        }
      });
      if (selected.size === 0) {
        alert('Por favor selecciona al menos un producto.');
        return;
      }
      if (!document.getElementById('pago').value) {
        alert('Por favor selecciona un método de pago.');
        return;
      }
      if (!valid) {
        alert('Por favor completa todos los campos obligatorios.');
        return;
      }
      document.getElementById('successOverlay').classList.add('show');
    }

    function closeSuccess() {
      document.getElementById('successOverlay').classList.remove('show');
      // Reset form
      selected.clear();
      [0,1,2,3].forEach(i => {
        document.getElementById(`opt-${i}`).classList.remove('selected');
      });
      updateSummary();
      ['nombre','apellido','email','telefono','calle','ciudad','estado','cp','referencias','notas'].forEach(id => {
        const el = document.getElementById(id);
        if (el) el.value = '';
      });
    }
  </script>  <!-- WHATSAPP FLOTANTE -->
  <a class="wa-float" href="https://wa.me/573213047416?text=Hola!%20Vi%20tu%20tienda%20y%20quiero%20más%20información%20sobre%20los%20productos%20🎧" target="_blank">
    <div class="wa-icon">
      <svg width="28" height="28" viewBox="0 0 24 24" fill="white"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347z"/><path d="M12 0C5.373 0 0 5.373 0 12c0 2.123.555 4.116 1.524 5.847L.057 23.882a.5.5 0 0 0 .606.637l6.198-1.63A11.94 11.94 0 0 0 12 24c6.627 0 12-5.373 12-12S18.627 0 12 0zm0 21.894a9.87 9.87 0 0 1-5.031-1.378l-.36-.214-3.733.981.999-3.645-.235-.374A9.867 9.867 0 0 1 2.106 12C2.106 6.533 6.533 2.106 12 2.106S21.894 6.533 21.894 12 17.467 21.894 12 21.894z"/></svg>
    </div>
    <span class="wa-label">¡Escríbenos!</span>
  </a>

</body>
</html>
