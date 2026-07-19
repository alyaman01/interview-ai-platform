[index.html](https://github.com/user-attachments/files/30168155/index.html)
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>🌍 Personal Environmental Health Analyzer</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Fraunces:opsz,wght@9..144,400;9..144,500;9..144,600;9..144,700&family=Inter:wght@400;500;600;700;800&family=JetBrains+Mono:wght@400;500;600;700&display=swap" rel="stylesheet">
<script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.4.4/chart.umd.min.js"></script>
<style>
:root{
  --bg-void:#0A0E17;
  --bg-panel:#121A2B;
  --bg-panel-2:#1A2439;
  --bg-panel-3:#212D47;
  --accent-air:#29D9C2;
  --accent-air-dim:#1B9E8E;
  --accent-water:#F2B84B;
  --accent-water-dim:#C99530;
  --ink-primary:#EAF0FA;
  --ink-muted:#8CA0C2;
  --ink-faint:#5B6C8C;
  --line:rgba(140,160,194,0.14);
  --line-strong:rgba(140,160,194,0.28);
  --good:#34D399;
  --satisfactory:#A3E635;
  --moderate:#FACC15;
  --poor:#FB923C;
  --verypoor:#EF4444;
  --severe:#7F1D1D;
  --radius:16px;
  --radius-sm:10px;
  --shadow-lift: 0 20px 50px -20px rgba(0,0,0,0.6);
}
*{box-sizing:border-box;}
html{scroll-behavior:smooth;}
body{
  margin:0;
  background:
    radial-gradient(1100px 600px at 12% -10%, rgba(41,217,194,0.10), transparent 60%),
    radial-gradient(900px 500px at 90% 0%, rgba(242,184,75,0.08), transparent 55%),
    linear-gradient(180deg,#0A0E17 0%, #0B111C 40%, #0A0E17 100%);
  color:var(--ink-primary);
  font-family:'Inter',system-ui,sans-serif;
  min-height:100vh;
  -webkit-font-smoothing:antialiased;
}
.mono{font-family:'JetBrains Mono',monospace;}
.display{font-family:'Fraunces',serif;}
.wrap{max-width:1280px;margin:0 auto;padding:0 24px;}

@media (prefers-reduced-motion: reduce){
  *{animation-duration:0.001ms !important; transition-duration:0.001ms !important;}
}

/* ---------- Top bar ---------- */
.topbar{
  position:sticky; top:0; z-index:50;
  background:rgba(10,14,23,0.78);
  backdrop-filter:blur(14px) saturate(140%);
  border-bottom:1px solid var(--line);
}
.topbar-inner{display:flex;align-items:center;justify-content:space-between;padding:14px 24px;max-width:1280px;margin:0 auto;}
.brand{display:flex;align-items:center;gap:10px;}
.brand-mark{width:34px;height:34px;border-radius:10px;background:linear-gradient(135deg,var(--accent-air),var(--accent-water));display:flex;align-items:center;justify-content:center;font-size:18px;}
.brand-text{font-family:'Fraunces',serif;font-weight:600;font-size:17px;letter-spacing:0.2px;}
.live-badge{display:flex;align-items:center;gap:8px;font-size:12px;color:var(--ink-muted);}
.pulse-dot{width:8px;height:8px;border-radius:50%;background:var(--good);box-shadow:0 0 0 0 rgba(52,211,153,0.6);animation:pulseDot 2s infinite;}
@keyframes pulseDot{0%{box-shadow:0 0 0 0 rgba(52,211,153,0.55);}70%{box-shadow:0 0 0 8px rgba(52,211,153,0);}100%{box-shadow:0 0 0 0 rgba(52,211,153,0);}}

/* ---------- Hero ---------- */
.hero{padding:52px 0 28px;}
.eyebrow{font-size:12px;letter-spacing:2.5px;text-transform:uppercase;color:var(--accent-air);font-weight:600;margin-bottom:14px;display:flex;align-items:center;gap:8px;}
.eyebrow::before{content:'';width:22px;height:1px;background:var(--accent-air);display:inline-block;}
h1.hero-title{font-family:'Fraunces',serif;font-weight:600;font-size:clamp(30px,4.4vw,52px);line-height:1.05;margin:0 0 14px;letter-spacing:-0.5px;}
.hero-title em{font-style:normal;background:linear-gradient(90deg,var(--accent-air),var(--accent-water));-webkit-background-clip:text;background-clip:text;color:transparent;}
.hero-sub{color:var(--ink-muted);font-size:16px;line-height:1.6;max-width:640px;margin:0 0 22px;}
.hero-tags{display:flex;flex-wrap:wrap;gap:10px;}
.tag{font-size:12px;padding:7px 12px;border-radius:100px;border:1px solid var(--line-strong);color:var(--ink-muted);background:var(--bg-panel);}
.tag b{color:var(--ink-primary);}

/* ---------- Metrics strip ---------- */
.metrics-grid{display:grid;grid-template-columns:repeat(5,1fr);gap:14px;margin:30px 0;}
.metric-card{
  background:linear-gradient(160deg,var(--bg-panel), var(--bg-panel-2));
  border:1px solid var(--line);border-radius:var(--radius);
  padding:20px 18px; position:relative; overflow:hidden;
  transition:transform .25s ease, border-color .25s ease;
}
.metric-card:hover{transform:translateY(-3px);border-color:var(--line-strong);}
.metric-card::after{content:'';position:absolute;inset:0;background:linear-gradient(120deg,transparent 40%, rgba(255,255,255,0.03) 50%, transparent 60%);}
.metric-label{font-size:11px;text-transform:uppercase;letter-spacing:1.2px;color:var(--ink-faint);margin-bottom:10px;font-weight:600;}
.metric-value{font-family:'Fraunces',serif;font-size:30px;font-weight:600;line-height:1;}
.metric-sub{margin-top:8px;font-size:12.5px;color:var(--ink-muted);}
.metric-value.air{color:var(--accent-air);}
.metric-value.water{color:var(--accent-water);}

/* ---------- Filters ---------- */
.filters-bar{
  background:var(--bg-panel);border:1px solid var(--line);border-radius:var(--radius);
  padding:18px 20px;margin:24px 0 34px;display:flex;flex-wrap:wrap;gap:22px;align-items:flex-end;
}
.filter-group{display:flex;flex-direction:column;gap:8px;min-width:150px;}
.filter-group label{font-size:11px;text-transform:uppercase;letter-spacing:1px;color:var(--ink-faint);font-weight:600;}
select, .rng-wrap input[type=range]{accent-color:var(--accent-air);}
select{
  background:var(--bg-panel-3);color:var(--ink-primary);border:1px solid var(--line-strong);
  border-radius:var(--radius-sm);padding:9px 10px;font-size:13.5px;font-family:'Inter',sans-serif;
}
.segmented{display:flex;background:var(--bg-panel-3);border-radius:var(--radius-sm);padding:3px;border:1px solid var(--line-strong);}
.segmented button{
  border:none;background:transparent;color:var(--ink-muted);padding:7px 13px;border-radius:8px;
  font-size:12.5px;font-weight:600;cursor:pointer;transition:all .2s ease;font-family:'Inter',sans-serif;
}
.segmented button.active{background:linear-gradient(135deg,var(--accent-air),var(--accent-air-dim));color:#04211D;}
.rng-wrap{display:flex;align-items:center;gap:10px;}
.rng-wrap input[type=range]{width:110px;}
.rng-val{font-size:12px;color:var(--ink-muted);}
.chip-toggle{display:flex;align-items:center;gap:8px;font-size:13px;color:var(--ink-muted);cursor:pointer;user-select:none;}
.chip-toggle input{accent-color:var(--accent-water);width:15px;height:15px;}
.filter-reset{margin-left:auto;align-self:center;background:none;border:1px solid var(--line-strong);color:var(--ink-muted);border-radius:100px;padding:9px 16px;font-size:12.5px;cursor:pointer;transition:.2s;font-family:'Inter',sans-serif;}
.filter-reset:hover{border-color:var(--accent-air);color:var(--accent-air);}

/* ---------- Section headers ---------- */
.section-head{display:flex;align-items:baseline;justify-content:space-between;margin:48px 0 18px;flex-wrap:wrap;gap:8px;}
.section-title{font-family:'Fraunces',serif;font-size:24px;font-weight:600;}
.section-note{font-size:12.5px;color:var(--ink-faint);}

/* ---------- Charts grid ---------- */
.charts-grid{display:grid;grid-template-columns:repeat(2,1fr);gap:16px;}
.chart-card{background:var(--bg-panel);border:1px solid var(--line);border-radius:var(--radius);padding:18px;}
.chart-card.wide{grid-column:1/-1;}
.chart-card h4{margin:0 0 4px;font-size:14px;font-weight:600;}
.chart-card p.desc{margin:0 0 14px;font-size:12px;color:var(--ink-faint);}
.chart-holder{height:230px;position:relative;}
.chart-holder.tall{height:280px;}

/* ---------- City cards ---------- */
.cities-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:14px;}
.city-card{
  background:linear-gradient(160deg,var(--bg-panel),var(--bg-panel-2));
  border:1px solid var(--line);border-radius:var(--radius);padding:18px;cursor:pointer;
  transition:transform .2s ease, border-color .2s ease, box-shadow .2s ease;position:relative;overflow:hidden;
}
.city-card:hover{transform:translateY(-4px);border-color:var(--accent-air);box-shadow:var(--shadow-lift);}
.city-card.selected{border-color:var(--accent-water);box-shadow:0 0 0 1px var(--accent-water);}
.city-card-top{display:flex;justify-content:space-between;align-items:flex-start;margin-bottom:12px;}
.city-name{font-family:'Fraunces',serif;font-weight:600;font-size:17px;}
.city-state{font-size:11px;color:var(--ink-faint);}
.badge{font-size:10.5px;font-weight:700;padding:4px 9px;border-radius:100px;text-transform:uppercase;letter-spacing:0.4px;}
.city-aqi-row{display:flex;align-items:baseline;gap:6px;margin:8px 0 14px;}
.city-aqi-num{font-family:'JetBrains Mono',monospace;font-size:30px;font-weight:700;}
.city-aqi-label{font-size:11px;color:var(--ink-faint);}
.city-metrics{display:grid;grid-template-columns:1fr 1fr;gap:8px;margin-bottom:12px;}
.mini-stat{background:rgba(255,255,255,0.03);border-radius:8px;padding:7px 9px;}
.mini-stat .k{font-size:9.5px;text-transform:uppercase;color:var(--ink-faint);letter-spacing:0.5px;}
.mini-stat .v{font-family:'JetBrains Mono',monospace;font-size:13px;margin-top:2px;}
.score-bar-track{height:6px;border-radius:100px;background:rgba(255,255,255,0.06);overflow:hidden;margin-top:4px;}
.score-bar-fill{height:100%;border-radius:100px;}
.city-card-footer{display:flex;justify-content:space-between;font-size:11px;color:var(--ink-faint);margin-top:10px;}

/* ---------- Report card ---------- */
.report-shell{background:linear-gradient(160deg,var(--bg-panel),var(--bg-panel-2));border:1px solid var(--line);border-radius:20px;padding:28px;}
.report-select-row{display:flex;gap:16px;align-items:center;flex-wrap:wrap;margin-bottom:22px;}
.report-columns{display:grid;grid-template-columns:1fr 1fr;gap:22px;}
.report-columns.single{grid-template-columns:1fr;}
.report-panel{background:var(--bg-panel-3);border:1px solid var(--line);border-radius:var(--radius);padding:22px;}
.report-panel-head{display:flex;justify-content:space-between;align-items:flex-start;margin-bottom:18px;}
.report-city-name{font-family:'Fraunces',serif;font-size:24px;font-weight:600;}
.report-city-meta{font-size:12px;color:var(--ink-muted);margin-top:4px;}

.gauge-row{display:flex;gap:16px;margin-bottom:20px;}
.gauge-box{flex:1;background:rgba(255,255,255,0.03);border-radius:14px;padding:16px;text-align:center;}
.gauge-svg{width:110px;height:110px;margin:0 auto;}
.gauge-num{font-family:'JetBrains Mono',monospace;font-weight:700;font-size:22px;}
.gauge-label{font-size:10.5px;text-transform:uppercase;letter-spacing:0.6px;color:var(--ink-faint);margin-top:6px;}

.grade-row{display:flex;gap:10px;margin-bottom:20px;flex-wrap:wrap;}
.grade-pill{flex:1;min-width:75px;text-align:center;background:rgba(255,255,255,0.03);border-radius:12px;padding:12px 8px;}
.grade-letter{font-family:'Fraunces',serif;font-size:26px;font-weight:700;}
.grade-name{font-size:10px;color:var(--ink-faint);text-transform:uppercase;letter-spacing:0.5px;margin-top:4px;}

.impact-block h5{font-size:12px;text-transform:uppercase;letter-spacing:1px;color:var(--accent-air);margin:18px 0 10px;}
.impact-block.water h5{color:var(--accent-water);}
.impact-row{display:flex;gap:10px;padding:9px 0;border-top:1px solid var(--line);font-size:13px;line-height:1.5;}
.impact-row:first-of-type{border-top:none;}
.impact-emoji{font-size:15px;flex-shrink:0;margin-top:1px;}
.impact-text b{color:var(--ink-primary);}
.impact-text span{color:var(--ink-muted);}

/* ---------- Insights ---------- */
.insights-grid{display:grid;grid-template-columns:1fr 1fr;gap:16px;}
.insight-card{background:var(--bg-panel);border:1px solid var(--line);border-radius:var(--radius);padding:20px;}
.insight-card h4{margin:0 0 12px;font-size:13.5px;display:flex;align-items:center;gap:8px;}
.rank-list{list-style:none;margin:0;padding:0;display:flex;flex-direction:column;gap:8px;}
.rank-list li{display:flex;justify-content:space-between;align-items:center;font-size:13px;background:rgba(255,255,255,0.03);padding:9px 12px;border-radius:9px;}
.rank-list .rk{color:var(--ink-faint);font-family:'JetBrains Mono',monospace;font-size:11px;margin-right:8px;}
.callout{font-size:13px;line-height:1.65;color:var(--ink-muted);}
.callout b{color:var(--ink-primary);}
.action-list{margin:0;padding-left:18px;font-size:13px;line-height:1.8;color:var(--ink-muted);}
.action-list li::marker{color:var(--accent-water);}

/* ---------- Recommendations ---------- */
.tabs{display:flex;gap:8px;flex-wrap:wrap;margin-bottom:18px;}
.tab-btn{background:var(--bg-panel-3);border:1px solid var(--line-strong);color:var(--ink-muted);padding:9px 16px;border-radius:100px;font-size:12.5px;font-weight:600;cursor:pointer;transition:.2s;}
.tab-btn.active{background:linear-gradient(135deg,var(--accent-water),var(--accent-water-dim));color:#2A1B02;border-color:transparent;}
.tab-panel{display:none;background:var(--bg-panel);border:1px solid var(--line);border-radius:var(--radius);padding:22px;}
.tab-panel.active{display:grid;grid-template-columns:1fr 1fr;gap:20px;}
.rec-col h5{font-size:12px;text-transform:uppercase;letter-spacing:1px;color:var(--accent-air);margin:0 0 10px;}
.rec-col ul{margin:0;padding-left:18px;font-size:13.5px;line-height:1.85;color:var(--ink-muted);}
.rec-col ul li::marker{color:var(--accent-air);}

/* ---------- Executive summary ---------- */
.exec-card{background:linear-gradient(135deg, rgba(41,217,194,0.08), rgba(242,184,75,0.06));border:1px solid var(--line-strong);border-radius:20px;padding:30px;}
.exec-card p{font-size:14.5px;line-height:1.8;color:var(--ink-muted);margin:0 0 12px;}
.exec-card p b{color:var(--ink-primary);}
.exec-card p:last-child{margin-bottom:0;}

/* ---------- Footer / methodology ---------- */
.footer{margin:48px 0 30px;padding-top:24px;border-top:1px solid var(--line);}
.footer h5{font-size:12px;text-transform:uppercase;letter-spacing:1px;color:var(--ink-faint);margin:0 0 10px;}
.footer p, .footer li{font-size:12px;color:var(--ink-faint);line-height:1.8;}
.footer ul{margin:0;padding-left:16px;}
.share-strip{display:flex;justify-content:space-between;align-items:center;gap:16px;flex-wrap:wrap;background:var(--bg-panel);border:1px solid var(--line);border-radius:var(--radius);padding:18px 22px;margin-top:16px;}
.share-strip .msg{font-size:13px;color:var(--ink-muted);}
.share-btn{background:linear-gradient(135deg,var(--accent-air),var(--accent-water));border:none;color:#04211D;font-weight:700;font-size:13px;padding:11px 20px;border-radius:100px;cursor:pointer;}

/* ---------- Category badge colors ---------- */
.bg-good{background:rgba(52,211,153,0.16);color:var(--good);}
.bg-satisfactory{background:rgba(163,230,53,0.16);color:var(--satisfactory);}
.bg-moderate{background:rgba(250,204,21,0.16);color:var(--moderate);}
.bg-poor{background:rgba(251,146,60,0.16);color:var(--poor);}
.bg-verypoor{background:rgba(239,68,68,0.16);color:var(--verypoor);}
.bg-severe{background:rgba(127,29,29,0.35);color:#FCA5A5;}

/* ---------- Responsive ---------- */
@media (max-width:1080px){
  .metrics-grid{grid-template-columns:repeat(3,1fr);}
  .cities-grid{grid-template-columns:repeat(2,1fr);}
  .charts-grid{grid-template-columns:1fr;}
  .report-columns{grid-template-columns:1fr;}
  .insights-grid{grid-template-columns:1fr;}
  .tab-panel.active{grid-template-columns:1fr;}
}
@media (max-width:640px){
  .metrics-grid{grid-template-columns:repeat(2,1fr);}
  .cities-grid{grid-template-columns:1fr;}
  .gauge-row{flex-wrap:wrap;}
  .filters-bar{flex-direction:column;align-items:stretch;}
  .filter-reset{margin-left:0;}
}

/* focus visibility */
button:focus-visible, select:focus-visible, input:focus-visible, .city-card:focus-visible{
  outline:2px solid var(--accent-air); outline-offset:2px;
}
</style>
</head>
<body>

<div class="topbar">
  <div class="topbar-inner">
    <div class="brand">
      <div class="brand-mark">🌍</div>
      <div class="brand-text">Environmental Health Analyzer</div>
    </div>
    <div class="live-badge"><span class="pulse-dot"></span> <span id="topbarUpdated">Live snapshot</span></div>
  </div>
</div>

<div class="wrap">

  <!-- HERO -->
  <div class="hero">
    <div class="eyebrow">Personal Environmental Health Report</div>
    <h1 class="hero-title">What your city's air <em>and water</em><br>are doing to your body.</h1>
    <p class="hero-sub">A real-time comparison of air quality and water quality across 8 major Indian cities — translated into lung, skin, hair and long-term health risk, with a personal score for the city you live in.</p>
    <div class="hero-tags">
      <div class="tag">📍 Default city: <b>New Delhi</b></div>
      <div class="tag" id="heroCityCount">🏙️ <b>8</b> cities analyzed</div>
      <div class="tag">🕒 Data as of <b id="heroTimestamp">18 Jul 2026, 17:01 IST</b></div>
    </div>
  </div>

  <!-- METRICS -->
  <div class="metrics-grid" id="metricsGrid"></div>

  <!-- FILTERS -->
  <div class="filters-bar">
    <div class="filter-group">
      <label>Focus city (report card)</label>
      <select id="citySelect"></select>
    </div>
    <div class="filter-group">
      <label>Health-risk filter</label>
      <select id="riskFilter">
        <option value="all">All risk levels</option>
        <option value="low">🟢 Low risk</option>
        <option value="moderate">🟡 Moderate risk</option>
        <option value="high">🔴 High risk</option>
      </select>
    </div>
    <div class="filter-group">
      <label>Rank chart by</label>
      <div class="segmented" id="pollutantSeg">
        <button data-p="aqi" class="active">AQI</button>
        <button data-p="pm25">PM2.5</button>
        <button data-p="pm10">PM10</button>
      </div>
    </div>
    <div class="filter-group">
      <label>AQI range: <span class="rng-val" id="aqiRangeLabel">0 – 300</span></label>
      <div class="rng-wrap">
        <input type="range" id="aqiMin" min="0" max="300" value="0" step="5">
        <input type="range" id="aqiMax" min="0" max="300" value="300" step="5">
      </div>
    </div>
    <div class="filter-group">
      <label>&nbsp;</label>
      <label class="chip-toggle"><input type="checkbox" id="compareToggle"> Compare two cities</label>
    </div>
    <div class="filter-group" id="compareGroup" style="display:none;">
      <label>Compare against</label>
      <select id="compareSelect"></select>
    </div>
    <button class="filter-reset" id="resetFilters">Reset filters</button>
  </div>

  <!-- CHARTS -->
  <div class="section-head">
    <div class="section-title">📈 Comparative visualizations</div>
    <div class="section-note" id="chartsNote">Reflecting current filters</div>
  </div>
  <div class="charts-grid">
    <div class="chart-card">
      <h4>AQI comparison</h4>
      <p class="desc">Air Quality Index across filtered cities, colour-coded by category.</p>
      <div class="chart-holder"><canvas id="aqiChart"></canvas></div>
    </div>
    <div class="chart-card">
      <h4>AQI distribution</h4>
      <p class="desc">How many cities fall into each air-quality category.</p>
      <div class="chart-holder"><canvas id="distChart"></canvas></div>
    </div>
    <div class="chart-card">
      <h4>PM2.5 comparison (µg/m³)</h4>
      <p class="desc">Fine particulate matter — the pollutant with the deepest lung penetration. <span id="pm25Note"></span></p>
      <div class="chart-holder"><canvas id="pm25Chart"></canvas></div>
    </div>
    <div class="chart-card">
      <h4>PM10 comparison (µg/m³)</h4>
      <p class="desc">Coarse particulate matter — dust, construction and road pollution. <span id="pm10Note"></span></p>
      <div class="chart-holder"><canvas id="pm10Chart"></canvas></div>
    </div>
    <div class="chart-card wide">
      <h4>City ranking</h4>
      <p class="desc">Cities ranked from best to worst on the metric selected above.</p>
      <div class="chart-holder tall"><canvas id="rankChart"></canvas></div>
    </div>
  </div>

  <!-- CITY CARDS -->
  <div class="section-head">
    <div class="section-title">📋 City detail cards</div>
    <div class="section-note">Click a card to load it into your personal report card below</div>
  </div>
  <div class="cities-grid" id="cityCards"></div>

  <!-- REPORT CARD -->
  <div class="section-head">
    <div class="section-title">🧾 Personal environmental health report card</div>
    <div class="section-note">Air impact on your body + water impact on hair &amp; skin</div>
  </div>
  <div class="report-shell">
    <div id="reportColumns" class="report-columns single"></div>
  </div>

  <!-- INSIGHTS -->
  <div class="section-head">
    <div class="section-title">🔍 Insights panel</div>
    <div class="section-note">Patterns pulled from today's dataset</div>
  </div>
  <div class="insights-grid" id="insightsGrid"></div>

  <!-- RECOMMENDATIONS -->
  <div class="section-head">
    <div class="section-title">✅ Personalized recommendations</div>
    <div class="section-note">Tailored to <span id="recCityLabel">New Delhi</span></div>
  </div>
  <div class="tabs" id="recTabs"></div>
  <div id="recPanels"></div>

  <!-- EXEC SUMMARY -->
  <div class="section-head">
    <div class="section-title">🧠 Executive summary</div>
  </div>
  <div class="exec-card" id="execSummary"></div>

  <!-- SHARE -->
  <div class="share-strip">
    <div class="msg">💡 Screenshot your Personal Report Card above — sized and styled for a LinkedIn post on urban health.</div>
    <button class="share-btn" onclick="window.print()">Export / Print report</button>
  </div>

  <!-- FOOTER -->
  <div class="footer">
    <h5>Data sources &amp; methodology</h5>
    <ul>
      <li><b>Live AQI, PM2.5 &amp; PM10 readings</b> for New Delhi (AQI 111, PM2.5 27 µg/m³, PM10 175 µg/m³) and the same-timestamp 7-city snapshot (Ahmedabad, Bangalore, Chennai, Hyderabad, Kolkata, Mumbai, Pune) sourced from aqi.in's India dashboard, US EPA AQI standard, captured 2026‑07‑18 17:01 IST.</li>
      <li>Where a city's PM2.5 / PM10 was not directly reported in that snapshot, it is <b>estimated from the reported AQI using the reverse US EPA breakpoint formula</b> and flagged with an asterisk (*) in charts and cards — this is a modelled value, not a direct sensor reading.</li>
      <li><b>Water quality scores</b> are directional estimates (0–100) informed by the Bureau of Indian Standards (BIS) tap-water testing of Indian state capitals (Mumbai ranked best, Delhi ranked worst on 19 tested parameters) plus subsequent regional water-infrastructure reporting through 2025–26. No single live, official, city-level daily water quality index exists for India, so these scores should be read as relative, illustrative benchmarks rather than a real-time lab reading.</li>
      <li>AQI category bands (Good / Satisfactory / Moderate / Poor / Very Poor / Severe) are mapped 1:1 onto the underlying US EPA AQI bands (0–50 / 51–100 / 101–150 / 151–200 / 201–300 / 301+) for a familiar Indian-style labelling scheme.</li>
      <li>Air, Water, Overall, Hair-risk and Skin-risk scores are computed client-side in this dashboard from the AQI and water-quality inputs above (Overall = 60% Air + 40% Water); they are analytical estimates for personal awareness, not a medical or regulatory diagnosis.</li>
      <li>Data quality: all 8 cities had a complete AQI reading; 0 missing AQI values; 7 of 8 cities had modelled (not directly sensed) PM2.5/PM10; water-quality figures are relative estimates for all 8 cities as noted above.</li>
    </ul>
  </div>

</div>

<script>
/* ============ DATA ============ */
const rawCities = [
  {name:"New Delhi", state:"Delhi", aqi:111, pm25:27, pm25Est:false, pm10:175, pm10Est:false, temp:37, humidity:45, waterScore:42, updated:"18 Jul 2026, 17:01 IST"},
  {name:"Mumbai", state:"Maharashtra", aqi:60, pm25:13.9, pm25Est:true, pm10:73, pm10Est:true, temp:29, humidity:79, waterScore:88, updated:"18 Jul 2026, 22:21 IST"},
  {name:"Bangalore", state:"Karnataka", aqi:66, pm25:17.2, pm25Est:true, pm10:85, pm10Est:true, temp:26, humidity:74, waterScore:74, updated:"18 Jul 2026, 17:01 IST"},
  {name:"Chennai", state:"Tamil Nadu", aqi:87, pm25:28.4, pm25Est:true, pm10:128, pm10Est:true, temp:32, humidity:71, waterScore:65, updated:"18 Jul 2026, 17:01 IST"},
  {name:"Kolkata", state:"West Bengal", aqi:59, pm25:13.4, pm25Est:true, pm10:71, pm10Est:true, temp:31, humidity:79, waterScore:68, updated:"18 Jul 2026, 17:01 IST"},
  {name:"Hyderabad", state:"Telangana", aqi:65, pm25:16.6, pm25Est:true, pm10:83, pm10Est:true, temp:28, humidity:66, waterScore:70, updated:"18 Jul 2026, 17:01 IST"},
  {name:"Pune", state:"Maharashtra", aqi:57, pm25:12.3, pm25Est:true, pm10:67, pm10Est:true, temp:26, humidity:70, waterScore:76, updated:"18 Jul 2026, 17:01 IST"},
  {name:"Ahmedabad", state:"Gujarat", aqi:78, pm25:23.6, pm25Est:true, pm10:110, pm10Est:true, temp:32, humidity:49, waterScore:63, updated:"18 Jul 2026, 17:01 IST"},
];

/* ============ DERIVED SCORE HELPERS ============ */
function aqiCategory(aqi){
  if(aqi<=50) return {label:"Good", cls:"bg-good", color:"#34D399"};
  if(aqi<=100) return {label:"Satisfactory", cls:"bg-satisfactory", color:"#A3E635"};
  if(aqi<=150) return {label:"Moderate", cls:"bg-moderate", color:"#FACC15"};
  if(aqi<=200) return {label:"Poor", cls:"bg-poor", color:"#FB923C"};
  if(aqi<=300) return {label:"Very Poor", cls:"bg-verypoor", color:"#EF4444"};
  return {label:"Severe", cls:"bg-severe", color:"#7F1D1D"};
}
function airScore(aqi){ return Math.max(0, Math.min(100, Math.round(100 - aqi*0.35))); }
function overallScore(c){ return Math.round(0.6*airScore(c.aqi) + 0.4*c.waterScore); }
function hairScore(c){ return Math.round(0.7*c.waterScore + 0.3*airScore(c.aqi)); }
function skinScore(c){ return Math.round(0.5*c.waterScore + 0.5*airScore(c.aqi)); }
function letterGrade(score){
  if(score>=90) return "A"; if(score>=75) return "B"; if(score>=60) return "C"; if(score>=45) return "D"; return "F";
}
function riskTier(score, goodAt75){
  // returns low/moderate/high
  if(goodAt75){ if(score>=75) return "low"; if(score>=55) return "moderate"; return "high"; }
  return score>=75?"low":score>=55?"moderate":"high";
}
function riskEmoji(tier){ return tier==="low"?"🟢":tier==="moderate"?"🟡":"🔴"; }
function riskWord(tier){ return tier==="low"?"Low":tier==="moderate"?"Moderate":"High"; }
function overallRiskTier(c){ return riskTier(overallScore(c), true); }

/* enrich */
rawCities.forEach(c=>{
  c.cat = aqiCategory(c.aqi);
  c.air = airScore(c.aqi);
  c.overall = overallScore(c);
  c.hair = hairScore(c);
  c.skin = skinScore(c);
  c.overallGrade = letterGrade(c.overall);
  c.airGrade = letterGrade(c.air);
  c.waterGrade = letterGrade(c.waterScore);
  c.riskTier = overallRiskTier(c);
});

/* ============ STATE ============ */
let state = {
  selectedCity: "New Delhi",
  compareCity: null,
  compareMode: false,
  riskFilter: "all",
  pollutant: "aqi",
  aqiMin: 0,
  aqiMax: 300,
};

/* ============ COPY BANKS ============ */
const airCopy = {
  lungs: {
    low: "Air is unlikely to strain healthy lungs today, though people with asthma should still keep a reliever inhaler handy.",
    moderate: "Fine particulate levels can start to irritate airways during longer outdoor exposure — expect mild throat or eye irritation on high-traffic streets.",
    high: "Particulate levels are high enough to inflame airways in most people, not just sensitive groups — coughing, throat irritation and breathlessness are common."
  },
  sleep: {
    low: "Bedroom air quality should support normal, uninterrupted sleep if windows are kept closed near traffic hours.",
    moderate: "Indoor particulate infiltration can lightly disrupt deep-sleep stages and cause a stuffy nose overnight, especially with windows open.",
    high: "Poor air can measurably fragment sleep — nasal congestion, dry throat and night-time coughing are more likely, especially in rooms without filtration."
  },
  energy: {
    low: "Oxygen uptake during daily activity should feel normal; no meaningful fatigue expected from air quality alone.",
    moderate: "Mild daytime fatigue and reduced concentration are possible on longer outdoor commutes.",
    high: "Chronic low-grade inflammation from high particulate exposure is commonly linked to daytime fatigue, brain fog and reduced stamina."
  },
  exercise: {
    low: "Outdoor workouts, running and cycling are safe at typical intensities.",
    moderate: "High-intensity outdoor cardio (running, cycling) increases inhalation volume — consider shifting hard sessions indoors or to early morning.",
    high: "Outdoor cardio at this AQI meaningfully raises pollutant intake; move intense workouts indoors or to a filtered gym until levels drop."
  },
  longterm: {
    low: "Long-term cardiovascular and respiratory risk from air alone is low at this level, assuming it holds through the year.",
    moderate: "Sustained exposure at this level over months is associated with measurable increases in respiratory and cardiovascular risk in population studies.",
    high: "Sustained exposure at this level is associated with meaningfully elevated long-term risk of respiratory disease, cardiovascular strain and reduced lung development in children."
  }
};
const waterCopy = {
  hairfall: {
    low: "Water hardness and contaminant load are low enough that hair fall linked to water quality is unlikely.",
    moderate: "Moderately hard or treated-but-imperfect water can gradually weaken hair shafts, contributing to above-average shedding.",
    high: "Higher mineral and contaminant load in this city's water supply is a plausible contributor to increased hair fall — a filtered shower head can help."
  },
  dryness: {
    low: "Water mineral content shouldn't meaningfully dry out hair with normal washing frequency.",
    moderate: "Expect some moisture-stripping with frequent washing — a weekly deep-conditioning treatment is worth adding.",
    high: "Hard, mineral-heavy water strips natural oils quickly — hair may feel rough or straw-like without regular deep conditioning."
  },
  scalp: {
    low: "Scalp irritation from water quality is unlikely; a normal scalp-care routine is sufficient.",
    moderate: "Mild scalp dryness, flaking or itchiness is possible, especially in colder months.",
    high: "Higher chlorine/mineral load raises the chance of scalp dryness, flaking and irritation — a clarifying shampoo once a week can help reset buildup."
  },
  skindry: {
    low: "Water quality is unlikely to meaningfully dry out skin.",
    moderate: "Skin barrier function may be mildly affected with frequent washing — a fragrance-free moisturiser after showers is a good habit.",
    high: "Hard or heavily treated water can noticeably strip the skin barrier — apply moisturiser within 3 minutes of washing to lock in hydration."
  },
  acne: {
    low: "Water-related breakouts are unlikely at this quality level.",
    moderate: "Mineral residue can occasionally clog pores along the hairline and jaw — rinse thoroughly and pat (don't rub) skin dry.",
    high: "Mineral and chlorine residue is a plausible contributor to breakouts along the hairline/jaw — consider a post-wash micellar water rinse."
  },
  sensitive: {
    low: "Low irritation risk for sensitive skin from tap water alone.",
    moderate: "Sensitive skin may react mildly (tightness, light redness) after washing — lukewarm (not hot) water helps.",
    high: "Sensitive skin is more likely to react (redness, tightness, itching) to this water supply — consider a shower filter and lukewarm water only."
  }
};
function airTier(aqi){ return aqi<=100?"low":aqi<=200?"moderate":"high"; }
function waterTier(score){ return score>=75?"low":score>=55?"moderate":"high"; }

/* ============ RENDER: METRICS ============ */
function filteredCities(){
  return rawCities.filter(c=>{
    if(c.aqi < state.aqiMin || c.aqi > state.aqiMax) return false;
    if(state.riskFilter!=="all" && c.riskTier!==state.riskFilter) return false;
    return true;
  });
}

function renderMetrics(){
  const f = filteredCities();
  const el = document.getElementById('metricsGrid');
  if(f.length===0){
    el.innerHTML = `<div class="metric-card" style="grid-column:1/-1;text-align:center;color:var(--ink-muted);">No cities match the current filters. Try widening the AQI range or risk filter.</div>`;
    document.getElementById('chartsNote').textContent = "0 of "+rawCities.length+" cities match filters";
    return;
  }
  const avgAqi = Math.round(f.reduce((s,c)=>s+c.aqi,0)/f.length);
  const highest = f.reduce((a,b)=>b.aqi>a.aqi?b:a);
  const lowest = f.reduce((a,b)=>b.aqi<a.aqi?b:a);
  const avgHealth = Math.round(f.reduce((s,c)=>s+c.overall,0)/f.length);
  el.innerHTML = `
    <div class="metric-card"><div class="metric-label">Average AQI</div><div class="metric-value air">${avgAqi}</div><div class="metric-sub">${aqiCategory(avgAqi).label} · across ${f.length} cities</div></div>
    <div class="metric-card"><div class="metric-label">Highest AQI city</div><div class="metric-value" style="color:var(--verypoor)">${highest.name}</div><div class="metric-sub">AQI ${highest.aqi} · ${highest.cat.label}</div></div>
    <div class="metric-card"><div class="metric-label">Lowest AQI city</div><div class="metric-value" style="color:var(--good)">${lowest.name}</div><div class="metric-sub">AQI ${lowest.aqi} · ${lowest.cat.label}</div></div>
    <div class="metric-card"><div class="metric-label">Cities analyzed</div><div class="metric-value">${f.length}<span style="font-size:16px;color:var(--ink-faint);"> / ${rawCities.length}</span></div><div class="metric-sub">matching current filters</div></div>
    <div class="metric-card"><div class="metric-label">Environmental health score</div><div class="metric-value water">${avgHealth}</div><div class="metric-sub">composite avg · 60% air / 40% water</div></div>
  `;
  document.getElementById('chartsNote').textContent = f.length+" of "+rawCities.length+" cities match filters";
  document.getElementById('heroCityCount').innerHTML = "🏙️ <b>"+rawCities.length+"</b> cities analyzed";
}

/* ============ RENDER: CITY CARDS ============ */
function renderCityCards(){
  const f = filteredCities();
  const el = document.getElementById('cityCards');
  if(f.length===0){ el.innerHTML=""; return; }
  el.innerHTML = f.map(c=>`
    <div class="city-card ${c.name===state.selectedCity?'selected':''}" tabindex="0" data-city="${c.name}">
      <div class="city-card-top">
        <div>
          <div class="city-name">${c.name}</div>
          <div class="city-state">${c.state}</div>
        </div>
        <div class="badge ${c.cat.cls}">${c.cat.label}</div>
      </div>
      <div class="city-aqi-row">
        <div class="city-aqi-num" style="color:${c.cat.color}">${c.aqi}</div>
        <div class="city-aqi-label">AQI (US)</div>
      </div>
      <div class="city-metrics">
        <div class="mini-stat"><div class="k">PM2.5${c.pm25Est?'*':''}</div><div class="v">${c.pm25} µg/m³</div></div>
        <div class="mini-stat"><div class="k">PM10${c.pm10Est?'*':''}</div><div class="v">${c.pm10} µg/m³</div></div>
        <div class="mini-stat"><div class="k">Health score</div><div class="v">${c.overall}/100
          <div class="score-bar-track"><div class="score-bar-fill" style="width:${c.overall}%;background:${c.overall>=75?'var(--good)':c.overall>=55?'var(--moderate)':'var(--verypoor)'}"></div></div>
        </div></div>
        <div class="mini-stat"><div class="k">Water score</div><div class="v">${c.waterScore}/100
          <div class="score-bar-track"><div class="score-bar-fill" style="width:${c.waterScore}%;background:var(--accent-water)"></div></div>
        </div></div>
      </div>
      <div class="city-card-footer"><span>${riskEmoji(c.riskTier)} ${riskWord(c.riskTier)} overall risk</span><span>${c.updated.split(',')[0]}</span></div>
    </div>
  `).join('');
  el.querySelectorAll('.city-card').forEach(card=>{
    card.addEventListener('click', ()=>{
      state.selectedCity = card.dataset.city;
      document.getElementById('citySelect').value = state.selectedCity;
      fullRender();
      document.getElementById('reportColumns').scrollIntoView({behavior:'smooth', block:'start'});
    });
    card.addEventListener('keypress', (e)=>{ if(e.key==='Enter') card.click(); });
  });
}

/* ============ RENDER: REPORT CARD ============ */
function gaugeSvg(value, color, size=110){
  const r = 44, c = 2*Math.PI*r;
  const offset = c - (value/100)*c;
  return `<svg class="gauge-svg" viewBox="0 0 110 110">
    <circle cx="55" cy="55" r="${r}" fill="none" stroke="rgba(255,255,255,0.08)" stroke-width="10"/>
    <circle cx="55" cy="55" r="${r}" fill="none" stroke="${color}" stroke-width="10" stroke-linecap="round"
      stroke-dasharray="${c}" stroke-dashoffset="${offset}" transform="rotate(-90 55 55)"/>
    <text x="55" y="61" text-anchor="middle" font-family="JetBrains Mono, monospace" font-size="22" font-weight="700" fill="${color}">${value}</text>
  </svg>`;
}

function renderCityPanel(c){
  const at = airTier(c.aqi), wt = waterTier(c.waterScore);
  return `
    <div class="report-panel">
      <div class="report-panel-head">
        <div>
          <div class="report-city-name">${c.name}</div>
          <div class="report-city-meta">${c.state} · updated ${c.updated}</div>
        </div>
        <div class="badge ${c.cat.cls}">${c.cat.label}</div>
      </div>

      <div class="gauge-row">
        <div class="gauge-box">${gaugeSvg(c.air, 'var(--accent-air)')}<div class="gauge-label">Air score</div></div>
        <div class="gauge-box">${gaugeSvg(c.waterScore, 'var(--accent-water)')}<div class="gauge-label">Water score</div></div>
        <div class="gauge-box">${gaugeSvg(c.overall, c.overall>=75?'#34D399':c.overall>=55?'#FACC15':'#EF4444')}<div class="gauge-label">Overall score</div></div>
      </div>

      <div class="grade-row">
        <div class="grade-pill"><div class="grade-letter" style="color:var(--accent-air)">${c.airGrade}</div><div class="grade-name">Air quality</div></div>
        <div class="grade-pill"><div class="grade-letter" style="color:var(--accent-water)">${c.waterGrade}</div><div class="grade-name">Water quality</div></div>
        <div class="grade-pill"><div class="grade-letter">${riskEmoji(riskTier(c.hair,true))}</div><div class="grade-name">Hair risk: ${riskWord(riskTier(c.hair,true))}</div></div>
        <div class="grade-pill"><div class="grade-letter">${riskEmoji(riskTier(c.skin,true))}</div><div class="grade-name">Skin risk: ${riskWord(riskTier(c.skin,true))}</div></div>
      </div>

      <div class="impact-block">
        <h5>🫁 Air quality impact (AQI ${c.aqi})</h5>
        <div class="impact-row"><span class="impact-emoji">${riskEmoji(at)}</span><span class="impact-text"><b>Lungs:</b> <span>${airCopy.lungs[at]}</span></span></div>
        <div class="impact-row"><span class="impact-emoji">${riskEmoji(at)}</span><span class="impact-text"><b>Sleep:</b> <span>${airCopy.sleep[at]}</span></span></div>
        <div class="impact-row"><span class="impact-emoji">${riskEmoji(at)}</span><span class="impact-text"><b>Energy levels:</b> <span>${airCopy.energy[at]}</span></span></div>
        <div class="impact-row"><span class="impact-emoji">${riskEmoji(at)}</span><span class="impact-text"><b>Exercise performance:</b> <span>${airCopy.exercise[at]}</span></span></div>
        <div class="impact-row"><span class="impact-emoji">${riskEmoji(at)}</span><span class="impact-text"><b>Long-term health:</b> <span>${airCopy.longterm[at]}</span></span></div>
      </div>

      <div class="impact-block water">
        <h5>💧 Water quality impact (score ${c.waterScore}/100)</h5>
        <div class="impact-row"><span class="impact-emoji">${riskEmoji(wt)}</span><span class="impact-text"><b>Hair fall:</b> <span>${waterCopy.hairfall[wt]}</span></span></div>
        <div class="impact-row"><span class="impact-emoji">${riskEmoji(wt)}</span><span class="impact-text"><b>Hair dryness:</b> <span>${waterCopy.dryness[wt]}</span></span></div>
        <div class="impact-row"><span class="impact-emoji">${riskEmoji(wt)}</span><span class="impact-text"><b>Scalp health:</b> <span>${waterCopy.scalp[wt]}</span></span></div>
        <div class="impact-row"><span class="impact-emoji">${riskEmoji(wt)}</span><span class="impact-text"><b>Skin dryness:</b> <span>${waterCopy.skindry[wt]}</span></span></div>
        <div class="impact-row"><span class="impact-emoji">${riskEmoji(wt)}</span><span class="impact-text"><b>Acne:</b> <span>${waterCopy.acne[wt]}</span></span></div>
        <div class="impact-row"><span class="impact-emoji">${riskEmoji(wt)}</span><span class="impact-text"><b>Sensitive skin:</b> <span>${waterCopy.sensitive[wt]}</span></span></div>
      </div>
    </div>
  `;
}

function renderReportCard(){
  const el = document.getElementById('reportColumns');
  const c1 = rawCities.find(c=>c.name===state.selectedCity);
  if(state.compareMode && state.compareCity){
    const c2 = rawCities.find(c=>c.name===state.compareCity);
    el.className = "report-columns";
    el.innerHTML = renderCityPanel(c1) + renderCityPanel(c2);
  } else {
    el.className = "report-columns single";
    el.innerHTML = renderCityPanel(c1);
  }
  document.getElementById('recCityLabel').textContent = state.selectedCity;
}

/* ============ RENDER: INSIGHTS ============ */
function renderInsights(){
  const sorted = [...rawCities].sort((a,b)=>a.aqi-b.aqi);
  const top3clean = sorted.slice(0,3);
  const top3polluted = [...sorted].reverse().slice(0,3);
  const el = document.getElementById('insightsGrid');
  el.innerHTML = `
    <div class="insight-card">
      <h4>🌿 Top 3 cleanest cities (lowest AQI)</h4>
      <ul class="rank-list">${top3clean.map((c,i)=>`<li><span><span class="rk">0${i+1}</span>${c.name}</span><span class="badge ${c.cat.cls}">${c.aqi}</span></li>`).join('')}</ul>
    </div>
    <div class="insight-card">
      <h4>🏭 Top 3 most polluted cities (highest AQI)</h4>
      <ul class="rank-list">${top3polluted.map((c,i)=>`<li><span><span class="rk">0${i+1}</span>${c.name}</span><span class="badge ${c.cat.cls}">${c.aqi}</span></li>`).join('')}</ul>
    </div>
    <div class="insight-card">
      <h4>⚠️ Biggest anomaly</h4>
      <p class="callout"><b>Chennai (AQI 87)</b> is a coastal city, which typically benefits from sea-breeze dispersion of pollutants — yet it currently reads higher than inland Kolkata (59) and Pune (57). That breaks the usual "coastal = cleaner" pattern seen across this dataset.</p>
    </div>
    <div class="insight-card">
      <h4>😮 Most surprising observation</h4>
      <p class="callout">New Delhi's current reading of <b>AQI 111</b> looks almost mild next to its own recent history — CPCB records show Delhi crossing <b>AQI 250–357</b> in the Oct–Nov smog season, and spiking past <b>680</b> around Diwali. The same city can swing from "Moderate" to "Severe" within weeks, purely on season.</p>
    </div>
    <div class="insight-card" style="grid-column:1/-1;">
      <h4>🎯 Recommended actions (national view)</h4>
      <ul class="action-list">
        <li>Prioritise indoor air filtration in <b>New Delhi</b> and <b>Chennai</b> — the two cities currently above the 8-city average AQI.</li>
        <li>Residents of <b>New Delhi</b> should treat tap water as non-potable without filtration — it scores lowest on the water-quality benchmark.</li>
        <li><b>Mumbai, Pune and Bangalore</b> currently offer the best combined air+water profile — favourable conditions for outdoor exercise.</li>
        <li>Re-check this dashboard during Oct–Nov; Delhi's air quality typically deteriorates sharply in the post-monsoon smog season.</li>
      </ul>
    </div>
  `;
}

/* ============ RENDER: RECOMMENDATIONS ============ */
const recTabs = ["Daily actions","Indoor air","Outdoor activity","Hair care","Skin care","Water quality"];
function recContent(c){
  const at = airTier(c.aqi), wt = waterTier(c.waterScore);
  const daily = {
    low: ["Normal outdoor routine is fine, including commuting and errands.","Keep windows open for natural ventilation during the day.","Light daily hydration habits (2–2.5L water) are enough."],
    moderate: ["Check the AQI before extended outdoor plans; avoid peak-traffic hours (8–10am, 6–8pm) if sensitive.","Crack windows for ventilation but avoid leaving them open near high-traffic roads.","Carry a light scarf or mask for dusty stretches of your commute."],
    high: ["Limit non-essential outdoor time, especially for children, older adults and those with asthma.","Keep windows closed during peak traffic hours and ventilate briefly in early morning instead.","Wear an N95 mask for any outdoor exposure longer than 15–20 minutes."]
  };
  const indoor = {
    low: ["A basic HEPA-filter fan is optional but nice-to-have.","Houseplants (money plant, areca palm) can help maintain healthy indoor air.","Vacuum with a HEPA-filter vacuum weekly to control indoor dust."],
    moderate: ["A HEPA air purifier in the bedroom noticeably improves sleep quality at this AQI.","Change AC/purifier filters every 4–6 weeks during this period.","Avoid indoor smoking or incense, which compounds particulate load."],
    high: ["Run a HEPA air purifier continuously in bedroom and living areas.","Seal obvious gaps around windows/doors during high-AQI hours.","Avoid frying/incense indoors without exhaust ventilation — it adds to an already high particulate load."]
  };
  const outdoor = {
    low: ["Outdoor running, cycling and sports are safe at normal intensity.","Best outdoor windows: early morning or after light rain.","No mask required for typical outdoor activity."],
    moderate: ["Shift high-intensity cardio to early morning or indoors on the worst days.","Choose parks/green cover over roadside routes for walks and runs.","A light mask is sensible for cycling commutes on main roads."],
    high: ["Move workouts indoors (gym, home) until AQI improves.","If you must be outside, keep exertion low — walking rather than running.","N95 mask recommended for any outdoor activity beyond a quick errand."]
  };
  const hair = {
    low: ["Standard wash routine (2–3x/week) is fine — no special water treatment needed.","Sulphate-free shampoo is still a good general habit.","Occasional oiling (once every 1–2 weeks) supports shine and strength."],
    moderate: ["Add a weekly deep-conditioning mask to counter mineral build-up.","Rinse with filtered/RO water for the final rinse if hair fall increases.","Reduce heat styling frequency — dry, mineral-exposed hair is more heat-sensitive."],
    high: ["Install a shower-head water filter to cut mineral/chlorine exposure at the source.","Use a clarifying (chelating) shampoo every 1–2 weeks to remove mineral buildup.","See a dermatologist if hair fall exceeds ~100 strands/day for several weeks."]
  };
  const skin = {
    low: ["Regular moisturiser after washing is sufficient.","No special adjustments needed for this water/air combination."],
    moderate: ["Moisturise within 3 minutes of washing to lock in hydration.","Double-cleanse in the evening to remove particulate residue from skin.","Patch-test new products — barrier is slightly more reactive at this level."],
    high: ["Use a gentle, fragrance-free cleanser and avoid hot water, which worsens dryness.","Apply a barrier-repair moisturiser (ceramides) twice daily.","Consider a shower filter — it measurably reduces chlorine/mineral-linked irritation."]
  };
  const water = {
    low: ["Standard filtration (basic RO/UV) is enough for drinking water.","No major action needed beyond routine filter maintenance."],
    moderate: ["Use an RO+UV purifier for drinking water and replace filters on schedule.","Consider a shower filter if you notice hair/skin dryness creeping up."],
    high: ["Treat tap water as non-potable — use RO+UV filtration for all drinking/cooking water.","Install a point-of-use shower filter to reduce hair and skin exposure.","Get water tested annually if relying on borewell/groundwater sources."]
  };
  return {daily:daily[at], indoor:indoor[at], outdoor:outdoor[at], hair:hair[wt], skin:skin[wt], water:water[wt]};
}
function renderRecommendations(){
  const c = rawCities.find(c=>c.name===state.selectedCity);
  const rc = recContent(c);
  const tabsEl = document.getElementById('recTabs');
  tabsEl.innerHTML = recTabs.map((t,i)=>`<button class="tab-btn ${i===0?'active':''}" data-idx="${i}">${t}</button>`).join('');
  const panelsEl = document.getElementById('recPanels');
  panelsEl.innerHTML = `
    <div class="tab-panel active" data-idx="0">
      <div class="rec-col"><h5>What to do today</h5><ul>${rc.daily.map(x=>`<li>${x}</li>`).join('')}</ul></div>
      <div class="rec-col"><h5>Why it matters here</h5><ul><li>Based on ${c.name}'s current AQI of ${c.aqi} (${c.cat.label}).</li><li>Overall environmental score: ${c.overall}/100 (${c.overallGrade}).</li></ul></div>
    </div>
    <div class="tab-panel" data-idx="1">
      <div class="rec-col"><h5>Indoor air improvements</h5><ul>${rc.indoor.map(x=>`<li>${x}</li>`).join('')}</ul></div>
      <div class="rec-col"><h5>Air score</h5><ul><li>Air quality grade: ${c.airGrade}</li><li>PM2.5: ${c.pm25} µg/m³${c.pm25Est?' (estimated)':''}</li><li>PM10: ${c.pm10} µg/m³${c.pm10Est?' (estimated)':''}</li></ul></div>
    </div>
    <div class="tab-panel" data-idx="2">
      <div class="rec-col"><h5>Outdoor activity guidance</h5><ul>${rc.outdoor.map(x=>`<li>${x}</li>`).join('')}</ul></div>
      <div class="rec-col"><h5>Best times</h5><ul><li>Early morning generally has the lowest traffic-linked particulate load.</li><li>Avoid 8–10am and 6–8pm rush windows on higher-AQI days.</li></ul></div>
    </div>
    <div class="tab-panel" data-idx="3">
      <div class="rec-col"><h5>Hair-care recommendations</h5><ul>${rc.hair.map(x=>`<li>${x}</li>`).join('')}</ul></div>
      <div class="rec-col"><h5>Hair risk</h5><ul><li>Hair-risk score: ${c.hair}/100 (${riskWord(riskTier(c.hair,true))} risk)</li><li>Driven mainly by water quality score: ${c.waterScore}/100</li></ul></div>
    </div>
    <div class="tab-panel" data-idx="4">
      <div class="rec-col"><h5>Skin-care recommendations</h5><ul>${rc.skin.map(x=>`<li>${x}</li>`).join('')}</ul></div>
      <div class="rec-col"><h5>Skin risk</h5><ul><li>Skin-risk score: ${c.skin}/100 (${riskWord(riskTier(c.skin,true))} risk)</li><li>Combines air (${c.air}) and water (${c.waterScore}) scores evenly.</li></ul></div>
    </div>
    <div class="tab-panel" data-idx="5">
      <div class="rec-col"><h5>Water-quality improvement</h5><ul>${rc.water.map(x=>`<li>${x}</li>`).join('')}</ul></div>
      <div class="rec-col"><h5>Water grade</h5><ul><li>Water-quality grade: ${c.waterGrade}</li><li>Score reflects BIS tap-water benchmark positioning (see methodology).</li></ul></div>
    </div>
  `;
  tabsEl.querySelectorAll('.tab-btn').forEach(btn=>{
    btn.addEventListener('click', ()=>{
      tabsEl.querySelectorAll('.tab-btn').forEach(b=>b.classList.remove('active'));
      btn.classList.add('active');
      panelsEl.querySelectorAll('.tab-panel').forEach(p=>p.classList.remove('active'));
      panelsEl.querySelector(`.tab-panel[data-idx="${btn.dataset.idx}"]`).classList.add('active');
    });
  });
}

/* ============ RENDER: EXEC SUMMARY ============ */
function renderExecSummary(){
  const sorted = [...rawCities].sort((a,b)=>a.aqi-b.aqi);
  const avgAqi = Math.round(rawCities.reduce((s,c)=>s+c.aqi,0)/rawCities.length);
  const cleanestOverall = [...rawCities].sort((a,b)=>b.overall-a.overall)[0];
  const worstOverall = [...rawCities].sort((a,b)=>a.overall-b.overall)[0];
  const el = document.getElementById('execSummary');
  el.innerHTML = `
    <p>Across the <b>${rawCities.length} major Indian cities</b> analyzed on this snapshot (${rawCities[0].updated}), the average Air Quality Index sits at <b>${avgAqi}</b> — a "${aqiCategory(avgAqi).label}" reading overall, but the range is wide: from <b>${sorted[0].name} (AQI ${sorted[0].aqi})</b> at the cleanest end to <b>${sorted[sorted.length-1].name} (AQI ${sorted[sorted.length-1].aqi})</b> at the most polluted end — a spread of <b>${sorted[sorted.length-1].aqi-sorted[0].aqi} points</b>.</p>
    <p>Factoring in water quality alongside air, <b>${cleanestOverall.name}</b> comes out as the strongest overall environment (score ${cleanestOverall.overall}/100, grade ${cleanestOverall.overallGrade}), while <b>${worstOverall.name}</b> ranks weakest (score ${worstOverall.overall}/100, grade ${worstOverall.overallGrade}) — driven largely by its comparatively low water-quality benchmark alongside elevated PM10.</p>
    <p>The most notable pattern in today's data is that <b>Delhi's PM10 (175 µg/m³) is disproportionately high relative to its PM2.5 (27 µg/m³)</b>, pointing to coarse dust and construction sources rather than combustion smoke as the dominant driver right now — a very different signature from its usual winter smog profile, where fine combustion particles (PM2.5) typically dominate.</p>
    <p>For a resident of <b>New Delhi</b> specifically: current air quality carries a moderate lung and long-term health risk if sustained, and its water benchmark is the weakest of the eight cities — filtered drinking water and a shower filter are the two highest-leverage actions available right now.</p>
  `;
}

/* ============ CHARTS ============ */
let charts = {};
function chartColors(cities, metric){
  return cities.map(c=>c.cat.color);
}
function buildOrUpdate(id, cfg){
  if(charts[id]){ charts[id].destroy(); }
  charts[id] = new Chart(document.getElementById(id).getContext('2d'), cfg);
}
const chartTextColor = "#8CA0C2";
const chartGridColor = "rgba(140,160,194,0.08)";
Chart.defaults.color = chartTextColor;
Chart.defaults.font.family = "Inter, sans-serif";
Chart.defaults.font.size = 11;

function renderCharts(){
  const f = filteredCities();
  const labels = f.map(c=>c.name);

  // AQI comparison
  buildOrUpdate('aqiChart', {
    type:'bar',
    data:{labels, datasets:[{label:'AQI', data:f.map(c=>c.aqi), backgroundColor:chartColors(f), borderRadius:6, maxBarThickness:34}]},
    options:{plugins:{legend:{display:false}, tooltip:{callbacks:{label:(ctx)=>`AQI ${ctx.raw} · ${f[ctx.dataIndex].cat.label}`}}},
      scales:{x:{grid:{display:false}}, y:{grid:{color:chartGridColor}, beginAtZero:true}}, maintainAspectRatio:false}
  });

  // PM2.5
  buildOrUpdate('pm25Chart', {
    type:'bar',
    data:{labels, datasets:[{label:'PM2.5', data:f.map(c=>c.pm25), backgroundColor:'#29D9C2', borderRadius:6, maxBarThickness:34}]},
    options:{plugins:{legend:{display:false}, tooltip:{callbacks:{label:(ctx)=>`${ctx.raw} µg/m³${f[ctx.dataIndex].pm25Est?' (estimated)':''}`}}},
      scales:{x:{grid:{display:false}}, y:{grid:{color:chartGridColor}, beginAtZero:true}}, maintainAspectRatio:false}
  });
  document.getElementById('pm25Note').textContent = f.some(c=>c.pm25Est) ? "* modelled from AQI where not directly reported." : "";

  // PM10
  buildOrUpdate('pm10Chart', {
    type:'bar',
    data:{labels, datasets:[{label:'PM10', data:f.map(c=>c.pm10), backgroundColor:'#F2B84B', borderRadius:6, maxBarThickness:34}]},
    options:{plugins:{legend:{display:false}, tooltip:{callbacks:{label:(ctx)=>`${ctx.raw} µg/m³${f[ctx.dataIndex].pm10Est?' (estimated)':''}`}}},
      scales:{x:{grid:{display:false}}, y:{grid:{color:chartGridColor}, beginAtZero:true}}, maintainAspectRatio:false}
  });
  document.getElementById('pm10Note').textContent = f.some(c=>c.pm10Est) ? "* modelled from AQI where not directly reported." : "";

  // Distribution donut
  const cats = ["Good","Satisfactory","Moderate","Poor","Very Poor","Severe"];
  const catColors = {Good:"#34D399",Satisfactory:"#A3E635",Moderate:"#FACC15",Poor:"#FB923C","Very Poor":"#EF4444",Severe:"#7F1D1D"};
  const counts = cats.map(cat=>f.filter(c=>c.cat.label===cat).length);
  buildOrUpdate('distChart', {
    type:'doughnut',
    data:{labels:cats, datasets:[{data:counts, backgroundColor:cats.map(c=>catColors[c]), borderColor:'#121A2B', borderWidth:3}]},
    options:{plugins:{legend:{position:'bottom', labels:{boxWidth:10, padding:12, font:{size:10.5}}}}, cutout:'62%', maintainAspectRatio:false}
  });

  // Ranking chart (metric-dependent)
  const metricKey = state.pollutant;
  const metricLabel = metricKey==='aqi'?'AQI':metricKey==='pm25'?'PM2.5 (µg/m³)':'PM10 (µg/m³)';
  const rsorted = [...f].sort((a,b)=>a[metricKey]-b[metricKey]);
  buildOrUpdate('rankChart', {
    type:'bar',
    data:{labels:rsorted.map(c=>c.name), datasets:[{label:metricLabel, data:rsorted.map(c=>c[metricKey]), backgroundColor:rsorted.map(c=>c.cat.color), borderRadius:6}]},
    options:{indexAxis:'y', plugins:{legend:{display:false}}, scales:{x:{grid:{color:chartGridColor}, beginAtZero:true}, y:{grid:{display:false}}}, maintainAspectRatio:false}
  });
}

/* ============ FILTER CONTROLS ============ */
function populateSelectors(){
  const citySelect = document.getElementById('citySelect');
  const compareSelect = document.getElementById('compareSelect');
  citySelect.innerHTML = rawCities.map(c=>`<option value="${c.name}">${c.name}</option>`).join('');
  compareSelect.innerHTML = rawCities.map(c=>`<option value="${c.name}">${c.name}</option>`).join('');
  citySelect.value = state.selectedCity;
  compareSelect.value = rawCities.find(c=>c.name!==state.selectedCity).name;
  state.compareCity = compareSelect.value;
}
function bindControls(){
  document.getElementById('citySelect').addEventListener('change', e=>{ state.selectedCity=e.target.value; fullRender(); });
  document.getElementById('compareSelect').addEventListener('change', e=>{ state.compareCity=e.target.value; renderReportCard(); });
  document.getElementById('compareToggle').addEventListener('change', e=>{
    state.compareMode = e.target.checked;
    document.getElementById('compareGroup').style.display = state.compareMode ? 'flex' : 'none';
    renderReportCard();
  });
  document.getElementById('riskFilter').addEventListener('change', e=>{ state.riskFilter=e.target.value; renderMetrics(); renderCityCards(); renderCharts(); });
  document.getElementById('pollutantSeg').addEventListener('click', e=>{
    if(e.target.tagName!=='BUTTON') return;
    document.querySelectorAll('#pollutantSeg button').forEach(b=>b.classList.remove('active'));
    e.target.classList.add('active');
    state.pollutant = e.target.dataset.p;
    renderCharts();
  });
  const aqiMin = document.getElementById('aqiMin'), aqiMax = document.getElementById('aqiMax');
  function syncRange(){
    let mn = parseInt(aqiMin.value), mx = parseInt(aqiMax.value);
    if(mn>mx){ [mn,mx] = [mx,mn]; }
    state.aqiMin = mn; state.aqiMax = mx;
    document.getElementById('aqiRangeLabel').textContent = `${mn} – ${mx}`;
    renderMetrics(); renderCityCards(); renderCharts();
  }
  aqiMin.addEventListener('input', syncRange);
  aqiMax.addEventListener('input', syncRange);
  document.getElementById('resetFilters').addEventListener('click', ()=>{
    state.riskFilter='all'; state.pollutant='aqi'; state.aqiMin=0; state.aqiMax=300;
    document.getElementById('riskFilter').value='all';
    document.querySelectorAll('#pollutantSeg button').forEach(b=>b.classList.remove('active'));
    document.querySelector('#pollutantSeg button[data-p="aqi"]').classList.add('active');
    aqiMin.value=0; aqiMax.value=300;
    document.getElementById('aqiRangeLabel').textContent = '0 – 300';
    renderMetrics(); renderCityCards(); renderCharts();
  });
}

/* ============ MASTER RENDER ============ */
function fullRender(){
  renderMetrics();
  renderCityCards();
  renderReportCard();
  renderCharts();
  renderRecommendations();
}

populateSelectors();
bindControls();
renderMetrics();
renderCityCards();
renderReportCard();
renderInsights();
renderRecommendations();
renderExecSummary();
renderCharts();
</script><img width="1385" height="655" alt="Screenshot 2026-07-19 at 10 15 56 PM" src="https://github.com/user-attachments/assets/013d6bbe-63f7-42d9-9ba0-f64153206cbe" /><img width="1382" height="654" alt="Screenshot 2026-07-19 at 10 16 35 PM" src="https://github.com/user-attachments/assets/4fdf7083-1993-49f0-a7f5-02f400eb45c5" />
<img width="1384" height="656" alt="Screenshot 2026-07-19 at 10 16 28 PM" src="https://github.com/user-attachments/assets/677ea1a6-9cd8-4f27-8e3e-9d227d38a74a" />
<img width="1386" height="658" alt="Screenshot 2026-07-19 at 10 16 18 PM" src="https://github.com/user-attachments/assets/f9e19f4c-c17e-46b3-a378-d2397f613a70" />
<img width="1384" height="654" alt="Screenshot 2026-07-19 at 10 16 06 PM" src="https://github.com/user-attachments/assets/cb9b47ad-240d-43da-a4ca-8ec5a84f2866" />
![Uploading Screenshot 2026-07-19 at 10.15.56 PM.png…]()


</body>
</html>
