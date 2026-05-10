<!DOCTYPE html>
<html lang="da">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width,initial-scale=1.0"/>
<title>Research Budget Builder</title>
<link rel="preconnect" href="https://fonts.googleapis.com"/>
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:ital,wght@0,300;0,400;0,500;0,600;1,400&family=DM+Mono:wght@400;500&display=swap" rel="stylesheet"/>
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@tabler/icons-webfont@2.44.0/tabler-icons.min.css"/>
<script src="https://cdnjs.cloudflare.com/ajax/libs/Sortable/1.15.2/Sortable.min.js"></script>
<style>
:root{
  --bg:#F7F6F3;--surface:#FFFFFF;--surface2:#F0EFE9;--surface3:#E8E6DE;
  --text:#1C1B18;--text2:#6B6860;--text3:#A8A69E;
  --accent:#C0392B;--accent-light:#FDECEA;--accent-text:#7B1A12;
  --blue:#1A56B0;--blue-light:#EBF2FD;--blue-total:#D6E4F7;
  --green:#1A7A4A;--green-light:#E6F5ED;
  --border:#E2E0D8;--border2:#C8C6BC;
  --radius:8px;--radius-lg:12px;--radius-xl:16px;
  --shadow:0 1px 3px rgba(0,0,0,.08),0 1px 2px rgba(0,0,0,.06);
  --shadow-lg:0 4px 16px rgba(0,0,0,.10);
  font-family:'DM Sans',sans-serif;
}
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0;}
body{background:var(--bg);color:var(--text);min-height:100vh;font-size:14px;line-height:1.5;}
.mono{font-family:'DM Mono',monospace;}

/* ── Layout ── */
.app{max-width:1100px;margin:0 auto;padding:2rem 1.25rem 5rem;}

/* ── Header ── */
.app-header{display:flex;align-items:center;justify-content:space-between;margin-bottom:2rem;flex-wrap:wrap;gap:12px;}
.app-title{font-size:20px;font-weight:600;letter-spacing:-.3px;}
.app-title span{color:var(--text3);font-weight:400;}
.header-controls{display:flex;align-items:center;gap:8px;flex-wrap:wrap;}

/* ── Pill groups ── */
.pill-group{display:flex;gap:2px;background:var(--surface2);border-radius:var(--radius);padding:3px;}
.pill{padding:4px 11px;font-size:12px;font-weight:500;cursor:pointer;border:none;border-radius:6px;background:transparent;color:var(--text2);transition:all .15s;}
.pill.active{background:var(--surface);color:var(--text);box-shadow:var(--shadow);}

/* ── Icon buttons ── */
.icon-btn{display:inline-flex;align-items:center;gap:5px;padding:6px 12px;font-size:12px;font-weight:500;cursor:pointer;border:1px solid var(--border2);border-radius:var(--radius);background:var(--surface);color:var(--text);font-family:inherit;transition:all .15s;white-space:nowrap;}
.icon-btn:hover{background:var(--surface2);border-color:var(--border2);}
.icon-btn:disabled{opacity:.45;cursor:not-allowed;}
.icon-btn.primary{background:var(--accent);color:#fff;border-color:var(--accent);}
.icon-btn.primary:hover{background:#a93226;}
.icon-btn.success{background:var(--green);color:#fff;border-color:var(--green);}
.icon-btn.danger{color:var(--accent);border-color:transparent;background:transparent;}
.icon-btn.danger:hover{background:var(--accent-light);}
.icon-btn.ghost{border-color:transparent;background:transparent;color:var(--text2);}
.icon-btn.ghost:hover{background:var(--surface2);color:var(--text);}

/* ── Lang toggle ── */
.lang-toggle{display:flex;border:1px solid var(--border2);border-radius:var(--radius);overflow:hidden;font-size:12px;font-weight:600;}
.lang-btn{padding:5px 10px;cursor:pointer;border:none;background:transparent;color:var(--text2);font-family:inherit;font-weight:600;font-size:12px;transition:all .15s;}
.lang-btn.active{background:var(--text);color:var(--bg);}

/* ── Summary cards ── */
.summary-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(130px,1fr));gap:10px;margin-bottom:1.5rem;}
.metric{background:var(--surface);border:1px solid var(--border);border-radius:var(--radius-lg);padding:14px 16px;}
.metric-label{font-size:11px;color:var(--text3);text-transform:uppercase;letter-spacing:.5px;margin-bottom:4px;}
.metric-value{font-size:16px;font-weight:600;font-family:'DM Mono',monospace;}
.metric-sub{font-size:11px;color:var(--text3);margin-top:2px;font-family:'DM Mono',monospace;}

/* ── Overhead bar ── */
.overhead-bar{display:flex;align-items:center;gap:10px;flex-wrap:wrap;padding:10px 14px;background:var(--surface);border:1px solid var(--border);border-radius:var(--radius-lg);margin-bottom:1.25rem;font-size:13px;}
.overhead-bar label{color:var(--text2);font-weight:500;}
.overhead-bar input{width:70px;font-size:13px;padding:4px 8px;border:1px solid var(--border2);border-radius:var(--radius);background:var(--bg);color:var(--text);font-family:'DM Mono',monospace;text-align:right;}
.overhead-result{font-weight:600;font-family:'DM Mono',monospace;color:var(--blue);}

/* ── Rate panel ── */
.panel{border:1px solid var(--border);border-radius:var(--radius-lg);margin-bottom:1.25rem;overflow:hidden;background:var(--surface);}
.panel-header{display:flex;align-items:center;justify-content:space-between;padding:10px 16px;background:var(--surface2);cursor:pointer;user-select:none;}
.panel-title{font-size:13px;font-weight:600;display:flex;align-items:center;gap:7px;color:var(--text);}
.chevron{font-size:14px;color:var(--text3);transition:transform .2s;display:inline-block;}
.chevron.open{transform:rotate(180deg);}
.rates-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(210px,1fr));gap:8px;padding:14px 16px;}
.rate-row{display:flex;flex-direction:column;gap:3px;}
.rate-label{font-size:11px;color:var(--text2);font-weight:500;}
.rate-inp{font-size:12px;padding:5px 8px;border:1px solid var(--border2);border-radius:var(--radius);background:var(--bg);color:var(--text);font-family:'DM Mono',monospace;text-align:right;}
.rate-inp:focus{outline:none;box-shadow:0 0 0 2px var(--blue-light);border-color:var(--blue);}

/* ── EUR rate bar ── */
.eur-bar{display:flex;align-items:center;gap:8px;padding:8px 14px;background:var(--surface);border:1px solid var(--border);border-radius:var(--radius-lg);margin-bottom:1.25rem;font-size:12px;color:var(--text2);}
.eur-bar input{width:80px;font-size:12px;padding:3px 6px;border:1px solid var(--border2);border-radius:var(--radius);background:var(--bg);color:var(--text);font-family:'DM Mono',monospace;text-align:right;}

/* ── Sections ── */
.sections-wrap{display:flex;flex-direction:column;gap:10px;}
.section{border:1px solid var(--border);border-radius:var(--radius-xl);overflow:hidden;background:var(--surface);transition:box-shadow .15s;}
.section:hover{box-shadow:var(--shadow);}
.section-header{display:flex;align-items:center;gap:10px;padding:11px 16px;background:var(--surface2);cursor:pointer;user-select:none;}
.section-drag-handle{color:var(--text3);cursor:grab;font-size:16px;flex-shrink:0;}
.section-drag-handle:active{cursor:grabbing;}
.section-dot{width:10px;height:10px;border-radius:3px;flex-shrink:0;}
.section-name{font-size:13px;font-weight:600;flex:1;}
.section-name input{font-size:13px;font-weight:600;border:none;background:transparent;color:var(--text);font-family:'DM Sans',sans-serif;width:100%;outline:none;}
.section-name input:focus{background:var(--surface);border-radius:4px;padding:2px 6px;}
.section-controls{display:flex;align-items:center;gap:6px;}
.section-total-badge{font-size:12px;font-weight:600;font-family:'DM Mono',monospace;color:var(--text);white-space:nowrap;}
.section-body{border-top:1px solid var(--border);}

/* ── Table ── */
.tbl-wrap{overflow-x:auto;}
table{width:100%;border-collapse:collapse;table-layout:auto;font-size:12px;}
th{font-size:11px;font-weight:600;color:var(--text3);text-align:left;padding:7px 10px;border-bottom:1px solid var(--border);background:var(--surface);white-space:nowrap;text-transform:uppercase;letter-spacing:.4px;}
th.right{text-align:right;}
td{padding:6px 10px;border-bottom:1px solid var(--border);vertical-align:middle;color:var(--text);}
tr:last-child td{border-bottom:none;}
tr.data-row:hover td{background:var(--bg);}
tr.hidden-row{display:none;}
.drag-row{cursor:grab;}
.drag-row:active{cursor:grabbing;}
.drag-row td:first-child{color:var(--text3);}

/* ── Inputs in table ── */
.num-inp{width:100%;font-size:12px;padding:3px 5px;border:1px solid transparent;border-radius:5px;background:transparent;color:var(--text);text-align:right;font-family:'DM Mono',monospace;}
.num-inp:hover{border-color:var(--border2);background:var(--bg);}
.num-inp:focus{outline:none;border-color:var(--blue);background:var(--surface);box-shadow:0 0 0 2px var(--blue-light);}
.text-inp{width:100%;font-size:12px;padding:3px 6px;border:1px solid transparent;border-radius:5px;background:transparent;color:var(--text);font-family:'DM Sans',sans-serif;}
.text-inp:hover{border-color:var(--border2);background:var(--bg);}
.text-inp:focus{outline:none;border-color:var(--blue);background:var(--surface);}
.desc-inp{font-size:11px;color:var(--text3);font-style:italic;}
.desc-inp::placeholder{color:var(--text3);}

/* ── Row totals ── */
.row-total{font-weight:600;text-align:right;font-family:'DM Mono',monospace;white-space:nowrap;}

/* ── Subtotal rows ── */
.subtotal-row td{background:var(--blue-total);font-weight:600;font-family:'DM Mono',monospace;}
.subtotal-row td:first-child{font-family:'DM Sans',sans-serif;font-size:12px;}
.grandtotal-row td{background:var(--blue-total);font-weight:700;font-size:13px;font-family:'DM Mono',monospace;border-top:2px solid var(--border2);}
.grandtotal-row td:first-child{font-family:'DM Sans',sans-serif;}
.overhead-row td{background:#EBF5FF;font-weight:600;font-family:'DM Mono',monospace;font-size:11px;color:var(--blue);}

/* ── Section footer ── */
.section-foot{display:flex;justify-content:space-between;align-items:center;padding:8px 16px;background:var(--surface2);border-top:1px solid var(--border);gap:10px;flex-wrap:wrap;}
.section-foot-add{display:flex;gap:6px;}

/* ── Grand total ── */
.grand-footer{display:flex;align-items:center;justify-content:space-between;padding:14px 20px;background:var(--surface);border:1px solid var(--border2);border-radius:var(--radius-xl);margin-top:1.25rem;}
.grand-label{font-size:14px;color:var(--text2);font-weight:500;}
.grand-val{font-size:22px;font-weight:700;font-family:'DM Mono',monospace;}
.grand-sub{font-size:12px;color:var(--text3);font-family:'DM Mono',monospace;}

/* ── Add section ── */
.add-section-btn{display:flex;align-items:center;justify-content:center;gap:8px;padding:12px;border:2px dashed var(--border2);border-radius:var(--radius-xl);background:transparent;color:var(--text3);font-size:13px;font-weight:500;cursor:pointer;font-family:'DM Sans',sans-serif;transition:all .15s;width:100%;}
.add-section-btn:hover{border-color:var(--blue);color:var(--blue);background:var(--blue-light);}

/* ── Badge ── */
.inst-badge{font-size:10px;padding:2px 6px;border-radius:4px;background:var(--surface2);color:var(--text3);font-weight:500;white-space:nowrap;}

/* ── DL area ── */
#dl-area{margin-bottom:10px;}
#dl-link{display:inline-flex;align-items:center;gap:6px;padding:7px 16px;font-size:12px;font-weight:600;border:1px solid var(--green);border-radius:var(--radius);background:var(--green-light);color:var(--green);text-decoration:none;}

/* ── Modal ── */
.modal-overlay{position:fixed;inset:0;background:rgba(0,0,0,.4);display:flex;align-items:center;justify-content:center;z-index:1000;}
.modal{background:var(--surface);border-radius:var(--radius-xl);padding:24px;max-width:440px;width:90%;box-shadow:var(--shadow-lg);}
.modal h3{font-size:16px;font-weight:600;margin-bottom:16px;}
.modal label{font-size:12px;color:var(--text2);font-weight:500;display:block;margin-bottom:4px;}
.modal input,.modal textarea{width:100%;font-size:13px;padding:8px 10px;border:1px solid var(--border2);border-radius:var(--radius);background:var(--bg);color:var(--text);font-family:'DM Sans',sans-serif;margin-bottom:12px;}
.modal textarea{height:80px;resize:vertical;}
.modal-actions{display:flex;gap:8px;justify-content:flex-end;margin-top:8px;}

/* ── Scrollbar ── */
::-webkit-scrollbar{width:6px;height:6px;}
::-webkit-scrollbar-track{background:transparent;}
::-webkit-scrollbar-thumb{background:var(--border2);border-radius:3px;}

/* ── Print / PDF ── */
@media print{
  .app-header .header-controls,.panel,.eur-bar,.overhead-bar .icon-btn,
  .section-drag-handle,.section-controls .icon-btn:not(.print-keep),
  .add-section-btn,.section-foot-add,#dl-area,.no-print{display:none!important;}
  body{background:#fff;font-size:11px;}
  .app{max-width:100%;padding:0;}
  .section{break-inside:avoid;border:1px solid #ccc;}
  .section-header{background:#f5f5f5!important;}
  th{background:#f5f5f5!important;}
  .subtotal-row td,.grandtotal-row td{background:#d6e4f7!important;}
  .grand-footer{border:1px solid #ccc;}
}
</style>
</head>
<body>
<div class="app">

  <!-- HEADER -->
  <div class="app-header">
    <div>
      <div class="app-title">Research Budget <span id="hdr-sub">Builder</span></div>
    </div>
    <div class="header-controls">
      <div class="lang-toggle">
        <button class="lang-btn active" id="btn-da" onclick="setLang('da')">DA</button>
        <button class="lang-btn" id="btn-en" onclick="setLang('en')">EN</button>
      </div>
      <div class="pill-group" id="year-btns">
        <button class="pill active" data-y="1">1</button>
        <button class="pill" data-y="2">2</button>
        <button class="pill" data-y="3">3</button>
        <button class="pill" data-y="4">4</button>
        <button class="pill" data-y="5">5</button>
      </div>
      <div class="pill-group" id="inst-btns">
        <button class="pill active" data-inst="all" id="inst-all">Alle</button>
        <button class="pill" data-inst="Rigshospitalet">Rigshospitalet</button>
        <button class="pill" data-inst="DTU">DTU</button>
      </div>
      <div class="pill-group">
        <button class="pill active" id="btn-dkk" onclick="setCurrency('DKK')">DKK</button>
        <button class="pill" id="btn-eur" onclick="setCurrency('EUR')">EUR</button>
      </div>
      <button class="icon-btn" onclick="exportExcel()"><i class="ti ti-file-spreadsheet"></i> <span class="t" data-k="export_excel">Excel</span></button>
      <button class="icon-btn primary" onclick="exportPDF()"><i class="ti ti-file-type-pdf"></i> <span class="t" data-k="export_pdf">PDF</span></button>
    </div>
  </div>

  <div id="dl-area"></div>

  <!-- EUR RATE -->
  <div class="eur-bar">
    <i class="ti ti-arrows-exchange"></i>
    <span class="t" data-k="eur_rate_label">1 EUR =</span>
    <input type="number" id="rate-inp" value="7.4728" step="0.0001"/>
    <span>DKK</span>
    <span style="color:var(--text3);font-size:11px" class="t" data-k="eur_rate_note">(kurs pr. 6. maj 2026)</span>
  </div>

  <!-- OVERHEAD -->
  <div class="overhead-bar">
    <label class="t" data-k="overhead_label">Overhead (%)</label>
    <input type="number" id="overhead-inp" value="0" min="0" max="100" step="0.5"/>
    <span id="overhead-result" class="overhead-result" style="display:none"></span>
    <span style="font-size:11px;color:var(--text3)" class="t" data-k="overhead_note">Overhead beregnes automatisk på total. Sæt til 0 for at skjule.</span>
  </div>

  <!-- SALARY RATES -->
  <div class="panel" id="rates-panel">
    <div class="panel-header" onclick="togglePanel('rates-panel')">
      <span class="panel-title"><i class="ti ti-coin"></i> <span class="t" data-k="salary_rates_title">Lønsatser (DKK/år ved 1,0 FTE)</span></span>
      <i class="ti ti-chevron-down chevron open" id="rates-chev"></i>
    </div>
    <div id="rates-body">
      <div class="rates-grid" id="rates-grid"></div>
      <div style="padding:0 16px 12px;font-size:11px;color:var(--text3)" class="t" data-k="salary_rates_hint">Budget = FTE × lønsats. Ret budgetfeltet manuelt for at låse det.</div>
    </div>
  </div>

  <!-- SUMMARY -->
  <div class="summary-grid" id="summary-grid"></div>

  <!-- SECTIONS -->
  <div class="sections-wrap" id="sections-wrap"></div>

  <!-- ADD SECTION -->
  <button class="add-section-btn no-print" onclick="addSection()">
    <i class="ti ti-plus"></i> <span class="t" data-k="add_category">Tilføj kategori</span>
  </button>

  <!-- GRAND TOTAL -->
  <div class="grand-footer" id="grand-footer">
    <span class="grand-label t" data-k="grand_total">Samlet total (alle år)</span>
    <div style="text-align:right">
      <div class="grand-val" id="grand-val">DKK 0</div>
      <div class="grand-sub" id="grand-sub-eur" style="display:none"></div>
      <div class="grand-sub" id="grand-overhead-total" style="display:none"></div>
    </div>
  </div>
</div>

<script>
// ══════════════════════════════════════════════
//  TRANSLATIONS
// ══════════════════════════════════════════════
const T = {
  da: {
    hdr_sub:'Builder', export_excel:'Excel', export_pdf:'PDF',
    eur_rate_label:'1 EUR =', eur_rate_note:'(kurs pr. 6. maj 2026)',
    overhead_label:'Overhead (%)', overhead_note:'Overhead beregnes automatisk. Sæt til 0 for at skjule.',
    salary_rates_title:'Lønsatser (DKK/år ved 1,0 FTE)',
    salary_rates_hint:'Budget = FTE × lønsats. Ret budgetfeltet manuelt for at låse det.',
    add_category:'Tilføj kategori', grand_total:'Samlet total (alle år)',
    year:'År', all:'Alle', subcategory:'Underkategori', institution:'Institution',
    fte:'FTE', budget:'Budget', total:'Total', description:'Beskrivelse',
    subtotal:'Subtotal', add_person:'+ Person', add_row:'+ Række',
    overhead_row:'Overhead', incl_overhead:'Inkl. overhead',
    save:'Gem', cancel:'Annuller', edit_section:'Rediger kategori',
    section_name:'Kategorinavn', section_desc:'Beskrivelse (valgfri)',
    section_color:'Farve',
    col_headers: y => `År ${y}`,
    salary_cats: {
      consultant_rh:'Speciallæge (RH)', pregrad_rh:'Prægraduat stipendiat (RH)',
      scientist_rh:'Forsker (RH)', phd_rh:'Ph.d.-studerende (RH)',
      tech_rh:'Forskningssygeplejerske (RH)', projempl_rh:'Projektansatte (RH)',
      projempl_dtu:'Projektansatte (DTU)', phd_dtu:'Ph.d.-studerende (DTU)',
      postdoc_dtu:'Postdoc (DTU)', pregrad_dtu:'Prægraduat stipendiat (DTU)',
    },
    cat_labels:{
      salary:'Løn', operation:'Drift',
      dissemination:'Formidling, uddannelse og træning',
      admin:'Administration', supplement:'Projekttillæg',
    },
    row_labels:{
      data_mgmt:'Datahåndtering', subcontractor:'Underleverandøromkostninger',
      bench_fee:'Bench fee', infrastructure:'Infrastruktur',
      proj_specific:'Projektspecifikke omkostninger', operating:'Driftsomkostninger',
      equipment_dtu:'Udstyr', equipment_rh:'Udstyr',
      travel:'Rejser', training:'Uddannelse',
      conf_rh:'Deltagelse i konferencer', conf_dtu:'Deltagelse i konferencer',
      collab_rh:'Samarbejdsaktiviteter', collab_dtu:'Samarbejdsaktiviteter',
      publication:'Publikationsomkostninger',
      admin_direct:'Direkte administrative omkostninger',
      supplement:'Projekttillæg',
    },
    generating_pdf:'Genererer PDF…', generating_excel:'Genererer Excel…',
    export_ready:'Klar til download',
  },
  en: {
    hdr_sub:'Builder', export_excel:'Excel', export_pdf:'PDF',
    eur_rate_label:'1 EUR =', eur_rate_note:'(rate as of 6 May 2026)',
    overhead_label:'Overhead (%)', overhead_note:'Overhead is auto-calculated on total. Set to 0 to hide.',
    salary_rates_title:'Salary rates (DKK/year at 1.0 FTE)',
    salary_rates_hint:'Budget = FTE × rate. Edit budget cells manually to lock them.',
    add_category:'Add category', grand_total:'Grand total (all years)',
    year:'Year', all:'All', subcategory:'Subcategory', institution:'Institution',
    fte:'FTE', budget:'Budget', total:'Total', description:'Description',
    subtotal:'Subtotal', add_person:'+ Person', add_row:'+ Row',
    overhead_row:'Overhead', incl_overhead:'Incl. overhead',
    save:'Save', cancel:'Cancel', edit_section:'Edit category',
    section_name:'Category name', section_desc:'Description (optional)',
    section_color:'Color',
    col_headers: y => `Year ${y}`,
    salary_cats:{
      consultant_rh:'Consultant, MD (RH)', pregrad_rh:'Pre-graduate scholar (RH)',
      scientist_rh:'Scientist / researcher (RH)', phd_rh:'PhD student (RH)',
      tech_rh:'Research nurse (RH)', projempl_rh:'Project employees (RH)',
      projempl_dtu:'Project employees (DTU)', phd_dtu:'PhD student (DTU)',
      postdoc_dtu:'Postdoc (DTU)', pregrad_dtu:'Pre-graduate scholar (DTU)',
    },
    cat_labels:{
      salary:'Salary', operation:'Operation',
      dissemination:'Dissemination, training & education',
      admin:'Administration', supplement:'Project supplement',
    },
    row_labels:{
      data_mgmt:'Data management', subcontractor:'Subcontractor costs',
      bench_fee:'Bench fee', infrastructure:'Infrastructure',
      proj_specific:'Project specific costs', operating:'Operating expenses',
      equipment_dtu:'Equipment', equipment_rh:'Equipment',
      travel:'Travel', training:'Training',
      conf_rh:'Conference participation', conf_dtu:'Conference participation',
      collab_rh:'Collaborative activities', collab_dtu:'Collaborative activities',
      publication:'Publication costs',
      admin_direct:'Direct administrative expenses',
      supplement:'Project supplement',
    },
    generating_pdf:'Generating PDF…', generating_excel:'Generating Excel…',
    export_ready:'Ready to download',
  }
};

// ══════════════════════════════════════════════
//  STATE
// ══════════════════════════════════════════════
let lang = 'da';
let currency = 'DKK';
let eurRate = 7.4728;
let numYears = 1;
let instFilter = 'all';
let overheadPct = 0;

const t = k => (T[lang][k] !== undefined ? T[lang][k] : k);

// Rate definitions
const RATE_DEFS = [
  {key:'consultant_rh', default:1080000},
  {key:'pregrad_rh',    default:150000},
  {key:'scientist_rh',  default:624000},
  {key:'phd_rh',        default:624000},
  {key:'tech_rh',       default:504000},
  {key:'projempl_rh',   default:550000},
  {key:'projempl_dtu',  default:550000},
  {key:'phd_dtu',       default:530000},
  {key:'postdoc_dtu',   default:650000},
  {key:'pregrad_dtu',   default:150000},
];
let rates = {};
RATE_DEFS.forEach(r => { rates[r.key] = r.default; });

// Category colors
const CAT_COLORS = ['#185FA5','#0F6E56','#854F0B','#5F5E5A','#534AB7','#7B2D8B','#C0392B','#1A7A4A'];

// ── Default categories (with labelKey for translation) ──
let categories = [
  {
    id:'salary', labelKey:'salary', label:'Løn', color:'#185FA5', hasFte:true, desc:'',
    rows:[
      {id:uid(),labelKey:'consultant_rh',   label:'Speciallæge (RH)',              inst:'Rigshospitalet',rateKey:'consultant_rh', fte:{},budget:{},budgetManual:{},desc:''},
      {id:uid(),labelKey:'pregrad_rh',      label:'Prægraduat stipendiat (RH)',     inst:'Rigshospitalet',rateKey:'pregrad_rh',    fte:{},budget:{},budgetManual:{},desc:''},
      {id:uid(),labelKey:'scientist_rh',    label:'Forsker (RH)',                   inst:'Rigshospitalet',rateKey:'scientist_rh',  fte:{},budget:{},budgetManual:{},desc:''},
      {id:uid(),labelKey:'phd_rh',          label:'Ph.d.-studerende (RH)',          inst:'Rigshospitalet',rateKey:'phd_rh',        fte:{},budget:{},budgetManual:{},desc:''},
      {id:uid(),labelKey:'tech_rh',         label:'Forskningssygeplejerske (RH)',   inst:'Rigshospitalet',rateKey:'tech_rh',       fte:{},budget:{},budgetManual:{},desc:''},
      {id:uid(),labelKey:'projempl_rh',     label:'Projektansatte (RH)',            inst:'Rigshospitalet',rateKey:'projempl_rh',   fte:{},budget:{},budgetManual:{},desc:''},
      {id:uid(),labelKey:'projempl_dtu',    label:'Projektansatte (DTU)',           inst:'DTU',           rateKey:'projempl_dtu',  fte:{},budget:{},budgetManual:{},desc:''},
      {id:uid(),labelKey:'phd_dtu',         label:'Ph.d.-studerende (DTU)',         inst:'DTU',           rateKey:'phd_dtu',       fte:{},budget:{},budgetManual:{},desc:''},
      {id:uid(),labelKey:'postdoc_dtu',     label:'Postdoc (DTU)',                  inst:'DTU',           rateKey:'postdoc_dtu',   fte:{},budget:{},budgetManual:{},desc:''},
      {id:uid(),labelKey:'pregrad_dtu',     label:'Prægraduat stipendiat (DTU)',    inst:'DTU',           rateKey:'pregrad_dtu',   fte:{},budget:{},budgetManual:{},desc:''},
    ]
  },
  {
    id:'operation', labelKey:'operation', label:'Drift', color:'#0F6E56', hasFte:false, desc:'',
    rows:[
      {id:uid(),labelKey:'data_mgmt',     label:'Datahåndtering',                inst:'DTU',           fte:{},budget:{},budgetManual:{},desc:''},
      {id:uid(),labelKey:'subcontractor', label:'Underleverandøromkostninger',   inst:'Rigshospitalet',fte:{},budget:{},budgetManual:{},desc:''},
      {id:uid(),labelKey:'bench_fee',     label:'Bench fee',                     inst:'Rigshospitalet',fte:{},budget:{},budgetManual:{},desc:''},
      {id:uid(),labelKey:'infrastructure',label:'Infrastruktur',                 inst:'DTU',           fte:{},budget:{},budgetManual:{},desc:''},
      {id:uid(),labelKey:'proj_specific', label:'Projektspecifikke omkostninger',inst:'Rigshospitalet',fte:{},budget:{},budgetManual:{},desc:''},
      {id:uid(),labelKey:'operating',     label:'Driftsomkostninger',            inst:'Rigshospitalet',fte:{},budget:{},budgetManual:{},desc:''},
      {id:uid(),labelKey:'equipment_dtu', label:'Udstyr',                        inst:'DTU',           fte:{},budget:{},budgetManual:{},desc:''},
      {id:uid(),labelKey:'equipment_rh',  label:'Udstyr',                        inst:'Rigshospitalet',fte:{},budget:{},budgetManual:{},desc:''},
    ]
  },
  {
    id:'dissemination', labelKey:'dissemination', label:'Formidling, uddannelse og træning', color:'#854F0B', hasFte:false, desc:'',
    rows:[
      {id:uid(),labelKey:'travel',      label:'Rejser',                    inst:'Rigshospitalet',fte:{},budget:{},budgetManual:{},desc:''},
      {id:uid(),labelKey:'training',    label:'Uddannelse',                inst:'Rigshospitalet',fte:{},budget:{},budgetManual:{},desc:''},
      {id:uid(),labelKey:'conf_rh',     label:'Deltagelse i konferencer',  inst:'Rigshospitalet',fte:{},budget:{},budgetManual:{},desc:''},
      {id:uid(),labelKey:'conf_dtu',    label:'Deltagelse i konferencer',  inst:'DTU',           fte:{},budget:{},budgetManual:{},desc:''},
      {id:uid(),labelKey:'collab_rh',   label:'Samarbejdsaktiviteter',     inst:'Rigshospitalet',fte:{},budget:{},budgetManual:{},desc:''},
      {id:uid(),labelKey:'collab_dtu',  label:'Samarbejdsaktiviteter',     inst:'DTU',           fte:{},budget:{},budgetManual:{},desc:''},
      {id:uid(),labelKey:'publication', label:'Publikationsomkostninger',  inst:'Rigshospitalet',fte:{},budget:{},budgetManual:{},desc:''},
    ]
  },
  {
    id:'admin', labelKey:'admin', label:'Administration', color:'#5F5E5A', hasFte:false, desc:'',
    rows:[
      {id:uid(),labelKey:'admin_direct',label:'Direkte administrative omkostninger',inst:'Rigshospitalet',fte:{},budget:{},budgetManual:{},desc:''},
    ]
  },
  {
    id:'supplement', labelKey:'supplement', label:'Projekttillæg', color:'#534AB7', hasFte:false, desc:'',
    rows:[
      {id:uid(),labelKey:'supplement',label:'Projekttillæg',inst:'DTU',fte:{},budget:{},budgetManual:{},desc:''},
    ]
  },
];

let collapsed = {};

// ══════════════════════════════════════════════
//  UTILS
// ══════════════════════════════════════════════
function uid(){ return Math.random().toString(36).slice(2,9); }

function fmtNum(n){
  if(currency==='EUR') n = n / eurRate;
  return Math.round(n).toLocaleString('da-DK');
}
function fmtCur(n){
  return (currency==='EUR'?'€ ':'kr. ') + fmtNum(n);
}
function years(){ return Array.from({length:numYears},(_,i)=>i+1); }

function rowBudget(row, y){
  return row.budget[y] || 0;
}
function catTotal(cat){
  let t=0;
  cat.rows.forEach(row=>{
    if(instFilter!=='all'&&row.inst!==instFilter)return;
    years().forEach(y=>{ t+=rowBudget(row,y); });
  });
  return t;
}
function yearGrand(y){
  let t=0;
  categories.forEach(cat=>{
    cat.rows.forEach(row=>{
      if(instFilter!=='all'&&row.inst!==instFilter)return;
      t+=rowBudget(row,y);
    });
  });
  return t;
}
function grandTotal(){
  let t=0; years().forEach(y=>{ t+=yearGrand(y); }); return t;
}

function rowLabel(row){
  // salary cats use salary_cats dict, others use row_labels
  if(row.rateKey && T[lang].salary_cats[row.rateKey]){
    // if row has been renamed by user (custom label != default), use custom
    const defDa = T['da'].salary_cats[row.rateKey];
    const defEn = T['en'].salary_cats[row.rateKey];
    if(row.label===defDa||row.label===defEn) return T[lang].salary_cats[row.rateKey];
  }
  if(row.labelKey && T[lang].row_labels[row.labelKey]){
    const defDa = T['da'].row_labels[row.labelKey];
    const defEn = T['en'].row_labels[row.labelKey];
    if(row.label===defDa||row.label===defEn) return T[lang].row_labels[row.labelKey];
  }
  return row.label; // custom label, leave as-is
}
function catLabel(cat){
  if(cat.labelKey && T[lang].cat_labels[cat.labelKey]){
    const defDa=T['da'].cat_labels[cat.labelKey];
    const defEn=T['en'].cat_labels[cat.labelKey];
    if(cat.label===defDa||cat.label===defEn) return T[lang].cat_labels[cat.labelKey];
  }
  return cat.label;
}

// ══════════════════════════════════════════════
//  LANGUAGE
// ══════════════════════════════════════════════
function setLang(l){
  lang=l;
  document.getElementById('btn-da').classList.toggle('active',l==='da');
  document.getElementById('btn-en').classList.toggle('active',l==='en');
  document.querySelectorAll('.t[data-k]').forEach(el=>{
    const k=el.dataset.k; if(T[lang][k]!==undefined) el.textContent=T[lang][k];
  });
  document.getElementById('inst-all').textContent=T[lang].all;
  buildRatesPanel();
  renderAll();
}

// ══════════════════════════════════════════════
//  CURRENCY
// ══════════════════════════════════════════════
function setCurrency(c){
  currency=c;
  document.getElementById('btn-dkk').classList.toggle('active',c==='DKK');
  document.getElementById('btn-eur').classList.toggle('active',c==='EUR');
  updateTotals();
}

// ══════════════════════════════════════════════
//  PANELS
// ══════════════════════════════════════════════
function togglePanel(id){
  const body=document.getElementById(id==='rates-panel'?'rates-body':id+'-body');
  const chev=document.getElementById(id==='rates-panel'?'rates-chev':id+'-chev');
  if(!body)return;
  const open=body.style.display!=='none';
  body.style.display=open?'none':'block';
  if(chev)chev.classList.toggle('open',!open);
}

// ══════════════════════════════════════════════
//  SALARY RATES
// ══════════════════════════════════════════════
function buildRatesPanel(){
  const grid=document.getElementById('rates-grid'); grid.innerHTML='';
  RATE_DEFS.forEach(r=>{
    const label = T[lang].salary_cats[r.key] || r.key;
    const div=document.createElement('div'); div.className='rate-row';
    div.innerHTML=`<span class="rate-label">${label}</span><input class="rate-inp" type="number" min="0" step="1000" value="${rates[r.key]}" data-key="${r.key}" />`;
    grid.appendChild(div);
  });
}

document.getElementById('rates-grid').addEventListener('input',e=>{
  const el=e.target; if(!el.dataset.key)return;
  rates[el.dataset.key]=parseFloat(el.value)||0;
  recalcSalaryFromRates(el.dataset.key);
  updateTotals();
});

function recalcSalaryFromRates(rateKey){
  categories.forEach(cat=>{
    if(!cat.hasFte)return;
    cat.rows.forEach(row=>{
      if(row.rateKey!==rateKey)return;
      years().forEach(y=>{
        if(row.budgetManual[y])return;
        const fte=row.fte[y]||0;
        row.budget[y]=Math.round(fte*(rates[rateKey]||0));
        const inp=document.getElementById(`bi_${row.id}_${y}`);
        if(inp)inp.value=row.budget[y]||'';
      });
    });
  });
}

// ══════════════════════════════════════════════
//  TOTALS
// ══════════════════════════════════════════════
function updateTotals(){
  // summary cards
  const sg=document.getElementById('summary-grid'); sg.innerHTML='';
  years().forEach(y=>{
    const yt=yearGrand(y);
    const m=document.createElement('div'); m.className='metric';
    m.innerHTML=`<div class="metric-label">${T[lang].col_headers(y)}</div><div class="metric-value">${fmtCur(yt)}</div>`;
    sg.appendChild(m);
  });

  const gt=grandTotal();
  const oh=overheadPct>0?Math.round(gt*overheadPct/100):0;

  // grand footer
  document.getElementById('grand-val').textContent=fmtCur(gt);
  const eurEl=document.getElementById('grand-sub-eur');
  if(currency==='DKK'){
    eurEl.textContent='≈ € '+Math.round(gt/eurRate).toLocaleString('da-DK');
    eurEl.style.display='block';
  } else { eurEl.style.display='none'; }

  const ohTotal=document.getElementById('grand-overhead-total');
  if(overheadPct>0){
    ohTotal.textContent=`${T[lang].incl_overhead}: ${fmtCur(gt+oh)}`;
    ohTotal.style.display='block';
    document.getElementById('overhead-result').style.display='inline';
    document.getElementById('overhead-result').textContent=`${T[lang].overhead_row}: ${fmtCur(oh)}`;
  } else {
    ohTotal.style.display='none';
    document.getElementById('overhead-result').style.display='none';
  }

  // per-section totals
  categories.forEach(cat=>{
    const ct=catTotal(cat);
    const el=document.getElementById(`sec-total-${cat.id}`); if(el)el.textContent=fmtCur(ct);
    // per-row totals
    cat.rows.forEach(row=>{
      let rowT=0; years().forEach(y=>{ rowT+=rowBudget(row,y); });
      const rt=document.getElementById(`rt_${row.id}`); if(rt)rt.textContent=fmtCur(rowT);
    });
    // update subtotal row in table
    const subEl=document.getElementById(`subtotal-${cat.id}`);
    if(subEl){
      const cells=subEl.querySelectorAll('.subtotal-ycell');
      cells.forEach((c,i)=>{
        const y=i+1;
        let yt=0;
        cat.rows.forEach(row=>{
          if(instFilter!=='all'&&row.inst!==instFilter)return;
          yt+=rowBudget(row,y);
        });
        c.textContent=fmtCur(yt);
      });
      const totCell=subEl.querySelector('.subtotal-total');
      if(totCell)totCell.textContent=fmtCur(ct);
    }
    // overhead row
    const ohEl=document.getElementById(`overhead-${cat.id}`);
    if(ohEl){
      if(overheadPct>0){
        ohEl.style.display='';
        const ohCells=ohEl.querySelectorAll('.oh-ycell');
        ohCells.forEach((c,i)=>{
          const y=i+1;
          let yt=0;
          cat.rows.forEach(row=>{
            if(instFilter!=='all'&&row.inst!==instFilter)return;
            yt+=rowBudget(row,y);
          });
          c.textContent=fmtCur(Math.round(yt*overheadPct/100));
        });
        const ohTot=ohEl.querySelector('.oh-total');
        if(ohTot)ohTot.textContent=fmtCur(Math.round(ct*overheadPct/100));
      } else {
        ohEl.style.display='none';
      }
    }
  });

  // update all budget-th headers
  document.querySelectorAll('.budget-th').forEach(th=>{
    const y=th.dataset.y;
    th.textContent=`${T[lang].col_headers(y)} ${T[lang].budget} (${currency})`;
  });
}

// ══════════════════════════════════════════════
//  RENDER ALL
// ══════════════════════════════════════════════
function renderAll(){
  const wrap=document.getElementById('sections-wrap');
  wrap.innerHTML='';
  categories.forEach(cat=>wrap.appendChild(buildSection(cat)));
  initSortableSections();
  updateTotals();
}

// ══════════════════════════════════════════════
//  BUILD SECTION
// ══════════════════════════════════════════════
function buildSection(cat){
  const isOpen=collapsed[cat.id]!==true;
  const sec=document.createElement('div');
  sec.className='section'; sec.dataset.catId=cat.id;

  // header
  const hdr=document.createElement('div'); hdr.className='section-header';
  hdr.innerHTML=`
    <i class="ti ti-grip-vertical section-drag-handle" title="Træk for at ændre rækkefølge"></i>
    <div class="section-dot" style="background:${cat.color}"></div>
    <div class="section-name" style="flex:1">
      <input type="text" value="${catLabel(cat)}" placeholder="Kategorinavn"
        onchange="renameCat('${cat.id}',this.value)" onclick="event.stopPropagation()"/>
    </div>
    <div class="section-controls">
      <span class="section-total-badge" id="sec-total-${cat.id}">${fmtCur(catTotal(cat))}</span>
      <button class="icon-btn ghost no-print" onclick="event.stopPropagation();editSection('${cat.id}')" title="${T[lang].edit_section}"><i class="ti ti-settings"></i></button>
      <button class="icon-btn danger no-print" onclick="event.stopPropagation();deleteSection('${cat.id}')" title="Slet"><i class="ti ti-trash"></i></button>
      <i class="ti ti-chevron-down chevron ${isOpen?'open':''}" id="chev-${cat.id}"></i>
    </div>`;
  hdr.addEventListener('click',()=>toggleSection(cat.id,sec));
  sec.appendChild(hdr);

  // body
  const body=document.createElement('div');
  body.className='section-body'; body.id=`sb-${cat.id}`;
  body.style.display=isOpen?'block':'none';

  // description
  if(cat.desc||true){
    const descRow=document.createElement('div');
    descRow.style.cssText='padding:8px 16px;border-bottom:1px solid var(--border);';
    descRow.innerHTML=`<input class="text-inp desc-inp" type="text" placeholder="${T[lang].section_desc||'Beskrivelse (valgfri)'}" value="${escHtml(cat.desc)}" style="width:100%" onchange="cat_${cat.id}_desc(this.value)"/>`;
    descRow.querySelector('input').addEventListener('change',e=>{ cat.desc=e.target.value; });
    body.appendChild(descRow);
  }

  body.appendChild(buildTable(cat));

  // footer
  const foot=document.createElement('div'); foot.className='section-foot';
  foot.innerHTML=`<div class="section-foot-add no-print">
    ${cat.hasFte?`<button class="icon-btn ghost" onclick="addPersonRow('${cat.id}')"><i class="ti ti-user-plus"></i> ${T[lang].add_person}</button>`:''}
    <button class="icon-btn ghost" onclick="addRow('${cat.id}')"><i class="ti ti-plus"></i> ${T[lang].add_row}</button>
  </div>`;
  body.appendChild(foot);
  sec.appendChild(body);
  return sec;
}

function escHtml(s){ return (s||'').replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/"/g,'&quot;'); }

// ══════════════════════════════════════════════
//  BUILD TABLE
// ══════════════════════════════════════════════
function buildTable(cat){
  const yrs=years();
  const wrap=document.createElement('div'); wrap.className='tbl-wrap';

  let html=`<table><thead><tr>
    <th style="width:22px" class="no-print"></th>
    <th style="min-width:160px">${T[lang].subcategory}</th>
    <th style="width:80px">${T[lang].institution}</th>`;
  if(cat.hasFte) yrs.forEach(y=>{ html+=`<th class="right" style="width:58px">${T[lang].col_headers(y)} ${T[lang].fte}</th>`; });
  yrs.forEach(y=>{ html+=`<th class="right budget-th" data-y="${y}" style="min-width:120px">${T[lang].col_headers(y)} ${T[lang].budget} (${currency})</th>`; });
  html+=`<th class="right" style="width:110px">${T[lang].total}</th>
    <th style="min-width:130px">${T[lang].description}</th>
  </tr></thead><tbody id="tbody-${cat.id}">`;

  // data rows
  cat.rows.forEach(row=>{
    html+=buildRowHTML(cat,row);
  });

  // subtotal row
  html+=`<tr class="subtotal-row" id="subtotal-${cat.id}">
    <td class="no-print"></td>
    <td colspan="2">${T[lang].subtotal} — ${catLabel(cat)}</td>`;
  if(cat.hasFte) yrs.forEach(()=>{ html+=`<td></td>`; });
  yrs.forEach(y=>{ html+=`<td class="subtotal-ycell" style="text-align:right"></td>`; });
  html+=`<td class="subtotal-total" style="text-align:right"></td><td></td></tr>`;

  // overhead row
  html+=`<tr class="overhead-row" id="overhead-${cat.id}" style="${overheadPct>0?'':'display:none'}">
    <td class="no-print"></td>
    <td colspan="2">${T[lang].overhead_row} (${overheadPct}%)</td>`;
  if(cat.hasFte) yrs.forEach(()=>{ html+=`<td></td>`; });
  yrs.forEach(y=>{ html+=`<td class="oh-ycell" style="text-align:right"></td>`; });
  html+=`<td class="oh-total" style="text-align:right"></td><td></td></tr>`;

  html+=`</tbody></table>`;
  wrap.innerHTML=html;

  // make rows sortable
  const tbody=wrap.querySelector(`#tbody-${cat.id}`);
  if(tbody){
    Sortable.create(tbody,{
      handle:'.drag-handle-cell',
      animation:150,
      onEnd(e){
        const rows=[...tbody.querySelectorAll('tr.data-row')];
        const newOrder=rows.map(tr=>tr.dataset.rowId);
        cat.rows.sort((a,b)=>newOrder.indexOf(a.id)-newOrder.indexOf(b.id));
        updateTotals();
      }
    });
  }

  return wrap;
}

function buildRowHTML(cat,row){
  const yrs=years();
  const hide=instFilter!=='all'&&row.inst!==instFilter;
  let html=`<tr class="data-row${hide?' hidden-row':''}" data-row-id="${row.id}">
    <td class="drag-handle-cell no-print" style="color:var(--text3);cursor:grab;padding:6px 4px;"><i class="ti ti-grip-horizontal"></i></td>
    <td><input class="text-inp" type="text" value="${escHtml(rowLabel(row))}" onchange="renameRow('${cat.id}','${row.id}',this.value)"/></td>
    <td><span class="inst-badge">${row.inst}</span></td>`;
  if(cat.hasFte) yrs.forEach(y=>{
    const v=row.fte[y]||'';
    html+=`<td><input id="fi_${row.id}_${y}" class="num-inp" type="number" min="0" max="10" step="0.1" placeholder="0" value="${v}" style="width:52px;text-align:center" onchange="onFteChange('${cat.id}','${row.id}',${y},this.value)"/></td>`;
  });
  yrs.forEach(y=>{
    const v=row.budget[y]||'';
    html+=`<td><input id="bi_${row.id}_${y}" class="num-inp" type="number" min="0" step="1000" placeholder="0" value="${v}" onchange="onBudgetChange('${cat.id}','${row.id}',${y},this.value)"/></td>`;
  });
  let rowT=0; yrs.forEach(y=>{ rowT+=rowBudget(row,y); });
  html+=`<td class="row-total" id="rt_${row.id}" style="text-align:right">${fmtCur(rowT)}</td>
    <td><input class="text-inp desc-inp" type="text" placeholder="${T[lang].description||'Beskrivelse'}..." value="${escHtml(row.desc)}" onchange="onRowDesc('${cat.id}','${row.id}',this.value)"/></td>
  </tr>`;
  return html;
}

// ══════════════════════════════════════════════
//  CHANGE HANDLERS
// ══════════════════════════════════════════════
window.onFteChange=function(catId,rowId,y,val){
  const cat=categories.find(c=>c.id===catId);
  const row=cat.rows.find(r=>r.id===rowId);
  row.fte[y]=parseFloat(val)||0;
  if(!row.budgetManual[y]){
    const auto=Math.round(row.fte[y]*(rates[row.rateKey]||0));
    row.budget[y]=auto;
    const inp=document.getElementById(`bi_${rowId}_${y}`);
    if(inp)inp.value=auto||'';
  }
  updateTotals();
};
window.onBudgetChange=function(catId,rowId,y,val){
  const cat=categories.find(c=>c.id===catId);
  const row=cat.rows.find(r=>r.id===rowId);
  const v=parseFloat(val)||0;
  if(cat.hasFte){
    const auto=Math.round((row.fte[y]||0)*(rates[row.rateKey]||0));
    row.budgetManual[y]=(v!==auto)?true:false;
  }
  row.budget[y]=v;
  updateTotals();
};
window.onRowDesc=function(catId,rowId,val){
  const cat=categories.find(c=>c.id===catId);
  const row=cat.rows.find(r=>r.id===rowId);
  row.desc=val;
};
window.renameRow=function(catId,rowId,val){
  const cat=categories.find(c=>c.id===catId);
  const row=cat.rows.find(r=>r.id===rowId);
  row.label=val;
};
window.renameCat=function(catId,val){
  const cat=categories.find(c=>c.id===catId);
  cat.label=val;
  const el=document.getElementById(`subtotal-${catId}`);
  if(el){ const td=el.querySelector('td:nth-child(2)'); if(td)td.textContent=`${T[lang].subtotal} — ${val}`; }
  updateTotals();
};

// ══════════════════════════════════════════════
//  SECTION ACTIONS
// ══════════════════════════════════════════════
function toggleSection(catId,sec){
  const isOpen=collapsed[catId]!==true;
  collapsed[catId]=isOpen;
  const body=document.getElementById(`sb-${catId}`);
  const chev=document.getElementById(`chev-${catId}`);
  if(body) body.style.display=isOpen?'none':'block';
  if(chev) chev.classList.toggle('open',!isOpen);
}

window.addPersonRow=function(catId){
  const cat=categories.find(c=>c.id===catId);
  const newRow={id:uid(),labelKey:'',label:cat.rows[0]?rowLabel(cat.rows[0]):'Ny person',
    inst:cat.rows[0]?.inst||'Rigshospitalet',rateKey:cat.rows[0]?.rateKey||'',
    fte:{},budget:{},budgetManual:{},desc:''};
  cat.rows.push(newRow);
  const tbody=document.getElementById(`tbody-${catId}`);
  if(tbody){
    const subtotalRow=document.getElementById(`subtotal-${catId}`);
    const tr=document.createElement('tr');
    tr.innerHTML=buildRowHTML(cat,newRow);
    tr.className='data-row';
    tr.dataset.rowId=newRow.id;
    tbody.insertBefore(tr.firstElementChild||tr,subtotalRow);
    renderAll(); // re-render to get proper structure
  }
};

window.addRow=function(catId){
  const cat=categories.find(c=>c.id===catId);
  const newRow={id:uid(),labelKey:'',label:'Ny post',
    inst:'Rigshospitalet',rateKey:'',
    fte:{},budget:{},budgetManual:{},desc:''};
  cat.rows.push(newRow);
  renderAll();
};

window.deleteSection=function(catId){
  if(!confirm('Slet denne kategori?'))return;
  categories=categories.filter(c=>c.id!==catId);
  renderAll();
};

window.addSection=function(){
  const color=CAT_COLORS[categories.length%CAT_COLORS.length];
  categories.push({
    id:uid(),labelKey:'',label:lang==='da'?'Ny kategori':'New category',
    color,hasFte:false,desc:'',rows:[
      {id:uid(),labelKey:'',label:lang==='da'?'Ny post':'New item',
       inst:'Rigshospitalet',rateKey:'',fte:{},budget:{},budgetManual:{},desc:''}
    ]
  });
  renderAll();
};

// ══════════════════════════════════════════════
//  EDIT SECTION MODAL
// ══════════════════════════════════════════════
window.editSection=function(catId){
  const cat=categories.find(c=>c.id===catId);
  const overlay=document.createElement('div');
  overlay.className='modal-overlay';
  overlay.innerHTML=`<div class="modal">
    <h3>${T[lang].edit_section}</h3>
    <label>${T[lang].section_name}</label>
    <input id="m-name" type="text" value="${escHtml(catLabel(cat))}"/>
    <label>${T[lang].section_desc}</label>
    <textarea id="m-desc">${escHtml(cat.desc)}</textarea>
    <label>${T[lang].section_color}</label>
    <div style="display:flex;gap:8px;flex-wrap:wrap;margin-bottom:12px">
      ${CAT_COLORS.map(c=>`<div onclick="selectColor('${c}',this)" style="width:28px;height:28px;border-radius:6px;background:${c};cursor:pointer;border:3px solid ${c===cat.color?'#000':'transparent'}"></div>`).join('')}
    </div>
    <label>FTE-baseret lønkategori?</label>
    <input id="m-fte" type="checkbox" ${cat.hasFte?'checked':''} style="width:auto;margin-bottom:12px"/>
    <div class="modal-actions">
      <button class="icon-btn" onclick="this.closest('.modal-overlay').remove()">${T[lang].cancel}</button>
      <button class="icon-btn primary" onclick="saveSection('${catId}',this)">${T[lang].save}</button>
    </div>
  </div>`;
  document.body.appendChild(overlay);
  overlay.addEventListener('click',e=>{ if(e.target===overlay)overlay.remove(); });
};
window.selectColor=function(c,el){
  el.closest('.modal').querySelectorAll('[onclick^="selectColor"]').forEach(d=>d.style.border='3px solid transparent');
  el.style.border='3px solid #000';
  el._selectedColor=c;
};
window.saveSection=function(catId,btn){
  const modal=btn.closest('.modal-overlay');
  const cat=categories.find(c=>c.id===catId);
  cat.label=modal.querySelector('#m-name').value;
  cat.desc=modal.querySelector('#m-desc').value;
  cat.hasFte=modal.querySelector('#m-fte').checked;
  const colorEl=[...modal.querySelectorAll('[onclick^="selectColor"]')].find(d=>d.style.border.includes('#000'));
  if(colorEl)cat.color=colorEl.style.background;
  modal.remove();
  renderAll();
};

// ══════════════════════════════════════════════
//  SORTABLE (sections)
// ══════════════════════════════════════════════
function initSortableSections(){
  const wrap=document.getElementById('sections-wrap');
  Sortable.create(wrap,{
    handle:'.section-drag-handle',
    animation:150,
    onEnd(e){
      const els=[...wrap.querySelectorAll('.section')];
      const newOrder=els.map(el=>el.dataset.catId);
      categories.sort((a,b)=>newOrder.indexOf(a.id)-newOrder.indexOf(b.id));
    }
  });
}

// ══════════════════════════════════════════════
//  INST FILTER
// ══════════════════════════════════════════════
function applyInstFilter(){
  categories.forEach(cat=>{
    cat.rows.forEach(row=>{
      const tr=document.querySelector(`tr[data-row-id="${row.id}"]`);
      if(tr)tr.classList.toggle('hidden-row',instFilter!=='all'&&row.inst!==instFilter);
    });
  });
  updateTotals();
}

// ══════════════════════════════════════════════
//  OVERHEAD
// ══════════════════════════════════════════════
document.getElementById('overhead-inp').addEventListener('input',e=>{
  overheadPct=parseFloat(e.target.value)||0;
  updateTotals();
});

// ══════════════════════════════════════════════
//  EXCEL EXPORT (via sendPrompt)
// ══════════════════════════════════════════════
window.exportExcel=function(){
  const payload=buildPayload();
  const msg='EXCEL_EXPORT_REQUEST:'+JSON.stringify(payload);
  document.getElementById('dl-area').innerHTML='<div style="font-size:12px;color:var(--text2);padding:6px 0">⏳ '+T[lang].generating_excel+' Sender data…</div>';
  if(typeof sendPrompt==='function'){ sendPrompt(msg); }
  else { navigator.clipboard.writeText(msg).then(()=>{ document.getElementById('dl-area').innerHTML='<div style="font-size:12px;color:var(--text2)">📋 Data kopieret til udklipsholder. Indsæt i chat.</div>'; }); }
};

// ══════════════════════════════════════════════
//  PDF EXPORT
// ══════════════════════════════════════════════
window.exportPDF=function(){
  document.title=`Research Budget ${new Date().toLocaleDateString('da-DK')}`;
  window.print();
};

// ══════════════════════════════════════════════
//  BUILD PAYLOAD for export
// ══════════════════════════════════════════════
function buildPayload(){
  const yrs=years();
  const payload={numYears,eurRate,currency,lang,overheadPct,categories:[],rateDefs:RATE_DEFS.map(r=>({label:T[lang].salary_cats[r.key]||r.key,rate:rates[r.key]}))};
  categories.forEach(cat=>{
    const visRows=[];
    cat.rows.forEach(row=>{
      if(instFilter!=='all'&&row.inst!==instFilter)return;
      const yData=yrs.map(y=>({budget:rowBudget(row,y),fte:cat.hasFte?(row.fte[y]||0):null}));
      if(yData.some(d=>d.budget>0||(d.fte!=null&&d.fte>0))){
        visRows.push({label:rowLabel(row),inst:row.inst,desc:row.desc,years:yData});
      }
    });
    if(visRows.length) payload.categories.push({label:catLabel(cat),hasFte:cat.hasFte,desc:cat.desc,rows:visRows});
  });
  return payload;
}

// ══════════════════════════════════════════════
//  YEAR / INST EVENTS
// ══════════════════════════════════════════════
document.getElementById('year-btns').addEventListener('click',e=>{
  const btn=e.target.closest('.pill');if(!btn||!btn.dataset.y)return;
  numYears=parseInt(btn.dataset.y);
  document.querySelectorAll('#year-btns .pill').forEach(b=>b.classList.toggle('active',b.dataset.y==numYears));
  renderAll();
});
document.getElementById('inst-btns').addEventListener('click',e=>{
  const btn=e.target.closest('.pill');if(!btn||!btn.dataset.inst)return;
  instFilter=btn.dataset.inst;
  document.querySelectorAll('#inst-btns .pill').forEach(b=>b.classList.toggle('active',b.dataset.inst===instFilter));
  applyInstFilter();
});
document.getElementById('rate-inp').addEventListener('input',e=>{
  eurRate=parseFloat(e.target.value)||7.4728; updateTotals();
});

// ══════════════════════════════════════════════
//  INIT
// ══════════════════════════════════════════════
buildRatesPanel();
renderAll();
</script>
</body>
</html>
