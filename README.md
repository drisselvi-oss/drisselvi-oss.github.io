# drisselvi-oss.github.io
Budget annuel 
<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Mon Budget Annuel</title>
<link href="https://fonts.googleapis.com/css2?family=DM+Serif+Display&family=Nunito:wght@400;600;700;800&display=swap" rel="stylesheet">
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">
<style>
  :root {
    --bg-primary: #F4F1EC;
    --bg-secondary: #FFFFFF;
    --bg-card: #FFFFFF;
    --text-primary: #2C2C2C;
    --text-secondary: #6B6B6B;
    --text-muted: #9E9E9E;
    --accent: #C8956C;
    --accent-light: #E8D5C4;
    --accent-dark: #A07050;
    --green: #5A9A6E;
    --green-bg: #EAF4EC;
    --red: #C75B5B;
    --red-bg: #FAEAEA;
    --blue: #5B7FC7;
    --blue-bg: #EAF0FA;
    --border: #E5E0D8;
    --shadow: 0 2px 12px rgba(0,0,0,0.06);
    --shadow-lg: 0 8px 30px rgba(0,0,0,0.08);
    --radius: 14px;
    --tab-active-bg: var(--accent);
    --tab-active-text: #FFF;
    --annual-badge: #8B6DC7;
    --annual-badge-bg: #F0EAFA;
    --savings: #2E8B8B;
    --savings-bg: #E4F5F3;
    --savings-light: #D0EDEB;
    --input-bg: #FAF8F5;
  }
  html.dark {
    --bg-primary: #1A1A1F;
    --bg-secondary: #222228;
    --bg-card: #2A2A32;
    --text-primary: #E8E4DF;
    --text-secondary: #A09A90;
    --text-muted: #6E6A62;
    --accent: #D4A06A;
    --accent-light: #3D3228;
    --accent-dark: #E8B880;
    --green: #6EBD84;
    --green-bg: #1E2E22;
    --red: #E07070;
    --red-bg: #2E1E1E;
    --blue: #7094DD;
    --blue-bg: #1E2436;
    --border: #3A3A42;
    --shadow: 0 2px 12px rgba(0,0,0,0.2);
    --shadow-lg: 0 8px 30px rgba(0,0,0,0.3);
    --annual-badge: #A88AE0;
    --annual-badge-bg: #2A2440;
    --savings: #4EC4C4;
    --savings-bg: #1E2E2E;
    --savings-light: #253838;
    --input-bg: #24242C;
  }
  * { margin:0; padding:0; box-sizing:border-box; }
  body {
    font-family: 'Nunito', sans-serif;
    background: var(--bg-primary);
    color: var(--text-primary);
    min-height: 100vh;
    overflow-x: hidden;
  }
  .app-header {
    background: var(--bg-secondary);
    border-bottom: 1px solid var(--border);
    padding: 16px 20px 0;
    position: sticky; top:0; z-index: 100;
    box-shadow: var(--shadow);
  }
  .header-top {
    display: flex; align-items: center; justify-content: space-between;
    margin-bottom: 14px;
  }
  .logo { display: flex; align-items: center; gap: 10px; }
  .logo-icon {
    width: 38px; height: 38px; border-radius: 10px;
    background: linear-gradient(135deg, var(--accent), var(--accent-dark));
    display: flex; align-items: center; justify-content: center;
    color: #FFF; font-size: 18px;
  }
  .logo h1 {
    font-family: 'DM Serif Display', serif;
    font-size: 22px; font-weight: 400; color: var(--text-primary);
  }
  .header-actions { display: flex; gap: 8px; }
  .btn-icon {
    width: 36px; height: 36px; border-radius: 10px; border: 1px solid var(--border);
    background: var(--bg-card); color: var(--text-secondary);
    display: flex; align-items: center; justify-content: center;
    cursor: pointer; font-size: 14px; transition: all .2s;
  }
  .btn-icon:hover { border-color: var(--accent); color: var(--accent); }
  .tabs-container {
    display: flex; gap: 4px; overflow-x: auto; padding-bottom: 0;
    scrollbar-width: none; -ms-overflow-style: none;
  }
  .tabs-container::-webkit-scrollbar { display: none; }
  .tab-btn {
    padding: 8px 14px; border-radius: 10px 10px 0 0;
    border: none; background: transparent;
    font-family: 'Nunito', sans-serif; font-size: 13px; font-weight: 700;
    color: var(--text-muted); cursor: pointer; white-space: nowrap;
    transition: all .25s; position: relative;
  }
  .tab-btn:hover { color: var(--text-secondary); background: var(--bg-primary); }
  .tab-btn.active { background: var(--accent); color: #FFF; }
  .tab-btn.annual-tab { color: var(--annual-badge); }
  .tab-btn.annual-tab.active { background: var(--annual-badge); color: #FFF; }
  .tab-btn.savings-tab { color: var(--savings); }
  .tab-btn.savings-tab.active { background: var(--savings); color: #FFF; }
  .tab-btn .tab-balance {
    display: block; font-size: 10px; font-weight: 600; margin-top: 1px;
  }
  .tab-btn .tab-balance.positive { color: var(--green); }
  .tab-btn .tab-balance.negative { color: var(--red); }
  .tab-btn.active .tab-balance.positive,
  .tab-btn.active .tab-balance.negative { color: rgba(255,255,255,0.85); }
  .main-content {
    max-width: 800px; margin: 0 auto;
    padding: 20px 16px 100px;
  }
  .summary-row {
    display: grid; grid-template-columns: 1fr 1fr 1fr 1fr; gap: 10px;
    margin-bottom: 20px;
  }
  .summary-row.three-cols { grid-template-columns: 1fr 1fr 1fr; }
  .summary-card {
    background: var(--bg-card); border-radius: var(--radius);
    padding: 14px 16px; box-shadow: var(--shadow);
    border: 1px solid var(--border);
  }
  .summary-card .label {
    font-size: 11px; font-weight: 700; text-transform: uppercase;
    letter-spacing: .8px; color: var(--text-muted); margin-bottom: 4px;
  }
  .summary-card .value {
    font-family: 'DM Serif Display', serif;
    font-size: 22px; color: var(--text-primary);
  }
  .summary-card.income .value { color: var(--green); }
  .summary-card.expense .value { color: var(--red); }
  .summary-card.balance .value.positive { color: var(--green); }
  .summary-card.balance .value.negative { color: var(--red); }
  .summary-card.savings-card .value { color: var(--savings); }
  .section {
    background: var(--bg-card); border-radius: var(--radius);
    box-shadow: var(--shadow); border: 1px solid var(--border);
    margin-bottom: 16px; overflow: hidden;
  }
  .section-header {
    display: flex; align-items: center; justify-content: space-between;
    padding: 14px 18px; border-bottom: 1px solid var(--border);
  }
  .section-title {
    display: flex; align-items: center; gap: 8px;
    font-size: 14px; font-weight: 800; color: var(--text-primary);
  }
  .section-title .icon {
    width: 28px; height: 28px; border-radius: 8px;
    display: flex; align-items: center; justify-content: center; font-size: 13px;
  }
  .section-title .icon.income-icon { background: var(--green-bg); color: var(--green); }
  .section-title .icon.expense-icon { background: var(--red-bg); color: var(--red); }
  .section-title .icon.annual-icon { background: var(--annual-badge-bg); color: var(--annual-badge); }
  .section-title .icon.savings-icon { background: var(--savings-bg); color: var(--savings); }
  .section-total { font-family: 'DM Serif Display', serif; font-size: 18px; }
  .section-total.income-total { color: var(--green); }
  .section-total.expense-total { color: var(--red); }
  .section-total.annual-total { color: var(--annual-badge); }
  .section-total.savings-total { color: var(--savings); }
  .budget-row {
    display: grid; grid-template-columns: 1fr 140px 40px;
    align-items: center; padding: 10px 18px;
    border-bottom: 1px solid var(--border); transition: background .15s;
  }
  .budget-row:last-child { border-bottom: none; }
  .budget-row:hover { background: var(--input-bg); }
  .budget-row.auto-row { background: var(--annual-badge-bg); cursor: default; }
  .budget-row.auto-row:hover { background: var(--annual-badge-bg); }
  .budget-row.provision-row { background: var(--blue-bg); cursor: default; }
  .budget-row.provision-row:hover { background: var(--blue-bg); }
  .budget-row.provision-row .auto-value { color: var(--blue); }
  .provision-detail-label {
    display: flex; flex-direction: column; gap: 1px;
  }
  .provision-detail-label .prov-name { font-size: 14px; font-weight: 600; color: var(--text-primary); }
  .provision-detail-label .prov-meta { font-size: 11px; color: var(--text-muted); font-weight: 600; }
  .provision-badge {
    display: inline-flex; align-items: center; gap: 4px;
    background: var(--blue-bg); color: var(--blue);
    padding: 2px 8px; border-radius: 6px; font-size: 10px; font-weight: 800;
    margin-left: 6px; letter-spacing: .5px;
  }
  .section-total.provision-total { color: var(--blue); }
  .section-title .icon.provision-icon { background: var(--blue-bg); color: var(--blue); }
  .row-label { font-size: 14px; font-weight: 600; color: var(--text-primary); }
  .row-label input {
    border: none; background: transparent; font-family: 'Nunito', sans-serif;
    font-size: 14px; font-weight: 600; color: var(--text-primary);
    width: 100%; outline: none;
  }
  .row-label input::placeholder { color: var(--text-muted); }
  .row-label input:focus { border-bottom: 2px solid var(--accent); }
  .row-amount input {
    border: none; background: var(--input-bg); border-radius: 8px;
    padding: 8px 12px; font-family: 'Nunito', sans-serif;
    font-size: 16px; font-weight: 700; color: var(--text-primary);
    width: 100%; text-align: right; outline: none; transition: all .2s;
  }
  .row-amount input:focus { background: var(--bg-secondary); box-shadow: 0 0 0 2px var(--accent); }
  .row-amount .auto-value {
    font-family: 'Nunito', sans-serif; font-size: 16px; font-weight: 700;
    color: var(--annual-badge); text-align: right; padding: 8px 12px;
  }
  .row-delete { display: flex; justify-content: center; }
  .row-delete button {
    width: 30px; height: 30px; border-radius: 8px;
    border: none; background: transparent; color: var(--text-muted);
    cursor: pointer; font-size: 13px; transition: all .2s;
    display: flex; align-items: center; justify-content: center;
  }
  .row-delete button:hover { background: var(--red-bg); color: var(--red); }
  .add-row-btn {
    display: flex; align-items: center; justify-content: center; gap: 6px;
    width: 100%; padding: 12px; border: none;
    background: transparent; font-family: 'Nunito', sans-serif;
    font-size: 13px; font-weight: 700; color: var(--accent);
    cursor: pointer; transition: all .2s;
  }
  .add-row-btn:hover { background: var(--accent-light); }
  .annual-row {
    display: grid; grid-template-columns: 1fr 140px 120px 40px;
    align-items: center; padding: 10px 18px;
    border-bottom: 1px solid var(--border); transition: background .15s;
  }
  .annual-row:last-child { border-bottom: none; }
  .annual-row:hover { background: var(--input-bg); }
  .month-select {
    padding: 8px 10px; border-radius: 8px; border: 1px solid var(--border);
    background: var(--input-bg); font-family: 'Nunito', sans-serif;
    font-size: 14px; font-weight: 600; color: var(--text-primary);
    outline: none; cursor: pointer; width: 100%;
  }
  .month-select:focus { border-color: var(--accent); box-shadow: 0 0 0 2px var(--accent-light); }
  .annual-summary {
    display: grid; grid-template-columns: repeat(3, 1fr); gap: 10px;
    margin-bottom: 20px;
  }
  .annual-summary .summary-card .value { color: var(--annual-badge); }
  .balance-bar { height: 6px; border-radius: 3px; background: var(--border); margin-top: 8px; overflow: hidden; }
  .balance-bar-fill { height: 100%; border-radius: 3px; transition: width .4s ease; }
  .balance-bar-fill.positive { background: var(--green); }
  .balance-bar-fill.negative { background: var(--red); }
  .modal-overlay {
    position: fixed; inset: 0; background: rgba(0,0,0,0.5);
    display: flex; align-items: center; justify-content: center;
    z-index: 200; opacity: 0; pointer-events: none; transition: opacity .25s;
  }
  .modal-overlay.show { opacity: 1; pointer-events: all; }
  .modal {
    background: var(--bg-card); border-radius: var(--radius);
    padding: 24px; max-width: 400px; width: 90%;
    box-shadow: var(--shadow-lg);
    transform: translateY(20px); transition: transform .25s;
  }
  .modal-overlay.show .modal { transform: translateY(0); }
  .modal h3 { font-family: 'DM Serif Display', serif; font-size: 20px; margin-bottom: 12px; }
  .modal p { color: var(--text-secondary); font-size: 14px; margin-bottom: 20px; line-height: 1.5; }
  .modal-actions { display: flex; gap: 10px; justify-content: flex-end; }
  .modal-btn {
    padding: 10px 20px; border-radius: 10px; border: none;
    font-family: 'Nunito', sans-serif; font-size: 14px; font-weight: 700;
    cursor: pointer; transition: all .2s;
  }
  .modal-btn.cancel { background: var(--bg-primary); color: var(--text-secondary); }
  .modal-btn.cancel:hover { background: var(--border); }
  .modal-btn.confirm { background: var(--red); color: #FFF; }
  .modal-btn.confirm:hover { opacity: .85; }
  .toast {
    position: fixed; bottom: 24px; left: 50%; transform: translateX(-50%) translateY(80px);
    background: var(--bg-card); color: var(--text-primary); border: 1px solid var(--border);
    padding: 12px 24px; border-radius: 12px; font-size: 14px; font-weight: 600;
    box-shadow: var(--shadow-lg); z-index: 300; transition: transform .3s ease;
    display: flex; align-items: center; gap: 8px;
  }
  .toast.show { transform: translateX(-50%) translateY(0); }
  .toast .toast-icon { font-size: 16px; }
  .file-input-hidden { display: none; }
  .auto-badge {
    display: inline-flex; align-items: center; gap: 4px;
    background: var(--annual-badge-bg); color: var(--annual-badge);
    padding: 2px 8px; border-radius: 6px; font-size: 10px; font-weight: 800;
    margin-left: 6px; letter-spacing: .5px;
  }
  .year-selector { display: flex; align-items: center; gap: 6px; }
  .year-selector span {
    font-family: 'DM Serif Display', serif;
    font-size: 17px; min-width: 50px; text-align: center;
  }
  .year-btn {
    width: 28px; height: 28px; border-radius: 8px;
    border: 1px solid var(--border); background: var(--bg-card);
    color: var(--text-secondary); cursor: pointer;
    display: flex; align-items: center; justify-content: center;
    font-size: 12px; transition: all .2s;
  }
  .year-btn:hover { border-color: var(--accent); color: var(--accent); }
  .annual-month-dist { padding: 14px 18px; }
  .dist-row { display: flex; align-items: center; gap: 10px; margin-bottom: 8px; }
  .dist-label { font-size: 12px; font-weight: 700; color: var(--text-muted); width: 36px; }
  .dist-bar { flex: 1; height: 8px; border-radius: 4px; background: var(--border); overflow: hidden; }
  .dist-bar-fill { height: 100%; border-radius: 4px; background: var(--annual-badge); transition: width .4s; }
  .dist-bar-fill.savings-fill { background: var(--savings); }
  .dist-amount { font-size: 12px; font-weight: 700; color: var(--text-secondary); width: 70px; text-align: right; }

  /* === SAVINGS PAGE === */
  .savings-summary {
    display: grid; grid-template-columns: repeat(3, 1fr); gap: 10px;
    margin-bottom: 20px;
  }
  .savings-summary .summary-card .value { color: var(--savings); }
  .savings-table-header {
    display: grid; grid-template-columns: 50px 1fr 100px 110px;
    padding: 10px 18px; font-size: 11px; font-weight: 800;
    text-transform: uppercase; letter-spacing: .8px; color: var(--text-muted);
    border-bottom: 2px solid var(--border);
  }
  .savings-table-row {
    display: grid; grid-template-columns: 50px 1fr 100px 110px;
    align-items: center; padding: 12px 18px;
    border-bottom: 1px solid var(--border); transition: background .15s;
  }
  .savings-table-row:last-child { border-bottom: none; }
  .savings-table-row:hover { background: var(--input-bg); }
  .savings-table-row .month-label {
    font-size: 13px; font-weight: 800; color: var(--text-muted);
  }
  .savings-table-row .month-name {
    font-size: 14px; font-weight: 700; color: var(--text-primary);
  }
  .savings-table-row .sav-amount {
    font-size: 16px; font-weight: 700; color: var(--savings); text-align: right;
  }
  .savings-table-row .sav-cumul {
    font-family: 'DM Serif Display', serif;
    font-size: 17px; color: var(--text-primary); text-align: right;
  }
  .savings-table-row.has-value .sav-cumul { color: var(--savings); }

  /* Savings inline section in month page */
  .savings-inline {
    display: flex; align-items: center; justify-content: space-between;
    padding: 14px 18px;
  }
  .savings-inline-label {
    display: flex; align-items: center; gap: 8px;
    font-size: 14px; font-weight: 700; color: var(--text-primary);
  }
  .savings-inline-input input {
    border: none; background: var(--savings-bg); border-radius: 8px;
    padding: 8px 14px; font-family: 'Nunito', sans-serif;
    font-size: 16px; font-weight: 700; color: var(--savings);
    width: 140px; text-align: right; outline: none; transition: all .2s;
  }
  .savings-inline-input input:focus {
    background: var(--bg-secondary); box-shadow: 0 0 0 2px var(--savings);
  }

  /* Savings chart canvas */
  .savings-chart-container {
    padding: 18px; position: relative;
  }
  .savings-chart-canvas {
    width: 100%; height: 200px; display: block;
  }

  /* Savings goal */
  .savings-goal-section {
    padding: 16px 18px; border-top: 1px solid var(--border);
  }
  .savings-goal-row {
    display: flex; align-items: center; gap: 12px; flex-wrap: wrap;
  }
  .savings-goal-row label {
    font-size: 13px; font-weight: 700; color: var(--text-secondary);
  }
  .savings-goal-row input {
    border: 1px solid var(--border); background: var(--input-bg); border-radius: 8px;
    padding: 8px 12px; font-family: 'Nunito', sans-serif;
    font-size: 16px; font-weight: 700; color: var(--savings);
    width: 140px; text-align: right; outline: none; transition: all .2s;
  }
  .savings-goal-row input:focus { border-color: var(--savings); box-shadow: 0 0 0 2px var(--savings-light); }
  .savings-goal-bar {
    width: 100%; height: 12px; border-radius: 6px; background: var(--border);
    margin-top: 12px; overflow: hidden; position: relative;
  }
  .savings-goal-fill {
    height: 100%; border-radius: 6px;
    background: linear-gradient(90deg, var(--savings), var(--green));
    transition: width .5s ease;
  }
  .savings-goal-pct {
    margin-top: 6px; font-size: 13px; font-weight: 700; color: var(--savings);
  }

  .empty-state { text-align: center; padding: 32px 20px; color: var(--text-muted); }
  .empty-state i { font-size: 28px; margin-bottom: 10px; display: block; color: var(--border); }
  .empty-state p { font-size: 13px; }

  @media (max-width: 600px) {
    .summary-row { grid-template-columns: 1fr 1fr; }
    .summary-row.three-cols { grid-template-columns: 1fr; }
    .annual-summary { grid-template-columns: 1fr; }
    .savings-summary { grid-template-columns: 1fr; }
    .budget-row { grid-template-columns: 1fr 110px 36px; padding: 8px 12px; }
    .annual-row { grid-template-columns: 1fr 100px 90px 36px; padding: 8px 12px; }
    .savings-table-header { grid-template-columns: 40px 1fr 80px 90px; padding: 8px 12px; font-size: 10px; }
    .savings-table-row { grid-template-columns: 40px 1fr 80px 90px; padding: 10px 12px; }
    .savings-table-row .sav-amount { font-size: 14px; }
    .savings-table-row .sav-cumul { font-size: 14px; }
    .section-header { padding: 12px 14px; }
    .summary-card .value { font-size: 18px; }
    .tab-btn { padding: 7px 10px; font-size: 12px; }
    .header-top { flex-wrap: wrap; gap: 8px; }
    .savings-inline { flex-wrap: wrap; gap: 10px; }
    .savings-inline-input input { width: 120px; }
  }

  @keyframes fadeIn { from { opacity:0; transform: translateY(10px); } to { opacity:1; transform: translateY(0); } }
  .section { animation: fadeIn .35s ease forwards; }
  .section:nth-child(2) { animation-delay: .05s; }
  .section:nth-child(3) { animation-delay: .1s; }
  .section:nth-child(4) { animation-delay: .15s; }
  .section:nth-child(5) { animation-delay: .2s; }
</style>
</head>
<body>

<div class="app-header">
  <div class="header-top">
    <div class="logo">
      <div class="logo-icon"><i class="fas fa-wallet"></i></div>
      <h1>Mon Budget</h1>
    </div>
    <div style="display:flex;align-items:center;gap:10px;">
      <div class="year-selector">
        <button class="year-btn" onclick="changeYear(-1)"><i class="fas fa-chevron-left"></i></button>
        <span id="yearDisplay">2025</span>
        <button class="year-btn" onclick="changeYear(1)"><i class="fas fa-chevron-right"></i></button>
      </div>
     
