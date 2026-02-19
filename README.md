<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>SR Runner \u2013 Entregas Hacienda Santa Rosa</title>
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Montserrat:wght@400;500;600;700;900&display=swap" rel="stylesheet">
<style>
  :root {
    --blue: #00b4ff;
    --cyan: #00ffcc;
    --dark: #0a0f1e;
    --dark2: #0d1a35;
    --dark3: #091528;
    --glass: rgba(255,255,255,0.04);
    --glass-border: rgba(0,180,255,0.2);
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  html { scroll-behavior: smooth; }

  body {
    font-family: 'Montserrat', sans-serif;
    background: var(--dark);
    color: #fff;
    overflow-x: hidden;
  }

  /* \u2500\u2500 SCROLLBAR \u2500\u2500 */
  ::-webkit-scrollbar { width: 6px; }
  ::-webkit-scrollbar-track { background: var(--dark); }
  ::-webkit-scrollbar-thumb { background: var(--blue); border-radius: 10px; }

  /* \u2500\u2500 GRID BG \u2500\u2500 */
  .grid-bg {
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(0,180,255,0.04) 1px, transparent 1px),
      linear-gradient(90deg, rgba(0,180,255,0.04) 1px, transparent 1px);
    background-size: 60px 60px;
    pointer-events: none;
    z-index: 0;
  }

  /* \u2500\u2500 NAV \u2500\u2500 */
  nav {
    position: fixed;
    top: 0; left: 0; right: 0;
    z-index: 100;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 18px 60px;
    background: rgba(10,15,30,0.85);
    backdrop-filter: blur(20px);
    border-bottom: 1px solid var(--glass-border);
  }

  .nav-logo {
    display: flex;
    align-items: center;
    gap: 12px;
    text-decoration: none;
  }

  .nav-logo span {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 32px;
    letter-spacing: 3px;
    background: linear-gradient(135deg, var(--blue), var(--cyan));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .nav-links {
    display: flex;
    gap: 36px;
    list-style: none;
  }

  .nav-links a {
    text-decoration: none;
    color: rgba(255,255,255,0.55);
    font-size: 12px;
    font-weight: 700;
    letter-spacing: 2px;
    text-transform: uppercase;
    transition: color 0.3s;
  }

  .nav-links a:hover { color: var(--cyan); }

  .nav-cta {
    background: linear-gradient(135deg, var(--blue), var(--cyan));
    color: var(--dark) !important;
    padding: 10px 24px;
    border-radius: 50px;
    font-weight: 900 !important;
    -webkit-text-fill-color: var(--dark) !important;
  }

  /* \u2500\u2500 HERO \u2500\u2500 */
  #hero {
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
    overflow: hidden;
    padding: 120px 60px 80px;
  }

  .hero-glow1 {
    position: absolute;
    width: 800px; height: 800px;
    border-radius: 50%;
    background: radial-gradient(circle, rgba(0,150,255,0.1) 0%, transparent 70%);
    top: -200px; left: -200px;
    pointer-events: none;
  }

  .hero-glow2 {
    position: absolute;
    width: 600px; height: 600px;
    border-radius: 50%;
    background: radial-gradient(circle, rgba(0,255,200,0.07) 0%, transparent 70%);
    bottom: -100px; right: -100px;
    pointer-events: none;
  }

  .hero-content {
    position: relative;
    z-index: 2;
    max-width: 700px;
    animation: fadeUp 0.8s ease both;
  }

  .hero-badge {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    background: rgba(0,180,255,0.1);
    border: 1px solid rgba(0,180,255,0.3);
    border-radius: 50px;
    padding: 8px 20px;
    font-size: 11px;
    font-weight: 700;
    letter-spacing: 3px;
    color: var(--cyan);
    text-transform: uppercase;
    margin-bottom: 28px;
    animation: fadeUp 0.8s 0.1s ease both;
  }

  .hero-badge::before {
    content: '';
    width: 8px; height: 8px;
    border-radius: 50%;
    background: var(--cyan);
    box-shadow: 0 0 10px var(--cyan);
    animation: pulse 2s infinite;
  }

  @keyframes pulse {
    0%, 100% { opacity: 1; transform: scale(1); }
    50% { opacity: 0.5; transform: scale(1.4); }
  }

  .hero-title {
    font-family: 'Bebas Neue', sans-serif;
    font-size: clamp(70px, 9vw, 120px);
    line-height: 0.95;
    letter-spacing: 2px;
    margin-bottom: 24px;
    animation: fadeUp 0.8s 0.2s ease both;
  }

  .hero-title .line1 {
    display: block;
    background: linear-gradient(135deg, #fff 0%, rgba(255,255,255,0.7) 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .hero-title .line2 {
    display: block;
    background: linear-gradient(135deg, var(--blue), var(--cyan));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    filter: drop-shadow(0 0 30px rgba(0,180,255,0.5));
  }

  .hero-sub {
    font-size: 17px;
    color: rgba(255,255,255,0.55);
    line-height: 1.7;
    margin-bottom: 40px;
    font-weight: 500;
    max-width: 500px;
    animation: fadeUp 0.8s 0.3s ease both;
  }

  .hero-sub strong {
    color: rgba(255,255,255,0.9);
    font-weight: 700;
  }

  .hero-buttons {
    display: flex;
    gap: 16px;
    flex-wrap: wrap;
    animation: fadeUp 0.8s 0.4s ease both;
  }

  .btn-primary {
    display: inline-flex;
    align-items: center;
    gap: 10px;
    background: linear-gradient(135deg, var(--blue), var(--cyan));
    color: var(--dark);
    font-weight: 900;
    font-size: 14px;
    letter-spacing: 2px;
    text-transform: uppercase;
    padding: 18px 36px;
    border-radius: 50px;
    text-decoration: none;
    transition: transform 0.2s, box-shadow 0.2s;
    box-shadow: 0 0 40px rgba(0,180,255,0.3);
  }

  .btn-primary:hover {
    transform: translateY(-3px);
    box-shadow: 0 10px 50px rgba(0,180,255,0.5);
  }

  .btn-secondary {
    display: inline-flex;
    align-items: center;
    gap: 10px;
    background: var(--glass);
    color: rgba(255,255,255,0.8);
    font-weight: 700;
    font-size: 14px;
    letter-spacing: 2px;
    text-transform: uppercase;
    padding: 18px 36px;
    border-radius: 50px;
    text-decoration: none;
    border: 1px solid var(--glass-border);
    transition: all 0.2s;
  }

  .btn-secondary:hover {
    background: rgba(0,180,255,0.1);
    border-color: var(--blue);
    color: #fff;
  }

  .hero-right {
    position: absolute;
    right: 60px;
    top: 50%;
    transform: translateY(-50%);
    font-size: 220px;
    opacity: 0.06;
    pointer-events: none;
    animation: float 4s ease-in-out infinite;
    z-index: 1;
  }

  @keyframes float {
    0%, 100% { transform: translateY(-50%) rotate(-5deg); }
    50% { transform: translateY(calc(-50% - 20px)) rotate(-5deg); }
  }

  .hero-stats {
    display: flex;
    gap: 40px;
    margin-top: 48px;
    padding-top: 40px;
    border-top: 1px solid rgba(255,255,255,0.08);
    animation: fadeUp 0.8s 0.5s ease both;
  }

  .stat {
    display: flex;
    flex-direction: column;
    gap: 4px;
  }

  .stat-number {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 40px;
    background: linear-gradient(135deg, var(--blue), var(--cyan));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    line-height: 1;
  }

  .stat-label {
    font-size: 11px;
    font-weight: 600;
    letter-spacing: 2px;
    color: rgba(255,255,255,0.35);
    text-transform: uppercase;
  }

  /* \u2500\u2500 SECTIONS SHARED \u2500\u2500 */
  section {
    position: relative;
    z-index: 2;
  }

  .section-header {
    text-align: center;
    margin-bottom: 60px;
  }

  .section-eyebrow {
    display: inline-block;
    font-size: 11px;
    font-weight: 700;
    letter-spacing: 5px;
    color: var(--cyan);
    text-transform: uppercase;
    margin-bottom: 16px;
  }

  .section-title {
    font-family: 'Bebas Neue', sans-serif;
    font-size: clamp(42px, 5vw, 64px);
    letter-spacing: 2px;
    background: linear-gradient(135deg, #fff, rgba(255,255,255,0.6));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    line-height: 1;
  }

  .section-divider {
    width: 60px;
    height: 3px;
    background: linear-gradient(90deg, var(--blue), var(--cyan));
    margin: 20px auto 0;
    border-radius: 2px;
  }

  /* \u2500\u2500 SERVICIOS \u2500\u2500 */
  #servicios {
    padding: 100px 60px;
    background: linear-gradient(180deg, var(--dark) 0%, var(--dark2) 100%);
  }

  .services-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
    gap: 20px;
    max-width: 1100px;
    margin: 0 auto;
  }

  .service-card {
    background: var(--glass);
    border: 1px solid var(--glass-border);
    border-radius: 20px;
    padding: 36px 28px;
    text-align: center;
    transition: all 0.3s;
    cursor: default;
    position: relative;
    overflow: hidden;
  }

  .service-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 3px;
    background: linear-gradient(90deg, var(--blue), var(--cyan));
    transform: scaleX(0);
    transition: transform 0.3s;
    transform-origin: left;
  }

  .service-card:hover {
    background: rgba(0,180,255,0.08);
    border-color: rgba(0,180,255,0.4);
    transform: translateY(-6px);
    box-shadow: 0 20px 60px rgba(0,180,255,0.15);
  }

  .service-card:hover::before { transform: scaleX(1); }

  .service-emoji {
    font-size: 48px;
    display: block;
    margin-bottom: 16px;
    filter: drop-shadow(0 0 15px rgba(0,180,255,0.4));
  }

  .service-name {
    font-size: 14px;
    font-weight: 800;
    text-transform: uppercase;
    letter-spacing: 1.5px;
    color: #fff;
    margin-bottom: 10px;
  }

  .service-desc {
    font-size: 13px;
    color: rgba(255,255,255,0.4);
    line-height: 1.6;
    font-weight: 500;
  }

  /* \u2500\u2500 TARIFAS \u2500\u2500 */
  #tarifas {
    padding: 100px 60px;
    background: var(--dark3);
    position: relative;
    overflow: hidden;
  }

  #tarifas::before {
    content: '';
    position: absolute;
    top: 50%; left: 50%;
    transform: translate(-50%, -50%);
    width: 800px; height: 800px;
    border-radius: 50%;
    background: radial-gradient(circle, rgba(0,150,255,0.06) 0%, transparent 70%);
    pointer-events: none;
  }

  .tarifas-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 24px;
    max-width: 900px;
    margin: 0 auto 60px;
  }

  .tarifa-card {
    background: var(--glass);
    border: 1px solid var(--glass-border);
    border-radius: 24px;
    padding: 40px 32px;
    text-align: center;
    position: relative;
    overflow: hidden;
    transition: all 0.3s;
  }

  .tarifa-card::after {
    content: '';
    position: absolute;
    bottom: 0; left: 0; right: 0;
    height: 3px;
    background: linear-gradient(90deg, var(--blue), var(--cyan));
  }

  .tarifa-card.featured {
    background: linear-gradient(145deg, rgba(0,180,255,0.12), rgba(0,255,200,0.06));
    border-color: rgba(0,255,200,0.4);
    transform: scale(1.05);
    box-shadow: 0 0 60px rgba(0,180,255,0.2);
  }

  .tarifa-card:hover {
    transform: translateY(-8px);
    box-shadow: 0 20px 60px rgba(0,180,255,0.2);
  }

  .tarifa-card.featured:hover { transform: scale(1.05) translateY(-8px); }

  .featured-tag {
    position: absolute;
    top: 16px; right: 16px;
    background: linear-gradient(135deg, var(--blue), var(--cyan));
    color: var(--dark);
    font-size: 10px;
    font-weight: 900;
    letter-spacing: 2px;
    text-transform: uppercase;
    padding: 5px 12px;
    border-radius: 20px;
  }

  .tarifa-zone {
    font-size: 11px;
    font-weight: 700;
    letter-spacing: 3px;
    color: rgba(255,255,255,0.4);
    text-transform: uppercase;
    margin-bottom: 12px;
  }

  .tarifa-price {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 88px;
    line-height: 1;
    background: linear-gradient(135deg, var(--blue), var(--cyan));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    filter: drop-shadow(0 0 20px rgba(0,180,255,0.5));
  }

  .tarifa-per {
    font-size: 13px;
    color: rgba(255,255,255,0.5);
    font-weight: 600;
    margin-bottom: 8px;
  }

  .tarifa-desc {
    font-size: 12px;
    color: rgba(255,255,255,0.3);
    letter-spacing: 1px;
    font-weight: 500;
  }

  .extra-note {
    text-align: center;
    font-size: 13px;
    color: rgba(255,255,255,0.35);
    font-weight: 600;
    letter-spacing: 1px;
    margin-top: -20px;
  }

  .extra-note span {
    color: var(--cyan);
  }

  /* \u2500\u2500 COMO FUNCIONA \u2500\u2500 */
  #como {
    padding: 100px 60px;
    background: linear-gradient(180deg, var(--dark2) 0%, var(--dark) 100%);
  }

  .steps {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 0;
    max-width: 900px;
    margin: 0 auto;
    position: relative;
  }

  .steps::before {
    content: '';
    position: absolute;
    top: 40px; left: 10%; right: 10%;
    height: 2px;
    background: linear-gradient(90deg, transparent, var(--blue), var(--cyan), transparent);
    z-index: 0;
  }

  .step {
    text-align: center;
    padding: 0 20px;
    position: relative;
    z-index: 1;
  }

  .step-number {
    width: 80px; height: 80px;
    border-radius: 50%;
    background: linear-gradient(145deg, var(--dark2), var(--dark));
    border: 2px solid var(--blue);
    display: flex;
    align-items: center;
    justify-content: center;
    margin: 0 auto 24px;
    font-family: 'Bebas Neue', sans-serif;
    font-size: 28px;
    background: linear-gradient(135deg, var(--blue), var(--cyan));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    box-shadow: 0 0 30px rgba(0,180,255,0.3);
    position: relative;
  }

  .step-number::after {
    content: attr(data-n);
    font-family: 'Bebas Neue', sans-serif;
    font-size: 28px;
    position: absolute;
    background: linear-gradient(135deg, var(--blue), var(--cyan));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .step-icon {
    font-size: 32px;
    display: block;
    margin-bottom: 16px;
  }

  .step-title {
    font-weight: 800;
    font-size: 14px;
    text-transform: uppercase;
    letter-spacing: 1px;
    color: #fff;
    margin-bottom: 10px;
  }

  .step-desc {
    font-size: 13px;
    color: rgba(255,255,255,0.4);
    line-height: 1.6;
    font-weight: 500;
  }

  /* \u2500\u2500 CONTACTO \u2500\u2500 */
  #contacto {
    padding: 100px 60px;
    background: var(--dark3);
    text-align: center;
    position: relative;
    overflow: hidden;
  }

  .contact-glow {
    position: absolute;
    top: 50%; left: 50%;
    transform: translate(-50%, -50%);
    width: 700px; height: 400px;
    border-radius: 50%;
    background: radial-gradient(ellipse, rgba(0,180,255,0.1) 0%, transparent 70%);
    pointer-events: none;
  }

  .contact-card {
    position: relative;
    z-index: 2;
    background: var(--glass);
    border: 1px solid var(--glass-border);
    border-radius: 30px;
    max-width: 700px;
    margin: 0 auto;
    padding: 60px;
    overflow: hidden;
  }

  .contact-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 3px;
    background: linear-gradient(90deg, var(--blue), var(--cyan));
  }

  .contact-card h2 {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 52px;
    letter-spacing: 2px;
    background: linear-gradient(135deg, #fff, rgba(255,255,255,0.7));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    margin-bottom: 16px;
  }

  .contact-card p {
    color: rgba(255,255,255,0.45);
    font-size: 15px;
    margin-bottom: 40px;
    line-height: 1.7;
    font-weight: 500;
  }

  .contact-methods {
    display: flex;
    flex-direction: column;
    gap: 16px;
    margin-bottom: 36px;
  }

  .contact-method {
    display: flex;
    align-items: center;
    gap: 16px;
    background: rgba(255,255,255,0.03);
    border: 1px solid rgba(255,255,255,0.07);
    border-radius: 16px;
    padding: 18px 24px;
  }

  .contact-method-icon {
    font-size: 24px;
    flex-shrink: 0;
  }

  .contact-method-info {
    text-align: left;
  }

  .contact-method-label {
    font-size: 10px;
    font-weight: 700;
    letter-spacing: 2px;
    color: rgba(255,255,255,0.35);
    text-transform: uppercase;
    margin-bottom: 3px;
  }

  .contact-method-value {
    font-size: 16px;
    font-weight: 700;
    color: #fff;
  }

  .contact-method-value a {
    color: var(--cyan);
    text-decoration: none;
  }

  .contact-info-row {
    display: flex;
    gap: 16px;
    justify-content: center;
    flex-wrap: wrap;
    margin-bottom: 36px;
  }

  .info-pill {
    display: flex;
    align-items: center;
    gap: 8px;
    background: rgba(0,180,255,0.08);
    border: 1px solid rgba(0,180,255,0.2);
    border-radius: 50px;
    padding: 10px 20px;
    font-size: 12px;
    font-weight: 700;
    color
