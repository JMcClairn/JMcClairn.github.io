<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>McClairn Health — Healthcare, Redesigned</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,400;0,600;0,700;1,400;1,600&family=DM+Sans:wght@300;400;500;600&family=DM+Mono:wght@400&display=swap" rel="stylesheet">

<style>
/* ============================================================
   DESIGN TOKENS
============================================================ */
:root {
  --purple:       #2D0F6B;
  --purple-mid:   #3E1A8E;
  --purple-light: #6B44C4;
  --purple-pale:  #EDE8FA;
  --purple-ghost: #F5F2FD;
  --green:        #6DB33F;
  --green-bright: #93D13A;
  --green-dark:   #4A8A1C;
  --green-pale:   #EEF8E3;
  --charcoal:     #1A1A2E;
  --gray-700:     #3D3D52;
  --gray-500:     #6B6B82;
  --gray-300:     #B8B8CC;
  --gray-100:     #F0F0F7;
  --gray-50:      #F8F8FC;
  --white:        #FFFFFF;
  --rule:         #E2E2EE;

  --font-display: 'Cormorant Garamond', Georgia, serif;
  --font-body:    'DM Sans', system-ui, sans-serif;
  --font-mono:    'DM Mono', monospace;

  --radius-sm:  6px;
  --radius-md:  12px;
  --radius-lg:  20px;
  --radius-xl:  32px;

  --shadow-sm:  0 1px 4px rgba(45,15,107,0.07);
  --shadow-md:  0 4px 20px rgba(45,15,107,0.10);
  --shadow-lg:  0 12px 48px rgba(45,15,107,0.14);

  --ease-out: cubic-bezier(0.22, 1, 0.36, 1);
  --transition: 0.35s var(--ease-out);
}

/* ============================================================
   RESET & BASE
============================================================ */
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
html { scroll-behavior: smooth; font-size: 16px; }
body {
  font-family: var(--font-body);
  color: var(--charcoal);
  background: var(--white);
  overflow-x: hidden;
  -webkit-font-smoothing: antialiased;
}
img { max-width: 100%; }
a { color: inherit; text-decoration: none; }
button { cursor: pointer; font-family: var(--font-body); border: none; background: none; }
input, textarea, select {
  font-family: var(--font-body);
  font-size: 15px;
  outline: none;
}
ul { list-style: none; }

/* ============================================================
   SCROLL REVEAL
============================================================ */
.reveal {
  opacity: 0;
  transform: translateY(28px);
  transition: opacity 0.7s var(--ease-out), transform 0.7s var(--ease-out);
}
.reveal.visible {
  opacity: 1;
  transform: translateY(0);
}
.reveal-delay-1 { transition-delay: 0.1s; }
.reveal-delay-2 { transition-delay: 0.2s; }
.reveal-delay-3 { transition-delay: 0.3s; }
.reveal-delay-4 { transition-delay: 0.4s; }

/* ============================================================
   NAVIGATION
============================================================ */
nav {
  position: fixed;
  top: 0; left: 0; right: 0;
  z-index: 100;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 48px;
  height: 72px;
  background: rgba(255,255,255,0.92);
  backdrop-filter: blur(16px);
  -webkit-backdrop-filter: blur(16px);
  border-bottom: 1px solid transparent;
  transition: border-color 0.3s, box-shadow 0.3s;
}
nav.scrolled {
  border-color: var(--rule);
  box-shadow: var(--shadow-sm);
}

.nav-logo {
  display: flex;
  align-items: center;
  gap: 10px;
}
.nav-logo svg { width: 140px; height: auto; }

.nav-links {
  display: flex;
  align-items: center;
  gap: 36px;
}
.nav-links a {
  font-size: 14px;
  font-weight: 500;
  color: var(--gray-700);
  letter-spacing: 0.01em;
  transition: color var(--transition);
  position: relative;
}
.nav-links a::after {
  content: '';
  position: absolute;
  bottom: -3px; left: 0; right: 0;
  height: 1.5px;
  background: var(--green);
  transform: scaleX(0);
  transform-origin: left;
  transition: transform var(--transition);
}
.nav-links a:hover { color: var(--purple); }
.nav-links a:hover::after { transform: scaleX(1); }

.nav-cta {
  display: flex;
  align-items: center;
  gap: 12px;
}
.btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
  padding: 10px 22px;
  border-radius: var(--radius-sm);
  font-size: 14px;
  font-weight: 500;
  letter-spacing: 0.01em;
  transition: all var(--transition);
  white-space: nowrap;
}
.btn-ghost {
  color: var(--purple);
  background: transparent;
}
.btn-ghost:hover { background: var(--purple-ghost); }
.btn-primary {
  background: var(--purple);
  color: var(--white);
  box-shadow: 0 2px 12px rgba(45,15,107,0.25);
}
.btn-primary:hover {
  background: var(--purple-mid);
  box-shadow: 0 4px 20px rgba(45,15,107,0.35);
  transform: translateY(-1px);
}
.btn-green {
  background: var(--green);
  color: var(--white);
  box-shadow: 0 2px 12px rgba(109,179,63,0.30);
}
.btn-green:hover {
  background: var(--green-dark);
  transform: translateY(-1px);
}
.btn-outline {
  border: 1.5px solid var(--rule);
  color: var(--gray-700);
  background: var(--white);
}
.btn-outline:hover { border-color: var(--purple-light); color: var(--purple); }

/* ============================================================
   HERO
============================================================ */
.hero {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  padding: 120px 48px 80px;
  position: relative;
  overflow: hidden;
  background: var(--white);
}

/* Organic background mesh */
.hero-bg {
  position: absolute;
  inset: 0;
  pointer-events: none;
  z-index: 0;
}
.hero-bg::before {
  content: '';
  position: absolute;
  top: -15%;
  right: -8%;
  width: 680px;
  height: 680px;
  background: radial-gradient(ellipse at center,
    rgba(147,209,58,0.09) 0%,
    rgba(109,179,63,0.05) 40%,
    transparent 70%);
  border-radius: 60% 40% 55% 45% / 50% 55% 45% 50%;
  animation: morph 18s ease-in-out infinite alternate;
}
.hero-bg::after {
  content: '';
  position: absolute;
  bottom: 5%;
  left: -5%;
  width: 520px;
  height: 520px;
  background: radial-gradient(ellipse at center,
    rgba(45,15,107,0.06) 0%,
    transparent 70%);
  border-radius: 45% 55% 40% 60% / 55% 45% 55% 45%;
  animation: morph 22s ease-in-out infinite alternate-reverse;
}

@keyframes morph {
  0%   { border-radius: 60% 40% 55% 45% / 50% 55% 45% 50%; }
  50%  { border-radius: 40% 60% 45% 55% / 55% 40% 60% 45%; }
  100% { border-radius: 55% 45% 60% 40% / 40% 60% 45% 55%; }
}

.hero-inner {
  position: relative;
  z-index: 1;
  max-width: 1160px;
  margin: 0 auto;
  width: 100%;
}

.hero-eyebrow {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  font-size: 12px;
  font-weight: 600;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: var(--green-dark);
  margin-bottom: 28px;
  opacity: 0;
  animation: fadeUp 0.8s var(--ease-out) 0.2s forwards;
}
.hero-eyebrow span {
  display: inline-block;
  width: 24px;
  height: 1.5px;
  background: var(--green);
}

.hero-headline {
  font-family: var(--font-display);
  font-size: clamp(52px, 7vw, 96px);
  font-weight: 700;
  line-height: 1.0;
  letter-spacing: -0.02em;
  color: var(--purple);
  max-width: 820px;
  margin-bottom: 32px;
  opacity: 0;
  animation: fadeUp 0.9s var(--ease-out) 0.35s forwards;
}
.hero-headline em {
  font-style: italic;
  color: var(--green-dark);
}

.hero-sub {
  font-size: 19px;
  font-weight: 300;
  line-height: 1.65;
  color: var(--gray-700);
  max-width: 560px;
  margin-bottom: 48px;
  opacity: 0;
  animation: fadeUp 0.9s var(--ease-out) 0.5s forwards;
}

.hero-actions {
  display: flex;
  gap: 14px;
  flex-wrap: wrap;
  opacity: 0;
  animation: fadeUp 0.9s var(--ease-out) 0.65s forwards;
}
.hero-actions .btn { padding: 14px 28px; font-size: 15px; }

.hero-scroll-hint {
  position: absolute;
  bottom: 40px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 8px;
  font-size: 11px;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: var(--gray-300);
  animation: fadeIn 1.5s ease 1.5s both;
}
.scroll-line {
  width: 1px;
  height: 40px;
  background: linear-gradient(to bottom, var(--gray-300), transparent);
  animation: scrollPulse 2s ease-in-out infinite;
}
@keyframes scrollPulse {
  0%, 100% { opacity: 0.4; transform: scaleY(1); }
  50%       { opacity: 1;   transform: scaleY(1.1); }
}

/* Stat band inside hero */
.hero-stats {
  display: flex;
  gap: 0;
  margin-top: 72px;
  border-top: 1px solid var(--rule);
  padding-top: 40px;
  opacity: 0;
  animation: fadeUp 0.9s var(--ease-out) 0.8s forwards;
}
.hero-stat {
  flex: 1;
  padding-right: 40px;
  border-right: 1px solid var(--rule);
  margin-right: 40px;
}
.hero-stat:last-child { border-right: none; padding-right: 0; margin-right: 0; }
.hero-stat-num {
  font-family: var(--font-display);
  font-size: 42px;
  font-weight: 700;
  color: var(--purple);
  line-height: 1;
  margin-bottom: 6px;
}
.hero-stat-num em { color: var(--green); font-style: normal; }
.hero-stat-label {
  font-size: 13px;
  color: var(--gray-500);
  line-height: 1.5;
}

@keyframes fadeUp {
  from { opacity: 0; transform: translateY(24px); }
  to   { opacity: 1; transform: translateY(0); }
}
@keyframes fadeIn {
  from { opacity: 0; }
  to   { opacity: 1; }
}

/* ============================================================
   SECTION COMMON
============================================================ */
section { padding: 100px 48px; }
.section-inner { max-width: 1160px; margin: 0 auto; }
.section-label {
  font-size: 11px;
  font-weight: 600;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: var(--green-dark);
  margin-bottom: 16px;
  display: flex;
  align-items: center;
  gap: 10px;
}
.section-label::before {
  content: '';
  display: inline-block;
  width: 20px;
  height: 1.5px;
  background: var(--green);
}
.section-headline {
  font-family: var(--font-display);
  font-size: clamp(36px, 4.5vw, 58px);
  font-weight: 700;
  line-height: 1.08;
  letter-spacing: -0.02em;
  color: var(--purple);
  margin-bottom: 20px;
}
.section-headline em { font-style: italic; color: var(--green-dark); }
.section-body {
  font-size: 17px;
  font-weight: 300;
  line-height: 1.75;
  color: var(--gray-700);
  max-width: 600px;
}

/* ============================================================
   MISSION / ABOUT
============================================================ */
.about { background: var(--purple-ghost); }
.about-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 80px;
  align-items: center;
}
.about-pillars {
  display: grid;
  gap: 24px;
  margin-top: 40px;
}
.pillar {
  display: flex;
  gap: 20px;
  align-items: flex-start;
  padding: 24px;
  background: var(--white);
  border-radius: var(--radius-md);
  border: 1px solid var(--rule);
  transition: all var(--transition);
}
.pillar:hover {
  border-color: var(--purple-light);
  box-shadow: var(--shadow-md);
  transform: translateX(4px);
}
.pillar-icon {
  width: 44px;
  height: 44px;
  border-radius: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
  font-size: 20px;
}
.pillar-icon.green  { background: var(--green-pale); }
.pillar-icon.purple { background: var(--purple-ghost); }
.pillar-icon.blue   { background: #EAF0FF; }
.pillar-title {
  font-size: 15px;
  font-weight: 600;
  color: var(--purple);
  margin-bottom: 4px;
}
.pillar-desc {
  font-size: 13.5px;
  color: var(--gray-500);
  line-height: 1.6;
}

.about-visual {
  position: relative;
}
.about-card-stack {
  position: relative;
  width: 100%;
  height: 440px;
}
.about-card {
  position: absolute;
  border-radius: var(--radius-lg);
  padding: 32px;
  font-size: 14px;
  line-height: 1.6;
}
.about-card-main {
  top: 0; left: 0; right: 0;
  background: var(--purple);
  color: var(--white);
  z-index: 2;
  box-shadow: var(--shadow-lg);
}
.about-card-main .card-q {
  font-family: var(--font-display);
  font-size: 22px;
  font-weight: 600;
  font-style: italic;
  line-height: 1.4;
  margin-bottom: 16px;
  color: rgba(255,255,255,0.92);
}
.about-card-main .card-a {
  color: rgba(255,255,255,0.65);
  font-size: 14px;
}
.about-card-accent {
  bottom: 0; right: -20px; left: 40px;
  background: var(--green-pale);
  border: 1px solid rgba(109,179,63,0.25);
  z-index: 1;
  padding-top: 180px;
  color: var(--gray-700);
}
.about-card-accent .accent-stat {
  font-family: var(--font-display);
  font-size: 32px;
  font-weight: 700;
  color: var(--green-dark);
}
.about-card-accent .accent-label {
  font-size: 13px;
  color: var(--gray-500);
}

/* ============================================================
   SERVICES
============================================================ */
.services { background: var(--white); }
.services-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 24px;
  margin-top: 56px;
}
.service-card {
  border: 1px solid var(--rule);
  border-radius: var(--radius-lg);
  padding: 36px 32px;
  transition: all var(--transition);
  cursor: default;
  position: relative;
  overflow: hidden;
}
.service-card::before {
  content: '';
  position: absolute;
  top: 0; left: 0; right: 0;
  height: 3px;
  background: linear-gradient(90deg, var(--purple), var(--purple-light));
  transform: scaleX(0);
  transform-origin: left;
  transition: transform var(--transition);
}
.service-card:hover {
  border-color: transparent;
  box-shadow: var(--shadow-lg);
  transform: translateY(-4px);
}
.service-card:hover::before { transform: scaleX(1); }
.service-num {
  font-family: var(--font-mono);
  font-size: 11px;
  color: var(--gray-300);
  letter-spacing: 0.05em;
  margin-bottom: 20px;
}
.service-icon {
  font-size: 28px;
  margin-bottom: 16px;
}
.service-title {
  font-family: var(--font-display);
  font-size: 24px;
  font-weight: 700;
  color: var(--purple);
  margin-bottom: 12px;
  line-height: 1.2;
}
.service-desc {
  font-size: 14px;
  color: var(--gray-500);
  line-height: 1.7;
}
.service-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-top: 20px;
}
.tag {
  font-size: 11px;
  font-weight: 500;
  letter-spacing: 0.04em;
  padding: 4px 10px;
  border-radius: 20px;
  background: var(--gray-100);
  color: var(--gray-500);
}
.tag.green { background: var(--green-pale); color: var(--green-dark); }
.tag.purple { background: var(--purple-ghost); color: var(--purple-light); }

/* ============================================================
   WHO WE SERVE (AUDIENCE TABS)
============================================================ */
.audience { background: var(--gray-50); }
.audience-tabs {
  display: flex;
  gap: 0;
  border: 1px solid var(--rule);
  border-radius: var(--radius-md);
  overflow: hidden;
  margin-bottom: 48px;
  max-width: 480px;
}
.audience-tab {
  flex: 1;
  padding: 13px 20px;
  font-size: 14px;
  font-weight: 500;
  color: var(--gray-500);
  background: var(--white);
  border: none;
  transition: all 0.25s;
  cursor: pointer;
  border-right: 1px solid var(--rule);
}
.audience-tab:last-child { border-right: none; }
.audience-tab.active {
  background: var(--purple);
  color: var(--white);
}
.audience-panel { display: none; }
.audience-panel.active { display: grid; grid-template-columns: 1fr 1fr; gap: 48px; align-items: start; }

.audience-text .panel-headline {
  font-family: var(--font-display);
  font-size: 36px;
  font-weight: 700;
  color: var(--purple);
  line-height: 1.15;
  margin-bottom: 16px;
}
.audience-text .panel-body {
  font-size: 16px;
  font-weight: 300;
  color: var(--gray-700);
  line-height: 1.75;
  margin-bottom: 28px;
}
.audience-features {
  display: grid;
  gap: 12px;
}
.audience-feature {
  display: flex;
  align-items: flex-start;
  gap: 12px;
  font-size: 14px;
  color: var(--gray-700);
}
.audience-feature::before {
  content: '';
  display: inline-block;
  width: 7px;
  height: 7px;
  border-radius: 50%;
  background: var(--green);
  margin-top: 6px;
  flex-shrink: 0;
}

.audience-visual-card {
  background: var(--white);
  border: 1px solid var(--rule);
  border-radius: var(--radius-lg);
  padding: 36px;
  box-shadow: var(--shadow-md);
}
.audience-quote {
  font-family: var(--font-display);
  font-size: 20px;
  font-style: italic;
  color: var(--gray-700);
  line-height: 1.55;
  margin-bottom: 20px;
  padding-bottom: 20px;
  border-bottom: 1px solid var(--rule);
}
.quote-attr {
  font-size: 13px;
  color: var(--gray-300);
  font-style: normal;
}

/* ============================================================
   VOICE SECTIONS (PATIENT / PRACTITIONER FEEDBACK)
============================================================ */
.voice-section {
  padding: 80px 48px;
}
.voice-section.patient-voice { background: var(--green-pale); }
.voice-section.practitioner-voice { background: var(--purple-ghost); }

.voice-inner {
  max-width: 760px;
  margin: 0 auto;
  text-align: center;
}
.voice-inner .section-label { justify-content: center; }
.voice-inner .section-label::before { display: none; }
.voice-headline {
  font-family: var(--font-display);
  font-size: clamp(30px, 4vw, 48px);
  font-weight: 700;
  color: var(--purple);
  line-height: 1.1;
  margin-bottom: 14px;
}
.voice-headline em { font-style: italic; color: var(--green-dark); }
.voice-sub {
  font-size: 16px;
  color: var(--gray-500);
  line-height: 1.7;
  margin-bottom: 40px;
  max-width: 520px;
  margin-left: auto;
  margin-right: auto;
}

.voice-form {
  background: var(--white);
  border-radius: var(--radius-lg);
  padding: 40px;
  box-shadow: var(--shadow-md);
  text-align: left;
  border: 1px solid var(--rule);
}
.form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 16px; margin-bottom: 16px; }
.form-group { display: flex; flex-direction: column; gap: 6px; margin-bottom: 16px; }
.form-group label {
  font-size: 12px;
  font-weight: 600;
  letter-spacing: 0.05em;
  text-transform: uppercase;
  color: var(--gray-500);
}
.form-group input,
.form-group select,
.form-group textarea {
  padding: 12px 16px;
  border: 1.5px solid var(--rule);
  border-radius: var(--radius-sm);
  font-size: 14.5px;
  color: var(--charcoal);
  background: var(--gray-50);
  transition: border-color var(--transition), box-shadow var(--transition);
  width: 100%;
}
.form-group input:focus,
.form-group select:focus,
.form-group textarea:focus {
  border-color: var(--purple-light);
  box-shadow: 0 0 0 3px rgba(107,68,196,0.1);
  background: var(--white);
}
.form-group textarea { resize: vertical; min-height: 120px; }
.form-footer {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-top: 24px;
  gap: 16px;
}
.form-privacy {
  font-size: 12px;
  color: var(--gray-300);
  line-height: 1.5;
  max-width: 300px;
}
.form-success {
  display: none;
  text-align: center;
  padding: 32px;
}
.form-success .success-icon { font-size: 40px; margin-bottom: 12px; }
.form-success h4 {
  font-family: var(--font-display);
  font-size: 22px;
  color: var(--purple);
  margin-bottom: 8px;
}
.form-success p { font-size: 14px; color: var(--gray-500); }

/* Voice category chips */
.category-chips {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-bottom: 16px;
}
.chip {
  padding: 7px 14px;
  border-radius: 20px;
  border: 1.5px solid var(--rule);
  font-size: 13px;
  color: var(--gray-500);
  cursor: pointer;
  transition: all 0.2s;
  background: var(--white);
}
.chip:hover { border-color: var(--purple-light); color: var(--purple); }
.chip.selected {
  background: var(--purple);
  border-color: var(--purple);
  color: var(--white);
}

/* ============================================================
   TECHNOLOGY
============================================================ */
.technology { background: var(--white); }
.tech-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 20px;
  margin-top: 56px;
}
.tech-card {
  border: 1px solid var(--rule);
  border-radius: var(--radius-md);
  padding: 28px 24px;
  transition: all var(--transition);
  text-align: center;
}
.tech-card:hover {
  border-color: var(--purple-light);
  box-shadow: var(--shadow-md);
  transform: translateY(-3px);
}
.tech-icon { font-size: 32px; margin-bottom: 12px; }
.tech-name {
  font-size: 13px;
  font-weight: 600;
  color: var(--purple);
  margin-bottom: 6px;
  letter-spacing: 0.01em;
}
.tech-role { font-size: 12px; color: var(--gray-300); line-height: 1.5; }

/* ============================================================
   WHY MCCLAIRN  
============================================================ */
.why { background: var(--purple); color: var(--white); position: relative; overflow: hidden; }
.why::before {
  content: '';
  position: absolute;
  top: -30%;
  right: -10%;
  width: 600px;
  height: 600px;
  background: radial-gradient(ellipse, rgba(147,209,58,0.1) 0%, transparent 65%);
  border-radius: 50%;
  pointer-events: none;
}
.why .section-label { color: rgba(147,209,58,0.85); }
.why .section-label::before { background: var(--green-bright); }
.why .section-headline { color: var(--white); }
.why .section-body { color: rgba(255,255,255,0.65); max-width: 100%; }

.why-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 80px;
  align-items: start;
  margin-top: 56px;
}
.why-reasons { display: grid; gap: 32px; }
.why-reason {
  border-top: 1px solid rgba(255,255,255,0.1);
  padding-top: 24px;
  display: grid;
  grid-template-columns: 40px 1fr;
  gap: 16px;
}
.reason-num {
  font-family: var(--font-mono);
  font-size: 12px;
  color: rgba(147,209,58,0.7);
  letter-spacing: 0.05em;
  padding-top: 3px;
}
.reason-title {
  font-size: 16px;
  font-weight: 600;
  color: var(--white);
  margin-bottom: 6px;
}
.reason-desc { font-size: 14px; color: rgba(255,255,255,0.55); line-height: 1.65; }

.why-cta-block {
  background: rgba(255,255,255,0.06);
  border: 1px solid rgba(255,255,255,0.1);
  border-radius: var(--radius-xl);
  padding: 48px;
}
.why-cta-block .cta-headline {
  font-family: var(--font-display);
  font-size: 32px;
  font-weight: 700;
  color: var(--white);
  line-height: 1.2;
  margin-bottom: 16px;
}
.why-cta-block .cta-body {
  font-size: 15px;
  color: rgba(255,255,255,0.6);
  line-height: 1.7;
  margin-bottom: 32px;
}
.why-cta-block .btn-white {
  background: var(--white);
  color: var(--purple);
  font-weight: 600;
  padding: 14px 28px;
  border-radius: var(--radius-sm);
  transition: all var(--transition);
  display: inline-flex;
  align-items: center;
  gap: 8px;
}
.why-cta-block .btn-white:hover {
  background: var(--green-pale);
  transform: translateY(-2px);
}
.why-cta-block .btn-white-outline {
  background: transparent;
  color: rgba(255,255,255,0.75);
  border: 1.5px solid rgba(255,255,255,0.25);
  padding: 14px 28px;
  border-radius: var(--radius-sm);
  font-size: 14px;
  font-weight: 500;
  margin-top: 12px;
  display: inline-flex;
  align-items: center;
  gap: 8px;
  transition: all var(--transition);
  cursor: pointer;
}
.why-cta-block .btn-white-outline:hover {
  border-color: rgba(255,255,255,0.6);
  color: var(--white);
}

/* ============================================================
   CONTACT / CONNECT
============================================================ */
.contact { background: var(--gray-50); }
.contact-grid {
  display: grid;
  grid-template-columns: 1fr 1.4fr;
  gap: 80px;
  align-items: start;
}
.contact-form-wrap {
  background: var(--white);
  border: 1px solid var(--rule);
  border-radius: var(--radius-lg);
  padding: 44px;
  box-shadow: var(--shadow-sm);
}
.contact-form-title {
  font-family: var(--font-display);
  font-size: 26px;
  font-weight: 700;
  color: var(--purple);
  margin-bottom: 6px;
}
.contact-form-sub {
  font-size: 14px;
  color: var(--gray-500);
  margin-bottom: 32px;
  line-height: 1.6;
}
.contact-info { display: grid; gap: 28px; }
.contact-info-item {
  display: flex;
  gap: 16px;
  align-items: flex-start;
}
.contact-info-icon {
  width: 42px;
  height: 42px;
  border-radius: 10px;
  background: var(--purple-ghost);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 18px;
  flex-shrink: 0;
}
.contact-info-label {
  font-size: 11px;
  font-weight: 600;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  color: var(--gray-300);
  margin-bottom: 4px;
}
.contact-info-value {
  font-size: 15px;
  color: var(--charcoal);
  font-weight: 500;
}
.contact-info-sub {
  font-size: 13px;
  color: var(--gray-500);
  margin-top: 2px;
}

/* ============================================================
   FOOTER
============================================================ */
footer {
  background: var(--charcoal);
  color: rgba(255,255,255,0.5);
  padding: 64px 48px 40px;
}
.footer-inner {
  max-width: 1160px;
  margin: 0 auto;
}
.footer-top {
  display: grid;
  grid-template-columns: 2fr 1fr 1fr 1fr;
  gap: 60px;
  padding-bottom: 48px;
  border-bottom: 1px solid rgba(255,255,255,0.08);
  margin-bottom: 32px;
}
.footer-brand-tagline {
  font-size: 14px;
  line-height: 1.7;
  margin-top: 16px;
  max-width: 280px;
}
.footer-col-title {
  font-size: 12px;
  font-weight: 600;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: rgba(255,255,255,0.75);
  margin-bottom: 16px;
}
.footer-links { display: grid; gap: 10px; }
.footer-links a {
  font-size: 14px;
  color: rgba(255,255,255,0.45);
  transition: color 0.2s;
}
.footer-links a:hover { color: var(--green-bright); }
.footer-bottom {
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-size: 12.5px;
}
.footer-legal { display: flex; gap: 20px; }
.footer-legal a { color: rgba(255,255,255,0.35); transition: color 0.2s; }
.footer-legal a:hover { color: rgba(255,255,255,0.7); }

/* ============================================================
   MODAL
============================================================ */
.modal-overlay {
  position: fixed;
  inset: 0;
  background: rgba(13,6,35,0.7);
  backdrop-filter: blur(6px);
  z-index: 1000;
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
  pointer-events: none;
  transition: opacity 0.3s;
  padding: 20px;
}
.modal-overlay.open { opacity: 1; pointer-events: all; }
.modal {
  background: var(--white);
  border-radius: var(--radius-xl);
  padding: 48px;
  max-width: 520px;
  width: 100%;
  transform: translateY(20px) scale(0.97);
  transition: transform 0.35s var(--ease-out);
  position: relative;
  max-height: 90vh;
  overflow-y: auto;
}
.modal-overlay.open .modal { transform: translateY(0) scale(1); }
.modal-close {
  position: absolute;
  top: 20px; right: 20px;
  width: 32px; height: 32px;
  border-radius: 50%;
  background: var(--gray-100);
  color: var(--gray-500);
  font-size: 18px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: all 0.2s;
  border: none;
}
.modal-close:hover { background: var(--rule); color: var(--charcoal); }
.modal-title {
  font-family: var(--font-display);
  font-size: 28px;
  font-weight: 700;
  color: var(--purple);
  margin-bottom: 8px;
}
.modal-sub { font-size: 14px; color: var(--gray-500); margin-bottom: 28px; line-height: 1.6; }

/* ============================================================
   MISC UTILITIES
============================================================ */
.text-center { text-align: center; }
.text-green { color: var(--green-dark); }
.mt-8  { margin-top: 8px; }
.mt-16 { margin-top: 16px; }
.mt-24 { margin-top: 24px; }
.mt-40 { margin-top: 40px; }
.flex { display: flex; }
.gap-12 { gap: 12px; }
.items-center { align-items: center; }
.divider { width: 100%; height: 1px; background: var(--rule); }

/* Ticker / marquee */
.marquee-wrap {
  background: var(--purple);
  padding: 14px 0;
  overflow: hidden;
  white-space: nowrap;
}
.marquee-track {
  display: inline-flex;
  animation: marquee 28s linear infinite;
  gap: 0;
}
.marquee-item {
  display: inline-flex;
  align-items: center;
  gap: 20px;
  padding: 0 32px;
  font-size: 12.5px;
  font-weight: 500;
  letter-spacing: 0.06em;
  text-transform: uppercase;
  color: rgba(255,255,255,0.6);
}
.marquee-dot { width: 4px; height: 4px; border-radius: 50%; background: var(--green); }
@keyframes marquee { 0% { transform: translateX(0); } 100% { transform: translateX(-50%); } }

/* ============================================================
   RESPONSIVE (basic)
============================================================ */
@media (max-width: 900px) {
  nav { padding: 0 24px; }
  .nav-links { display: none; }
  section { padding: 72px 24px; }
  .hero { padding: 100px 24px 60px; }
  .about-grid,
  .why-grid,
  .contact-grid { grid-template-columns: 1fr; gap: 40px; }
  .services-grid { grid-template-columns: 1fr; }
  .tech-grid { grid-template-columns: repeat(2, 1fr); }
  .hero-stats { flex-direction: column; gap: 24px; }
  .hero-stat { border-right: none; padding-right: 0; margin-right: 0; border-bottom: 1px solid var(--rule); padding-bottom: 24px; margin-bottom: 0; }
  .hero-stat:last-child { border-bottom: none; }
  .form-row { grid-template-columns: 1fr; }
  .audience-panel.active { grid-template-columns: 1fr; }
  .footer-top { grid-template-columns: 1fr 1fr; gap: 32px; }
}
</style>
</head>
<body>

<!-- ============================================================
     NAVIGATION
============================================================ -->
<nav id="mainNav">
  <a href="#" class="nav-logo">
    <!-- Inline logo SVG -->
    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 400 110" width="200" height="55">
      <defs>
        <linearGradient id="npg" x1="0%" y1="0%" x2="60%" y2="100%">
          <stop offset="0%" stop-color="#3E1A8E"/><stop offset="100%" stop-color="#2D0F6B"/>
        </linearGradient>
        <linearGradient id="nlg1" x1="10%" y1="0%" x2="90%" y2="100%">
          <stop offset="0%" stop-color="#93D13A"/><stop offset="100%" stop-color="#5E9E1A"/>
        </linearGradient>
        <linearGradient id="nlg2" x1="10%" y1="0%" x2="90%" y2="100%">
          <stop offset="0%" stop-color="#AADA52"/><stop offset="100%" stop-color="#74B825"/>
        </linearGradient>
        <radialGradient id="ndg" cx="38%" cy="35%" r="65%">
          <stop offset="0%" stop-color="#5B2DC6"/><stop offset="100%" stop-color="#2D0F6B"/>
        </radialGradient>
      </defs>
      <!-- Leaf mark -->
      <g transform="translate(-2, 4) scale(0.62)">
        <path d="M88,20 C95,14 108,18 112,30 C116,42 108,58 98,62 C90,66 80,60 78,48 C76,36 81,26 88,20 Z" fill="url(#nlg1)"/>
        <path d="M68,50 C73,44 84,46 87,56 C90,65 84,76 76,78 C69,80 63,74 63,65 C63,57 63,56 68,50 Z" fill="url(#nlg2)"/>
        <circle cx="60" cy="90" r="8.5" fill="url(#ndg)"/>
      </g>
      <!-- Wordmark -->
      <text x="58" y="62"
        font-family="'Palatino Linotype', Palatino, 'Book Antiqua', Georgia, serif"
        font-size="52" font-weight="700" letter-spacing="-1" fill="url(#npg)">McClairn</text>
      <text x="60" y="80"
        font-family="'Trebuchet MS', Calibri, sans-serif"
        font-size="12" font-weight="400" letter-spacing="7" fill="#8A8A9A">HEALTH</text>
      <line x1="60" y1="86" x2="305" y2="86" stroke="#DDDDE8" stroke-width="0.75"/>
    </svg>
  </a>

  <ul class="nav-links">
    <li><a href="#about">About</a></li>
    <li><a href="#services">Solutions</a></li>
    <li><a href="#audience">Who We Serve</a></li>
    <li><a href="#technology">Technology</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>

  <div class="nav-cta">
    <button class="btn btn-ghost" onclick="openModal('patient-modal')">I'm a Patient</button>
    <button class="btn btn-primary" onclick="document.getElementById('contact').scrollIntoView({behavior:'smooth'})">Get in Touch</button>
  </div>
</nav>


<!-- ============================================================
     MARQUEE TICKER
============================================================ -->
<div class="marquee-wrap" style="margin-top:72px;">
  <div class="marquee-track">
    <!-- Doubled for seamless loop -->
    <span class="marquee-item">Patient-Centered Care <span class="marquee-dot"></span></span>
    <span class="marquee-item">Clinical Intelligence <span class="marquee-dot"></span></span>
    <span class="marquee-item">AI-Powered Documentation <span class="marquee-dot"></span></span>
    <span class="marquee-item">Revenue Cycle Optimization <span class="marquee-dot"></span></span>
    <span class="marquee-item">Post-Quantum Security <span class="marquee-dot"></span></span>
    <span class="marquee-item">Care Coordination <span class="marquee-dot"></span></span>
    <span class="marquee-item">Health IT Modernization <span class="marquee-dot"></span></span>
    <span class="marquee-item">Research Intelligence <span class="marquee-dot"></span></span>
    <span class="marquee-item">Patient-Centered Care <span class="marquee-dot"></span></span>
    <span class="marquee-item">Clinical Intelligence <span class="marquee-dot"></span></span>
    <span class="marquee-item">AI-Powered Documentation <span class="marquee-dot"></span></span>
    <span class="marquee-item">Revenue Cycle Optimization <span class="marquee-dot"></span></span>
    <span class="marquee-item">Post-Quantum Security <span class="marquee-dot"></span></span>
    <span class="marquee-item">Care Coordination <span class="marquee-dot"></span></span>
    <span class="marquee-item">Health IT Modernization <span class="marquee-dot"></span></span>
    <span class="marquee-item">Research Intelligence <span class="marquee-dot"></span></span>
  </div>
</div>


<!-- ============================================================
     HERO
============================================================ -->
<section class="hero" id="hero">
  <div class="hero-bg"></div>
  <div class="hero-inner">
    <div class="hero-eyebrow"><span></span> Healthcare. Redesigned.</div>
    <h1 class="hero-headline">
      At your service.<br>
      <em>Every step</em> of the way.
    </h1>
    <p class="hero-sub">
      McClairn Health builds the intelligent infrastructure that healthcare has always deserved — 
      connecting patients, practitioners, and researchers through AI that listens, learns, and delivers.
    </p>
    <div class="hero-actions">
      <button class="btn btn-primary" onclick="document.getElementById('services').scrollIntoView({behavior:'smooth'})">
        Explore Our Solutions →
      </button>
      <button class="btn btn-outline" onclick="document.getElementById('audience').scrollIntoView({behavior:'smooth'})">
        See How We Help
      </button>
    </div>

    <div class="hero-stats">
      <div class="hero-stat">
        <div class="hero-stat-num">50<em>%</em></div>
        <div class="hero-stat-label">Reduction in clinical documentation burden through ambient AI</div>
      </div>
      <div class="hero-stat">
        <div class="hero-stat-num">30<em>%</em></div>
        <div class="hero-stat-label">Faster time to appropriate care with intelligent triage</div>
      </div>
      <div class="hero-stat">
        <div class="hero-stat-num">95<em>%+</em></div>
        <div class="hero-stat-label">Coding accuracy with AI-assisted revenue cycle management</div>
      </div>
      <div class="hero-stat">
        <div class="hero-stat-num">3<em>:1</em></div>
        <div class="hero-stat-label">Projected ROI through operational savings and revenue recovery</div>
      </div>
    </div>
  </div>

  <div class="hero-scroll-hint">
    <div class="scroll-line"></div>
    scroll
  </div>
</section>


<!-- ============================================================
     ABOUT / MISSION
============================================================ -->
<section class="about" id="about">
  <div class="section-inner">
    <div class="about-grid">
      <div>
        <div class="section-label reveal">Our Mission</div>
        <h2 class="section-headline reveal reveal-delay-1">
          Healthcare should work<br><em>for</em> everyone in it.
        </h2>
        <p class="section-body reveal reveal-delay-2">
          McClairn Health is a patient-centric Health IT transformation company. We build AI-powered systems 
          that make healthcare more efficient, more equitable, and more human — without losing the human part.
        </p>
        <p class="section-body reveal reveal-delay-2" style="margin-top:16px;">
          We operate as an <strong>advocate for patients</strong>, a <strong>clinical partner for practitioners</strong>, 
          and a <strong>resource for researchers</strong>. That's not a mission statement. That's a service model.
        </p>

        <div class="about-pillars reveal reveal-delay-3">
          <div class="pillar">
            <div class="pillar-icon green">🫀</div>
            <div>
              <div class="pillar-title">Advocate for Patients</div>
              <div class="pillar-desc">We design around the patient experience first — reducing friction, wait times, and the exhausting complexity of navigating care.</div>
            </div>
          </div>
          <div class="pillar">
            <div class="pillar-icon purple">🩺</div>
            <div>
              <div class="pillar-title">Partner for Practitioners</div>
              <div class="pillar-desc">Clinicians spend too much time on systems and too little on patients. Our AI handles the burden so they can focus on what they trained for.</div>
            </div>
          </div>
          <div class="pillar">
            <div class="pillar-icon blue">🔬</div>
            <div>
              <div class="pillar-title">Resource for Researchers</div>
              <div class="pillar-desc">Evidence-based medicine requires evidence. We make clinical data accessible, synthesized, and actionable for the people advancing it.</div>
            </div>
          </div>
        </div>
      </div>

      <div class="about-visual reveal reveal-delay-2">
        <div class="about-card-stack">
          <div class="about-card about-card-accent">
            <div class="accent-stat">9M+</div>
            <div class="accent-label">Americans navigating fragmented care systems<br>every single day. We're here to change that.</div>
            <div style="margin-top:20px; display:flex; gap:10px; flex-wrap:wrap;">
              <span class="tag green">Care Coordination</span>
              <span class="tag green">Intelligent Triage</span>
              <span class="tag purple">AI Documentation</span>
            </div>
          </div>
          <div class="about-card about-card-main">
            <div class="card-q">"What if your healthcare system actually knew who you were?"</div>
            <div class="card-a">
              McClairn Health builds the connective tissue between fragmented systems — 
              so that the next time a patient walks through a door, the door is already open.
            </div>
            <div style="margin-top:20px; display:flex; gap:8px; align-items:center;">
              <div style="width:32px;height:32px;border-radius:50%;background:rgba(147,209,58,0.2);display:flex;align-items:center;justify-content:center;font-size:14px;">✓</div>
              <span style="font-size:12px;color:rgba(255,255,255,0.5);">Constitutional AI · HIPAA-ready · FedRAMP capable</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>


<!-- ============================================================
     SERVICES
============================================================ -->
<section class="services" id="services">
  <div class="section-inner">
    <div class="text-center">
      <div class="section-label reveal" style="justify-content:center;"><span style="display:none;"></span>What We Build</div>
      <h2 class="section-headline reveal reveal-delay-1">
        Intelligent systems.<br><em>Real outcomes.</em>
      </h2>
      <p class="section-body reveal reveal-delay-2" style="max-width:540px; margin:0 auto;">
        Our AI platform doesn't replace clinical judgment — it amplifies it, so every interaction generates 
        better care, cleaner records, and less paperwork.
      </p>
    </div>

    <div class="services-grid">
      <div class="service-card reveal">
        <div class="service-num">01</div>
        <div class="service-icon">🧠</div>
        <div class="service-title">Clinical Decision Support</div>
        <div class="service-desc">Real-time AI assistance for diagnosis, treatment planning, and risk prediction. Evidence-based, explainable, and always deferential to the clinician in the room.</div>
        <div class="service-tags">
          <span class="tag green">Differential Diagnosis</span>
          <span class="tag green">Drug Interactions</span>
          <span class="tag">Guideline Adherence</span>
        </div>
      </div>

      <div class="service-card reveal reveal-delay-1">
        <div class="service-num">02</div>
        <div class="service-icon">📋</div>
        <div class="service-title">Ambient Documentation</div>
        <div class="service-desc">Encounters become notes. Automatically. Our ambient AI captures clinical conversations and generates comprehensive SOAP notes — so providers can look at patients, not screens.</div>
        <div class="service-tags">
          <span class="tag purple">Ambient Listening</span>
          <span class="tag">SOAP Notes</span>
          <span class="tag">Med Reconciliation</span>
        </div>
      </div>

      <div class="service-card reveal reveal-delay-2">
        <div class="service-num">03</div>
        <div class="service-icon">💡</div>
        <div class="service-title">Care Pathway Intelligence</div>
        <div class="service-desc">From the moment a patient reaches out, our AI maps the optimal path forward — coordinating specialists, scheduling appointments, and anticipating what comes next.</div>
        <div class="service-tags">
          <span class="tag green">Smart Triage</span>
          <span class="tag">Multi-Specialty Coordination</span>
          <span class="tag">Patient Engagement</span>
        </div>
      </div>

      <div class="service-card reveal">
        <div class="service-num">04</div>
        <div class="service-icon">💰</div>
        <div class="service-title">Revenue Cycle Optimization</div>
        <div class="service-desc">Medical coding that understands clinical context. Fewer denials, faster payments, and fraud detection that pays for itself many times over.</div>
        <div class="service-tags">
          <span class="tag">ICD-10 / CPT Coding</span>
          <span class="tag green">HCC Risk Adjustment</span>
          <span class="tag purple">FWA Detection</span>
        </div>
      </div>

      <div class="service-card reveal reveal-delay-1">
        <div class="service-num">05</div>
        <div class="service-icon">📊</div>
        <div class="service-title">Predictive Analytics</div>
        <div class="service-desc">Risk stratification, readmission prediction, population health scoring. We see what's coming before it arrives — giving care teams the time to act.</div>
        <div class="service-tags">
          <span class="tag purple">Risk Models</span>
          <span class="tag">Population Health</span>
          <span class="tag green">Early Warning</span>
        </div>
      </div>

      <div class="service-card reveal reveal-delay-2">
        <div class="service-num">06</div>
        <div class="service-icon">🔒</div>
        <div class="service-title">Quantum-Safe Security</div>
        <div class="service-desc">Your patients' data is protected against threats that don't even exist yet. Post-quantum cryptography, zero-trust architecture, and enterprise-grade compliance — baked in from day one.</div>
        <div class="service-tags">
          <span class="tag">Post-Quantum Crypto</span>
          <span class="tag purple">FedRAMP Capable</span>
          <span class="tag">HIPAA Compliant</span>
        </div>
      </div>
    </div>
  </div>
</section>


<!-- ============================================================
     WHO WE SERVE
============================================================ -->
<section class="audience" id="audience">
  <div class="section-inner">
    <div class="section-label reveal">Who We Serve</div>
    <h2 class="section-headline reveal reveal-delay-1">Built for <em>everyone</em><br>healthcare touches.</h2>
    <p class="section-body reveal reveal-delay-2" style="margin-bottom:40px;">
      Whether you're waiting for a call back, drowning in charting, or analyzing clinical trial data — 
      McClairn Health was designed with you in mind.
    </p>

    <div class="audience-tabs reveal reveal-delay-2">
      <button class="audience-tab active" onclick="switchTab('patients')">Patients</button>
      <button class="audience-tab" onclick="switchTab('practitioners')">Practitioners</button>
      <button class="audience-tab" onclick="switchTab('researchers')">Researchers</button>
      <button class="audience-tab" onclick="switchTab('enterprise')">Enterprise</button>
    </div>

    <!-- PATIENTS -->
    <div class="audience-panel active" id="tab-patients">
      <div class="audience-text">
        <div class="panel-headline">Your care,<br>finally coordinated.</div>
        <div class="panel-body">
          You shouldn't have to repeat your medical history at every appointment, 
          wait months for a referral, or navigate a phone tree to get answers. 
          McClairn Health exists to make care feel like it's actually on your side.
        </div>
        <div class="audience-features">
          <div class="audience-feature">Intelligent triage that routes you to the right care, faster</div>
          <div class="audience-feature">Coordinated appointments across specialties — no more falling through the cracks</div>
          <div class="audience-feature">A care team that's informed before you even arrive</div>
          <div class="audience-feature">Clear, timely communication at every step of your journey</div>
          <div class="audience-feature">Your history, your preferences, your outcomes — remembered</div>
        </div>
        <div style="margin-top:28px;">
          <button class="btn btn-green" onclick="openModal('patient-modal')">Share Your Experience →</button>
        </div>
      </div>
      <div class="audience-visual-card">
        <div class="audience-quote">
          "I saw three different specialists and none of them had talked to each other. 
          It felt like I was the only one trying to figure out what was wrong with me."
        </div>
        <div class="quote-attr">— A patient who deserved better. We're building it.</div>
        <div style="margin-top:24px;padding-top:24px;border-top:1px solid var(--rule);">
          <div style="font-size:13px;color:var(--gray-500);margin-bottom:12px;font-weight:500;">What drives us:</div>
          <div style="display:flex;gap:10px;flex-wrap:wrap;">
            <span class="tag green">Fragmented care</span>
            <span class="tag green">Long wait times</span>
            <span class="tag green">Lost referrals</span>
            <span class="tag">Repeated intake</span>
          </div>
        </div>
      </div>
    </div>

    <!-- PRACTITIONERS -->
    <div class="audience-panel" id="tab-practitioners">
      <div class="audience-text">
        <div class="panel-headline">Less charting.<br>More caring.</div>
        <div class="panel-body">
          You went to medical school to practice medicine, not to manage a document system. 
          McClairn Health gives you an AI clinical partner that handles the documentation, 
          surfaces the evidence, and lets you be the doctor again.
        </div>
        <div class="audience-features">
          <div class="audience-feature">Ambient AI documentation — notes generated as you work</div>
          <div class="audience-feature">Real-time clinical decision support without the noise</div>
          <div class="audience-feature">Complete patient context before you walk through the door</div>
          <div class="audience-feature">Accurate coding, fewer denials, less administrative friction</div>
          <div class="audience-feature">Predictive alerts for patients who need attention now</div>
        </div>
        <div style="margin-top:28px;">
          <button class="btn btn-primary" onclick="openModal('practitioner-modal')">Tell Us What You Need →</button>
        </div>
      </div>
      <div class="audience-visual-card">
        <div class="audience-quote">
          "I spend 2-3 hours every evening finishing charts. That's time I'm not spending 
          with my family — or thinking about my patients."
        </div>
        <div class="quote-attr">— A physician who didn't sign up for this. We heard you.</div>
        <div style="margin-top:24px;padding-top:24px;border-top:1px solid var(--rule);">
          <div style="font-size:13px;color:var(--gray-500);margin-bottom:12px;font-weight:500;">What we're solving:</div>
          <div style="display:flex;gap:10px;flex-wrap:wrap;">
            <span class="tag purple">Documentation burden</span>
            <span class="tag purple">EHR fatigue</span>
            <span class="tag">Coding errors</span>
            <span class="tag">Alert fatigue</span>
          </div>
        </div>
      </div>
    </div>

    <!-- RESEARCHERS -->
    <div class="audience-panel" id="tab-researchers">
      <div class="audience-text">
        <div class="panel-headline">Evidence that<br>moves at your speed.</div>
        <div class="panel-body">
          Research moves fast. Literature moves faster. McClairn Health's research intelligence 
          platform synthesizes clinical data, surfaces relevant studies, and helps translate 
          evidence into practice — without the months of manual review.
        </div>
        <div class="audience-features">
          <div class="audience-feature">AI-powered literature synthesis across clinical domains</div>
          <div class="audience-feature">Clinical trial analysis and pharmacological research tools</div>
          <div class="audience-feature">Evidence-based guideline generation and validation</div>
          <div class="audience-feature">Population-level insights from de-identified clinical data</div>
          <div class="audience-feature">Real-world evidence to support clinical and regulatory decisions</div>
        </div>
        <div style="margin-top:28px;">
          <button class="btn btn-outline" onclick="document.getElementById('contact').scrollIntoView({behavior:'smooth'})">Partner With Us →</button>
        </div>
      </div>
      <div class="audience-visual-card">
        <div class="audience-quote">
          "The gap between what we know in research and what gets practiced in clinics 
          is still measured in years. That's unacceptable."
        </div>
        <div class="quote-attr">— A researcher narrowing that gap. We're helping them get there faster.</div>
        <div style="margin-top:24px;padding-top:24px;border-top:1px solid var(--rule);">
          <div style="font-size:13px;color:var(--gray-500);margin-bottom:12px;font-weight:500;">Research capabilities:</div>
          <div style="display:flex;gap:10px;flex-wrap:wrap;">
            <span class="tag green">Literature AI</span>
            <span class="tag green">Trial Analysis</span>
            <span class="tag purple">Guideline Generation</span>
          </div>
        </div>
      </div>
    </div>

    <!-- ENTERPRISE -->
    <div class="audience-panel" id="tab-enterprise">
      <div class="audience-text">
        <div class="panel-headline">Transformation<br>at scale.</div>
        <div class="panel-body">
          For health systems, integrated delivery networks, and federal healthcare programs 
          ready to move beyond legacy infrastructure. McClairn Health delivers enterprise-grade 
          AI that integrates with your existing systems and grows with your mission.
        </div>
        <div class="audience-features">
          <div class="audience-feature">Full-stack Health IT transformation strategy and deployment</div>
          <div class="audience-feature">EHR-native integration via SMART on FHIR and HL7</div>
          <div class="audience-feature">FedRAMP-capable cloud infrastructure on Google GovCloud</div>
          <div class="audience-feature">Measurable ROI with defined performance benchmarks</div>
          <div class="audience-feature">Ongoing partnership model — not a one-time implementation</div>
        </div>
        <div style="margin-top:28px;">
          <button class="btn btn-primary" onclick="document.getElementById('contact').scrollIntoView({behavior:'smooth'})">Request a Briefing →</button>
        </div>
      </div>
      <div class="audience-visual-card">
        <div class="audience-quote">
          "We need a partner who understands healthcare deeply, moves at the speed 
          of technology, and is accountable for outcomes — not just deliverables."
        </div>
        <div class="quote-attr">— A healthcare executive looking for the right partner.</div>
        <div style="margin-top:24px;padding-top:24px;border-top:1px solid var(--rule);">
          <div style="font-size:13px;color:var(--gray-500);margin-bottom:12px;font-weight:500;">Enterprise strengths:</div>
          <div style="display:flex;gap:10px;flex-wrap:wrap;">
            <span class="tag purple">FedRAMP-capable</span>
            <span class="tag">EHR Integration</span>
            <span class="tag green">Measurable ROI</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>


<!-- ============================================================
     PATIENT VOICE SECTION
============================================================ -->
<section class="voice-section patient-voice" id="patient-voice">
  <div class="voice-inner">
    <div class="section-label">Your Voice Matters</div>
    <h2 class="voice-headline reveal">
      Tell us where<br>healthcare <em>let you down.</em>
    </h2>
    <p class="voice-sub reveal reveal-delay-1">
      Real change starts with real stories. If you've experienced care that was 
      fragmented, slow, confusing, or dismissive — we want to hear about it. 
      Your experience shapes what we build next.
    </p>

    <div class="voice-form reveal reveal-delay-2" id="patient-voice-form">
      <div style="font-size:15px;font-weight:600;color:var(--purple);margin-bottom:6px;">What area of care frustrated you most?</div>
      <div style="font-size:13px;color:var(--gray-500);margin-bottom:16px;">Select all that apply.</div>
      <div class="category-chips" id="patient-chips">
        <div class="chip" onclick="toggleChip(this)">Wait times</div>
        <div class="chip" onclick="toggleChip(this)">Getting a referral</div>
        <div class="chip" onclick="toggleChip(this)">Being heard by my doctor</div>
        <div class="chip" onclick="toggleChip(this)">Navigating insurance</div>
        <div class="chip" onclick="toggleChip(this)">Repeated paperwork</div>
        <div class="chip" onclick="toggleChip(this)">Care coordination</div>
        <div class="chip" onclick="toggleChip(this)">Access to specialists</div>
        <div class="chip" onclick="toggleChip(this)">Getting test results</div>
        <div class="chip" onclick="toggleChip(this)">Mental health support</div>
        <div class="chip" onclick="toggleChip(this)">Something else</div>
      </div>

      <div class="form-group">
        <label>Tell us more</label>
        <textarea id="patient-story" placeholder="You don't have to write a lot. Even a sentence helps. What would you most want a healthcare system to understand about your experience?"></textarea>
      </div>

      <div class="form-row">
        <div class="form-group" style="margin-bottom:0;">
          <label>First Name <span style="color:var(--gray-300)">(optional)</span></label>
          <input type="text" placeholder="Your first name">
        </div>
        <div class="form-group" style="margin-bottom:0;">
          <label>Email <span style="color:var(--gray-300)">(optional)</span></label>
          <input type="email" placeholder="If you'd like a response">
        </div>
      </div>

      <div class="form-footer">
        <div class="form-privacy">Your response is confidential. We never share personal information. We use these insights to guide how we build.</div>
        <button class="btn btn-green" onclick="submitVoice('patient-voice-form')">Share My Experience →</button>
      </div>
    </div>

    <div class="form-success" id="patient-voice-success">
      <div class="success-icon">🌱</div>
      <h4>Thank you for sharing.</h4>
      <p>Your experience is exactly the reason McClairn Health exists. We read every submission — and we build accordingly.</p>
    </div>
  </div>
</section>


<!-- ============================================================
     PRACTITIONER VOICE SECTION
============================================================ -->
<section class="voice-section practitioner-voice" id="practitioner-voice">
  <div class="voice-inner">
    <div class="section-label" style="color:var(--purple-mid);">Clinician Insights</div>
    <h2 class="voice-headline reveal">
      What would you fix if<br>you <em>actually could?</em>
    </h2>
    <p class="voice-sub reveal reveal-delay-1">
      You work inside these systems every day. You know exactly where they break. 
      We're building solutions for the problems you live with — and we'd rather 
      build the right ones. What's at the top of your list?
    </p>

    <div class="voice-form reveal reveal-delay-2" id="pract-voice-form">
      <div style="font-size:15px;font-weight:600;color:var(--purple);margin-bottom:6px;">Where do your systems fall shortest?</div>
      <div style="font-size:13px;color:var(--gray-500);margin-bottom:16px;">Select the areas that cost you the most time or confidence.</div>
      <div class="category-chips">
        <div class="chip" onclick="toggleChip(this)">Clinical documentation</div>
        <div class="chip" onclick="toggleChip(this)">EHR usability</div>
        <div class="chip" onclick="toggleChip(this)">Coding & billing</div>
        <div class="chip" onclick="toggleChip(this)">Referral tracking</div>
        <div class="chip" onclick="toggleChip(this)">Alert fatigue</div>
        <div class="chip" onclick="toggleChip(this)">Prior authorizations</div>
        <div class="chip" onclick="toggleChip(this)">Care transitions</div>
        <div class="chip" onclick="toggleChip(this)">Clinical decision support</div>
        <div class="chip" onclick="toggleChip(this)">Patient communication</div>
        <div class="chip" onclick="toggleChip(this)">After-hours burden</div>
      </div>

      <div class="form-group">
        <label>What would make the biggest difference?</label>
        <textarea id="pract-story" placeholder="What's the one thing your current system gets most wrong? What would you build differently?"></textarea>
      </div>

      <div class="form-row">
        <div class="form-group" style="margin-bottom:0;">
          <label>Role / Specialty <span style="color:var(--gray-300)">(optional)</span></label>
          <input type="text" placeholder="e.g. Cardiologist, NP, Admin">
        </div>
        <div class="form-group" style="margin-bottom:0;">
          <label>Email <span style="color:var(--gray-300)">(optional)</span></label>
          <input type="email" placeholder="If you'd like to continue the conversation">
        </div>
      </div>

      <div class="form-footer">
        <div class="form-privacy">Responses are confidential and used solely to improve our clinical solutions. We never sell data.</div>
        <button class="btn btn-primary" onclick="submitVoice('pract-voice-form')">Submit Feedback →</button>
      </div>
    </div>

    <div class="form-success" id="pract-voice-success">
      <div class="success-icon">💜</div>
      <h4>We appreciate you.</h4>
      <p>Your clinical insight directly informs what we build. This is the kind of input that creates real change — thank you for taking the time.</p>
    </div>
  </div>
</section>


<!-- ============================================================
     TECHNOLOGY
============================================================ -->
<section class="technology" id="technology">
  <div class="section-inner">
    <div class="section-label reveal">Technology Stack</div>
    <h2 class="section-headline reveal reveal-delay-1">
      Best-in-class.<br><em>By design.</em>
    </h2>
    <p class="section-body reveal reveal-delay-2">
      We don't build with whatever's available. We architect with what's best — 
      combining proven enterprise platforms with emerging technologies to create 
      a stack that's secure, scalable, and future-proof.
    </p>

    <div class="tech-grid reveal reveal-delay-2">
      <div class="tech-card">
        <div class="tech-icon">🤖</div>
        <div class="tech-name">Constitutional AI</div>
        <div class="tech-role">Safe, explainable AI with built-in clinical reasoning</div>
      </div>
      <div class="tech-card">
        <div class="tech-icon">☁️</div>
        <div class="tech-name">GovCloud Infrastructure</div>
        <div class="tech-role">FedRAMP High authorized cloud for sensitive healthcare data</div>
      </div>
      <div class="tech-card">
        <div class="tech-icon">📊</div>
        <div class="tech-name">Unified Data Lakehouse</div>
        <div class="tech-role">Real-time analytics and ML orchestration at enterprise scale</div>
      </div>
      <div class="tech-card">
        <div class="tech-icon">🔐</div>
        <div class="tech-name">Post-Quantum Security</div>
        <div class="tech-role">NIST-approved quantum-resistant encryption protecting PHI</div>
      </div>
      <div class="tech-card">
        <div class="tech-icon">🏥</div>
        <div class="tech-name">EHR Integration</div>
        <div class="tech-role">SMART on FHIR and HL7 for seamless clinical workflow embedding</div>
      </div>
      <div class="tech-card">
        <div class="tech-icon">🧬</div>
        <div class="tech-name">Medical AI Models</div>
        <div class="tech-role">Specialized clinical and biomedical AI for research and care</div>
      </div>
      <div class="tech-card">
        <div class="tech-icon">⚡</div>
        <div class="tech-name">Real-Time Inference</div>
        <div class="tech-role">Sub-2-second AI response with enterprise uptime guarantees</div>
      </div>
      <div class="tech-card">
        <div class="tech-icon">🔄</div>
        <div class="tech-name">Standards-Based Interop</div>
        <div class="tech-role">FHIR R4, HL7 v2/v3, DICOM, and emerging health data standards</div>
      </div>
    </div>
  </div>
</section>


<!-- ============================================================
     WHY MCCLAIRN
============================================================ -->
<section class="why" id="why">
  <div class="section-inner">
    <div class="why-grid">
      <div>
        <div class="section-label reveal">Why McClairn Health</div>
        <h2 class="section-headline reveal reveal-delay-1" style="color:white;">
          A different kind of<br><em>Health IT company.</em>
        </h2>
        <p class="section-body reveal reveal-delay-2">
          We didn't start with technology. We started with a problem: 
          healthcare systems that serve everyone except the people inside them. 
          That belief shapes everything we build.
        </p>

        <div class="why-reasons reveal reveal-delay-3">
          <div class="why-reason">
            <div class="reason-num">01</div>
            <div>
              <div class="reason-title">Patient-First Architecture</div>
              <div class="reason-desc">Every system we design is evaluated against a single question: does this make care better for the person receiving it?</div>
            </div>
          </div>
          <div class="why-reason">
            <div class="reason-num">02</div>
            <div>
              <div class="reason-title">Purpose-Built, Not Adapted</div>
              <div class="reason-desc">We don't take general AI and retrofit it for healthcare. We build for healthcare from the ground up — with the clinical specificity that demands.</div>
            </div>
          </div>
          <div class="why-reason">
            <div class="reason-num">03</div>
            <div>
              <div class="reason-title">Partnership, Not Procurement</div>
              <div class="reason-desc">We're in this with you for the long term. Our success is measured by your outcomes — not your signature on a contract.</div>
            </div>
          </div>
          <div class="why-reason">
            <div class="reason-num">04</div>
            <div>
              <div class="reason-title">Security Without Compromise</div>
              <div class="reason-desc">Patient data is sacred. Our quantum-safe security architecture protects it against threats today — and the ones still being invented.</div>
            </div>
          </div>
        </div>
      </div>

      <div class="reveal reveal-delay-2">
        <div class="why-cta-block">
          <div class="cta-headline">Ready to transform how your system delivers care?</div>
          <div class="cta-body">
            Whether you're a health system planning a multi-year transformation or a single 
            practice looking to reclaim 10 hours a week — let's start with a conversation.
          </div>
          <div style="display:flex;flex-direction:column;gap:12px;">
            <button class="btn-white" onclick="document.getElementById('contact').scrollIntoView({behavior:'smooth'})">
              Request an Executive Briefing →
            </button>
            <button class="btn-white-outline" onclick="openModal('patient-modal')">
              I'm a patient or practitioner
            </button>
          </div>

          <div style="margin-top:36px;padding-top:32px;border-top:1px solid rgba(255,255,255,0.1);">
            <div style="font-size:11px;letter-spacing:0.1em;text-transform:uppercase;color:rgba(255,255,255,0.3);margin-bottom:16px;">As a Service. At Your Service.</div>
            <div style="display:flex;gap:16px;flex-wrap:wrap;">
              <span style="font-size:12px;color:rgba(255,255,255,0.45);display:flex;align-items:center;gap:6px;">
                <span style="color:var(--green-bright);">✓</span> Clinical AI as a Service
              </span>
              <span style="font-size:12px;color:rgba(255,255,255,0.45);display:flex;align-items:center;gap:6px;">
                <span style="color:var(--green-bright);">✓</span> Practice AI as a Service
              </span>
              <span style="font-size:12px;color:rgba(255,255,255,0.45);display:flex;align-items:center;gap:6px;">
                <span style="color:var(--green-bright);">✓</span> Research AI as a Service
              </span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>


<!-- ============================================================
     CONTACT
============================================================ -->
<section class="contact" id="contact">
  <div class="section-inner">
    <div class="contact-grid">
      <div>
        <div class="section-label reveal">Get in Touch</div>
        <h2 class="section-headline reveal reveal-delay-1">
          Let's talk about<br>what's <em>possible.</em>
        </h2>
        <p class="section-body reveal reveal-delay-2">
          Whether you're a health system CIO, a clinical champion, an investor, 
          or a researcher — we want to hear from you. Great healthcare transformation 
          starts with the right conversation.
        </p>

        <div class="contact-info reveal reveal-delay-3" style="margin-top:40px;">
          <div class="contact-info-item">
            <div class="contact-info-icon">🏢</div>
            <div>
              <div class="contact-info-label">Headquarters</div>
              <div class="contact-info-value">McClairn Health Systems</div>
              <div class="contact-info-sub">United States</div>
            </div>
          </div>
          <div class="contact-info-item">
            <div class="contact-info-icon">📧</div>
            <div>
              <div class="contact-info-label">General Inquiries</div>
              <div class="contact-info-value">hello@mcclairnhealth.com</div>
              <div class="contact-info-sub">We respond within one business day</div>
            </div>
          </div>
          <div class="contact-info-item">
            <div class="contact-info-icon">🤝</div>
            <div>
              <div class="contact-info-label">Enterprise & Partnerships</div>
              <div class="contact-info-value">partners@mcclairnhealth.com</div>
              <div class="contact-info-sub">For health systems, investors, and strategic partners</div>
            </div>
          </div>
        </div>
      </div>

      <div class="contact-form-wrap reveal reveal-delay-1">
        <div class="contact-form-title">Start the conversation.</div>
        <div class="contact-form-sub">Tell us about yourself and what brought you here — we'll make sure the right person gets back to you.</div>

        <div id="contact-form-body">
          <div class="form-row">
            <div class="form-group" style="margin-bottom:0;">
              <label>First Name</label>
              <input type="text" placeholder="First name" id="c-fname">
            </div>
            <div class="form-group" style="margin-bottom:0;">
              <label>Last Name</label>
              <input type="text" placeholder="Last name" id="c-lname">
            </div>
          </div>

          <div class="form-group">
            <label>Email</label>
            <input type="email" placeholder="your@email.com" id="c-email">
          </div>

          <div class="form-group">
            <label>Organization</label>
            <input type="text" placeholder="Health system, company, or institution" id="c-org">
          </div>

          <div class="form-group">
            <label>I am a…</label>
            <select id="c-role">
              <option value="">Select your role</option>
              <option>Health System Executive (CIO / CMIO / CEO)</option>
              <option>Clinician / Physician / Nurse</option>
              <option>Researcher / Academic</option>
              <option>Investor / VC / PE</option>
              <option>Government / Federal Agency</option>
              <option>Patient / Patient Advocate</option>
              <option>Technology / IT Professional</option>
              <option>Other</option>
            </select>
          </div>

          <div class="form-group">
            <label>Message</label>
            <textarea placeholder="What are you working on? What challenges are you facing? What do you hope to accomplish?" id="c-message"></textarea>
          </div>

          <div class="form-footer">
            <div class="form-privacy">We protect your information. No spam, no third-party sharing, ever.</div>
            <button class="btn btn-primary" onclick="submitContact()">Send Message →</button>
          </div>
        </div>

        <div class="form-success" id="contact-success" style="display:none;">
          <div class="success-icon">✉️</div>
          <h4>Message received.</h4>
          <p>We'll be in touch within one business day. Thank you for reaching out to McClairn Health.</p>
        </div>
      </div>
    </div>
  </div>
</section>


<!-- ============================================================
     FOOTER
============================================================ -->
<footer>
  <div class="footer-inner">
    <div class="footer-top">
      <div>
        <!-- Footer logo -->
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 400 110" width="180" height="50">
          <defs>
            <linearGradient id="fpg" x1="0%" y1="0%" x2="60%" y2="100%">
              <stop offset="0%" stop-color="rgba(255,255,255,0.9)"/><stop offset="100%" stop-color="rgba(255,255,255,0.7)"/>
            </linearGradient>
            <linearGradient id="flg1" x1="10%" y1="0%" x2="90%" y2="100%">
              <stop offset="0%" stop-color="#93D13A"/><stop offset="100%" stop-color="#5E9E1A"/>
            </linearGradient>
            <linearGradient id="flg2" x1="10%" y1="0%" x2="90%" y2="100%">
              <stop offset="0%" stop-color="#AADA52"/><stop offset="100%" stop-color="#74B825"/>
            </linearGradient>
            <radialGradient id="fdg" cx="38%" cy="35%" r="65%">
              <stop offset="0%" stop-color="#7B50D8"/><stop offset="100%" stop-color="#4A22A0"/>
            </radialGradient>
          </defs>
          <g transform="translate(-2, 4) scale(0.62)">
            <path d="M88,20 C95,14 108,18 112,30 C116,42 108,58 98,62 C90,66 80,60 78,48 C76,36 81,26 88,20 Z" fill="url(#flg1)"/>
            <path d="M68,50 C73,44 84,46 87,56 C90,65 84,76 76,78 C69,80 63,74 63,65 C63,57 63,56 68,50 Z" fill="url(#flg2)"/>
            <circle cx="60" cy="90" r="8.5" fill="url(#fdg)"/>
          </g>
          <text x="58" y="62" font-family="'Palatino Linotype', Georgia, serif" font-size="52" font-weight="700" letter-spacing="-1" fill="url(#fpg)">McClairn</text>
          <text x="60" y="80" font-family="'Trebuchet MS', Calibri, sans-serif" font-size="12" font-weight="400" letter-spacing="7" fill="rgba(255,255,255,0.35)">HEALTH</text>
        </svg>
        <div class="footer-brand-tagline">
          Patient-centric Health IT transformation. AI-powered. Human-centered. 
          At your service — always.
        </div>
      </div>

      <div>
        <div class="footer-col-title">Solutions</div>
        <div class="footer-links">
          <a href="#services">Clinical Decision Support</a>
          <a href="#services">Ambient Documentation</a>
          <a href="#services">Care Pathway Intelligence</a>
          <a href="#services">Revenue Cycle Optimization</a>
          <a href="#services">Predictive Analytics</a>
          <a href="#services">Quantum-Safe Security</a>
        </div>
      </div>

      <div>
        <div class="footer-col-title">Who We Serve</div>
        <div class="footer-links">
          <a href="#audience">Patients</a>
          <a href="#audience">Practitioners</a>
          <a href="#audience">Researchers</a>
          <a href="#audience">Health Systems</a>
          <a href="#audience">Federal Healthcare</a>
          <a href="#audience">Investors</a>
        </div>
      </div>

      <div>
        <div class="footer-col-title">Company</div>
        <div class="footer-links">
          <a href="#about">About</a>
          <a href="#why">Why McClairn</a>
          <a href="#technology">Technology</a>
          <a href="#contact">Contact</a>
          <a href="#patient-voice">Patient Voice</a>
          <a href="#practitioner-voice">Practitioner Insights</a>
        </div>
      </div>
    </div>

    <div class="footer-bottom">
      <div>© 2025 McClairn Health Systems. All rights reserved.</div>
      <div class="footer-legal">
        <a href="#">Privacy Policy</a>
        <a href="#">Terms of Use</a>
        <a href="#">HIPAA Notice</a>
        <a href="#">Accessibility</a>
      </div>
    </div>
  </div>
</footer>


<!-- ============================================================
     MODALS
============================================================ -->
<!-- Patient Modal -->
<div class="modal-overlay" id="patient-modal" onclick="closeModalOutside(event, 'patient-modal')">
  <div class="modal">
    <button class="modal-close" onclick="closeModal('patient-modal')">✕</button>
    <div class="modal-title">For Patients</div>
    <div class="modal-sub">We're here to listen. If you have a question about care, want to share a healthcare experience, or just want to understand what McClairn Health can do for you — you're in the right place.</div>
    <div class="form-group">
      <label>Your Name <span style="color:var(--gray-300)">(optional)</span></label>
      <input type="text" placeholder="How can we address you?">
    </div>
    <div class="form-group">
      <label>Email</label>
      <input type="email" placeholder="your@email.com">
    </div>
    <div class="form-group">
      <label>What's on your mind?</label>
      <textarea placeholder="A question, a concern, a story — whatever you'd like us to know." style="min-height:100px;"></textarea>
    </div>
    <div style="display:flex;justify-content:flex-end;gap:12px;margin-top:8px;">
      <button class="btn btn-ghost" onclick="closeModal('patient-modal')">Cancel</button>
      <button class="btn btn-green" onclick="closeModal('patient-modal')">Send →</button>
    </div>
  </div>
</div>

<!-- Practitioner Modal -->
<div class="modal-overlay" id="practitioner-modal" onclick="closeModalOutside(event, 'practitioner-modal')">
  <div class="modal">
    <button class="modal-close" onclick="closeModal('practitioner-modal')">✕</button>
    <div class="modal-title">For Clinicians</div>
    <div class="modal-sub">You're the experts in the room. Tell us what your system gets wrong and what you'd fix first. We build solutions around clinical reality — not theoretical use cases.</div>
    <div class="form-group">
      <label>Name & Specialty <span style="color:var(--gray-300)">(optional)</span></label>
      <input type="text" placeholder="e.g. Dr. Smith, Internal Medicine">
    </div>
    <div class="form-group">
      <label>Email</label>
      <input type="email" placeholder="your@email.com">
    </div>
    <div class="form-group">
      <label>What would you change?</label>
      <textarea placeholder="What's the most broken thing in your clinical workflow? What would make tomorrow better?" style="min-height:110px;"></textarea>
    </div>
    <div style="display:flex;justify-content:flex-end;gap:12px;margin-top:8px;">
      <button class="btn btn-ghost" onclick="closeModal('practitioner-modal')">Cancel</button>
      <button class="btn btn-primary" onclick="closeModal('practitioner-modal')">Send Feedback →</button>
    </div>
  </div>
</div>


<!-- ============================================================
     JAVASCRIPT
============================================================ -->
<script>
// ---- NAV SCROLL STATE ----
window.addEventListener('scroll', () => {
  const nav = document.getElementById('mainNav');
  if (window.scrollY > 20) nav.classList.add('scrolled');
  else nav.classList.remove('scrolled');
});

// ---- SCROLL REVEAL ----
const revealObserver = new IntersectionObserver((entries) => {
  entries.forEach(e => {
    if (e.isIntersecting) {
      e.target.classList.add('visible');
      revealObserver.unobserve(e.target);
    }
  });
}, { threshold: 0.1, rootMargin: '0px 0px -40px 0px' });

document.querySelectorAll('.reveal').forEach(el => revealObserver.observe(el));

// ---- AUDIENCE TABS ----
function switchTab(id) {
  document.querySelectorAll('.audience-tab').forEach(t => t.classList.remove('active'));
  document.querySelectorAll('.audience-panel').forEach(p => p.classList.remove('active'));
  const tabs = document.querySelectorAll('.audience-tab');
  const tabMap = { patients: 0, practitioners: 1, researchers: 2, enterprise: 3 };
  tabs[tabMap[id]].classList.add('active');
  document.getElementById('tab-' + id).classList.add('active');
}

// ---- CHIP TOGGLE ----
function toggleChip(el) {
  el.classList.toggle('selected');
}

// ---- VOICE FORM SUBMIT ----
function submitVoice(formId) {
  const form = document.getElementById(formId);
  const successId = formId === 'patient-voice-form' ? 'patient-voice-success' : 'pract-voice-success';
  form.style.display = 'none';
  document.getElementById(successId).style.display = 'block';
}

// ---- CONTACT FORM SUBMIT ----
function submitContact() {
  const email = document.getElementById('c-email').value;
  const message = document.getElementById('c-message').value;
  if (!email || !message) {
    alert('Please provide your email and a message so we can get back to you.');
    return;
  }
  document.getElementById('contact-form-body').style.display = 'none';
  document.getElementById('contact-success').style.display = 'block';
}

// ---- MODALS ----
function openModal(id) {
  document.getElementById(id).classList.add('open');
  document.body.style.overflow = 'hidden';
}
function closeModal(id) {
  document.getElementById(id).classList.remove('open');
  document.body.style.overflow = '';
}
function closeModalOutside(e, id) {
  if (e.target.id === id) closeModal(id);
}
document.addEventListener('keydown', e => {
  if (e.key === 'Escape') {
    document.querySelectorAll('.modal-overlay.open').forEach(m => {
      m.classList.remove('open');
      document.body.style.overflow = '';
    });
  }
});

// ---- SMOOTH NAV LINKS ----
document.querySelectorAll('a[href^="#"]').forEach(a => {
  a.addEventListener('click', e => {
    const target = document.querySelector(a.getAttribute('href'));
    if (target) {
      e.preventDefault();
      target.scrollIntoView({ behavior: 'smooth' });
    }
  });
});
</script>

</body>
</html>
