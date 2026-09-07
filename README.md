<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1"/>
<title>Common Tongue · Chinese Classroom</title>
<meta name="description" content="A shared Chinese classroom for notes, pronunciation practice, questions, and private teacher feedback."/>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Manrope:wght@400;500;600;700;800&family=Newsreader:opsz,wght@6..72,500;6..72,600&display=swap" rel="stylesheet">
<style>
:root {
  --background: 36 42% 94%;
  --foreground: 212 28% 17%;
  --border: 35 24% 84%;
  --card: 39 44% 97%;
  --card-border: 35 25% 86%;
  --primary: 13 63% 52%;
  --secondary: 174 28% 28%;
  --muted-foreground: 212 14% 47%;
  --accent: 43 79% 61%;
  --app-font-sans: 'Manrope', sans-serif;
  --app-font-serif: 'Newsreader', Georgia, serif;
  --shadow-soft: 0 15px 40px hsl(174 28% 24% / 0.08);
}
* { box-sizing: border-box; }
html { min-width: 320px; scroll-behavior: smooth; }
body {
  margin: 0; min-width: 320px; min-height: 100dvh;
  background: hsl(var(--background)); color: hsl(var(--foreground));
  font-family: var(--app-font-sans); -webkit-font-smoothing: antialiased;
}
.classroom-page { min-height:100dvh; padding:40px 32px 64px; max-width:1100px; margin:0 auto; }
.classroom-header { display:flex; align-items:center; gap:16px; margin-bottom:36px; }
.classroom-header h1 { margin:0; font:600 28px var(--app-font-serif); letter-spacing:-0.03em; }
.classroom-header p { margin:2px 0 0; color:hsl(var(--muted-foreground)); font-size:13px; }
.brand-mark { width:46px; height:46px; flex:0 0 auto; display:grid; place-items:center; border-radius:14px 14px 14px 4px; background:hsl(var(--accent)); color:hsl(var(--foreground)); font-family:var(--app-font-serif); font-size:26px; }

.lesson-block { margin-top:8px; }
.lesson-title-row { margin-bottom:14px; display:flex; align-items:center; justify-content:space-between; gap:12px; }
.lesson-title { margin:0; border:none; background:none; padding:2px 4px; width:auto; min-width:120px; font:600 20px var(--app-font-serif); letter-spacing:-0.02em; color:hsl(var(--foreground)); }
.lesson-title:focus { outline:none; border-bottom:1px solid hsl(var(--primary)); }
.lesson-actions { display:flex; align-items:center; gap:4px; flex:0 0 auto; }
.lesson-action-button { display:inline-flex; align-items:center; justify-content:center; width:28px; height:28px; border:1px solid hsl(var(--card-border)); border-radius:999px; background:hsl(var(--card)); color:hsl(var(--muted-foreground)); cursor:pointer; }
.lesson-action-button:hover:not(:disabled) { color:hsl(var(--primary)); border-color:hsl(var(--primary)); }
.lesson-action-button:disabled { opacity:0.35; cursor:not-allowed; }
.lesson-action-danger:hover:not(:disabled) { color:hsl(0 60% 50%); border-color:hsl(0 60% 50%); }

.lesson-table { display:grid; gap:12px 16px; align-items:start; }
.lesson-table-head { font-size:13px; font-weight:700; color:hsl(var(--secondary)); text-transform:uppercase; letter-spacing:0.05em; padding:4px 4px 10px; border-bottom:1px solid hsl(var(--card-border)); }

.practice-session-block { margin-top:28px; }
.practice-title-row { margin-bottom:14px; display:flex; align-items:center; justify-content:space-between; gap:12px; }
.practice-title { margin:0; border:none; background:none; padding:2px 4px; width:auto; min-width:120px; font:600 16px var(--app-font-serif); letter-spacing:-0.01em; color:hsl(var(--secondary)); }
.practice-title:focus { outline:none; border-bottom:1px solid hsl(var(--primary)); }
.add-session-button { display:inline-flex; align-items:center; gap:6px; margin-top:16px; border:1px dashed hsl(var(--card-border)); background:none; border-radius:999px; padding:7px 14px; font:600 12px var(--app-font-sans); color:hsl(var(--muted-foreground)); cursor:pointer; }
.add-session-button:hover { color:hsl(var(--primary)); border-color:hsl(var(--primary)); }
.practice-table { display:grid; gap:12px 16px; align-items:start; }

.task-col { position:relative; display:flex; align-items:center; min-height:64px; }
.task-prompt { margin:0; padding:4px 2px; font:500 14px var(--app-font-sans); color:hsl(var(--foreground)); }
.answer-input { width:100%; min-height:64px; resize:vertical; border:1px solid hsl(var(--card-border)); border-radius:10px; padding:8px 10px; font:500 13px var(--app-font-sans); color:hsl(var(--foreground)); background:hsl(var(--background)); }
.answer-input:focus { outline:none; border-color:hsl(var(--primary)); }
.judgment-row { display:inline-flex; gap:6px; }
.judgment-button { display:inline-flex; align-items:center; gap:4px; border:1px solid hsl(var(--card-border)); background:hsl(var(--background)); border-radius:999px; padding:5px 10px; font:600 11px var(--app-font-sans); color:hsl(var(--muted-foreground)); cursor:pointer; }
.judgment-button:hover { border-color:hsl(var(--primary)); }
.judgment-correct.judgment-active { background:hsl(150 45% 40%); border-color:hsl(150 45% 40%); color:hsl(39 44% 97%); }
.judgment-incorrect.judgment-active { background:hsl(0 60% 50%); border-color:hsl(0 60% 50%); color:hsl(39 44% 97%); }

.lesson-row, .task-row { display:contents; }
.word-col { display:flex; align-items:center; min-height:64px; }
.word-col-split { position:relative; flex-direction:column; align-items:stretch; justify-content:center; gap:2px; }
.row-delete-button { position:absolute; top:-2px; right:-2px; display:inline-flex; align-items:center; justify-content:center; width:20px; height:20px; border:1px solid hsl(var(--card-border)); border-radius:999px; background:hsl(var(--card)); color:hsl(var(--muted-foreground)); cursor:pointer; opacity:0; transition:opacity 0.15s ease, color 0.15s ease, border-color 0.15s ease; }
.lesson-row:hover .row-delete-button, .task-row:hover .row-delete-button, .row-delete-button:focus-visible { opacity:1; }
.row-delete-button:hover { color:hsl(0 60% 50%); border-color:hsl(0 60% 50%); }
.word-display { margin:0; padding:4px 2px; }
.word-display-zh { font:600 18px var(--app-font-serif); color:hsl(var(--foreground)); }
.word-display-pinyin { font:500 12px var(--app-font-sans); font-style:italic; color:hsl(var(--primary)); }
.word-display-en { font:500 13px var(--app-font-sans); color:hsl(var(--muted-foreground)); }

.lesson-cell { min-width:0; min-height:64px; padding:16px; border:1px solid hsl(var(--card-border)); border-radius:16px; background:hsl(var(--card)); box-shadow:var(--shadow-soft); display:flex; flex-direction:column; gap:8px; justify-content:center; }
.record-button { display:inline-flex; flex-direction:column; align-items:center; justify-content:center; gap:2px; flex:1 1 0; min-width:0; padding:8px 4px; border:none; border-radius:14px; font:600 10px var(--app-font-sans); line-height:1.25; text-align:center; white-space:normal; word-break:break-word; cursor:pointer; transition:opacity 0.15s ease; background:hsl(var(--secondary)); color:hsl(39 44% 97%); }
.record-button:hover { opacity:0.9; }
.record-button svg { flex:0 0 auto; width:13px; height:13px; }
.record-button-active { background:hsl(0 68% 52%); animation:record-pulse 1.4s ease-in-out infinite; }
@keyframes record-pulse { 0%,100%{opacity:1;} 50%{opacity:0.7;} }

.add-word-button { display:inline-flex; align-items:center; gap:6px; border:1px dashed hsl(var(--card-border)); background:none; border-radius:999px; padding:7px 14px; font:600 12px var(--app-font-sans); color:hsl(var(--muted-foreground)); cursor:pointer; }
.add-word-button:hover { color:hsl(var(--primary)); border-color:hsl(var(--primary)); }
.add-lesson-button { display:inline-flex; align-items:center; gap:8px; margin-top:12px; margin-bottom:40px; border:1px dashed hsl(var(--secondary)); background:none; border-radius:999px; padding:10px 20px; font:700 13px var(--app-font-sans); color:hsl(var(--secondary)); cursor:pointer; }
.add-lesson-button:hover { color:hsl(var(--primary)); border-color:hsl(var(--primary)); }

.dialog-overlay { position:fixed; inset:0; background:hsl(212 28% 12% / 0.45); display:grid; place-items:center; padding:20px; z-index:50; }
.dialog-card { width:100%; max-width:340px; background:hsl(var(--card)); border:1px solid hsl(var(--card-border)); border-radius:18px; padding:20px; box-shadow:var(--shadow-soft); display:flex; flex-direction:column; gap:14px; }
.dialog-header { display:flex; align-items:center; justify-content:space-between; }
.dialog-header h3 { margin:0; font:600 17px var(--app-font-serif); }
.dialog-close { border:none; background:none; color:hsl(var(--muted-foreground)); cursor:pointer; display:inline-flex; padding:2px; }
.dialog-close:hover { color:hsl(var(--primary)); }
.dialog-input { border:1px solid hsl(var(--card-border)); border-radius:10px; padding:9px 12px; font:500 14px var(--app-font-sans); color:hsl(var(--foreground)); background:hsl(var(--background)); width:100%; }
.dialog-input:focus { outline:none; border-color:hsl(var(--primary)); }
.dialog-textarea { border:1px solid hsl(var(--card-border)); border-radius:10px; padding:9px 12px; font:500 14px var(--app-font-sans); color:hsl(var(--foreground)); background:hsl(var(--background)); min-height:72px; resize:vertical; width:100%; }
.dialog-textarea:focus { outline:none; border-color:hsl(var(--primary)); }
.dialog-actions { display:flex; justify-content:flex-end; gap:10px; margin-top:4px; }
.dialog-cancel { border:none; background:none; padding:9px 14px; font:600 13px var(--app-font-sans); color:hsl(var(--muted-foreground)); cursor:pointer; }
.dialog-cancel:hover { color:hsl(var(--foreground)); }
.dialog-submit { border:none; border-radius:999px; padding:9px 18px; font:600 13px var(--app-font-sans); background:hsl(var(--primary)); color:hsl(39 44% 97%); cursor:pointer; }
.dialog-submit:hover { opacity:0.9; }
.dialog-submit-danger { background:hsl(0 60% 50%); }
.dialog-message { margin:0; font:500 13px var(--app-font-sans); color:hsl(var(--muted-foreground)); line-height:1.5; }

.media-name { margin:0; font-size:13px; font-weight:600; color:hsl(var(--foreground)); word-break:break-word; }
.media-player { width:100%; max-height:200px; border-radius:12px; background:#000; }
.star-row { display:inline-flex; gap:2px; }
.star-button { border:none; background:none; padding:2px; cursor:pointer; color:hsl(var(--accent)); display:inline-flex; }
.comment-input { width:100%; border:1px solid hsl(var(--primary)); border-radius:999px; padding:5px 12px; font-size:12px; background:hsl(var(--background)); color:hsl(var(--foreground)); }
.comment-input:focus { outline:none; }

.status-page { min-height:100dvh; display:grid; place-items:center; padding:24px; text-align:center; }
.status-card { max-width:420px; padding:32px; border:1px solid hsl(var(--card-border)); border-radius:18px; background:hsl(var(--card)); box-shadow:var(--shadow-soft); display:flex; flex-direction:column; gap:14px; align-items:center; }
.status-card h2 { margin:0; font:600 20px var(--app-font-serif); }

/* SVG icons inline */
.icon { display:inline-block; vertical-align:middle; }

@media (max-width:480px) {
  .classroom-page { padding:28px 18px 48px; }
  .lesson-table, .practice-table { grid-template-columns:1fr !important; }
  .word-col, .task-col { min-height:auto; }
}
</style>
</head>
<body>
<div id="app"></div>
<script>
// SVG icon helpers
const icons = {
  chevronUp: `<svg width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="m18 15-6-6-6 6"/></svg>`,
  chevronDown: `<svg width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="m6 9 6 6 6-6"/></svg>`,
  plus: `<svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M5 12h14"/><path d="M12 5v14"/></svg>`,
  trash: `<svg width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M3 6h18"/><path d="M19 6v14c0 1-1 2-2 2H7c-1 0-2-1-2-2V6"/><path d="M8 6V4c0-1 1-2 2-2h4c1 0 2 1 2 2v2"/></svg>`,
  x: `<svg width="13" height="13" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M18 6 6 18"/><path d="m6 6 12 12"/></svg>`,
  mic: `<svg width="13" height="13" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M12 2a3 3 0 0 0-3 3v7a3 3 0 0 0 6 0V5a3 3 0 0 0-3-3Z"/><path d="M19 10v2a7 7 0 0 1-14 0v-2"/><line x1="12" x2="12" y1="19" y2="22"/></svg>`,
  square: `<svg width="12" height="12" viewBox="0 0 24 24" fill="currentColor" stroke="currentColor" stroke-width="2"><rect x="3" y="3" width="18" height="18" rx="2"/></svg>`,
  star: (filled) => `<svg width="15" height="15" viewBox="0 0 24 24" fill="${filled?'currentColor':'none'}" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polygon points="12 2 15.09 8.26 22 9.27 17 14.14 18.18 21.02 12 17.77 5.82 21.02 7 14.14 2 9.27 8.91 8.26 12 2"/></svg>`,
  check: `<svg width="13" height="13" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M20 6 9 17l-5-5"/></svg>`,
};

const STORAGE_KEY = 'classroom-state-standalone-v1';
const MEDIA_DB = 'classroom-media-standalone';
const MEDIA_STORE = 'files';
const STUDENTS = [{key:'a',label:'Student A'},{key:'b',label:'Student B'}];

// IndexedDB helpers
function openDb() {
  return new Promise((resolve, reject) => {
    const req = indexedDB.open(MEDIA_DB, 1);
    req.onupgradeneeded = () => { if (!req.result.objectStoreNames.contains(MEDIA_STORE)) req.result.createObjectStore(MEDIA_STORE); };
    req.onsuccess = () => resolve(req.result);
    req.onerror = () => reject(req.error);
  });
}
async function putFile(blob) {
  const id = crypto.randomUUID();
  const db = await openDb();
  await new Promise((resolve, reject) => { const tx = db.transaction(MEDIA_STORE,'readwrite'); tx.objectStore(MEDIA_STORE).put(blob,id); tx.oncomplete=()=>resolve(); tx.onerror=()=>reject(tx.error); });
  db.close(); return id;
}
async function getFileBlob(id) {
  const db = await openDb();
  const blob = await new Promise((resolve, reject) => { const r = db.transaction(MEDIA_STORE,'readonly').objectStore(MEDIA_STORE).get(id); r.onsuccess=()=>resolve(r.result??null); r.onerror=()=>reject(r.error); });
  db.close(); return blob;
}

// State
let state = { lessons: [], ready: false };
let dialog = null; // {type, ...data}
let recorders = {}; // id -> {recorder, stream, timer, seconds}

function uuid() { return crypto.randomUUID(); }
function emptySubmission() { return {media:null,rating:0,comment:''}; }
function emptyResponse() { return {answer:'',judgment:null,comment:''}; }
function makeExercise(zh='',pinyin='',en='') { return {id:uuid(),wordZh:zh,wordPinyin:pinyin,wordEn:en,teacherVideo:null,submissions:{a:emptySubmission(),b:emptySubmission()}}; }
function makeTask(prompt) { return {id:uuid(),prompt,responses:{a:emptyResponse(),b:emptyResponse()}}; }
function makeLesson(title) { return {id:uuid(),title,exercises:[],practiceSessions:[]}; }
function makePracticeSession(n) { return {id:uuid(),title:`Practice Session ${n}`,tasks:[]}; }

function toStored(media) { return media ? {id:media.id,name:media.name,type:media.type} : null; }
function toStoredLesson(l) {
  return {...l, exercises: l.exercises.map(e => ({...e, teacherVideo:toStored(e.teacherVideo), submissions:{a:{...e.submissions.a,media:toStored(e.submissions.a.media)},b:{...e.submissions.b,media:toStored(e.submissions.b.media)}}}))};
}
function save() { localStorage.setItem(STORAGE_KEY, JSON.stringify(state.lessons.map(toStoredLesson))); }

async function hydrateMedia(m) { if(!m) return null; const blob = await getFileBlob(m.id); return blob ? {...m, url:URL.createObjectURL(blob)} : null; }
async function hydrateLessons(stored) {
  return Promise.all(stored.map(async l => ({...l, exercises: await Promise.all(l.exercises.map(async e => ({...e, teacherVideo: await hydrateMedia(e.teacherVideo), submissions: {a:{...e.submissions.a, media:await hydrateMedia(e.submissions.a.media)}, b:{...e.submissions.b, media:await hydrateMedia(e.submissions.b.media)}}})))})));
}

async function init() {
  let stored = [];
  try { const p = JSON.parse(localStorage.getItem(STORAGE_KEY)||'[]'); stored = Array.isArray(p)?p:[]; } catch {}
  state.lessons = (await hydrateLessons(stored));
  if (!state.lessons.length) state.lessons = [makeLesson('Lesson 1')];
  state.ready = true;
  render();
}

function formatSeconds(s) { return `${Math.floor(s/60).toString().padStart(2,'0')}:${(s%60).toString().padStart(2,'0')}`; }

// Recording
async function startRecording(id, onDone) {
  if (!navigator.mediaDevices?.getUserMedia || typeof MediaRecorder === 'undefined') { alert('Voice recording not supported'); return; }
  try {
    const stream = await navigator.mediaDevices.getUserMedia({audio:true});
    const recorder = new MediaRecorder(stream);
    const chunks = [];
    recorder.ondataavailable = e => { if(e.data.size>0) chunks.push(e.data); };
    recorder.onstop = () => {
      const blob = new Blob(chunks, {type:recorder.mimeType||'audio/webm'});
      const ext = blob.type.includes('mp4')?'m4a':'webm';
      onDone(new File([blob],`recording-${Date.now()}.${ext}`,{type:blob.type}));
      stream.getTracks().forEach(t=>t.stop());
      delete recorders[id];
      render();
    };
    recorder.start();
    recorders[id] = {recorder, stream, seconds:0, timer: setInterval(()=>{recorders[id].seconds++;render();},1000)};
    render();
  } catch { alert('Microphone access denied'); }
}
function stopRecording(id) {
  const r = recorders[id];
  if(r) { r.recorder.stop(); clearInterval(r.timer); }
}

async function saveMedia(file) { const id = await putFile(file); return {id, name:file.name, type:file.type, url:URL.createObjectURL(file)}; }

// Render helpers
function h(tag, attrs, ...children) {
  const el = document.createElement(tag);
  if (attrs) for (const [k,v] of Object.entries(attrs)) {
    if (k === 'style' && typeof v === 'object') Object.assign(el.style, v);
    else if (k.startsWith('on')) el.addEventListener(k.slice(2).toLowerCase(), v);
    else if (k === 'innerHTML') el.innerHTML = v;
    else if (k === 'className') el.className = v;
    else if (k === 'disabled') { if(v) el.setAttribute('disabled',''); }
    else if (k === 'value') el.value = v;
    else if (k === 'placeholder') el.placeholder = v;
    else if (k === 'required') { if(v) el.required = true; }
    else if (k === 'type') el.type = v;
    else if (k === 'controls') el.controls = true;
    else if (k === 'src') el.src = v;
    else el.setAttribute(k, v);
  }
  for (const c of children) {
    if (c == null) continue;
    if (typeof c === 'string') el.appendChild(document.createTextNode(c));
    else if (Array.isArray(c)) c.forEach(x => { if(x) el.appendChild(x); });
    else el.appendChild(c);
  }
  return el;
}

function renderRecordButton(recId, label, onRecorded) {
  const rec = recorders[recId];
  if (rec) {
    return h('button', {className:'record-button record-button-active', onClick:()=>stopRecording(recId), innerHTML: icons.square + ' ' + formatSeconds(rec.seconds)});
  }
  return h('button', {className:'record-button', onClick:()=>startRecording(recId, onRecorded), innerHTML: icons.mic + ' ' + label});
}

function renderStars(value, onChange) {
  const row = h('div', {className:'star-row'});
  for (let i=1;i<=5;i++) {
    row.appendChild(h('button', {className:'star-button', innerHTML: icons.star(i<=value), onClick:()=>{onChange(i);save();render();}}));
  }
  return row;
}

function renderComment(value, onChange) {
  const ta = h('textarea', {className:'comment-input', placeholder:'Comment...', value});
  ta.value = value;
  ta.addEventListener('input', e=>{onChange(e.target.value);save();});
  return ta;
}

function renderWordRow(lesson, exercise) {
  const els = [];
  // Word column
  const wordCol = h('div', {className:'word-col word-col-split'},
    h('p', {className:'word-display word-display-zh'}, exercise.wordZh||'—'),
    exercise.wordPinyin ? h('p',{className:'word-display word-display-pinyin'},exercise.wordPinyin) : null,
    h('p', {className:'word-display word-display-en'}, exercise.wordEn),
    h('button', {className:'row-delete-button', onClick:()=>{dialog={type:'confirmDelete',kind:'word',id:exercise.id};render();}, innerHTML: icons.x})
  );
  els.push(wordCol);
  // Teacher cell
  const teacherCell = h('div', {className:'lesson-cell'});
  if (exercise.teacherVideo) {
    teacherCell.appendChild(h('p',{className:'media-name'},exercise.teacherVideo.name));
    teacherCell.appendChild(h('audio',{className:'media-player',src:exercise.teacherVideo.url,controls:true}));
  }
  const tRecId = 'teacher-'+exercise.id;
  teacherCell.appendChild(renderRecordButton(tRecId, exercise.teacherVideo?'re-record':'record', async(file)=>{
    exercise.teacherVideo = await saveMedia(file); save(); render();
  }));
  els.push(teacherCell);
  // Student cells
  for (const s of STUDENTS) {
    const sub = exercise.submissions[s.key];
    const cell = h('div', {className:'lesson-cell'});
    if (sub.media) {
      cell.appendChild(h('p',{className:'media-name'},sub.media.name));
      cell.appendChild(h('audio',{className:'media-player',src:sub.media.url,controls:true}));
    }
    const sRecId = `student-${s.key}-${exercise.id}`;
    cell.appendChild(renderRecordButton(sRecId, sub.media?'re-record':'record', async(file)=>{
      sub.media = await saveMedia(file); save(); render();
    }));
    cell.appendChild(renderStars(sub.rating, v=>{sub.rating=v;}));
    cell.appendChild(renderComment(sub.comment, v=>{sub.comment=v;}));
    els.push(cell);
  }
  return els;
}

function renderTaskRow(lesson, session, task) {
  const els = [];
  const taskCol = h('div',{className:'task-col'},
    h('p',{className:'task-prompt'},task.prompt),
    h('button',{className:'row-delete-button',onClick:()=>{dialog={type:'confirmDelete',kind:'task',id:task.id};render();},innerHTML:icons.x})
  );
  els.push(taskCol);
  for (const s of STUDENTS) {
    const resp = task.responses[s.key];
    const cell = h('div',{className:'lesson-cell'});
    const answerTA = h('textarea',{className:'answer-input',placeholder:'Type your answer...'});
    answerTA.value = resp.answer;
    answerTA.addEventListener('input', e=>{resp.answer=e.target.value;save();});
    cell.appendChild(answerTA);
    const jRow = h('div',{className:'judgment-row'});
    const correctBtn = h('button',{className:'judgment-button judgment-correct'+(resp.judgment==='correct'?' judgment-active':''),innerHTML:icons.check,onClick:()=>{resp.judgment=resp.judgment==='correct'?null:'correct';save();render();}});
    const incorrectBtn = h('button',{className:'judgment-button judgment-incorrect'+(resp.judgment==='incorrect'?' judgment-active':''),innerHTML:icons.x,onClick:()=>{resp.judgment=resp.judgment==='incorrect'?null:'incorrect';save();render();}});
    jRow.appendChild(correctBtn);
    jRow.appendChild(incorrectBtn);
    cell.appendChild(jRow);
    cell.appendChild(renderComment(resp.comment, v=>{resp.comment=v;}));
    els.push(cell);
  }
  return els;
}

function render() {
  const app = document.getElementById('app');
  app.innerHTML = '';
  if (!state.ready) {
    app.appendChild(h('div',{className:'status-page'},h('div',{className:'status-card'},h('h2',null,'Loading classroom…'))));
    return;
  }

  const page = h('div',{className:'classroom-page'});
  // Header
  page.appendChild(h('header',{className:'classroom-header'},
    h('div',{className:'brand-mark'},'文'),
    h('div',null,h('h1',null,'Common Tongue'),h('p',null,'A simple Chinese classroom'))
  ));

  // Lessons
  state.lessons.forEach((lesson, li) => {
    const section = h('section',{className:'lesson-block'});
    // Title row
    const titleInput = h('input',{className:'lesson-title',value:lesson.title});
    titleInput.value = lesson.title;
    titleInput.addEventListener('blur',()=>{if(titleInput.value.trim()) lesson.title=titleInput.value.trim(); save();});
    titleInput.addEventListener('keydown',e=>{if(e.key==='Enter')titleInput.blur();});

    const actions = h('div',{className:'lesson-actions'},
      h('button',{className:'lesson-action-button',disabled:li===0,onClick:()=>{if(li>0){[state.lessons[li],state.lessons[li-1]]=[state.lessons[li-1],state.lessons[li]];save();render();}},innerHTML:icons.chevronUp}),
      h('button',{className:'lesson-action-button',disabled:li===state.lessons.length-1,onClick:()=>{if(li<state.lessons.length-1){[state.lessons[li],state.lessons[li+1]]=[state.lessons[li+1],state.lessons[li]];save();render();}},innerHTML:icons.chevronDown}),
      h('button',{className:'lesson-action-button lesson-action-danger',onClick:()=>{dialog={type:'confirmDelete',kind:'lesson',id:lesson.id};render();},innerHTML:icons.trash})
    );
    section.appendChild(h('div',{className:'lesson-title-row'},titleInput,actions));

    // Word table
    const table = h('div',{className:'lesson-table',style:{gridTemplateColumns:'110px repeat(3, minmax(0, 1fr))'}});
    table.appendChild(h('div',{className:'lesson-table-head word-col'}));
    table.appendChild(h('div',{className:'lesson-table-head'},'Teacher'));
    STUDENTS.forEach(s=>table.appendChild(h('div',{className:'lesson-table-head'},s.label)));
    lesson.exercises.forEach(ex => {
      const rowEls = renderWordRow(lesson, ex);
      rowEls.forEach(el => table.appendChild(el));
    });
    // Add word button row
    table.appendChild(h('div',{className:'word-col'},h('button',{className:'add-word-button',onClick:()=>{dialog={type:'addWord',lessonId:lesson.id};render();},innerHTML:icons.plus+' word'})));
    table.appendChild(h('div'));table.appendChild(h('div'));table.appendChild(h('div'));
    section.appendChild(table);

    // Practice sessions
    lesson.practiceSessions.forEach((sess, si) => {
      const sessBlock = h('section',{className:'practice-session-block'});
      const sessTitle = h('input',{className:'practice-title',value:sess.title});
      sessTitle.value = sess.title;
      sessTitle.addEventListener('blur',()=>{if(sessTitle.value.trim()) sess.title=sessTitle.value.trim(); save();});
      sessTitle.addEventListener('keydown',e=>{if(e.key==='Enter')sessTitle.blur();});
      const sessActions = h('div',{className:'lesson-actions'},
        h('button',{className:'lesson-action-button',disabled:si===0,onClick:()=>{if(si>0){[lesson.practiceSessions[si],lesson.practiceSessions[si-1]]=[lesson.practiceSessions[si-1],lesson.practiceSessions[si]];save();render();}},innerHTML:icons.chevronUp}),
        h('button',{className:'lesson-action-button',disabled:si===lesson.practiceSessions.length-1,onClick:()=>{if(si<lesson.practiceSessions.length-1){[lesson.practiceSessions[si],lesson.practiceSessions[si+1]]=[lesson.practiceSessions[si+1],lesson.practiceSessions[si]];save();render();}},innerHTML:icons.chevronDown}),
        h('button',{className:'lesson-action-button lesson-action-danger',onClick:()=>{dialog={type:'confirmDelete',kind:'session',id:sess.id};render();},innerHTML:icons.trash})
      );
      sessBlock.appendChild(h('div',{className:'practice-title-row'},sessTitle,sessActions));
      const pTable = h('div',{className:'practice-table',style:{gridTemplateColumns:'200px repeat(2, minmax(0, 1fr))'}});
      pTable.appendChild(h('div',{className:'lesson-table-head task-col'},'Task'));
      STUDENTS.forEach(s=>pTable.appendChild(h('div',{className:'lesson-table-head'},s.label)));
      sess.tasks.forEach(task => {
        renderTaskRow(lesson, sess, task).forEach(el=>pTable.appendChild(el));
      });
      sessBlock.appendChild(pTable);
      sessBlock.appendChild(h('button',{className:'add-word-button',onClick:()=>{dialog={type:'addTask',sessionId:sess.id};render();},innerHTML:icons.plus+' task'}));
      section.appendChild(sessBlock);
    });
    section.appendChild(h('button',{className:'add-session-button',onClick:()=>{lesson.practiceSessions.push(makePracticeSession(lesson.practiceSessions.length+1));save();render();},innerHTML:icons.plus+' practice session'}));
    page.appendChild(section);
  });

  // Add lesson button
  page.appendChild(h('button',{className:'add-lesson-button',onClick:()=>{state.lessons.push(makeLesson(`Lesson ${state.lessons.length+1}`));save();render();},innerHTML:icons.plus+' Lesson'}));
  app.appendChild(page);

  // Dialogs
  if (dialog) {
    if (dialog.type === 'addWord') renderAddWordDialog();
    if (dialog.type === 'addTask') renderAddTaskDialog();
    if (dialog.type === 'confirmDelete') renderConfirmDialog();
  }
}

function renderAddWordDialog() {
  const overlay = h('div',{className:'dialog-overlay',onMousedown:()=>{dialog=null;render();}});
  const form = h('form',{className:'dialog-card',onMousedown:e=>e.stopPropagation()});
  const zh = h('input',{className:'dialog-input',placeholder:'Chinese'});
  const pinyin = h('input',{className:'dialog-input',placeholder:'Pinyin'});
  const en = h('input',{className:'dialog-input',placeholder:'English meaning',required:true});
  form.appendChild(h('div',{className:'dialog-header'},h('h3',null,'Add word'),h('button',{type:'button',className:'dialog-close',onClick:()=>{dialog=null;render();},innerHTML:icons.x})));
  form.appendChild(zh); form.appendChild(pinyin); form.appendChild(en);
  form.appendChild(h('button',{className:'dialog-submit',type:'submit'},'Add word'));
  form.addEventListener('submit',e=>{
    e.preventDefault();
    if(!en.value.trim()) return;
    const lesson = state.lessons.find(l=>l.id===dialog.lessonId);
    if(lesson) { lesson.exercises.push(makeExercise(zh.value.trim(),pinyin.value.trim(),en.value.trim())); save(); }
    dialog=null; render();
  });
  overlay.appendChild(form);
  document.getElementById('app').appendChild(overlay);
}

function renderAddTaskDialog() {
  const overlay = h('div',{className:'dialog-overlay',onMousedown:()=>{dialog=null;render();}});
  const form = h('form',{className:'dialog-card',onMousedown:e=>e.stopPropagation()});
  const ta = h('textarea',{className:'dialog-textarea',placeholder:'Write the practice prompt...',required:true});
  form.appendChild(h('div',{className:'dialog-header'},h('h3',null,'Add task'),h('button',{type:'button',className:'dialog-close',onClick:()=>{dialog=null;render();},innerHTML:icons.x})));
  form.appendChild(ta);
  form.appendChild(h('button',{className:'dialog-submit',type:'submit'},'Add task'));
  form.addEventListener('submit',e=>{
    e.preventDefault();
    if(!ta.value.trim()) return;
    for(const l of state.lessons) for(const s of l.practiceSessions) if(s.id===dialog.sessionId) { s.tasks.push(makeTask(ta.value.trim())); save(); }
    dialog=null; render();
  });
  overlay.appendChild(form);
  document.getElementById('app').appendChild(overlay);
}

function renderConfirmDialog() {
  const overlay = h('div',{className:'dialog-overlay',onMousedown:()=>{dialog=null;render();}});
  const card = h('div',{className:'dialog-card',onMousedown:e=>e.stopPropagation()});
  card.appendChild(h('div',{className:'dialog-header'},h('h3',null,`Delete ${dialog.kind}?`),h('button',{type:'button',className:'dialog-close',onClick:()=>{dialog=null;render();},innerHTML:icons.x})));
  card.appendChild(h('p',{className:'dialog-message'},'This cannot be undone.'));
  const actions = h('div',{className:'dialog-actions'});
  actions.appendChild(h('button',{className:'dialog-cancel',onClick:()=>{dialog=null;render();}},'Cancel'));
  actions.appendChild(h('button',{className:'dialog-submit dialog-submit-danger',onClick:()=>{
    const {kind,id} = dialog;
    if(kind==='lesson') state.lessons = state.lessons.filter(l=>l.id!==id);
    if(kind==='word') state.lessons.forEach(l=>{l.exercises=l.exercises.filter(e=>e.id!==id);});
    if(kind==='session') state.lessons.forEach(l=>{l.practiceSessions=l.practiceSessions.filter(s=>s.id!==id);});
    if(kind==='task') state.lessons.forEach(l=>{l.practiceSessions.forEach(s=>{s.tasks=s.tasks.filter(t=>t.id!==id);});});
    save(); dialog=null; render();
  }},'Delete'));
  card.appendChild(actions);
  overlay.appendChild(card);
  document.getElementById('app').appendChild(overlay);
}

init();
</script>
</body>
</html>
