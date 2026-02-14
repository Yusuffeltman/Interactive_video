
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Interactive Learning Video</title>
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@300;400;500;600;700&family=DM+Mono:wght@400;500&display=swap" rel="stylesheet"/>
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
  :root {
    --bg:       #0d1117;
    --surface:  #161b22;
    --surface2: #1f2733;
    --border:   #2d3748;
    --teal:     #0ed2c8;
    --teal-dim: rgba(14,210,200,0.12);
    --teal-glow:rgba(14,210,200,0.35);
    --amber:    #f6ad3c;
    --green:    #3de07a;
    --red:      #f05252;
    --text:     #e6edf3;
    --muted:    #7d8fa3;
    --radius:   12px;
  }
  html,body { height:100%; background:var(--bg); color:var(--text); font-family:'DM Sans',sans-serif; font-size:15px; line-height:1.6; -webkit-font-smoothing:antialiased; }
  .app { min-height:100vh; display:flex; flex-direction:column; }

  /* HEADER */
  .header { background:var(--surface); border-bottom:1px solid var(--border); padding:14px 28px; display:flex; align-items:center; gap:14px; flex-shrink:0; }
  .header-icon { width:36px; height:36px; border-radius:8px; background:var(--teal-dim); border:1px solid var(--teal-glow); display:grid; place-items:center; flex-shrink:0; }
  .header-icon svg { color:var(--teal); }
  .header-title { font-size:16px; font-weight:600; }
  .header-meta  { font-size:12px; color:var(--muted); margin-top:1px; }
  .header-score { margin-left:auto; background:var(--teal-dim); border:1px solid var(--teal-glow); border-radius:20px; padding:4px 14px; font-size:13px; font-weight:600; color:var(--teal); font-family:'DM Mono',monospace; display:flex; align-items:center; gap:6px; opacity:0; transition:opacity .4s; }
  .header-score.visible { opacity:1; }

  /* MAIN GRID */
  .main { flex:1; display:grid; grid-template-columns:1fr 300px; min-height:0; }
  .video-section { display:flex; flex-direction:column; padding:20px 20px 20px 24px; gap:14px; min-width:0; }

  /* 16:9 VIDEO WRAPPER — padding-top trick, children fill absolutely */
  .video-wrapper { position:relative; width:100%; padding-top:56.25%; background:#000; border-radius:var(--radius); border:1px solid var(--border); overflow:hidden; flex-shrink:0; }
  .video-wrapper > * { position:absolute; top:0; left:0; width:100%; height:100%; border:none; }

  /* The iframe */
  #yt-frame { z-index:1; }

  /* Click shield — stops user interacting with iframe while quiz is open */
  #click-shield { z-index:3; background:rgba(0,0,0,0.68); display:flex; flex-direction:column; align-items:center; justify-content:center; gap:10px; opacity:0; pointer-events:none; transition:opacity .3s; }
  #click-shield.active { opacity:1; pointer-events:all; }
  #click-shield span { font-size:13px; color:var(--muted); font-weight:500; }

  /* Intro overlay — first-load state */
  #intro-overlay { z-index:4; background:rgba(13,17,23,0.92); display:flex; flex-direction:column; align-items:center; justify-content:center; gap:14px; }
  #intro-overlay.gone { display:none; }
  .intro-play-btn { background:var(--teal); color:#0d1117; border:none; border-radius:50%; width:64px; height:64px; display:grid; place-items:center; cursor:pointer; box-shadow:0 0 32px var(--teal-glow); transition:transform .2s, box-shadow .2s; }
  .intro-play-btn:hover { transform:scale(1.1); box-shadow:0 0 48px var(--teal-glow); }
  .intro-label { font-size:13px; color:var(--muted); }

  /* PROGRESS */
  .progress-area { display:flex; flex-direction:column; gap:8px; flex-shrink:0; }
  .progress-header { display:flex; justify-content:space-between; font-size:12px; color:var(--muted); }
  .timeline { position:relative; height:6px; background:var(--surface2); border-radius:10px; overflow:visible; }
  .timeline-fill { height:100%; width:0%; background:linear-gradient(90deg,var(--teal),#06b6d4); border-radius:10px; transition:width .5s linear; }
  .marker { position:absolute; top:50%; transform:translate(-50%,-50%); width:14px; height:14px; border-radius:50%; border:2px solid var(--bg); cursor:default; transition:transform .2s,box-shadow .2s; z-index:2; }
  .marker:hover { transform:translate(-50%,-50%) scale(1.5); }
  .marker.pending   { background:var(--amber); box-shadow:0 0 8px rgba(246,173,60,.5); }
  .marker.correct   { background:var(--green); box-shadow:0 0 8px rgba(61,224,122,.4); }
  .marker.wrong     { background:var(--red);   box-shadow:0 0 8px rgba(240,82,82,.4); }

  /* SIDEBAR */
  .side-panel { border-left:1px solid var(--border); background:var(--surface); display:flex; flex-direction:column; overflow-y:auto; padding:20px 16px; gap:8px; }
  .panel-heading { font-size:11px; font-weight:700; letter-spacing:1.2px; text-transform:uppercase; color:var(--muted); margin-bottom:4px; flex-shrink:0; }
  .q-item { background:var(--surface2); border-radius:8px; padding:12px; border:1px solid transparent; transition:border-color .2s; flex-shrink:0; }
  .q-item.active  { border-color:var(--teal); }
  .q-item.correct { border-color:var(--green); }
  .q-item.wrong   { border-color:var(--red); }
  .q-item-top { display:flex; align-items:flex-start; gap:8px; margin-bottom:4px; }
  .q-badge { width:20px; height:20px; border-radius:50%; display:grid; place-items:center; font-size:10px; font-weight:700; flex-shrink:0; margin-top:1px; }
  .q-badge.pending  { background:var(--surface); border:1px solid var(--border); color:var(--muted); }
  .q-badge.correct  { background:rgba(61,224,122,.15); color:var(--green); }
  .q-badge.wrong    { background:rgba(240,82,82,.15); color:var(--red); }
  .q-text { font-size:13px; font-weight:500; line-height:1.4; }
  .q-time { font-size:11px; color:var(--muted); font-family:'DM Mono',monospace; }

  /* QUIZ MODAL */
  .quiz-overlay { position:fixed; inset:0; background:rgba(0,0,0,0.65); display:flex; align-items:center; justify-content:center; z-index:100; padding:20px; opacity:0; pointer-events:none; transition:opacity .35s; }
  .quiz-overlay.active { opacity:1; pointer-events:all; }
  .quiz-card { background:var(--surface); border:1px solid var(--border); border-radius:16px; padding:32px; max-width:540px; width:100%; box-shadow:0 24px 64px rgba(0,0,0,.6); transform:translateY(16px) scale(.97); transition:transform .35s cubic-bezier(.2,.8,.4,1); }
  .quiz-overlay.active .quiz-card { transform:translateY(0) scale(1); }
  .quiz-top { display:flex; align-items:center; gap:10px; margin-bottom:20px; }
  .quiz-tag { background:var(--teal-dim); border:1px solid var(--teal-glow); color:var(--teal); border-radius:20px; padding:3px 12px; font-size:11px; font-weight:700; letter-spacing:.8px; text-transform:uppercase; }
  .quiz-num { font-size:12px; color:var(--muted); margin-left:auto; font-family:'DM Mono',monospace; }
  .quiz-question { font-size:17px; font-weight:600; line-height:1.5; margin-bottom:22px; }

  .options { display:flex; flex-direction:column; gap:10px; margin-bottom:22px; }
  .option { background:var(--surface2); border:1px solid var(--border); border-radius:10px; padding:13px 16px; cursor:pointer; font-size:14px; font-weight:500; display:flex; align-items:center; gap:12px; transition:border-color .2s,background .2s,transform .15s; user-select:none; }
  .option:hover:not(.disabled) { border-color:var(--teal); background:var(--teal-dim); transform:translateX(3px); }
  .option.selected { border-color:var(--teal); background:var(--teal-dim); }
  .option.correct  { border-color:var(--green); background:rgba(61,224,122,.08); }
  .option.wrong    { border-color:var(--red); background:rgba(240,82,82,.08); }
  .option.disabled { cursor:default; }
  .option-letter { width:26px; height:26px; border-radius:6px; background:var(--surface); border:1px solid var(--border); display:grid; place-items:center; font-size:11px; font-weight:700; flex-shrink:0; font-family:'DM Mono',monospace; transition:background .2s,border-color .2s; }
  .option.correct  .option-letter { background:rgba(61,224,122,.2); border-color:var(--green); color:var(--green); }
  .option.wrong    .option-letter { background:rgba(240,82,82,.2); border-color:var(--red); color:var(--red); }
  .option.selected .option-letter { background:var(--teal-dim); border-color:var(--teal); color:var(--teal); }

  .feedback-box { border-radius:10px; padding:14px; font-size:13px; line-height:1.6; display:none; margin-bottom:18px; gap:10px; align-items:flex-start; }
  .feedback-box.show      { display:flex; }
  .feedback-box.correct-fb{ background:rgba(61,224,122,.08); border:1px solid rgba(61,224,122,.25); }
  .feedback-box.wrong-fb  { background:rgba(240,82,82,.08); border:1px solid rgba(240,82,82,.25); }
  .fb-icon  { flex-shrink:0; margin-top:2px; }
  .fb-title { font-weight:700; margin-bottom:2px; }
  .fb-title.green { color:var(--green); }
  .fb-title.red   { color:var(--red); }
  .fb-body  { color:var(--muted); }

  .btn { border:none; border-radius:10px; padding:12px 24px; font-family:'DM Sans',sans-serif; font-weight:600; font-size:14px; cursor:pointer; transition:transform .15s,box-shadow .2s; display:inline-flex; align-items:center; gap:8px; }
  .btn:active { transform:scale(.97); }
  .btn-primary { background:var(--teal); color:#0d1117; box-shadow:0 4px 16px var(--teal-glow); }
  .btn-primary:hover { box-shadow:0 6px 24px var(--teal-glow); }
  .btn-ghost { background:var(--surface2); border:1px solid var(--border); color:var(--text); }
  .btn-ghost:hover { border-color:var(--teal); }
  .btn-row { display:flex; gap:10px; flex-wrap:wrap; }
  .btn[disabled] { opacity:.4; cursor:not-allowed; pointer-events:none; }

  /* RESULTS */
  .results-overlay { position:fixed; inset:0; background:rgba(0,0,0,.75); display:flex; align-items:center; justify-content:center; z-index:200; padding:20px; opacity:0; pointer-events:none; transition:opacity .4s; }
  .results-overlay.active { opacity:1; pointer-events:all; }
  .results-card { background:var(--surface); border:1px solid var(--border); border-radius:20px; padding:40px; max-width:480px; width:100%; box-shadow:0 32px 80px rgba(0,0,0,.7); text-align:center; }
  .results-icon { width:72px; height:72px; border-radius:50%; display:grid; place-items:center; margin:0 auto 20px; font-size:32px; }
  .results-icon.great { background:rgba(61,224,122,.12); border:2px solid rgba(61,224,122,.3); }
  .results-icon.good  { background:rgba(246,173,60,.12); border:2px solid rgba(246,173,60,.3); }
  .results-icon.try   { background:rgba(240,82,82,.1); border:2px solid rgba(240,82,82,.2); }
  .results-score { font-size:48px; font-weight:700; font-family:'DM Mono',monospace; letter-spacing:-2px; margin-bottom:4px; }
  .results-score.great { color:var(--green); }
  .results-score.good  { color:var(--amber); }
  .results-score.try   { color:var(--red); }
  .results-label { font-size:14px; color:var(--muted); margin-bottom:28px; }
  .results-breakdown { background:var(--surface2); border-radius:12px; padding:18px; margin-bottom:24px; display:flex; justify-content:space-around; }
  .rb-item { text-align:center; }
  .rb-num  { font-size:24px; font-weight:700; font-family:'DM Mono',monospace; }
  .rb-lbl  { font-size:11px; color:var(--muted); text-transform:uppercase; letter-spacing:.8px; margin-top:2px; }

  @media(max-width:760px) {
    .main { grid-template-columns:1fr; }
    .side-panel { border-left:none; border-top:1px solid var(--border); max-height:200px; }
    .quiz-card { padding:20px; }
  }
</style>
</head>
<body>
<div class="app">

  <!-- HEADER -->
  <header class="header">
    <div class="header-icon">
      <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polygon points="5 3 19 12 5 21 5 3"/></svg>
    </div>
    <div>
      <div class="header-title" id="unit-title">Interactive Learning Video</div>
      <div class="header-meta"  id="unit-meta">Loading…</div>
    </div>
    <div class="header-score" id="header-score">
      <svg width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><polyline points="20 6 9 17 4 12"/></svg>
      <span id="score-text">0 / 0</span>
    </div>
  </header>

  <!-- MAIN -->
  <div class="main">
    <div class="video-section">

      <!-- 16:9 responsive video wrapper -->
      <div class="video-wrapper">

        <!-- Intro overlay: click to acknowledge and start (so we know when timing begins) -->
        <div id="intro-overlay">
          <button class="intro-play-btn" onclick="startVideo()">
            <svg width="26" height="26" viewBox="0 0 24 24" fill="currentColor"><polygon points="5 3 19 12 5 21"/></svg>
          </button>
          <span class="intro-label">Click to start the interactive lesson</span>
        </div>

        <!-- YouTube embedded via plain iframe — no external API script needed -->
        <iframe
          id="yt-frame"
          src=""
          allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
          allowfullscreen>
        </iframe>

        <!-- Darkens & blocks the iframe while quiz is active -->
        <div id="click-shield">
          <svg width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="var(--teal)" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
            <rect x="3" y="11" width="18" height="11" rx="2" ry="2"/><path d="M7 11V7a5 5 0 0 1 10 0v4"/>
          </svg>
          <span>Answer the question to continue</span>
        </div>

      </div><!-- /.video-wrapper -->

      <!-- Progress timeline -->
      <div class="progress-area">
        <div class="progress-header">
          <span id="time-display">0:00 / --:--</span>
          <span id="progress-pct">—</span>
        </div>
        <div class="timeline" id="timeline">
          <div class="timeline-fill" id="timeline-fill"></div>
        </div>
      </div>

    </div><!-- /.video-section -->

    <!-- SIDEBAR -->
    <div class="side-panel" id="side-panel">
      <div class="panel-heading">Questions</div>
    </div>

  </div><!-- /.main -->
</div><!-- /.app -->

<!-- QUIZ MODAL -->
<div class="quiz-overlay" id="quiz-overlay">
  <div class="quiz-card">
    <div class="quiz-top">
      <span class="quiz-tag">Question</span>
      <span class="quiz-num" id="quiz-num"></span>
    </div>
    <div class="quiz-question" id="quiz-question"></div>
    <div class="options"       id="quiz-options"></div>
    <div class="feedback-box"  id="feedback-box">
      <div class="fb-icon"  id="fb-icon"></div>
      <div>
        <div class="fb-title" id="fb-title"></div>
        <div class="fb-body"  id="fb-body"></div>
      </div>
    </div>
    <div class="btn-row">
      <button class="btn btn-primary" id="btn-submit"   onclick="submitAnswer()" disabled>Submit Answer</button>
      <button class="btn btn-ghost"   id="btn-continue" onclick="continueVideo()" style="display:none">
        Continue
        <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><polyline points="9 18 15 12 9 6"/></svg>
      </button>
    </div>
  </div>
</div>

<!-- RESULTS MODAL -->
<div class="results-overlay" id="results-overlay">
  <div class="results-card">
    <div class="results-icon" id="res-icon"></div>
    <div class="results-score" id="res-score"></div>
    <div class="results-label" id="res-label"></div>
    <div class="results-breakdown">
      <div class="rb-item"><div class="rb-num" id="rb-correct" style="color:var(--green)">0</div><div class="rb-lbl">Correct</div></div>
      <div class="rb-item"><div class="rb-num" id="rb-wrong"   style="color:var(--red)">0</div><div class="rb-lbl">Incorrect</div></div>
      <div class="rb-item"><div class="rb-num" id="rb-total"   style="color:var(--teal)">0</div><div class="rb-lbl">Total</div></div>
    </div>
    <div class="btn-row" style="justify-content:center;">
      <button class="btn btn-primary" onclick="restartQuiz()">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><polyline points="1 4 1 10 7 10"/><path d="M3.51 15a9 9 0 1 0 .49-3.56"/></svg>
        Restart
      </button>
      <button class="btn btn-ghost" onclick="closeResults()">Review Video</button>
    </div>
  </div>
</div>

<script>
/* ================================================================
   ✏️  CONFIGURATION — edit this section to customise your lesson
   ================================================================ */
const CONFIG = {

  // YouTube video ID — the part after ?v= in the URL
  // Example: https://www.youtube.com/watch?v=YE7VzlLtp-4  →  'YE7VzlLtp-4'
  videoId: 'YE7VzlLtp-4',

  // Optional: total video duration in seconds (used for progress bar only)
  // Set to 0 if you don't know it — progress will still work after first play
  videoDuration: 609,   // 10:09 for this TED talk

  title:    'Effective Communication in the Workplace',
  subtitle: 'TED Talk — Julian Treasure · 4 Questions',

  questions: [
    {
      time: 60,            // seconds into the video when question appears
      question: 'According to the speaker, what percentage of our communication time do we spend listening?',
      options: [
        'Around 25% of the day',
        'Approximately 60% of the day',
        'Around 2–3 hours per day',
        'More than 8 hours per day'
      ],
      correct: 1,          // 0 = first option, 1 = second option, etc.
      feedback: 'Treasure notes we spend about 60% of communication time listening — yet retain only about 25% of what we hear.'
    },
    {
      time: 150,
      question: 'Which of the following is one of Treasure\'s "7 Deadly Sins" of speaking?',
      options: ['Speaking too quickly', 'Using technical jargon', 'Gossip', 'Being overly formal'],
      correct: 2,
      feedback: 'Gossip — speaking ill of someone not present — is one of the sins. The full list includes judging, negativity, complaining, excuses, lying, and dogmatism.'
    },
    {
      time: 270,
      question: 'What does the acronym HAIL stand for in Treasure\'s framework?',
      options: [
        'Honesty, Authority, Intelligence, Listening',
        'Honesty, Authenticity, Integrity, Love',
        'Harmony, Attention, Influence, Language',
        'Humility, Awareness, Impact, Logic'
      ],
      correct: 1,
      feedback: 'HAIL = Honesty, Authenticity, Integrity, Love — four cornerstones Treasure recommends for powerful, positive speech.'
    },
    {
      time: 400,
      question: 'Which warm-up exercises does the speaker demonstrate on stage?',
      options: [
        'Humming a musical scale',
        'Saying "very good" in different tones',
        '"Ba Ba Ba" and "We We We" exercises',
        'Deep breathing and lip trills only'
      ],
      correct: 2,
      feedback: 'Treasure demonstrates "Ba Ba Ba", "We We We" and similar exercises to warm up the mouth and voice before speaking.'
    }
  ]
};
/* ================================================================ */


/* ── Video control via postMessage ──────────────────────────────
   This approach sends commands directly to the embedded YouTube
   iframe. No external script loading required — works everywhere
   including SharePoint, Teams, and local file:// opens.
   ─────────────────────────────────────────────────────────────── */

const frame = document.getElementById('yt-frame');

// Build the embed URL. enablejsapi=1 enables postMessage communication.
// autoplay=0 keeps control with us until the play button is clicked.
frame.src = 'https://www.youtube.com/embed/' + CONFIG.videoId
           + '?enablejsapi=1&rel=0&modestbranding=1&playsinline=1&autoplay=0';

function ytCmd(func, args) {
  // Send a command to the YouTube iframe player
  try {
    frame.contentWindow.postMessage(
      JSON.stringify({ event: 'command', func: func, args: args || '' }),
      '*'
    );
  } catch(e) {}
}

function ytPause()      { ytCmd('pauseVideo'); }
function ytPlay()       { ytCmd('playVideo'); }
function ytSeek(secs)   { ytCmd('seekTo', [secs, true]); }
function ytSubscribe()  {
  try {
    frame.contentWindow.postMessage(JSON.stringify({ event: 'listening' }), '*');
  } catch(e) {}
}

// Listen for state-change messages from YouTube
window.addEventListener('message', function(e) {
  // Accept messages from YouTube only
  if (typeof e.data !== 'string' && typeof e.data !== 'object') return;
  let d;
  try { d = typeof e.data === 'string' ? JSON.parse(e.data) : e.data; }
  catch(_) { return; }

  if (d.event === 'onReady')       { ytSubscribe(); }
  if (d.event === 'onStateChange') { handleYTState(d.info); }
});

frame.addEventListener('load', function() {
  // Re-subscribe after every iframe load
  setTimeout(ytSubscribe, 500);
});

/* ── Time tracking without API ─────────────────────────────────
   Because we can't query getCurrentTime() via postMessage,
   we track elapsed time ourselves using a JavaScript timer.
   - When YouTube fires "playing" (state 1): we record wall-clock start
   - When it fires "paused" (state 2): we accumulate elapsed seconds
   - tick() uses these to estimate the current playback position
   ─────────────────────────────────────────────────────────────── */

let watchStart   = null;   // Date.now() when video started playing
let watchedSecs  = 0;      // Accumulated seconds before current session
let isPlaying    = false;
let pollTimer    = null;
let videoStarted = false;

function getTime() {
  if (!isPlaying || watchStart === null) return watchedSecs;
  return watchedSecs + (Date.now() - watchStart) / 1000;
}

function handleYTState(state) {
  // YouTube player states: -1=unstarted, 0=ended, 1=playing, 2=paused, 3=buffering
  if (state === 1) {
    // Playing
    isPlaying  = true;
    watchStart = Date.now();
    videoStarted = true;
    document.getElementById('intro-overlay').classList.add('gone');
    startPolling();
  } else if (state === 2 || state === 0) {
    // Paused or ended
    if (isPlaying && watchStart !== null) {
      watchedSecs += (Date.now() - watchStart) / 1000;
    }
    isPlaying  = false;
    watchStart = null;
    if (state === 0) stopPolling();
  }
}

function startPolling() { if (!pollTimer) pollTimer = setInterval(tick, 400); }
function stopPolling()  { clearInterval(pollTimer); pollTimer = null; }


/* ── Initialise ─────────────────────────────────────────────── */

document.getElementById('unit-title').textContent = CONFIG.title;
document.getElementById('unit-meta').textContent  = CONFIG.subtitle;
buildSidebar();
buildMarkers();


/* ── Tick: update UI and trigger questions ──────────────────── */

function tick() {
  const t = getTime();
  const d = CONFIG.videoDuration || 0;

  // Update progress bar
  if (d > 0) {
    const pct = Math.min(100, t / d * 100);
    document.getElementById('timeline-fill').style.width = pct + '%';
    document.getElementById('progress-pct').textContent  = Math.round(pct) + '%';

    // Update marker positions
    CONFIG.questions.forEach((q, i) => {
      const m = document.getElementById('mk-' + i);
      if (m) m.style.left = Math.min(99, q.time / d * 100) + '%';
    });
  }
  document.getElementById('time-display').textContent = fmt(t) + (d > 0 ? ' / ' + fmt(d) : '');

  // Fire unanswered questions whose timestamp we've passed
  if (currentQ === null) {
    CONFIG.questions.forEach((q, i) => {
      if (answers[i] !== undefined) return;
      if (t >= q.time) triggerQuestion(i);
    });
  }

  // All answered — show results
  if (Object.keys(answers).length >= CONFIG.questions.length) {
    stopPolling();
    setTimeout(showResults, 1200);
  }
}


/* ── Intro play button (so we know when watching begins) ────── */

function startVideo() {
  document.getElementById('intro-overlay').classList.add('gone');
  // Don't seek — just let it play from the start
  ytPlay();
}


/* ── Build sidebar ──────────────────────────────────────────── */

function buildSidebar() {
  const panel = document.getElementById('side-panel');
  CONFIG.questions.forEach((q, i) => {
    const el = document.createElement('div');
    el.className = 'q-item';
    el.id = 'qi-' + i;
    el.innerHTML =
      '<div class="q-item-top">' +
        '<div class="q-badge pending" id="qb-' + i + '">' + (i+1) + '</div>' +
        '<div class="q-text">'  + q.question + '</div>' +
      '</div>' +
      '<div class="q-time">' + fmt(q.time) + '</div>';
    panel.appendChild(el);
  });
}


/* ── Build timeline markers ─────────────────────────────────── */

function buildMarkers() {
  const tl = document.getElementById('timeline');
  const d  = CONFIG.videoDuration || 0;
  CONFIG.questions.forEach((q, i) => {
    const m = document.createElement('div');
    m.className = 'marker pending';
    m.id = 'mk-' + i;
    m.style.left = d > 0 ? Math.min(99, q.time / d * 100) + '%' : '0%';
    m.title = 'Q' + (i+1) + ' at ' + fmt(q.time);
    tl.appendChild(m);
  });
}


/* ── Quiz state ─────────────────────────────────────────────── */

let currentQ   = null;
let selectedOpt= null;
let answers    = {};

function triggerQuestion(idx) {
  currentQ    = idx;
  selectedOpt = null;

  ytPause();
  document.getElementById('click-shield').classList.add('active');

  // Highlight sidebar
  document.querySelectorAll('.q-item').forEach(el => el.classList.remove('active'));
  document.getElementById('qi-' + idx).classList.add('active');

  // Populate modal
  const q = CONFIG.questions[idx];
  document.getElementById('quiz-num').textContent      = (idx+1) + ' of ' + CONFIG.questions.length;
  document.getElementById('quiz-question').textContent = q.question;

  const letters = ['A','B','C','D','E'];
  const wrap    = document.getElementById('quiz-options');
  wrap.innerHTML = '';
  q.options.forEach((opt, oi) => {
    const el = document.createElement('div');
    el.className = 'option';
    el.innerHTML = '<div class="option-letter">' + letters[oi] + '</div><span>' + opt + '</span>';
    el.onclick = () => pick(el, oi);
    wrap.appendChild(el);
  });

  document.getElementById('feedback-box').className     = 'feedback-box';
  document.getElementById('btn-submit').disabled        = true;
  document.getElementById('btn-submit').style.display   = 'inline-flex';
  document.getElementById('btn-continue').style.display = 'none';
  document.getElementById('quiz-overlay').classList.add('active');
}

function pick(el, idx) {
  if (el.classList.contains('disabled')) return;
  document.querySelectorAll('.option').forEach(o => o.classList.remove('selected'));
  el.classList.add('selected');
  selectedOpt = idx;
  document.getElementById('btn-submit').disabled = false;
}

function submitAnswer() {
  if (selectedOpt === null || currentQ === null) return;
  const q       = CONFIG.questions[currentQ];
  const correct = selectedOpt === q.correct;
  answers[currentQ] = { correct };

  document.querySelectorAll('.option').forEach((el, i) => {
    el.classList.add('disabled');
    if (i === q.correct)               el.classList.add('correct');
    if (i === selectedOpt && !correct) el.classList.add('wrong');
  });

  const fb  = document.getElementById('feedback-box');
  const fbT = document.getElementById('fb-title');
  const fbB = document.getElementById('fb-body');
  const fbI = document.getElementById('fb-icon');

  if (correct) {
    fb.className  = 'feedback-box show correct-fb';
    fbI.innerHTML = '<svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="var(--green)" stroke-width="2.5"><polyline points="20 6 9 17 4 12"/></svg>';
    fbT.className = 'fb-title green';
    fbT.textContent = 'Correct!';
  } else {
    fb.className  = 'feedback-box show wrong-fb';
    fbI.innerHTML = '<svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="var(--red)" stroke-width="2.5"><line x1="18" y1="6" x2="6" y2="18"/><line x1="6" y1="6" x2="18" y2="18"/></svg>';
    fbT.className = 'fb-title red';
    fbT.textContent = 'Incorrect';
  }
  fbB.textContent = q.feedback;

  const state = correct ? 'correct' : 'wrong';
  const mk = document.getElementById('mk-' + currentQ);
  if (mk) mk.className = 'marker ' + state;
  document.getElementById('qi-' + currentQ).classList.remove('active');
  document.getElementById('qi-' + currentQ).classList.add(state);
  document.getElementById('qb-' + currentQ).className = 'q-badge ' + state;

  const n = Object.keys(answers).length;
  const r = Object.values(answers).filter(a => a.correct).length;
  document.getElementById('score-text').textContent = r + ' / ' + n;
  document.getElementById('header-score').classList.add('visible');

  document.getElementById('btn-submit').style.display   = 'none';
  document.getElementById('btn-continue').style.display = 'inline-flex';
}

function continueVideo() {
  document.getElementById('quiz-overlay').classList.remove('active');
  document.getElementById('click-shield').classList.remove('active');
  const wasQ = currentQ;
  currentQ = null;

  // Advance time estimate past the trigger point so it won't re-fire
  watchedSecs = CONFIG.questions[wasQ].time + 2;
  watchStart  = Date.now();
  isPlaying   = true;

  ytPlay();
  startPolling();
}


/* ── Results ────────────────────────────────────────────────── */

function showResults() {
  if (document.getElementById('results-overlay').classList.contains('active')) return;
  const total   = CONFIG.questions.length;
  const correct = Object.values(answers).filter(a => a.correct).length;
  const pct     = Math.round(correct / total * 100);

  document.getElementById('rb-correct').textContent = correct;
  document.getElementById('rb-wrong').textContent   = total - correct;
  document.getElementById('rb-total').textContent   = total;

  const tier = pct >= 80 ? 'great' : pct >= 50 ? 'good' : 'try';
  document.getElementById('res-icon').className    = 'results-icon ' + tier;
  document.getElementById('res-icon').textContent  = pct >= 80 ? '🎉' : pct >= 50 ? '👍' : '📚';
  document.getElementById('res-score').className   = 'results-score ' + tier;
  document.getElementById('res-score').textContent = pct + '%';
  document.getElementById('res-label').textContent =
    pct >= 80 ? 'Excellent! ' + correct + ' of ' + total + ' correct.' :
    pct >= 50 ? 'Good effort — ' + correct + ' of ' + total + ' correct.' :
                correct + ' of ' + total + ' correct. Give it another try!';

  document.getElementById('results-overlay').classList.add('active');
}

function closeResults() {
  document.getElementById('results-overlay').classList.remove('active');
}

function restartQuiz() {
  answers = {}; currentQ = null; selectedOpt = null;
  watchedSecs = 0; watchStart = null; isPlaying = false;

  document.getElementById('results-overlay').classList.remove('active');
  document.getElementById('header-score').classList.remove('visible');
  document.getElementById('timeline-fill').style.width = '0%';
  document.getElementById('time-display').textContent = '0:00' + (CONFIG.videoDuration ? ' / ' + fmt(CONFIG.videoDuration) : '');
  document.getElementById('progress-pct').textContent = CONFIG.videoDuration ? '0%' : '—';

  document.querySelectorAll('.q-item').forEach(el  => el.classList.remove('active','correct','wrong'));
  document.querySelectorAll('.q-badge').forEach(el => el.className = 'q-badge pending');
  document.querySelectorAll('.marker').forEach(el  => el.className = 'marker pending');

  // Reload the iframe cleanly — avoids postMessage seek issues
  frame.src = frame.src;
  document.getElementById('intro-overlay').classList.remove('gone');
}

/* ── Helpers ────────────────────────────────────────────────── */
function fmt(s) {
  s = Math.max(0, Math.floor(s || 0));
  return Math.floor(s / 60) + ':' + String(s % 60).padStart(2, '0');
}
</script>
</body>
</html>
