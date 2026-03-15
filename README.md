<!DOCTYPE html>

<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Still Ground — 15-Minute Guided Meditation</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;1,300;1,400&family=Jost:wght@200;300;400&display=swap');

*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

:root {
–ink:      #1a1a2e;
–deep:     #0d0d1a;
–mist:     #e8e4f0;
–veil:     #c8c0e0;
–gold:     #c9a84c;
–gold-dim: rgba(201,168,76,0.3);
–rose:     #a07080;
–sage:     #7a9e8a;
–cream:    #f5f0e8;
–sky:      #4a6a9a;
}

html, body {
width: 100%; height: 100%;
background: var(–deep);
color: var(–mist);
font-family: ‘Jost’, sans-serif;
font-weight: 300;
overflow: hidden;
user-select: none;
}

#starfield { position: fixed; inset: 0; pointer-events: none; opacity: 0.5; }

.orb { position: fixed; border-radius: 50%; filter: blur(80px); pointer-events: none; transition: opacity 8s ease; }
.orb-1 { width:500px;height:500px;top:-100px;left:-100px;background:radial-gradient(circle,rgba(74,106,154,0.25) 0%,transparent 70%);animation:drift1 20s ease-in-out infinite; }
.orb-2 { width:600px;height:600px;bottom:-150px;right:-100px;background:radial-gradient(circle,rgba(160,112,128,0.2) 0%,transparent 70%);animation:drift2 25s ease-in-out infinite; }
.orb-3 { width:400px;height:400px;top:50%;left:50%;transform:translate(-50%,-50%);background:radial-gradient(circle,rgba(122,158,138,0.12) 0%,transparent 70%);animation:drift3 18s ease-in-out infinite; }
@keyframes drift1{0%,100%{transform:translate(0,0)}50%{transform:translate(40px,60px)}}
@keyframes drift2{0%,100%{transform:translate(0,0)}50%{transform:translate(-50px,-40px)}}
@keyframes drift3{0%,100%{transform:translate(-50%,-50%) scale(1)}50%{transform:translate(-50%,-50%) scale(1.2)}}

.screen { position:fixed;inset:0;display:flex;flex-direction:column;align-items:center;justify-content:center;padding:40px 24px;opacity:0;pointer-events:none;transition:opacity 1.5s ease; }
.screen.active { opacity:1;pointer-events:all; }

/* ── LANDING ── */
#landing { text-align:center; gap:0; }
.brand { font-family:‘Cormorant Garamond’,serif;font-weight:300;font-size:clamp(13px,1.8vw,16px);letter-spacing:.35em;color:var(–gold);text-transform:uppercase;margin-bottom:32px;opacity:0;animation:fadeUp 1.2s ease 0.3s forwards; }
.main-title { font-family:‘Cormorant Garamond’,serif;font-weight:300;font-size:clamp(42px,7vw,80px);line-height:1.1;color:var(–cream);margin-bottom:20px;opacity:0;animation:fadeUp 1.2s ease 0.6s forwards; }
.main-title em { font-style:italic;color:var(–veil); }
.subtitle { font-size:clamp(13px,1.6vw,15px);letter-spacing:.18em;color:var(–veil);text-transform:uppercase;margin-bottom:48px;opacity:0;animation:fadeUp 1.2s ease 0.9s forwards; }
.theme-tag { font-family:‘Cormorant Garamond’,serif;font-style:italic;font-size:clamp(15px,2vw,18px);color:rgba(200,192,224,0.6);margin-bottom:40px;opacity:0;animation:fadeUp 1.2s ease 1.1s forwards; }

/* Voice selector */
.voice-row { display:flex;flex-direction:column;align-items:center;gap:10px;margin-bottom:36px;opacity:0;animation:fadeUp 1.2s ease 1.25s forwards; }
.voice-label { font-size:11px;letter-spacing:.22em;text-transform:uppercase;color:rgba(200,192,224,0.4); }
.voice-select { background:transparent;border:1px solid rgba(201,168,76,0.3);color:var(–veil);font-family:‘Jost’,sans-serif;font-weight:300;font-size:13px;padding:8px 20px;border-radius:0;cursor:pointer;outline:none;max-width:320px;width:100%; }
.voice-select option { background:#1a1a2e;color:var(–cream); }

/* Volume row */
.vol-row { display:flex;align-items:center;gap:20px;margin-bottom:36px;opacity:0;animation:fadeUp 1.2s ease 1.35s forwards; }
.vol-label { font-size:11px;letter-spacing:.22em;text-transform:uppercase;color:rgba(200,192,224,0.4);white-space:nowrap; }
.vol-group { display:flex;flex-direction:column;align-items:center;gap:4px; }
.vol-sub { font-size:10px;letter-spacing:.15em;color:rgba(200,192,224,0.3);text-transform:uppercase; }
input[type=range] { -webkit-appearance:none;width:100px;height:2px;background:rgba(201,168,76,0.25);outline:none;cursor:pointer; }
input[type=range]::-webkit-slider-thumb { -webkit-appearance:none;width:12px;height:12px;border-radius:50%;background:var(–gold);cursor:pointer; }

.begin-btn { background:transparent;border:1px solid var(–gold);color:var(–gold);font-family:‘Jost’,sans-serif;font-weight:200;font-size:13px;letter-spacing:.3em;text-transform:uppercase;padding:16px 48px;cursor:pointer;position:relative;overflow:hidden;opacity:0;animation:fadeUp 1.2s ease 1.5s forwards;transition:color .4s,background .4s; }
.begin-btn::before { content:’’;position:absolute;inset:0;background:var(–gold);transform:translateX(-100%);transition:transform .4s ease;z-index:-1; }
.begin-btn:hover { color:var(–deep); }
.begin-btn:hover::before { transform:translateX(0); }
.prep-note { margin-top:28px;font-size:12px;letter-spacing:.12em;color:rgba(200,192,224,0.3);text-align:center;opacity:0;animation:fadeUp 1.2s ease 1.7s forwards; }

@keyframes fadeUp { from{opacity:0;transform:translateY(18px)} to{opacity:1;transform:translateY(0)} }

/* ── MEDITATION ── */
#meditation { display:flex;flex-direction:column;align-items:center;justify-content:space-between;padding:48px 24px 40px;gap:0; }

.top-bar { width:100%;max-width:600px;display:flex;align-items:center;justify-content:space-between;opacity:.6; }
.phase-label { font-size:11px;letter-spacing:.28em;text-transform:uppercase;color:var(–gold); }
.timer-display { font-family:‘Cormorant Garamond’,serif;font-weight:300;font-size:18px;letter-spacing:.08em;color:var(–veil); }
.phase-dots { display:flex;gap:8px;align-items:center; }
.dot { width:5px;height:5px;border-radius:50%;background:rgba(200,192,224,0.25);transition:background .6s,transform .6s; }
.dot.done { background:var(–gold); }
.dot.active { background:var(–gold);transform:scale(1.4); }

.breath-center { flex:1;display:flex;flex-direction:column;align-items:center;justify-content:center;gap:44px; }

.breath-ring-wrap { position:relative;width:180px;height:180px;display:flex;align-items:center;justify-content:center; }
.breath-ring { position:absolute;inset:0;border-radius:50%;border:1px solid rgba(201,168,76,0.2);transition:transform 4s cubic-bezier(0.4,0,0.2,1),border-color 4s ease; }
.breath-ring.r2 { inset:-16px;opacity:.5; }
.breath-ring.r3 { inset:-32px;opacity:.2; }
.breath-ring.inhale { border-color:rgba(201,168,76,0.5);transform:scale(1.12); }
.breath-ring.r2.inhale { transform:scale(1.1); }
.breath-ring.r3.inhale { transform:scale(1.08); }
.breath-core { width:90px;height:90px;border-radius:50%;background:radial-gradient(circle at 40% 40%,rgba(201,168,76,0.3),rgba(122,158,138,0.15),rgba(74,106,154,0.1));transition:transform 4s cubic-bezier(0.4,0,0.2,1),box-shadow 4s ease;box-shadow:0 0 30px rgba(201,168,76,0.15),inset 0 0 20px rgba(201,168,76,0.08); }
.breath-core.inhale { transform:scale(1.18);box-shadow:0 0 60px rgba(201,168,76,0.3),inset 0 0 30px rgba(201,168,76,0.15); }
.breath-word { font-family:‘Cormorant Garamond’,serif;font-weight:300;font-style:italic;font-size:14px;letter-spacing:.2em;color:rgba(201,168,76,0.7);text-align:center;min-height:22px;transition:opacity .8s;position:absolute;bottom:-36px;left:50%;transform:translateX(-50%);white-space:nowrap; }

.script-area { max-width:580px;width:100%;text-align:center;min-height:120px;display:flex;align-items:center;justify-content:center; }
.script-text { font-family:‘Cormorant Garamond’,serif;font-weight:300;font-size:clamp(17px,2.5vw,22px);line-height:1.75;color:var(–cream);opacity:0;transform:translateY(8px);transition:opacity 1.2s ease,transform 1.2s ease; }
.script-text.visible { opacity:1;transform:translateY(0); }
.script-text em { font-style:italic;color:var(–veil); }

.phase-title-display { font-family:‘Cormorant Garamond’,serif;font-weight:300;font-size:clamp(11px,1.4vw,13px);letter-spacing:.3em;text-transform:uppercase;color:rgba(201,168,76,0.5);text-align:center;min-height:20px;transition:opacity .8s; }

.progress-track { width:100%;max-width:500px;height:1px;background:rgba(200,192,224,0.1);position:relative; }
.progress-fill { position:absolute;top:0;left:0;height:100%;background:linear-gradient(90deg,var(–gold-dim),var(–gold));transition:width 1s linear; }
.progress-glow { position:absolute;top:-2px;right:0;width:6px;height:6px;border-radius:50%;background:var(–gold);box-shadow:0 0 8px var(–gold);transform:translateX(50%); }

/* Audio controls in meditation */
.audio-controls { display:flex;align-items:center;gap:16px;margin-top:4px; }
.aud-icon { font-size:14px;cursor:pointer;opacity:.4;transition:opacity .3s;background:none;border:none;color:var(–veil);padding:4px; }
.aud-icon:hover { opacity:.8; }
.aud-icon.muted { opacity:.2; }
.mini-vol { width:70px; }

/* ── END ── */
#ending { text-align:center; }
.end-title { font-family:‘Cormorant Garamond’,serif;font-weight:300;font-size:clamp(32px,5vw,52px);color:var(–cream);margin-bottom:16px; }
.end-sub { font-family:‘Cormorant Garamond’,serif;font-style:italic;font-size:clamp(16px,2.2vw,20px);color:var(–veil);margin-bottom:48px; }
.namaste { font-family:‘Cormorant Garamond’,serif;font-weight:300;font-size:clamp(28px,4vw,44px);color:var(–gold);letter-spacing:.08em;margin-bottom:56px; }
.fade-in-end { opacity:0; }
.fade-in-end.show { animation:fadeUp 1.5s ease forwards; }
.fade-in-end.show.d1 { animation-delay:.0s; }
.fade-in-end.show.d2 { animation-delay:.6s; }
.fade-in-end.show.d3 { animation-delay:1.1s; }
.fade-in-end.show.d4 { animation-delay:1.6s; }
.restart-btn { background:transparent;border:1px solid rgba(200,192,224,0.3);color:rgba(200,192,224,0.5);font-family:‘Jost’,sans-serif;font-weight:200;font-size:11px;letter-spacing:.28em;text-transform:uppercase;padding:14px 40px;cursor:pointer;transition:color .3s,border-color .3s; }
.restart-btn:hover { color:var(–cream);border-color:rgba(200,192,224,0.6); }

/* ── PAUSE OVERLAY ── */
#pause-overlay { position:fixed;inset:0;display:flex;align-items:center;justify-content:center;background:rgba(13,13,26,0.85);opacity:0;pointer-events:none;transition:opacity .4s;z-index:100; }
#pause-overlay.visible { opacity:1;pointer-events:all; }
.pause-word { font-family:‘Cormorant Garamond’,serif;font-weight:300;font-style:italic;font-size:32px;color:var(–veil);margin-bottom:32px; }
.resume-btn { background:transparent;border:1px solid var(–gold);color:var(–gold);font-family:‘Jost’,sans-serif;font-weight:200;font-size:12px;letter-spacing:.25em;text-transform:uppercase;padding:14px 44px;cursor:pointer;transition:background .3s,color .3s; }
.resume-btn:hover { background:var(–gold);color:var(–deep); }

.pause-btn { position:fixed;bottom:28px;right:28px;width:40px;height:40px;border:1px solid rgba(200,192,224,0.2);border-radius:50%;background:transparent;color:rgba(200,192,224,0.35);cursor:pointer;font-size:14px;display:none;align-items:center;justify-content:center;transition:color .3s,border-color .3s;z-index:50; }
.pause-btn:hover { color:var(–cream);border-color:rgba(200,192,224,0.5); }
.pause-btn.show { display:flex; }
</style>

</head>
<body>

<canvas id="starfield"></canvas>

<div class="orb orb-1"></div>
<div class="orb orb-2"></div>
<div class="orb orb-3"></div>

<!-- ── LANDING ── -->

<div class="screen active" id="landing">
  <div class="brand">TheSoulPractice</div>
  <h1 class="main-title">Still<br><em>Ground</em></h1>
  <div class="subtitle">15-Minute Guided Meditation</div>
  <div class="theme-tag">Pratyahara — the art of turning inward</div>

  <div class="voice-row">
    <div class="voice-label">Narrator Voice</div>
    <select class="voice-select" id="voice-select">
      <option value="">Loading voices…</option>
    </select>
  </div>

  <div class="vol-row">
    <div class="vol-label">Volume</div>
    <div class="vol-group">
      <input type="range" id="vol-voice"   min="0" max="1" step="0.05" value="1">
      <div class="vol-sub">Voice</div>
    </div>
    <div class="vol-group">
      <input type="range" id="vol-ambient" min="0" max="1" step="0.05" value="0.35">
      <div class="vol-sub">Ambient</div>
    </div>
    <div class="vol-group">
      <input type="range" id="vol-bells"   min="0" max="1" step="0.05" value="0.7">
      <div class="vol-sub">Bells</div>
    </div>
  </div>

<button class="begin-btn" onclick="startMeditation()">Begin</button>

  <p class="prep-note">Find a comfortable seat &nbsp;·&nbsp; Earphones recommended &nbsp;·&nbsp; No experience needed</p>
</div>

<!-- ── MEDITATION ── -->

<div class="screen" id="meditation">
  <div class="top-bar">
    <div class="phase-label" id="phase-label">Arriving</div>
    <div class="timer-display" id="timer">15:00</div>
    <div class="phase-dots" id="dots"></div>
  </div>

  <div class="breath-center">
    <div class="breath-ring-wrap" id="breath-wrap">
      <div class="breath-ring r3" id="ring3"></div>
      <div class="breath-ring r2" id="ring2"></div>
      <div class="breath-ring r1" id="ring1"></div>
      <div class="breath-core"   id="core"></div>
      <div class="breath-word"   id="breath-word"></div>
    </div>

```
<div class="script-area">
  <p class="script-text" id="script-text"></p>
</div>
```

  </div>

  <div class="phase-title-display" id="phase-title-display"></div>

  <div class="progress-track">
    <div class="progress-fill" id="progress">
      <div class="progress-glow"></div>
    </div>
  </div>
</div>

<!-- ── ENDING ── -->

<div class="screen" id="ending">
  <div class="end-title fade-in-end" id="et1">You have arrived.</div>
  <div class="end-sub   fade-in-end" id="et2">Carry this stillness with you.</div>
  <div class="namaste   fade-in-end" id="et3">Namaste</div>
  <button class="restart-btn fade-in-end" id="et4" onclick="restartMeditation()">Begin Again</button>
</div>

<!-- ── PAUSE ── -->

<div id="pause-overlay">
  <div class="pause-content">
    <div class="pause-word">Paused</div>
    <button class="resume-btn" onclick="resumeMeditation()">Continue</button>
  </div>
</div>

<button class="pause-btn" id="pause-btn" onclick="togglePause()">⏸</button>

<script>
// ═══════════════════════════════════════════════════════════
// STARFIELD
// ═══════════════════════════════════════════════════════════
(function() {
  const canvas = document.getElementById('starfield');
  const ctx = canvas.getContext('2d');
  let stars = [];
  function resize() { canvas.width = innerWidth; canvas.height = innerHeight; }
  function init() {
    stars = [];
    for (let i = 0; i < 120; i++) stars.push({ x: Math.random()*canvas.width, y: Math.random()*canvas.height, r: Math.random()*1.2, a: Math.random(), speed: 0.001+Math.random()*0.003, phase: Math.random()*Math.PI*2 });
  }
  function draw(t) {
    ctx.clearRect(0,0,canvas.width,canvas.height);
    stars.forEach(s => {
      const alpha = s.a*(0.4+0.6*Math.sin(t*s.speed+s.phase));
      ctx.beginPath(); ctx.arc(s.x,s.y,s.r,0,Math.PI*2);
      ctx.fillStyle=`rgba(200,190,230,${alpha})`; ctx.fill();
    });
    requestAnimationFrame(draw);
  }
  resize(); init();
  window.addEventListener('resize', ()=>{ resize(); init(); });
  requestAnimationFrame(draw);
})();

// ═══════════════════════════════════════════════════════════
// AUDIO ENGINE
// ═══════════════════════════════════════════════════════════
let audioCtx = null;
let ambientGain, bellGain;
let ambientNodes = [];
let isMuted = false;

function initAudio() {
  audioCtx = new (window.AudioContext || window.webkitAudioContext)();
  ambientGain = audioCtx.createGain();
  ambientGain.gain.value = parseFloat(document.getElementById('vol-ambient').value);
  ambientGain.connect(audioCtx.destination);

  bellGain = audioCtx.createGain();
  bellGain.gain.value = parseFloat(document.getElementById('vol-bells').value);
  bellGain.connect(audioCtx.destination);

  // Wire volume sliders
  document.getElementById('vol-ambient').addEventListener('input', e => {
    if (ambientGain) ambientGain.gain.value = parseFloat(e.target.value);
  });
  document.getElementById('vol-bells').addEventListener('input', e => {
    if (bellGain) bellGain.gain.value = parseFloat(e.target.value);
  });

  startAmbient();
}

// ── AMBIENT DRONE ─────────────────────────────────────────
function startAmbient() {
  // Tibetan bowl drone — layered slow-beating tones
  const baseFreqs = [110, 136.1, 174.6, 220]; // A2, C#3, F3, A3 — resonant bowl harmonics
  ambientNodes = [];

  baseFreqs.forEach((freq, i) => {
    const osc1 = audioCtx.createOscillator();
    const osc2 = audioCtx.createOscillator();
    const gain = audioCtx.createGain();

    // Slight detuning for natural beating
    osc1.frequency.value = freq;
    osc2.frequency.value = freq + (i % 2 === 0 ? 0.3 : 0.5);
    osc1.type = 'sine';
    osc2.type = 'sine';

    gain.gain.value = 0.08 - i * 0.01;
    osc1.connect(gain); osc2.connect(gain);
    gain.connect(ambientGain);

    osc1.start(); osc2.start();
    ambientNodes.push(osc1, osc2);

    // Slow amplitude modulation — breath-like
    const lfo = audioCtx.createOscillator();
    const lfoGain = audioCtx.createGain();
    lfo.frequency.value = 0.05 + i * 0.015;
    lfoGain.gain.value = 0.03;
    lfo.connect(lfoGain);
    lfoGain.connect(gain.gain);
    lfo.start();
    ambientNodes.push(lfo);
  });

  // Soft noise pad
  const bufferSize = audioCtx.sampleRate * 4;
  const buffer = audioCtx.createBuffer(1, bufferSize, audioCtx.sampleRate);
  const data = buffer.getChannelData(0);
  for (let i = 0; i < bufferSize; i++) data[i] = (Math.random() * 2 - 1) * 0.015;

  const noiseSource = audioCtx.createBufferSource();
  noiseSource.buffer = buffer;
  noiseSource.loop = true;

  const noiseFilter = audioCtx.createBiquadFilter();
  noiseFilter.type = 'lowpass';
  noiseFilter.frequency.value = 600;

  const noiseGain = audioCtx.createGain();
  noiseGain.gain.value = 0.4;

  noiseSource.connect(noiseFilter);
  noiseFilter.connect(noiseGain);
  noiseGain.connect(ambientGain);
  noiseSource.start();
  ambientNodes.push(noiseSource);
}

// ── TIBETAN BOWL BELL ──────────────────────────────────────
function playBell(type = 'phase') {
  if (!audioCtx || !bellGain) return;

  const freqs = type === 'phase'
    ? [432, 528, 639]          // transition bell — fuller chord
    : [528];                    // breath bell — single soft tone

  const duration = type === 'phase' ? 4.5 : 2.5;
  const volume   = type === 'phase' ? 0.35 : 0.18;

  freqs.forEach((freq, i) => {
    const osc  = audioCtx.createOscillator();
    const gain = audioCtx.createGain();

    osc.type = 'sine';
    osc.frequency.value = freq;

    // Layered harmonics for bowl character
    const osc2 = audioCtx.createOscillator();
    osc2.type = 'sine';
    osc2.frequency.value = freq * 2.756; // characteristic bowl overtone
    const gain2 = audioCtx.createGain();
    gain2.gain.value = volume * 0.15;
    osc2.connect(gain2);
    gain2.connect(bellGain);
    osc2.start();
    osc2.stop(audioCtx.currentTime + duration);

    const now = audioCtx.currentTime + i * 0.08;
    gain.gain.setValueAtTime(0, now);
    gain.gain.linearRampToValueAtTime(volume * (1 - i * 0.08), now + 0.015);
    gain.gain.exponentialRampToValueAtTime(0.001, now + duration);

    osc.connect(gain);
    gain.connect(bellGain);
    osc.start(now);
    osc.stop(now + duration);
  });
}

// ── BREATHING SOUND ────────────────────────────────────────
function playBreathSound(type) {
  if (!audioCtx || !ambientGain) return;

  const duration = type === 'inhale' ? 4 : 5;
  const bufferSize = audioCtx.sampleRate * duration;
  const buffer = audioCtx.createBuffer(1, bufferSize, audioCtx.sampleRate);
  const data = buffer.getChannelData(0);

  for (let i = 0; i < bufferSize; i++) {
    data[i] = (Math.random() * 2 - 1);
  }

  const source = audioCtx.createBufferSource();
  source.buffer = buffer;

  const filter = audioCtx.createBiquadFilter();
  filter.type = 'bandpass';
  filter.frequency.value = type === 'inhale' ? 900 : 600;
  filter.Q.value = 1.5;

  const gain = audioCtx.createGain();
  const now = audioCtx.currentTime;
  const peak = duration * 0.35;
  gain.gain.setValueAtTime(0, now);
  gain.gain.linearRampToValueAtTime(0.04, now + peak);
  gain.gain.linearRampToValueAtTime(0, now + duration);

  source.connect(filter);
  filter.connect(gain);
  gain.connect(ambientGain);
  source.start();
  source.stop(now + duration);
}

// ═══════════════════════════════════════════════════════════
// TEXT-TO-SPEECH
// ═══════════════════════════════════════════════════════════
let voices = [];
let selectedVoice = null;
let speechQueue = [];
let isSpeaking = false;
let speechEnabled = true;

function loadVoices() {
  voices = window.speechSynthesis.getVoices();
  const sel = document.getElementById('voice-select');
  sel.innerHTML = '';

  if (voices.length === 0) {
    sel.innerHTML = '<option>Voice not available on this device</option>';
    return;
  }

  // Prefer English voices, sort: females first, then by name
  const engVoices = voices.filter(v => v.lang.startsWith('en'));
  const displayVoices = engVoices.length > 0 ? engVoices : voices;

  // Mark remote (higher quality) voices
  displayVoices.forEach((v, i) => {
    const opt = document.createElement('option');
    opt.value = i;
    const quality = v.localService ? '' : ' ✦';
    opt.textContent = `${v.name}${quality} (${v.lang})`;
    sel.appendChild(opt);
  });

  // Auto-select a good default — prefer "Samantha", "Karen", "Moira", or first female-sounding name
  const preferred = ['Samantha','Karen','Moira','Tessa','Fiona','Victoria','Serena','Helena','Alice'];
  let defaultIdx = 0;
  for (let p of preferred) {
    const found = displayVoices.findIndex(v => v.name.includes(p));
    if (found !== -1) { defaultIdx = found; break; }
  }
  sel.value = defaultIdx;
  selectedVoice = displayVoices[defaultIdx];

  sel.addEventListener('change', () => {
    selectedVoice = displayVoices[parseInt(sel.value)];
  });

  // Store reference for later
  window._displayVoices = displayVoices;
}

window.speechSynthesis.onvoiceschanged = loadVoices;
loadVoices();

function speak(text, onEnd) {
  if (!text || !speechEnabled) { if (onEnd) onEnd(); return; }

  // Cancel any current speech
  window.speechSynthesis.cancel();

  const utt = new SpeechSynthesisUtterance(text);
  if (selectedVoice) utt.voice = selectedVoice;
  utt.rate  = 0.82;
  utt.pitch = 0.95;
  utt.volume = parseFloat(document.getElementById('vol-voice').value);

  utt.onend = () => { if (onEnd) onEnd(); };
  utt.onerror = () => { if (onEnd) onEnd(); };

  window.speechSynthesis.speak(utt);
}

function stopSpeech() {
  window.speechSynthesis.cancel();
}

// ═══════════════════════════════════════════════════════════
// MEDITATION DATA
// ═══════════════════════════════════════════════════════════
const TOTAL_SECONDS = 15 * 60;

const phases = [
  {
    name: "Arriving", label: "Phase I — Arrival",
    duration: 120, breathCycle: 8,
    lines: [
      { t: 0,   text: "Close your eyes, or let your gaze soften toward the floor." },
      { t: 12,  text: "Feel the weight of your body in this seat. Let it be heavy." },
      { t: 26,  text: "There is nowhere to get to right now. You have arrived." },
      { t: 40,  text: "Notice the sounds in the room — not reaching toward them. Just noticing." },
      { t: 58,  text: "Let the attention begin to turn inward. Toward the breath. Toward the body." },
      { t: 76,  text: "Take one breath in — slow, full. And let the exhale be longer than the inhale." },
      { t: 96,  text: "Feel the body soften with that exhale. Just a little. That is enough." },
      { t: 112, text: "" }
    ]
  },
  {
    name: "The Breath", label: "Phase II — The Breath",
    duration: 180, breathCycle: 7,
    lines: [
      { t: 0,   text: "Bring all of your attention to the breath." },
      { t: 14,  text: "Not controlling it. Just watching it happen." },
      { t: 28,  text: "The body knows how to breathe. It has been doing this your entire life — without your help." },
      { t: 50,  text: "Notice where you feel the breath most clearly. The nostrils. The chest. The belly." },
      { t: 68,  text: "Let that place be the anchor. When the mind drifts — and it will — come back here." },
      { t: 88,  text: "Not as failure. As practice. The returning is the practice." },
      { t: 106, text: "Each exhale: a little more settling. Like a snow globe going still." },
      { t: 124, text: "" },
      { t: 144, text: "Notice: is the breath different from when you began? Longer? Quieter?" },
      { t: 162, text: "That shift is you, turning inward. That is pratyahara." },
      { t: 174, text: "" }
    ]
  },
  {
    name: "The Body", label: "Phase III — Body Scan",
    duration: 210, breathCycle: 8,
    lines: [
      { t: 0,   text: "Begin a slow scan from the soles of the feet upward." },
      { t: 14,  text: "Not looking for anything wrong. Simply noticing what is here." },
      { t: 28,  text: "The feet and ankles. The calves. The backs of the knees." },
      { t: 46,  text: "The thighs. The hips. The lower back. Is there any holding here? Let it soften." },
      { t: 66,  text: "The belly. Soft and rising. The ribs expanding with each breath." },
      { t: 84,  text: "The chest. Wider than you might have let yourself feel. Let it be open." },
      { t: 102, text: "The shoulders. Let them fall — further than you think they can." },
      { t: 118, text: "The arms. The hands. Open. Receiving." },
      { t: 136, text: "The throat, soft. The jaw, unclenched. The tongue resting in the lower jaw." },
      { t: 154, text: "The brow, smooth. The eyes, soft behind the lids." },
      { t: 170, text: "" },
      { t: 188, text: "Your whole body — from sole to crown — at rest." },
      { t: 202, text: "" }
    ]
  },
  {
    name: "The Stillness", label: "Phase IV — Stillness",
    duration: 210, breathCycle: 9,
    lines: [
      { t: 0,   text: "Rest in the stillness that has gathered." },
      { t: 16,  text: "You did not manufacture this. You simply gave it the conditions." },
      { t: 32,  text: "When we stop feeding the outward pull — the mind settles on its own. Like mud settling in still water." },
      { t: 56,  text: "" },
      { t: 76,  text: "Notice the quality of the silence — not the absence of sound, but the quality of inner space." },
      { t: 98,  text: "That space is always here. Underneath everything." },
      { t: 114, text: "" },
      { t: 134, text: "If a thought arises — notice it, like watching a cloud move across the sky. And return." },
      { t: 154, text: "Return to the breath. Return to the body. Return to here." },
      { t: 172, text: "" },
      { t: 192, text: "You are not your thoughts. You are the awareness watching them." }
    ]
  },
  {
    name: "The Offering", label: "Phase V — The Offering",
    duration: 150, breathCycle: 8,
    lines: [
      { t: 0,   text: "Bring to mind one small thing you want to carry from this practice into the rest of your day." },
      { t: 24,  text: "Not a grand intention. Something small." },
      { t: 38,  text: "The quality of your attention in your next conversation. A full breath before you speak." },
      { t: 60,  text: "The space between stimulus and response — that pause you found here today." },
      { t: 80,  text: "" },
      { t: 100, text: "Let it land somewhere it can grow." },
      { t: 114, text: "" },
      { t: 128, text: "The world will be loud again soon. You know now there is a quiet place inside it." },
      { t: 142, text: "You have been there." }
    ]
  },
  {
    name: "Returning", label: "Phase VI — Returning",
    duration: 30, breathCycle: 6,
    lines: [
      { t: 0,  text: "Begin to deepen the breath. Let it become intentional again." },
      { t: 14, text: "Wiggle the fingers and toes. Let the body begin to stir." },
      { t: 24, text: "When you are ready — open your eyes slowly." }
    ]
  }
];

// ═══════════════════════════════════════════════════════════
// STATE
// ═══════════════════════════════════════════════════════════
let S = {
  running: false, paused: false,
  elapsed: 0, phaseIndex: 0, phaseElapsed: 0,
  lastLineIndex: -1, lastSpokenIndex: -1,
  interval: null, breathInterval: null
};

// ── INIT DOTS ─────────────────────────────────────────────
function initDots() {
  const c = document.getElementById('dots');
  c.innerHTML = '';
  phases.forEach((_, i) => {
    const d = document.createElement('div');
    d.className = 'dot' + (i === 0 ? ' active' : '');
    d.id = `dot-${i}`;
    c.appendChild(d);
  });
}

// ── START ─────────────────────────────────────────────────
function startMeditation() {
  initAudio();

  // Update selected voice
  const sel = document.getElementById('voice-select');
  if (window._displayVoices && sel.value !== '') {
    selectedVoice = window._displayVoices[parseInt(sel.value)];
  }

  document.getElementById('landing').classList.remove('active');
  setTimeout(() => {
    document.getElementById('meditation').classList.add('active');
    document.getElementById('pause-btn').classList.add('show');
    initDots();
    updatePhaseUI(0);
    Object.assign(S, { running: true, elapsed: 0, phaseIndex: 0, phaseElapsed: 0, lastLineIndex: -1, lastSpokenIndex: -1, paused: false });
    startTimers();
    // Opening bell
    setTimeout(() => playBell('phase'), 600);
  }, 800);
}

function startTimers() {
  S.interval = setInterval(tick, 1000);
  startBreathCycle();
}

// ── TICK ──────────────────────────────────────────────────
function tick() {
  if (!S.running || S.paused) return;
  S.elapsed++;
  S.phaseElapsed++;

  const remaining = TOTAL_SECONDS - S.elapsed;
  const m = Math.floor(remaining / 60);
  const s = remaining % 60;
  document.getElementById('timer').textContent = `${String(m).padStart(2,'0')}:${String(s).padStart(2,'0')}`;
  document.getElementById('progress').style.width = ((S.elapsed / TOTAL_SECONDS) * 100) + '%';

  const phase = phases[S.phaseIndex];
  if (S.phaseElapsed >= phase.duration) {
    S.phaseIndex++;
    S.phaseElapsed = 0;
    S.lastLineIndex = -1;
    S.lastSpokenIndex = -1;
    stopSpeech();
    if (S.phaseIndex >= phases.length) { endMeditation(); return; }
    updatePhaseUI(S.phaseIndex);
    playBell('phase');
    clearInterval(S.breathInterval);
    startBreathCycle();
  }

  checkScriptLines();
}

function checkScriptLines() {
  const lines = phases[S.phaseIndex].lines;
  for (let i = lines.length - 1; i >= 0; i--) {
    if (S.phaseElapsed >= lines[i].t) {
      if (i !== S.lastLineIndex) {
        S.lastLineIndex = i;
        const text = lines[i].text;
        showLine(text);
        if (text && i !== S.lastSpokenIndex) {
          S.lastSpokenIndex = i;
          // Small delay so visual and audio sync
          setTimeout(() => {
            if (S.running && !S.paused) speak(text);
          }, 800);
        }
      }
      break;
    }
  }
}

function showLine(text) {
  const el = document.getElementById('script-text');
  el.classList.remove('visible');
  setTimeout(() => {
    el.innerHTML = text || '&nbsp;';
    el.classList.add('visible');
  }, 500);
}

// ── PHASE UI ──────────────────────────────────────────────
function updatePhaseUI(idx) {
  document.getElementById('phase-label').textContent = phases[idx].name;
  document.getElementById('phase-title-display').textContent = phases[idx].label;
  phases.forEach((_, i) => {
    const d = document.getElementById(`dot-${i}`);
    if (d) d.className = 'dot' + (i < idx ? ' done' : i === idx ? ' active' : '');
  });
}

// ── BREATH CYCLE ──────────────────────────────────────────
function startBreathCycle() {
  if (!phases[S.phaseIndex]) return;
  const cycle = phases[S.phaseIndex].breathCycle;

  function runCycle() {
    if (!S.running || S.paused) return;
    const inhaleTime = cycle * 0.4;
    const holdTime   = 1.2;
    const exhaleTime = cycle - inhaleTime - holdTime;

    // Inhale
    setBreathVisual('inhale', 'Inhale');
    playBreathSound('inhale');

    setTimeout(() => {
      if (!S.running || S.paused) return;
      setBreathVisual('hold', 'Hold');
    }, inhaleTime * 1000);

    setTimeout(() => {
      if (!S.running || S.paused) return;
      setBreathVisual('exhale', 'Exhale');
      playBreathSound('exhale');
    }, (inhaleTime + holdTime) * 1000);
  }

  runCycle();
  S.breathInterval = setInterval(runCycle, cycle * 1000);
}

function setBreathVisual(type, word) {
  const core = document.getElementById('core');
  const r1 = document.getElementById('ring1');
  const r2 = document.getElementById('ring2');
  const r3 = document.getElementById('ring3');
  const wordEl = document.getElementById('breath-word');

  [core, r1, r2, r3].forEach(el => el.classList.toggle('inhale', type === 'inhale'));
  wordEl.style.opacity = type === 'hold' ? '0.4' : '0.7';
  wordEl.textContent = word;
}

// ── PAUSE ─────────────────────────────────────────────────
function togglePause() {
  if (S.paused) resumeMeditation(); else pauseMeditation();
}

function pauseMeditation() {
  S.paused = true;
  stopSpeech();
  if (audioCtx) audioCtx.suspend();
  document.getElementById('pause-overlay').classList.add('visible');
  document.getElementById('pause-btn').textContent = '▶';
}

function resumeMeditation() {
  S.paused = false;
  if (audioCtx) audioCtx.resume();
  document.getElementById('pause-overlay').classList.remove('visible');
  document.getElementById('pause-btn').textContent = '⏸';
  document.getElementById('pause-btn').onclick = togglePause;
}

// ── END ───────────────────────────────────────────────────
function endMeditation() {
  S.running = false;
  clearInterval(S.interval);
  clearInterval(S.breathInterval);
  stopSpeech();
  playBell('phase');
  setTimeout(() => playBell('phase'), 3000);

  document.getElementById('pause-btn').classList.remove('show');
  document.getElementById('meditation').classList.remove('active');

  setTimeout(() => {
    document.getElementById('ending').classList.add('active');
    setTimeout(() => {
      speak("Namaste.", () => {});
      ['et1','et2','et3','et4'].forEach((id, i) => {
        const el = document.getElementById(id);
        el.classList.add('show');
        el.classList.add(['d1','d2','d3','d4'][i]);
      });
    }, 600);
  }, 800);
}

function restartMeditation() {
  stopSpeech();
  clearInterval(S.interval);
  clearInterval(S.breathInterval);
  if (audioCtx) { audioCtx.close(); audioCtx = null; }

  ['et1','et2','et3','et4'].forEach(id => {
    const el = document.getElementById(id);
    el.classList.remove('show','d1','d2','d3','d4');
  });
  document.getElementById('ending').classList.remove('active');
  setBreathVisual('exhale', '');
  document.getElementById('script-text').classList.remove('visible');
  document.getElementById('progress').style.width = '0%';
  document.getElementById('timer').textContent = '15:00';

  Object.assign(S, { running:false, paused:false, elapsed:0, phaseIndex:0, phaseElapsed:0, lastLineIndex:-1, lastSpokenIndex:-1 });

  setTimeout(() => document.getElementById('landing').classList.add('active'), 400);
}
</script>

</body>
</html>