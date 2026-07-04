# CalisPro
<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>CalisPro — Metodo Completo de Calistenia</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300;400;500;600;700;800&family=DM+Sans:ital,wght@0,300;0,400;0,500;0,600;0,700;1,400&display=swap" rel="stylesheet">
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">
<style>
:root{
  --bg:#09090D;--bg2:#0F0F15;--bg3:#15151D;--bg4:#1B1B26;
  --accent:#FF6B2C;--accent-l:#FF8F5C;--accent-d:#E55A1B;
  --gold:#FFB800;--gold-l:#FFD060;
  --green:#34D399;--blue:#60A5FA;--purple:#C084FC;--pink:#F472B6;--red:#F87171;
  --text:#EAEAF2;--text2:#9494AE;--text3:#5C5C74;
  --border:#222233;--border2:#2E2E42;
  --sidebar-w:260px;--topbar-h:56px;
  --radius:12px;--radius-sm:8px;
  --font-h:'Space Grotesk',sans-serif;--font-b:'DM Sans',sans-serif;
  --ease:cubic-bezier(.4,0,.2,1);
}
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
html{scroll-behavior:smooth}
::-webkit-scrollbar{width:6px}
::-webkit-scrollbar-track{background:var(--bg2)}
::-webkit-scrollbar-thumb{background:var(--border2);border-radius:10px}
::selection{background:rgba(255,107,44,.25);color:#fff}
body{font-family:var(--font-b);background:var(--bg);color:var(--text);min-height:100vh;overflow-x:hidden;-webkit-font-smoothing:antialiased}

.bg-glow{position:fixed;inset:0;z-index:0;pointer-events:none;
  background:radial-gradient(ellipse 70% 50% at 20% 0%,rgba(255,107,44,.04) 0%,transparent 60%),
             radial-gradient(ellipse 50% 40% at 80% 100%,rgba(255,184,0,.03) 0%,transparent 50%)}

#sidebar{position:fixed;left:0;top:0;bottom:0;width:var(--sidebar-w);background:var(--bg2);
  border-right:1px solid var(--border);z-index:200;display:flex;flex-direction:column;
  transition:transform .35s var(--ease);overflow-y:auto;overflow-x:hidden}
.sidebar-head{padding:20px 20px 16px;display:flex;align-items:center;gap:10px;border-bottom:1px solid var(--border)}
.sidebar-logo{font-family:var(--font-h);font-size:1.35rem;font-weight:800;color:var(--accent);letter-spacing:-.03em}
.sidebar-logo span{color:var(--text);font-weight:400}
.nav-group{padding:12px 0 4px}
.nav-group-title{padding:0 20px 6px;font-size:.65rem;font-weight:700;letter-spacing:.1em;color:var(--text3);text-transform:uppercase}
.nav-item{display:flex;align-items:center;gap:12px;padding:10px 20px;color:var(--text2);
  font-size:.88rem;font-weight:500;cursor:pointer;transition:all .2s var(--ease);border-left:3px solid transparent;text-decoration:none}
.nav-item:hover{color:var(--text);background:rgba(255,255,255,.03)}
.nav-item.active{color:var(--accent);background:rgba(255,107,44,.06);border-left-color:var(--accent)}
.nav-item i{width:20px;text-align:center;font-size:.9rem}
.nav-badge{margin-left:auto;background:var(--accent);color:#fff;font-size:.65rem;
  font-weight:700;padding:2px 7px;border-radius:50px;min-width:20px;text-align:center}
.sidebar-foot{margin-top:auto;padding:16px 20px;border-top:1px solid var(--border)}
.user-level{display:flex;justify-content:space-between;font-size:.78rem;color:var(--text2);margin-bottom:8px}
.user-level strong{color:var(--gold)}
.xp-bar{height:5px;background:var(--bg);border-radius:10px;overflow:hidden}
.xp-bar-fill{height:100%;width:0%;background:linear-gradient(90deg,var(--accent-d),var(--accent),var(--gold));border-radius:10px;transition:width .8s var(--ease)}

#overlay{position:fixed;inset:0;background:rgba(0,0,0,.6);z-index:190;opacity:0;pointer-events:none;transition:opacity .3s var(--ease)}
#overlay.show{opacity:1;pointer-events:auto}

#topbar{position:fixed;top:0;left:0;right:0;height:var(--topbar-h);background:rgba(9,9,13,.92);
  backdrop-filter:blur(12px);border-bottom:1px solid var(--border);z-index:180;
  display:none;align-items:center;padding:0 16px;gap:12px}
#menuBtn{background:none;border:none;color:var(--text);font-size:1.2rem;cursor:pointer;padding:4px}
.topbar-title{font-family:var(--font-h);font-weight:700;font-size:1rem;color:var(--accent)}
.topbar-xp{margin-left:auto;font-size:.75rem;font-weight:600;color:var(--gold);background:rgba(255,184,0,.1);
  padding:4px 10px;border-radius:50px}

#main{margin-left:var(--sidebar-w);min-height:100vh;position:relative;z-index:1}
.section{display:none;padding:32px 36px 60px;max-width:960px;margin:0 auto;animation:fadeUp .4s var(--ease)}
.section.active{display:block}
@keyframes fadeUp{from{opacity:0;transform:translateY(14px)}to{opacity:1;transform:translateY(0)}}

h1{font-family:var(--font-h);font-size:clamp(1.8rem,4vw,2.6rem);font-weight:800;line-height:1.1;letter-spacing:-.03em;margin-bottom:12px}
h2{font-family:var(--font-h);font-size:clamp(1.2rem,3vw,1.5rem);font-weight:700;letter-spacing:-.02em;margin-bottom:8px}
h3{font-family:var(--font-h);font-size:1.05rem;font-weight:600;margin-bottom:6px}
.subtitle{color:var(--text2);font-size:.95rem;line-height:1.6;margin-bottom:24px}
.highlight{color:var(--accent)}
.gold{color:var(--gold)}

.card{background:var(--bg3);border:1px solid var(--border);border-radius:var(--radius);padding:20px;transition:all .25s var(--ease)}
.card:hover{border-color:var(--border2);transform:translateY(-2px)}
.card-grid{display:grid;gap:14px}
.card-grid--2{grid-template-columns:1fr 1fr}
.card-grid--3{grid-template-columns:repeat(3,1fr)}
.card-grid--4{grid-template-columns:repeat(4,1fr)}
.card-icon{width:44px;height:44px;border-radius:10px;display:flex;align-items:center;justify-content:center;font-size:1.1rem;margin-bottom:12px;flex-shrink:0}
.card-title{font-family:var(--font-h);font-weight:600;font-size:.95rem;margin-bottom:4px}
.card-desc{font-size:.82rem;color:var(--text2);line-height:1.5}

.btn{display:inline-flex;align-items:center;justify-content:center;gap:8px;font-family:var(--font-h);
  font-weight:600;border:none;border-radius:var(--radius-sm);cursor:pointer;padding:12px 24px;
  font-size:.9rem;transition:all .25s var(--ease);text-decoration:none}
.btn-primary{background:linear-gradient(135deg,var(--accent-d),var(--accent));color:#fff;
  box-shadow:0 4px 16px rgba(255,107,44,.25)}
.btn-primary:hover{transform:translateY(-2px);box-shadow:0 6px 24px rgba(255,107,44,.35)}
.btn-sm{padding:8px 16px;font-size:.8rem;border-radius:var(--radius-sm)}
.btn-outline{background:transparent;border:1.5px solid var(--border);color:var(--text)}
.btn-outline:hover{border-color:var(--accent);color:var(--accent)}
.btn-gold{background:linear-gradient(135deg,#D4A000,var(--gold));color:#1a1400;font-weight:700;
  box-shadow:0 4px 16px rgba(255,184,0,.2)}
.btn-gold:hover{transform:translateY(-2px);box-shadow:0 6px 24px rgba(255,184,0,.3)}
.btn-ghost{background:rgba(255,255,255,.04);color:var(--text2);border:1px solid var(--border)}
.btn-ghost:hover{background:rgba(255,255,255,.08);color:var(--text)}
.btn:disabled{opacity:.35;cursor:not-allowed;transform:none!important;box-shadow:none!important}

.hero{position:relative;padding:60px 0 40px;text-align:center;overflow:hidden}
.hero::before{content:'';position:absolute;top:-60px;left:50%;transform:translateX(-50%);
  width:500px;height:500px;border-radius:50%;background:radial-gradient(circle,rgba(255,107,44,.08) 0%,transparent 70%);pointer-events:none}
.hero-badge{display:inline-flex;align-items:center;gap:6px;background:rgba(255,107,44,.08);
  border:1px solid rgba(255,107,44,.15);padding:6px 16px;border-radius:50px;font-size:.78rem;
  color:var(--accent-l);font-weight:600;margin-bottom:20px}
.hero h1{margin-bottom:16px}
.hero-stats{display:flex;justify-content:center;gap:32px;margin:32px 0;flex-wrap:wrap}
.hero-stat{text-align:center}
.hero-stat-num{font-family:var(--font-h);font-size:1.8rem;font-weight:800;color:var(--accent)}
.hero-stat-label{font-size:.75rem;color:var(--text3);margin-top:2px}

.progress-circle-wrap{display:flex;flex-direction:column;align-items:center;margin:20px 0}
.progress-circle{position:relative;width:180px;height:180px}
.progress-circle svg{transform:rotate(-90deg)}
.progress-circle-bg{fill:none;stroke:var(--bg);stroke-width:10}
.progress-circle-fill{fill:none;stroke:var(--accent);stroke-width:10;stroke-linecap:round;transition:stroke-dashoffset 1.2s var(--ease)}
.progress-circle-text{position:absolute;inset:0;display:flex;flex-direction:column;align-items:center;justify-content:center}
.progress-circle-pct{font-family:var(--font-h);font-size:2.4rem;font-weight:800;color:var(--text)}
.progress-circle-label{font-size:.78rem;color:var(--text3)}
.stat-cards{display:grid;grid-template-columns:repeat(4,1fr);gap:12px;margin:24px 0}
.stat-card{background:var(--bg3);border:1px solid var(--border);border-radius:var(--radius);padding:16px;text-align:center}
.stat-card-num{font-family:var(--font-h);font-size:1.5rem;font-weight:700}
.stat-card-label{font-size:.72rem;color:var(--text3);margin-top:2px}

.module-item{background:var(--bg3);border:1px solid var(--border);border-radius:var(--radius);
  margin-bottom:12px;overflow:hidden;transition:border-color .25s var(--ease)}
.module-item:hover{border-color:var(--border2)}
.module-item.completed{border-color:rgba(52,211,153,.3)}
.module-header{display:flex;align-items:center;gap:14px;padding:16px 18px;cursor:pointer;transition:background .2s var(--ease)}
.module-header:hover{background:rgba(255,255,255,.02)}
.module-num{width:32px;height:32px;border-radius:8px;display:flex;align-items:center;justify-content:center;
  font-family:var(--font-h);font-size:.8rem;font-weight:700;flex-shrink:0;
  background:var(--bg);color:var(--text3);border:1px solid var(--border);transition:all .3s var(--ease)}
.module-item.completed .module-num{background:rgba(52,211,153,.1);color:var(--green);border-color:rgba(52,211,153,.25)}
.module-title{flex:1;font-weight:600;font-size:.9rem}
.module-chevron{color:var(--text3);transition:transform .3s var(--ease);font-size:.75rem}
.module-item.open .module-chevron{transform:rotate(180deg)}
.module-body{max-height:0;overflow:hidden;transition:max-height .4s var(--ease)}
.module-item.open .module-body{max-height:800px}
.module-content{padding:0 18px 18px}
.video-wrap{position:relative;width:100%;padding-top:56.25%;background:var(--bg);border-radius:var(--radius-sm);overflow:hidden;margin-bottom:14px}
.video-wrap iframe{position:absolute;inset:0;width:100%;height:100%;border:none}
.module-desc{font-size:.85rem;color:var(--text2);line-height:1.6;margin-bottom:14px}
.checklist{list-style:none;display:flex;flex-direction:column;gap:6px;margin-bottom:16px}
.checklist li{display:flex;align-items:center;gap:10px;padding:8px 12px;background:var(--bg);border-radius:var(--radius-sm);
  font-size:.82rem;color:var(--text2);cursor:pointer;transition:all .2s var(--ease);border:1px solid transparent}
.checklist li:hover{background:var(--bg4)}
.checklist li.checked{color:var(--green);border-color:rgba(52,211,153,.15)}
.checklist li.checked .ck-box{background:var(--green);border-color:var(--green);color:#fff}
.ck-box{width:18px;height:18px;border-radius:5px;border:1.5px solid var(--border2);display:flex;
  align-items:center;justify-content:center;font-size:.6rem;flex-shrink:0;transition:all .2s var(--ease);color:transparent}
.module-actions{display:flex;gap:10px;flex-wrap:wrap}

.goal-card{background:var(--bg3);border:1px solid var(--border);border-radius:var(--radius);padding:20px;
  cursor:pointer;transition:all .25s var(--ease);position:relative;overflow:hidden}
.goal-card:hover{border-color:var(--border2);transform:translateY(-2px)}
.goal-card.selected{border-color:var(--accent);box-shadow:0 0 20px rgba(255,107,44,.1)}
.goal-card.selected::after{content:'';position:absolute;top:0;right:0;width:40px;height:40px;
  background:var(--accent);clip-path:polygon(100% 0,0 0,100% 100%)}
.goal-card.selected::before{content:'\f00c';font-family:'Font Awesome 6 Free';font-weight:900;
  position:absolute;top:4px;right:4px;font-size:.55rem;color:#fff;z-index:1}
.goal-icon{font-size:1.6rem;margin-bottom:10px}
.goal-name{font-family:var(--font-h);font-weight:600;font-size:.95rem;margin-bottom:6px}
.goal-meta{font-size:.75rem;color:var(--text3);display:flex;align-items:center;gap:6px}
.goal-detail{max-height:0;overflow:hidden;transition:max-height .4s var(--ease)}
.goal-card.expanded .goal-detail{max-height:300px}
.goal-detail-inner{padding-top:14px;font-size:.82rem;color:var(--text2);line-height:1.6;border-top:1px solid var(--border);margin-top:14px}
.goal-detail-inner ul{list-style:none;margin-top:8px}
.goal-detail-inner li{padding:3px 0;display:flex;align-items:center;gap:6px}
.goal-detail-inner li i{color:var(--accent);font-size:.6rem}

.tabs{display:flex;gap:4px;margin-bottom:20px;background:var(--bg2);border-radius:var(--radius-sm);padding:4px;overflow-x:auto}
.tab-btn{padding:10px 18px;border:none;background:none;color:var(--text3);font-family:var(--font-h);
  font-size:.82rem;font-weight:600;cursor:pointer;border-radius:6px;white-space:nowrap;transition:all .2s var(--ease)}
.tab-btn.active{background:var(--accent);color:#fff}
.tab-panel{display:none;animation:fadeUp .3s var(--ease)}
.tab-panel.active{display:block}
.nutri-grid{display:grid;grid-template-columns:1fr 1fr;gap:12px}
.nutri-card{background:var(--bg3);border:1px solid var(--border);border-radius:var(--radius);padding:16px}
.nutri-card h4{font-family:var(--font-h);font-size:.9rem;font-weight:600;margin-bottom:8px}
.nutri-card p,.nutri-card li{font-size:.82rem;color:var(--text2);line-height:1.6}
.nutri-card ul{list-style:none}
.nutri-card li{padding:3px 0;display:flex;align-items:center;gap:8px}
.nutri-card li i{font-size:.55rem}
.meal-plan{background:var(--bg3);border:1px solid var(--border);border-radius:var(--radius);padding:16px;margin-bottom:12px}
.meal-time{font-family:var(--font-h);font-size:.8rem;font-weight:700;color:var(--accent);margin-bottom:8px;text-transform:uppercase;letter-spacing:.05em}
.meal-items{font-size:.83rem;color:var(--text2);line-height:1.7}

.tip-card{background:var(--bg3);border:1px solid var(--border);border-radius:var(--radius);overflow:hidden;margin-bottom:8px}
.tip-header{display:flex;align-items:center;gap:12px;padding:14px 18px;cursor:pointer;transition:background .2s var(--ease)}
.tip-header:hover{background:rgba(255,255,255,.02)}
.tip-num{font-family:var(--font-h);font-size:.75rem;font-weight:700;color:var(--accent);width:24px}
.tip-title{flex:1;font-weight:600;font-size:.88rem}
.tip-chevron{color:var(--text3);font-size:.7rem;transition:transform .3s var(--ease)}
.tip-card.open .tip-chevron{transform:rotate(180deg)}
.tip-body{max-height:0;overflow:hidden;transition:max-height .4s var(--ease)}
.tip-card.open .tip-body{max-height:400px}
.tip-content{padding:0 18px 18px;font-size:.84rem;color:var(--text2);line-height:1.7}

.cal-grid{display:grid;grid-template-columns:repeat(7,1fr);gap:8px;margin-bottom:20px}
.cal-day{text-align:center}
.cal-day-label{font-size:.7rem;font-weight:700;color:var(--text3);margin-bottom:6px;text-transform:uppercase;letter-spacing:.05em}
.cal-day-card{background:var(--bg3);border:1.5px solid var(--border);border-radius:var(--radius);padding:14px 8px;
  min-height:110px;cursor:pointer;transition:all .25s var(--ease);display:flex;flex-direction:column;align-items:center;gap:6px}
.cal-day-card:hover{border-color:var(--border2)}
.cal-day-card.done{border-color:rgba(52,211,153,.3);background:rgba(52,211,153,.03)}
.cal-day-card.today{border-color:var(--accent)}
.cal-day-card .day-name{font-family:var(--font-h);font-size:.8rem;font-weight:700;color:var(--text2)}
.cal-day-card .day-icon{font-size:1.3rem;color:var(--text3);transition:color .2s var(--ease)}
.cal-day-card.done .day-icon{color:var(--green)}
.cal-day-card .day-status{font-size:.65rem;color:var(--text3);font-weight:600}
.cal-day-card.done .day-status{color:var(--green)}

.evo-form{display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:20px}
.evo-input-wrap{display:flex;flex-direction:column;gap:4px}
.evo-input-wrap label{font-size:.75rem;font-weight:600;color:var(--text3);text-transform:uppercase;letter-spacing:.04em}
.evo-input-wrap input,.evo-input-wrap textarea{background:var(--bg3);border:1.5px solid var(--border);border-radius:var(--radius-sm);
  padding:10px 14px;color:var(--text);font-family:var(--font-b);font-size:.9rem;font-weight:600;
  outline:none;transition:border-color .2s var(--ease);-moz-appearance:textfield;resize:vertical}
.evo-input-wrap input:focus,.evo-input-wrap textarea:focus{border-color:var(--accent)}
.evo-input-wrap input::-webkit-inner-spin-button{-webkit-appearance:none}
.evo-history{width:100%;border-collapse:collapse;margin-top:16px}
.evo-history th,.evo-history td{padding:10px 12px;font-size:.8rem;text-align:left;border-bottom:1px solid var(--border)}
.evo-history th{font-family:var(--font-h);font-weight:600;color:var(--text2);background:var(--bg2);position:sticky;top:0}
.evo-history tr:hover td{background:rgba(255,255,255,.02)}

.quote-card{background:linear-gradient(135deg,rgba(255,107,44,.06),rgba(255,184,0,.04));
  border:1px solid rgba(255,107,44,.12);border-radius:var(--radius);padding:32px;text-align:center;margin-bottom:24px;position:relative}
.quote-card::before{content:'\201C';position:absolute;top:12px;left:20px;font-size:4rem;font-family:Georgia,serif;
  color:rgba(255,107,44,.15);line-height:1}
.quote-text{font-size:1.1rem;font-style:italic;line-height:1.7;color:var(--text);margin-bottom:12px;max-width:500px;margin-left:auto;margin-right:auto}
.quote-author{font-size:.82rem;color:var(--text3);font-weight:600}
.challenge-card{background:var(--bg3);border:1.5px solid var(--gold);border-radius:var(--radius);padding:20px;margin-bottom:24px}
.challenge-card h3{color:var(--gold);display:flex;align-items:center;gap:8px;margin-bottom:8px}
.challenge-card p{font-size:.88rem;color:var(--text2);line-height:1.6;margin-bottom:12px}
.badge-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:12px}
.badge-item{background:var(--bg3);border:1px solid var(--border);border-radius:var(--radius);padding:16px;text-align:center;
  transition:all .25s var(--ease)}
.badge-item.earned{border-color:rgba(255,184,0,.3);background:rgba(255,184,0,.04)}
.badge-item.earned .badge-icon{color:var(--gold);filter:drop-shadow(0 0 8px rgba(255,184,0,.3))}
.badge-item:not(.earned){opacity:.4;filter:grayscale(1)}
.badge-icon{font-size:1.8rem;color:var(--text3);margin-bottom:6px;transition:all .3s var(--ease)}
.badge-name{font-size:.72rem;font-weight:600;color:var(--text2)}

.faq-item{border:1px solid var(--border);border-radius:var(--radius-sm);margin-bottom:8px;overflow:hidden}
.faq-item.open{border-color:var(--border2)}
.faq-q{display:flex;align-items:center;justify-content:space-between;padding:14px 16px;cursor:pointer;
  font-size:.86rem;font-weight:600;color:var(--text);background:none;border:none;width:100%;text-align:left;font-family:var(--font-b)}
.faq-q:hover{color:var(--accent-l)}
.faq-q i{transition:transform .3s var(--ease);color:var(--text3);font-size:.7rem;flex-shrink:0}
.faq-item.open .faq-q i{transform:rotate(180deg);color:var(--accent)}
.faq-a{max-height:0;overflow:hidden;transition:max-height .4s var(--ease)}
.faq-a-inner{padding:0 16px 14px;font-size:.83rem;color:var(--text2);line-height:1.7}
.faq-item.open .faq-a{max-height:300px}
.glossary-table{width:100%;border-collapse:collapse}
.glossary-table th,.glossary-table td{padding:10px 14px;font-size:.82rem;text-align:left;border-bottom:1px solid var(--border)}
.glossary-table th{font-family:var(--font-h);font-weight:600;color:var(--text2);background:var(--bg2)}
.glossary-table td:first-child{color:var(--accent);font-weight:600;white-space:nowrap}
.plan-timeline{position:relative;padding-left:28px;margin:16px 0}
.plan-timeline::before{content:'';position:absolute;left:10px;top:0;bottom:0;width:2px;background:var(--border)}
.plan-phase{position:relative;padding:0 0 24px}
.plan-phase::before{content:'';position:absolute;left:-22px;top:4px;width:12px;height:
