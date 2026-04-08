# Gatekeeper-financial-assessment-1

<html lang="he" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>GateKeeper — מבדק אמינות פיננסית</title>
<link href="https://fonts.googleapis.com/css2?family=Heebo:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
<style>
*{box-sizing:border-box;margin:0;padding:0;}

:root{
  --bg:#060b14;
  --surface:#0d1117;
  --surface2:#111827;
  --border:#1e2a3a;
  --border2:#243348;
  --text:#e0e6f0;
  --text2:#94a3b8;
  --text3:#475569;
  --accent:#38bdf8;
  --accent2:#0ea5e9;
  --green:#22c55e;
  --orange:#f97316;
  --red:#ef4444;
  --glow-accent:rgba(56,189,248,0.15);
  --glow-green:rgba(34,197,94,0.15);
  --glow-orange:rgba(249,115,22,0.15);
  --glow-red:rgba(239,68,68,0.15);
}

body{
  font-family:'Heebo',sans-serif;
  direction:rtl;
  background:var(--bg);
  min-height:100vh;
  color:var(--text);
  overflow-x:hidden;
}

/* BACKGROUND GRID */
body::before{
  content:'';
  position:fixed;
  inset:0;
  background-image:
    linear-gradient(rgba(56,189,248,0.03) 1px, transparent 1px),
    linear-gradient(90deg, rgba(56,189,248,0.03) 1px, transparent 1px);
  background-size:40px 40px;
  pointer-events:none;
  z-index:0;
}

/* SCAN LINE ANIMATION */
body::after{
  content:'';
  position:fixed;
  top:-100%;
  left:0;right:0;
  height:200px;
  background:linear-gradient(to bottom, transparent, rgba(56,189,248,0.015), transparent);
  animation:scan 8s linear infinite;
  pointer-events:none;
  z-index:0;
}
@keyframes scan{to{top:100%;}}

.wrap{
  position:relative;
  z-index:1;
  max-width:780px;
  margin:0 auto;
  padding:32px 16px 60px;
}

/* ═══ HEADER ═══ */
.hdr{
  display:flex;
  justify-content:space-between;
  align-items:center;
  margin-bottom:32px;
  padding-bottom:20px;
  border-bottom:1px solid var(--border);
}
.logo{
  display:flex;
  align-items:center;
  gap:12px;
}
.logo-icon{
  width:40px;height:40px;
  background:linear-gradient(135deg,#0ea5e9,#38bdf8);
  border-radius:10px;
  display:flex;align-items:center;justify-content:center;
  font-size:18px;
  box-shadow:0 0 20px rgba(56,189,248,0.35);
}
.logo-text{font-size:20px;font-weight:800;color:var(--accent);letter-spacing:1px;text-shadow:0 0 20px rgba(56,189,248,0.4);}
.logo-sub{font-size:10px;color:var(--text3);font-weight:400;letter-spacing:1.5px;text-transform:uppercase;margin-top:2px;}
.hdr-badge{
  background:rgba(56,189,248,0.08);
  border:1px solid rgba(56,189,248,0.2);
  border-radius:8px;
  padding:6px 14px;
  font-size:11px;
  color:var(--text2);
  letter-spacing:0.5px;
}
.hdr-badge span{color:var(--accent);font-weight:600;}

/* ═══ PROGRESS ═══ */
.progress-wrap{margin-bottom:28px;}
.progress-info{display:flex;justify-content:space-between;align-items:center;margin-bottom:8px;}
.progress-label{font-size:11px;color:var(--text3);letter-spacing:1px;text-transform:uppercase;}
.progress-count{font-size:13px;font-weight:700;color:var(--accent);}
.progress-track{
  height:4px;
  background:var(--border);
  border-radius:4px;
  overflow:hidden;
  position:relative;
}
.progress-fill{
  height:100%;
  background:linear-gradient(90deg,#0ea5e9,#38bdf8);
  border-radius:4px;
  transition:width 0.5s cubic-bezier(0.4,0,0.2,1);
  box-shadow:0 0 12px rgba(56,189,248,0.5);
  width:0%;
}
.section-dots{display:flex;gap:6px;margin-top:10px;justify-content:flex-end;}
.sdot{
  width:8px;height:8px;border-radius:50%;
  background:var(--border2);
  transition:all 0.3s;
}
.sdot.active{background:var(--accent);box-shadow:0 0 8px rgba(56,189,248,0.6);}
.sdot.done{background:var(--green);box-shadow:0 0 8px rgba(34,197,94,0.4);}

/* ═══ SCREENS ═══ */
.screen{display:none;animation:fadeIn 0.4s ease;}
.screen.active{display:block;}
@keyframes fadeIn{from{opacity:0;transform:translateY(10px);}to{opacity:1;transform:translateY(0);}}

/* ═══ INTRO SCREEN ═══ */
.intro-card{
  background:var(--surface);
  border:1px solid var(--border);
  border-radius:16px;
  overflow:hidden;
}
.intro-top{
  background:linear-gradient(135deg, rgba(14,165,233,0.12), rgba(56,189,248,0.05));
  border-bottom:1px solid var(--border);
  padding:28px 28px 24px;
  position:relative;
}
.intro-top::before{
  content:'FINANCIAL INTEGRITY ASSESSMENT';
  position:absolute;
  top:14px;left:20px;
  font-size:8px;letter-spacing:2px;
  color:rgba(56,189,248,0.2);
  font-weight:600;
}
.intro-badge{
  display:inline-flex;align-items:center;gap:6px;
  background:rgba(56,189,248,0.1);
  border:1px solid rgba(56,189,248,0.25);
  border-radius:20px;padding:4px 12px;
  font-size:10px;color:var(--accent);
  font-weight:600;letter-spacing:1px;
  margin-bottom:14px;
}
.pulse{
  width:6px;height:6px;border-radius:50%;
  background:var(--accent);
  animation:pulse 1.5s ease infinite;
}
@keyframes pulse{0%,100%{opacity:1;transform:scale(1);}50%{opacity:0.4;transform:scale(0.8);}}

.intro-title{font-size:26px;font-weight:800;color:var(--text);line-height:1.25;margin-bottom:8px;}
.intro-title span{color:var(--accent);}
.intro-sub{font-size:13px;color:var(--text2);line-height:1.6;}

.intro-body{padding:24px 28px;}

.intro-section{margin-bottom:22px;}
.intro-section-title{
  display:flex;align-items:center;gap:8px;
  font-size:11px;font-weight:700;
  color:var(--accent);
  letter-spacing:1.5px;text-transform:uppercase;
  margin-bottom:12px;
}
.intro-section-title::after{
  content:'';flex:1;
  height:1px;background:linear-gradient(90deg,rgba(56,189,248,0.3),transparent);
}

.intro-text{font-size:13px;color:var(--text2);line-height:1.75;}
.intro-text p{margin-bottom:10px;}
.intro-text p:last-child{margin-bottom:0;}
.intro-text strong{color:var(--text);font-weight:600;}

.alert-box{
  background:rgba(249,115,22,0.07);
  border:1px solid rgba(249,115,22,0.25);
  border-radius:10px;
  padding:14px 16px;
  display:flex;gap:12px;align-items:flex-start;
  margin:16px 0;
}
.alert-icon{font-size:18px;flex-shrink:0;margin-top:1px;}
.alert-text{font-size:12px;color:var(--text2);line-height:1.65;}
.alert-text strong{color:var(--orange);}

.trust-box{
  background:rgba(34,197,94,0.06);
  border:1px solid rgba(34,197,94,0.2);
  border-radius:10px;
  padding:14px 16px;
  display:flex;gap:12px;align-items:flex-start;
}
.trust-text{font-size:12px;color:var(--text2);line-height:1.65;}
.trust-text strong{color:var(--green);}

.instructions-grid{
  display:grid;grid-template-columns:1fr 1fr;
  gap:10px;margin-top:12px;
}
.inst-item{
  background:rgba(255,255,255,0.03);
  border:1px solid var(--border);
  border-radius:8px;
  padding:12px;
  display:flex;gap:10px;align-items:flex-start;
}
.inst-num{
  width:22px;height:22px;border-radius:50%;
  background:rgba(56,189,248,0.12);
  border:1px solid rgba(56,189,248,0.25);
  color:var(--accent);
  font-size:10px;font-weight:700;
  display:flex;align-items:center;justify-content:center;
  flex-shrink:0;
}
.inst-txt{font-size:11px;color:var(--text2);line-height:1.55;}

.sections-preview{
  display:flex;gap:8px;flex-wrap:wrap;margin-top:12px;
}
.sec-tag{
  background:rgba(255,255,255,0.04);
  border:1px solid var(--border2);
  border-radius:6px;
  padding:6px 12px;
  font-size:11px;color:var(--text2);
  display:flex;align-items:center;gap:6px;
}
.sec-tag-dot{width:6px;height:6px;border-radius:50%;}

.start-btn{
  width:100%;
  padding:16px;
  background:linear-gradient(135deg,#0ea5e9,#38bdf8);
  border:none;border-radius:12px;
  color:#fff;font-size:15px;font-weight:700;
  font-family:'Heebo',sans-serif;
  cursor:pointer;
  letter-spacing:0.5px;
  box-shadow:0 0 30px rgba(56,189,248,0.3);
  transition:all 0.2s;
  display:flex;align-items:center;justify-content:center;gap:8px;
  margin-top:24px;
}
.start-btn:hover{
  background:linear-gradient(135deg,#38bdf8,#7dd3fc);
  box-shadow:0 0 40px rgba(56,189,248,0.5);
  transform:translateY(-1px);
}

/* ═══ QUESTION SCREEN ═══ */
.q-section-header{
  display:flex;align-items:center;gap:10px;
  margin-bottom:20px;
}
.q-section-tag{
  background:rgba(56,189,248,0.1);
  border:1px solid rgba(56,189,248,0.25);
  border-radius:20px;padding:4px 14px;
  font-size:10px;font-weight:700;
  color:var(--accent);letter-spacing:1px;
}
.q-section-name{font-size:13px;color:var(--text2);}

.q-card{
  background:var(--surface);
  border:1px solid var(--border);
  border-radius:16px;
  padding:28px;
  position:relative;
  overflow:hidden;
}
.q-card::before{
  content:'';
  position:absolute;top:0;right:0;left:0;height:2px;
  background:linear-gradient(90deg,transparent,var(--accent),transparent);
  opacity:0.5;
}
.q-num{
  font-size:10px;font-weight:600;
  color:var(--text3);letter-spacing:2px;
  text-transform:uppercase;margin-bottom:12px;
}
.q-text{
  font-size:17px;font-weight:600;
  color:var(--text);line-height:1.55;
  margin-bottom:24px;
}

.options{display:flex;flex-direction:column;gap:8px;}
.option{
  background:rgba(255,255,255,0.03);
  border:1px solid var(--border);
  border-radius:10px;
  padding:14px 16px;
  cursor:pointer;
  transition:all 0.2s;
  display:flex;align-items:center;gap:12px;
  font-size:13px;color:var(--text2);
  position:relative;
  overflow:hidden;
}
.option::before{
  content:'';
  position:absolute;inset:0;
  background:linear-gradient(135deg,rgba(56,189,248,0.06),transparent);
  opacity:0;transition:opacity 0.2s;
}
.option:hover{
  border-color:rgba(56,189,248,0.4);
  color:var(--text);
}
.option:hover::before{opacity:1;}
.option.selected{
  border-color:var(--accent);
  background:rgba(56,189,248,0.08);
  color:var(--text);
}
.option.selected::before{opacity:1;}
.opt-radio{
  width:18px;height:18px;border-radius:50%;
  border:2px solid var(--border2);
  display:flex;align-items:center;justify-content:center;
  flex-shrink:0;transition:all 0.2s;
}
.option.selected .opt-radio{
  border-color:var(--accent);
  background:var(--accent);
  box-shadow:0 0 8px rgba(56,189,248,0.5);
}
.opt-check{
  width:8px;height:8px;border-radius:50%;
  background:#fff;opacity:0;transition:opacity 0.2s;
}
.option.selected .opt-check{opacity:1;}
.opt-text{flex:1;}

.q-nav{
  display:flex;justify-content:space-between;align-items:center;
  margin-top:24px;
}
.btn-prev{
  background:transparent;
  border:1px solid var(--border2);
  border-radius:8px;padding:10px 20px;
  color:var(--text2);font-size:13px;
  font-family:'Heebo',sans-serif;
  cursor:pointer;transition:all 0.2s;
  display:flex;align-items:center;gap:6px;
}
.btn-prev:hover{border-color:var(--accent);color:var(--accent);}
.btn-prev:disabled{opacity:0.3;cursor:not-allowed;}
.btn-next{
  background:linear-gradient(135deg,#0ea5e9,#38bdf8);
  border:none;border-radius:8px;padding:10px 24px;
  color:#fff;font-size:13px;font-weight:700;
  font-family:'Heebo',sans-serif;
  cursor:pointer;transition:all 0.2s;
  display:flex;align-items:center;gap:6px;
  box-shadow:0 0 16px rgba(56,189,248,0.25);
}
.btn-next:hover{box-shadow:0 0 24px rgba(56,189,248,0.45);transform:translateY(-1px);}
.btn-next:disabled{opacity:0.35;cursor:not-allowed;transform:none;}

.skip-note{font-size:11px;color:var(--text3);text-align:center;margin-top:12px;}

/* ═══ SECTION DIVIDER ═══ */
.section-divider{
  background:var(--surface);
  border:1px solid var(--border);
  border-radius:16px;
  padding:32px;
  text-align:center;
  margin:4px 0;
}
.sdiv-icon{font-size:36px;margin-bottom:12px;}
.sdiv-title{font-size:18px;font-weight:700;color:var(--text);margin-bottom:6px;}
.sdiv-sub{font-size:13px;color:var(--text2);margin-bottom:20px;line-height:1.6;}
.sdiv-progress{
  display:flex;justify-content:center;gap:8px;margin-bottom:20px;
}
.sdiv-dot{
  width:10px;height:10px;border-radius:50%;
  background:var(--border2);
}
.sdiv-dot.done{background:var(--green);}
.sdiv-dot.current{background:var(--accent);box-shadow:0 0 8px rgba(56,189,248,0.6);}

/* ═══ PROCESSING ═══ */
.processing{
  background:var(--surface);
  border:1px solid var(--border);
  border-radius:16px;
  padding:60px 32px;
  text-align:center;
}
.proc-ring{
  width:80px;height:80px;border-radius:50%;
  border:3px solid var(--border2);
  border-top:3px solid var(--accent);
  animation:spin 1s linear infinite;
  margin:0 auto 20px;
}
@keyframes spin{to{transform:rotate(360deg);}}
.proc-title{font-size:18px;font-weight:700;color:var(--text);margin-bottom:8px;}
.proc-sub{font-size:13px;color:var(--text2);}
.proc-steps{margin-top:24px;display:flex;flex-direction:column;gap:8px;max-width:300px;margin-left:auto;margin-right:auto;}
.proc-step{
  display:flex;align-items:center;gap:10px;
  font-size:12px;color:var(--text3);
  opacity:0;animation:fadeStep 0.5s forwards;
}
.proc-step.s1{animation-delay:0.3s;}
.proc-step.s2{animation-delay:0.9s;}
.proc-step.s3{animation-delay:1.5s;}
.proc-step.s4{animation-delay:2.1s;}
@keyframes fadeStep{to{opacity:1;color:#94a3b8;}}
.proc-dot{width:6px;height:6px;border-radius:50%;background:var(--accent);}

/* ═══ REPORT ═══ */
.report{animation:fadeIn 0.5s ease;}

.report-hdr{
  background:var(--surface);
  border:1px solid var(--border);
  border-radius:16px;
  padding:24px 28px;
  margin-bottom:16px;
  display:flex;justify-content:space-between;align-items:center;
}
.report-hdr-left{}
.report-title{font-size:13px;font-weight:700;color:var(--text2);letter-spacing:1px;text-transform:uppercase;margin-bottom:4px;}
.report-name{font-size:22px;font-weight:800;color:var(--text);}
.report-meta{font-size:11px;color:var(--text3);margin-top:4px;}

.verdict-badge{
  padding:14px 20px;border-radius:12px;
  text-align:center;min-width:160px;
}
.verdict-badge.green{
  background:rgba(34,197,94,0.1);
  border:1px solid rgba(34,197,94,0.3);
}
.verdict-badge.orange{
  background:rgba(249,115,22,0.1);
  border:1px solid rgba(249,115,22,0.3);
}
.verdict-badge.red{
  background:rgba(239,68,68,0.1);
  border:1px solid rgba(239,68,68,0.3);
}
.verdict-icon{font-size:28px;margin-bottom:6px;}
.verdict-text{font-size:12px;font-weight:700;letter-spacing:0.5px;}
.verdict-badge.green .verdict-text{color:var(--green);}
.verdict-badge.orange .verdict-text{color:var(--orange);}
.verdict-badge.red .verdict-text{color:var(--red);}

/* ═══ HEATMAP + RADAR ROW ═══ */
.hm-radar-row{display:grid;grid-template-columns:1fr 300px;gap:16px;margin-bottom:16px;}
.heatmap-card{background:var(--surface);border:1px solid var(--border);border-radius:16px;padding:24px 20px;}
.radar-card{background:var(--surface);border:1px solid var(--border);border-radius:16px;padding:24px 16px;display:flex;flex-direction:column;align-items:center;}
.radar-center{display:flex;justify-content:center;align-items:center;flex:1;margin-top:8px;}

/* 4-CELL HEATMAP */
.hm-4grid{display:grid;grid-template-columns:1fr 1fr;gap:10px;margin-top:12px;}
.hm-big-cell{
  border-radius:12px;padding:20px 16px;
  display:flex;flex-direction:column;align-items:center;justify-content:center;
  gap:8px;cursor:default;border:1px solid;
  transition:transform 0.2s,filter 0.2s;min-height:120px;
  position:relative;overflow:hidden;
}
.hm-big-cell:hover{transform:scale(1.03);filter:brightness(1.15);}
.hm-big-cell::after{
  content:'';position:absolute;inset:0;
  background:radial-gradient(circle at 30% 30%,rgba(255,255,255,0.06),transparent 60%);
  pointer-events:none;
}
.hm-big-cell.c-green{background:rgba(34,197,94,0.10);border-color:rgba(34,197,94,0.30);}
.hm-big-cell.c-orange{background:rgba(249,115,22,0.13);border-color:rgba(249,115,22,0.35);}
.hm-big-cell.c-red{background:rgba(239,68,68,0.18);border-color:rgba(239,68,68,0.40);}
.hm-big-icon{font-size:26px;line-height:1;}
.hm-big-name{font-size:12px;font-weight:700;text-align:center;line-height:1.3;}
.hm-big-cell.c-green .hm-big-name{color:#22c55e;}
.hm-big-cell.c-orange .hm-big-name{color:#f97316;}
.hm-big-cell.c-red .hm-big-name{color:#ef4444;}
.hm-big-score{font-size:28px;font-weight:800;line-height:1;}
.hm-big-cell.c-green .hm-big-score{color:#22c55e;text-shadow:0 0 16px rgba(34,197,94,0.5);}
.hm-big-cell.c-orange .hm-big-score{color:#f97316;text-shadow:0 0 16px rgba(249,115,22,0.5);}
.hm-big-cell.c-red .hm-big-score{color:#ef4444;text-shadow:0 0 16px rgba(239,68,68,0.5);}
.hm-big-bar{width:70%;height:4px;border-radius:4px;margin-top:2px;opacity:0.7;}
.hm-big-cell.c-green .hm-big-bar{background:#22c55e;}
.hm-big-cell.c-orange .hm-big-bar{background:#f97316;}
.hm-big-cell.c-red .hm-big-bar{background:#ef4444;}
.hm-big-label{font-size:9px;letter-spacing:1px;font-weight:600;opacity:0.7;text-transform:uppercase;}
.hm-big-cell.c-green .hm-big-label{color:#22c55e;}
.hm-big-cell.c-orange .hm-big-label{color:#f97316;}
.hm-big-cell.c-red .hm-big-label{color:#ef4444;}

@media(max-width:680px){
  .hm-radar-row{grid-template-columns:1fr;}
  .hm-4grid{grid-template-columns:1fr 1fr;}
}


/* HEATMAP */
.heatmap-card{
  background:var(--surface);border:1px solid var(--border);
  border-radius:16px;padding:24px 28px;margin-bottom:16px;
}
.hm-legend{display:flex;gap:16px;margin-bottom:14px;flex-wrap:wrap;}
.hml{display:flex;align-items:center;gap:6px;font-size:10px;color:var(--text3);}
.hml-dot{width:12px;height:12px;border-radius:3px;}
.hm-grid-wrap{display:flex;flex-direction:column;gap:10px;}

.hm-section-row{
  border:1px solid var(--border2);border-radius:10px;overflow:hidden;
}
.hm-section-header{
  display:flex;align-items:center;gap:10px;
  padding:10px 14px;
  background:rgba(255,255,255,0.03);
  border-bottom:1px solid var(--border);
}
.hm-sec-icon{font-size:14px;}
.hm-sec-name{font-size:12px;font-weight:700;color:var(--text);flex:1;}
.hm-sec-score{font-size:11px;font-weight:600;padding:2px 10px;border-radius:12px;}

.hm-questions-grid{
  display:grid;grid-template-columns:repeat(5,1fr);
  gap:0;
}
.hm-cell{
  padding:10px 8px;
  border-left:1px solid var(--border);
  cursor:pointer;
  transition:all 0.2s;
  position:relative;
  display:flex;flex-direction:column;align-items:center;justify-content:center;
  gap:4px;min-height:68px;
}
.hm-cell:last-child{border-left:none;}
.hm-cell:hover{filter:brightness(1.3);z-index:2;}
.hm-cell.risk-0{background:rgba(34,197,94,0.08);}
.hm-cell.risk-1{background:rgba(34,197,94,0.05);}
.hm-cell.risk-2{background:rgba(249,115,22,0.1);}
.hm-cell.risk-3{background:rgba(249,115,22,0.18);}
.hm-cell.risk-4{background:rgba(239,68,68,0.15);}
.hm-cell.risk-5{background:rgba(239,68,68,0.28);}
.hm-cell-num{font-size:9px;color:var(--text3);font-weight:600;letter-spacing:0.5px;}
.hm-cell-score{font-size:18px;font-weight:800;line-height:1;}
.hm-cell.risk-0 .hm-cell-score,.hm-cell.risk-1 .hm-cell-score{color:#22c55e;}
.hm-cell.risk-2 .hm-cell-score,.hm-cell.risk-3 .hm-cell-score{color:#f97316;}
.hm-cell.risk-4 .hm-cell-score,.hm-cell.risk-5 .hm-cell-score{color:#ef4444;}
.hm-cell-dot{width:6px;height:6px;border-radius:50%;}
.hm-cell.risk-0 .hm-cell-dot,.hm-cell.risk-1 .hm-cell-dot{background:#22c55e;}
.hm-cell.risk-2 .hm-cell-dot,.hm-cell.risk-3 .hm-cell-dot{background:#f97316;}
.hm-cell.risk-4 .hm-cell-dot,.hm-cell.risk-5 .hm-cell-dot{background:#ef4444;}

/* TOOLTIP for heatmap */
.hm-tooltip{
  position:fixed;
  background:#0f1827;border:1px solid #1e3a5a;
  border-radius:10px;padding:10px 14px;
  font-size:11px;color:var(--text2);
  min-width:200px;max-width:260px;
  z-index:999;pointer-events:none;
  opacity:0;transition:opacity 0.15s;
  line-height:1.7;
}
.hm-tooltip.show{opacity:1;}
.hm-tt-title{font-weight:700;color:var(--text);margin-bottom:6px;font-size:12px;}
.hm-tt-ans{color:var(--text2);margin-bottom:4px;}
.hm-tt-score{font-weight:700;}

/* TIMELINE */
.timeline-card{
  background:var(--surface);border:1px solid var(--border);
  border-radius:16px;padding:24px 28px;margin-bottom:16px;
}
.timeline-wrap{position:relative;padding-right:20px;}
.timeline-wrap::before{
  content:'';position:absolute;
  right:6px;top:0;bottom:0;
  width:2px;background:linear-gradient(to bottom,var(--accent),transparent);
  border-radius:2px;
}
.tl-item{
  display:grid;grid-template-columns:1fr 100px;
  gap:12px;align-items:center;
  padding:9px 0 9px 0;
  border-bottom:1px solid rgba(30,42,58,0.5);
  position:relative;
}
.tl-item:last-child{border-bottom:none;}
.tl-item::before{
  content:'';position:absolute;
  right:-14px;top:50%;transform:translateY(-50%);
  width:8px;height:8px;border-radius:50%;
  border:2px solid var(--bg);
}
.tl-left{}
.tl-qnum{font-size:9px;color:var(--text3);letter-spacing:1px;font-weight:600;margin-bottom:3px;}
.tl-qtext{font-size:11px;color:var(--text2);line-height:1.4;}
.tl-ans{font-size:10px;color:var(--text3);margin-top:3px;font-style:italic;}
.tl-badge{
  text-align:center;font-size:11px;font-weight:700;
  padding:4px 10px;border-radius:20px;
  white-space:nowrap;
}

@media(max-width:680px){
  .score-radar-row{grid-template-columns:1fr;}
  .hm-questions-grid{grid-template-columns:repeat(3,1fr);}
  .score-section-inner{grid-template-columns:1fr;text-align:center;}
  .gauge-wrap{margin:0 auto;}
}


.gauge-wrap{display:flex;flex-direction:column;align-items:center;gap:8px;}
.gauge{
  width:120px;height:120px;border-radius:50%;
  border:4px solid;
  display:flex;flex-direction:column;align-items:center;justify-content:center;
  background:radial-gradient(circle,#1a1f2e 60%,#0f1623 100%);
}
.gauge.green{border-color:var(--green);box-shadow:0 0 24px rgba(34,197,94,0.3),inset 0 0 16px rgba(34,197,94,0.08);}
.gauge.orange{border-color:var(--orange);box-shadow:0 0 24px rgba(249,115,22,0.3),inset 0 0 16px rgba(249,115,22,0.08);}
.gauge.red{border-color:var(--red);box-shadow:0 0 24px rgba(239,68,68,0.3),inset 0 0 16px rgba(239,68,68,0.08);}
.gauge-status{font-size:8px;font-weight:700;letter-spacing:1.5px;}
.gauge.green .gauge-status{color:var(--green);}
.gauge.orange .gauge-status{color:var(--orange);}
.gauge.red .gauge-status{color:var(--red);}
.gauge-score{font-size:32px;font-weight:800;color:var(--text);line-height:1;}
.gauge-max{font-size:10px;color:var(--text3);}
.gauge-label{font-size:11px;color:var(--text3);text-align:center;}

.score-insight{
  padding:18px 20px;border-radius:12px;
}
.score-insight.green{background:rgba(34,197,94,0.06);border:1px solid rgba(34,197,94,0.2);}
.score-insight.orange{background:rgba(249,115,22,0.06);border:1px solid rgba(249,115,22,0.2);}
.score-insight.red{background:rgba(239,68,68,0.06);border:1px solid rgba(239,68,68,0.2);}
.si-title{font-size:11px;font-weight:700;letter-spacing:1px;margin-bottom:8px;}
.score-insight.green .si-title{color:var(--green);}
.score-insight.orange .si-title{color:var(--orange);}
.score-insight.red .si-title{color:var(--red);}
.si-text{font-size:12px;color:var(--text2);line-height:1.65;}

/* Breakdown */
.breakdown-card{
  background:var(--surface);
  border:1px solid var(--border);
  border-radius:16px;
  padding:24px 28px;
  margin-bottom:16px;
}
.bc-title{
  font-size:10px;font-weight:600;letter-spacing:1.5px;
  color:var(--text3);text-transform:uppercase;
  margin-bottom:16px;padding-bottom:10px;
  border-bottom:1px solid var(--border);
}
.brow{
  display:grid;
  grid-template-columns:28px 1fr 140px 80px;
  align-items:center;gap:12px;
  padding:10px 0;
  border-bottom:1px solid rgba(30,42,58,0.5);
}
.brow:last-child{border-bottom:none;}
.brow-icon{font-size:14px;text-align:center;}
.brow-label{font-size:12px;color:var(--text);}
.bar-wrap{background:#060b14;border-radius:4px;height:6px;overflow:hidden;}
.bar-fill{height:100%;border-radius:4px;transition:width 1s cubic-bezier(0.4,0,0.2,1);}
.bar-fill.green{background:var(--green);box-shadow:0 0 6px rgba(34,197,94,0.5);}
.bar-fill.orange{background:var(--orange);box-shadow:0 0 6px rgba(249,115,22,0.5);}
.bar-fill.red{background:var(--red);box-shadow:0 0 6px rgba(239,68,68,0.5);}
.brow-badge{
  font-size:10px;font-weight:600;
  padding:3px 10px;border-radius:20px;
  text-align:center;
}
.bb-green{background:rgba(34,197,94,0.12);color:var(--green);border:1px solid rgba(34,197,94,0.25);}
.bb-orange{background:rgba(249,115,22,0.12);color:var(--orange);border:1px solid rgba(249,115,22,0.25);}
.bb-red{background:rgba(239,68,68,0.12);color:var(--red);border:1px solid rgba(239,68,68,0.25);}

/* Findings */
.findings-card{
  background:var(--surface);
  border:1px solid var(--border);
  border-radius:16px;
  padding:24px 28px;
  margin-bottom:16px;
}
.finding{
  display:flex;gap:10px;align-items:flex-start;
  padding:10px 0;
  border-bottom:1px solid rgba(30,42,58,0.5);
  font-size:12px;color:var(--text2);line-height:1.6;
}
.finding:last-child{border-bottom:none;}
.finding-dot{
  width:6px;height:6px;border-radius:50%;
  flex-shrink:0;margin-top:5px;
}

/* Print */
@media print{
  body{background:#fff!important;color:#111!important;}
  body::before,body::after{display:none;}
  .hdr,.progress-wrap,.q-nav,.start-btn{display:none!important;}
  .screen:not(.active){display:none!important;}
}

/* Mobile */
@media(max-width:600px){
  .score-section{grid-template-columns:1fr;text-align:center;}
  .gauge-wrap{margin:0 auto;}
  .instructions-grid{grid-template-columns:1fr;}
  .brow{grid-template-columns:28px 1fr 80px;}
  .brow-badge{display:none;}
  .report-hdr{flex-direction:column;gap:16px;}
}

.confidential-bar{
  background:rgba(239,68,68,0.06);
  border:1px solid rgba(239,68,68,0.2);
  border-radius:8px;
  padding:8px 16px;
  font-size:10px;color:rgba(239,68,68,0.7);
  letter-spacing:2px;font-weight:600;
  text-align:center;margin-bottom:16px;
}
</style>
</head>
<body>
<div class="wrap">

  <!-- HEADER -->
  <div class="hdr">
    <div class="logo">
      <div class="logo-icon">🛡️</div>
      <div>
        <div class="logo-text">GateKeeper</div>
        <div class="logo-sub">Financial Integrity System</div>
      </div>
    </div>
    <div class="hdr-badge">מבדק <span>פיננסי</span> | v2.1</div>
  </div>

  <!-- PROGRESS -->
  <div class="progress-wrap" id="progressWrap" style="display:none;">
    <div class="progress-info">
      <div class="progress-label">התקדמות המבדק</div>
      <div class="progress-count" id="progressCount">שאלה 1 מתוך 15</div>
    </div>
    <div class="progress-track"><div class="progress-fill" id="progressFill"></div></div>
    <div class="section-dots" id="sectionDots">
      <div class="sdot" id="dot0"></div>
      <div class="sdot" id="dot1"></div>
      <div class="sdot" id="dot2"></div>
      <div class="sdot" id="dot3"></div>
    </div>
  </div>

  <!-- ══════════════ INTRO SCREEN ══════════════ -->
  <div class="screen active" id="screenIntro">
    <div class="intro-card">
      <div class="intro-top">
        <div class="intro-badge"><div class="pulse"></div>מבדק מאובטח ומוצפן</div>
        <div class="intro-title">מבדק <span>אמינות פיננסית</span><br>GateKeeper</div>
        <div class="intro-sub">הערכה ממוחשבת לניתוח פרופיל סיכון פיננסי — סודי ומקצועי</div>
      </div>

      <div class="intro-body">

        <div class="intro-section">
          <div class="intro-section-title">כמה מילים לפני שמתחילים</div>
          <div class="intro-text">
            <p>אנחנו יודעים שמילוי שאלון מסוג זה לא תמיד נוח. כולנו עברנו תקופות מאתגרות, קיבלנו החלטות פיננסיות שהיינו עושים אחרת היום, ולפעמים החיים פשוט הפתיעו אותנו.</p>
            <p><strong>אנחנו לא מממנים עבר. אנחנו מממנים אדם.</strong> ואדם שמסוגל להביט בכנות על עברו — הוא בדיוק סוג האדם שאנחנו רוצים לעבוד איתו.</p>
          </div>
        </div>

        <div class="alert-box">
          <div class="alert-icon">⚡</div>
          <div class="alert-text">
            <strong>חשוב לדעת:</strong> מבדק זה הינו חלק ממערכת הערכה רחבה יותר. בנוסף לתשובותיך, אנו מבצעים בדיקות עצמאיות ממקורות מידע פיננסיים מוסדיים. היסטוריית אשראי, חשבונות מוגבלים, הסדרי חוב ודפוסי התנהלות פיננסית — נגישים ומתועדים. <strong>עדיף שנשמע ממך על קושי שעברת, מאשר שנגלה אותו בעצמנו.</strong>
          </div>
        </div>

        <div class="trust-box">
          <div class="alert-icon">✅</div>
          <div class="trust-text">
            מועמדים שבחרו בשקיפות מלאה וסיפקו הקשר למצבים מורכבים — זכו לאמון גבוה יותר ולהחלטות חיוביות יותר. <strong>ניסיון חיים, קשיים פיננסיים ואף כישלונות בעבר אינם מחסום — כאשר מוצגים בכנות.</strong>
          </div>
        </div>

        <div class="intro-section" style="margin-top:22px;">
          <div class="intro-section-title">הוראות מילוי</div>
          <div class="instructions-grid">
            <div class="inst-item">
              <div class="inst-num">1</div>
              <div class="inst-txt">קרא כל שאלה בעיון לפני שאתה בוחר תשובה</div>
            </div>
            <div class="inst-item">
              <div class="inst-num">2</div>
              <div class="inst-txt">בחר את התשובה המתארת בצורה הכנה ביותר את מצבך</div>
            </div>
            <div class="inst-item">
              <div class="inst-num">3</div>
              <div class="inst-txt">אין תשובות נכונות או שגויות — יש רק תשובות כנות</div>
            </div>
            <div class="inst-item">
              <div class="inst-num">4</div>
              <div class="inst-txt">זמן מילוי משוער: כ־10 דקות | 15 שאלות בסך הכל</div>
            </div>
          </div>
        </div>

        <div class="intro-section">
          <div class="intro-section-title">נושאי המבדק</div>
          <div class="sections-preview">
            <div class="sec-tag"><div class="sec-tag-dot" style="background:#38bdf8;"></div>רקע פיננסי (5 שאלות)</div>
            <div class="sec-tag"><div class="sec-tag-dot" style="background:#a78bfa;"></div>מוסר ומצפון (5 שאלות)</div>
            <div class="sec-tag"><div class="sec-tag-dot" style="background:#34d399;"></div>יכולת החזר (3 שאלות)</div>
            <div class="sec-tag"><div class="sec-tag-dot" style="background:#fb923c;"></div>גורמי לחץ (2 שאלות)</div>
          </div>
        </div>

        <button class="start-btn" onclick="startAssessment()">
          <span>התחל במבדק</span>
          <span>←</span>
        </button>

      </div>
    </div>
  </div>

  <!-- ══════════════ QUESTION SCREEN ══════════════ -->
  <div class="screen" id="screenQuestion">
    <div class="q-section-header">
      <div class="q-section-tag" id="qSectionTag">חלק א'</div>
      <div class="q-section-name" id="qSectionName">רקע פיננסי</div>
    </div>

    <div class="q-card">
      <div class="q-num" id="qNum">שאלה 1 מתוך 15</div>
      <div class="q-text" id="qText"></div>
      <div class="options" id="optionsWrap"></div>
      <div class="q-nav">
        <button class="btn-prev" id="btnPrev" onclick="prevQuestion()" disabled>→ חזור</button>
        <button class="btn-next" id="btnNext" onclick="nextQuestion()" disabled>המשך ←</button>
      </div>
      <div class="skip-note">לא ניתן לחזור לאחר מעבר לשאלה הבאה</div>
    </div>
  </div>

  <!-- ══════════════ PROCESSING ══════════════ -->
  <div class="screen" id="screenProcessing">
    <div class="processing">
      <div class="proc-ring"></div>
      <div class="proc-title">מעבד את תשובותיך...</div>
      <div class="proc-sub">המערכת מנתחת את פרופיל הסיכון הפיננסי</div>
      <div class="proc-steps">
        <div class="proc-step s1"><div class="proc-dot"></div>מנתח דפוסי תשובה...</div>
        <div class="proc-step s2"><div class="proc-dot"></div>מחשב ציונים לפי קטגוריה...</div>
        <div class="proc-step s3"><div class="proc-dot"></div>מסנן גורמי סיכון...</div>
        <div class="proc-step s4"><div class="proc-dot"></div>מכין דוח מסכם...</div>
      </div>
    </div>
  </div>

  <!-- ══════════════ REPORT ══════════════ -->
  <div class="screen" id="screenReport">
    <div class="report">

      <div class="confidential-bar">⚠ סודי — לעיני מזמין המבדק בלבד ⚠</div>

      <!-- Header -->
      <div class="report-hdr">
        <div class="report-hdr-left">
          <div class="report-title">דוח מבדק אמינות פיננסית</div>
          <div class="report-name">GateKeeper Financial Report</div>
          <div class="report-meta" id="reportMeta">תאריך: — | מזהה: —</div>
        </div>
        <div class="verdict-badge" id="verdictBadge">
          <div class="verdict-icon" id="verdictIcon">🟢</div>
          <div class="verdict-text" id="verdictText">—</div>
        </div>
      </div>

      <!-- Gauge + Insight -->
      <div class="score-section">
        <div class="gauge-wrap">
          <div class="gauge" id="reportGauge">
            <div class="gauge-status" id="gaugeStatus">—</div>
            <div class="gauge-score" id="gaugeScore">0</div>
            <div class="gauge-max">מתוך 77</div>
          </div>
          <div class="gauge-label">ציון סיכון כולל</div>
        </div>
        <div class="score-insight" id="scoreInsight">
          <div class="si-title" id="siTitle">—</div>
          <div class="si-text" id="siText">—</div>
        </div>
      </div>

      <!-- HEATMAP + RADAR -->
      <div class="hm-radar-row">
        <div class="heatmap-card">
          <div class="bc-title">מפת חום — Risk Heatmap</div>
          <div class="hm-legend">
            <div class="hml"><div class="hml-dot" style="background:rgba(34,197,94,0.18);border:1px solid #22c55e50;"></div>תקין</div>
            <div class="hml"><div class="hml-dot" style="background:rgba(249,115,22,0.18);border:1px solid #f9731650;"></div>בירור</div>
            <div class="hml"><div class="hml-dot" style="background:rgba(239,68,68,0.25);border:1px solid #ef444450;"></div>סיכון</div>
          </div>
          <div id="heatmapGrid" class="hm-4grid"></div>
        </div>
        <div class="radar-card">
          <div class="bc-title">פרופיל סיכון — Radar</div>
          <div class="radar-center"><canvas id="radarCanvas" width="260" height="260"></canvas></div>
        </div>
      </div>

      <!-- DUMMY score-radar-row placeholder so old refs don't break -->
      <div class="score-radar-row" style="display:none">
      </div><!-- /score-radar-row hidden -->

      <!-- Findings -->
      <div class="findings-card" id="findingsCard" style="display:none;">
        <div class="bc-title">ממצאים עיקריים — Key Findings</div>
        <div id="findingsList"></div>
      </div>

    </div>
  </div>

</div><!-- /wrap -->

<script>
// ═══════════════════════════════════════════
//  DATA — 15 QUESTIONS
// ═══════════════════════════════════════════
const SECTIONS = [
  { tag:"חלק א'", name:"רקע פיננסי", icon:"💳", color:"#38bdf8" },
  { tag:"חלק ב'", name:"מוסר ומצפון", icon:"⚖️", color:"#a78bfa" },
  { tag:"חלק ג'", name:"יכולת החזר ותכנון", icon:"📊", color:"#34d399" },
  { tag:"חלק ד'", name:"גורמי לחץ חיצוניים", icon:"🔴", color:"#fb923c" }
];

const QUESTIONS = [
  // SECTION 0 — רקע פיננסי
  {
    s:0, text:"האם נדרשת בעבר להחזיר הלוואה שלא עמדת בתנאי הפירעון שלה?",
    opts:["מעולם לא","פעם אחת בנסיבות חריגות","פעמיים או יותר"],
    scores:[0,2,5]
  },
  {
    s:0, text:"האם חשבון הבנק שלך היה מוגבל או מעוקל בעשר השנים האחרונות?",
    opts:["לא","כן, פעם אחת","כן, יותר מפעם אחת"],
    scores:[0,3,6]
  },
  {
    s:0, text:"האם צברת חובות לרשויות (מס הכנסה, ביטוח לאומי, עירייה)?",
    opts:["לא","חוב קטן שסולק","חוב פעיל שטרם סולק"],
    scores:[0,1,5]
  },
  {
    s:0, text:"האם הגשת בעבר בקשה לפשיטת רגל או הסדר נושים?",
    opts:["לא","שקלתי אך לא הגשתי","כן"],
    scores:[0,2,7]
  },
  {
    s:0, text:"האם ההלוואה הנוכחית היא לצורך פירעון הלוואה קיימת אחרת (גלגול חוב)?",
    opts:["לא","חלקית","כן, בעיקר לכך"],
    scores:[0,3,6]
  },
  // SECTION 1 — מוסר ומצפון
  {
    s:1, text:"אם היית נקלע לקושי כלכלי זמני, מה הייתה תגובתך הראשונה?",
    opts:["פונה לבנק או יועץ להסדר מוסדר","מבקש עזרה ממשפחה וחברים","נמנע מלהתמודד עד שיחלוף","מפסיק לשלם ומחכה לראות מה קורה"],
    scores:[0,1,4,7]
  },
  {
    s:1, text:"אם ידעת שהמלווה לא יגלה, האם היית דוחה תשלום שאינך חייב לשלם עכשיו?",
    opts:["לא, אשלם במועד ללא קשר","אולי אבקש דחייה קצרה","כנראה שכן"],
    scores:[0,2,5]
  },
  {
    s:1, text:"כאשר אתה לווה כסף מחבר או בן משפחה, האם אתה מחזיר במועד שנקבע?",
    opts:["תמיד","בדרך כלל, עם עיכובים קלים","לעיתים קרובות מתעכב","לא תמיד מחזיר"],
    scores:[0,2,5,8]
  },
  {
    s:1, text:"האם אתה מאמין שמוסד פיננסי גדול יכול 'לספוג' אי-החזר הלוואה?",
    opts:["לא, יש לי חובה להחזיר ללא קשר לגודל המוסד","אולי, אבל עדיין אחזיר","כן, זה פחות חמור לדעתי"],
    scores:[0,2,6]
  },
  {
    s:1, text:"האם קרה שהצגת מידע לא מדויק בבקשת אשראי או הלוואה בעבר?",
    opts:["לא מעולם","השמטתי פרט אך לא שיקרתי","כן"],
    scores:[0,4,8]
  },
  // SECTION 2 — יכולת החזר
  {
    s:2, text:"מהו יחס ההחזר החודשי של ההלוואה המבוקשת ביחס להכנסתך נטו?",
    opts:["עד 20%","21%–35%","36%–50%","מעל 50%"],
    scores:[0,2,4,7]
  },
  {
    s:2, text:"האם יש לך חיסכון או רזרבה פיננסית שתכסה לפחות 3 חודשי החזר?",
    opts:["כן, בקלות","כן, בקושי","לא"],
    scores:[0,2,5]
  },
  {
    s:2, text:"האם תכננת תקציב חודשי הכולל את ההחזר החדש לפני הגשת הבקשה?",
    opts:["כן, תכנון מפורט","בערך, חישוב כללי","לא"],
    scores:[0,2,4]
  },
  // SECTION 3 — גורמי לחץ
  {
    s:3, text:"מהו המצב המשפחתי-כלכלי שלך כרגע?",
    opts:["יציב, ללא אירועים חריגים","שינוי אחרון (גירושין, ילד חדש, מעבר דירה)","משבר פעיל (אובדן עבודה, מחלה, פרידה)"],
    scores:[0,2,6]
  },
  {
    s:3, text:"האם אתה תחת לחץ חיצוני כלשהו לקחת את ההלוואה הזו (לחץ משפחתי, חוב לאדם פרטי, דחיפות)?",
    opts:["לא, החלטה עצמאית ורגועה","יש קצת לחץ אך ההחלטה שלי","כן, יש לחץ משמעותי"],
    scores:[0,2,6]
  }
];

// Max scores per section for bar % calculation
const SECTION_MAX = [21, 28, 16, 12]; // rough max per section
const SECTION_ICONS = ["💳","⚖️","📊","🔴"];

// State
let current = 0;
let answers = new Array(15).fill(null);
let sectionScores = [0,0,0,0];

// ═══════════════════════════════════════════
function startAssessment(){
  show('screenQuestion');
  document.getElementById('progressWrap').style.display='block';
  renderQuestion();
}

function renderQuestion(){
  const q = QUESTIONS[current];
  const sec = SECTIONS[q.s];

  // Section header
  document.getElementById('qSectionTag').textContent = sec.tag;
  document.getElementById('qSectionTag').style.background = hexToRgba(sec.color,0.1);
  document.getElementById('qSectionTag').style.borderColor = hexToRgba(sec.color,0.3);
  document.getElementById('qSectionTag').style.color = sec.color;
  document.getElementById('qSectionName').textContent = sec.name;

  // Q number
  document.getElementById('qNum').textContent = `שאלה ${current+1} מתוך 15`;

  // Q text
  document.getElementById('qText').textContent = q.text;

  // Options
  const wrap = document.getElementById('optionsWrap');
  wrap.innerHTML = '';
  q.opts.forEach((opt, i) => {
    const div = document.createElement('div');
    div.className = 'option' + (answers[current]===i?' selected':'');
    div.innerHTML = `
      <div class="opt-radio"><div class="opt-check"></div></div>
      <div class="opt-text">${opt}</div>
    `;
    div.onclick = () => selectOption(i);
    wrap.appendChild(div);
  });

  // Progress
  const pct = (current / 15) * 100;
  document.getElementById('progressFill').style.width = pct + '%';
  document.getElementById('progressCount').textContent = `שאלה ${current+1} מתוך 15`;

  // Section dots
  for(let i=0;i<4;i++){
    const dot = document.getElementById('dot'+i);
    const sectionStart = QUESTIONS.findIndex(q=>q.s===i);
    const sectionEnd = QUESTIONS.map(q=>q.s).lastIndexOf(i);
    dot.className = 'sdot';
    if(current > sectionEnd) dot.classList.add('done');
    else if(current >= sectionStart) dot.classList.add('active');
  }

  // Nav buttons
  document.getElementById('btnPrev').disabled = current === 0;
  document.getElementById('btnNext').disabled = answers[current] === null;
  document.getElementById('btnNext').textContent = current===14 ? 'סיים מבדק ✓' : 'המשך ←';
}

function selectOption(i){
  answers[current] = i;
  document.querySelectorAll('.option').forEach((el,idx)=>{
    el.classList.toggle('selected', idx===i);
  });
  document.getElementById('btnNext').disabled = false;
}

function nextQuestion(){
  if(answers[current]===null) return;
  if(current===14){
    finishAssessment();
    return;
  }
  current++;
  renderQuestion();
  window.scrollTo({top:0,behavior:'smooth'});
}

function prevQuestion(){
  if(current===0) return;
  current--;
  renderQuestion();
  window.scrollTo({top:0,behavior:'smooth'});
}

function finishAssessment(){
  show('screenProcessing');
  document.getElementById('progressWrap').style.display='none';
  setTimeout(()=>{
    buildReport();
    show('screenReport');
    animateBars();
  }, 3200);
}

function buildReport(){
  let total = 0;
  sectionScores = [0,0,0,0];
  QUESTIONS.forEach((q,i)=>{
    if(answers[i]!==null){
      const sc = q.scores[answers[i]];
      total += sc;
      sectionScores[q.s] += sc;
    }
  });

  let level, icon, statusText, insightTitle, insightText;
  if(total <= 10){
    level='green'; icon='✅'; statusText='סיכון נמוך';
    insightTitle='לא נמצאו גורמי סיכון מהותיים';
    insightText='פרופיל הנבדק מצביע על התנהלות פיננסית אחראית ויציבה. התשובות עקביות ומשקפות מודעות פיננסית גבוהה. מומלץ לאשר את הבקשה.';
  } else if(total <= 25){
    level='orange'; icon='⚠️'; statusText='מחייב בירור';
    insightTitle='אותרו ממצאים המחייבים בירור נוסף';
    insightText='פרופיל הנבדק מכיל מספר אינדיקטורים הדורשים תשומת לב. מומלץ לקיים שיחת בירור ממוקדת לפני קבלת החלטה סופית.';
  } else {
    level='red'; icon='🚫'; statusText='סיכון גבוה';
    insightTitle='אותרו גורמי סיכון משמעותיים';
    insightText='פרופיל הנבדק מצביע על מספר גורמי סיכון מהותיים. לא מומלץ לאשר את הבקשה בשלב זה ללא בחינה מעמיקה נוספת.';
  }

  // Meta
  const now = new Date();
  document.getElementById('reportMeta').textContent =
    `תאריך: ${now.toLocaleDateString('he-IL')} | מזהה: GK-${Math.random().toString(36).substr(2,8).toUpperCase()}`;

  // Verdict
  document.getElementById('verdictBadge').className = 'verdict-badge '+level;
  document.getElementById('verdictIcon').textContent = icon;
  document.getElementById('verdictText').textContent = statusText;

  // Gauge
  document.getElementById('reportGauge').className = 'gauge '+level;
  document.getElementById('gaugeStatus').textContent = statusText.toUpperCase();
  document.getElementById('gaugeScore').textContent = total;

  // Insight
  const si = document.getElementById('scoreInsight');
  si.className = 'score-insight '+level;
  document.getElementById('siTitle').textContent = insightTitle;
  document.getElementById('siText').textContent = insightText;

  // ══ HEATMAP ══
  buildHeatmap();

  // ══ RADAR ══
  setTimeout(()=>drawRadar(), 100);

  // ══ FINDINGS ══
  const findings = [];
  QUESTIONS.forEach((q,i)=>{
    if(answers[i]!==null && q.scores[answers[i]]>=4){
      findings.push({ q, i, score:q.scores[answers[i]], ans:q.opts[answers[i]] });
    }
  });
  if(findings.length>0){
    document.getElementById('findingsCard').style.display='block';
    const fl = document.getElementById('findingsList');
    fl.innerHTML = '';
    findings.forEach(f=>{
      const col = f.score>=6?'#ef4444':'#f97316';
      fl.innerHTML += `
        <div class="finding">
          <div class="finding-dot" style="background:${col};box-shadow:0 0 6px ${col}50;"></div>
          <div><strong style="color:${col}">ש${f.i+1}:</strong> ${f.q.text}<br>
          <span style="color:#64748b;font-size:11px;">תשובה: "${f.ans}" — ציון: ${f.score}</span></div>
        </div>`;
    });
  }
}

function getRiskClass(score, maxScore){
  const pct = score / maxScore;
  if(pct === 0) return 'risk-0';
  if(pct <= 0.2) return 'risk-1';
  if(pct <= 0.4) return 'risk-2';
  if(pct <= 0.6) return 'risk-3';
  if(pct <= 0.8) return 'risk-4';
  return 'risk-5';
}

function buildHeatmap(){
  const secNames = ['רקע פיננסי','מוסר ומצפון','יכולת החזר','גורמי לחץ'];
  const secColors = ['#38bdf8','#a78bfa','#34d399','#fb923c'];
  const grid = document.getElementById('heatmapGrid');
  grid.innerHTML = '';

  [0,1,2,3].forEach(secIdx=>{
    const sc = sectionScores[secIdx];
    const mx = SECTION_MAX[secIdx];
    const pct = sc / mx;
    let cls = pct<=0.3?'c-green':pct<=0.6?'c-orange':'c-red';
    let lbl = pct<=0.3?'תקין':pct<=0.6?'בירור נדרש':'סיכון גבוה';
    const barW = Math.round(pct*100);

    const cell = document.createElement('div');
    cell.className = 'hm-big-cell ' + cls;
    cell.innerHTML = `
      <div class="hm-big-icon">${SECTION_ICONS[secIdx]}</div>
      <div class="hm-big-name">${secNames[secIdx]}</div>
      <div class="hm-big-score">${sc}<span style="font-size:13px;font-weight:400;opacity:0.5"> / ${mx}</span></div>
      <div class="hm-big-bar" style="width:${barW}%"></div>
      <div class="hm-big-label">${lbl}</div>`;
    grid.appendChild(cell);
  });
}

function drawRadar(){
  const canvas = document.getElementById('radarCanvas');
  if(!canvas) return;
  const ctx = canvas.getContext('2d');
  const W=220, H=220, cx=110, cy=115, R=80;
  const labels = ['רקע\nפיננסי','מוסר\nומצפון','יכולת\nהחזר','גורמי\nלחץ'];
  const pcts = sectionScores.map((sc,i)=>Math.min(1, sc/SECTION_MAX[i]));
  const N=4;
  ctx.clearRect(0,0,W,H);

  // Draw grid rings
  [0.25,0.5,0.75,1].forEach(r=>{
    ctx.beginPath();
    for(let i=0;i<N;i++){
      const angle = (i/N)*Math.PI*2 - Math.PI/2;
      const x = cx + Math.cos(angle)*R*r;
      const y = cy + Math.sin(angle)*R*r;
      i===0?ctx.moveTo(x,y):ctx.lineTo(x,y);
    }
    ctx.closePath();
    ctx.strokeStyle = r===1?'rgba(56,189,248,0.2)':'rgba(30,42,58,0.8)';
    ctx.lineWidth = r===1?1.5:1;
    ctx.stroke();
    // ring label
    if(r<1){
      ctx.fillStyle='rgba(71,85,105,0.6)';
      ctx.font='8px Heebo';
      ctx.textAlign='center';
      ctx.fillText(Math.round(r*100)+'%', cx+4, cy-R*r+3);
    }
  });

  // Draw axes
  for(let i=0;i<N;i++){
    const angle=(i/N)*Math.PI*2-Math.PI/2;
    ctx.beginPath();
    ctx.moveTo(cx,cy);
    ctx.lineTo(cx+Math.cos(angle)*R, cy+Math.sin(angle)*R);
    ctx.strokeStyle='rgba(30,42,58,0.9)';
    ctx.lineWidth=1;
    ctx.stroke();
  }

  // Draw data polygon
  ctx.beginPath();
  pcts.forEach((p,i)=>{
    const angle=(i/N)*Math.PI*2-Math.PI/2;
    const x=cx+Math.cos(angle)*R*p;
    const y=cy+Math.sin(angle)*R*p;
    i===0?ctx.moveTo(x,y):ctx.lineTo(x,y);
  });
  ctx.closePath();
  const maxPct = Math.max(...pcts);
  const fillColor = maxPct>0.6?'rgba(239,68,68,0.18)':maxPct>0.3?'rgba(249,115,22,0.18)':'rgba(34,197,94,0.18)';
  const strokeColor = maxPct>0.6?'#ef4444':maxPct>0.3?'#f97316':'#22c55e';
  ctx.fillStyle=fillColor;
  ctx.fill();
  ctx.strokeStyle=strokeColor;
  ctx.lineWidth=2;
  ctx.shadowColor=strokeColor;
  ctx.shadowBlur=8;
  ctx.stroke();
  ctx.shadowBlur=0;

  // Draw dots
  pcts.forEach((p,i)=>{
    const angle=(i/N)*Math.PI*2-Math.PI/2;
    const x=cx+Math.cos(angle)*R*p;
    const y=cy+Math.sin(angle)*R*p;
    ctx.beginPath();
    ctx.arc(x,y,4,0,Math.PI*2);
    ctx.fillStyle=strokeColor;
    ctx.fill();
    ctx.shadowColor=strokeColor;
    ctx.shadowBlur=10;
    ctx.fill();
    ctx.shadowBlur=0;
  });

  // Labels
  const labelColors=['#38bdf8','#a78bfa','#34d399','#fb923c'];
  labels.forEach((label,i)=>{
    const angle=(i/N)*Math.PI*2-Math.PI/2;
    const lx=cx+Math.cos(angle)*(R+22);
    const ly=cy+Math.sin(angle)*(R+22);
    ctx.fillStyle=labelColors[i];
    ctx.font='bold 9px Heebo';
    ctx.textAlign='center';
    const parts=label.split('\n');
    parts.forEach((p,pi)=>ctx.fillText(p, lx, ly+(pi-parts.length/2+0.5)*12));
  });
}

function buildTimeline(){
  const wrap = document.getElementById('timelineWrap');
  wrap.innerHTML='';
  const dotColors=['#38bdf8','#a78bfa','#34d399','#fb923c'];
  QUESTIONS.forEach((q,i)=>{
    const sc = answers[i]!==null ? q.scores[answers[i]] : 0;
    const ansText = answers[i]!==null ? q.opts[answers[i]] : '—';
    const maxSc = Math.max(...q.scores);
    const pct = sc/(maxSc||1);
    const badgeColor = pct===0?'#22c55e':pct<=0.4?'#34d399':pct<=0.7?'#f97316':'#ef4444';
    const badgeBg = pct===0?'rgba(34,197,94,0.1)':pct<=0.4?'rgba(52,211,153,0.1)':pct<=0.7?'rgba(249,115,22,0.1)':'rgba(239,68,68,0.1)';
    const dotCol = dotColors[q.s];
    const item = document.createElement('div');
    item.className='tl-item';
    item.style.setProperty('--dot-col',dotCol);
    item.innerHTML=`
      <div class="tl-left">
        <div class="tl-qnum">שאלה ${i+1} · ${['רקע פיננסי','מוסר ומצפון','יכולת החזר','גורמי לחץ'][q.s]}</div>
        <div class="tl-qtext">${q.text}</div>
        <div class="tl-ans">"${ansText}"</div>
      </div>
      <div class="tl-badge" style="color:${badgeColor};background:${badgeBg};border:1px solid ${badgeColor}40;">
        ${sc} נק'
      </div>`;
    item.querySelector('::before');
    // set dot color via inline style on ::before via wrapper
    item.style.cssText += `--dot-col:${dotCol}`;
    // manual dot via sibling span
    const dot = document.createElement('span');
    dot.style.cssText=`position:absolute;right:-14px;top:50%;transform:translateY(-50%);width:8px;height:8px;border-radius:50%;background:${dotCol};box-shadow:0 0 6px ${dotCol}80;border:2px solid var(--bg);`;
    item.style.position='relative';
    item.appendChild(dot);
    wrap.appendChild(item);
  });
}

function animateBars(){ /* no-op, kept for compatibility */ }

function show(id){
  document.querySelectorAll('.screen').forEach(s=>s.classList.remove('active'));
  document.getElementById(id).classList.add('active');
}

function hexToRgba(hex,a){
  const r=parseInt(hex.slice(1,3),16);
  const g=parseInt(hex.slice(3,5),16);
  const b=parseInt(hex.slice(5,7),16);
  return `rgba(${r},${g},${b},${a})`;
}
</script>
</body>
</html>


