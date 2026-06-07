<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>AGI Network - منصة التعدين السحابي</title>
<link href="https://fonts.googleapis.com/css2?family=Cairo:wght@300;400;600;700;900&family=Rajdhani:wght@400;600;700&display=swap" rel="stylesheet">
<style>
:root{--gold:#F5C518;--gold-dark:#C9A000;--bg-dark:#0A0C14;--bg-card:#111827;--bg-card2:#1A2235;--border:rgba(245,197,24,0.2);--text:#E8EAF0;--muted:#8B95A8;--green:#00D68F;--red:#FF4B55;--blue:#4B8FFF;--purple:#9B6DFF;}
*{margin:0;padding:0;box-sizing:border-box;}
body{font-family:'Cairo',sans-serif;background:var(--bg-dark);color:var(--text);min-height:100vh;overflow-x:hidden;}
/* LAYOUT */
.app{display:flex;min-height:100vh;}
.sidebar{width:240px;background:var(--bg-card);border-left:1px solid var(--border);display:flex;flex-direction:column;position:fixed;top:0;right:0;height:100vh;z-index:100;}
.main{margin-right:240px;flex:1;min-height:100vh;}
/* SIDEBAR */
.logo-area{padding:20px 16px;border-bottom:1px solid var(--border);text-align:center;}
.logo-text{font-family:'Rajdhani',sans-serif;font-size:28px;font-weight:700;color:var(--gold);letter-spacing:2px;}
.logo-sub{font-size:11px;color:var(--muted);letter-spacing:1px;}
.nav{flex:1;padding:12px 0;overflow-y:auto;}
.nav-item{display:flex;align-items:center;gap:10px;padding:11px 18px;cursor:pointer;transition:all .2s;border-right:3px solid transparent;font-size:14px;color:var(--muted);}
.nav-item:hover{background:rgba(245,197,24,.05);color:var(--text);}
.nav-item.active{background:rgba(245,197,24,.1);color:var(--gold);border-right-color:var(--gold);}
.nav-badge{margin-right:auto;background:var(--gold);color:#000;font-size:10px;font-weight:700;padding:2px 7px;border-radius:20px;}
.user-area{padding:16px;border-top:1px solid var(--border);display:flex;align-items:center;gap:10px;}
.user-avatar{width:38px;height:38px;border-radius:50%;background:linear-gradient(135deg,var(--gold),var(--gold-dark));display:flex;align-items:center;justify-content:center;font-weight:700;color:#000;font-size:14px;flex-shrink:0;}
.user-name{font-size:13px;font-weight:600;}
.user-role{font-size:11px;color:var(--gold);}
/* TOPBAR */
.topbar{background:var(--bg-card);border-bottom:1px solid var(--border);padding:12px 24px;display:flex;align-items:center;justify-content:space-between;position:sticky;top:0;z-index:50;}
.page-title{font-size:18px;font-weight:700;}
.topbar-actions{display:flex;align-items:center;gap:12px;}
.btn{padding:8px 18px;border-radius:8px;font-family:'Cairo',sans-serif;font-size:13px;font-weight:600;cursor:pointer;border:none;transition:all .2s;}
.btn-gold{background:var(--gold);color:#000;}
.btn-gold:hover{background:var(--gold-dark);}
.btn-outline{background:transparent;border:1px solid var(--border);color:var(--text);}
.btn-outline:hover{border-color:var(--gold);color:var(--gold);}
.notif-btn{width:38px;height:38px;border-radius:8px;background:var(--bg-card2);border:1px solid var(--border);display:flex;align-items:center;justify-content:center;cursor:pointer;font-size:18px;position:relative;}
.notif-dot{position:absolute;top:6px;left:6px;width:8px;height:8px;border-radius:50%;background:var(--red);}
/* CONTENT */
.content{padding:24px;}
.page{display:none;}
.page.active{display:block;}
/* CARDS */
.card{background:var(--bg-card);border:1px solid var(--border);border-radius:14px;padding:20px;margin-bottom:16px;}
.card-header{display:flex;align-items:center;justify-content:space-between;margin-bottom:16px;}
.card-title{font-size:15px;font-weight:600;}
/* STATS */
.stats-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:16px;margin-bottom:24px;}
.stat-card{background:var(--bg-card);border:1px solid var(--border);border-radius:14px;padding:18px;}
.stat-value{font-size:24px;font-weight:700;line-height:1;margin:6px 0 4px;}
.stat-label{font-size:12px;color:var(--muted);}
.stat-change{font-size:12px;margin-top:8px;}
.up{color:var(--green);}
.down{color:var(--red);}
/* GRID */
.grid-2{display:grid;grid-template-columns:1fr 1fr;gap:16px;margin-bottom:16px;}
/* MACHINES */
.machines-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:16px;}
.machine-card{background:var(--bg-card);border:1px solid var(--border);border-radius:14px;padding:20px;transition:border-color .2s;}
.machine-card.owned{border-color:var(--gold);}
.machine-card.locked-card{opacity:.8;}
.mbadge{display:inline-flex;align-items:center;gap:5px;font-size:11px;font-weight:700;padding:3px 10px;border-radius:20px;margin-bottom:12px;}
.mbadge.free{background:rgba(0,214,143,.15);color:var(--green);}
.mbadge.pro{background:rgba(245,197,24,.15);color:var(--gold);}
.mbadge.locked{background:rgba(139,149,168,.1);color:var(--muted);}
.mbadge.ultra{background:rgba(155,109,255,.15);color:var(--purple);}
.mname{font-size:16px;font-weight:700;margin-bottom:4px;}
.mhash{font-size:13px;color:var(--muted);margin-bottom:14px;}
.mstats{display:grid;grid-template-columns:1fr 1fr;gap:8px;margin-bottom:14px;}
.mstat{background:var(--bg-dark);border-radius:8px;padding:8px;}
.mstat-label{font-size:10px;color:var(--muted);margin-bottom:2px;}
.mstat-value{font-size:13px;font-weight:600;}
.mprogress{height:5px;background:rgba(255,255,255,.08);border-radius:4px;margin-bottom:6px;}
.mprogress-bar{height:100%;border-radius:4px;background:var(--gold);transition:width 1s linear;}
.mspeed{font-size:11px;color:var(--muted);margin-bottom:14px;}
.coin-selector{display:flex;gap:6px;flex-wrap:wrap;margin:8px 0 14px;}
.coin-btn{padding:4px 10px;border-radius:6px;background:var(--bg-dark);border:1px solid var(--border);color:var(--muted);font-size:12px;cursor:pointer;font-family:'Cairo',sans-serif;transition:all .2s;}
.coin-btn.active{background:rgba(245,197,24,.15);border-color:var(--gold);color:var(--gold);}
/* MINING STATUS */
.mine-status{display:flex;align-items:center;gap:8px;padding:8px 12px;border-radius:8px;margin-top:8px;font-size:13px;}
.mine-status.running{background:rgba(0,214,143,.1);color:var(--green);border:1px solid rgba(0,214,143,.2);}
.mine-status.stopped{background:rgba(139,149,168,.08);color:var(--muted);border:1px solid var(--border);}
.pulse{width:8px;height:8px;border-radius:50%;background:var(--green);animation:pulse 1.5s infinite;flex-shrink:0;}
@keyframes pulse{0%,100%{opacity:1;transform:scale(1);}50%{opacity:.5;transform:scale(1.3);}}
/* WALLET */
.wallet-banner{background:linear-gradient(135deg,#1A2235,#0F1A2A);border:1px solid var(--gold);border-radius:14px;padding:24px;margin-bottom:24px;}
.wallet-total{font-size:36px;font-weight:900;color:var(--gold);}
.wallet-total span{font-size:16px;font-weight:400;color:var(--muted);}
.wallet-actions{display:flex;gap:10px;margin-top:16px;}
.wallet-btn{flex:1;padding:10px;border-radius:10px;text-align:center;font-family:'Cairo',sans-serif;font-size:13px;font-weight:600;cursor:pointer;border:none;transition:all .2s;}
.wallet-btn.withdraw{background:var(--gold);color:#000;}
.wallet-btn.deposit{background:var(--bg-card2);color:var(--text);border:1px solid var(--border);}
.wallet-btn.swap-btn{background:var(--bg-card2);color:var(--text);border:1px solid var(--border);}
.coins-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:12px;}
.coin-card{background:var(--bg-card2);border:1px solid var(--border);border-radius:12px;padding:16px;text-align:center;cursor:pointer;transition:border-color .2s;}
.coin-card:hover{border-color:rgba(245,197,24,.4);}
.coin-symbol{font-size:28px;margin-bottom:6px;}
.coin-name{font-size:14px;font-weight:600;}
.coin-balance{font-size:12px;color:var(--muted);margin-top:4px;}
.coin-usd{font-size:15px;font-weight:700;margin-top:4px;color:var(--gold);}
/* EARN */
.earn-tabs{display:flex;gap:4px;background:var(--bg-dark);border-radius:10px;padding:4px;margin-bottom:20px;}
.earn-tab{flex:1;padding:9px;border-radius:8px;text-align:center;font-size:13px;font-weight:600;cursor:pointer;color:var(--muted);transition:all .2s;font-family:'Cairo',sans-serif;}
.earn-tab.active{background:var(--bg-card);color:var(--gold);}
.ad-card{background:var(--bg-card);border:1px solid var(--border);border-radius:12px;padding:16px;display:flex;align-items:center;gap:14px;margin-bottom:10px;}
.ad-thumb{width:60px;height:60px;border-radius:10px;background:var(--bg-dark);display:flex;align-items:center;justify-content:center;font-size:28px;flex-shrink:0;}
.ad-info{flex:1;}
.ad-title{font-size:14px;font-weight:600;margin-bottom:3px;}
.ad-desc{font-size:12px;color:var(--muted);margin-bottom:6px;}
.ad-reward{font-size:13px;color:var(--gold);font-weight:600;}
.ad-btn{padding:8px 16px;border-radius:8px;background:var(--gold);color:#000;font-family:'Cairo',sans-serif;font-size:13px;font-weight:700;cursor:pointer;border:none;white-space:nowrap;}
/* REFERRAL */
.ref-code-box{background:var(--bg-dark);border:1px dashed var(--gold);border-radius:10px;padding:14px 18px;display:flex;align-items:center;justify-content:space-between;margin-bottom:16px;}
.ref-code{font-family:'Rajdhani',monospace;font-size:22px;font-weight:700;color:var(--gold);letter-spacing:3px;}
.copy-btn{background:var(--gold);color:#000;border:none;border-radius:7px;padding:7px 14px;font-family:'Cairo',sans-serif;font-size:12px;font-weight:700;cursor:pointer;}
.ref-stats{display:grid;grid-template-columns:1fr 1fr 1fr;gap:12px;margin-bottom:16px;}
.ref-stat{background:var(--bg-dark);border-radius:10px;padding:14px;text-align:center;}
.ref-stat-val{font-size:22px;font-weight:700;color:var(--gold);}
.ref-stat-label{font-size:12px;color:var(--muted);margin-top:2px;}
/* GAMES */
.games-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:16px;}
.game-card{background:var(--bg-card);border:1px solid var(--border);border-radius:14px;overflow:hidden;transition:transform .2s,border-color .2s;cursor:pointer;}
.game-card:hover{transform:translateY(-3px);border-color:rgba(245,197,24,.5);}
.game-thumb{height:130px;display:flex;align-items:center;justify-content:center;font-size:60px;}
.game-info{padding:14px;}
.game-name{font-size:15px;font-weight:700;margin-bottom:4px;}
.game-desc{font-size:12px;color:var(--muted);margin-bottom:10px;}
.game-reward{font-size:13px;color:var(--gold);font-weight:600;}
/* SWAP */
.swap-box{background:var(--bg-dark);border-radius:12px;padding:16px;margin-bottom:12px;}
.swap-row{display:flex;align-items:center;gap:10px;}
.swap-amount{flex:1;background:transparent;border:none;font-size:24px;font-weight:700;color:var(--text);font-family:'Cairo',sans-serif;outline:none;width:100%;}
.swap-coin-badge{background:var(--bg-card);border:1px solid var(--border);border-radius:8px;padding:7px 12px;font-size:14px;font-weight:600;cursor:pointer;display:flex;align-items:center;gap:6px;white-space:nowrap;color:var(--text);font-family:'Cairo',sans-serif;}
/* ADMIN */
.admin-lock{display:flex;flex-direction:column;align-items:center;justify-content:center;min-height:60vh;gap:16px;}
.admin-input{background:var(--bg-dark);border:1px solid var(--border);border-radius:8px;padding:12px 18px;color:var(--text);font-family:'Cairo',sans-serif;font-size:16px;outline:none;width:280px;text-align:center;letter-spacing:4px;}
.admin-input:focus{border-color:var(--gold);}
/* TABLE */
.table-wrap{overflow-x:auto;}
table{width:100%;border-collapse:collapse;font-size:13px;}
th{text-align:right;padding:10px 14px;color:var(--muted);font-weight:600;border-bottom:1px solid var(--border);white-space:nowrap;}
td{padding:12px 14px;border-bottom:1px solid rgba(255,255,255,.04);vertical-align:middle;}
tr:last-child td{border-bottom:none;}
.badge{display:inline-flex;align-items:center;gap:4px;padding:3px 10px;border-radius:20px;font-size:11px;font-weight:600;}
.badge-green{background:rgba(0,214,143,.15);color:var(--green);}
.badge-red{background:rgba(255,75,85,.15);color:var(--red);}
.badge-gold{background:rgba(245,197,24,.15);color:var(--gold);}
.badge-blue{background:rgba(75,143,255,.15);color:var(--blue);}
/* MODAL */
.modal-overlay{display:none;position:fixed;inset:0;background:rgba(0,0,0,.75);z-index:200;align-items:center;justify-content:center;}
.modal-overlay.open{display:flex;}
.modal{background:var(--bg-card);border:1px solid var(--gold);border-radius:18px;padding:28px;width:440px;max-width:95vw;max-height:90vh;overflow-y:auto;}
.modal-title{font-size:18px;font-weight:700;margin-bottom:20px;}
.input-group{margin-bottom:14px;}
.input-label{font-size:13px;color:var(--muted);margin-bottom:6px;}
.input-field{width:100%;background:var(--bg-dark);border:1px solid var(--border);border-radius:8px;padding:10px 14px;color:var(--text);font-family:'Cairo',sans-serif;font-size:14px;outline:none;transition:border-color .2s;}
.input-field:focus{border-color:var(--gold);}
select.input-field{cursor:pointer;}
/* WALLET CONNECT BUTTONS */
.wallet-connect-grid{display:grid;grid-template-columns:1fr 1fr;gap:10px;margin-bottom:16px;}
.wallet-connect-btn{display:flex;align-items:center;gap:10px;padding:14px;border-radius:12px;background:var(--bg-dark);border:1px solid var(--border);cursor:pointer;transition:all .2s;text-decoration:none;color:var(--text);}
.wallet-connect-btn:hover{border-color:var(--gold);color:var(--gold);}
.wallet-icon{font-size:28px;}
.wallet-connect-name{font-size:14px;font-weight:600;}
.wallet-connect-chain{font-size:11px;color:var(--muted);}
/* ADMIN WALLET */
.admin-wallet-card{background:linear-gradient(135deg,#1a0a00,#2A1500);border:2px solid var(--gold);border-radius:16px;padding:24px;margin-bottom:20px;}
.admin-wallet-id{font-family:'Rajdhani',monospace;font-size:14px;color:var(--muted);margin-bottom:4px;}
.admin-wallet-balance{font-size:42px;font-weight:900;color:var(--gold);}
.admin-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:14px;margin-bottom:20px;}
.admin-stat{background:var(--bg-card);border:1px solid var(--border);border-radius:12px;padding:16px;text-align:center;}
.admin-stat-val{font-size:26px;font-weight:700;color:var(--gold);}
.admin-stat-label{font-size:12px;color:var(--muted);}
.admin-actions-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:12px;margin-bottom:20px;}
.admin-action{background:var(--bg-card);border:1px solid var(--border);border-radius:12px;padding:16px;text-align:center;cursor:pointer;transition:all .2s;}
.admin-action:hover{border-color:var(--gold);}
.admin-action-icon{font-size:30px;margin-bottom:8px;}
.admin-action-label{font-size:13px;font-weight:600;}
/* VIDEO OVERLAY */
.video-overlay{display:none;position:fixed;inset:0;background:rgba(0,0,0,.92);z-index:300;align-items:center;justify-content:center;flex-direction:column;gap:20px;}
.video-overlay.open{display:flex;}
.video-screen{width:480px;max-width:90vw;height:270px;background:var(--bg-card);border-radius:14px;display:flex;align-items:center;justify-content:center;font-size:50px;border:2px solid var(--gold);}
.video-timer{font-size:40px;font-weight:700;color:var(--gold);}
.video-skip{background:var(--gold);color:#000;border:none;border-radius:8px;padding:10px 28px;font-family:'Cairo',sans-serif;font-size:14px;font-weight:700;cursor:pointer;opacity:.4;pointer-events:none;}
.video-skip.ready{opacity:1;pointer-events:all;}
/* TOAST */
.toast{position:fixed;bottom:24px;right:50%;transform:translateX(50%);background:var(--bg-card);border:1px solid var(--gold);border-radius:10px;padding:12px 24px;font-size:14px;font-weight:600;color:var(--gold);z-index:999;opacity:0;transition:opacity .3s;pointer-events:none;white-space:nowrap;}
.toast.show{opacity:1;}
/* LIVE MINING ROW */
.live-row{background:var(--bg-dark);border-radius:10px;padding:12px 16px;display:flex;align-items:center;gap:12px;margin-bottom:6px;}
.live-dot{width:8px;height:8px;border-radius:50%;background:var(--green);animation:pulse 1.5s infinite;flex-shrink:0;}
.live-text{font-size:13px;flex:1;}
.live-earn{font-size:14px;font-weight:700;color:var(--gold);}
::-webkit-scrollbar{width:5px;}
::-webkit-scrollbar-thumb{background:var(--border);border-radius:10px;}
::-webkit-scrollbar-thumb:hover{background:var(--gold);}
</style>
</head>
<body>
<div class="app">
<!-- SIDEBAR -->
<aside class="sidebar">
  <div class="logo-area">
    <div class="logo-text">AGI NETWORK</div>
    <div class="logo-sub">منصة التعدين السحابي</div>
  </div>
  <nav class="nav">
    <div class="nav-item active" onclick="showPage('dashboard')"><span>⚡</span><span>لوحة التحكم</span></div>
    <div class="nav-item" onclick="showPage('mining')"><span>⛏️</span><span>ماكينات التعدين</span></div>
    <div class="nav-item" onclick="showPage('wallet')"><span>💼</span><span>المحفظة</span></div>
    <div class="nav-item" onclick="showPage('earn')"><span>💰</span><span>اكسب المزيد</span><span class="nav-badge">NEW</span></div>
    <div class="nav-item" onclick="showPage('referral')"><span>👥</span><span>دعوة الأصدقاء</span></div>
    <div class="nav-item" onclick="showPage('games')"><span>🎮</span><span>الألعاب</span></div>
    <div class="nav-item" onclick="showPage('swap')"><span>🔄</span><span>تبديل العملات</span></div>
    <div class="nav-item" onclick="showPage('admin')"><span>👑</span><span>لوحة الإدارة</span></div>
  </nav>
  <div class="user-area">
    <div class="user-avatar">أج</div>
    <div>
      <div class="user-name">المدير العام</div>
      <div class="user-role">⭐ المالك</div>
    </div>
  </div>
</aside>

<!-- MAIN -->
<main class="main">
  <div class="topbar">
    <div class="page-title" id="pageTitle">لوحة التحكم</div>
    <div class="topbar-actions">
      <button class="btn btn-gold" onclick="openModal('depositModal')">+ إيداع</button>
      <button class="btn btn-outline" onclick="openModal('withdrawModal')">سحب</button>
      <div class="notif-btn">🔔<div class="notif-dot"></div></div>
    </div>
  </div>

  <div class="content">

    <!-- ===== DASHBOARD ===== -->
    <div class="page active" id="page-dashboard">
      <div class="stats-grid">
        <div class="stat-card">
          <div style="font-size:22px">💰</div>
          <div class="stat-value" id="dashBalance">$847.32</div>
          <div class="stat-label">إجمالي الرصيد</div>
          <div class="stat-change up">↑ +$12.50 اليوم</div>
        </div>
        <div class="stat-card">
          <div style="font-size:22px">⛏️</div>
          <div class="stat-value" id="dashMining">$0.0000</div>
          <div class="stat-label">أرباح التعدين الحي</div>
          <div class="stat-change up">↑ يعمل الآن</div>
        </div>
        <div class="stat-card">
          <div style="font-size:22px">👥</div>
          <div class="stat-value">23</div>
          <div class="stat-label">الأصدقاء المدعوون</div>
          <div class="stat-change up">↑ +3 هذا الأسبوع</div>
        </div>
        <div class="stat-card">
          <div style="font-size:22px">⚡</div>
          <div class="stat-value" id="activeMachines">3</div>
          <div class="stat-label">الماكينات النشطة</div>
          <div class="stat-change up">↑ تعمل الآن</div>
        </div>
      </div>
      <div class="grid-2">
        <div class="card">
          <div class="card-header"><div class="card-title">🔥 التعدين الحي</div><span class="badge badge-green">● نشط</span></div>
          <div class="live-row"><div class="live-dot"></div><div class="live-text">Starter Miner — <span id="d_coin0">BTC</span></div><div class="live-earn" id="le0">$0.000000</div></div>
          <div class="live-row"><div class="live-dot"></div><div class="live-text">Pro Miner — <span id="d_coin1">ETH</span></div><div class="live-earn" id="le1">$0.000000</div></div>
          <div class="live-row"><div class="live-dot"></div><div class="live-text">Turbo Miner — <span id="d_coin2">USDT</span></div><div class="live-earn" id="le2">$0.000000</div></div>
        </div>
        <div class="card">
          <div class="card-header"><div class="card-title">⚡ الأرباح السريعة</div><button class="btn btn-gold" style="font-size:12px;padding:5px 12px" onclick="showPage('earn')">المزيد</button></div>
          <div class="ad-card" style="margin-bottom:8px"><div class=# Eg
بوت وموقع اجى نتورك
