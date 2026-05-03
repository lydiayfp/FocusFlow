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
/* ═══════════════════════════════
   DESIGN TOKENS
═══════════════════════════════ */
:root {
  --bg:      #ede5d4;
  --bg2:     #e4dacb;
  --canvas:  #f8f2e6;
  --surf:    #fdfaf2;
  --surf2:   #f2e8d8;
  --surf3:   #e8dcc8;
  --bdr:     #d8ccb4;
  --bdr2:    #c8b898;
  --ink:     #28200e;
  --ink2:    #5a4828;
  --muted:   #9a8868;
  --ghost:   #c0aa8c;
  --terra:   #b85c38;
  --terra2:  #d4785a;
  --teralt:  #faeee8;
  --ochre:   #a87428;
  --ochre2:  #c89030;
  --ochrelt: #f8f0da;
  --moss:    #557040;
  --mosslt:  #ecf2e2;
  --clay:    #8a5630;
  --sh0: 0 1px 3px rgba(70,40,10,.07);
  --sh1: 0 3px 10px rgba(70,40,10,.10), 0 1px 4px rgba(70,40,10,.06);
  --sh2: 0 8px 28px rgba(70,40,10,.13), 0 2px 8px rgba(70,40,10,.07);
  --sh3: 0 16px 50px rgba(70,40,10,.16), 0 4px 16px rgba(70,40,10,.08);
  --r:   16px;
  --rsm: 11px;
  --rxs:  8px;
  --st: env(safe-area-inset-top,    0px);
  --sb: env(safe-area-inset-bottom, 0px);
}

/* ═══════════════════════════════
   RESET
═══════════════════════════════ */
*, *::before, *::after {
  box-sizing: border-box; margin: 0; padding: 0;
  -webkit-tap-highlight-color: transparent;
  -webkit-touch-callout: none;
}
html { height: 100%; touch-action: manipulation; }
body {
  height: 100%; overflow: hidden;
  background: var(--bg); color: var(--ink);
  font-family: -apple-system, 'Helvetica Neue', Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
}
button {
  -webkit-appearance: none; appearance: none;
  border: none; cursor: pointer; font-family: inherit;
  background: transparent; padding: 0;
}
input {
  -webkit-appearance: none; appearance: none;
  font-family: inherit;
}
.ser { font-family: Georgia, 'Book Antiqua', Palatino, serif; }

/* ═══════════════════════════════
   APP SHELL
═══════════════════════════════ */
#app {
  display: flex; flex-direction: column;
  height: 100vh; height: 100dvh;
  padding-top: var(--st);
}

/* ═══════════════════════════════
   FLASH OVERLAY
═══════════════════════════════ */
#flash {
  position: fixed; inset: 0; z-index: 9999;
  pointer-events: none; opacity: 0;
  background: rgba(184,92,56,.30);
  transition: opacity .12s;
}

/* ═══════════════════════════════
   TOAST
═══════════════════════════════ */
#toast {
  position: fixed;
  top: calc(var(--st) + 10px);
  left: 12px; right: 12px;
  background: #1a1410; color: #fff;
  border-radius: 16px; padding: 13px 16px;
  box-shadow: var(--sh3); z-index: 9000;
  display: flex; align-items: flex-start; gap: 10px;
  transform: translateY(-160px);
  transition: transform .35s cubic-bezier(.32,.72,0,1);
  pointer-events: none;
}
#toast.show { transform: translateY(0); }
.t-ico  { font-size: 22px; flex-shrink: 0; line-height: 1.2; }
.t-ttl  { font-size: 14px; font-weight: 800; line-height: 1.3; }
.t-sub  { font-size: 11px; opacity: .75; margin-top: 2px; font-weight: 500; }

/* ═══════════════════════════════
   HEADER
═══════════════════════════════ */
.hdr {
  flex-shrink: 0;
  padding: 11px 16px 9px;
  background: linear-gradient(180deg, var(--canvas), var(--bg));
  border-bottom: 1px solid var(--bdr);
  display: flex; align-items: center; justify-content: space-between; gap: 8px;
}
.logo { font-size: 20px; font-weight: 700; color: var(--clay); letter-spacing: -.3px; }
.logo i { font-style: italic; color: var(--terra); }
.hdr-mid { flex: 1; text-align: center; }
.hdr-clock {
  font-family: Georgia, serif;
  font-size: 22px; font-weight: 700;
  color: var(--ink); letter-spacing: 1px;
  font-variant-numeric: tabular-nums; line-height: 1;
}
.hdr-date { font-size: 9px; font-weight: 600; color: var(--muted); margin-top: 2px; letter-spacing: .3px; }

/* Bell button */
#bellBtn {
  width: 40px; height: 40px;
  border-radius: var(--rxs);
  background: var(--surf); border: 1.5px solid var(--bdr);
  font-size: 18px; line-height: 1;
  display: flex; align-items: center; justify-content: center;
  box-shadow: var(--sh0); transition: all .15s;
  flex-shrink: 0;
}
#bellBtn.on { background: var(--mosslt); border-color: var(--moss); }
#bellBtn:active { transform: scale(.9); }

/* ═══════════════════════════════
   NAV TABS
═══════════════════════════════ */
.nav {
  flex-shrink: 0;
  display: flex; gap: 5px;
  padding: 9px 16px 7px;
  background: var(--bg);
}
.tab {
  flex: 1; padding: 9px 4px;
  border-radius: var(--rsm);
  border: 1.5px solid transparent;
  background: transparent;
  font-size: 12px; font-weight: 700;
  color: var(--muted); text-align: center;
  transition: all .18s;
}
.tab.on {
  background: var(--surf); border-color: var(--bdr);
  color: var(--clay); box-shadow: var(--sh0);
}

/* ═══════════════════════════════
   VIEWS
═══════════════════════════════ */
.view { display: none; flex: 1; overflow: hidden; flex-direction: column; }
.view.on { display: flex; }

/* ═══════════════════════════════
   STATS STRIP
═══════════════════════════════ */
.stats { flex-shrink: 0; display: flex; gap: 7px; padding: 0 16px 8px; }
.sc {
  flex: 1; background: var(--surf); border: 1px solid var(--bdr);
  border-radius: 14px; padding: 10px 8px; text-align: center;
  box-shadow: var(--sh0);
}
.sv { font-family: Georgia, serif; font-size: 19px; font-weight: 700; color: var(--clay); line-height: 1.1; }
.sl { font-size: 9px; font-weight: 700; text-transform: uppercase; letter-spacing: .5px; color: var(--muted); margin-top: 4px; }

/* ═══════════════════════════════
   ACTIVE BLOCK TICKER
═══════════════════════════════ */
#ticker {
  flex-shrink: 0; display: none;
  margin: 0 16px 8px; border-radius: 12px;
  padding: 10px 14px; align-items: center; gap: 10px;
  border: 1.5px solid var(--terra);
  background: var(--teralt); box-shadow: var(--sh0);
}
#ticker.show { display: flex; }
.tdot {
  width: 8px; height: 8px; border-radius: 50%;
  background: var(--terra); flex-shrink: 0;
  animation: pulse 1.4s ease-in-out infinite;
}
@keyframes pulse { 0%,100%{opacity:1;transform:scale(1)} 50%{opacity:.5;transform:scale(1.3)} }
.tname { flex: 1; font-size: 13px; font-weight: 700; color: var(--clay); }
.tremain {
  font-family: Georgia, serif; font-size: 14px;
  font-weight: 700; color: var(--terra);
  font-variant-numeric: tabular-nums; white-space: nowrap;
}

/* ═══════════════════════════════
   DAY TOOLBAR
═══════════════════════════════ */
.dtb {
  flex-shrink: 0;
  display: flex; align-items: center; justify-content: space-between;
  padding: 2px 16px 8px;
}
.dnav { display: flex; align-items: center; gap: 7px; }
.darr {
  width: 31px; height: 31px; border-radius: var(--rxs);
  background: var(--surf); border: 1px solid var(--bdr);
  display: flex; align-items: center; justify-content: center;
  font-size: 15px; color: var(--ink2); box-shadow: var(--sh0);
}
.darr:active { background: var(--surf3); }
.dtitle {
  font-family: Georgia, serif; font-size: 15px;
  font-weight: 600; color: var(--ink);
  max-width: 168px; white-space: nowrap;
  overflow: hidden; text-overflow: ellipsis;
}
.abtn {
  background: var(--terra); color: #fff;
  border-radius: 22px; padding: 9px 17px;
  font-size: 13px; font-weight: 800;
  box-shadow: 0 4px 14px rgba(184,92,56,.32);
  transition: transform .1s;
}
.abtn:active { transform: scale(.95); }

/* ═══════════════════════════════
   TIMELINE
═══════════════════════════════ */
.tls { flex: 1; overflow-y: auto; overflow-x: hidden; -webkit-overflow-scrolling: touch; }
.tli { position: relative; padding: 4px 14px 64px 54px; }

.hrow {
  position: absolute; left: 0; right: 14px;
  display: flex; align-items: flex-start; pointer-events: none;
}
.hlbl {
  width: 48px; flex-shrink: 0; text-align: right;
  padding-right: 7px; font-size: 10px; font-weight: 700;
  color: var(--muted); line-height: 1;
  font-variant-numeric: tabular-nums;
}
.hline { flex: 1; border-top: 1px solid var(--bdr); margin-top: 5px; }
.hline.half { border-top-style: dashed; opacity: .38; }

/* Time Block */
.tblk {
  position: absolute; border-radius: 12px;
  padding: 8px 11px; cursor: pointer; overflow: hidden;
  box-shadow: var(--sh1);
  border-left: 3px solid transparent;
  border-top: 1px solid rgba(255,255,255,.62);
  border-right: 1px solid rgba(0,0,0,.03);
  border-bottom: 1px solid rgba(0,0,0,.04);
}
.tblk:active { opacity: .82; }
.tblk.nowblk { border-left-width: 4px; box-shadow: var(--sh2); }
.tb-t { font-size: 12px; font-weight: 800; white-space: nowrap; overflow: hidden; text-overflow: ellipsis; line-height: 1.3; }
.tb-s { font-size: 10px; font-weight: 600; margin-top: 2px; opacity: .7; white-space: nowrap; overflow: hidden; }
.tb-n { font-size: 10px; font-weight: 500; margin-top: 3px; opacity: .58; white-space: nowrap; overflow: hidden; text-overflow: ellipsis; }
.tbr {
  position: absolute; bottom: 0; left: 0; right: 0;
  height: 14px; display: flex; align-items: flex-end;
  justify-content: center; padding-bottom: 4px; cursor: ns-resize;
}
.tbr-b { width: 28px; height: 3px; border-radius: 2px; background: rgba(0,0,0,.12); }

/* Now Line */
.nowln { position: absolute; left: 0; right: 0; z-index: 20; pointer-events: none; display: flex; align-items: center; }
.now-d {
  width: 9px; height: 9px; border-radius: 50%;
  background: var(--terra); flex-shrink: 0;
  margin-left: -1px;
  box-shadow: 0 0 0 3px rgba(184,92,56,.18);
}
.now-l { flex: 1; height: 1.5px; background: linear-gradient(90deg, var(--terra), var(--terra2) 55%, transparent); }

/* Empty */
.empty {
  display: flex; flex-direction: column;
  align-items: center; justify-content: center;
  padding: 32px 24px; gap: 12px; text-align: center;
}
.e-ico { font-size: 48px; filter: grayscale(15%) opacity(.55); line-height: 1; }
.e-msg { font-size: 14px; font-weight: 500; color: var(--muted); line-height: 1.7; }
.e-btn {
  margin-top: 4px; background: var(--ochrelt); color: var(--clay);
  border: 1.5px solid var(--bdr); border-radius: 22px;
  padding: 9px 22px; font-size: 13px; font-weight: 800;
}

/* ═══════════════════════════════
   CALENDAR
═══════════════════════════════ */
#cal-view { padding: 0; }
.cal-hdr {
  flex-shrink: 0; display: flex; align-items: center;
  justify-content: space-between; padding: 4px 18px 10px;
}
.cal-m { font-family: Georgia, serif; font-size: 20px; font-weight: 700; color: var(--ink); }
.cal-a {
  width: 34px; height: 34px; border-radius: var(--rxs);
  background: var(--surf); border: 1px solid var(--bdr);
  display: flex; align-items: center; justify-content: center;
  font-size: 16px; color: var(--ink2); box-shadow: var(--sh0);
}
.cal-a:active { background: var(--surf3); }
.cgrd { flex-shrink: 0; display: grid; grid-template-columns: repeat(7,1fr); gap: 3px; padding: 0 14px 10px; }
.cdow { text-align: center; font-size: 10px; font-weight: 800; text-transform: uppercase; letter-spacing: .6px; color: var(--ghost); padding: 4px 0; }
.cday {
  aspect-ratio: 1; display: flex; align-items: center; justify-content: center;
  border-radius: 11px; font-size: 13px; font-weight: 600;
  cursor: pointer; position: relative; color: var(--ink);
}
.cday:active { background: var(--surf3); }
.cday.other { color: var(--ghost); }
.cday.today { background: var(--terra); color: #fff; font-weight: 800; box-shadow: 0 2px 10px rgba(184,92,56,.3); }
.cday.sel:not(.today) { background: var(--ochrelt); border: 1.5px solid var(--ochre2); color: var(--clay); font-weight: 800; }
.cday .blip { position: absolute; bottom: 3px; width: 4px; height: 4px; border-radius: 50%; background: var(--moss); }
.cday.today .blip { background: rgba(255,255,255,.7); }
.mlist { flex: 1; overflow-y: auto; -webkit-overflow-scrolling: touch; padding: 0 14px 24px; }
.dcard {
  background: var(--surf); border: 1px solid var(--bdr);
  border-radius: var(--r); padding: 12px 14px; margin-bottom: 8px;
  cursor: pointer; display: flex; align-items: center; gap: 12px;
  box-shadow: var(--sh0);
}
.dcard:active { background: var(--surf2); }
.dcn { font-family: Georgia, serif; font-size: 26px; font-weight: 700; color: var(--ochre); min-width: 36px; text-align: center; line-height: 1; }
.dci { flex: 1; }
.dcw { font-size: 10px; font-weight: 800; text-transform: uppercase; letter-spacing: .6px; color: var(--muted); }
.dcb { font-size: 13px; font-weight: 600; color: var(--ink2); margin-top: 2px; }
.dcp { display: flex; gap: 4px; flex-wrap: wrap; margin-top: 6px; }
.dpill { font-size: 10px; padding: 2px 8px; border-radius: 20px; font-weight: 700; }
.dca { color: var(--ghost); font-size: 15px; }

/* ═══════════════════════════════
   SETTINGS
═══════════════════════════════ */
#set-view { overflow-y: auto; -webkit-overflow-scrolling: touch; padding: 0 0 60px; background: var(--bg); }

/* Install card */
.inst-card { margin: 12px 16px 0; border-radius: var(--r); overflow: hidden; box-shadow: var(--sh2); }
.inst-top { background: linear-gradient(135deg, var(--terra), var(--clay)); padding: 16px 18px 0; }
.inst-hd { display: flex; align-items: center; gap: 10px; margin-bottom: 10px; }
.inst-ttl { font-size: 15px; font-weight: 800; color: #fff; }
.inst-sub { font-size: 11px; color: rgba(255,255,255,.72); margin-top: 1px; font-weight: 500; }
.inst-steps { background: rgba(255,255,255,.13); border-radius: 10px 10px 0 0; padding: 12px 14px; }
.istep { display: flex; align-items: flex-start; gap: 9px; margin-bottom: 10px; }
.istep:last-child { margin-bottom: 0; }
.isn { width: 21px; height: 21px; border-radius: 50%; background: rgba(255,255,255,.25); color: #fff; font-size: 11px; font-weight: 800; display: flex; align-items: center; justify-content: center; flex-shrink: 0; margin-top: 1px; }
.ist { font-size: 12px; font-weight: 500; color: rgba(255,255,255,.92); line-height: 1.55; }
.ist b { color: #fff; font-weight: 800; }
.inst-note { background: var(--surf); padding: 10px 16px; font-size: 11px; font-weight: 600; color: var(--muted); text-align: center; line-height: 1.7; }
.inst-note b { color: var(--terra); }

/* Alert warning box */
.alert-warn {
  margin: 10px 16px 0; border-radius: var(--rsm);
  background: var(--ochrelt); border: 1.5px solid var(--bdr2);
  padding: 11px 14px; font-size: 12px; font-weight: 600;
  color: var(--ink2); line-height: 1.6;
}
.alert-warn b { color: var(--clay); }

/* Settings sections */
.sw { padding: 14px 16px 0; }
.ss { margin-bottom: 20px; }
.shd { font-size: 10px; font-weight: 800; text-transform: uppercase; letter-spacing: .8px; color: var(--muted); margin-bottom: 8px; padding-left: 2px; }
.scard { background: var(--surf); border: 1px solid var(--bdr); border-radius: var(--r); overflow: hidden; box-shadow: var(--sh0); }
.srow { display: flex; align-items: center; justify-content: space-between; padding: 13px 16px; border-bottom: 1px solid var(--bdr); }
.srow:last-child { border-bottom: none; }
.srow-l label { font-size: 14px; font-weight: 600; color: var(--ink); display: block; }
.srow-l small { font-size: 11px; color: var(--muted); margin-top: 2px; display: block; font-weight: 500; }

/* ═══════════════════════════════
   TOGGLE  — data-on="1" = ON
   data attribute is more reliable
   than className on iOS Safari
═══════════════════════════════ */
.tog {
  position: relative;
  width: 50px; height: 28px;
  border-radius: 14px;
  -webkit-appearance: none; appearance: none;
  border: none; cursor: pointer; flex-shrink: 0;
  background: #b0a090;          /* OFF: warm grey */
  transition: background .22s;
  outline: none;
}
.tog[data-on="1"] {
  background: #557040;           /* ON: moss green */
}
.tog::after {
  content: '';
  position: absolute;
  top: 3px; left: 3px;
  width: 22px; height: 22px;
  border-radius: 50%;
  background: #fff;
  box-shadow: 0 1px 4px rgba(0,0,0,.22);
  transition: transform .22s cubic-bezier(.34,1.56,.64,1);
}
.tog[data-on="1"]::after { transform: translateX(22px); }

/* Slider */
.drblk { padding: 13px 16px; border-bottom: 1px solid var(--bdr); }
.drblk:last-child { border-bottom: none; }
.drtop { display: flex; justify-content: space-between; align-items: center; margin-bottom: 8px; }
.drtop label { font-size: 14px; font-weight: 600; color: var(--ink); }
.drbdg { background: var(--ochrelt); color: var(--clay); border-radius: 20px; padding: 3px 11px; font-size: 12px; font-weight: 800; border: 1px solid var(--bdr); }
input[type=range] { width: 100%; accent-color: #b85c38; cursor: pointer; height: 22px; }
.rmk { display: flex; justify-content: space-between; font-size: 9px; color: var(--ghost); font-weight: 700; margin-top: 1px; }

/* Cat chips in settings */
.scatg { display: grid; grid-template-columns: repeat(3,1fr); gap: 6px; padding: 12px; }
.schip { display: flex; flex-direction: column; align-items: center; gap: 5px; padding: 11px 4px; border-radius: 13px; font-size: 11px; font-weight: 700; border: 1.5px solid var(--bdr); background: var(--bg); }

/* Action rows */
.sact { display: flex; align-items: center; justify-content: space-between; padding: 13px 16px; border-bottom: 1px solid var(--bdr); cursor: pointer; }
.sact:active { background: var(--surf2); }
.sact:last-child { border-bottom: none; }
.sact-l { font-size: 14px; font-weight: 600; color: var(--ink); }

/* Test alert button */
.test-btn {
  width: 100%; padding: 13px;
  background: #557040; color: #fff;
  border-radius: 14px; margin-top: 8px;
  font-size: 14px; font-weight: 800;
  box-shadow: 0 3px 12px rgba(85,112,64,.3);
}
.test-btn:active { opacity: .85; }

/* Notif request button */
.notif-req-btn {
  width: 100%; padding: 12px 16px;
  background: var(--ochrelt); color: var(--clay);
  border-radius: 12px; margin-top: 6px;
  font-size: 13px; font-weight: 800;
  border: 1.5px solid var(--ochre2);
}
.notif-req-btn:active { opacity: .8; }

.foot { text-align: center; color: var(--ghost); font-size: 11px; padding: 12px 0 8px; font-weight: 600; line-height: 1.8; }

/* ═══════════════════════════════
   MODAL
═══════════════════════════════ */
#modal {
  display: none;
  position: fixed; inset: 0; z-index: 800;
}
#modal.show { display: block; }

.modal-backdrop {
  position: absolute; inset: 0;
  background: rgba(36,24,10,.45);
  -webkit-backdrop-filter: blur(6px);
  backdrop-filter: blur(6px);
}

.sheet {
  position: absolute; bottom: 0; left: 0; right: 0;
  background: var(--canvas);
  border-radius: 24px 24px 0 0;
  padding: 14px 20px calc(22px + var(--sb));
  animation: shUp .28s cubic-bezier(.32,.72,0,1);
  max-height: 92vh; overflow-y: auto;
  -webkit-overflow-scrolling: touch;
  box-shadow: 0 -10px 50px rgba(70,40,10,.18);
  border-top: 1px solid var(--bdr);
}
@keyframes shUp { from { transform: translateY(100%) } to { transform: translateY(0) } }

.sh-hnd { width: 36px; height: 4px; border-radius: 2px; background: var(--bdr2); margin: 0 auto 18px; }
.sh-ttl { font-family: Georgia, serif; font-size: 22px; font-weight: 700; color: var(--ink); margin-bottom: 20px; }

/* Form fields */
.fg { margin-bottom: 15px; }
.flbl { display: block; font-size: 10px; font-weight: 800; text-transform: uppercase; letter-spacing: .7px; color: var(--muted); margin-bottom: 6px; }
.fi {
  display: block; width: 100%;
  background: var(--surf); border: 2px solid var(--bdr);
  border-radius: 12px; padding: 12px 14px;
  color: var(--ink);
  font-size: 16px; /* 16px prevents iOS zoom */
  font-weight: 600; font-family: inherit;
  outline: none;
  transition: border-color .14s;
}
.fi:focus { border-color: var(--terra); }
.fi.err { border-color: var(--terra); background: var(--teralt); }
.fi::placeholder { color: var(--ghost); font-weight: 400; }

/* Category selector */
.csg { display: grid; grid-template-columns: repeat(3,1fr); gap: 6px; }
.copt {
  padding: 11px 4px; border-radius: 13px;
  border: 2px solid var(--bdr);
  text-align: center; font-size: 11px; font-weight: 700;
  cursor: pointer; background: var(--surf); color: var(--muted);
  line-height: 1.5;
}
.copt:active { opacity: .75; }
.copt.on { font-weight: 800; }

/* Duration display */
.dbd { text-align: center; font-family: Georgia, serif; font-size: 36px; font-weight: 700; color: var(--clay); margin: 4px 0 2px; }

/* Modal buttons — explicit hex colours, no CSS vars, for reliability */
.shbtns { display: flex; gap: 8px; margin-top: 20px; }

.btn-cancel {
  padding: 14px 18px;
  border-radius: 14px;
  border: 2px solid #d8ccb4;
  background: #fdfaf2;
  color: #5a4828;
  font-size: 15px; font-weight: 700;
}
.btn-cancel:active { background: #e8dcc8; }

.btn-save {
  flex: 1; padding: 14px;
  border-radius: 14px;
  background: #b85c38;   /* terra — explicit hex */
  color: #ffffff;
  font-size: 15px; font-weight: 800;
  box-shadow: 0 4px 16px rgba(184,92,56,.35);
}
.btn-save:active { opacity: .85; }

.btn-delete {
  padding: 14px 14px;
  border-radius: 14px;
  border: 2px solid rgba(184,92,56,.3);
  background: #faeee8;
  color: #b85c38;
  font-size: 14px; font-weight: 700;
}
.btn-delete:active { opacity: .8; }

/* scrollbar */
::-webkit-scrollbar { width: 3px; }
::-webkit-scrollbar-thumb { background: var(--bdr2); border-radius: 4px; }
</style>
</head>
<body>

<!-- Flash overlay -->
<div id="flash"></div>

<!-- Toast -->
<div id="toast">
  <div class="t-ico" id="tIco">🔔</div>
  <div>
    <div class="t-ttl" id="tTtl"></div>
    <div class="t-sub" id="tSub"></div>
  </div>
</div>

<div id="app">

  <!-- HEADER -->
  <header class="hdr">
    <div class="logo ser">Focus<i>Flow</i></div>
    <div class="hdr-mid">
      <div class="hdr-clock" id="hClock">00:00</div>
      <div class="hdr-date"  id="hDate">—</div>
    </div>
    <button id="bellBtn" onclick="toggleBell()">🔔</button>
  </header>

  <!-- NAV -->
  <nav class="nav">
    <button class="tab on" id="tab-day" onclick="goTab('day')">⏱ Day</button>
    <button class="tab"    id="tab-cal" onclick="goTab('cal')">📅 Month</button>
    <button class="tab"    id="tab-set" onclick="goTab('set')">⚙ Settings</button>
  </nav>

  <!-- ═══ DAY VIEW ═══ -->
  <div class="view on" id="day-view">
    <div class="dtb">
      <div class="dnav">
        <button class="darr" onclick="shiftDay(-1)">‹</button>
        <div class="dtitle" id="dtitle">Today</div>
        <button class="darr" onclick="shiftDay(1)">›</button>
      </div>
      <button class="abtn" onclick="openAdd()">＋ Block</button>
    </div>
    <div class="stats" id="stats"></div>
    <div id="ticker">
      <div class="tdot"></div>
      <div class="tname"   id="tickName">—</div>
      <div class="tremain" id="tickRemain">—</div>
    </div>
    <div class="tls" id="tls">
      <div class="tli" id="tli"></div>
    </div>
  </div>

  <!-- ═══ CALENDAR VIEW ═══ -->
  <div class="view" id="cal-view">
    <div class="cal-hdr">
      <button class="cal-a" onclick="prevMon()">‹</button>
      <div class="cal-m" id="calM">—</div>
      <button class="cal-a" onclick="nextMon()">›</button>
    </div>
    <div class="cgrd" id="cgrd"></div>
    <div class="mlist" id="mlist"></div>
  </div>

  <!-- ═══ SETTINGS VIEW ═══ -->
  <div class="view" id="set-view">

    <div class="inst-card">
      <div class="inst-top">
        <div class="inst-hd">
          <div style="font-size:26px;line-height:1">📲</div>
          <div>
            <div class="inst-ttl">Deployed on GitHub Pages</div>
            <div class="inst-sub">To update: re-upload index.html to GitHub repo</div>
          </div>
        </div>
        <div class="inst-steps">
          <div class="istep"><div class="isn">↑</div><div class="ist">Upload new <b>index.html</b> to your GitHub repo → GitHub automatically rebuilds → open app to get latest version</div></div>
        </div>
      </div>
      <div class="inst-note">Your URL: <b>lydiayfp.github.io/focusflow</b></div>
    </div>

    <!-- Alert limitation notice -->
    <div class="alert-warn">
      ⚠️ <b>Important about alerts:</b> Alerts fire when this app is <b>open or backgrounded</b> on iPhone. When the app is fully closed, iOS cannot run JavaScript — alerts require the app to be running. Keep the app open in background for reliable alerts.
    </div>

    <div class="sw">

      <!-- ALERTS -->
      <div class="ss">
        <div class="shd">Alerts &amp; Sound</div>
        <div class="scard">
          <div class="srow">
            <div class="srow-l">
              <label>Alerts armed</label>
              <small>Tap 🔔 in header to toggle</small>
            </div>
            <button class="tog" id="tog-alerts" data-key="alerts" onclick="togClick('alerts')"></button>
          </div>
          <div class="srow">
            <div class="srow-l">
              <label>Block start chime</label>
              <small>Sound when block begins</small>
            </div>
            <button class="tog" id="tog-alertStart" data-key="alertStart" onclick="togClick('alertStart')"></button>
          </div>
          <div class="srow">
            <div class="srow-l">
              <label>Block end chime</label>
              <small>Sound when block ends</small>
            </div>
            <button class="tog" id="tog-alertEnd" data-key="alertEnd" onclick="togClick('alertEnd')"></button>
          </div>
        </div>
        <button class="notif-req-btn" onclick="reqNotifPerm()">
          🔔 Allow System Notification Banners
        </button>
        <button class="test-btn" onclick="doTestAlert()">
          ▶ Test Alert Right Now
        </button>
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
            <input type="range" min="15" max="120" step="15" id="sDslr" oninput="sDur(this.value)">
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
            <button class="tog" id="tog-showNow" data-key="showNow" onclick="togClick('showNow')"></button>
          </div>
          <div class="srow">
            <div class="srow-l"><label>Half-hour marks</label></div>
            <button class="tog" id="tog-showHalf" data-key="showHalf" onclick="togClick('showHalf')"></button>
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
            <span class="sact-l" style="color:#b85c38">🗑 Clear selected day</span>
            <span style="color:#b85c38;opacity:.5;font-size:15px">›</span>
          </div>
        </div>
      </div>

      <div class="foot">FocusFlow v5 · All data on your device only</div>
    </div>
  </div>

</div><!-- /app -->

<!-- ═══ MODAL ═══ -->
<div id="modal">
  <div class="modal-backdrop" onclick="closeModal()"></div>
  <div class="sheet" onclick="event.stopPropagation()">
    <div class="sh-hnd"></div>
    <div class="sh-ttl" id="shTtl">New Focus Block</div>

    <div class="fg">
      <label class="flbl">Activity</label>
      <input class="fi" id="fAct" type="text"
        placeholder="Deep Work, Revision, Planning…"
        maxlength="40" autocomplete="off" autocorrect="off">
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
        style="width:100%;accent-color:#b85c38">
      <div class="rmk"><span>15m</span><span>30m</span><span>1h</span><span>2h</span><span>3h</span><span>4h</span></div>
    </div>

    <div class="fg">
      <label class="flbl">Note
        <span style="font-weight:400;text-transform:none;letter-spacing:0"> (optional)</span>
      </label>
      <input class="fi" id="fNt" type="text"
        placeholder="Goal or reminder…"
        maxlength="60" autocomplete="off" autocorrect="off">
    </div>

    <div class="shbtns" id="shbtns"></div>
  </div>
</div>

<!-- ═══════════════════════════════
     JAVASCRIPT
═══════════════════════════════ -->
<script>
/* ─────────────────────────────────────
   CATEGORIES
───────────────────────────────────── */
var CATS = [
  { id:'work',     label:'Work',     e:'💼', color:'#8a5630', bg:'#f5ede4' },
  { id:'study',    label:'Study',    e:'📚', color:'#486830', bg:'#ecf2e4' },
  { id:'break',    label:'Break',    e:'☕', color:'#7a5428', bg:'#f6f0dc' },
  { id:'personal', label:'Personal', e:'🏡', color:'#5a7060', bg:'#e8f0e8' },
  { id:'move',     label:'Move',     e:'🌿', color:'#4a6848', bg:'#e8f0e4' },
  { id:'creative', label:'Creative', e:'🎨', color:'#7a4850', bg:'#f4e8ea' }
];

/* ─────────────────────────────────────
   CONSTANTS
───────────────────────────────────── */
var PPM = 1.15;   /* px per minute on timeline */
var HRS = 7;      /* timeline start hour */
var HRE = 22;     /* timeline end hour */

/* ─────────────────────────────────────
   PREFS  — loaded from localStorage
   Key: ff_v5  (fresh key = clean slate)
───────────────────────────────────── */
var P = {
  alerts:     true,
  alertStart: true,
  alertEnd:   true,
  showNow:    true,
  showHalf:   true,
  defDur:     30
};
(function loadPrefs() {
  try {
    var s = localStorage.getItem('ff_v5');
    if (s) {
      var o = JSON.parse(s);
      for (var k in o) {
        if (o.hasOwnProperty(k) && P.hasOwnProperty(k)) {
          P[k] = o[k];
        }
      }
    }
  } catch(e) {}
})();

/* ─────────────────────────────────────
   BLOCK DATA  — loaded from localStorage
───────────────────────────────────── */
var B = {};
(function loadBlocks() {
  try {
    var s = localStorage.getItem('ff_b');
    if (s) B = JSON.parse(s);
  } catch(e) {}
})();

/* ─────────────────────────────────────
   UI STATE
───────────────────────────────────── */
var selDate = new Date();
var calDate = new Date();
var editId  = null;
var selCat  = 'work';

/* ─────────────────────────────────────
   HELPERS
───────────────────────────────────── */
var DS = ['Sun','Mon','Tue','Wed','Thu','Fri','Sat'];
var DL = ['Sunday','Monday','Tuesday','Wednesday','Thursday','Friday','Saturday'];
var MS = ['Jan','Feb','Mar','Apr','May','Jun','Jul','Aug','Sep','Oct','Nov','Dec'];
var ML = ['January','February','March','April','May','June','July','August','September','October','November','December'];

function p2(n)  { return String(n).padStart(2, '0'); }
function dk(d)  { return d.getFullYear()+'-'+p2(d.getMonth()+1)+'-'+p2(d.getDate()); }
function todK() { return dk(new Date()); }
function getB(k){ return B[k] || []; }

function setB(k, arr) {
  B[k] = arr;
  try { localStorage.setItem('ff_b', JSON.stringify(B)); } catch(e) {}
}

function saveP() {
  try { localStorage.setItem('ff_v5', JSON.stringify(P)); } catch(e) {}
}

function fmt(h, m) {
  return (h % 12 || 12) + ':' + p2(m) + ' ' + (h < 12 ? 'am' : 'pm');
}

function mStr(m) {
  return m >= 60
    ? Math.floor(m/60) + 'h' + (m%60 ? ' '+m%60+'m' : '')
    : m + 'm';
}

function gebi(id) { return document.getElementById(id); }

function activeTab() {
  if (gebi('day-view').classList.contains('on')) return 'day';
  if (gebi('cal-view').classList.contains('on')) return 'cal';
  return 'set';
}

/* ─────────────────────────────────────
   AUDIO ENGINE
   Key iOS rule: AudioContext must be
   created AND resumed inside a user
   gesture handler. We keep one context
   and resume it before every play call.
───────────────────────────────────── */
var _ctx = null;

function getCtx() {
  if (!_ctx) {
    try {
      _ctx = new (window.AudioContext || window.webkitAudioContext)();
    } catch(e) { return null; }
  }
  /* Always try to resume — iOS suspends after inactivity */
  if (_ctx.state === 'suspended') {
    try { _ctx.resume(); } catch(e) {}
  }
  return _ctx;
}

/* Resume audio on any touch — critical for iOS */
document.addEventListener('touchstart', function() {
  getCtx();
}, { passive: true });
document.addEventListener('touchend', function() {
  getCtx();
}, { passive: true });
document.addEventListener('click', function() {
  getCtx();
}, { passive: true });

function playTone(freq, startSec, durSec, vol) {
  var ctx = getCtx();
  if (!ctx) return;
  try {
    var o = ctx.createOscillator();
    var g = ctx.createGain();
    o.connect(g);
    g.connect(ctx.destination);
    o.type = 'triangle';
    o.frequency.value = freq;
    var t = ctx.currentTime + startSec;
    g.gain.setValueAtTime(0, t);
    g.gain.linearRampToValueAtTime(vol || 0.4, t + 0.025);
    g.gain.exponentialRampToValueAtTime(0.0001, t + durSec);
    o.start(t);
    o.stop(t + durSec + 0.05);
  } catch(e) {}
}

function chimeStart() {
  /* Rising triad: E4 → G4 → C5 */
  playTone(330, 0.00, 0.35, 0.45);
  playTone(392, 0.22, 0.38, 0.45);
  playTone(523, 0.44, 0.65, 0.42);
}

function chimeEnd() {
  /* Falling triad: C5 → G4 → E4 */
  playTone(523, 0.00, 0.35, 0.42);
  playTone(392, 0.22, 0.38, 0.40);
  playTone(330, 0.44, 0.75, 0.35);
}

/* Vibration — Android only, iOS silently ignores */
function vibrate(pattern) {
  try { if (navigator.vibrate) navigator.vibrate(pattern); } catch(e) {}
}

/* Screen flash */
function flashScreen() {
  var f = gebi('flash');
  if (!f) return;
  f.style.opacity = '1';
  setTimeout(function() { f.style.opacity = '0'; }, 220);
}

/* ─────────────────────────────────────
   TOAST
───────────────────────────────────── */
var _toastTmr = null;
function showToast(ico, title, sub) {
  gebi('tIco').textContent = ico;
  gebi('tTtl').textContent = title;
  gebi('tSub').textContent = sub || '';
  var t = gebi('toast');
  t.classList.add('show');
  if (_toastTmr) clearTimeout(_toastTmr);
  _toastTmr = setTimeout(function() { t.classList.remove('show'); }, 5000);
}

/* ─────────────────────────────────────
   SYSTEM NOTIFICATIONS
───────────────────────────────────── */
function reqNotifPerm() {
  if (typeof Notification === 'undefined') {
    showToast('ℹ️', 'Notifications require iOS 16.4+', 'Install app to Home Screen first');
    return;
  }
  if (Notification.permission === 'granted') {
    showToast('✅', 'Notifications already allowed', 'Banners will show when app is open/backgrounded');
    return;
  }
  Notification.requestPermission(function(result) {
    if (result === 'granted') {
      showToast('✅', 'Notification banners enabled!', 'Keep app open/backgrounded for alerts');
    } else {
      showToast('ℹ️', 'Banners blocked', 'Enable in iPhone Settings → FocusFlow → Notifications');
    }
  });
}

function sysNotif(title, body) {
  if (typeof Notification === 'undefined') return;
  if (Notification.permission !== 'granted') return;
  try { new Notification(title, { body: body }); } catch(e) {}
}

/* ─────────────────────────────────────
   ALERT ENGINE
   Polls every 15 seconds.
   Fires when device clock HH:MM matches
   block start or end minute exactly.
   Dedup key: date|blockId|S or E
───────────────────────────────────── */
var _firedSet = {};
var _lastAlertMin = -1;

function resetDayAlerts() {
  /* Reset fired log each new day */
  var stored = localStorage.getItem('ff_alertDay');
  var today  = todK();
  if (stored !== today) {
    _firedSet    = {};
    _lastAlertMin = -1;
    try { localStorage.setItem('ff_alertDay', today); } catch(e) {}
  }
}

function pollAlerts() {
  if (!P.alerts) return;

  var now    = new Date();
  var nowMin = now.getHours() * 60 + now.getMinutes();

  /* Only process once per clock minute */
  if (nowMin === _lastAlertMin) return;
  _lastAlertMin = nowMin;

  var bl = getB(todK());
  for (var i = 0; i < bl.length; i++) {
    var b      = bl[i];
    var parts  = b.start.split(':');
    var bh     = parseInt(parts[0], 10);
    var bm     = parseInt(parts[1], 10);
    var startM = bh * 60 + bm;
    var endM   = startM + b.dur;
    var cat    = getCat(b.cat);

    /* ── START alert ── */
    if (P.alertStart && nowMin === startM) {
      var sk = todK() + '|' + b.id + '|S';
      if (!_firedSet[sk]) {
        _firedSet[sk] = true;
        chimeStart();
        vibrate([100, 60, 100]);
        flashScreen();
        showToast(cat.e, '▶ Starting: ' + b.act, mStr(b.dur) + ' block — go!');
        sysNotif('▶ ' + b.act + ' starting', mStr(b.dur) + ' block — focus time!');
        renderDay();
      }
    }

    /* ── END alert ── */
    if (P.alertEnd && nowMin === endM) {
      var ek = todK() + '|' + b.id + '|E';
      if (!_firedSet[ek]) {
        _firedSet[ek] = true;
        chimeEnd();
        vibrate([80, 50, 80, 50, 200]);
        flashScreen();
        showToast('✅', 'Done: ' + b.act, 'Block complete — great work! ✓');
        sysNotif('✅ ' + b.act + ' complete', 'Block finished — well done!');
        renderDay();
      }
    }
  }
}

/* Manual test — fires immediately */
function doTestAlert() {
  getCtx(); /* ensure audio unlocked */
  setTimeout(function() {
    chimeStart();
    vibrate([100, 60, 100]);
    flashScreen();
    showToast('🔔', 'Alert test ✓', 'Sound + flash working! (vibration: Android only)');
  }, 100);
}

/* ─────────────────────────────────────
   TOGGLE SYSTEM
   Uses data-on="1" / data-on="0"
   CSS [data-on="1"] handles styling
───────────────────────────────────── */
function togClick(key) {
  P[key] = !P[key];
  saveP();
  applyTog(key);
  /* Side effects */
  if (key === 'alerts') {
    renderBell();
  }
  if (key === 'showNow' || key === 'showHalf') {
    renderDay();
  }
}

function applyTog(key) {
  var btn = gebi('tog-' + key);
  if (!btn) return;
  btn.setAttribute('data-on', P[key] ? '1' : '0');
}

function applyAllTogs() {
  var keys = ['alerts', 'alertStart', 'alertEnd', 'showNow', 'showHalf'];
  for (var i = 0; i < keys.length; i++) {
    applyTog(keys[i]);
  }
}

/* Bell button in header */
function toggleBell() {
  P.alerts = !P.alerts;
  saveP();
  applyTog('alerts');
  renderBell();
}

function renderBell() {
  var btn = gebi('bellBtn');
  if (!btn) return;
  if (P.alerts) {
    btn.className = 'on';
    btn.textContent = '🔔';
  } else {
    btn.className = '';
    btn.textContent = '🔕';
  }
}

/* ─────────────────────────────────────
   CLOCK — exact iPhone time, 1s tick
───────────────────────────────────── */
function tick() {
  var n = new Date();
  gebi('hClock').textContent = p2(n.getHours()) + ':' + p2(n.getMinutes());
  gebi('hDate').textContent  = DS[n.getDay()] + ' ' + n.getDate() + ' ' + MS[n.getMonth()] + ' ' + n.getFullYear();
  updateTicker(n);
}

/* Live countdown ticker */
function updateTicker(now) {
  var isToday = dk(selDate) === dk(now);
  if (!isToday) { gebi('ticker').classList.remove('show'); return; }

  var nowSec = now.getHours() * 3600 + now.getMinutes() * 60 + now.getSeconds();
  var bl = getB(dk(selDate));
  var found = null;

  for (var i = 0; i < bl.length; i++) {
    var b     = bl[i];
    var parts = b.start.split(':');
    var bh    = parseInt(parts[0], 10);
    var bm    = parseInt(parts[1], 10);
    var startS = bh * 3600 + bm * 60;
    var endS   = startS + b.dur * 60;
    if (startS <= nowSec && nowSec < endS) {
      found = { block: b, remSec: endS - nowSec };
      break;
    }
  }

  if (found) {
    var cat = getCat(found.block.cat);
    gebi('tickName').textContent = cat.e + ' ' + found.block.act;
    var rm = Math.floor(found.remSec / 60);
    var rs = found.remSec % 60;
    gebi('tickRemain').textContent = rm + ':' + p2(rs) + ' left';
    gebi('ticker').classList.add('show');
  } else {
    gebi('ticker').classList.remove('show');
  }
}

/* ─────────────────────────────────────
   BOOT
───────────────────────────────────── */
window.onload = function() {
  /* Render settings */
  buildCsg();
  buildScatg();
  applyAllTogs();
  renderBell();
  gebi('sDslr').value = P.defDur;
  gebi('sDbdg').textContent = mStr(P.defDur);

  /* Start clock — 1 second precision */
  tick();
  setInterval(tick, 1000);

  /* Alert poll — every 15 seconds */
  resetDayAlerts();
  setTimeout(pollAlerts, 500); /* immediate check on load */
  setInterval(function() {
    resetDayAlerts();
    pollAlerts();
  }, 15000);

  renderDay();
  renderCal();
};

/* ─────────────────────────────────────
   TABS
───────────────────────────────────── */
function goTab(t) {
  var tabs = ['day', 'cal', 'set'];
  for (var i = 0; i < tabs.length; i++) {
    var id = tabs[i];
    gebi('tab-' + id).className = 'tab' + (id === t ? ' on' : '');
    gebi(id + '-view').className = 'view' + (id === t ? ' on' : '');
  }
  if (t === 'cal') renderCal();
  if (t === 'day') renderDay();
}

/* ─────────────────────────────────────
   DAY VIEW
───────────────────────────────────── */
function shiftDay(d) {
  selDate = new Date(selDate);
  selDate.setDate(selDate.getDate() + d);
  renderDay();
}

function renderDay() {
  var now     = new Date();
  var isToday = dk(selDate) === dk(now);

  /* Title */
  gebi('dtitle').textContent = isToday
    ? 'Today · ' + selDate.getDate() + ' ' + ML[selDate.getMonth()]
    : DL[selDate.getDay()].slice(0, 3) + ' ' + selDate.getDate() + ' ' + ML[selDate.getMonth()];

  /* Stats */
  var bl  = getB(dk(selDate));
  var tot = 0;
  var byCat = {};
  for (var i = 0; i < bl.length; i++) {
    tot += bl[i].dur;
    byCat[bl[i].cat] = (byCat[bl[i].cat] || 0) + bl[i].dur;
  }
  var topId = null, topV = 0;
  for (var k in byCat) {
    if (byCat.hasOwnProperty(k) && byCat[k] > topV) { topV = byCat[k]; topId = k; }
  }
  var topC = topId ? getCat(topId) : null;
  gebi('stats').innerHTML =
    '<div class="sc"><div class="sv">' + bl.length + '</div><div class="sl">Blocks</div></div>' +
    '<div class="sc"><div class="sv">' + (tot ? mStr(tot) : '—') + '</div><div class="sl">Focused</div></div>' +
    '<div class="sc"><div class="sv" style="font-size:21px">' + (topC ? topC.e : '·') + '</div><div class="sl">' + (topC ? topC.label : 'Rest') + '</div></div>';

  /* Timeline */
  var inner = gebi('tli');
  inner.innerHTML = '';
  inner.style.height = ((HRE - HRS) * 60 * PPM + 64) + 'px';

  /* Hour rows */
  for (var h = HRS; h <= HRE; h++) {
    var top = ((h - HRS) * 60) * PPM;
    addRow(inner, top, h < 12 ? h + 'am' : h === 12 ? '12pm' : (h - 12) + 'pm', false);
    if (P.showHalf && h < HRE) {
      var halfLbl = h < 11 ? (h+1)+':30' : h === 11 ? '12:30' : (h-11)+':30';
      addRow(inner, top + 30 * PPM, halfLbl, true);
    }
  }

  /* Current minute totals */
  var nowTotMin = isToday ? now.getHours() * 60 + now.getMinutes() : -1;
  var nowMins   = isToday ? (now.getHours() - HRS) * 60 + now.getMinutes() : -1;

  /* Blocks */
  for (var i = 0; i < bl.length; i++) {
    renderBlock(inner, bl[i], nowTotMin, dk(selDate));
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
      '<div class="e-ico">🌾</div>' +
      '<div class="e-msg">No focus blocks yet.<br>Plant your first intention for the day.</div>' +
      '<button class="e-btn" onclick="openAdd()">＋ Add first block</button>';
    inner.appendChild(emp);
  }

  /* Scroll to current hour */
  var sc = gebi('tls');
  setTimeout(function() {
    sc.scrollTop = isToday ? Math.max(0, (now.getHours() - HRS - 0.8) * 60 * PPM) : 0;
  }, 60);
}

function renderBlock(inner, b, nowTotMin, key) {
  var parts = b.start.split(':');
  var bh    = parseInt(parts[0], 10);
  var bm    = parseInt(parts[1], 10);
  var sm    = (bh - HRS) * 60 + bm;
  if (sm < 0 || sm > (HRE - HRS) * 60) return;

  var hpx   = Math.max(b.dur * PPM, 46);
  var cat   = getCat(b.cat);
  var em    = bh * 60 + bm + b.dur;
  var isNow = nowTotMin >= 0 && (bh * 60 + bm) <= nowTotMin && nowTotMin < em;

  var div = document.createElement('div');
  div.className = 'tblk' + (isNow ? ' nowblk' : '');
  div.style.cssText =
    'top:' + (sm * PPM) + 'px;' +
    'height:' + hpx + 'px;' +
    'left:0;right:0;' +
    'background:' + cat.bg + ';' +
    'border-left-color:' + cat.color + ';';

  div.innerHTML =
    '<div class="tb-t" style="color:' + cat.color + '">' + cat.e + ' ' + b.act + '</div>' +
    '<div class="tb-s" style="color:' + cat.color + '">' +
      fmt(bh, bm) + ' → ' + fmt(Math.floor(em/60), em%60) + ' · ' + mStr(b.dur) +
    '</div>' +
    (b.note ? '<div class="tb-n" style="color:' + cat.color + '">' + b.note + '</div>' : '') +
    '<div class="tbr"><div class="tbr-b" style="background:' + cat.color + ';opacity:.18"></div></div>';

  /* Use IIFE to capture b and key */
  (function(block, dKey) {
    div.addEventListener('click', function(ev) {
      if (!ev.target.closest('.tbr')) openEdit(block.id);
    });
    setupResize(div.querySelector('.tbr'), block, dKey);
  })(b, key);

  inner.appendChild(div);
}

function addRow(parent, top, label, half) {
  var r = document.createElement('div');
  r.className = 'hrow';
  r.style.top = top + 'px';
  r.innerHTML =
    '<div class="hlbl"' + (half ? ' style="opacity:.38;font-size:9px"' : '') + '>' + label + '</div>' +
    '<div class="hline' + (half ? ' half' : '') + '"></div>';
  parent.appendChild(r);
}

/* ─────────────────────────────────────
   RESIZE HANDLE
───────────────────────────────────── */
function setupResize(handle, block, key) {
  if (!handle) return;
  var sy, sd;
  handle.addEventListener('pointerdown', function(e) {
    e.stopPropagation();
    sy = e.clientY;
    sd = block.dur;
    handle.setPointerCapture(e.pointerId);

    function mv(ev) {
      var delta = Math.round((ev.clientY - sy) / PPM / 15) * 15;
      var nd    = Math.max(15, Math.min(240, sd + delta));
      if (nd !== block.dur) {
        block.dur = nd;
        var arr = getB(key);
        for (var j = 0; j < arr.length; j++) {
          if (arr[j].id === block.id) { arr[j].dur = nd; break; }
        }
        setB(key, arr);
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

/* ─────────────────────────────────────
   MODAL — OPEN / CLOSE
───────────────────────────────────── */
function openAdd() {
  editId  = null;
  selCat  = 'work';

  gebi('shTtl').textContent = 'New Focus Block';
  gebi('fAct').value = '';
  gebi('fAct').className = 'fi';
  gebi('fNt').value  = '';

  /* Default duration */
  gebi('fDslr').value = P.defDur;
  updDbd(P.defDur);

  /* Default start time: now rounded to nearest 15 min */
  var n = new Date();
  var h = Math.max(HRS, Math.min(HRE - 1, n.getHours()));
  var m = Math.round(n.getMinutes() / 15) * 15;
  if (m >= 60) { h = Math.min(HRE - 1, h + 1); m = 0; }
  gebi('fSt').value = p2(h) + ':' + p2(m);

  refreshCsg();
  gebi('shbtns').innerHTML =
    '<button class="btn-cancel" type="button" onclick="closeModal()">Cancel</button>' +
    '<button class="btn-save"   type="button" onclick="saveBlock()">Save Block</button>';

  gebi('modal').classList.add('show');
  setTimeout(function() { gebi('fAct').focus(); }, 320);
}

function openEdit(id) {
  var arr = getB(dk(selDate));
  var b   = null;
  for (var i = 0; i < arr.length; i++) {
    if (arr[i].id === id) { b = arr[i]; break; }
  }
  if (!b) return;

  editId = id;
  selCat = b.cat;

  gebi('shTtl').textContent = 'Edit Block';
  gebi('fAct').value = b.act;
  gebi('fAct').className = 'fi';
  gebi('fNt').value  = b.note || '';
  gebi('fSt').value  = b.start;
  gebi('fDslr').value = b.dur;
  updDbd(b.dur);

  refreshCsg();
  gebi('shbtns').innerHTML =
    '<button class="btn-delete" type="button" onclick="delBlock()">Delete</button>' +
    '<button class="btn-cancel" type="button" onclick="closeModal()">Cancel</button>' +
    '<button class="btn-save"   type="button" onclick="saveBlock()">Update</button>';

  gebi('modal').classList.add('show');
}

function closeModal() {
  gebi('modal').classList.remove('show');
  editId = null;
}

/* ─────────────────────────────────────
   SAVE BLOCK — the critical fix
   Reads all fields carefully,
   validates, then writes to storage.
───────────────────────────────────── */
function saveBlock() {
  /* 1. Read activity name */
  var actEl = gebi('fAct');
  var act   = actEl ? actEl.value.trim() : '';

  /* 2. Validate — activity is required */
  if (!act) {
    if (actEl) {
      actEl.className = 'fi err';
      actEl.placeholder = '← Enter an activity name';
      actEl.focus();
    }
    return;
  }
  if (actEl) actEl.className = 'fi';

  /* 3. Read other fields with safe fallbacks */
  var stEl  = gebi('fSt');
  var durEl = gebi('fDslr');
  var ntEl  = gebi('fNt');

  var start = (stEl  && stEl.value)  ? stEl.value        : '09:00';
  var dur   = (durEl && durEl.value) ? parseInt(durEl.value, 10) : P.defDur;
  var note  = (ntEl  && ntEl.value)  ? ntEl.value.trim() : '';

  /* 4. Sanitise dur */
  if (isNaN(dur) || dur < 15) dur = 15;
  if (dur > 240) dur = 240;

  /* 5. Save */
  var key = dk(selDate);
  var arr = getB(key);

  if (editId) {
    /* Update existing block */
    for (var i = 0; i < arr.length; i++) {
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
    /* Create new block */
    var newId = Date.now().toString(36) + Math.random().toString(36).slice(2);
    arr.push({ id: newId, act: act, cat: selCat, start: start, dur: dur, note: note });
    /* Sort by start time */
    arr.sort(function(a, b) {
      return a.start < b.start ? -1 : a.start > b.start ? 1 : 0;
    });
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
  var out = [];
  for (var i = 0; i < arr.length; i++) {
    if (arr[i].id !== editId) out.push(arr[i]);
  }
  setB(key, out);
  closeModal();
  renderDay();
}

function updDbd(v) {
  gebi('fDbd').textContent = mStr(parseInt(v, 10));
}

/* ─────────────────────────────────────
   CATEGORY SELECT
───────────────────────────────────── */
function getCat(id) {
  for (var i = 0; i < CATS.length; i++) {
    if (CATS[i].id === id) return CATS[i];
  }
  return CATS[0];
}

function buildCsg() {
  var g = gebi('csg');
  if (!g) return;
  g.innerHTML = '';
  for (var i = 0; i < CATS.length; i++) {
    var c   = CATS[i];
    var div = document.createElement('div');
    div.className = 'copt';
    div.setAttribute('data-c', c.id);
    div.innerHTML = c.e + '<br>' + c.label;
    /* Capture c.id in closure */
    (function(cid) {
      div.onclick = function() { selCat = cid; refreshCsg(); };
    })(c.id);
    g.appendChild(div);
  }
  refreshCsg();
}

function refreshCsg() {
  var opts = document.querySelectorAll('.copt');
  for (var i = 0; i < opts.length; i++) {
    var opt = opts[i];
    var cid = opt.getAttribute('data-c');
    var cat = getCat(cid);
    var on  = (cid === selCat);
    opt.className            = 'copt' + (on ? ' on' : '');
    opt.style.borderColor    = on ? cat.color : 'var(--bdr)';
    opt.style.background     = on ? cat.bg    : 'var(--surf)';
    opt.style.color          = on ? cat.color : 'var(--muted)';
  }
}

/* ─────────────────────────────────────
   CALENDAR
───────────────────────────────────── */
function renderCal() {
  var y = calDate.getFullYear();
  var m = calDate.getMonth();
  gebi('calM').textContent = ML[m] + ' ' + y;

  var grd = gebi('cgrd');
  grd.innerHTML = '';

  var dow = ['Su','Mo','Tu','We','Th','Fr','Sa'];
  for (var i = 0; i < dow.length; i++) {
    var h = document.createElement('div');
    h.className   = 'cdow';
    h.textContent = dow[i];
    grd.appendChild(h);
  }

  var first = new Date(y, m, 1);
  var last  = new Date(y, m+1, 0);
  var tK    = todK();
  var sK    = dk(selDate);

  /* Blank prefix */
  for (var i = 0; i < first.getDay(); i++) {
    var pd  = new Date(y, m, 1 - first.getDay() + i);
    var pEl = document.createElement('div');
    pEl.className   = 'cday other';
    pEl.textContent = pd.getDate();
    grd.appendChild(pEl);
  }

  /* Days */
  for (var d = 1; d <= last.getDate(); d++) {
    var dt  = new Date(y, m, d);
    var dK  = dk(dt);
    var isT = dK === tK;
    var iS  = dK === sK && !isT;
    var hB  = getB(dK).length > 0;

    var dEl = document.createElement('div');
    dEl.className   = 'cday' + (isT ? ' today' : '') + (iS ? ' sel' : '');
    dEl.textContent = d;

    if (hB) {
      var bp = document.createElement('div');
      bp.className = 'blip';
      dEl.appendChild(bp);
    }

    (function(dt2) {
      dEl.onclick = function() {
        selDate = dt2;
        calDate = new Date(dt2);
        renderCal();
        goTab('day');
      };
    })(dt);

    grd.appendChild(dEl);
  }

  /* Month list */
  var list = gebi('mlist');
  list.innerHTML = '';
  var any = false;

  for (var d = 1; d <= last.getDate(); d++) {
    var dt2 = new Date(y, m, d);
    var dK2 = dk(dt2);
    var bl  = getB(dK2);
    if (!bl.length) continue;
    any = true;

    var tot = 0;
    for (var i = 0; i < bl.length; i++) tot += bl[i].dur;

    var seen  = {};
    var pills = '';
    for (var i = 0; i < bl.length; i++) {
      var cid = bl[i].cat;
      if (seen[cid]) continue;
      seen[cid] = true;
      var cat = getCat(cid);
      pills += '<span class="dpill" style="background:' + cat.bg + ';color:' + cat.color + '">' + cat.e + ' ' + cat.label + '</span>';
    }

    var card = document.createElement('div');
    card.className = 'dcard';
    card.innerHTML =
      '<div class="dcn">' + d + '</div>' +
      '<div class="dci">' +
        '<div class="dcw">' + DS[dt2.getDay()] + '</div>' +
        '<div class="dcb">' + bl.length + ' block' + (bl.length > 1 ? 's' : '') + ' · ' + mStr(tot) + ' focused</div>' +
        '<div class="dcp">' + pills + '</div>' +
      '</div>' +
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

/* ─────────────────────────────────────
   SETTINGS HELPERS
───────────────────────────────────── */
function sDur(v) {
  P.defDur = parseInt(v, 10);
  gebi('sDbdg').textContent = mStr(P.defDur);
  saveP();
}

function buildScatg() {
  var g = gebi('scatg');
  if (!g) return;
  g.innerHTML = '';
  for (var i = 0; i < CATS.length; i++) {
    var c  = CATS[i];
    var ch = document.createElement('div');
    ch.className = 'schip';
    ch.style.cssText = 'border-color:' + c.color + '22;background:' + c.bg + ';';
    ch.innerHTML = '<span style="font-size:22px">' + c.e + '</span><span style="color:' + c.color + ';font-size:11px">' + c.label + '</span>';
    g.appendChild(ch);
  }
}

function doExport() {
  try {
    var blob = new Blob([JSON.stringify(B, null, 2)], { type: 'application/json' });
    var a    = document.createElement('a');
    a.href   = URL.createObjectURL(blob);
    a.download = 'focusflow-' + todK() + '.json';
    a.click();
  } catch(e) {
    alert('On iPhone: Share → Save to Files to export your data.');
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
