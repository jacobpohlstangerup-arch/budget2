<h2 class="sr-only">Research project budget builder v6</h2>
<script src="https://cdnjs.cloudflare.com/ajax/libs/xlsx/0.18.5/xlsx.full.min.js"></script>
<style>
* { box-sizing: border-box; }
.wrap { padding: 1rem 0 2rem; }
.top-bar { display: flex; align-items: center; gap: 10px; margin-bottom: 1.25rem; flex-wrap: wrap; }
.top-bar h1 { font-size: 22px; font-weight: 500; color: var(--color-text-primary); margin: 0; flex: 1; min-width: 140px; }
.pill-group { display: flex; gap: 3px; }
.pill { padding: 5px 11px; font-size: 12px; cursor: pointer; border: 0.5px solid var(--color-border-secondary); border-radius: var(--border-radius-md); background: transparent; color: var(--color-text-secondary); white-space: nowrap; }
.pill.active { background: var(--color-background-info); color: var(--color-text-info); border-color: var(--color-border-info); font-weight: 500; }
.currency-toggle { display: flex; border: 0.5px solid var(--color-border-secondary); border-radius: var(--border-radius-md); overflow: hidden; }
.cur-btn { padding: 5px 13px; font-size: 12px; font-weight: 500; cursor: pointer; border: none; background: transparent; color: var(--color-text-secondary); transition: background 0.12s, color 0.12s; }
.cur-btn.active { background: var(--color-text-primary); color: var(--color-background-primary); }
.icon-btn { display: flex; align-items: center; gap: 5px; padding: 5px 12px; font-size: 12px; cursor: pointer; border: 0.5px solid var(--color-border-secondary); border-radius: var(--border-radius-md); background: transparent; color: var(--color-text-primary); white-space: nowrap; }
.icon-btn:hover { background: var(--color-background-secondary); }
.icon-btn:disabled { opacity: 0.5; cursor: not-allowed; }
.rate-bar { display: flex; align-items: center; gap: 8px; flex-wrap: wrap; padding: 8px 12px; background: var(--color-background-secondary); border: 0.5px solid var(--color-border-tertiary); border-radius: var(--border-radius-lg); margin-bottom: 1.25rem; font-size: 12px; color: var(--color-text-secondary); }
.rate-bar input { font-size: 13px; padding: 3px 7px; border: 0.5px solid var(--color-border-secondary); border-radius: var(--border-radius-md); background: var(--color-background-primary); color: var(--color-text-primary); width: 80px; }
.panel { border: 0.5px solid var(--color-border-tertiary); border-radius: var(--border-radius-lg); margin-bottom: 1.25rem; overflow: hidden; }
.panel-header { display: flex; align-items: center; justify-content: space-between; padding: 9px 14px; background: var(--color-background-secondary); cursor: pointer; }
.panel-title { font-size: 13px; font-weight: 500; color: var(--color-text-primary); display: flex; align-items: center; gap: 7px; }
.chevron { font-size: 14px; color: var(--color-text-tertiary); transition: transform 0.18s; display: inline-block; }
.chevron.open { transform: rotate(180deg); }
.rates-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(200px, 1fr)); gap: 8px; padding: 12px 14px; }
.rate-row { display: flex; flex-direction: column; gap: 3px; }
.rate-label { font-size: 11px; color: var(--color-text-secondary); }
.rate-inp { font-size: 13px; padding: 4px 7px; border: 0.5px solid var(--color-border-secondary); border-radius: var(--border-radius-md); background: var(--color-background-primary); color: var(--color-text-primary); width: 100%; }
.summary-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(115px, 1fr)); gap: 10px; margin-bottom: 1.25rem; }
.metric { background: var(--color-background-secondary); border-radius: var(--border-radius-md); padding: 10px 12px; }
.metric-label { font-size: 11px; color: var(--color-text-secondary); margin: 0 0 3px; }
.metric-value { font-size: 15px; font-weight: 500; color: var(--color-text-primary); margin: 0; }
.section { margin-bottom: 1rem; border: 0.5px solid var(--color-border-tertiary); border-radius: var(--border-radius-lg); overflow: hidden; }
.section-header { display: flex; align-items: center; justify-content: space-between; padding: 9px 14px; background: var(--color-background-secondary); cursor: pointer; user-select: none; }
.section-title { font-size: 13px; font-weight: 500; color: var(--color-text-primary); display: flex; align-items: center; gap: 7px; }
.section-total { font-size: 13px; font-weight: 500; color: var(--color-text-primary); }
.section-body { border-top: 0.5px solid var(--color-border-tertiary); }
.tbl-wrap { overflow-x: auto; }
table { width: 100%; border-collapse: collapse; table-layout: fixed; min-width: 480px; }
th { font-size: 11px; font-weight: 500; color: var(--color-text-secondary); text-align: left; padding: 6px 8px; border-bottom: 0.5px solid var(--color-border-tertiary); background: var(--color-background-primary); }
td { font-size: 12px; color: var(--color-text-primary); padding: 5px 8px; border-bottom: 0.5px solid var(--color-border-tertiary); vertical-align: middle; }
tr:last-child td { border-bottom: none; }
tr.hidden-row { display: none; }
tr:not(.hidden-row):hover td { background: var(--color-background-secondary); }
.inst-badge { font-size: 10px; padding: 1px 5px; border-radius: var(--border-radius-md); background: var(--color-background-secondary); color: var(--color-text-secondary); white-space: nowrap; }
.num-inp { width: 100%; font-size: 12px; padding: 3px 5px; border: 0.5px solid var(--color-border-secondary); border-radius: var(--border-radius-md); background: var(--color-background-primary); color: var(--color-text-primary); text-align: right; }
.num-inp:focus { outline: none; box-shadow: 0 0 0 2px var(--color-border-info); }
.row-total { font-weight: 500; text-align: right; font-size: 12px; }
.section-foot { display: flex; justify-content: space-between; align-items: center; padding: 7px 14px; border-top: 0.5px solid var(--color-border-tertiary); background: var(--color-background-secondary); }
.section-foot-label { font-size: 11px; color: var(--color-text-secondary); }
.section-foot-val { font-size: 13px; font-weight: 500; color: var(--color-text-primary); }
.grand-foot { display: flex; justify-content: space-between; align-items: center; padding: 12px 16px; border: 0.5px solid var(--color-border-secondary); border-radius: var(--border-radius-lg); margin-top: 1rem; }
.grand-label { font-size: 13px; color: var(--color-text-secondary); }
.grand-val { font-size: 20px; font-weight: 500; color: var(--color-text-primary); }
#dl-area { margin-bottom: 10px; }
#dl-link { display: inline-flex; align-items: center; gap: 6px; padding: 7px 16px; font-size: 13px; font-weight: 500; border: 0.5px solid var(--color-border-success); border-radius: var(--border-radius-md); background: var(--color-background-success); color: var(--color-text-success); text-decoration: none; }
</style>

<div class="wrap">
  <div class="top-bar">
    <h1>Research budget</h1>
    <div style="display:flex;align-items:center;gap:6px;flex-wrap:wrap;">
      <span style="font-size:12px;color:var(--color-text-secondary)">Years:</span>
      <div class="pill-group" id="year-btns">
        <button class="pill active" data-y="1">1</button>
        <button class="pill" data-y="2">2</button>
        <button class="pill" data-y="3">3</button>
        <button class="pill" data-y="4">4</button>
        <button class="pill" data-y="5">5</button>
      </div>
      <span style="font-size:12px;color:var(--color-text-secondary);margin-left:4px">Institution:</span>
      <div class="pill-group" id="inst-btns">
        <button class="pill active" data-inst="all">All</button>
        <button class="pill" data-inst="Rigshospitalet">Rigshospitalet</button>
        <button class="pill" data-inst="DTU">DTU</button>
      </div>
      <div class="currency-toggle" title="Skift visningsvaluta" style="margin-left:4px">
        <button class="cur-btn active" id="btn-dkk">DKK</button>
        <button class="cur-btn" id="btn-eur">EUR</button>
      </div>
      <button class="icon-btn" id="export-btn"><i class="ti ti-download" aria-hidden="true"></i> Export Excel</button>
    </div>
  </div>

  <div id="dl-area"></div>

  <div class="rate-bar">
    <i class="ti ti-arrows-exchange" aria-hidden="true" style="font-size:15px"></i>
    <span>1 EUR =</span>
    <input type="number" id="rate-inp" value="7.4728" step="0.0001" />
    <span>DKK</span>
    <span style="color:var(--color-text-tertiary);font-size:11px">(bruges til EUR-visning og Excel-export — kurs pr. 6. maj 2026)</span>
  </div>

  <div class="panel">
    <div class="panel-header" id="rates-toggle">
      <span class="panel-title"><i class="ti ti-coin" aria-hidden="true" style="font-size:15px"></i> Lønsatser (DKK / år ved 1,0 FTE)</span>
      <i class="ti ti-chevron-down chevron open" id="rates-chev" aria-hidden="true"></i>
    </div>
    <div id="rates-body">
      <div class="rates-grid" id="rates-grid"></div>
      <div style="padding:0 14px 10px;font-size:11px;color:var(--color-text-tertiary)">Budget = FTE × lønsats. Ret budgetfeltet manuelt for at låse det.</div>
    </div>
  </div>

  <div class="summary-grid" id="summary-grid"></div>
  <div id="sections-container"></div>
  <div class="grand-foot">
    <span class="grand-label">Samlet total (alle år)</span>
    <span class="grand-val" id="grand-total">DKK 0</span>
  </div>
</div>

<script>
let eurRate = 7.4728;
let displayCurrency = 'DKK';

function toDisplay(dkk) { return displayCurrency === 'EUR' ? dkk / eurRate : dkk; }
function fmtDisplay(dkk) {
  const v = Math.round(toDisplay(dkk));
  return displayCurrency === 'EUR'
    ? '€ ' + v.toLocaleString('da-DK')
    : 'DKK ' + v.toLocaleString('da-DK');
}

const SALARY_ROWS = [
  { sub: 'Consultant', inst: 'Rigshospitalet', rateKey: 'consultant_rh' },
  { sub: 'Pre-graduate scholar', inst: 'Rigshospitalet', rateKey: 'pregrad_rh' },
  { sub: 'Scientist / researcher', inst: 'Rigshospitalet', rateKey: 'scientist_rh' },
  { sub: 'PhD student', inst: 'Rigshospitalet', rateKey: 'phd_rh' },
  { sub: 'Research technician / nurse', inst: 'Rigshospitalet', rateKey: 'tech_rh' },
  { sub: 'Project employees at admin. institution', inst: 'Rigshospitalet', rateKey: 'projempl_rh' },
  { sub: 'Project employees', inst: 'DTU', rateKey: 'projempl_dtu' },
  { sub: 'PhD student', inst: 'DTU', rateKey: 'phd_dtu' },
  { sub: 'Postdoc', inst: 'DTU', rateKey: 'postdoc_dtu' },
  { sub: 'Pre-graduate scholar', inst: 'DTU', rateKey: 'pregrad_dtu' },
];

const CATEGORIES = [
  { id: 'salary', label: 'Salary', color: '#E6F1FB', tcolor: '#185FA5', hasFte: true, rows: SALARY_ROWS },
  { id: 'operation', label: 'Operation', color: '#E1F5EE', tcolor: '#0F6E56', hasFte: false, rows: [
    { sub: 'Data management', inst: 'DTU' }, { sub: 'Subcontractor costs', inst: 'Rigshospitalet' },
    { sub: 'Bench fee', inst: 'Rigshospitalet' }, { sub: 'Infrastructure', inst: 'DTU' },
    { sub: 'Project specific costs', inst: 'Rigshospitalet' }, { sub: 'Operating expenses', inst: 'Rigshospitalet' },
    { sub: 'Equipment', inst: 'DTU' }, { sub: 'Equipment', inst: 'Rigshospitalet' },
  ]},
  { id: 'dissemination', label: 'Dissemination, training & education', color: '#FAEEDA', tcolor: '#854F0B', hasFte: false, rows: [
    { sub: 'Travel', inst: 'Rigshospitalet' }, { sub: 'Training', inst: 'Rigshospitalet' },
    { sub: 'Conference participation', inst: 'Rigshospitalet' }, { sub: 'Conference participation', inst: 'DTU' },
    { sub: 'Collaborative activities', inst: 'Rigshospitalet' }, { sub: 'Collaborative activities', inst: 'DTU' },
    { sub: 'Publication costs', inst: 'Rigshospitalet' },
  ]},
  { id: 'admin', label: 'Administration', color: '#F1EFE8', tcolor: '#5F5E5A', hasFte: false, rows: [
    { sub: 'Direct administrative expenses', inst: 'Rigshospitalet' },
  ]},
  { id: 'supplement', label: 'Project supplement', color: '#EEEDFE', tcolor: '#534AB7', hasFte: false, rows: [
    { sub: 'Project supplement', inst: 'DTU' },
  ]},
];

const RATE_DEFS = [
  { key: 'consultant_rh',  label: 'Consultant (RH)',                        default: 1080000 },
  { key: 'pregrad_rh',     label: 'Pre-graduate scholar (RH)',               default: 150000  },
  { key: 'scientist_rh',   label: 'Scientist / researcher (RH)',             default: 624000  },
  { key: 'phd_rh',         label: 'PhD student (RH)',                        default: 624000  },
  { key: 'tech_rh',        label: 'Research technician / nurse (RH)',        default: 504000  },
  { key: 'projempl_rh',    label: 'Project employees (RH)',                  default: 550000  },
  { key: 'projempl_dtu',   label: 'Project employees (DTU)',                 default: 550000  },
  { key: 'phd_dtu',        label: 'PhD student (DTU)',                       default: 530000  },
  { key: 'postdoc_dtu',    label: 'Postdoc (DTU)',                           default: 650000  },
  { key: 'pregrad_dtu',    label: 'Pre-graduate scholar (DTU)',              default: 150000  },
];

let numYears = 1, instFilter = 'all', state = {}, rates = {}, collapsed = {};
RATE_DEFS.forEach(r => { rates[r.key] = r.default; });

function sk(c, r, y, f) { return `${c}_${r}_y${y}_${f}`; }
function getVal(c, r, y, f) { return state[sk(c, r, y, f)] || 0; }
function setVal(c, r, y, f, v) { state[sk(c, r, y, f)] = parseFloat(v) || 0; }

function catTotal(catId) {
  const cat = CATEGORIES.find(c => c.id === catId); let t = 0;
  cat.rows.forEach((row, ri) => {
    if (instFilter !== 'all' && row.inst !== instFilter) return;
    for (let y = 1; y <= numYears; y++) t += getVal(catId, ri, y, 'budget');
  });
  return t;
}
function yearTotal(y) {
  let t = 0;
  CATEGORIES.forEach(cat => cat.rows.forEach((row, ri) => {
    if (instFilter !== 'all' && row.inst !== instFilter) return;
    t += getVal(cat.id, ri, y, 'budget');
  }));
  return t;
}
function grandTotal() { let t = 0; for (let y = 1; y <= numYears; y++) t += yearTotal(y); return t; }

function updateTotals() {
  document.getElementById('grand-total').textContent = fmtDisplay(grandTotal());
  const sg = document.getElementById('summary-grid'); sg.innerHTML = '';
  for (let y = 1; y <= numYears; y++) {
    const m = document.createElement('div'); m.className = 'metric';
    m.innerHTML = `<p class="metric-label">År ${y} total</p><p class="metric-value">${fmtDisplay(yearTotal(y))}</p>`;
    sg.appendChild(m);
  }
  CATEGORIES.forEach(cat => {
    const ct = catTotal(cat.id);
    const el = document.getElementById('sec-total-' + cat.id); if (el) el.textContent = fmtDisplay(ct);
    const fl = document.getElementById('sec-foot-' + cat.id); if (fl) fl.textContent = fmtDisplay(ct);
    cat.rows.forEach((_, ri) => {
      let rowT = 0; for (let y = 1; y <= numYears; y++) rowT += getVal(cat.id, ri, y, 'budget');
      const rt = document.getElementById(`rt_${cat.id}_${ri}`); if (rt) rt.textContent = fmtDisplay(rowT);
    });
  });
  document.querySelectorAll('.budget-th').forEach(th => {
    th.textContent = `År ${th.dataset.y} budget (${displayCurrency === 'EUR' ? 'EUR' : 'DKK'})`;
  });
}

function applyInstFilter() {
  CATEGORIES.forEach(cat => cat.rows.forEach((row, ri) => {
    const tr = document.getElementById(`tr_${cat.id}_${ri}`);
    if (tr) tr.classList.toggle('hidden-row', instFilter !== 'all' && row.inst !== instFilter);
  }));
  updateTotals();
}

function buildRatesPanel() {
  const grid = document.getElementById('rates-grid'); grid.innerHTML = '';
  RATE_DEFS.forEach(r => {
    const div = document.createElement('div'); div.className = 'rate-row';
    div.innerHTML = `<span class="rate-label">${r.label}</span><input class="rate-inp" type="number" min="0" step="1000" value="${rates[r.key]}" data-key="${r.key}" />`;
    grid.appendChild(div);
  });
  grid.addEventListener('input', e => {
    const el = e.target; if (!el.dataset.key) return;
    rates[el.dataset.key] = parseFloat(el.value) || 0;
    SALARY_ROWS.forEach((row, ri) => {
      if (row.rateKey !== el.dataset.key) return;
      for (let y = 1; y <= numYears; y++) {
        if (state[sk('salary', ri, y, 'budget_manual')] !== undefined) return;
        const auto = Math.round(getVal('salary', ri, y, 'fte') * rates[row.rateKey]);
        setVal('salary', ri, y, 'budget', auto);
        const inp = document.getElementById(`bi_salary_${ri}_${y}`); if (inp) inp.value = auto || '';
      }
    });
    updateTotals();
  });
}

function buildTable(cat) {
  const years = Array.from({length: numYears}, (_, i) => i + 1);
  let cols = `<col style="width:150px"><col style="width:78px">`;
  if (cat.hasFte) years.forEach(() => { cols += `<col style="width:55px">`; });
  years.forEach(() => { cols += `<col style="width:105px">`; });
  cols += `<col style="width:95px">`;

  let thead = `<thead><tr><th>Underkategori</th><th>Institution</th>`;
  if (cat.hasFte) years.forEach(y => { thead += `<th style="text-align:center">År ${y} FTE</th>`; });
  years.forEach(y => { thead += `<th class="budget-th" data-y="${y}" style="text-align:right">År ${y} budget (${displayCurrency === 'EUR' ? 'EUR' : 'DKK'})</th>`; });
  thead += `<th style="text-align:right">Total</th></tr></thead>`;

  let tbody = '<tbody>';
  cat.rows.forEach((row, ri) => {
    const hide = instFilter !== 'all' && row.inst !== instFilter;
    tbody += `<tr id="tr_${cat.id}_${ri}" ${hide ? 'class="hidden-row"' : ''}>`;
    tbody += `<td style="font-size:11px">${row.sub}</td><td><span class="inst-badge">${row.inst}</span></td>`;
    if (cat.hasFte) years.forEach(y => {
      const v = getVal(cat.id, ri, y, 'fte') || '';
      // step=0.1 som ønsket
      tbody += `<td style="text-align:center"><input id="fi_${cat.id}_${ri}_${y}" class="num-inp" type="number" min="0" max="1" step="0.1" placeholder="0" value="${v}" style="width:50px;text-align:center" data-cat="${cat.id}" data-ri="${ri}" data-y="${y}" data-field="fte" /></td>`;
    });
    years.forEach(y => {
      const v = getVal(cat.id, ri, y, 'budget') || '';
      tbody += `<td><input id="bi_${cat.id}_${ri}_${y}" class="num-inp" type="number" min="0" step="1000" placeholder="0" value="${v}" data-cat="${cat.id}" data-ri="${ri}" data-y="${y}" data-field="budget" /></td>`;
    });
    let rowT = 0; for (let y = 1; y <= numYears; y++) rowT += getVal(cat.id, ri, y, 'budget');
    tbody += `<td class="row-total" id="rt_${cat.id}_${ri}">${fmtDisplay(rowT)}</td></tr>`;
  });
  tbody += '</tbody>';
  return `<div class="tbl-wrap"><table><colgroup>${cols}</colgroup>${thead}${tbody}</table></div>`;
}

function render() {
  const container = document.getElementById('sections-container'); container.innerHTML = '';
  CATEGORIES.forEach(cat => {
    // Default: open. collapsed[id] = true means closed
    const isOpen = collapsed[cat.id] !== true;
    const ct = catTotal(cat.id);
    const sec = document.createElement('div'); sec.className = 'section';
    sec.innerHTML = `
      <div class="section-header" id="sh-${cat.id}">
        <span class="section-title">
          <span style="display:inline-block;width:9px;height:9px;border-radius:2px;background:${cat.color};border:1px solid ${cat.tcolor}66"></span>
          ${cat.label}
        </span>
        <span style="display:flex;align-items:center;gap:10px">
          <span class="section-total" id="sec-total-${cat.id}">${fmtDisplay(ct)}</span>
          <i class="ti ti-chevron-down chevron ${isOpen ? 'open' : ''}" aria-hidden="true"></i>
        </span>
      </div>
      <div class="section-body" id="sb-${cat.id}" style="display:${isOpen ? 'block' : 'none'}">
        ${buildTable(cat)}
        <div class="section-foot">
          <span class="section-foot-label">Subtotal — ${cat.label}</span>
          <span class="section-foot-val" id="sec-foot-${cat.id}">${fmtDisplay(ct)}</span>
        </div>
      </div>`;
    container.appendChild(sec);

    // Toggle collapse/expand — fix: capture isOpen at definition time
    sec.querySelector(`#sh-${cat.id}`).addEventListener('click', () => {
      const currentlyOpen = collapsed[cat.id] !== true;
      collapsed[cat.id] = currentlyOpen; // true = closed
      const body = sec.querySelector(`#sb-${cat.id}`);
      const chev = sec.querySelector('.chevron');
      body.style.display = currentlyOpen ? 'none' : 'block';
      chev.classList.toggle('open', !currentlyOpen);
    });
  });

  container.addEventListener('input', e => {
    const el = e.target; if (!el.dataset.cat) return;
    const { cat: catId, ri, y, field } = el.dataset;
    const riN = parseInt(ri), yN = parseInt(y);
    if (field === 'fte') {
      setVal(catId, riN, yN, 'fte', el.value);
      const row = SALARY_ROWS[riN];
      if (row) {
        const auto = Math.round((parseFloat(el.value) || 0) * (rates[row.rateKey] || 0));
        if (state[sk(catId, riN, yN, 'budget_manual')] === undefined) {
          setVal(catId, riN, yN, 'budget', auto);
          const bi = document.getElementById(`bi_${catId}_${riN}_${yN}`); if (bi) bi.value = auto || '';
        }
      }
    } else if (field === 'budget') {
      const v = parseFloat(el.value) || 0;
      if (catId === 'salary') {
        const row = SALARY_ROWS[riN];
        const auto = row ? Math.round(getVal(catId, riN, yN, 'fte') * (rates[row.rateKey] || 0)) : 0;
        if (v !== auto) state[sk(catId, riN, yN, 'budget_manual')] = v;
        else delete state[sk(catId, riN, yN, 'budget_manual')];
      }
      setVal(catId, riN, yN, 'budget', v);
    }
    updateTotals();
  });
  updateTotals();
}

function exportExcel() {
  // Collect all data from state and send to backend via Anthropic API to build styled xlsx
  const btn = document.getElementById('export-btn');
  btn.disabled = true; btn.innerHTML = '<i class="ti ti-loader" aria-hidden="true"></i> Bygger Excel...';

  const years = Array.from({length: numYears}, (_, i) => i + 1);

  // Build structured data payload for the API
  const payload = { numYears, instFilter, eurRate, categories: [] };
  CATEGORIES.forEach(cat => {
    const catData = { id: cat.id, label: cat.label, hasFte: cat.hasFte, rows: [] };
    cat.rows.forEach((row, ri) => {
      if (instFilter !== 'all' && row.inst !== instFilter) return;
      let hasAny = false;
      const rowData = { sub: row.sub, inst: row.inst, years: [] };
      years.forEach(y => {
        const fte = cat.hasFte ? getVal(cat.id, ri, y, 'fte') : null;
        const bud = getVal(cat.id, ri, y, 'budget');
        rowData.years.push({ y, fte, budget: bud });
        if (bud > 0 || (fte && fte > 0)) hasAny = true;
      });
      if (hasAny) catData.rows.push(rowData);
    });
    if (catData.rows.length > 0) payload.categories.push(catData);
  });

  // Use XLSX client-side with styling via SheetJS
  try {
    const wb = XLSX.utils.book_new();
    const wsData = [];

    // Header row
    const hdr = ['Category', 'Subcategory', 'Institution'];
    years.forEach(y => {
      if (true) hdr.push(`Year ${y} Budget (DKK)`);
      hdr.push(`Year ${y} FTE`);
    });
    hdr.push('Total (DKK)');
    wsData.push(hdr);

    payload.categories.forEach(cat => {
      cat.rows.forEach(row => {
        const dr = [cat.label, row.sub, row.inst];
        let rowTotal = 0;
        row.years.forEach(yData => {
          dr.push(yData.budget || 0);
          dr.push(cat.hasFte ? (yData.fte != null ? yData.fte : '') : '');
          rowTotal += yData.budget || 0;
        });
        dr.push(rowTotal);
        wsData.push(dr);
      });
      // Subtotal row
      const sub = [cat.label + ' — subtotal', '', ''];
      let subTotal = 0;
      years.forEach(y => {
        let yt = 0;
        cat.rows.forEach(row => { const yData = row.years.find(d => d.y === y); yt += yData ? yData.budget || 0 : 0; });
        sub.push(yt); sub.push(''); subTotal += yt;
      });
      sub.push(subTotal);
      wsData.push(sub);
      wsData.push([]);
    });

    // Grand total
    const tot = ['GRAND TOTAL', '', ''];
    years.forEach(y => {
      let yt = 0;
      payload.categories.forEach(cat => cat.rows.forEach(row => { const yData = row.years.find(d => d.y === y); yt += yData ? yData.budget || 0 : 0; }));
      tot.push(yt); tot.push('');
    });
    let gt = 0;
    payload.categories.forEach(cat => cat.rows.forEach(row => row.years.forEach(yData => { gt += yData.budget || 0; })));
    tot.push(gt);
    wsData.push(tot);

    const ws = XLSX.utils.aoa_to_sheet(wsData);

    // Column widths
    const colW = [{wch:20},{wch:38},{wch:18}];
    years.forEach(() => { colW.push({wch:18}); colW.push({wch:10}); });
    colW.push({wch:18});
    ws['!cols'] = colW;

    XLSX.utils.book_append_sheet(wb, ws, 'Budget');

    // Assumptions sheet
    const assump = [['Lønsatser',''],['Rolle','DKK/år ved 1,0 FTE']];
    RATE_DEFS.forEach(r => assump.push([r.label, rates[r.key]]));
    assump.push([]); assump.push(['EUR/DKK kurs', eurRate]);
    const aws = XLSX.utils.aoa_to_sheet(assump);
    aws['!cols'] = [{wch:36},{wch:20}];
    XLSX.utils.book_append_sheet(wb, aws, 'Forudsætninger');

    const wbout = XLSX.write(wb, {bookType:'xlsx', type:'base64'});
    document.getElementById('dl-area').innerHTML = `<a id="dl-link" href="data:application/vnd.openxmlformats-officedocument.spreadsheetml.sheet;base64,${wbout}" download="Research_Budget.xlsx"><i class="ti ti-file-spreadsheet" aria-hidden="true"></i> Download Research_Budget.xlsx</a>`;
  } catch(err) {
    document.getElementById('dl-area').innerHTML = `<span style="font-size:12px;color:var(--color-text-danger)">Fejl: ${err.message}</span>`;
  }
  btn.disabled = false; btn.innerHTML = '<i class="ti ti-download" aria-hidden="true"></i> Export Excel';
}

// Event listeners
document.getElementById('btn-dkk').addEventListener('click', () => {
  displayCurrency = 'DKK';
  document.getElementById('btn-dkk').classList.add('active');
  document.getElementById('btn-eur').classList.remove('active');
  updateTotals();
});
document.getElementById('btn-eur').addEventListener('click', () => {
  displayCurrency = 'EUR';
  document.getElementById('btn-eur').classList.add('active');
  document.getElementById('btn-dkk').classList.remove('active');
  updateTotals();
});
document.getElementById('year-btns').addEventListener('click', e => {
  const btn = e.target.closest('.pill'); if (!btn || !btn.dataset.y) return;
  numYears = parseInt(btn.dataset.y);
  document.querySelectorAll('#year-btns .pill').forEach(b => b.classList.toggle('active', b.dataset.y == numYears));
  render();
});
document.getElementById('inst-btns').addEventListener('click', e => {
  const btn = e.target.closest('.pill'); if (!btn || !btn.dataset.inst) return;
  instFilter = btn.dataset.inst;
  document.querySelectorAll('#inst-btns .pill').forEach(b => b.classList.toggle('active', b.dataset.inst === instFilter));
  applyInstFilter();
});
document.getElementById('rates-toggle').addEventListener('click', () => {
  const body = document.getElementById('rates-body'), chev = document.getElementById('rates-chev');
  const open = body.style.display !== 'none';
  body.style.display = open ? 'none' : 'block'; chev.classList.toggle('open', !open);
});
document.getElementById('export-btn').addEventListener('click', exportExcel);
document.getElementById('rate-inp').addEventListener('input', e => {
  eurRate = parseFloat(e.target.value) || 7.4728; updateTotals();
});

buildRatesPanel(); render();
</script>
