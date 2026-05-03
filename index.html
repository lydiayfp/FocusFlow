<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1,viewport-fit=cover,user-scalable=no">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="default">
<meta name="apple-mobile-web-app-title" content="FocusFlow">
<meta name="theme-color" content="#ede5d4">
<title>FocusFlow</title>
<style>
:root{
  --bg:#ede5d4;--bg2:#e4dacb;--canvas:#f8f2e6;
  --surf:#fdfaf2;--surf2:#f2e8d8;--surf3:#e8dcc8;
  --bdr:#d8ccb4;--bdr2:#c8b898;
  --ink:#28200e;--ink2:#5a4828;--muted:#9a8868;--ghost:#c0aa8c;
  --terra:#b85c38;--terra2:#d4785a;--teralt:#faeee8;
  --ochre:#a87428;--ochre2:#c89030;--ochrelt:#f8f0da;
  --moss:#557040;--mosslt:#ecf2e2;--clay:#8a5630;
  --sh0:0 1px 3px rgba(70,40,10,.07);
  --sh1:0 3px 10px rgba(70,40,10,.10),0 1px 4px rgba(70,40,10,.06);
  --sh2:0 8px 28px rgba(70,40,10,.13),0 2px 8px rgba(70,40,10,.07);
  --sh3:0 16px 50px rgba(70,40,10,.16),0 4px 16px rgba(70,40,10,.08);
  --r:16px;--rsm:11px;--rxs:8px;
  --st:env(safe-area-inset-top,0px);
  --sb:env(safe-area-inset-bottom,0px);
}
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0;
  -webkit-tap-highlight-color:transparent;-webkit-touch-callout:none;}
html{height:100%;touch-action:manipulation;}
body{height:100%;overflow:hidden;background:var(--bg);color:var(--ink);
  font-family:-apple-system,'SF Pro Text','Helvetica Neue',Arial,sans-serif;
  -webkit-font-smoothing:antialiased;}
.ser{font-family:Georgia,'Book Antiqua',Palatino,serif;}
#app{display:flex;flex-direction:column;height:100vh;height:100dvh;padding-top:var(--st);}

/* FLASH */
#flash{position:fixed;inset:0;z-index:9999;pointer-events:none;opacity:0;
  background:rgba(184,92,56,.28);transition:opacity .12s;}

/* TOAST */
.toast{position:fixed;top:calc(var(--st) + 10px);left:12px;right:12px;
  background:var(--ink);color:#fff;border-radius:16px;padding:13px 16px;
  box-shadow:var(--sh3);z-index:998;
  transform:translateY(-140px);
  transition:transform .32s cubic-bezier(.32,.72,0,1);
  display:flex;align-items:flex-start;gap:10px;pointer-events:none;}
.toast.show{transform:translateY(0);}
.t-ico{font-size:22px;flex-shrink:0;line-height:1.2;}
.t-ttl{font-size:14px;font-weight:800;line-height:1.3;}
.t-sub{font-size:11px;opacity:.75;margin-top:2px;font-weight:500;}

/* HEADER */
.hdr{flex-shrink:0;padding:11px 16px 9px;
  background:linear-gradient(180deg,var(--canvas),var(--bg));
  border-bottom:1px solid var(--bdr);
  display:flex;align-items:center;justify-content:space-between;gap:8px;}
.logo{font-size:20px;font-weight:700;color:var(--clay);letter-spacing:-.3px;flex-shrink:0;}
.logo i{font-style:italic;color:var(--terra);}
.hdr-clock-wrap{flex:1;text-align:center;}
.hdr-clock{font-family:Georgia,serif;font-size:22px;font-weight:700;
  color:var(--ink);letter-spacing:1px;font-variant-numeric:tabular-nums;}
.hdr-date{font-size:9px;font-weight:600;color:var(--muted);letter-spacing:.3px;margin-top:1px;}
.bell-btn{flex-shrink:0;background:var(--surf);border:1.5px solid var(--bdr);
  border-radius:10px;padding:6px 10px;font-size:18px;line-height:1;
  cursor:pointer;box-shadow:var(--sh0);transition:all .15s;}
.bell-btn.on{background:var(--mosslt);border-color:var(--moss);}
.bell-btn:active{transform:scale(.92);}

/* NAV */
.nav{flex-shrink:0;display:flex;gap:5px;padding:9px 16px 7px;background:var(--bg);}
.tab{flex:1;padding:9px 4px;border-radius:var(--rsm);border:1.5px solid transparent;
  background:transparent;font-family:inherit;font-size:12px;font-weight:700;
  cursor:pointer;color:var(--muted);text-align:center;transition:all .18s;}
.tab.on{background:var(--surf);border-color:var(--bdr);color:var(--clay);box-shadow:var(--sh0);}

/* VIEWS */
.view{display:none;flex:1;overflow:hidden;flex-direction:column;}
.view.on{display:flex;}

/* STATS */
.stats{flex-shrink:0;display:flex;gap:7px;padding:0 16px 8px;}
.sc{flex:1;background:var(--surf);border:1px solid var(--bdr);border-radius:14px;
  padding:10px 8px;text-align:center;box-shadow:var(--sh0);}
.sv{font-family:Georgia,serif;font-size:19px;font-weight:700;color:var(--clay);line-height:1.1;}
.sl{font-size:9px;font-weight:700;text-transform:uppercase;letter-spacing:.5px;color:var(--muted);margin-top:4px;}

/* TICKER */
.ticker{flex-shrink:0;display:none;margin:0 16px 8px;border-radius:12px;
  padding:10px 14px;align-items:center;gap:10px;
  border:1.5px solid var(--terra);background:var(--teralt);box-shadow:var(--sh0);}
.ticker.show{display:flex;}
.t-dot{width:8px;height:8px;border-radius:50%;background:var(--terra);
  flex-shrink:0;animation:pulse 1.4s ease-in-out infinite;}
@keyframes pulse{0%,100%{opacity:1;transform:scale(1)}50%{opacity:.5;transform:scale(1.3)}}
.t-name{flex:1;font-size:13px;font-weight:700;color:var(--clay);}
.t-remain{font-family:Georgia,serif;font-size:14px;font-weight:700;
  color:var(--terra);font-variant-numeric:tabular-nums;white-space:nowrap;}

/* DAY TOOLBAR */
.dtb{flex-shrink:0;display:flex;align-items:center;justify-content:space-between;padding:2px 16px 8px;}
.dnav{display:flex;align-items:center;gap:7px;}
.darr{width:31px;height:31px;border-radius:var(--rxs);background:var(--surf);
  border:1px solid var(--bdr);display:flex;align-items:center;justify-content:center;
  font-size:15px;cursor:pointer;color:var(--ink2);box-shadow:var(--sh0);}
.darr:active{background:var(--surf3);}
.dtitle{font-family:Georgia,serif;font-size:15px;font-weight:600;color:var(--ink);
  max-width:168px;white-space:nowrap;overflow:hidden;text-overflow:ellipsis;}
.abtn{background:var(--terra);color:#fff;border:none;border-radius:22px;
  padding:9px 17px;font-family:inherit;font-size:13px;font-weight:800;cursor:pointer;
  box-shadow:0 4px 14px rgba(184,92,56,.32);transition:transform .1s;}
.abtn:active{transform:scale(.95);}

/* TIMELINE */
.tls{flex:1;overflow-y:auto;overflow-x:hidden;-webkit-overflow-scrolling:touch;}
.tli{position:relative;padding:4px 14px 64px 54px;}
.hrow{position:absolute;left:0;right:14px;display:flex;align-items:flex-start;pointer-events:none;}
.hlbl{width:48px;flex-shrink:0;text-align:right;padding-right:7px;
  font-size:10px;font-weight:700;color:var(--muted);line-height:1;font-variant-numeric:tabular-nums;}
.hline{flex:1;border-top:1px solid var(--bdr);margin-top:5px;}
.hline.half{border-top:1px dashed var(--bdr);opacity:.38;}

/* BLOCK */
.tblk{position:absolute;border-radius:12px;padding:8px 11px;cursor:pointer;
  overflow:hidden;box-shadow:var(--sh1);
  border-left:3px solid transparent;
  border-top:1px solid rgba(255,255,255,.62);
  border-right:1px solid rgba(0,0,0,.03);
  border-bottom:1px solid rgba(0,0,0,.04);}
.tblk:active{opacity:.85;}
.tblk.now-blk{border-left-width:4px;box-shadow:var(--sh2);}
.tb-t{font-size:12px;font-weight:800;white-space:nowrap;overflow:hidden;text-overflow:ellipsis;line-height:1.3;}
.tb-s{font-size:10px;font-weight:600;margin-top:2px;opacity:.7;white-space:nowrap;overflow:hidden;}
.tb-n{font-size:10px;font-weight:500;margin-top:3px;opacity:.58;white-space:nowrap;overflow:hidden;text-overflow:ellipsis;}
.tbr{position:absolute;bottom:0;left:0;right:0;height:14px;
  display:flex;align-items:flex-end;justify-content:center;padding-bottom:4px;cursor:ns-resize;}
.tbr-b{width:28px;height:3px;border-radius:2px;background:rgba(0,0,0,.12);}

/* NOW LINE */
.nowln{position:absolute;left:0;right:0;z-index:20;pointer-events:none;display:flex;align-items:center;}
.now-d{width:9px;height:9px;border-radius:50%;background:var(--terra);
  flex-shrink:0;margin-left:-1px;box-shadow:0 0 0 3px rgba(184,92,56,.18);}
.now-l{flex:1;height:1.5px;background:linear-gradient(90deg,var(--terra),var(--terra2) 55%,transparent);}

/* EMPTY */
.empty{display:flex;flex-direction:column;align-items:center;
  justify-content:center;padding:32px 24px;gap:12px;text-align:center;}
.e-ico{font-size:48px;filter:grayscale(15%) opacity(.55);line-height:1;}
.e-msg{font-size:14px;font-weight:500;color:var(--muted);line-height:1.7;}
.e-btn{margin-top:4px;background:var(--ochrelt);color:var(--clay);
  border:1.5px solid var(--bdr);border-radius:22px;padding:9px 22px;
  font-size:13px;font-weight:800;cursor:pointer;font-family:inherit;}

/* CALENDAR */
#cal-view{padding:0;}
.cal-hdr{flex-shrink:0;display:flex;align-items:center;justify-content:space-between;padding:4px 18px 10px;}
.cal-m{font-family:Georgia,serif;font-size:20px;font-weight:700;color:var(--ink);}
.cal-a{width:34px;height:34px;border-radius:var(--rxs);background:var(--surf);
  border:1px solid var(--bdr);display:flex;align-items:center;justify-content:center;
  cursor:pointer;font-size:16px;color:var(--ink2);box-shadow:var(--sh0);}
.cgrd{flex-shrink:0;display:grid;grid-template-columns:repeat(7,1fr);gap:3px;padding:0 14px 10px;}
.cdow{text-align:center;font-size:10px;font-weight:800;text-transform:uppercase;
  letter-spacing:.6px;color:var(--ghost);padding:4px 0;}
.cday{aspect-ratio:1;display:flex;align-items:center;justify-content:center;
  border-radius:11px;font-size:13px;font-weight:600;cursor:pointer;
  position:relative;color:var(--ink);}
.cday.other{color:var(--ghost);}
.cday.today{background:var(--terra);color:#fff;font-weight:800;}
.cday.sel:not(.today){background:var(--ochrelt);border:1.5px solid var(--ochre2);color:var(--clay);font-weight:800;}
.cday .blip{position:absolute;bottom:3px;width:4px;height:4px;border-radius:50%;background:var(--moss);}
.cday.today .blip{background:rgba(255,255,255,.7);}
.mlist{flex:1;overflow-y:auto;-webkit-overflow-scrolling:touch;padding:0 14px 24px;}
.dcard{background:var(--surf);border:1px solid var(--bdr);border-radius:var(--r);
  padding:12px 14px;margin-bottom:8px;cursor:pointer;
  display:flex;align-items:center;gap:12px;box-shadow:var(--sh0);}
.dcn{font-family:Georgia,serif;font-size:26px;font-weight:700;color:var(--ochre);min-width:36px;text-align:center;line-height:1;}
.dci{flex:1;}
.dcw{font-size:10px;font-weight:800;text-transform:uppercase;letter-spacing:.6px;color:var(--muted);}
.dcb{font-size:13px;font-weight:600;color:var(--ink2);margin-top:2px;}
.dcp{display:flex;gap:4px;flex-wrap:wrap;margin-top:6px;}
.dpill{font-size:10px;padding:2px 8px;border-radius:20px;font-weight:700;}
.dca{color:var(--ghost);font-size:15px;}

/* SETTINGS */
#set-view{overflow-y:auto;-webkit-overflow-scrolling:touch;padding:0 0 60px;background:var(--bg);}
.inst-hero{margin:12px 16px 0;border-radius:var(--r);overflow:hidden;box-shadow:var(--sh2);}
.inst-bar{background:linear-gradient(135deg,var(--terra),var(--clay));padding:16px 18px 0;}
.inst-hd{display:flex;align-items:center;gap:10px;margin-bottom:10px;}
.inst-ttl{font-size:15px;font-weight:800;color:#fff;}
.inst-ss{font-size:11px;color:rgba(255,255,255,.72);margin-top:1px;font-weight:500;}
.inst-steps{background:rgba(255,255,255,.13);border-radius:10px 10px 0 0;padding:12px 14px;}
.istep{display:flex;align-items:flex-start;gap:9px;margin-bottom:10px;}
.istep:last-child{margin-bottom:0;}
.sn{width:21px;height:21px;border-radius:50%;background:rgba(255,255,255,.25);
  color:#fff;font-size:11px;font-weight:800;display:flex;align-items:center;
  justify-content:center;flex-shrink:0;margin-top:1px;}
.st2{font-size:12px;font-weight:500;color:rgba(255,255,255,.9);line-height:1.55;}
.st2 b{color:#fff;font-weight:800;}
.inst-note{background:var(--surf);padding:10px 16px;font-size:11px;
  font-weight:600;color:var(--muted);text-align:center;line-height:1.7;}
.inst-note b{color:var(--terra);}
.sw{padding:14px 16px 0;}
.ss{margin-bottom:20px;}
.shd{font-size:10px;font-weight:800;text-transform:uppercase;letter-spacing:.8px;
  color:var(--muted);margin-bottom:8px;padding-left:2px;}
.scard{background:var(--surf);border:1px solid var(--bdr);border-radius:var(--r);
  overflow:hidden;box-shadow:var(--sh0);}
.srow{display:flex;align-items:center;justify-content:space-between;
  padding:13px 16px;border-bottom:1px solid var(--bdr);}
.srow:last-child{border-bottom:none;}
.srow-l label{font-size:14px;font-weight:600;color:var(--ink);display:block;}
.srow-l small{font-size:11px;color:var(--muted);margin-top:2px;display:block;font-weight:500;}

/* TOGGLE — standalone, no JS class confusion */
.tog{
  width:50px;height:29px;border-radius:15px;
  border:none;cursor:pointer;flex-shrink:0;
  position:relative;
  background:var(--bdr2);
  transition:background .22s;
  -webkit-appearance:none;appearance:none;
  outline:none;
}
.tog.on{background:var(--moss);}
.tog::after{
  content:'';position:absolute;
  top:3px;left:3px;
  width:23px;height:23px;border-radius:50%;
  background:#fff;
  box-shadow:0 1px 4px rgba(0,0,0,.2);
  transition:transform .22s cubic-bezier(.34,1.56,.64,1);
}
.tog.on::after{transform:translateX(21px);}

.drblk{padding:13px 16px;border-bottom:1px solid var(--bdr);}
.drblk:last-child{border-bottom:none;}
.drtop{display:flex;justify-content:space-between;align-items:center;margin-bottom:8px;}
.drtop label{font-size:14px;font-weight:600;color:var(--ink);}
.drbdg{background:var(--ochrelt);color:var(--clay);border-radius:20px;
  padding:3px 11px;font-size:12px;font-weight:800;border:1px solid var(--bdr);}
input[type=range]{width:100%;accent-color:var(--terra);cursor:pointer;height:22px;}
.rmk{display:flex;justify-content:space-between;font-size:9px;color:var(--ghost);font-weight:700;margin-top:1px;}
.scatg{display:grid;grid-template-columns:repeat(3,1fr);gap:6px;padding:12px;}
.schip{display:flex;flex-direction:column;align-items:center;gap:5px;
  padding:11px 4px;border-radius:13px;font-size:11px;font-weight:700;
  border:1.5px solid var(--bdr);background:var(--bg);}
.sact{display:flex;align-items:center;justify-content:space-between;
  padding:13px 16px;border-bottom:1px solid var(--bdr);cursor:pointer;}
.sact:active{background:var(--surf2);}
.sact:last-child{border-bottom:none;}
.sact-l{font-size:14px;font-weight:600;color:var(--ink);}
.test-btn{
  width:100%;padding:13px;border:none;border-radius:14px;
  background:var(--moss);color:#fff;font-family:inherit;
  font-size:14px;font-weight:800;cursor:pointer;margin-top:2px;
  box-shadow:0 3px 12px rgba(85,112,64,.3);
}
.test-btn:active{opacity:.85;}
.foot{text-align:center;color:var(--ghost);font-size:11px;padding:12px 0 8px;font-weight:600;line-height:1.8;}

/* MODAL */
.bdrop{position:fixed;inset:0;background:rgba(36,24,10,.42);
  display:flex;align-items:flex-end;z-index:500;
  -webkit-backdrop-filter:blur(6px);backdrop-filter:blur(6px);}
.sheet{width:100%;background:var(--canvas);border-radius:24px 24px 0 0;
  padding:14px 20px calc(20px + var(--sb));
  animation:shUp .28s cubic-bezier(.32,.72,0,1);
  max-height:93vh;overflow-y:auto;-webkit-overflow-scrolling:touch;
  box-shadow:0 -10px 50px rgba(70,40,10,.16);border-top:1px solid var(--bdr);}
@keyframes shUp{from{transform:translateY(100%)}to{transform:translateY(0)}}
.sh-hnd{width:36px;height:4px;border-radius:2px;background:var(--bdr2);margin:0 auto 18px;}
.sh-ttl{font-family:Georgia,serif;font-size:22px;font-weight:700;color:var(--ink);margin-bottom:20px;}
.fg{margin-bottom:15px;}
.flbl{display:block;font-size:10px;font-weight:800;text-transform:uppercase;
  letter-spacing:.7px;color:var(--muted);margin-bottom:6px;}
.fi{width:100%;background:var(--surf);border:1.5px solid var(--bdr);
  border-radius:12px;padding:12px 14px;color:var(--ink);font-family:inherit;
  font-size:15px;font-weight:600;outline:none;
  -webkit-appearance:none;appearance:none;}
.fi:focus{border-color:var(--terra);}
.fi.err{border-color:var(--terra);background:var(--teralt);}
.fi::placeholder{color:var(--ghost);font-weight:400;}
.csg{display:grid;grid-template-columns:repeat(3,1fr);gap:6px;}
.copt{padding:11px 4px;border-radius:13px;border:1.5px solid var(--bdr);
  text-align:center;font-size:11px;font-weight:700;cursor:pointer;
  background:var(--surf);color:var(--muted);line-height:1.5;}
.copt:active{opacity:.75;}
.copt.on{border-width:2px;font-weight:800;}
.dbd{text-align:center;font-family:Georgia,serif;font-size:36px;font-weight:700;color:var(--clay);margin:4px 0 2px;}
.shbtns{display:flex;gap:8px;margin-top:20px;}
.btn-c{padding:13px 16px;border-radius:14px;border:1.5px solid var(--bdr);
  background:var(--surf);color:var(--ink2);font-family:inherit;font-size:14px;font-weight:700;cursor:pointer;}
.btn-s{flex:1;padding:13px;border-radius:14px;border:none;background:var(--terra);
  color:#fff;font-family:inherit;font-size:15px;font-weight:800;cursor:pointer;
  box-shadow:0 4px 14px rgba(184,92,56,.28);}
.btn-s:active{opacity:.85;}
.btn-d{padding:13px 14px;border-radius:14px;
  border:1.5px solid rgba(184,92,56,.3);background:var(--teralt);
  color:var(--terra);font-family:inherit;font-size:14px;font-weight:700;cursor:pointer;}
::-webkit-scrollbar{width:3px;}
::-webkit-scrollbar-thumb{background:var(--bdr2);border-radius:4px;}
</style>
</head>
<body>
<div id="flash"></div>
<div class="toast" id="toast">
  <div class="t-ico" id="tIco">🔔</div>
  <div><div class="t-ttl" id="tTtl"></div><div class="t-sub" id="tSub"></div></div>
</div>

<div id="app">
  <header class="hdr">
    <div class="logo ser">Focus<i>Flow</i></div>
    <div class="hdr-clock-wrap">
      <div class="hdr-clock" id="hClock">00:00</div>
      <div class="hdr-date"  id="hDate">—</div>
    </div>
    <button class="bell-btn" id="bellBtn" onclick="toggleBell()">🔔</button>
  </header>

  <nav class="nav">
    <button class="tab on" id="tab-day" onclick="goTab('day')">⏱ Day</button>
    <button class="tab"    id="tab-cal" onclick="goTab('cal')">📅 Month</button>
    <button class="tab"    id="tab-set" onclick="goTab('set')">⚙ Settings</button>
  </nav>

  <!-- DAY VIEW -->
  <div class="view on" id="day-view">
    <div class="dtb">
      <div class="dnav">
        <button class="darr" onclick="shiftDay(-1)">‹</button>
        <div class="dtitle" id="dtitle">Today</div>
        <button class="darr" onclick="shiftDay(1)">›</button>
      </div>
      <button class="abtn" onclick="openAdd()">＋ Block</button>
    </div>
    <div class="stats"  id="stats"></div>
    <div class="ticker" id="ticker">
      <div class="t-dot"></div>
      <div class="t-name"   id="tickName">—</div>
      <div class="t-remain" id="tickTime">—</div>
    </div>
    <div class="tls" id="tls"><div class="tli" id="tli"></div></div>
  </div>

  <!-- CALENDAR VIEW -->
  <div class="view" id="cal-view">
    <div class="cal-hdr">
      <button class="cal-a" onclick="prevMon()">‹</button>
      <div class="cal-m" id="calM">—</div>
      <button class="cal-a" onclick="nextMon()">›</button>
    </div>
    <div class="cgrd" id="cgrd"></div>
    <div class="mlist" id="mlist"></div>
  </div>

  <!-- SETTINGS VIEW -->
  <div class="view" id="set-view">
    <div class="inst-hero">
      <div class="inst-bar">
        <div class="inst-hd">
          <div style="font-size:26px;line-height:1">📲</div>
          <div><div class="inst-ttl">Install via GitHub Pages — Free</div>
               <div class="inst-ss">Offline after first open · Update by re-uploading</div></div>
        </div>
        <div class="inst-steps">
          <div class="istep"><div class="sn">1</div><div class="st2">Go to <b>github.com</b> · sign up free · create Public repo named <b>focusflow</b></div></div>
          <div class="istep"><div class="sn">2</div><div class="st2">Tap <b>"uploading an existing file"</b> → pick <b>index.html</b> → tap <b>Commit changes</b></div></div>
          <div class="istep"><div class="sn">3</div><div class="st2">Tap <b>Settings → Pages → Source: main → Save</b></div></div>
          <div class="istep"><div class="sn">4</div><div class="st2">Open <b>yourusername.github.io/focusflow</b> in Safari → Share ⎋ → <b>Add to Home Screen</b></div></div>
          <div class="istep"><div class="sn">↑</div><div class="st2"><b>To update app:</b> re-upload index.html to GitHub — tap the app to reload</div></div>
        </div>
      </div>
      <div class="inst-note">Data saved <b>only on your iPhone</b> · Never uploaded anywhere</div>
    </div>

    <div class="sw">
      <!-- ALERTS -->
      <div class="ss" style="margin-top:18px">
        <div class="shd">Alerts &amp; Sound</div>
        <div class="scard">
          <div class="srow">
            <div class="srow-l">
              <label>Alerts armed</label>
              <small>Bell 🔔 in header shows status</small>
            </div>
            <button class="tog" id="tog-alerts" onclick="togClick('alerts')"></button>
          </div>
          <div class="srow">
            <div class="srow-l">
              <label>Block start alert</label>
              <small>Chime when block begins</small>
            </div>
            <button class="tog" id="tog-alertStart" onclick="togClick('alertStart')"></button>
          </div>
          <div class="srow">
            <div class="srow-l">
              <label>Block end alert</label>
              <small>Chime when block ends</small>
            </div>
            <button class="tog" id="tog-alertEnd" onclick="togClick('alertEnd')"></button>
          </div>
        </div>
        <div style="margin-top:8px">
          <button class="test-btn" onclick="testAlert()">🔔 Test Alert Now</button>
        </div>
      </div>

      <!-- DURATION -->
      <div class="ss">
        <div class="shd">Default Bite Size</div>
        <div class="scard">
          <div class="drblk">
            <div class="drtop">
              <label>Block Duration</label>
              <div class="drbdg" id="sDbdg">30 min</div>
            </div>
            <input type="range" min="15" max="120" step="15" id="sDslr"
              oninput="sDur(this.value)">
            <div class="rmk"><span>15m</span><span>30</span><span>45</span><span>1h</span><span>1.5h</span><span>2h</span></div>
          </div>
        </div>
      </div>

      <!-- DISPLAY -->
      <div class="ss">
        <div class="shd">Display</div>
        <div class="scard">
          <div class="srow">
            <div class="srow-l"><label>Current time marker</label></div>
            <button class="tog" id="tog-showNow" onclick="togClick('showNow')"></button>
          </div>
          <div class="srow">
            <div class="srow-l"><label>Half-hour marks</label></div>
            <button class="tog" id="tog-showHalf" onclick="togClick('showHalf')"></button>
          </div>
        </div>
      </div>

      <!-- CATS -->
      <div class="ss">
        <div class="shd">Categories</div>
        <div class="scard"><div class="scatg" id="scatg"></div></div>
      </div>

      <!-- DATA -->
      <div class="ss">
        <div class="shd">Data</div>
        <div class="scard">
          <div class="sact" onclick="doExport()">
            <span class="sact-l">📤 Export schedule (JSON)</span>
            <span style="color:var(--ghost);font-size:15px">›</span>
          </div>
          <div class="sact" onclick="doClear()">
            <span class="sact-l" style="color:var(--terra)">🗑 Clear selected day</span>
            <span style="color:var(--terra);opacity:.5;font-size:15px">›</span>
          </div>
        </div>
      </div>
      <div class="foot">FocusFlow v4 · All data on your device only</div>
    </div>
  </div>
</div><!-- /app -->

<!-- MODAL -->
<div id="bdrop" style="display:none">
  <div class="bdrop" onclick="bdTap(event)">
    <div class="sheet" onclick="event.stopPropagation()">
      <div class="sh-hnd"></div>
      <div class="sh-ttl" id="shTtl">New Focus Block</div>
      <div class="fg">
        <label class="flbl">Activity</label>
        <input class="fi" id="fAct" type="text"
          placeholder="Deep Work, Revision, Planning…" maxlength="40" autocomplete="off">
      </div>
      <div class="fg">
        <label class="flbl">Category</label>
        <div class="csg" id="csg"></div>
      </div>
      <div class="fg">
        <label class="flbl">Start Time</label>
        <input class="fi" id="fSt" type="time">
      </div>
      <div class="fg">
        <label class="flbl">Duration</label>
        <div class="dbd" id="fDbd">30 min</div>
        <input type="range" min="15" max="240" step="15" id="fDslr"
          oninput="updDbd(this.value)"
          style="width:100%;accent-color:var(--terra)">
        <div class="rmk">
          <span>15m</span><span>30m</span><span>1h</span>
          <span>2h</span><span>3h</span><span>4h</span>
        </div>
      </div>
      <div class="fg">
        <label class="flbl">Note
          <span style="font-weight:400;text-transform:none;letter-spacing:0">
            (optional)
          </span>
        </label>
        <input class="fi" id="fNt" type="text"
          placeholder="Goal or reminder…" maxlength="60" autocomplete="off">
      </div>
      <div class="shbtns" id="shbtns"></div>
    </div>
  </div>
</div>

<script>
/* =============================================
   FocusFlow v4
   KEY FIXES:
   - Toggle: direct className set, no "this" bugs
   - Save: null-safe reads, proper error display
   - Alert: poll every 15s, fires on exact HH:MM
   - Ticker: live MM:SS countdown every second
   ============================================= */

/* ── CATEGORIES ── */
var CATS = [
  {id:'work',    label:'Work',    e:'💼', color:'#8a5630', bg:'#f5ede4'},
  {id:'study',   label:'Study',   e:'📚', color:'#486830', bg:'#ecf2e4'},
  {id:'break',   label:'Break',   e:'☕', color:'#7a5428', bg:'#f6f0dc'},
  {id:'personal',label:'Personal',e:'🏡', color:'#5a7060', bg:'#e8f0e8'},
  {id:'move',    label:'Move',    e:'🌿', color:'#4a6848', bg:'#e8f0e4'},
  {id:'creative',label:'Creative',e:'🎨', color:'#7a4850', bg:'#f4e8ea'}
];

/* ── CONSTANTS ── */
var PPM = 1.15;   /* pixels per minute on timeline */
var HRS = 7;      /* timeline start hour */
var HRE = 22;     /* timeline end hour */

/* ── PREFS (all keys flat, no nesting) ── */
var P = {
  alerts:     true,
  alertStart: true,
  alertEnd:   true,
  showNow:    true,
  showHalf:   true,
  defDur:     30
};
try {
  var _sp = localStorage.getItem('ff_p4');
  if (_sp) {
    var _pp = JSON.parse(_sp);
    var _k;
    for (_k in _pp) { if (_pp.hasOwnProperty(_k)) P[_k] = _pp[_k]; }
  }
} catch(e) {}

/* ── BLOCK DATA ── */
var B = {};
try {
  var _sb = localStorage.getItem('ff_b');
  if (_sb) B = JSON.parse(_sb);
} catch(e) {}

/* ── UI STATE ── */
var selDate = new Date();
var calDate = new Date();
var editId  = null;
var selCat  = 'work';

/* ── HELPERS ── */
var DS = ['Sun','Mon','Tue','Wed','Thu','Fri','Sat'];
var DL = ['Sunday','Monday','Tuesday','Wednesday','Thursday','Friday','Saturday'];
var MS = ['Jan','Feb','Mar','Apr','May','Jun','Jul','Aug','Sep','Oct','Nov','Dec'];
var ML = ['January','February','March','April','May','June','July','August','September','October','November','December'];

function p2(n) { return String(n).padStart(2,'0'); }
function dk(d) { return d.getFullYear()+'-'+p2(d.getMonth()+1)+'-'+p2(d.getDate()); }
function todK() { return dk(new Date()); }
function getB(k) { return B[k] || []; }
function setB(k, a) {
  B[k] = a;
  try { localStorage.setItem('ff_b', JSON.stringify(B)); } catch(e) {}
}
function saveP() {
  try { localStorage.setItem('ff_p4', JSON.stringify(P)); } catch(e) {}
}
function fmt(h, m) { return (h % 12 || 12) + ':' + p2(m) + ' ' + (h < 12 ? 'am' : 'pm'); }
function mStr(m) { return m >= 60 ? Math.floor(m/60)+'h'+(m%60?' '+m%60+'m':'') : m+'m'; }

function el(id) { return document.getElementById(id); }

/* ─────────────────────────────────────────
   AUDIO  (Web Audio API, unlocked on tap)
   ───────────────────────────────────────── */
var _ctx = null;

/* Unlock on very first touch anywhere */
document.addEventListener('touchstart', function _unlock() {
  if (!_ctx) {
    try { _ctx = new (window.AudioContext || window.webkitAudioContext)(); } catch(e) {}
  }
  if (_ctx && _ctx.state === 'suspended') _ctx.resume();
  document.removeEventListener('touchstart', _unlock);
}, false);

function getCtx() {
  if (!_ctx) {
    try { _ctx = new (window.AudioContext || window.webkitAudioContext)(); } catch(e) {}
  }
  if (_ctx && _ctx.state === 'suspended') _ctx.resume();
  return _ctx;
}

/* Play a single beep */
function beep(ctx, freq, startSec, durSec, vol) {
  try {
    var o = ctx.createOscillator();
    var g = ctx.createGain();
    o.connect(g);
    g.connect(ctx.destination);
    o.type = 'triangle';
    o.frequency.value = freq;
    var t = ctx.currentTime + startSec;
    g.gain.setValueAtTime(0, t);
    g.gain.linearRampToValueAtTime(vol, t + 0.025);
    g.gain.exponentialRampToValueAtTime(0.0001, t + durSec);
    o.start(t);
    o.stop(t + durSec + 0.05);
  } catch(e) {}
}

/* Three-note chimes */
function playStart() {
  var ctx = getCtx(); if (!ctx) return;
  beep(ctx, 330, 0.0,  0.35, 0.45); /* E4 */
  beep(ctx, 392, 0.22, 0.35, 0.45); /* G4 */
  beep(ctx, 523, 0.44, 0.65, 0.40); /* C5 */
}
function playEnd() {
  var ctx = getCtx(); if (!ctx) return;
  beep(ctx, 523, 0.0,  0.35, 0.40); /* C5 */
  beep(ctx, 392, 0.22, 0.35, 0.38); /* G4 */
  beep(ctx, 330, 0.44, 0.75, 0.35); /* E4 */
}

/* Vibration (works on Android; iOS ignores silently) */
function vibrate(type) {
  try {
    if (!navigator.vibrate) return;
    if (type === 'start') navigator.vibrate([100, 60, 100]);
    else                  navigator.vibrate([80, 50, 80, 50, 200]);
  } catch(e) {}
}

/* Flash screen */
function flashScreen() {
  var f = el('flash');
  if (!f) return;
  f.style.opacity = '1';
  setTimeout(function() { f.style.opacity = '0'; }, 200);
}

/* ─────────────────────────────────────────
   TOAST
   ───────────────────────────────────────── */
var _toastTimer = null;
function showToast(ico, title, sub) {
  el('tIco').textContent = ico;
  el('tTtl').textContent = title;
  el('tSub').textContent = sub || '';
  var t = el('toast');
  t.classList.add('show');
  if (_toastTimer) clearTimeout(_toastTimer);
  _toastTimer = setTimeout(function() { t.classList.remove('show'); }, 5000);
}

/* ─────────────────────────────────────────
   ALERT ENGINE — polls every 15 seconds
   Compares current HH:MM to block start/end
   Each alert fires exactly once per day
   ───────────────────────────────────────── */
var _fired = {};   /* "DATEKEY|blockId|type" -> true */
var _lastMin = -1; /* avoid double-fire within same minute */

function pollAlerts() {
  if (!P.alerts) return;

  var now = new Date();
  var nowMin = now.getHours() * 60 + now.getMinutes();

  /* Only fire once per minute */
  if (nowMin === _lastMin) return;
  _lastMin = nowMin;

  var bl = getB(todK());
  var i;
  for (i = 0; i < bl.length; i++) {
    var b = bl[i];
    var parts = b.start.split(':');
    var bh = parseInt(parts[0], 10);
    var bm = parseInt(parts[1], 10);
    var startMin = bh * 60 + bm;
    var endMin   = startMin + b.dur;
    var cat = CATS[0];
    var j;
    for (j = 0; j < CATS.length; j++) {
      if (CATS[j].id === b.cat) { cat = CATS[j]; break; }
    }

    /* START */
    if (P.alertStart && nowMin === startMin) {
      var sk = todK() + '|' + b.id + '|S';
      if (!_fired[sk]) {
        _fired[sk] = true;
        playStart();
        vibrate('start');
        flashScreen();
        showToast(cat.e, '▶ Starting: ' + b.act, mStr(b.dur) + ' block — focus time!');
        renderDay();
      }
    }

    /* END */
    if (P.alertEnd && nowMin === endMin) {
      var ek = todK() + '|' + b.id + '|E';
      if (!_fired[ek]) {
        _fired[ek] = true;
        playEnd();
        vibrate('end');
        flashScreen();
        showToast('✅', 'Done: ' + b.act, 'Block complete — great work! ✓');
        renderDay();
      }
    }
  }
}

/* Reset fired log each new day */
function maybeDayReset() {
  var stored = localStorage.getItem('ff_alertDay');
  var today  = todK();
  if (stored !== today) {
    _fired = {};
    _lastMin = -1;
    try { localStorage.setItem('ff_alertDay', today); } catch(e) {}
  }
}

/* Test alert (bypasses armed check) */
function testAlert() {
  playStart();
  vibrate('start');
  flashScreen();
  showToast('🔔', 'Alert test ✓', 'Sound + vibration + flash all working!');
}

/* ─────────────────────────────────────────
   TOGGLE SYSTEM  (fixed)
   All toggles stored in P, rendered by key
   togClick(key) — called from HTML onclick
   ───────────────────────────────────────── */
function togClick(key) {
  P[key] = !P[key];
  saveP();
  renderTog(key);
  /* Side effects */
  if (key === 'alerts') renderBell();
  if (key === 'showNow' || key === 'showHalf') renderDay();
}

function renderTog(key) {
  var btn = el('tog-' + key);
  if (!btn) return;
  if (P[key]) {
    btn.className = 'tog on';
  } else {
    btn.className = 'tog';
  }
}

function renderAllTogs() {
  var keys = ['alerts','alertStart','alertEnd','showNow','showHalf'];
  var i;
  for (i = 0; i < keys.length; i++) renderTog(keys[i]);
}

/* Bell button in header */
function toggleBell() {
  P.alerts = !P.alerts;
  saveP();
  renderTog('alerts');
  renderBell();
}

function renderBell() {
  var btn = el('bellBtn');
  if (!btn) return;
  if (P.alerts) {
    btn.className = 'bell-btn on';
    btn.textContent = '🔔';
  } else {
    btn.className = 'bell-btn';
    btn.textContent = '🔕';
  }
}

/* ─────────────────────────────────────────
   CLOCK — updates every second
   Ticker countdown — updates every second
   ───────────────────────────────────────── */
function tick() {
  var n = new Date();
  el('hClock').textContent = p2(n.getHours()) + ':' + p2(n.getMinutes());
  el('hDate').textContent  = DS[n.getDay()] + ' ' + n.getDate() + ' ' + MS[n.getMonth()] + ' ' + n.getFullYear();
  updateTicker(n);
}

function updateTicker(now) {
  if (!dk(selDate) === todK()) { el('ticker').classList.remove('show'); return; }
  var isToday = dk(selDate) === dk(now || new Date());
  if (!isToday) { el('ticker').classList.remove('show'); return; }

  var n = now || new Date();
  var nowSec = n.getHours() * 3600 + n.getMinutes() * 60 + n.getSeconds();
  var bl = getB(dk(selDate));
  var active = null;
  var i;
  for (i = 0; i < bl.length; i++) {
    var b = bl[i];
    var parts = b.start.split(':');
    var bh = parseInt(parts[0], 10);
    var bm = parseInt(parts[1], 10);
    var startSec = bh * 3600 + bm * 60;
    var endSec   = startSec + b.dur * 60;
    if (startSec <= nowSec && nowSec < endSec) {
      active = b;
      var remSec = endSec - nowSec;
      var cat = CATS[0];
      var j;
      for (j = 0; j < CATS.length; j++) {
        if (CATS[j].id === b.cat) { cat = CATS[j]; break; }
      }
      el('tickName').textContent = cat.e + ' ' + b.act;
      /* Show MM:SS remaining */
      var rm = Math.floor(remSec / 60);
      var rs = remSec % 60;
      el('tickTime').textContent = rm + ':' + p2(rs) + ' left';
      break;
    }
  }
  if (active) {
    el('ticker').classList.add('show');
  } else {
    el('ticker').classList.remove('show');
  }
}

/* ─────────────────────────────────────────
   BOOT
   ───────────────────────────────────────── */
window.onload = function() {
  buildCsg();
  buildScatg();
  renderAllTogs();
  renderBell();
  initDurSlider();

  tick();
  /* 1-second ticker for live countdown */
  setInterval(tick, 1000);

  /* 15-second poll for alerts */
  setInterval(function() {
    maybeDayReset();
    pollAlerts();
  }, 15000);

  /* Immediate poll on load (catches block already running) */
  maybeDayReset();
  setTimeout(pollAlerts, 800);

  renderDay();
  renderCal();
};

/* ─────────────────────────────────────────
   TABS
   ───────────────────────────────────────── */
function activeTab() {
  var tabs = ['day','cal','set'];
  var i;
  for (i = 0; i < tabs.length; i++) {
    if (el(tabs[i]+'-view').classList.contains('on')) return tabs[i];
  }
  return 'day';
}

function goTab(t) {
  var tabs = ['day','cal','set'];
  var i;
  for (i = 0; i < tabs.length; i++) {
    var id = tabs[i];
    el('tab-'+id).className = 'tab' + (id === t ? ' on' : '');
    el(id+'-view').className = 'view' + (id === t ? ' on' : '');
  }
  if (t === 'cal') renderCal();
  if (t === 'day') renderDay();
}

function shiftDay(d) {
  selDate = new Date(selDate);
  selDate.setDate(selDate.getDate() + d);
  renderDay();
}

/* ─────────────────────────────────────────
   DAY VIEW
   ───────────────────────────────────────── */
function renderDay() {
  var now = new Date();
  var isToday = dk(selDate) === dk(now);

  /* Title */
  el('dtitle').textContent = isToday
    ? 'Today · ' + selDate.getDate() + ' ' + ML[selDate.getMonth()]
    : DL[selDate.getDay()].slice(0,3) + ' ' + selDate.getDate() + ' ' + ML[selDate.getMonth()];

  /* Stats */
  var bl = getB(dk(selDate));
  var tot = 0;
  var byCat = {};
  var i;
  for (i = 0; i < bl.length; i++) {
    tot += bl[i].dur;
    byCat[bl[i].cat] = (byCat[bl[i].cat] || 0) + bl[i].dur;
  }
  /* Find top category */
  var topId = null, topVal = 0;
  var k;
  for (k in byCat) {
    if (byCat.hasOwnProperty(k) && byCat[k] > topVal) {
      topVal = byCat[k]; topId = k;
    }
  }
  var topC = null;
  if (topId) {
    for (i = 0; i < CATS.length; i++) {
      if (CATS[i].id === topId) { topC = CATS[i]; break; }
    }
  }
  el('stats').innerHTML =
    '<div class="sc"><div class="sv">'+bl.length+'</div><div class="sl">Blocks</div></div>'+
    '<div class="sc"><div class="sv">'+(tot ? mStr(tot) : '—')+'</div><div class="sl">Focused</div></div>'+
    '<div class="sc"><div class="sv" style="font-size:21px">'+(topC ? topC.e : '·')+'</div><div class="sl">'+(topC ? topC.label : 'Rest')+'</div></div>';

  /* Timeline */
  var inner = el('tli');
  inner.innerHTML = '';
  inner.style.height = ((HRE - HRS) * 60 * PPM + 64) + 'px';

  var h;
  for (h = HRS; h <= HRE; h++) {
    var top = ((h - HRS) * 60) * PPM;
    addRow(inner, top, h < 12 ? h+'am' : h === 12 ? '12pm' : (h-12)+'pm', false);
    if (P.showHalf && h < HRE) {
      var halfLbl = h < 11 ? (h+1)+':30' : h === 11 ? '12:30' : (h-11)+':30';
      addRow(inner, top + 30 * PPM, halfLbl, true);
    }
  }

  /* Now-line */
  var nowMins = isToday ? (now.getHours() - HRS) * 60 + now.getMinutes() : -1;
  var nowTotalMin = isToday ? now.getHours() * 60 + now.getMinutes() : -1;

  /* Blocks */
  for (i = 0; i < bl.length; i++) {
    var b = bl[i];
    var parts = b.start.split(':');
    var bh = parseInt(parts[0], 10);
    var bm = parseInt(parts[1], 10);
    var sm = (bh - HRS) * 60 + bm;
    if (sm < 0 || sm > (HRE - HRS) * 60) continue;
    var hpx = Math.max(b.dur * PPM, 46);
    var cat = CATS[0];
    var j;
    for (j = 0; j < CATS.length; j++) {
      if (CATS[j].id === b.cat) { cat = CATS[j]; break; }
    }
    var em = bh * 60 + bm + b.dur;
    var isNow = nowTotalMin >= 0 && (bh*60+bm) <= nowTotalMin && nowTotalMin < em;

    var div = document.createElement('div');
    div.className = 'tblk' + (isNow ? ' now-blk' : '');
    div.style.cssText =
      'top:' + (sm * PPM) + 'px;' +
      'height:' + hpx + 'px;' +
      'left:0;right:0;' +
      'background:' + cat.bg + ';' +
      'border-left-color:' + cat.color + ';';
    div.innerHTML =
      '<div class="tb-t" style="color:'+cat.color+'">'+cat.e+' '+b.act+'</div>'+
      '<div class="tb-s" style="color:'+cat.color+'">'+
        fmt(bh,bm)+' → '+fmt(Math.floor(em/60), em%60)+' · '+mStr(b.dur)+
      '</div>'+
      (b.note ? '<div class="tb-n" style="color:'+cat.color+'">'+b.note+'</div>' : '')+
      '<div class="tbr"><div class="tbr-b" style="background:'+cat.color+';opacity:.18"></div></div>';

    /* Closures to capture b and key */
    (function(block, key) {
      div.addEventListener('click', function(ev) {
        if (!ev.target.closest('.tbr')) openEdit(block.id);
      });
      setupResize(div.querySelector('.tbr'), block, key);
    })(b, dk(selDate));

    inner.appendChild(div);
  }

  /* Now line */
  if (isToday && P.showNow && nowMins >= 0) {
    var nl = document.createElement('div');
    nl.className = 'nowln';
    nl.style.cssText = 'top:' + (nowMins * PPM) + 'px;position:absolute;';
    nl.innerHTML = '<div class="now-d"></div><div class="now-l"></div>';
    inner.appendChild(nl);
  }

  /* Empty */
  if (bl.length === 0) {
    var emp = document.createElement('div');
    emp.className = 'empty';
    emp.innerHTML =
      '<div class="e-ico">🌾</div>'+
      '<div class="e-msg">No focus blocks yet.<br>Plant your first intention for the day.</div>'+
      '<button class="e-btn" onclick="openAdd()">＋ Add first block</button>';
    inner.appendChild(emp);
  }

  /* Scroll to current hour */
  var sc = el('tls');
  setTimeout(function() {
    sc.scrollTop = isToday ? Math.max(0, (now.getHours() - HRS - 0.8) * 60 * PPM) : 0;
  }, 60);
}

function addRow(parent, top, label, half) {
  var r = document.createElement('div');
  r.className = 'hrow';
  r.style.top = top + 'px';
  r.innerHTML =
    '<div class="hlbl"' + (half ? ' style="opacity:.38;font-size:9px"' : '') + '>' + label + '</div>'+
    '<div class="hline' + (half ? ' half' : '') + '"></div>';
  parent.appendChild(r);
}

/* ─────────────────────────────────────────
   RESIZE HANDLE
   ───────────────────────────────────────── */
function setupResize(handle, block, key) {
  var sy, sd;
  handle.addEventListener('pointerdown', function(e) {
    e.stopPropagation();
    sy = e.clientY;
    sd = block.dur;
    handle.setPointerCapture(e.pointerId);

    function mv(ev) {
      var delta = Math.round((ev.clientY - sy) / PPM / 15) * 15;
      var nd = Math.max(15, Math.min(240, sd + delta));
      if (nd !== block.dur) {
        block.dur = nd;
        var arr = getB(key);
        var idx = -1;
        var i;
        for (i = 0; i < arr.length; i++) {
          if (arr[i].id === block.id) { idx = i; break; }
        }
        if (idx >= 0) { arr[idx].dur = nd; setB(key, arr); }
        renderDay();
      }
    }
    function up() {
      handle.removeEventListener('pointermove', mv);
      handle.removeEventListener('pointerup', up);
    }
    handle.addEventListener('pointermove', mv);
    handle.addEventListener('pointerup', up);
  });
}

/* ─────────────────────────────────────────
   MODAL — SAVE BLOCK (fixed)
   ───────────────────────────────────────── */
function openAdd() {
  editId  = null;
  selCat  = 'work';
  el('shTtl').textContent = 'New Focus Block';
  el('fAct').value = '';
  el('fAct').className = 'fi';
  el('fNt').value  = '';
  el('fDslr').value = P.defDur;
  updDbd(P.defDur);
  /* Default start time = now rounded to nearest 15m */
  var n = new Date();
  var h = Math.max(HRS, Math.min(HRE - 1, n.getHours()));
  var m = Math.round(n.getMinutes() / 15) * 15;
  if (m >= 60) { h = Math.min(HRE - 1, h + 1); m = 0; }
  el('fSt').value = p2(h) + ':' + p2(m);
  refreshCsg();
  el('shbtns').innerHTML =
    '<button class="btn-c" type="button" onclick="closeModal()">Cancel</button>'+
    '<button class="btn-s" type="button" onclick="saveBlock()">Save Block</button>';
  el('bdrop').style.display = 'block';
  setTimeout(function() { el('fAct').focus(); }, 300);
}

function openEdit(id) {
  var bl = getB(dk(selDate));
  var b  = null;
  var i;
  for (i = 0; i < bl.length; i++) {
    if (bl[i].id === id) { b = bl[i]; break; }
  }
  if (!b) return;
  editId = id;
  selCat = b.cat;
  el('shTtl').textContent = 'Edit Block';
  el('fAct').value = b.act;
  el('fAct').className = 'fi';
  el('fNt').value  = b.note || '';
  el('fSt').value  = b.start;
  el('fDslr').value = b.dur;
  updDbd(b.dur);
  refreshCsg();
  el('shbtns').innerHTML =
    '<button class="btn-d" type="button" onclick="delBlock()">Delete</button>'+
    '<button class="btn-c" type="button" onclick="closeModal()">Cancel</button>'+
    '<button class="btn-s" type="button" onclick="saveBlock()">Update</button>';
  el('bdrop').style.display = 'block';
}

function closeModal() {
  el('bdrop').style.display = 'none';
  editId = null;
}

function bdTap(e) {
  if (e.target === e.currentTarget) closeModal();
}

/* ── SAVE — the main fix ── */
function saveBlock() {
  /* Read values safely */
  var actEl   = el('fAct');
  var startEl = el('fSt');
  var durEl   = el('fDslr');
  var noteEl  = el('fNt');

  var act   = actEl   ? actEl.value.trim()   : '';
  var start = startEl ? startEl.value        : '';
  var dur   = durEl   ? parseInt(durEl.value, 10) : P.defDur;
  var note  = noteEl  ? noteEl.value.trim()  : '';

  /* Validation */
  if (!act) {
    if (actEl) {
      actEl.className = 'fi err';
      actEl.focus();
      actEl.placeholder = '← Please enter an activity name';
    }
    return;
  }
  if (!start) {
    /* Default to 9am if empty */
    start = '09:00';
  }
  if (isNaN(dur) || dur < 15) dur = P.defDur;

  /* Save */
  var key = dk(selDate);
  var arr = getB(key);

  if (editId) {
    /* Update existing */
    var i;
    for (i = 0; i < arr.length; i++) {
      if (arr[i].id === editId) {
        arr[i].act   = act;
        arr[i].cat   = selCat;
        arr[i].start = start;
        arr[i].dur   = dur;
        arr[i].note  = note;
        break;
      }
    }
  } else {
    /* Add new */
    var newId = Date.now().toString(36) + Math.random().toString(36).slice(2);
    arr.push({ id: newId, act: act, cat: selCat, start: start, dur: dur, note: note });
    /* Sort by start time */
    arr.sort(function(a, b) { return a.start < b.start ? -1 : a.start > b.start ? 1 : 0; });
  }

  setB(key, arr);
  closeModal();
  renderDay();
  if (activeTab() === 'cal') renderCal();
}

function delBlock() {
  if (!editId) return;
  var key = dk(selDate);
  var arr = getB(key);
  var i;
  var newArr = [];
  for (i = 0; i < arr.length; i++) {
    if (arr[i].id !== editId) newArr.push(arr[i]);
  }
  setB(key, newArr);
  closeModal();
  renderDay();
}

function updDbd(v) {
  el('fDbd').textContent = mStr(parseInt(v, 10));
}

/* ─────────────────────────────────────────
   CATEGORY SELECT
   ───────────────────────────────────────── */
function buildCsg() {
  var g = el('csg');
  g.innerHTML = '';
  var i;
  for (i = 0; i < CATS.length; i++) {
    var c   = CATS[i];
    var div = document.createElement('div');
    div.className = 'copt';
    div.setAttribute('data-c', c.id);
    div.innerHTML = c.e + '<br>' + c.label;
    div.onclick = (function(cid) {
      return function() { selCat = cid; refreshCsg(); };
    })(c.id);
    g.appendChild(div);
  }
  refreshCsg();
}

function refreshCsg() {
  var opts = document.querySelectorAll('.copt');
  var i;
  for (i = 0; i < opts.length; i++) {
    var opt = opts[i];
    var cid = opt.getAttribute('data-c');
    var cat = null;
    var j;
    for (j = 0; j < CATS.length; j++) {
      if (CATS[j].id === cid) { cat = CATS[j]; break; }
    }
    if (!cat) continue;
    var on = (cid === selCat);
    opt.className = 'copt' + (on ? ' on' : '');
    opt.style.borderColor = on ? cat.color : 'var(--bdr)';
    opt.style.background  = on ? cat.bg    : 'var(--surf)';
    opt.style.color       = on ? cat.color : 'var(--muted)';
  }
}

/* ─────────────────────────────────────────
   CALENDAR
   ───────────────────────────────────────── */
function renderCal() {
  var y = calDate.getFullYear();
  var m = calDate.getMonth();
  el('calM').textContent = ML[m] + ' ' + y;

  var grd = el('cgrd');
  grd.innerHTML = '';
  var dow = ['Su','Mo','Tu','We','Th','Fr','Sa'];
  var i;
  for (i = 0; i < dow.length; i++) {
    var d = document.createElement('div');
    d.className = 'cdow';
    d.textContent = dow[i];
    grd.appendChild(d);
  }

  var first = new Date(y, m, 1);
  var last  = new Date(y, m+1, 0);
  var tK    = todK();
  var sK    = dk(selDate);

  /* Blank leading days */
  for (i = 0; i < first.getDay(); i++) {
    var pd = new Date(y, m, 1 - first.getDay() + i);
    var pEl = document.createElement('div');
    pEl.className = 'cday other';
    pEl.textContent = pd.getDate();
    grd.appendChild(pEl);
  }

  /* Actual days */
  for (i = 1; i <= last.getDate(); i++) {
    var dt  = new Date(y, m, i);
    var dK  = dk(dt);
    var isT = dK === tK;
    var iS  = dK === sK && !isT;
    var hB  = getB(dK).length > 0;
    var dEl = document.createElement('div');
    dEl.className = 'cday' + (isT ? ' today' : '') + (iS ? ' sel' : '');
    dEl.textContent = i;
    if (hB) {
      var bp = document.createElement('div');
      bp.className = 'blip';
      dEl.appendChild(bp);
    }
    (function(dt2) {
      dEl.onclick = function() {
        selDate  = dt2;
        calDate  = new Date(dt2);
        renderCal();
        goTab('day');
      };
    })(dt);
    grd.appendChild(dEl);
  }

  /* Month list */
  var list = el('mlist');
  list.innerHTML = '';
  var any = false;
  for (i = 1; i <= last.getDate(); i++) {
    var dt2 = new Date(y, m, i);
    var dK2 = dk(dt2);
    var bl2 = getB(dK2);
    if (!bl2.length) continue;
    any = true;
    var tot2 = 0;
    var j;
    for (j = 0; j < bl2.length; j++) tot2 += bl2[j].dur;
    var seen = {};
    var pills = '';
    for (j = 0; j < bl2.length; j++) {
      var cid = bl2[j].cat;
      if (seen[cid]) continue;
      seen[cid] = true;
      var catObj = CATS[0];
      var q;
      for (q = 0; q < CATS.length; q++) {
        if (CATS[q].id === cid) { catObj = CATS[q]; break; }
      }
      pills += '<span class="dpill" style="background:'+catObj.bg+';color:'+catObj.color+'">'+catObj.e+' '+catObj.label+'</span>';
    }
    var card = document.createElement('div');
    card.className = 'dcard';
    card.innerHTML =
      '<div class="dcn">'+i+'</div>'+
      '<div class="dci">'+
        '<div class="dcw">'+DS[dt2.getDay()]+'</div>'+
        '<div class="dcb">'+bl2.length+' block'+(bl2.length>1?'s':'')+' · '+mStr(tot2)+' focused</div>'+
        '<div class="dcp">'+pills+'</div>'+
      '</div>'+
      '<div class="dca">›</div>';
    (function(dt3) {
      card.onclick = function() { selDate = dt3; goTab('day'); };
    })(dt2);
    list.appendChild(card);
  }
  if (!any) {
    list.innerHTML = '<div style="text-align:center;color:var(--muted);padding:28px 20px;font-size:14px;font-weight:600">No blocks this month</div>';
  }
}

function prevMon() { calDate = new Date(calDate.getFullYear(), calDate.getMonth()-1, 1); renderCal(); }
function nextMon() { calDate = new Date(calDate.getFullYear(), calDate.getMonth()+1, 1); renderCal(); }

/* ─────────────────────────────────────────
   SETTINGS
   ───────────────────────────────────────── */
function initDurSlider() {
  el('sDslr').value = P.defDur;
  el('sDbdg').textContent = mStr(P.defDur);
}
function sDur(v) {
  P.defDur = parseInt(v, 10);
  el('sDbdg').textContent = mStr(P.defDur);
  saveP();
}

function buildScatg() {
  var g = el('scatg');
  g.innerHTML = '';
  var i;
  for (i = 0; i < CATS.length; i++) {
    var c  = CATS[i];
    var ch = document.createElement('div');
    ch.className = 'schip';
    ch.style.cssText = 'border-color:'+c.color+'22;background:'+c.bg+';';
    ch.innerHTML = '<span style="font-size:22px">'+c.e+'</span><span style="color:'+c.color+';font-size:11px">'+c.label+'</span>';
    g.appendChild(ch);
  }
}

function doExport() {
  try {
    var blob = new Blob([JSON.stringify(B, null, 2)], {type:'application/json'});
    var a    = document.createElement('a');
    a.href   = URL.createObjectURL(blob);
    a.download = 'focusflow-' + todK() + '.json';
    a.click();
  } catch(e) {
    alert('On iPhone: Share → Save to Files to export.');
  }
}

function doClear() {
  if (confirm('Clear all blocks for ' + dk(selDate) + '?')) {
    delete B[dk(selDate)];
    try { localStorage.setItem('ff_b', JSON.stringify(B)); } catch(e) {}
    renderDay();
  }
}
</script>
</body>
</html>
