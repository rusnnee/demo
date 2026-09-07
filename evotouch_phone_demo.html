<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
<title>evoTouch — Phone Demo</title>
<style>
:root {
  --bg:        #f4ece5;
  --surface:   #ffffff;
  --surface-2: #f0e5da;
  --border:    #ddd0c4;
  --border-strong: #c4b0a0;

  --brown-900: #2e1e16;
  --brown-700: #5c3828;
  --brown-500: #9a6040;
  --brown-300: #c89070;

  --teal:      #28a0b0;
  --teal-dark: #1a7888;
  --teal-light:#50c8c0;

  --skin:      #e8c890;

  --liver-col: #a83828;
  --liver-glow:#d45040;
  --spleen-col:#6040a0;
  --spleen-glow:#8060c8;

  --green:  #2a9060;
  --amber:  #b87820;

  --text:        #2e1e16;
  --text-muted:  #7a5840;
  --text-subtle: #a89080;
}

* { box-sizing: border-box; margin: 0; padding: 0; }

html, body {
  height: 100%;
  overflow: hidden;
  background: #14100d;
  font-family: 'Segoe UI', system-ui, sans-serif;
  color: var(--text);
}

body {
  display: flex;
  align-items: center;
  justify-content: center;
}

/* ── PHONE FRAME ──
   Fixed 2:1 aspect ratio regardless of the actual browser/viewport shape --
   width:min(100vw,200vh) + aspect-ratio always fits inside the viewport
   while keeping the exact ratio (the real device is 13cm x 6.5cm, but cm
   can't be guaranteed to map 1:1 across screens, so the RATIO is what's
   actually enforced here, scaled to fill whatever viewport this loads in). */
#phone {
  width: min(100vw, 200vh);
  aspect-ratio: 2 / 1;
  max-width: 100vw;
  max-height: 100vh;
  background: var(--bg);
  display: flex;
  overflow: hidden;
  box-shadow: 0 0 50px #0009;
}

/* Reserved strip for the phone's notch/camera cutout in landscape -- a
   visible border PLUS the real safe-area inset (env()) stacked together,
   so this both reads as a deliberate design margin in the demo and
   actually keeps content clear of a real notch if opened on one. */
#notch-border {
  width: calc(26px + env(safe-area-inset-left, 0px));
  flex-shrink: 0;
  background: var(--brown-900);
}

/* ── LEFT PANEL (now the only panel -- fills the whole frame) ── */
#left {
  flex: 1;
  background: var(--surface);
  display: flex;
  flex-direction: column;
  padding: 2.4% 4%;
  gap: 2.2%;
  overflow: hidden;
}

/* ── Inline status row: System / Liver / Spleen side by side ── */
#status-row {
  display: flex;
  justify-content: space-between;
  gap: 6px;
}
.status-chip {
  flex: 1;
  display: flex;
  align-items: center;
  gap: 5px;
  min-width: 0;
}
.status-chip .led {
  width: 8px; height: 8px; border-radius: 50%; flex-shrink: 0;
  background: #ddd; transition: background .3s, box-shadow .3s;
}
.status-chip .led.off      { background: #d0c8c0; }
.status-chip .led.ready    { background: var(--green); box-shadow: 0 0 5px var(--green); }
.status-chip .led.playing  { background: var(--teal);  box-shadow: 0 0 5px var(--teal); animation: led-flash-1hz 1s step-end infinite; }
@keyframes led-flash-1hz { 0%,49%{opacity:1} 50%,100%{opacity:.15} }
.status-chip .chip-text { display: flex; flex-direction: column; gap: 1px; min-width: 0; }
.status-chip .chip-label { font-size: 8px; font-weight: 700; text-transform: uppercase; letter-spacing: .06em; color: var(--text-subtle); }
.status-chip .chip-value { font-size: 9.5px; font-weight: 600; color: var(--text-muted); white-space: nowrap; overflow: hidden; text-overflow: ellipsis; }
.status-chip.liver  .chip-label { color: var(--liver-col); }
.status-chip.spleen .chip-label { color: var(--spleen-col); }

/* ── BREATHING VISUAL (the main focal point now the silhouette is gone) ──
   A big pulsing circle + large phase label, plus the linear bar underneath
   as a secondary, precise readout. The circle is the "distinct" cue --
   scale/glow/opacity all track frac directly, so it's obviously breathing
   even at a glance, not just a thin bar changing width. */
/* width:100% is load-bearing here: #breathing-col has align-items:center,
   which sizes children to shrink-to-fit content by default. Without an
   explicit width, #breath-visual's own box would shrink/grow to match
   whatever its widest child currently needs -- and since the phase label's
   text length changes ("Breathing Out" vs "Fully Breathed Out" vs "Fully
   Breathed In" are all different widths), #breath-circle-wrap's 50% below
   was actually 50% of a MOVING TARGET, not a stable base. That's what was
   really causing the circle to visibly resize at the breath extremes (a
   layout-width jump, not anything wrong with the scale() animation itself
   -- confirmed by sampling getBoundingClientRect() live: the wrap's actual
   rendered width changed by ~30px exactly when the label text changed,
   while the scale() value barely moved). Pinning this to 100% makes
   #breath-circle-wrap's 50% a stable fraction of #breathing-col's fixed
   width instead, so the label can never affect the circle's size again. */
#breath-visual {
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 2%;
  flex: 1;
  min-height: 0;
}
#breath-circle-wrap {
  position: relative;
  width: 50%;
  aspect-ratio: 1;
  flex-shrink: 0;
  display: flex;
  align-items: center;
  justify-content: center;
}
#breath-circle-ring {
  position: absolute; inset: 0;
  border-radius: 50%;
  border: 2px dashed var(--border-strong);
}
/* No CSS transition on transform/box-shadow here -- they're already being
   set every animation frame from JS (see updateBreathCircle()), computing
   a continuous, already-eased curve. Layering a second, independent CSS
   transition on top of per-frame updates fights that curve (each new frame
   restarts a transition toward a target the previous one hadn't reached
   yet), which is exactly what read as "jumping between sizes" -- removing
   it lets the JS-computed values alone drive the motion, smoothly. */
#breath-circle {
  width: 60%; height: 60%;
  border-radius: 50%;
  background: radial-gradient(circle at 40% 35%, var(--teal-light), var(--teal) 70%, var(--teal-dark));
  box-shadow: 0 0 14px 2px #28a0b055;
}
/* Reserves space for its OWN worst case (2 lines, for the longer "Fully
   Breathed In/Out" text) at all times, even while showing shorter 1-line
   text like "Breathing In" -- otherwise the label's box height changes the
   instant the text switches (right at each breath extreme), which reflows
   the flex layout around it and makes the circle itself appear to jump in
   size/position exactly at those moments. Fixed height + centered content
   means the text can change without ever moving anything else. */
#breath-phase-label {
  font-size: 20px;
  line-height: 1.25;
  min-height: 2.5em;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: 800;
  letter-spacing: .04em;
  text-transform: uppercase;
  color: var(--teal-dark);
  text-align: center;
  transition: color .15s;
}

#breathing-wrap { width: 100%; display: flex; flex-direction: column; gap: 4px; }
#breathing-label { font-size: 13px; font-weight: 700; text-transform: uppercase; letter-spacing: .08em; color: var(--teal-dark); }
#breathing-bar-track {
  height: 10px; background: var(--border); border-radius: 5px; overflow: hidden;
}
#breathing-bar-fill {
  height: 100%; width: 0%;
  background: linear-gradient(90deg, var(--teal-light), var(--teal));
  border-radius: 5px;
  transition: width .05s linear;
}

/* ── Two-column split: controls on one side, breathing visual on the
   other (see #main-row below the status row). ── */
#main-row {
  display: flex;
  flex: 1;
  min-height: 0;
  gap: 4%;
}
#controls-col {
  width: 42%;
  flex-shrink: 0;
  display: flex;
  flex-direction: column;
  justify-content: center;
  gap: 6%;
}
#breathing-col {
  width: 58%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 5%;
}

/* ── Organ length sliders (settable range + auto-moving live marker) ──
   Stacked (not side by side) now that they live in the narrower
   controls column. */
.organ-len-row { display: flex; flex-direction: column; gap: 12%; }
.organ-len { display: flex; flex-direction: column; gap: 4px; }
.organ-len-header { display: flex; justify-content: space-between; align-items: baseline; }
.organ-len-name { font-size: 14px; font-weight: 700; text-transform: uppercase; letter-spacing: .06em; }
.organ-len-name.liver  { color: var(--liver-col); }
.organ-len-name.spleen { color: var(--spleen-col); }
.organ-len-val { font-size: 14px; color: var(--text-subtle); }

.slider-track-wrap { position: relative; height: 18px; }
input[type=range] {
  -webkit-appearance: none; width: 100%; height: 4px; margin-top: 7px;
  background: var(--border); border-radius: 2px; outline: none; cursor: pointer;
}
input[type=range]::-webkit-slider-thumb {
  -webkit-appearance: none; width: 15px; height: 15px; border-radius: 50%;
  border: 2px solid #fff; box-shadow: 0 1px 3px #0003; cursor: pointer;
}
#liver-len::-webkit-slider-thumb  { background: var(--liver-col); }
#spleen-len::-webkit-slider-thumb { background: var(--spleen-col); }

/* The live "breathing position" marker -- purely visual, moves on its own
   between 0 and the slider's current value while Play/Voice is active.
   Sits UNDER the real thumb on the same track so dragging the slider still
   works normally at any time. */
.pos-marker {
  position: absolute; top: 7px; left: 0%;
  width: 9px; height: 9px; border-radius: 50%;
  transform: translate(-50%, -2.5px);
  pointer-events: none;
  opacity: 0;
  transition: opacity .2s;
}
.pos-marker.active { opacity: .8; }
.pos-marker.liver  { background: var(--liver-glow);  box-shadow: 0 0 6px var(--liver-glow); }
.pos-marker.spleen { background: var(--spleen-glow); box-shadow: 0 0 6px var(--spleen-glow); }

/* ── Buttons ── */
#btn-row { display: flex; flex-direction: column; gap: 6px; }
button {
  font-family: inherit; border: none; cursor: pointer; border-radius: 6px;
  transition: all .15s; line-height: 1;
}
#play-btn {
  width: 100%; padding: 10px; font-size: 17px; font-weight: 700;
  background: var(--teal); color: #fff; letter-spacing: .02em;
}
#play-btn:hover { background: var(--teal-dark); }
#play-btn.playing { background: var(--brown-700); }
#play-btn.playing:hover { background: var(--brown-900); }

#voice-btn {
  width: 100%; padding: 9px; font-size: 15px; font-weight: 600;
  background: var(--surface-2); color: var(--brown-500);
  border: 1px solid var(--border-strong);
}
#voice-btn:hover { border-color: var(--brown-500); color: var(--brown-700); }
#voice-btn.active { background: var(--teal); color: #fff; border-color: var(--teal); }
#voice-btn.active:hover { background: var(--teal-dark); }
</style>
</head>
<body>

<div id="phone">
  <div id="notch-border"></div>

  <!-- Single panel now -- status row, the big breathing visual, organ
       length sliders, controls. No device connection, no silhouette. -->
  <div id="left">

    <div id="status-row">
      <div class="status-chip">
        <div class="led ready" id="led-sys"></div>
        <div class="chip-text">
          <span class="chip-label">System</span>
          <span class="chip-value" id="txt-sys">Ready</span>
        </div>
      </div>
      <div class="status-chip liver">
        <div class="led ready" id="led-liver"></div>
        <div class="chip-text">
          <span class="chip-label">Liver</span>
          <span class="chip-value" id="txt-liver">Ready</span>
        </div>
      </div>
      <div class="status-chip spleen">
        <div class="led ready" id="led-spleen"></div>
        <div class="chip-text">
          <span class="chip-label">Spleen</span>
          <span class="chip-value" id="txt-spleen">Ready</span>
        </div>
      </div>
    </div>

    <!-- Two columns: controls on one side, the breathing visual isolated
         on the other -- see #main-row/#controls-col/#breathing-col. -->
    <div id="main-row">

      <div id="controls-col">
        <div class="organ-len-row">
          <div class="organ-len">
            <div class="organ-len-header">
              <span class="organ-len-name liver">Liver length</span>
              <span class="organ-len-val" id="liver-len-val">3.0 cm</span>
            </div>
            <div class="slider-track-wrap">
              <input type="range" id="liver-len" min="0" max="5" step="0.1" value="3">
              <div class="pos-marker liver" id="liver-pos-marker"></div>
            </div>
          </div>

          <div class="organ-len">
            <div class="organ-len-header">
              <span class="organ-len-name spleen">Spleen length</span>
              <span class="organ-len-val" id="spleen-len-val">3.0 cm</span>
            </div>
            <div class="slider-track-wrap">
              <input type="range" id="spleen-len" min="0" max="5" step="0.1" value="3">
              <div class="pos-marker spleen" id="spleen-pos-marker"></div>
            </div>
          </div>
        </div>

        <div id="btn-row">
          <button id="play-btn">Play</button>
          <button id="voice-btn">Voice Control: Off</button>
        </div>
      </div><!-- /controls-col -->

      <div id="breathing-col">
        <!-- Big pulsing circle + large phase label -- the focal point. -->
        <div id="breath-visual">
          <div id="breath-circle-wrap">
            <div id="breath-circle-ring"></div>
            <div id="breath-circle"></div>
          </div>
          <div id="breath-phase-label">Ready</div>
        </div>

        <div id="breathing-wrap">
          <span id="breathing-label">Breathing</span>
          <div id="breathing-bar-track"><div id="breathing-bar-fill"></div></div>
        </div>
      </div><!-- /breathing-col -->

    </div><!-- /main-row -->

  </div><!-- /left -->
</div><!-- /phone -->

<script>
// ─── STATE ───────────────────────────────────────────────────────────────
// UI-only demo: no device, no Web Serial, no real firmware. Everything
// below is a local visual simulation driven by requestAnimationFrame.
const CYCLE_MS = 4000; // one full in+out breath cycle -- ~15 breaths/min, matching the app's usual default BPM

let playing = false;
let voiceOn = false;
let rafId = null;
let cycleStartMs = null;

// ─── ELEMENTS ────────────────────────────────────────────────────────────
const playBtn   = document.getElementById('play-btn');
const voiceBtn  = document.getElementById('voice-btn');
const liverLenSlider   = document.getElementById('liver-len');
const spleenLenSlider  = document.getElementById('spleen-len');
const liverLenVal      = document.getElementById('liver-len-val');
const spleenLenVal     = document.getElementById('spleen-len-val');
const liverPosMarker   = document.getElementById('liver-pos-marker');
const spleenPosMarker  = document.getElementById('spleen-pos-marker');
const breathingBarFill = document.getElementById('breathing-bar-fill');
const breathCircle     = document.getElementById('breath-circle');
const breathPhaseLabel = document.getElementById('breath-phase-label');

// ─── STATUS HELPERS ──────────────────────────────────────────────────────
function setLed(id, cls) { document.getElementById(id).className = 'led ' + cls; }
function setTxt(id, txt) { document.getElementById(id).textContent = txt; }

// ─── SLIDER LABEL SYNC ───────────────────────────────────────────────────
liverLenSlider.addEventListener('input', () => {
  liverLenVal.textContent = parseFloat(liverLenSlider.value).toFixed(1) + ' cm';
});
spleenLenSlider.addEventListener('input', () => {
  spleenLenVal.textContent = parseFloat(spleenLenSlider.value).toFixed(1) + ' cm';
});

// ─── BREATHING SIMULATION ────────────────────────────────────────────────
// frac: 0 = fully breathed out, 1 = fully breathed in, sinusoidal in between
// (1 - cos) so it starts and ends each half at zero velocity, same "natural"
// ease the real coordinated moves aim for -- no linear/robotic snap.
function breathFraction(nowMs) {
  if (cycleStartMs === null) cycleStartMs = nowMs;
  const t = (nowMs - cycleStartMs) % CYCLE_MS;
  const phase = t / CYCLE_MS; // 0..1 across one full cycle
  const frac = (1 - Math.cos(phase * 2 * Math.PI)) / 2;
  const inhaling = phase < 0.5;
  return { frac, inhaling };
}

function updatePosMarker(markerEl, sliderEl, frac) {
  const min = parseFloat(sliderEl.min), max = parseFloat(sliderEl.max);
  const len = parseFloat(sliderEl.value); // current length setting -- can be dragged live while playing
  const posCm = frac * len; // 0..len, moving on its own between HOME and the set length
  const span = (max - min) || 1;
  markerEl.style.left = (((posCm - min) / span) * 100) + '%';
}

// The big circle is the main "make it obviously breathing" cue -- a wide
// size swing (not a subtle one) plus a glow that brightens noticeably at
// full inhale, so the state reads at a glance rather than needing the
// small bar/label to be read closely.
function updateBreathCircle(frac) {
  const scale = 0.55 + frac * 0.65; // 0.55 at fully out -> 1.20 at fully in
  const glowSize   = 10 + frac * 34;
  const glowSpread = 1 + frac * 5;
  const glowAlpha  = 0.35 + frac * 0.45;
  breathCircle.style.transform  = `scale(${scale.toFixed(3)})`;
  breathCircle.style.boxShadow  = `0 0 ${glowSize.toFixed(0)}px ${glowSpread.toFixed(0)}px rgba(40,160,176,${glowAlpha.toFixed(2)})`;
}

// Four distinct phases (not just two) -- a brief, clearly-labeled "Fully..."
// moment at each end of the cycle, matching the real device panel's own
// breathing-stage concept, instead of only ever saying "in"/"out".
function phaseLabel(frac, inhaling) {
  if (frac >= 0.97) return 'Fully Breathed In';
  if (frac <= 0.03) return 'Fully Breathed Out';
  return inhaling ? 'Breathing In' : 'Breathing Out';
}

function tick(nowMs) {
  if (!playing && !voiceOn) { rafId = null; return; }

  const { frac, inhaling } = breathFraction(nowMs);

  breathingBarFill.style.width = (frac * 100).toFixed(1) + '%';
  updatePosMarker(liverPosMarker, liverLenSlider, frac);
  updatePosMarker(spleenPosMarker, spleenLenSlider, frac);
  updateBreathCircle(frac);

  const label = phaseLabel(frac, inhaling);
  breathPhaseLabel.textContent = label;
  setLed('led-liver', 'playing');  setTxt('txt-liver',  label);
  setLed('led-spleen', 'playing'); setTxt('txt-spleen', label);

  rafId = requestAnimationFrame(tick);
}

function startBreathing() {
  cycleStartMs = null; // always start a fresh cycle from "fully breathed out"
  liverPosMarker.classList.add('active');
  spleenPosMarker.classList.add('active');
  if (!rafId) rafId = requestAnimationFrame(tick);
}

function stopBreathing() {
  if (rafId) cancelAnimationFrame(rafId);
  rafId = null;
  breathingBarFill.style.width = '0%';
  liverPosMarker.classList.remove('active');
  spleenPosMarker.classList.remove('active');
  liverPosMarker.style.left = '0%';
  spleenPosMarker.style.left = '0%';
  updateBreathCircle(0);
  breathPhaseLabel.textContent = 'Ready';
  setLed('led-sys', 'ready');    setTxt('txt-sys', 'Ready');
  setLed('led-liver', 'ready');  setTxt('txt-liver', 'Ready');
  setLed('led-spleen', 'ready'); setTxt('txt-spleen', 'Ready');
}

// ─── CONTROLS ────────────────────────────────────────────────────────────
// Play and Voice Control are mutually exclusive, same convention as the
// full desktop panel -- pressing one always wins and takes over.
playBtn.addEventListener('click', () => {
  if (playing) {
    playing = false;
    playBtn.textContent = 'Play';
    playBtn.classList.remove('playing');
    stopBreathing();
    return;
  }
  playing = true;
  voiceOn = false;
  playBtn.textContent = 'Pause';
  playBtn.classList.add('playing');
  voiceBtn.textContent = 'Voice Control: Off';
  voiceBtn.classList.remove('active');
  setLed('led-sys', 'playing'); setTxt('txt-sys', 'Playing');
  startBreathing();
});

voiceBtn.addEventListener('click', () => {
  if (voiceOn) {
    voiceOn = false;
    voiceBtn.textContent = 'Voice Control: Off';
    voiceBtn.classList.remove('active');
    stopBreathing();
    return;
  }
  voiceOn = true;
  playing = false;
  voiceBtn.textContent = 'Voice Control: On';
  voiceBtn.classList.add('active');
  playBtn.textContent = 'Play';
  playBtn.classList.remove('playing');
  setLed('led-sys', 'playing'); setTxt('txt-sys', 'Voice Control On');
  startBreathing();
});
</script>
</body>
</html>
