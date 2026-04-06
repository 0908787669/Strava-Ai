# Strava-Ai
Good 
<!DOCTYPE html>
<html lang="zh-TW">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Strava AI \u8dd1\u6b65\u5206\u6790</title>
<link href="https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&family=Noto+Sans+TC:wght@300;400;700;900&display=swap" rel="stylesheet">
<style>
:root {
  --orange: #FC4C02;
  --orange-dim: #c93d00;
  --dark: #0d0d0d;
  --dark2: #1a1a1a;
  --dark3: #252525;
  --card: #1e1e1e;
  --border: #333;
  --text: #f0f0f0;
  --muted: #888;
  --green: #39d98a;
  --blue: #4dabf7;
  --yellow: #ffd43b;
}

* { box-sizing: border-box; margin: 0; padding: 0; }

body {
  font-family: 'Noto Sans TC', sans-serif;
  background: var(--dark);
  color: var(--text);
  min-height: 100vh;
  overflow-x: hidden;
}

/* Header */
.header {
  position: relative;
  padding: 36px 20px 28px;
  text-align: center;
  border-bottom: 1px solid var(--border);
  background: linear-gradient(180deg, #1a0a00 0%, var(--dark) 100%);
  overflow: hidden;
}
.header::before {
  content: '';
  position: absolute;
  top: -60px; left: 50%; transform: translateX(-50%);
  width: 300px; height: 300px;
  background: radial-gradient(circle, rgba(252,76,2,0.2) 0%, transparent 70%);
  pointer-events: none;
}
.header-icon {
  font-size: 40px;
  display: block;
  margin-bottom: 8px;
  animation: pulse 2s ease-in-out infinite;
}
@keyframes pulse { 0%,100%{transform:scale(1)} 50%{transform:scale(1.08)} }

.header h1 {
  font-family: 'Space Mono', monospace;
  font-size: 22px;
  font-weight: 700;
  color: var(--orange);
  letter-spacing: 1px;
}
.header p { font-size: 12px; color: var(--muted); margin-top: 4px; letter-spacing: 2px; text-transform: uppercase; }

/* Container */
.container { padding: 16px; max-width: 640px; margin: 0 auto; }

/* Cards */
.card {
  background: var(--card);
  border: 1px solid var(--border);
  border-radius: 16px;
  padding: 20px;
  margin: 14px 0;
  position: relative;
  overflow: hidden;
}
.card::before {
  content: '';
  position: absolute;
  top: 0; left: 0; right: 0;
  height: 2px;
  background: linear-gradient(90deg, transparent, var(--orange), transparent);
}

.step-label {
  font-family: 'Space Mono', monospace;
  font-size: 10px;
  color: var(--orange);
  letter-spacing: 3px;
  text-transform: uppercase;
  margin-bottom: 6px;
}
.card h2 { font-size: 16px; font-weight: 700; margin-bottom: 14px; }

/* Inputs */
input {
  width: 100%;
  padding: 11px 14px;
  background: var(--dark3);
  border: 1px solid var(--border);
  border-radius: 8px;
  color: var(--text);
  font-size: 13px;
  margin: 5px 0;
  font-family: 'Space Mono', monospace;
  transition: border 0.2s;
}
input:focus { outline: none; border-color: var(--orange); }
input::placeholder { color: var(--muted); font-size: 12px; }

/* Buttons */
.btn {
  width: 100%;
  padding: 13px;
  border: none;
  border-radius: 10px;
  font-size: 14px;
  font-weight: 700;
  cursor: pointer;
  margin-top: 10px;
  transition: all 0.2s;
  font-family: 'Noto Sans TC', sans-serif;
  letter-spacing: 1px;
}
.btn-orange {
  background: var(--orange);
  color: white;
}
.btn-orange:hover { background: var(--orange-dim); transform: translateY(-1px); }
.btn-orange:active { transform: translateY(0); }
.btn-orange:disabled { background: #444; color: #666; cursor: not-allowed; transform: none; }

.btn-ai {
  background: linear-gradient(135deg, #6e40c9, #4dabf7);
  color: white;
  position: relative;
  overflow: hidden;
}
.btn-ai::after {
  content: '';
  position: absolute;
  top: -50%; left: -50%;
  width: 200%; height: 200%;
  background: linear-gradient(45deg, transparent 30%, rgba(255,255,255,0.1) 50%, transparent 70%);
  animation: shine 3s ease-in-out infinite;
}
@keyframes shine { 0%{transform:translateX(-100%) rotate(45deg)} 100%{transform:translateX(100%) rotate(45deg)} }
.btn-ai:disabled { background: #333; color: #666; cursor: not-allowed; }
.btn-ai:disabled::after { display: none; }

.btn-green { background: var(--green); color: #000; margin-top: 10px; }
.btn-green:hover { opacity: 0.9; }

/* Status */
.status {
  padding: 10px 14px;
  border-radius: 8px;
  margin: 8px 0;
  font-size: 13px;
  font-family: 'Space Mono', monospace;
}
.status-success { background: rgba(57,217,138,0.1); border: 1px solid rgba(57,217,138,0.3); color: var(--green); }
.status-error { background: rgba(255,80,80,0.1); border: 1px solid rgba(255,80,80,0.3); color: #ff6b6b; }
.status-info { background: rgba(77,171,247,0.1); border: 1px solid rgba(77,171,247,0.3); color: var(--blue); }

/* Token box */
.token-box {
  background: var(--dark3);
  border: 1px solid var(--border);
  border-radius: 8px;
  padding: 10px 12px;
  font-size: 11px;
  font-family: 'Space Mono', monospace;
  word-break: break-all;
  color: var(--green);
  margin-top: 10px;
}

/* Stats grid */
.stat-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 10px;
  margin: 12px 0;
}
.stat-box {
  background: var(--dark3);
  border: 1px solid var(--border);
  border-radius: 10px;
  padding: 14px 10px;
  text-align: center;
}
.stat-num {
  font-family: 'Space Mono', monospace;
  font-size: 24px;
  font-weight: 700;
  color: var(--orange);
}
.stat-label { font-size: 11px; color: var(--muted); margin-top: 3px; }

/* Table */
.table-wrap { overflow-x: auto; margin-top: 10px; border-radius: 10px; border: 1px solid var(--border); }
table { width: 100%; border-collapse: collapse; font-size: 12px; }
th {
  background: var(--dark3);
  padding: 10px 8px;
  text-align: left;
  font-family: 'Space Mono', monospace;
  font-size: 10px;
  color: var(--orange);
  letter-spacing: 1px;
  text-transform: uppercase;
  white-space: nowrap;
}
td { padding: 9px 8px; border-bottom: 1px solid var(--border); color: var(--text); white-space: nowrap; }
tr:last-child td { border-bottom: none; }
tr:hover td { background: rgba(252,76,2,0.05); }

/* AI Analysis */
.ai-result {
  background: var(--dark3);
  border: 1px solid #6e40c9;
  border-radius: 12px;
  padding: 16px;
  margin-top: 12px;
  font-size: 14px;
  line-height: 1.8;
  white-space: pre-wrap;
  color: var(--text);
  font-family: 'Noto Sans TC', sans-serif;
}
.ai-result strong { color: var(--yellow); }
.ai-label {
  font-family: 'Space Mono', monospace;
  font-size: 10px;
  color: #a78bfa;
  letter-spacing: 3px;
  text-transform: uppercase;
  margin-bottom: 8px;
}

.hidden { display: none; }
.divider { height: 1px; background: var(--border); margin: 14px 0; }

/* Progress bar */
.progress-bar {
  height: 4px;
  background: var(--dark3);
  border-radius: 2px;
  margin: 8px 0;
  overflow: hidden;
}
.progress-fill {
  height: 100%;
  background: linear-gradient(90deg, var(--orange), #ff8c00);
  border-radius: 2px;
  transition: width 0.3s ease;
  width: 0%;
}

/* Typing cursor */
.typing::after {
  content: '\u258b';
  animation: blink 1s step-end infinite;
  color: var(--orange);
}
@keyframes blink { 0%,100%{opacity:1} 50%{opacity:0} }
</style>
</head>
<body>

<div class="header">
  <span class="header-icon">\ud83c\udfc3</span>
  <h1>STRAVA AI ANALYZER</h1>
  <p>\u5fc3\u7387 \u00b7 \u914d\u901f \u00b7 \u8ddd\u96e2 \u00b7 AI \u8a13\u7df4\u5206\u6790</p>
</div>

<div class="container">

  <!-- Step 1 -->
  <div class="card">
    <div class="step-label">Step 01</div>
    <h2>\u63db\u53d6 Access Token</h2>
    <input id="clientId" placeholder="Client ID" value="221221">
    <input id="clientSecret" placeholder="Client Secret" value="c742d354256219fce8462250c83420aff8feef9b">
    <input id="authCode" placeholder="\u6388\u6b0a\u78bc\uff08code=\u5f8c\u9762\u90a3\u4e32\uff09">
    <button class="btn btn-orange" onclick="getToken()">\u63db\u53d6 Access Token</button>
    <div id="tokenStatus"></div>
    <div id="tokenResult" class="hidden">
      <div class="token-box" id="tokenBox"></div>
    </div>
  </div>

  <!-- Step 2 -->
  <div class="card">
    <div class="step-label">Step 02</div>
    <h2>\u6293\u53d6\u8dd1\u6b65\u8cc7\u6599</h2>
    <input id="accessToken" placeholder="Access Token\uff08Step 1 \u5b8c\u6210\u5f8c\u81ea\u52d5\u586b\u5165\uff09">
    <button class="btn btn-orange" onclick="fetchRuns()" id="fetchBtn">\u958b\u59cb\u6293\u53d6\u8cc7\u6599</button>
    <div id="progressWrap" class="hidden">
      <div class="progress-bar"><div class="progress-fill" id="progressFill"></div></div>
    </div>
    <div id="fetchStatus"></div>
  </div>

  <!-- Results -->
  <div class="card hidden" id="resultCard">
    <div class="step-label">Result</div>
    <h2>\u8dd1\u6b65\u7d00\u9304\u7e3d\u89bd</h2>
    <div class="stat-grid" id="statGrid"></div>
    <div class="table-wrap">
      <table>
        <thead>
          <tr>
            <th>\u65e5\u671f</th>
            <th>\u8ddd\u96e2 km</th>
            <th>\u914d\u901f</th>
            <th>\u5fc3\u7387</th>
            <th>\u6642\u9593 \u5206</th>
          </tr>
        </thead>
        <tbody id="runBody"></tbody>
      </table>
    </div>
    <button class="btn btn-green" onclick="downloadCSV()">\u2b07 \u4e0b\u8f09 CSV</button>
  </div>

  <!-- AI Analysis -->
  <div class="card hidden" id="aiCard">
    <div class="step-label">Step 03</div>
    <h2>\u2728 AI \u8a13\u7df4\u5206\u6790</h2>
    <p style="font-size:13px; color:var(--muted); margin-bottom:12px;">\u8b93 AI \u5e6b\u4f60\u5206\u6790\u8dd1\u6b65\u8da8\u52e2\u3001\u914d\u901f\u5fc3\u7387\u8868\u73fe\u3001\u4e26\u7d66\u51fa\u8a13\u7df4\u5efa\u8b70</p>
    <button class="btn btn-ai" onclick="runAIAnalysis()" id="aiBtn">\ud83e\udd16 \u958b\u59cb AI \u5206\u6790</button>
    <div id="aiStatus"></div>
    <div id="aiResultWrap" class="hidden">
      <div class="ai-label">AI \u5206\u6790\u5831\u544a</div>
      <div class="ai-result" id="aiResult"></div>
    </div>
  </div>

</div>

<script>
let allRuns = [];

// \u2500\u2500 Token \u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500
async function getToken() {
  const clientId = document.getElementById('clientId').value.trim();
  const clientSecret = document.getElementById('clientSecret').value.trim();
  const authCode = document.getElementById('authCode').value.trim();
  const statusEl = document.getElementById('tokenStatus');

  if (!authCode) {
    statusEl.innerHTML = '<div class="status status-error">\u26a0 \u8acb\u586b\u5165\u6388\u6b0a\u78bc</div>';
    return;
  }
  statusEl.innerHTML = '<div class="status status-info">\u23f3 \u63db\u53d6\u4e2d...</div>';

  try {
    const res = await fetch('https://www.strava.com/oauth/token', {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({ client_id: clientId, client_secret: clientSecret, code: authCode, grant_type: 'authorization_code' })
    });
    const data = await res.json();
    if (data.access_token) {
      statusEl.innerHTML = `<div class="status status-success">\u2713 Token \u53d6\u5f97\u6210\u529f\uff5c\u7bc4\u570d\uff1a${data.scope || 'N/A'}</div>`;
      document.getElementById('tokenBox').textContent = data.access_token;
      document.getElementById('tokenResult').classList.remove('hidden');
      document.getElementById('accessToken').value = data.access_token;
    } else {
      statusEl.innerHTML = `<div class="status status-error">\u2717 ${data.message || '\u6388\u6b0a\u78bc\u5df2\u5931\u6548\uff0c\u8acb\u91cd\u65b0\u53d6\u5f97'}</div>`;
    }
  } catch (e) {
    statusEl.innerHTML = `<div class="status status-error">\u2717 \u7db2\u8def\u932f\u8aa4\uff1a${e.message}</div>`;
  }
}

// \u2500\u2500 Pace \u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500
function mpsToMinPerKm(mps) {
  if (!mps || mps <= 0) return '-';
  const s = 1000 / mps;
  return `${Math.floor(s/60)}'${String(Math.round(s%60)).padStart(2,'0')}"`;
}

// \u2500\u2500 Fetch Runs \u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500
async function fetchRuns() {
  const token = document.getElementById('accessToken').value.trim();
  const statusEl = document.getElementById('fetchStatus');
  if (!token) { statusEl.innerHTML = '<div class="status status-error">\u26a0 \u8acb\u5148\u53d6\u5f97 Access Token</div>'; return; }

  document.getElementById('fetchBtn').disabled = true;
  document.getElementById('progressWrap').classList.remove('hidden');
  statusEl.innerHTML = '<div class="status status-info">\u23f3 \u6293\u53d6\u6d3b\u52d5\u5217\u8868...</div>';

  const headers = { Authorization: 'Bearer ' + token };
  let activities = [], page = 1;

  try {
    while (true) {
      const res = await fetch(`https://www.strava.com/api/v3/athlete/activities?per_page=200&page=${page}`, { headers });
      const data = await res.json();
      if (!Array.isArray(data) || !data.length) break;
      activities = activities.concat(data);
      page++;
      if (data.length < 200) break;
    }

    const runs = activities.filter(a => a.type === 'Run' || a.sport_type === 'Run');
    allRuns = [];

    for (let i = 0; i < runs.length; i++) {
      const run = runs[i];
      const pct = Math.round(((i+1)/runs.length)*100);
      document.getElementById('progressFill').style.width = pct + '%';
      statusEl.innerHTML = `<div class="status status-info">\u23f3 ${i+1}/${runs.length}\uff1a${run.name}</div>`;

      allRuns.push({
        date: (run.start_date_local || '').slice(0,10),
        name: run.name,
        distance: (run.distance/1000).toFixed(2),
        pace: mpsToMinPerKm(run.average_speed),
        paceRaw: run.average_speed || 0,
        hr: run.average_heartrate ? Math.round(run.average_heartrate) : '-',
        hrRaw: run.average_heartrate || 0,
        time: (run.moving_time/60).toFixed(1),
        elevation: run.total_elevation_gain || 0
      });

      if (i % 5 === 0) renderTable();
      await new Promise(r => setTimeout(r, 80));
    }

    renderTable();
    renderStats();
    document.getElementById('resultCard').classList.remove('hidden');
    document.getElementById('aiCard').classList.remove('hidden');
    statusEl.innerHTML = `<div class="status status-success">\u2713 \u5b8c\u6210\uff01\u5171 ${allRuns.length} \u7b46\u8dd1\u6b65\u8cc7\u6599</div>`;
    document.getElementById('progressFill').style.width = '100%';

  } catch(e) {
    statusEl.innerHTML = `<div class="status status-error">\u2717 \u932f\u8aa4\uff1a${e.message}</div>`;
  }
  document.getElementById('fetchBtn').disabled = false;
}

// \u2500\u2500 Render \u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500\u2500
function renderTable() {
  document.getElementById('runBody').innerHTML = allRuns.map(r => `
    <tr>
      <td>${r.date}</td>
      <td>${r.distance}</td>
      <td>${r.pace}</td>
      <td>${r.hr !== '-' ? r.hr + ' bpm' : '-'}</td>
      <td>${r.time}</td>
    </tr>`).join('');
  document.getElementById('resultCard').classList.remove('hidden');
}

function renderStats() {
  const totalKm = allRuns.reduce((s,r) => s+parseFloat(r.distance), 0).toFixed(1);
  const withHr
