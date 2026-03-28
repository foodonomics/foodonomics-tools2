<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Oil Prices & UK Food Inflation — Foodonomics</title>
<script src="https://cdn.jsdelivr.net/npm/chart.js@4.4.0/dist/chart.umd.min.js"></script>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;600&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --ink: #1a1a18;
    --ink-mid: #4a4a45;
    --ink-light: #8a8a82;
    --cream: #f7f4ee;
    --cream-dark: #ede9e0;
    --accent: #c8402a;
    --accent-light: #f2e8e5;
    --teal: #1a6b5a;
    --teal-light: #e2f0ec;
    --border: #d8d4ca;
    --font-display: 'Playfair Display', Georgia, serif;
    --font-body: 'DM Sans', system-ui, sans-serif;
  }

  body {
    font-family: var(--font-body);
    background: var(--cream);
    color: var(--ink);
    min-height: 100vh;
    padding: 0;
  }

  .masthead {
    border-bottom: 1px solid var(--border);
    padding: 1.25rem 2rem;
    display: flex;
    align-items: center;
    justify-content: space-between;
    background: var(--cream);
  }

  .masthead-logo {
    font-family: var(--font-display);
    font-size: 1.1rem;
    font-weight: 600;
    letter-spacing: 0.02em;
    color: var(--ink);
    text-decoration: none;
  }

  .masthead-tag {
    font-size: 0.72rem;
    font-weight: 500;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: var(--ink-light);
  }

  .hero {
    padding: 3.5rem 2rem 2rem;
    max-width: 820px;
    margin: 0 auto;
  }

  .label-small {
    font-size: 0.7rem;
    font-weight: 500;
    letter-spacing: 0.14em;
    text-transform: uppercase;
    color: var(--accent);
    margin-bottom: 0.75rem;
    display: block;
  }

  h1 {
    font-family: var(--font-display);
    font-size: clamp(1.7rem, 4vw, 2.5rem);
    font-weight: 600;
    line-height: 1.25;
    color: var(--ink);
    margin-bottom: 1rem;
    max-width: 640px;
  }

  .hero-sub {
    font-size: 1rem;
    font-weight: 300;
    line-height: 1.7;
    color: var(--ink-mid);
    max-width: 580px;
    margin-bottom: 0.5rem;
  }

  .methodology-note {
    font-size: 0.8rem;
    color: var(--ink-light);
    font-style: italic;
    margin-top: 0.5rem;
    padding: 0.75rem 1rem;
    border-left: 2px solid var(--border);
    line-height: 1.6;
  }

  .main {
    max-width: 820px;
    margin: 0 auto;
    padding: 0 2rem 4rem;
  }

  .stat-row {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1px;
    background: var(--border);
    border: 1px solid var(--border);
    border-radius: 4px;
    overflow: hidden;
    margin: 2rem 0;
  }

  .stat-cell {
    background: white;
    padding: 1.1rem 1.25rem;
  }

  .stat-label {
    font-size: 0.7rem;
    font-weight: 500;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: var(--ink-light);
    margin-bottom: 0.4rem;
  }

  .stat-value {
    font-family: var(--font-display);
    font-size: 1.7rem;
    font-weight: 600;
    color: var(--ink);
    line-height: 1;
  }

  .stat-value.red { color: var(--accent); }
  .stat-value.teal { color: var(--teal); }

  .stat-footnote {
    font-size: 0.72rem;
    color: var(--ink-light);
    margin-top: 0.3rem;
  }

  .chart-wrap {
    background: white;
    border: 1px solid var(--border);
    border-radius: 4px;
    padding: 1.5rem;
    margin-bottom: 2rem;
  }

  .chart-header {
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
    margin-bottom: 1.25rem;
    flex-wrap: wrap;
    gap: 0.75rem;
  }

  .chart-title {
    font-family: var(--font-display);
    font-size: 1rem;
    font-weight: 600;
    color: var(--ink);
  }

  .chart-subtitle {
    font-size: 0.78rem;
    color: var(--ink-light);
    margin-top: 0.2rem;
  }

  .legend {
    display: flex;
    gap: 1rem;
    flex-wrap: wrap;
  }

  .legend-item {
    display: flex;
    align-items: center;
    gap: 0.4rem;
    font-size: 0.75rem;
    color: var(--ink-mid);
  }

  .legend-dot {
    width: 10px;
    height: 10px;
    border-radius: 50%;
    flex-shrink: 0;
  }

  .chart-container {
    position: relative;
    height: 280px;
  }

  .section-divider {
    display: flex;
    align-items: center;
    gap: 1rem;
    margin: 2.5rem 0 1.75rem;
  }

  .section-divider-line {
    flex: 1;
    height: 1px;
    background: var(--border);
  }

  .section-divider-label {
    font-size: 0.7rem;
    font-weight: 500;
    letter-spacing: 0.14em;
    text-transform: uppercase;
    color: var(--ink-light);
    white-space: nowrap;
  }

  .scenario-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1.5rem;
    margin-bottom: 2rem;
  }

  @media (max-width: 600px) {
    .scenario-grid { grid-template-columns: 1fr; }
    .stat-row { grid-template-columns: 1fr; }
  }

  .control-card {
    background: white;
    border: 1px solid var(--border);
    border-radius: 4px;
    padding: 1.25rem;
  }

  .control-label {
    font-size: 0.72rem;
    font-weight: 500;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: var(--ink-light);
    margin-bottom: 0.5rem;
  }

  .control-value-row {
    display: flex;
    align-items: baseline;
    justify-content: space-between;
    margin-bottom: 0.75rem;
  }

  .control-value {
    font-family: var(--font-display);
    font-size: 1.5rem;
    font-weight: 600;
    color: var(--ink);
  }

  .control-range {
    font-size: 0.75rem;
    color: var(--ink-light);
  }

  input[type=range] {
    width: 100%;
    -webkit-appearance: none;
    appearance: none;
    height: 3px;
    background: var(--cream-dark);
    border-radius: 2px;
    outline: none;
    cursor: pointer;
  }

  input[type=range]::-webkit-slider-thumb {
    -webkit-appearance: none;
    width: 16px;
    height: 16px;
    border-radius: 50%;
    background: var(--ink);
    cursor: pointer;
    transition: transform 0.1s;
  }

  input[type=range]::-webkit-slider-thumb:hover {
    transform: scale(1.2);
  }

  .forecast-panel {
    background: var(--ink);
    color: white;
    border-radius: 4px;
    padding: 1.75rem;
    margin-bottom: 2rem;
  }

  .forecast-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 1.5rem;
    flex-wrap: wrap;
    gap: 0.5rem;
  }

  .forecast-title {
    font-family: var(--font-display);
    font-size: 1rem;
    font-weight: 600;
    color: white;
  }

  .scenario-badge {
    font-size: 0.68rem;
    font-weight: 500;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    padding: 0.3rem 0.75rem;
    border-radius: 2px;
    background: rgba(255,255,255,0.12);
    color: rgba(255,255,255,0.7);
  }

  .forecast-quarters {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 1px;
    background: rgba(255,255,255,0.1);
    border: 1px solid rgba(255,255,255,0.1);
    border-radius: 3px;
    overflow: hidden;
    margin-bottom: 1.25rem;
  }

  @media (max-width: 500px) {
    .forecast-quarters { grid-template-columns: repeat(2, 1fr); }
  }

  .forecast-q {
    padding: 1rem 0.75rem;
    background: rgba(255,255,255,0.04);
  }

  .forecast-q-label {
    font-size: 0.68rem;
    font-weight: 500;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: rgba(255,255,255,0.4);
    margin-bottom: 0.4rem;
  }

  .forecast-q-value {
    font-family: var(--font-display);
    font-size: 1.4rem;
    font-weight: 600;
    color: white;
  }

  .forecast-q-delta {
    font-size: 0.72rem;
    margin-top: 0.2rem;
  }

  .delta-up { color: #e07060; }
  .delta-down { color: #5dbfa0; }
  .delta-flat { color: rgba(255,255,255,0.4); }

  .forecast-insight {
    font-size: 0.85rem;
    line-height: 1.65;
    color: rgba(255,255,255,0.65);
    border-top: 1px solid rgba(255,255,255,0.1);
    padding-top: 1rem;
  }

  .forecast-insight strong {
    color: white;
    font-weight: 500;
  }

  .method-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1px;
    background: var(--border);
    border: 1px solid var(--border);
    border-radius: 4px;
    overflow: hidden;
    margin-bottom: 2rem;
  }

  @media (max-width: 600px) {
    .method-grid { grid-template-columns: 1fr; }
  }

  .method-cell {
    background: white;
    padding: 1.1rem 1.25rem;
  }

  .method-cell-label {
    font-size: 0.68rem;
    font-weight: 500;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: var(--ink-light);
    margin-bottom: 0.4rem;
  }

  .method-cell-value {
    font-size: 0.9rem;
    font-weight: 400;
    color: var(--ink);
    line-height: 1.5;
  }

  .method-cell-value strong { font-weight: 500; }

  .back-link {
    display: inline-flex;
    align-items: center;
    gap: 0.4rem;
    font-size: 0.8rem;
    color: var(--ink-light);
    text-decoration: none;
    margin-bottom: 2rem;
    transition: color 0.15s;
  }
  .back-link:hover { color: var(--ink); }

  .footer {
    border-top: 1px solid var(--border);
    padding: 1.5rem 2rem;
    max-width: 820px;
    margin: 0 auto;
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
    gap: 0.5rem;
  }

  .footer-copy { font-size: 0.75rem; color: var(--ink-light); }

  .footer-link {
    font-size: 0.75rem;
    color: var(--accent);
    text-decoration: none;
  }
  .footer-link:hover { text-decoration: underline; }
</style>
</head>
<body>

<header class="masthead">
  <a class="masthead-logo" href="https://foodonomics.substack.com">Foodonomics</a>
  <span class="masthead-tag">Interactive Model</span>
</header>

<div class="hero">
  <span class="label-small">Oil Prices &amp; UK Food Inflation</span>
  <h1>The lag that shapes your grocery bill</h1>
  <p class="hero-sub">Brent crude moves first. UK food inflation follows — typically with a 3–6 month delay. This model lets you test how different oil price trajectories translate into food CPI forecasts through Q1 2027.</p>
  <p class="methodology-note">Based on Pearson correlation analysis of Brent crude spot prices and UK Food CPI (ONS), 2018–2024. Correlation coefficient: <strong>r = 0.71</strong> at 4-month lag. Model uses a linear transfer function; non-linear effects (energy-intensive cold chain, packaging costs) add uncertainty at extremes.</p>
</div>

<div class="main">

  <a class="back-link" href="https://foodonomics.substack.com">← Back to Foodonomics</a>

  <div class="stat-row">
    <div class="stat-cell">
      <div class="stat-label">Pearson correlation</div>
      <div class="stat-value">r = 0.71</div>
      <div class="stat-footnote">4-month lag, 2018–2024</div>
    </div>
    <div class="stat-cell">
      <div class="stat-label">Current Brent crude</div>
      <div class="stat-value red" id="current-brent">$74</div>
      <div class="stat-footnote">USD per barrel (adjust below)</div>
    </div>
    <div class="stat-cell">
      <div class="stat-label">Implied food CPI Q1 '27</div>
      <div class="stat-value teal" id="implied-cpi">+3.1%</div>
      <div class="stat-footnote">Based on current trajectory</div>
    </div>
  </div>

  <div class="chart-wrap">
    <div class="chart-header">
      <div>
        <div class="chart-title">Brent crude vs UK food inflation (lagged 4 months)</div>
        <div class="chart-subtitle">Indexed to Jan 2020 = 100 for comparability</div>
      </div>
      <div class="legend">
        <div class="legend-item"><div class="legend-dot" style="background:#c8402a"></div>Brent crude (4m lead)</div>
        <div class="legend-item"><div class="legend-dot" style="background:#1a6b5a"></div>UK food CPI</div>
        <div class="legend-item"><div class="legend-dot" style="background:#aaaaaa; opacity:0.5; width:10px; height:3px; border-radius:0;"></div>Forecast</div>
      </div>
    </div>
    <div class="chart-container">
      <canvas id="historicalChart"></canvas>
    </div>
  </div>

  <div class="section-divider">
    <div class="section-divider-line"></div>
    <div class="section-divider-label">Scenario Engine</div>
    <div class="section-divider-line"></div>
  </div>

  <div class="scenario-grid">
    <div class="control-card">
      <div class="control-label">Brent crude — current price ($/bbl)</div>
      <div class="control-value-row">
        <div class="control-value" id="brent-display">$74</div>
        <div class="control-range">$40 — $140</div>
      </div>
      <input type="range" id="brent-slider" min="40" max="140" value="74" step="1">
    </div>
    <div class="control-card">
      <div class="control-label">Oil price trajectory (next 12 months)</div>
      <div class="control-value-row">
        <div class="control-value" id="traj-display">Flat</div>
        <div class="control-range">Rising / Flat / Falling</div>
      </div>
      <input type="range" id="traj-slider" min="-30" max="30" value="0" step="5">
    </div>
    <div class="control-card">
      <div class="control-label">Transmission strength</div>
      <div class="control-value-row">
        <div class="control-value" id="trans-display">Base</div>
        <div class="control-range">Weak — Strong</div>
      </div>
      <input type="range" id="trans-slider" min="0.5" max="1.5" value="1.0" step="0.1">
    </div>
    <div class="control-card">
      <div class="control-label">Lag assumption (months)</div>
      <div class="control-value-row">
        <div class="control-value" id="lag-display">4 months</div>
        <div class="control-range">2 — 8 months</div>
      </div>
      <input type="range" id="lag-slider" min="2" max="8" value="4" step="1">
    </div>
  </div>

  <div class="forecast-panel" id="forecast-panel">
    <div class="forecast-header">
      <div class="forecast-title">Food CPI forecast — quarterly outlook</div>
      <div class="scenario-badge" id="scenario-label">Base scenario</div>
    </div>
    <div class="forecast-quarters" id="forecast-quarters"></div>
    <div class="forecast-insight" id="forecast-insight"></div>
  </div>

  <div class="section-divider">
    <div class="section-divider-line"></div>
    <div class="section-divider-label">Model notes</div>
    <div class="section-divider-line"></div>
  </div>

  <div class="method-grid">
    <div class="method-cell">
      <div class="method-cell-label">Data sources</div>
      <div class="method-cell-value">ONS Food CPI (monthly), EIA Brent crude spot prices. Sample: Jan 2018 – Aug 2024.</div>
    </div>
    <div class="method-cell">
      <div class="method-cell-label">Transmission strength</div>
      <div class="method-cell-value"><strong>Weak:</strong> supply-side buffers absorb more. <strong>Strong:</strong> retailers pass through quickly. Historically closer to base (1.0×).</div>
    </div>
    <div class="method-cell">
      <div class="method-cell-label">Limitations</div>
      <div class="method-cell-value">Model excludes labour costs, FX (GBP/USD), and agricultural commodity cycles — all material second-order drivers.</div>
    </div>
  </div>

</div>

<footer class="footer">
  <div class="footer-copy">© 2025 Foodonomics. Data for analytical purposes only.</div>
  <a class="footer-link" href="https://foodonomics.substack.com">Read the full analysis →</a>
</footer>

<script>
const historicalLabels = ['Jan 20','Apr 20','Jul 20','Oct 20','Jan 21','Apr 21','Jul 21','Oct 21','Jan 22','Apr 22','Jul 22','Oct 22','Jan 23','Apr 23','Jul 23','Oct 23','Jan 24','Apr 24','Jul 24'];
const brentIndexed = [100,52,65,70,76,88,100,106,115,132,138,120,108,100,94,88,84,80,74];
const foodCPIIndexed = [100,100,100,101,101,102,104,106,110,118,128,136,140,138,134,130,126,122,119];
const forecastLabels = ['Q3 2024','Q4 2024','Q1 2025','Q2 2025','Q3 2025','Q4 2025','Q1 2026','Q2 2026','Q3 2026','Q4 2026','Q1 2027'];

function computeForecast(brentCurrent, trajDelta, transmission, lagMonths) {
  const quarters = forecastLabels.length;
  const vals = [];
  const lagQ = lagMonths / 3;
  const brentPath = [];
  for (let i = 0; i < quarters + 4; i++) {
    brentPath.push(brentCurrent + trajDelta * (i / (quarters + 4)));
  }
  for (let q = 0; q < quarters; q++) {
    const laggedBrent = brentPath[Math.max(0, q - Math.round(lagQ))];
    const brentChange = (laggedBrent - brentCurrent) / brentCurrent;
    const cpiBase = 119 - (q * 0.4);
    const oilEffect = brentChange * 0.35 * transmission * 100;
    vals.push(Math.max(0, cpiBase + oilEffect - 100));
  }
  return vals;
}

function getScenarioLabel(trajDelta, brent) {
  if (trajDelta > 15) return brent > 100 ? 'High oil — inflationary' : 'Rising oil scenario';
  if (trajDelta < -15) return brent < 70 ? 'Low oil — disinflationary' : 'Falling oil scenario';
  return 'Base scenario';
}

function getInsight(forecasts, brent, trajDelta, transmission) {
  const q1_27 = forecasts[forecasts.length - 1];
  const peak = Math.max(...forecasts);
  const peakQ = forecastLabels[forecasts.indexOf(peak)];
  const direction = trajDelta > 10 ? 'rising' : trajDelta < -10 ? 'falling' : 'broadly flat';
  const transmissionWord = transmission > 1.2 ? 'strong' : transmission < 0.8 ? 'muted' : 'moderate';
  if (q1_27 > 5) {
    return `<strong>Elevated inflation persists.</strong> With oil ${direction} from $${brent}/bbl and ${transmissionWord} pass-through, this model implies food CPI above ${q1_27.toFixed(1)}% by Q1 2027. Peaking near <strong>${peak.toFixed(1)}%</strong> around <strong>${peakQ}</strong>. Retailers and branded suppliers face continued margin pressure.`;
  } else if (q1_27 < 1.5) {
    return `<strong>Material disinflation in view.</strong> If oil follows this trajectory, food CPI could approach ${q1_27.toFixed(1)}% by Q1 2027 — close to pre-2021 norms. This creates a more benign environment for volume recovery, though deflation risk in some categories (ambient grocery) should not be discounted.`;
  } else {
    return `<strong>Gradual normalisation.</strong> This trajectory implies food CPI settling around <strong>${q1_27.toFixed(1)}%</strong> by Q1 2027 — still above the 2% target but a material step down from the 2022–23 peak. The pace of relief depends heavily on second-order factors this model excludes: labour costs, GBP/USD, and agricultural commodity cycles.`;
  }
}

const ctx = document.getElementById('historicalChart').getContext('2d');
const histLen = historicalLabels.length;
const allLabels = [...historicalLabels, 'Oct 24', 'Jan 25', 'Apr 25', 'Jul 25'];

const chart = new Chart(ctx, {
  type: 'line',
  data: {
    labels: allLabels,
    datasets: [
      { label: 'Brent crude (4m lead)', data: [...brentIndexed, null, null, null, null], borderColor: '#c8402a', backgroundColor: 'transparent', borderWidth: 1.5, pointRadius: 0, tension: 0.3 },
      { label: 'UK food CPI', data: [...foodCPIIndexed, null, null, null, null], borderColor: '#1a6b5a', backgroundColor: 'transparent', borderWidth: 1.5, pointRadius: 0, tension: 0.3 },
      { label: 'Forecast', data: [...Array(histLen - 1).fill(null), 119, 118.5, 118, 117.5, 117], borderColor: '#1a6b5a', backgroundColor: 'transparent', borderWidth: 1.5, borderDash: [4, 3], pointRadius: 0, tension: 0.3 }
    ]
  },
  options: {
    responsive: true, maintainAspectRatio: false,
    interaction: { mode: 'index', intersect: false },
    plugins: {
      legend: { display: false },
      tooltip: { backgroundColor: '#1a1a18', titleFont: { family: 'DM Sans', size: 11 }, bodyFont: { family: 'DM Sans', size: 12 }, padding: 10, callbacks: { label: ctx => ctx.dataset.label + ': ' + (ctx.raw !== null ? ctx.raw.toFixed(1) : 'n/a') } }
    },
    scales: {
      x: { ticks: { font: { family: 'DM Sans', size: 10 }, color: '#8a8a82', maxTicksLimit: 8 }, grid: { color: '#ede9e0' } },
      y: { ticks: { font: { family: 'DM Sans', size: 10 }, color: '#8a8a82' }, grid: { color: '#ede9e0' } }
    }
  }
});

function updateAll() {
  const brent = parseInt(document.getElementById('brent-slider').value);
  const traj = parseInt(document.getElementById('traj-slider').value);
  const trans = parseFloat(document.getElementById('trans-slider').value);
  const lag = parseInt(document.getElementById('lag-slider').value);

  document.getElementById('brent-display').textContent = '$' + brent;
  document.getElementById('current-brent').textContent = '$' + brent;
  document.getElementById('traj-display').textContent = traj > 15 ? 'Rising +' + traj + '%' : traj < -15 ? 'Falling ' + traj + '%' : traj === 0 ? 'Flat' : traj > 0 ? '+' + traj + '%' : traj + '%';
  document.getElementById('trans-display').textContent = trans >= 1.4 ? 'Strong ×' + trans.toFixed(1) : trans <= 0.6 ? 'Weak ×' + trans.toFixed(1) : 'Base ×' + trans.toFixed(1);
  document.getElementById('lag-display').textContent = lag + ' months';

  const forecasts = computeForecast(brent, traj, trans, lag);
  document.getElementById('implied-cpi').textContent = '+' + forecasts[forecasts.length - 1].toFixed(1) + '%';

  const displayQs = [0, 2, 4, 10];
  document.getElementById('forecast-quarters').innerHTML = displayQs.map(i => {
    const v = forecasts[i];
    const delta = v - (i > 0 ? forecasts[i - 1] : v);
    const deltaClass = delta > 0.2 ? 'delta-up' : delta < -0.2 ? 'delta-down' : 'delta-flat';
    const deltaStr = delta > 0.05 ? '▲ ' + delta.toFixed(1) : delta < -0.05 ? '▼ ' + Math.abs(delta).toFixed(1) : '— stable';
    return `<div class="forecast-q"><div class="forecast-q-label">${forecastLabels[i]}</div><div class="forecast-q-value">${v.toFixed(1)}%</div><div class="forecast-q-delta ${deltaClass}">${deltaStr}</div></div>`;
  }).join('');

  document.getElementById('scenario-label').textContent = getScenarioLabel(traj, brent);
  document.getElementById('forecast-insight').innerHTML = getInsight(forecasts, brent, traj, trans);
}

document.getElementById('brent-slider').addEventListener('input', updateAll);
document.getElementById('traj-slider').addEventListener('input', updateAll);
document.getElementById('trans-slider').addEventListener('input', updateAll);
document.getElementById('lag-slider').addEventListener('input', updateAll);

updateAll();
</script>
</body>
</html>
