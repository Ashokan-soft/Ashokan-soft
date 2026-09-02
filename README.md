<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<meta name="theme-color" content="#08090d"/>
<meta name="description" content="Ashokan — Full-Stack Web Developer, Angular Specialist, Backend Developer & Real-Time Problem Solver."/>
<title>Ashokan — Full-Stack Developer · Problem Solver</title>

<!-- Fonts & Icons (CDN) -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@700;800&family=Space+Grotesk:wght@400;500;600&family=JetBrains+Mono:wght@400;500;600&display=swap" rel="stylesheet">
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.2/css/all.min.css">

<style>
/* ═══════════════════════════════════════════════════════════════
   ASHOKAN — PORTFOLIO  ·  single-file build
   1. tokens & base      7. workflow        13. design
   2. background         8. projects        14. github activity
   3. cursor             9. problem solver  15. contact
   4. navigation        10. services        16. footer
   5. hero              11. gallery         17. reveal system
   6. about             12. (scenes)        18. reduced motion
   ═══════════════════════════════════════════════════════════════ */

/* ── 1. TOKENS & BASE ─────────────────────────────────────────── */
:root{
  --bg:#08090d; --bg-2:#0c0e14; --bg-3:#10131a;
  --ink:#eef1f6; --muted:#8b93a3; --faint:#5b6370;
  --accent:#6fe3ff; --accent-2:#a8a3ff;
  --ok:#57e6a8; --warn:#ffcf8a; --bad:#ff7a8a;
  --line:rgba(255,255,255,.08); --line-2:rgba(255,255,255,.15);
  --fd:'Syne',sans-serif; --fb:'Space Grotesk',sans-serif; --fm:'JetBrains Mono',monospace;
  --ease:cubic-bezier(.22,1,.36,1);
  --r:18px; --rs:12px;
}
*{margin:0;padding:0;box-sizing:border-box}
html{scroll-behavior:smooth;scroll-padding-top:96px}
body{
  background:var(--bg); color:var(--muted);
  font-family:var(--fb); font-size:16px; line-height:1.75;
  overflow-x:clip; -webkit-font-smoothing:antialiased;
}
::selection{background:var(--accent);color:#062028}
img{display:block;max-width:100%}
a{color:inherit}
:focus-visible{outline:2px solid var(--accent);outline-offset:3px;border-radius:4px}
h1,h2,h3,h4{color:var(--ink);font-weight:700;line-height:1.15}
.mono{font-family:var(--fm)}
.wrap{width:min(1180px,calc(100% - 48px));margin-inline:auto}
main{position:relative;z-index:1}
section{position:relative;padding:clamp(90px,11vw,150px) 0}

/* custom cursor: hide native only when JS enables it */
html.cur, html.cur *{cursor:none!important}

/* ── shared section header ────────────────────────────────────── */
.kicker{display:flex;align-items:center;gap:14px;font-family:var(--fm);font-size:.72rem;font-weight:500;letter-spacing:.3em;text-transform:uppercase;color:var(--muted)}
.kicker b{color:var(--accent);font-weight:600}
.kicker::after{content:"";height:1px;width:64px;background:linear-gradient(90deg,rgba(111,227,255,.55),transparent)}
.sec-title{font-family:var(--fd);font-weight:800;font-size:clamp(2.1rem,4.6vw,3.4rem);line-height:1.05;letter-spacing:-.02em;margin-top:20px}
.sec-title .o{color:transparent;-webkit-text-stroke:1px rgba(238,241,246,.42)}
.sec-sub{margin-top:22px;max-width:46ch;font-size:1.02rem;color:var(--muted)}
.sec-head.split{display:flex;align-items:flex-end;justify-content:space-between;gap:40px;flex-wrap:wrap}

/* glass card base */
.glass{background:linear-gradient(180deg,rgba(255,255,255,.05),rgba(255,255,255,.015));border:1px solid var(--line);border-radius:var(--r);backdrop-filter:blur(14px);-webkit-backdrop-filter:blur(14px)}

/* buttons */
.btn{position:relative;display:inline-flex;align-items:center;gap:12px;padding:15px 28px;border-radius:999px;
  font-family:var(--fm);font-size:.75rem;font-weight:600;letter-spacing:.16em;text-transform:uppercase;text-decoration:none;
  border:1px solid transparent;isolation:isolate;
  transform:translate(var(--mx,0px),var(--my,0px));transition:transform .25s var(--ease),box-shadow .4s var(--ease),border-color .4s,background .4s,color .4s}
.btn i{font-size:.82rem;transition:transform .35s var(--ease)}
.btn-solid{background:var(--ink);color:#0a0c11}
.btn-solid:hover{box-shadow:0 16px 44px -14px rgba(238,241,246,.4)}
.btn-solid:hover i{transform:translate(3px,-3px)}
.btn-ghost{color:var(--ink);border-color:var(--line-2);background:rgba(255,255,255,.02)}
.btn-ghost::before{content:"";position:absolute;inset:0;border-radius:inherit;z-index:-1;
  background:linear-gradient(120deg,rgba(111,227,255,.16),rgba(168,163,255,.12));transform:translateX(-101%);transition:transform .5s var(--ease)}
.btn-ghost:hover{border-color:rgba(111,227,255,.5)}
.btn-ghost:hover::before{transform:none}
.btn-ghost i{color:var(--accent)}
.btn-ghost:hover i{transform:translateX(4px)}

/* ── 2. BACKGROUND ────────────────────────────────────────────── */
.bg{position:fixed;inset:0;z-index:0;pointer-events:none;overflow:hidden}
.bg-grid{position:absolute;inset:-60px;
  background-image:linear-gradient(rgba(255,255,255,.027) 1px,transparent 1px),linear-gradient(90deg,rgba(255,255,255,.027) 1px,transparent 1px);
  background-size:58px 58px;
  -webkit-mask-image:radial-gradient(ellipse 95% 75% at 50% 18%,#000 25%,transparent 78%);
  mask-image:radial-gradient(ellipse 95% 75% at 50% 18%,#000 25%,transparent 78%);
  animation:gridDrift 90s linear infinite}
.blob{position:absolute;border-radius:50%}
.b1{width:58vw;height:58vw;left:-18vw;top:-14vw;background:radial-gradient(circle,rgba(111,227,255,.075),transparent 62%);animation:drift1 26s ease-in-out infinite alternate}
.b2{width:50vw;height:50vw;right:-16vw;top:26%;background:radial-gradient(circle,rgba(168,163,255,.06),transparent 60%);animation:drift2 34s ease-in-out infinite alternate}
.b3{width:44vw;height:44vw;left:8vw;bottom:-20vw;background:radial-gradient(circle,rgba(111,227,255,.045),transparent 60%);animation:drift1 40s ease-in-out infinite alternate-reverse}
#bgParticles{position:absolute;inset:0}
.bg-noise{position:absolute;inset:0;opacity:.04;
  background-image:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='140' height='140'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='2'/%3E%3C/filter%3E%3Crect width='140' height='140' filter='url(%23n)' opacity='0.6'/%3E%3C/svg%3E")}
@keyframes gridDrift{to{transform:translate(58px,58px)}}
@keyframes drift1{to{transform:translate(6vw,4vw) scale(1.08)}}
@keyframes drift2{to{transform:translate(-5vw,6vw) scale(1.1)}}

/* ── 3. CUSTOM CURSOR ─────────────────────────────────────────── */
.cursor-dot,.cursor-ring,.cursor-glow{position:fixed;top:0;left:0;pointer-events:none;z-index:999;opacity:0}
html.cur .cursor-dot,html.cur .cursor-ring,html.cur .cursor-glow{opacity:1}
.cursor-dot{width:6px;height:6px;margin:-3px 0 0 -3px;border-radius:50%;background:var(--accent);scale:1;transition:scale .3s,border-color .3s}
.cursor-ring{width:36px;height:36px;margin:-18px 0 0 -18px;border-radius:50%;border:1px solid rgba(111,227,255,.5);scale:1;transition:scale .35s var(--ease),border-color .35s,background .35s;will-change:translate}
.cursor-ring.big{scale:1.7;border-color:rgba(111,227,255,.9);background:rgba(111,227,255,.05)}
.cursor-ring.big + .cursor-dot{scale:.5}
.cursor-glow{width:520px;height:520px;margin:-260px 0 0 -260px;border-radius:50%;
  background:radial-gradient(circle,rgba(111,227,255,.06),rgba(111,227,255,.02) 40%,transparent 70%)}

/* ── 4. NAVIGATION ────────────────────────────────────────────── */
.nav{position:fixed;top:16px;left:50%;translate:-50% 0;width:min(1180px,calc(100% - 32px));z-index:100}
.nav-inner{display:flex;align-items:center;justify-content:space-between;gap:20px;
  padding:11px 12px 11px 16px;border-radius:999px;border:1px solid transparent;
  transition:padding .45s var(--ease),background .45s,border-color .45s,box-shadow .45s,backdrop-filter .45s}
.nav.scrolled .nav-inner{padding:7px 10px 7px 12px;background:rgba(10,12,17,.72);border-color:var(--line);
  backdrop-filter:blur(18px) saturate(1.4);-webkit-backdrop-filter:blur(18px) saturate(1.4);
  box-shadow:0 14px 40px -18px rgba(0,0,0,.8)}
.brand{display:flex;align-items:center;gap:12px;text-decoration:none}
.brand-mark{width:34px;height:34px;border-radius:11px;display:grid;place-items:center;background:var(--ink);color:#0a0c11;font-family:var(--fd);font-weight:800;font-size:1.05rem;transition:transform .4s var(--ease),border-radius .4s var(--ease)}
.brand:hover .brand-mark{transform:rotate(-6deg);border-radius:9px}
.brand-name{font-family:var(--fm);font-size:.92rem;font-weight:500;color:var(--ink);letter-spacing:.02em}
.brand-dot{width:6px;height:6px;border-radius:50%;background:var(--ok);animation:pulseDot 2.4s ease-in-out infinite}
.nav-links{display:flex;gap:26px;list-style:none}
.nav-link{position:relative;padding:8px 2px;font-size:.87rem;letter-spacing:.04em;color:var(--muted);text-decoration:none;transition:color .3s}
.nav-link::after{content:"";position:absolute;left:0;right:0;bottom:3px;height:1.5px;background:var(--accent);transform:scaleX(0);transform-origin:left;transition:transform .35s var(--ease)}
.nav-link:hover,.nav-link.active{color:var(--ink)}
.nav-link:hover::after,.nav-link.active::after{transform:scaleX(1)}
.nav-cta{padding:10px 20px;font-size:.72rem;color:var(--accent);border-color:rgba(111,227,255,.35)}
.nav-cta:hover{border-color:var(--accent);box-shadow:0 8px 26px -10px rgba(111,227,255,.35)}
.burger{display:none;width:42px;height:42px;border-radius:50%;border:1px solid var(--line-2);background:rgba(255,255,255,.03);
  flex-direction:column;align-items:center;justify-content:center;gap:5px}
.burger span{display:block;width:17px;height:1.5px;background:var(--ink);transition:transform .4s var(--ease)}
body.menu-open .burger span:first-child{transform:translateY(3.3px) rotate(45deg)}
body.menu-open .burger span:last-child{transform:translateY(-3.3px) rotate(-45deg)}

/* mobile overlay menu */
.mob-menu{position:fixed;inset:0;z-index:90;display:flex;flex-direction:column;justify-content:center;padding:100px 32px 40px;
  background:rgba(6,7,10,.86);backdrop-filter:blur(24px);-webkit-backdrop-filter:blur(24px);
  opacity:0;pointer-events:none;transition:opacity .45s var(--ease)}
body.menu-open .mob-menu{opacity:1;pointer-events:auto}
body.menu-open{overflow:hidden}
.mob-menu nav{display:flex;flex-direction:column;gap:6px}
.mob-link{display:flex;align-items:baseline;gap:18px;text-decoration:none;font-family:var(--fd);font-weight:700;font-size:clamp(1.7rem,7vw,2.3rem);color:var(--ink);
  opacity:0;translate:0 26px;transition:opacity .5s var(--ease),translate .5s var(--ease),color .3s;transition-delay:calc(var(--i)*.055s + .1s)}
body.menu-open .mob-link{opacity:1;translate:0 0}
.mob-link span{font-family:var(--fm);font-size:.7rem;color:var(--accent)}
.mob-link:active{color:var(--accent)}
.mob-foot{margin-top:auto;display:flex;align-items:center;gap:18px;padding-top:30px;border-top:1px solid var(--line)}
.mob-foot a{width:44px;height:44px;border-radius:50%;border:1px solid var(--line-2);display:grid;place-items:center;color:var(--muted);text-decoration:none;font-size:.9rem}
.mob-foot .st{font-family:var(--fm);font-size:.68rem;letter-spacing:.12em;color:var(--muted);margin-left:auto;display:flex;align-items:center;gap:8px}
.pdot{width:7px;height:7px;border-radius:50%;background:var(--ok);position:relative;flex:none}
.pdot::after{content:"";position:absolute;inset:-4px;border-radius:50%;border:1px solid rgba(87,230,168,.5);animation:ping 2s var(--ease) infinite}
@keyframes pulseDot{0%,100%{box-shadow:0 0 0 0 rgba(87,230,168,.45)}50%{box-shadow:0 0 0 5px rgba(87,230,168,0)}}
@keyframes ping{0%{transform:scale(.6);opacity:1}100%{transform:scale(1.8);opacity:0}}

/* ── 5. HERO ──────────────────────────────────────────────────── */
.hero{min-height:100vh;min-height:100svh;display:grid;align-items:center;padding:130px 0 100px}
.hero-grid{display:grid;grid-template-columns:1.08fr .92fr;gap:clamp(30px,5vw,72px);align-items:center}
.hero-hello{display:flex;align-items:center;gap:14px;font-family:var(--fm);font-size:.74rem;font-weight:500;letter-spacing:.42em;text-transform:uppercase;color:var(--muted)}
.hero-hello .tick{width:34px;height:1px;background:var(--accent)}
.hero-name{margin:22px 0 10px;font-family:var(--fd);font-weight:800;font-size:clamp(3.2rem,8.6vw,7.2rem);line-height:.95;letter-spacing:-.035em;color:var(--ink)}
.hero-name .ln{display:block;overflow:hidden}
.hero-name .l{display:inline-block}
.hero-name .nd{color:var(--accent)}
.hero-type{display:flex;align-items:center;gap:10px;font-family:var(--fm);font-size:clamp(.92rem,1.6vw,1.08rem);min-height:1.9em;color:var(--ink)}
.hero-type .tp{color:var(--accent);font-weight:600}
.caret{width:9px;height:1.15em;background:var(--accent);animation:blink 1.05s steps(1) infinite}
@keyframes blink{50%{opacity:0}}
.hero-sub{margin:26px 0 38px;max-width:46ch;font-size:clamp(1rem,1.4vw,1.1rem)}
.hero-cta{display:flex;gap:16px;flex-wrap:wrap}

/* staged entrance */
.hr{opacity:0;transform:translateY(26px);transition:opacity 1s var(--ease) var(--d,.1s),transform 1s var(--ease) var(--d,.1s)}
body.loaded .hr{opacity:1;transform:none}
.hero-name .l{transform:translateY(115%);transition:transform .9s var(--ease) calc(var(--i)*.055s + .15s)}
body.loaded .hero-name .l{transform:none}

/* hero visual — orbit system */
.hero-visual{position:relative;width:min(520px,100%);aspect-ratio:1;margin-inline:auto;
  opacity:0;transform:scale(.94);transition:opacity 1.3s var(--ease) .35s,transform 1.3s var(--ease) .35s}
body.loaded .hero-visual{opacity:1;transform:none}
.hv-tilt{position:absolute;inset:0;transform-style:preserve-3d}
.orb{position:absolute;inset:19%;border-radius:50%;
  background:radial-gradient(circle at 36% 30%,rgba(111,227,255,.24),rgba(111,227,255,.05) 45%,transparent 64%),
             radial-gradient(circle at 62% 72%,rgba(168,163,255,.14),transparent 55%);
  animation:orbPulse 7s ease-in-out infinite}
@keyframes orbPulse{0%,100%{transform:scale(1);opacity:.9}50%{transform:scale(1.05);opacity:1}}
.ring{position:absolute;border-radius:50%}
.r1{inset:5%;border:1px dashed rgba(150,160,180,.22);animation:spin 70s linear infinite}
.r2{inset:16%;border:1px dashed rgba(111,227,255,.22);animation:spin 44s linear infinite reverse}
.r3{inset:27%;border:1px solid rgba(255,255,255,.05);animation:spin 100s linear infinite}
@keyframes spin{to{transform:rotate(360deg)}}
.orbit{position:absolute;inset:5%;animation:spin var(--t,30s) linear infinite}
.orbit.o2{inset:16%;--t:38s;animation-direction:reverse}
.orbit.o3{inset:27%;--t:26s}
.orbit .chip{position:absolute;top:0;left:50%;animation:chipRev var(--t,30s) linear infinite;animation-direction:var(--rd,normal)}
.orbit.o2 .chip{--rd:reverse}
@keyframes chipRev{from{transform:translate(-50%,-50%) rotate(0)}to{transform:translate(-50%,-50%) rotate(-360deg)}}
.orbit .chip{display:inline-flex;align-items:center;gap:8px;padding:8px 14px;border-radius:999px;
  background:rgba(12,15,21,.85);border:1px solid var(--line-2);font-family:var(--fm);font-size:.68rem;color:var(--muted);
  box-shadow:0 12px 30px -12px rgba(0,0,0,.8);white-space:nowrap}
.orbit .chip i{color:var(--accent);font-size:.8rem}

/* central code card */
.code-card{position:absolute;left:50%;top:50%;transform:translate(-50%,-47%);width:63%;
  background:rgba(13,16,22,.78);border:1px solid var(--line-2);border-radius:15px;
  backdrop-filter:blur(10px);-webkit-backdrop-filter:blur(10px);
  box-shadow:0 26px 60px -22px rgba(0,0,0,.75),0 0 60px -22px rgba(111,227,255,.28);
  padding:14px 16px 16px;font-family:var(--fm);font-size:clamp(.6rem,1vw,.72rem);line-height:1.75}
.cc-bar{display:flex;align-items:center;gap:6px;padding-bottom:10px;margin-bottom:10px;border-bottom:1px solid var(--line)}
.cc-bar i{width:8px;height:8px;border-radius:50%;background:rgba(255,255,255,.14)}
.cc-bar i:first-child{background:rgba(111,227,255,.6)}
.cc-bar em{margin-left:8px;font-style:normal;font-size:.62rem;color:var(--faint);letter-spacing:.05em}
.cc-code{font-family:var(--fm);white-space:pre;overflow:hidden}
.cc-code .k{color:var(--accent-2)}.cc-code .s{color:#86e5b5}.cc-code .f{color:var(--accent)}
.cc-code .c{color:var(--faint)}.cc-code .t{color:#c9d2e0}
.code-caret{display:inline-block;width:7px;height:.9em;background:var(--accent);vertical-align:-.12em;animation:blink 1.05s steps(1) infinite}

/* floating status pills */
.fc{position:absolute;display:inline-flex;align-items:center;gap:9px;padding:9px 14px;border-radius:999px;
  background:rgba(13,16,22,.82);border:1px solid var(--line-2);font-family:var(--fm);font-size:.66rem;color:var(--muted);
  box-shadow:0 16px 34px -16px rgba(0,0,0,.8);animation:floaty 6.5s ease-in-out infinite;animation-delay:var(--fd2,0s);white-space:nowrap}
.fc i{color:var(--accent)}
.fc-dot{width:7px;height:7px;border-radius:50%;background:var(--ok);animation:pulseDot 2.2s infinite}
.fc1{top:6%;right:-4%;animation-delay:0s}
.fc2{bottom:9%;left:-6%;animation-delay:1.6s}
.fc3{top:44%;left:-11%;animation-delay:3.1s}
@keyframes floaty{0%,100%{transform:translateY(0)}50%{transform:translateY(-11px)}}

/* scroll indicator + side label */
.hero-scroll{position:absolute;bottom:26px;left:50%;translate:-50% 0;display:flex;flex-direction:column;align-items:center;gap:9px;
  font-family:var(--fm);font-size:.62rem;letter-spacing:.34em;text-transform:uppercase;color:var(--faint);transition:opacity .5s}
.hero-scroll.hide{opacity:0}
.mouse{width:24px;height:38px;border:1.5px solid var(--line-2);border-radius:14px;display:flex;justify-content:center;padding-top:7px}
.mouse span{width:3px;height:7px;border-radius:3px;background:var(--accent);animation:wheel 1.9s var(--ease) infinite}
@keyframes wheel{0%{transform:translateY(0);opacity:1}70%{transform:translateY(11px);opacity:0}100%{opacity:0}}
.hero-side{position:absolute;left:20px;bottom:130px;writing-mode:vertical-rl;transform:rotate(180deg);
  font-family:var(--fm);font-size:.62rem;letter-spacing:.42em;text-transform:uppercase;color:var(--faint)}

/* ── 6. ABOUT ─────────────────────────────────────────────────── */
.about-grid{display:grid;grid-template-columns:1fr 1fr;gap:clamp(40px,6vw,90px);margin-top:64px;align-items:start}
.lead{font-size:clamp(1.2rem,2.1vw,1.55rem);line-height:1.55;color:var(--ink);font-weight:500}
.support{margin-top:24px;max-width:44ch}
.about-cards{display:flex;flex-direction:column;gap:18px}
.a-card{padding:26px 28px;transition:transform .4s var(--ease),border-color .4s,box-shadow .4s,background-color .4s}
.a-card:nth-child(2){margin-top:30px}
.a-card:nth-child(3){margin-top:60px}
.a-card:hover{transform:translateY(-6px);border-color:rgba(111,227,255,.4);box-shadow:0 24px 60px -28px rgba(111,227,255,.3)}
.a-top{display:flex;align-items:center;justify-content:space-between;margin-bottom:18px}
.a-ico{width:44px;height:44px;border-radius:13px;display:grid;place-items:center;color:var(--accent);
  background:rgba(111,227,255,.08);border:1px solid rgba(111,227,255,.18);transition:transform .45s var(--ease),background .4s}
.a-card:hover .a-ico{transform:rotate(-8deg) scale(1.06);background:rgba(111,227,255,.14)}
.a-idx{font-family:var(--fm);font-size:.68rem;color:var(--faint);letter-spacing:.2em}
.a-card h3{font-family:var(--fd);font-size:1.25rem;letter-spacing:.02em}
.a-card p{margin-top:10px;font-size:.94rem}

/* stats strip (pattern B — parent reveals, children stagger) */
.stats{display:grid;grid-template-columns:repeat(4,1fr);margin-top:90px;border-top:1px solid var(--line)}
.stat{padding:32px 26px 4px;position:relative;
  opacity:0;translate:0 26px;transition:opacity .7s var(--ease) calc(var(--i)*.1s),translate .7s var(--ease) calc(var(--i)*.1s)}
.stat+.stat::before{content:"";position:absolute;left:0;top:32px;bottom:4px;width:1px;background:var(--line)}
[data-reveal].in .stat{opacity:1;translate:0 0}
.stat-n{display:flex;align-items:baseline;gap:2px;font-family:var(--fd);font-weight:800;font-size:clamp(2.2rem,4vw,3.3rem);color:var(--ink);letter-spacing:-.02em}
.stat-n .suf{color:var(--accent);font-size:.6em}
.stat p{margin-top:6px;font-family:var(--fm);font-size:.7rem;letter-spacing:.16em;text-transform:uppercase;color:var(--muted)}

/* ── 7. SKILLS ────────────────────────────────────────────────── */
.skill-grid{display:grid;grid-template-columns:repeat(12,1fr);gap:18px;margin-top:64px}
.sk-panel{padding:28px 30px 24px;grid-column:span 5;position:relative;overflow:hidden;
  transition:transform .45s var(--ease),border-color .45s,box-shadow .45s}
.sk-panel.w{grid-column:span 7}
.sk-panel:hover{border-color:rgba(111,227,255,.35);box-shadow:0 26px 70px -34px rgba(111,227,255,.28)}
.sk-head{display:flex;align-items:center;gap:14px;padding-bottom:18px;border-bottom:1px solid var(--line)}
.sk-head i{color:var(--accent);font-size:1rem;width:38px;height:38px;border-radius:11px;display:grid;place-items:center;
  background:rgba(111,227,255,.07);border:1px solid rgba(111,227,255,.16);transition:transform .45s var(--ease)}
.sk-panel:hover .sk-head i{transform:rotate(-8deg)}
.sk-idx{font-family:var(--fm);font-size:.66rem;color:var(--faint);letter-spacing:.2em;margin-left:auto}
.sk-head h3{font-family:var(--fd);font-size:1.12rem}
.sk-chips{display:flex;flex-wrap:wrap;gap:10px;margin-top:20px}
.chip-s{display:inline-flex;align-items:center;gap:8px;padding:8px 13px;border-radius:999px;
  border:1px solid var(--line);background:rgba(255,255,255,.02);font-size:.82rem;color:var(--muted);
  transition:transform .3s var(--ease),border-color .3s,background-color .3s,color .3s}
.chip-s i{font-size:.82rem;color:var(--faint);transition:color .3s,transform .3s var(--ease)}
.cdot{width:4px;height:4px;border-radius:50%;background:var(--faint);transition:background .3s,transform .3s}
.chip-s:hover{transform:translateY(-3px);color:var(--ink);border-color:rgba(111,227,255,.5);
  background:linear-gradient(120deg,rgba(111,227,255,.12),rgba(168,163,255,.08))}
.chip-s:hover i{color:var(--accent);transform:rotate(-10deg) scale(1.12)}
.chip-s:hover .cdot{background:var(--accent);transform:scale(1.5)}
.sk-bars{margin-top:22px;display:flex;flex-direction:column;gap:14px}
.bar-top{display:flex;justify-content:space-between;font-family:var(--fm);font-size:.66rem;letter-spacing:.12em;text-transform:uppercase;color:var(--muted);margin-bottom:7px}
.bar-top b{color:var(--accent);font-weight:500}
.bar-track{height:3px;border-radius:99px;background:rgba(255,255,255,.07);overflow:hidden}
.bar-fill{display:block;height:100%;border-radius:99px;background:linear-gradient(90deg,var(--accent),var(--accent-2));
  transform:scaleX(0);transform-origin:left;transition:transform 1.1s var(--ease) .25s}
[data-reveal].in .bar-fill{transform:scaleX(var(--p,.5))}
.sk-note{margin-top:22px;font-family:var(--fm);font-size:.68rem;color:var(--faint)}

/* ── 8. WORKFLOW ("HOW I WORK") ───────────────────────────────── */
.wf{position:relative;max-width:880px;margin:80px auto 0}
.wf-line{position:absolute;left:50%;top:14px;bottom:60px;width:1px;background:rgba(255,255,255,.07)}
.wf-fill{display:block;height:100%;background:linear-gradient(180deg,var(--accent),rgba(168,163,255,.5));
  transform:scaleY(0);transform-origin:top;transition:transform 1.8s var(--ease) .15s}
[data-reveal].in .wf-fill{transform:scaleY(1)}
.wf-step{position:relative;display:grid;grid-template-columns:1fr 1fr;gap:0 70px;padding:34px 0;
  opacity:0;translate:0 34px;transition:opacity .7s var(--ease) calc(var(--i)*.12s),translate .7s var(--ease) calc(var(--i)*.12s)}
[data-reveal].in .wf-step{opacity:1;translate:0 0}
.wf-node{position:absolute;left:50%;top:52px;width:13px;height:13px;margin-left:-6.5px;border-radius:50%;
  background:var(--bg);border:2px solid var(--accent);box-shadow:0 0 14px rgba(111,227,255,.5)}
.wf-num{font-family:var(--fd);font-weight:800;font-size:clamp(2.6rem,5vw,4.4rem);line-height:1;
  color:transparent;-webkit-text-stroke:1px rgba(255,255,255,.17);transition:-webkit-text-stroke-color .4s;align-self:start}
.wf-card{padding:24px 26px;transition:transform .4s var(--ease),border-color .4s}
.wf-card:hover{transform:translateY(-5px);border-color:rgba(111,227,255,.35)}
.wf-card h3{font-family:var(--fd);font-size:1.2rem}
.wf-card p{margin-top:8px;font-size:.92rem}
.wf-step:nth-child(odd) .wf-card{grid-column:1;justify-self:end;text-align:right;max-width:400px}
.wf-step:nth-child(odd) .wf-num{grid-column:2;grid-row:1;justify-self:start;padding-left:14px}
.wf-step:nth-child(even) .wf-card{grid-column:2;grid-row:1;max-width:400px}
.wf-step:nth-child(even) .wf-num{grid-column:1;grid-row:1;justify-self:end;padding-right:14px}
.wf-step:hover .wf-num{-webkit-text-stroke-color:rgba(111,227,255,.55)}

/* ── 9. PROJECTS ──────────────────────────────────────────────── */
.proj-list{margin-top:70px;display:flex;flex-direction:column;gap:90px}
.proj{position:relative;display:grid;grid-template-columns:1.05fr 1fr;gap:clamp(30px,4vw,60px);align-items:center;
  padding:clamp(24px,3vw,44px);border-radius:26px;border:1px solid var(--line);
  background:linear-gradient(180deg,rgba(255,255,255,.028),rgba(255,255,255,.008));
  transition:border-color .5s,box-shadow .5s}
.proj::before{content:"";position:absolute;inset:-1px;border-radius:27px;padding:1px;pointer-events:none;
  background:linear-gradient(135deg,rgba(111,227,255,.55),transparent 32%,transparent 68%,rgba(168,163,255,.45));
  -webkit-mask:linear-gradient(#000 0 0) content-box,linear-gradient(#000 0 0);-webkit-mask-composite:xor;mask-composite:exclude;
  opacity:0;transition:opacity .55s}
.proj:hover{border-color:rgba(111,227,255,.28);box-shadow:0 40px 100px -50px rgba(111,227,255,.35)}
.proj:hover::before{opacity:1}
.proj:nth-child(even){grid-template-columns:1fr 1.05fr}
.proj:nth-child(even) .proj-visual{order:2}
.proj-visual{position:relative;aspect-ratio:16/11;border-radius:19px;border:1px solid var(--line);overflow:hidden;
  transform:perspective(900px) rotateX(0) rotateY(0);transition:transform .3s ease-out,border-color .5s}
.proj-visual:hover{border-color:rgba(111,227,255,.4)}
.pv-inner{position:absolute;inset:0;transition:transform .7s var(--ease)}
.proj:hover .pv-inner{transform:scale(1.035)}
.p-idx{font-family:var(--fm);font-size:.68rem;letter-spacing:.28em;text-transform:uppercase;color:var(--accent)}
.proj h3{font-family:var(--fd);font-weight:800;font-size:clamp(1.6rem,2.6vw,2.15rem);letter-spacing:-.01em;margin:12px 0 12px}
.p-desc{font-size:.98rem}
.csr{list-style:none;margin:24px 0 0}
.csr li{display:grid;grid-template-columns:96px 1fr;gap:16px;padding:11px 2px;border-bottom:1px dashed var(--line);
  transition:padding-left .35s var(--ease),border-color .35s}
.csr li:hover{padding-left:10px;border-bottom-color:rgba(111,227,255,.35)}
.csr span{font-family:var(--fm);font-size:.62rem;letter-spacing:.2em;text-transform:uppercase;color:var(--accent);padding-top:4px}
.csr p{font-size:.88rem;color:var(--muted)}
.tags{display:flex;flex-wrap:wrap;gap:8px;margin-top:22px}
.tags span{font-family:var(--fm);font-size:.66rem;padding:5px 11px;border-radius:6px;color:var(--muted);
  border:1px solid var(--line);background:rgba(255,255,255,.02)}
.p-links{display:flex;gap:14px;margin-top:26px}
.p-btn{display:inline-flex;align-items:center;gap:9px;padding:11px 20px;border-radius:10px;text-decoration:none;
  font-family:var(--fm);font-size:.72rem;font-weight:600;letter-spacing:.1em;text-transform:uppercase;
  transform:translate(var(--mx,0px),var(--my,0px));transition:transform .25s var(--ease),background-color .35s,color .35s,border-color .35s,box-shadow .35s}
.p-btn.solid{background:var(--ink);color:#0a0c11}
.p-btn.solid:hover{box-shadow:0 12px 30px -12px rgba(238,241,246,.35)}
.p-btn.ghost{border:1px solid var(--line-2);color:var(--ink)}
.p-btn.ghost:hover{border-color:var(--accent);color:var(--accent)}

/* project mockups (pure CSS mini-UIs) */
.mock{position:absolute;inset:0;background:linear-gradient(160deg,#0e1219,#0a0d13);font-family:var(--fm)}
.mock .chrome{position:absolute;top:0;left:0;right:0;height:34px;display:flex;align-items:center;gap:6px;padding:0 14px;
  border-bottom:1px solid var(--line);font-size:.6rem;color:var(--faint);background:rgba(255,255,255,.02)}
.mock .chrome em{font-style:normal;margin-left:10px;letter-spacing:.04em;overflow:hidden;white-space:nowrap}
.m-d{width:8px;height:8px;border-radius:50%;background:rgba(255,255,255,.13);flex:none}
.m-d:first-child{background:rgba(111,227,255,.55)}
.live{margin-left:auto;display:inline-flex;align-items:center;gap:6px;color:var(--ok);font-size:.56rem;letter-spacing:.2em}
.live i{width:6px;height:6px;border-radius:50%;background:var(--ok);animation:pulseDot 1.8s infinite}
/* dashboard */
.m-dash{position:absolute;top:34px;left:0;right:0;bottom:0;display:flex;padding:16px;gap:14px}
.m-side{width:64px;display:flex;flex-direction:column;gap:9px;padding-top:4px}
.m-side span{height:7px;border-radius:4px;background:rgba(255,255,255,.07)}
.m-side span:first-child{width:80%;background:rgba(111,227,255,.35)}
.m-main{flex:1;display:flex;flex-direction:column;gap:14px}
.m-stats{display:grid;grid-template-columns:repeat(3,1fr);gap:10px}
.m-stats div{border:1px solid var(--line);border-radius:8px;padding:10px;display:flex;flex-direction:column;gap:7px}
.m-stats span{height:6px;width:55%;border-radius:4px;background:rgba(255,255,255,.09)}
.m-stats b{height:9px;width:70%;border-radius:4px;background:rgba(255,255,255,.2)}
.m-chart{flex:1;border:1px solid var(--line);border-radius:8px;display:flex;align-items:flex-end;gap:7px;padding:14px}
.m-chart span{flex:1;height:calc(var(--h)*1%);border-radius:3px 3px 0 0;
  background:linear-gradient(180deg,rgba(111,227,255,.75),rgba(111,227,255,.15));
  transform:scaleY(.25);opacity:.45;transform-origin:bottom;transition:transform .6s var(--ease) calc(var(--i)*.06s),opacity .6s calc(var(--i)*.06s)}
[data-reveal].in .m-chart span,.proj:hover .m-chart span{transform:scaleY(1);opacity:1}
/* realtime feed */
.m-rt{position:absolute;top:34px;left:0;right:0;bottom:0;display:grid;grid-template-columns:1.15fr 1fr;gap:0}
.m-feed{padding:14px;border-right:1px solid var(--line);display:flex;flex-direction:column;gap:8px;overflow:hidden}
.fr{display:flex;align-items:center;gap:8px;font-size:.58rem;color:var(--muted);padding:7px 9px;border-radius:6px;
  background:rgba(255,255,255,.02);opacity:0;translate:0 8px;transition:opacity .5s var(--ease) calc(var(--i)*.09s),translate .5s var(--ease) calc(var(--i)*.09s)}
[data-reveal].in .fr{opacity:1;translate:0 0}
.fr em{font-style:normal;margin-left:auto;color:var(--faint)}
.fd{width:5px;height:5px;border-radius:50%;flex:none}
.fd.ok{background:var(--ok)}.fd.warn{background:var(--warn)}.fd.bad{background:var(--bad)}
.m-spark{padding:14px;display:flex;flex-direction:column;gap:10px}
.m-spark em{font-style:normal;font-size:.56rem;letter-spacing:.18em;color:var(--faint);text-transform:uppercase}
.m-spark svg{flex:1;width:100%;overflow:visible}
.spark{stroke:var(--accent);fill:none;stroke-width:1.6;stroke-dasharray:1;stroke-dashoffset:1;
  transition:stroke-dashoffset 1.6s var(--ease) .4s}
[data-reveal].in .spark{stroke-dashoffset:0}
.sparkfill{fill:rgba(111,227,255,.08);stroke:none;opacity:0;transition:opacity .8s 1.2s}
[data-reveal].in .sparkfill{opacity:1}
/* gallery mock */
.m-gl{position:absolute;top:34px;left:0;right:0;bottom:0;display:grid;grid-template-columns:repeat(4,1fr);grid-template-rows:repeat(2,1fr);gap:8px;padding:14px}
.gt{border-radius:7px;opacity:0;scale:.85;transition:opacity .5s var(--ease) calc(var(--i)*.07s),scale .5s var(--ease) calc(var(--i)*.07s),filter .5s}
[data-reveal].in .gt{opacity:1;scale:1}
.gt.big{grid-row:span 2}
.proj:hover .gt{filter:brightness(1.18)}

/* ── 10. PROBLEM SOLVER / TERMINAL ────────────────────────────── */
.solver-grid{display:grid;grid-template-columns:1fr 1.05fr;gap:clamp(40px,5vw,80px);align-items:center}
.fix-list{list-style:none;margin-top:30px;display:grid;gap:12px}
.fix-list li{display:flex;align-items:center;gap:14px;font-size:.95rem;color:var(--muted);
  padding:12px 16px;border:1px solid var(--line);border-radius:12px;background:rgba(255,255,255,.02);
  transition:border-color .4s,transform .4s var(--ease),color .4s}
.fix-list li:hover{border-color:rgba(111,227,255,.4);transform:translateX(6px);color:var(--ink)}
.fix-list i{color:var(--ok);font-size:.8rem}
.term{background:rgba(9,11,16,.9);border:1px solid var(--line-2);border-radius:16px;overflow:hidden;
  box-shadow:0 34px 80px -30px rgba(0,0,0,.85),0 0 70px -34px rgba(111,227,255,.3)}
.term-bar{display:flex;align-items:center;gap:7px;padding:13px 16px;border-bottom:1px solid var(--line)}
.term-bar i{width:10px;height:10px;border-radius:50%;background:rgba(255,255,255,.12)}
.term-bar i:nth-child(1){background:rgba(255,122,138,.7)}
.term-bar i:nth-child(2){background:rgba(255,207,138,.7)}
.term-bar i:nth-child(3){background:rgba(87,230,168,.7)}
.term-bar em{font-style:normal;margin-left:10px;font-family:var(--fm);font-size:.68rem;color:var(--faint);letter-spacing:.05em}
.t-replay{margin-left:auto;width:32px;height:32px;border-radius:9px;border:1px solid var(--line);background:none;color:var(--muted);
  display:grid;place-items:center;font-size:.75rem;transform:translate(var(--mx,0px),var(--my,0px));
  transition:transform .25s var(--ease),color .3s,border-color .3s}
.t-replay:hover{color:var(--accent);border-color:rgba(111,227,255,.5)}
.term-body{padding:20px 22px 24px;font-family:var(--fm);font-size:.8rem;line-height:2;min-height:330px}
.tl{white-space:pre-wrap;word-break:break-word;animation:lineIn .35s ease both}
@keyframes lineIn{from{opacity:0;translate:0 6px}}
.tl .pr{color:var(--accent-2)}
.tl.d{color:var(--faint)}
.tl .g{color:var(--ok)}.tl .r{color:var(--bad)}.tl .y{color:var(--warn)}
.tl.ok{color:var(--muted)}
.dots::after{content:"";animation:dots 1.2s steps(1) infinite}
@keyframes dots{0%{content:""}25%{content:"."}50%{content:".."}75%{content:"..."}}
.t-caret{display:inline-block;width:8px;height:14px;background:var(--accent);vertical-align:-2px;animation:blink 1s steps(1) infinite}

/* ── 11. SERVICES — horizontal process track ──────────────────── */
.split-p{max-width:38ch;font-size:.95rem;padding-bottom:6px}
.track-arrows{display:flex;gap:12px;padding-bottom:6px}
.ta{width:46px;height:46px;border-radius:50%;border:1px solid var(--line-2);background:rgba(255,255,255,.03);color:var(--ink);
  display:grid;place-items:center;font-size:.85rem;transform:translate(var(--mx,0px),var(--my,0px));
  transition:transform .25s var(--ease),border-color .3s,color .3s,opacity .3s}
.ta:hover{border-color:var(--accent);color:var(--accent)}
.ta[disabled]{opacity:.3;pointer-events:none}
.track-zone{margin-top:56px}
.track{--over:0;overflow-x:auto;overscroll-behavior-x:contain;scroll-snap-type:x proximity;
  scrollbar-width:none;-webkit-overflow-scrolling:touch}
.track::-webkit-scrollbar{display:none}
.track.drag{cursor:grabbing;user-select:none}
.track-inner{position:relative;display:flex;gap:20px;padding:36px 8px 30px;width:max-content}
.track-linewrap{position:absolute;left:0;right:0;top:53px;height:1px}
.track-line{display:block;height:1px;transform:scaleX(0);transform-origin:left;
  background:linear-gradient(90deg,transparent,rgba(111,227,255,.45) 6%,rgba(255,255,255,.14) 30% 70%,rgba(111,227,255,.45) 94%,transparent);
  transition:transform 1.5s var(--ease) .2s}
[data-reveal].in .track-line{transform:scaleX(1)}
.track-item{flex:0 0 212px;scroll-snap-align:start;position:relative;
  opacity:0;translate:0 30px;transition:opacity .65s var(--ease) calc(var(--i)*.07s),translate .65s var(--ease) calc(var(--i)*.07s)}
[data-reveal].in .track-item{opacity:1;translate:0 0}
.t-node{display:flex;align-items:center;gap:10px;height:12px;margin-left:8px}
.t-dot{width:12px;height:12px;border-radius:50%;background:var(--bg-2);border:2px solid var(--accent);flex:none;
  box-shadow:0 0 12px rgba(111,227,255,.45);transition:transform .35s var(--ease)}
.track-item:hover .t-dot{transform:scale(1.35)}
.t-idx{font-family:var(--fm);font-size:.6rem;color:var(--faint);letter-spacing:.15em}
.t-card{margin-top:22px;padding:20px;border-radius:15px;
  transition:transform .4s var(--ease),border-color .4s,box-shadow .4s}
.track-item:hover .t-card{transform:translateY(-6px);border-color:rgba(111,227,255,.35);box-shadow:0 22px 50px -26px rgba(111,227,255,.3)}
.t-card i{color:var(--accent);font-size:1rem}
.t-card h4{font-family:var(--fd);font-size:.98rem;margin:12px 0 6px}
.t-card p{font-size:.8rem;line-height:1.6}
.track-foot{display:flex;align-items:center;gap:20px;margin-top:6px}
.track-progress{width:170px;height:2px;border-radius:99px;background:rgba(255,255,255,.09);overflow:hidden}
.track-progress span{display:block;height:100%;width:100%;background:linear-gradient(90deg,var(--accent),var(--accent-2));
  transform:scaleX(.06);transform-origin:left;transition:transform .15s linear}
.hint{font-size:.62rem;letter-spacing:.22em;text-transform:uppercase;color:var(--faint)}

/* ── 12. GALLERY (PHOTOGRAPHY + TRAVEL) ───────────────────────── */
.ph-head{display:flex;align-items:flex-end;justify-content:space-between;gap:40px;flex-wrap:wrap}
.tag-pills{display:flex;gap:10px;padding-bottom:6px}
.tag-pills span{font-family:var(--fm);font-size:.66rem;letter-spacing:.16em;text-transform:uppercase;color:var(--muted);
  padding:8px 14px;border-radius:999px;border:1px solid var(--line)}
.ph-grid{display:grid;grid-template-columns:repeat(6,1fr);grid-auto-rows:clamp(130px,19vw,205px);gap:14px;margin-top:56px}
.ph-item{position:relative;border-radius:16px;overflow:hidden;margin:0;
  opacity:0;translate:0 34px;transition:opacity .8s var(--ease) var(--d,0s),translate .8s var(--ease) var(--d,0s)}
[data-reveal].in .ph-item{opacity:1;translate:0 0}
.ph-a{grid-column:span 3;grid-row:span 2}
.ph-b,.ph-c{grid-column:span 3}
.ph-d,.ph-e,.ph-f{grid-column:span 2}
.ph-zoom{position:absolute;inset:0;overflow:hidden;transition:transform .9s var(--ease)}
.ph-item:hover .ph-zoom{transform:scale(1.05)}
.ph-fb{position:absolute;inset:0}
.ph-zoom img{position:absolute;inset:0;width:100%;height:100%;object-fit:cover;
  transform:scale(1.16) translateY(var(--py,0px));
  filter:saturate(.72) brightness(.92);transition:filter .7s}
.ph-item:hover .ph-zoom img{filter:saturate(1.08) brightness(1)}
.no-img .ph-zoom img{display:none}
.ph-item figcaption{position:absolute;left:0;right:0;bottom:0;padding:40px 18px 14px;
  background:linear-gradient(transparent,rgba(5,7,10,.85));
  display:flex;align-items:baseline;justify-content:space-between;gap:12px;
  opacity:.75;transform:translateY(6px);transition:opacity .5s,transform .5s var(--ease)}
.ph-item:hover figcaption{opacity:1;transform:none}
.ph-cap{color:var(--ink);font-size:.92rem;font-weight:500}
.ph-meta{font-family:var(--fm);font-size:.62rem;letter-spacing:.08em;color:var(--muted);white-space:nowrap}

/* ── 13. DESIGNER SECTION ─────────────────────────────────────── */
.dsn-grid{display:grid;grid-template-columns:1fr 1.12fr;gap:clamp(40px,5vw,80px);align-items:center}
.dsn-list{margin-top:38px}
.dsn-item{display:flex;align-items:center;gap:16px;width:100%;padding:17px 6px;background:none;border:none;
  border-bottom:1px solid var(--line);color:var(--muted);cursor:pointer;text-align:left;
  transition:color .3s,padding-left .35s var(--ease);
  opacity:0;translate:0 20px;transition:color .3s,padding-left .35s var(--ease),opacity .6s var(--ease) calc(var(--i)*.07s),translate .6s var(--ease) calc(var(--i)*.07s)}
[data-reveal].in .dsn-item{opacity:1;translate:0 0}
.dsn-item .di-idx{font-family:var(--fm);font-size:.64rem;color:var(--accent);letter-spacing:.15em}
.dsn-item .di-t{flex:1;font-family:var(--fb);font-size:1.04rem;font-weight:500}
.dsn-item > i{opacity:0;transform:translateX(-8px);transition:opacity .35s,transform .35s var(--ease),color .3s;font-size:.8rem}
.dsn-item:hover,.dsn-item.on{color:var(--ink)}
.dsn-item.on{padding-left:12px}
.dsn-item:hover > i,.dsn-item.on > i{opacity:1;transform:none;color:var(--accent)}
.dsn-stage{position:relative;aspect-ratio:16/11.5;overflow:hidden;border-radius:var(--r)}
.stage-chrome{position:absolute;top:0;left:0;right:0;height:38px;z-index:2;display:flex;align-items:center;gap:6px;padding:0 16px;
  border-bottom:1px solid var(--line);background:rgba(255,255,255,.02);font-family:var(--fm);font-size:.62rem;color:var(--faint)}
.stage-chrome em{font-style:normal;margin-left:10px;letter-spacing:.06em}
.stage-body{position:absolute;inset:38px 0 0 0}
.scene{position:absolute;inset:0;padding:26px;opacity:0;translate:0 14px;scale:.985;visibility:hidden;pointer-events:none;
  transition:opacity .5s var(--ease),translate .5s var(--ease),scale .5s var(--ease),visibility .5s}
.scene.is-on{opacity:1;translate:0 0;scale:1;visibility:visible}
/* scene 1 — UI skeleton */
.sk{border-radius:6px;background:rgba(255,255,255,.06);position:relative;overflow:hidden}
.sk::after{content:"";position:absolute;inset:0;transform:translateX(-100%);
  background:linear-gradient(100deg,transparent 25%,rgba(111,227,255,.13) 50%,transparent 75%);
  animation:shimmer 2.8s var(--ease) infinite;animation-delay:var(--sd,0s)}
@keyframes shimmer{to{transform:translateX(100%)}}
.sk-c{width:26px;height:26px;border-radius:50%;flex:none}
.sk-l{height:9px}
.w1{width:70px}.w2{width:110px}.w3{width:150px}.w4{width:190px}
.sk-b{margin-left:auto;width:74px;height:26px;border-radius:7px}
.sc-ui{display:flex;flex-direction:column;gap:16px}
.sk-bar{display:flex;align-items:center;gap:12px;padding:12px 14px}
.sk-hero{display:flex;flex-direction:column;gap:10px;padding:22px 18px}
.sk-hero .sk-b{margin:8px 0 0}
.sk-cards{display:grid;grid-template-columns:repeat(3,1fr);gap:12px;flex:1}
.sk-card{min-height:70px}
/* scene 2 — UX flow */
.sc-ux svg{width:100%;height:100%}
.ux-p{fill:none;stroke:rgba(255,255,255,.2);stroke-width:1.4;stroke-dasharray:5 7;animation:flow 1.4s linear infinite}
@keyframes flow{to{stroke-dashoffset:-24}}
.ux-n{fill:#0d1017;stroke:rgba(111,227,255,.55);stroke-width:1.4}
.ux-c{fill:var(--accent)}
.ux-pulse{transform-box:fill-box;transform-origin:center;animation:nodePulse 2.2s var(--ease) infinite}
@keyframes nodePulse{0%,100%{transform:scale(1)}50%{transform:scale(1.35)}}
/* scene 3 — hierarchy */
.hi-guide{position:absolute;top:26px;bottom:26px;width:1px;border-left:1px dashed rgba(111,227,255,.22)}
.hg1{left:46px}.hg2{right:46px}
.sc-hier{display:flex;flex-direction:column;gap:13px;justify-content:center}
.hi-row{display:flex;align-items:center;gap:24px}
.hi-aa{font-family:var(--fd);font-weight:800;font-size:clamp(2rem,4vw,3rem);color:var(--ink)}
.hi-lines{display:flex;flex-direction:column;gap:9px;flex:1}
.hi-l{height:10px;border-radius:5px;background:rgba(255,255,255,.09)}
.hi-l.hl1{width:64%}.hi-l.hl2{width:46%}
.hi-l.hl3{width:82%}.hi-l.hl4{width:62%;height:8px}.hi-l.hl5{width:38%;height:7px;background:rgba(111,227,255,.28)}
/* scene 4 — responsive */
.sc-resp{display:flex;align-items:center;justify-content:center;gap:22px;flex-wrap:wrap}
.rs{display:flex;flex-direction:column;gap:8px;padding:12px;border:1px solid var(--line-2);border-radius:10px;
  transition:border-color .4s,transform .4s var(--ease)}
.rs:hover{border-color:rgba(111,227,255,.5);transform:translateY(-4px)}
.rs span{border-radius:3px;background:rgba(255,255,255,.1)}
.rs span{height:7px}
.rs-d{width:150px}.rs-d span:nth-child(1){width:60%;background:rgba(111,227,255,.4)}
.rs-t{width:82px}.rs-t span:nth-child(1){width:55%;background:rgba(111,227,255,.4)}
.rs-p{width:38px}.rs-p span{height:8px}
.rs-lab{font-family:var(--fm);font-size:.58rem;letter-spacing:.16em;text-transform:uppercase;color:var(--faint)}
/* scene 5 — design to code */
.sc-d2c{display:flex;align-items:center;justify-content:center;gap:26px}
.d2-col{display:flex;flex-direction:column;gap:10px;width:38%}
.d2-col .sk{height:16px}
.d2-col .sk:nth-child(2){width:72%}
.d2-col .sk:nth-child(3){width:52%}
.d2-arrow{display:flex;flex-direction:column;gap:2px}
.d2-arrow i{font-size:1rem;color:var(--muted);opacity:.15;animation:chev 1.6s infinite;animation-delay:calc(var(--i)*.18s)}
@keyframes chev{0%,100%{opacity:.15}35%{opacity:1;color:var(--accent)}}
.d2-code{width:44%;font-family:var(--fm);font-size:.66rem;line-height:2.1;white-space:pre}
.d2-code .k{color:var(--accent-2)}.d2-code .p{color:var(--muted)}.d2-code .v{color:var(--accent)}
/* scene 6 — creative direction */
.sc-cd{display:flex;align-items:center;justify-content:center;gap:18px;flex-wrap:wrap}
.sw-t{display:flex;flex-direction:column;gap:8px;align-items:center}
.sw-t span{width:46px;height:46px;border-radius:13px;background:var(--c);opacity:.85;
  animation:floaty 5s ease-in-out infinite;animation-delay:var(--sd,0s)}
.sw-t.sel span{opacity:1;box-shadow:0 0 0 2px var(--bg),0 0 0 3.5px var(--accent)}
.sw-t em{font-style:normal;font-family:var(--fm);font-size:.56rem;letter-spacing:.14em;text-transform:uppercase;color:var(--faint)}

/* ── 14. GITHUB ACTIVITY ──────────────────────────────────────── */
.gh-card{margin-top:56px;padding:26px clamp(18px,3vw,34px) 22px}
.gh-head{display:flex;align-items:center;justify-content:space-between;gap:16px;flex-wrap:wrap;
  padding-bottom:20px;border-bottom:1px solid var(--line);margin-bottom:22px}
.gh-head .gt-l{display:flex;align-items:center;gap:12px;font-size:.95rem;color:var(--ink);font-weight:500}
.gh-head .gt-l i{color:var(--muted);font-size:1.2rem}
.gh-head .mono{font-size:.7rem;color:var(--muted)}
.gh-head .mono b{color:var(--accent);font-weight:600}
.gh-scroll{display:flex;gap:9px;overflow-x:auto;padding-bottom:8px;scrollbar-width:thin;scrollbar-color:rgba(255,255,255,.14) transparent}
.gh-days{display:grid;grid-template-rows:repeat(7,var(--cs));gap:3.5px;flex:none;
  font-family:var(--fm);font-size:.56rem;color:var(--faint)}
.gh-days span{display:flex;align-items:center}
.gh-days span:empty{visibility:hidden}
.gh-main{display:flex;flex-direction:column;min-width:540px;flex:1}
.gh-months{position:relative;height:14px;margin-bottom:5px;flex:none}
.gh-months span{position:absolute;top:0;font-family:var(--fm);font-size:.56rem;color:var(--faint);translate:-50% 0}
.gh-grid{--cs:12px;display:grid;grid-auto-flow:column;grid-template-rows:repeat(7,var(--cs));grid-auto-columns:var(--cs);gap:3.5px}
.gh-grid .sq{width:var(--cs);height:var(--cs);border-radius:2.5px;opacity:0;transform:scale(.3);
  transition:opacity .2s,transform .2s;outline:1px solid transparent;outline-offset:1px}
.gh-grid.on .sq{animation:ghpop .45s var(--ease) forwards;animation-delay:calc(var(--w)*13ms)}
@keyframes ghpop{to{opacity:1;transform:scale(1)}}
.sq:hover{outline-color:var(--accent)}
.l0{background:#14171d}.l1{background:#0e3a46}.l2{background:#155e6e}.l3{background:#2a9db2}.l4{background:#6fe3ff}
.gh-foot{display:flex;align-items:center;justify-content:space-between;gap:16px;flex-wrap:wrap;margin-top:20px}
.gh-legend{display:flex;align-items:center;gap:4px;font-family:var(--fm);font-size:.62rem;color:var(--faint)}
.gh-legend i{width:10px;height:10px;border-radius:2.5px}
.gh-tip{position:fixed;z-index:300;top:0;left:0;background:#10141b;border:1px solid var(--line-2);border-radius:9px;
  padding:7px 12px;font-family:var(--fm);font-size:.66rem;color:var(--ink);pointer-events:none;white-space:nowrap;
  opacity:0;translate:-50% -140%;transition:opacity .15s;box-shadow:0 12px 30px -10px rgba(0,0,0,.7)}

/* ── 15. CONTACT ──────────────────────────────────────────────── */
.contact-wrap{text-align:center;display:flex;flex-direction:column;align-items:center}
.contact-wrap .kicker{justify-content:center}
.contact-wrap .kicker::before{content:"";height:1px;width:64px;background:linear-gradient(270deg,rgba(111,227,255,.55),transparent)}
.contact-sub{margin-top:22px;max-width:44ch}
.contact-card{position:relative;margin-top:60px;border-radius:26px;padding:1px;overflow:hidden;
  background:rgba(255,255,255,.05);box-shadow:0 34px 100px -46px rgba(111,227,255,.4);width:min(760px,100%)}
.cc-spin{position:absolute;left:50%;top:50%;width:1400px;height:1400px;margin:-700px 0 0 -700px;
  background:conic-gradient(from 0deg,transparent 0deg,transparent 258deg,rgba(111,227,255,.9) 296deg,rgba(168,163,255,.75) 328deg,transparent 360deg);
  animation:spin 8s linear infinite}
.cc-inner{position:relative;border-radius:25px;background:linear-gradient(180deg,#0e1119,#0a0d12);
  padding:clamp(32px,5vw,56px) clamp(24px,4vw,52px);text-align:left}
.cc-status{display:flex;align-items:center;gap:10px;font-family:var(--fm);font-size:.68rem;letter-spacing:.16em;
  text-transform:uppercase;color:var(--muted)}
.cc-status em{font-style:normal;margin-left:auto;color:var(--faint);letter-spacing:.08em;text-transform:none}
.cc-mailrow{display:flex;align-items:center;gap:18px;margin:26px 0 34px;flex-wrap:wrap}
.cc-mail{font-family:var(--fd);font-weight:700;font-size:clamp(1.35rem,3.4vw,2.3rem);letter-spacing:-.01em;color:var(--ink);
  text-decoration:none;background:linear-gradient(var(--accent),var(--accent)) no-repeat 0 100%/0 2px;
  transition:background-size .5s var(--ease),color .35s;padding-bottom:4px}
.cc-mail:hover{color:var(--accent);background-size:100% 2px}
.cc-copy{display:inline-flex;align-items:center;gap:8px;padding:9px 15px;border-radius:999px;border:1px solid var(--line-2);
  background:none;color:var(--muted);font-family:var(--fm);font-size:.66rem;letter-spacing:.14em;text-transform:uppercase;cursor:pointer;
  transform:translate(var(--mx,0px),var(--my,0px));transition:transform .25s var(--ease),color .3s,border-color .3s}
.cc-copy:hover{color:var(--accent);border-color:rgba(111,227,255,.5)}
.cc-copy.ok{color:var(--ok);border-color:rgba(87,230,168,.5)}
.cc-soc{display:grid;grid-template-columns:repeat(auto-fit,minmax(210px,1fr));gap:12px}
.s-btn{display:flex;align-items:center;gap:14px;padding:15px 18px;border-radius:14px;text-decoration:none;
  border:1px solid var(--line);background:rgba(255,255,255,.02);
  transform:translate(var(--mx,0px),var(--my,0px));
  transition:transform .25s var(--ease),border-color .35s,background-color .35s,box-shadow .35s}
.s-btn > i:first-child{width:40px;height:40px;border-radius:11px;display:grid;place-items:center;flex:none;
  color:var(--accent);background:rgba(111,227,255,.07);border:1px solid rgba(111,227,255,.16);font-size:1rem}
.s-btn b{display:block;color:var(--ink);font-size:.9rem;font-weight:500}
.s-btn small{font-family:var(--fm);font-size:.62rem;color:var(--faint)}
.s-btn .go{margin-left:auto;color:var(--faint);font-size:.75rem;transition:transform .35s var(--ease),color .3s}
.s-btn:hover{border-color:rgba(111,227,255,.45);background:rgba(111,227,255,.05);box-shadow:0 18px 44px -22px rgba(111,227,255,.3)}
.s-btn:hover .go{transform:translate(3px,-3px);color:var(--accent)}
.s-btn > div{flex:1;min-width:0}

/* ── 16. FOOTER ───────────────────────────────────────────────── */
footer{position:relative;z-index:1;padding:70px 0 36px;border-top:1px solid var(--line);margin-top:40px}
.foot-status{display:flex;align-items:center;gap:10px;font-family:var(--fm);font-size:.68rem;letter-spacing:.18em;
  text-transform:uppercase;color:var(--muted)}
.foot-motto{margin-top:26px;font-family:var(--fd);font-weight:700;font-size:clamp(1.4rem,3.6vw,2.3rem);
  color:var(--ink);letter-spacing:-.01em}
.foot-motto span{color:var(--accent);padding:0 .35em;font-weight:400}
.foot-meta{display:flex;align-items:center;justify-content:space-between;gap:18px;flex-wrap:wrap;
  margin-top:44px;padding-top:24px;border-top:1px solid var(--line);font-size:.82rem}
.foot-meta strong{color:var(--ink);font-weight:500}
.foot-year{font-family:var(--fm);font-size:.68rem;color:var(--faint)}

/* back to top */
#toTop{position:fixed;right:22px;bottom:22px;z-index:80;width:48px;height:48px;border-radius:50%;border:none;
  background:rgba(12,15,21,.8);backdrop-filter:blur(12px);color:var(--ink);display:grid;place-items:center;font-size:.85rem;
  transform:scale(.6) translate(var(--mx,0px),var(--my,0px));opacity:0;pointer-events:none;
  transition:transform .45s var(--ease),opacity .45s,color .3s}
#toTop.show{transform:scale(1) translate(var(--mx,0px),var(--my,0px));opacity:1;pointer-events:auto}
#toTop:hover{color:var(--accent)}
#toTop::before{content:"";position:absolute;inset:-3px;border-radius:50%;
  background:conic-gradient(var(--accent) calc(var(--sp,0)*1%),rgba(255,255,255,.1) 0);
  -webkit-mask:radial-gradient(farthest-side,transparent calc(100% - 2.5px),#000 calc(100% - 2px));
  mask:radial-gradient(farthest-side,transparent calc(100% - 2.5px),#000 calc(100% - 2px))}

/* ── 17. SCROLL REVEAL (generic, JS-driven — see script) ──────── */

/* ── 18. REDUCED MOTION ───────────────────────────────────────── */
@media (prefers-reduced-motion:reduce){
  html{scroll-behavior:auto}
  *,*::before,*::after{animation-duration:.001s!important;animation-delay:0s!important;transition-duration:.001s!important;transition-delay:0s!important;animation-iteration-count:1!important}
}
/* ── RESPONSIVE ───────────────────────────────────────────────── */
@media (max-width:1200px){.hero-side{display:none}}
@media (max-width:1080px){
  .hero-grid{grid-template-columns:1fr;gap:20px}
  .hero{padding-top:120px}
  .hero-visual{width:min(400px,88vw);margin:36px auto 0}
  .fc3{display:none}
  .about-grid{grid-template-columns:1fr;gap:40px}
  .a-card:nth-child(2),.a-card:nth-child(3){margin-top:0}
  .sk-panel,.sk-panel.w{grid-column:span 12}
  .proj,.proj:nth-child(even){grid-template-columns:1fr}
  .proj:nth-child(even) .proj-visual{order:0}
  .solver-grid{grid-template-columns:1fr;gap:48px}
  .dsn-grid{grid-template-columns:1fr}
  .dsn-stage{order:-1}
}
@media (max-width:860px){
  .nav-links,.nav-cta{display:none}
  .burger{display:flex}
  .stats{grid-template-columns:1fr 1fr}
  .stat+.stat::before{display:none}
  .stat{border-top:1px solid var(--line);margin-top:0;padding-top:26px}
  .stat:nth-child(1),.stat:nth-child(2){border-top:none}
  .wf-line{left:21px}
  .wf-fill{transform-origin:top}
  .wf-step{grid-template-columns:1fr;padding:22px 0 22px 52px}
  .wf-node{left:21px;margin-left:0;top:44px}
  .wf-step:nth-child(odd) .wf-card{grid-column:1;justify-self:start;text-align:left;max-width:none}
  .wf-step:nth-child(odd) .wf-num,.wf-step:nth-child(even) .wf-num{grid-column:1;grid-row:auto;justify-self:start;padding:0 0 6px}
  .wf-num{font-size:2rem;-webkit-text-stroke-color:rgba(111,227,255,.4)}
  .csr li{grid-template-columns:1fr;gap:4px}
  .sec-head.split{flex-direction:column;align-items:flex-start;gap:26px}
}
@media (max-width:640px){
  .wrap{width:calc(100% - 36px)}
  section{padding:80px 0}
  .hero-visual{width:min(320px,90vw)}
  .fc2{display:none}
  .hero-cta .btn{flex:1;justify-content:center}
  .ph-grid{grid-template-columns:1fr 1fr;grid-auto-rows:150px}
  .ph-a{grid-column:span 2;grid-row:span 2}
  .ph-b,.ph-c{grid-column:span 2}
  .ph-d,.ph-e,.ph-f{grid-column:span 1}
  .ph-meta{display:none}
  .gh-grid{--cs:9px}
  .track-item{flex-basis:186px}
  .p-links{flex-wrap:wrap}
  .p-btn{flex:1;justify-content:center}
  .term-body{font-size:.72rem;min-height:360px}
  .sc-d2c{gap:12px}
  .d2-col{width:34%}.d2-code{width:42%;font-size:.56rem}
}
</style>
</head>
<body>

<!-- ╔══════════════════════════════════════════════════════════╗
     ║  EDIT HERE  ·  SITE CONFIGURATION                        ║
     ║  Everything personal lives in this one object.           ║
     ║  Replace the placeholder values marked  ← REPLACE.        ║
     ╚══════════════════════════════════════════════════════════╝ -->
<script>
const CONFIG = {

  /* identity */
  name: 'Ashokan',
  roles: ['Coder','Photographer','Designer','Traveller','Angular Developer','Web Developer','Backend Developer','Real-Time Problem Solver'],
  email: 'hello@ashokan.dev',                    // ← REPLACE with your email

  /* social links (placeholder URLs — replace them) */
  socials: [
    { label:'GitHub',    icon:'fa-brands fa-github',    url:'https://github.com/your-username',      handle:'@your-username' },   // ← REPLACE
    { label:'LinkedIn',  icon:'fa-brands fa-linkedin',  url:'https://linkedin.com/in/your-username', handle:'in/your-username' }, // ← REPLACE
    { label:'Email',     icon:'fa-solid fa-envelope',   url:'mailto:hello@ashokan.dev',              handle:'hello@ashokan.dev' },
    { label:'Instagram', icon:'fa-brands fa-instagram', url:'https://instagram.com/your-handle',     handle:'@your-handle' }     // ← REPLACE
  ],

  /* animated statistics — edit the numbers here */
  stats: [
    { value: 5,  suffix: '+',  label: 'Years Experience' },
    { value: 20, suffix: '+',  label: 'Projects Delivered' },
    { value: 10, suffix: '+',  label: 'Technologies' },
    { value: 24, suffix: '/7', label: 'Problem Solver' }
  ],

  /* skills — grouped panels; icon is any Font Awesome 6 free class */
  skills: [
    { title:'Frontend', icon:'fa-solid fa-code', span:'w', note:'// where pixels meet logic',
      bars:[{label:'Angular',level:95},{label:'TypeScript',level:90},{label:'Responsive UI',level:88}],
      items:[
        {name:'Angular',icon:'fa-brands fa-angular'},{name:'TypeScript'},
        {name:'JavaScript',icon:'fa-brands fa-js'},{name:'HTML5',icon:'fa-brands fa-html5'},
        {name:'CSS3',icon:'fa-brands fa-css3'},{name:'Responsive UI',icon:'fa-solid fa-mobile-screen'}]},
    { title:'Backend', icon:'fa-solid fa-server', note:'// what powers the pixels',
      bars:[{label:'Django',level:88},{label:'Python',level:90}],
      items:[
        {name:'Django'},{name:'Python',icon:'fa-brands fa-python'},{name:'REST APIs',icon:'fa-solid fa-plug'},
        {name:'Firebase',icon:'fa-solid fa-fire'},{name:'Authentication',icon:'fa-solid fa-shield-halved'},
        {name:'Database',icon:'fa-solid fa-database'}]},
    { title:'Engineering', icon:'fa-solid fa-screwdriver-wrench', note:'// when things go sideways',
      items:[
        {name:'Real-Time Debugging',icon:'fa-solid fa-bug'},{name:'API Integration',icon:'fa-solid fa-diagram-project'},
        {name:'Performance Optimization',icon:'fa-solid fa-gauge-high'},{name:'Production Issue Solving',icon:'fa-solid fa-bolt'},
        {name:'System Troubleshooting',icon:'fa-solid fa-screwdriver-wrench'}]},
    { title:'Professional', icon:'fa-solid fa-people-group', note:'// everything around the code',
      items:[
        {name:'Client Handling',icon:'fa-solid fa-handshake'},{name:'Requirement Analysis',icon:'fa-solid fa-clipboard-list'},
        {name:'Budget Planning',icon:'fa-solid fa-coins'},{name:'Project Coordination',icon:'fa-solid fa-diagram-project'},
        {name:'Team Handling',icon:'fa-solid fa-users'}]}
  ],

  /* projects — fully editable; visual: 'dashboard' | 'realtime' | 'gallery' */
  projects: [
    { name:'Orbit Commerce', visual:'dashboard',
      desc:'A real-time e-commerce platform with live inventory, order tracking and a full admin dashboard.',
      tags:['Angular','Django','Firebase','REST API'],
      challenge:'Inventory went out of sync between storefront and warehouse during flash sales.',
      solution:'Moved stock updates to Firebase real-time listeners with optimistic UI and server-side reconciliation.',
      result:'Zero oversold orders across the next three sale events.',
      github:'#', demo:'#' },                        // ← REPLACE links
    { name:'Pulseboard', visual:'realtime',
      desc:'Live production monitoring that surfaces errors, latency and API health the moment they happen.',
      tags:['Angular','TypeScript','WebSockets','Django'],
      challenge:'The client only learned about production issues when users complained.',
      solution:'Built a streaming event pipeline with WebSocket feeds, anomaly rules and severity filters.',
      result:'Mean detection time dropped from hours to under a minute.',
      github:'#', demo:'#' },                        // ← REPLACE links
    { name:'Framely', visual:'gallery',
      desc:'A photography portfolio platform with a fast image pipeline, albums and a fully customisable showcase.',
      tags:['Angular','Django','Image Pipeline','UI/UX'],
      challenge:'Large galleries were slow to load and painful to browse on mobile.',
      solution:'Responsive image pipeline, aggressive lazy-loading and a swipe-first gallery designed from scratch.',
      result:'First meaningful paint under one second, even on 4G.',
      github:'#', demo:'#' }                         // ← REPLACE links
  ],

  /* client & project management process — 10 stations */
  process: [
    { title:'Client Communication', icon:'fa-solid fa-comments',        desc:'Listening first — clear, honest, regular updates.' },
    { title:'Requirement Analysis', icon:'fa-solid fa-clipboard-list',  desc:'Turning ideas into precise, buildable specs.' },
    { title:'Technical Planning',   icon:'fa-solid fa-diagram-project', desc:'Architecture, stack and milestones.' },
    { title:'Budget Planning',      icon:'fa-solid fa-coins',           desc:'Realistic estimates with no surprises.' },
    { title:'Task Breakdown',       icon:'fa-solid fa-list-check',      desc:'Small, deliverable, testable units.' },
    { title:'Team Coordination',    icon:'fa-solid fa-people-group',    desc:'Everyone aligned, blockers surfaced early.' },
    { title:'Development',          icon:'fa-solid fa-code',            desc:'Frontend, backend, APIs — built to last.' },
    { title:'Testing',              icon:'fa-solid fa-bug',             desc:'Edge cases found before users find them.' },
    { title:'Deployment',           icon:'fa-solid fa-rocket',          desc:'Smooth releases, safe rollbacks.' },
    { title:'Post-Launch Support',  icon:'fa-solid fa-life-ring',       desc:'Staying around long after go-live.' }
  ],

  /* photography & travel gallery — replace URLs with your own shots.
     If an image fails to load, a gradient tile takes its place. */
  photos: [
    { url:'https://images.unsplash.com/photo-1519681393784-d120267933ba?auto=format&fit=crop&w=1100&q=60', cls:'ph-a', fb:'radial-gradient(circle at 30% 30%,#1d2c3a,#0d1218)', caption:'Night Ridge',    meta:'Himalayas · 30s · f/2.8' },
    { url:'https://images.unsplash.com/photo-1476514525535-07fb3b4ae5f1?auto=format&fit=crop&w=800&q=60',   cls:'ph-b', fb:'linear-gradient(140deg,#1c2530,#0f151d)',           caption:'Still Water',   meta:'Kerala · 1/500s · ISO 100' },
    { url:'https://images.unsplash.com/photo-1470071459604-3b5ec3a7fe05?auto=format&fit=crop&w=800&q=60',   cls:'ph-c', fb:'linear-gradient(140deg,#231f2e,#12101a)',           caption:'Morning Mist',  meta:'Munnar · f/4 · ISO 200' },
    { url:'https://images.unsplash.com/photo-1441974231531-c6227db76b6e?auto=format&fit=crop&w=800&q=60',   cls:'ph-d', fb:'linear-gradient(140deg,#18262a,#0e1416)',           caption:'Green Silence', meta:'Western Ghats · 1/250s' },
    { url:'https://images.unsplash.com/photo-1464822759023-fed622ff2c3b?auto=format&fit=crop&w=800&q=60',   cls:'ph-e', fb:'linear-gradient(140deg,#22283a,#101321)',           caption:'High Altitude', meta:'Himachal · 24mm' },
    { url:'https://images.unsplash.com/photo-1506905925346-21bda4d32df4?auto=format&fit=crop&w=800&q=60',   cls:'ph-f', fb:'linear-gradient(140deg,#26222b,#121015)',           caption:'Above Clouds',  meta:'Sunrise · f/8 · ISO 100' }
  ],

  /* contribution heatmap — seed changes the pattern, density (0–1) how busy it looks */
  activity: { seed: 7, density: 0.58 }
};
</script>

<!-- dynamic background (grid · blobs · particles · noise) -->
<div class="bg" aria-hidden="true">
  <div class="blob b1"></div><div class="blob b2"></div><div class="blob b3"></div>
  <div class="bg-grid"></div>
  <canvas id="bgParticles"></canvas>
  <div class="bg-noise"></div>
</div>

<!-- custom cursor (desktop only) -->
<div class="cursor-glow" id="cursorGlow" aria-hidden="true"></div>
<div class="cursor-ring" id="cursorRing" aria-hidden="true"></div>
<div class="cursor-dot" id="cursorDot" aria-hidden="true"></div>

<!-- ═══ 1. NAVIGATION ═══════════════════════════════════════════ -->
<header class="nav" id="nav">
  <div class="nav-inner">
    <a href="#home" class="brand" aria-label="Ashokan — home">
      <span class="brand-mark">A</span>
      <span class="brand-name">ashokan</span>
      <span class="brand-dot" aria-hidden="true"></span>
    </a>
    <ul class="nav-links">
      <li><a class="nav-link active" href="#home">Home</a></li>
      <li><a class="nav-link" href="#about">About</a></li>
      <li><a class="nav-link" href="#skills">Skills</a></li>
      <li><a class="nav-link" href="#experience">Experience</a></li>
      <li><a class="nav-link" href="#projects">Projects</a></li>
      <li><a class="nav-link" href="#services">Services</a></li>
      <li><a class="nav-link" href="#contact">Contact</a></li>
    </ul>
    <a href="#contact" class="btn btn-ghost nav-cta magnetic">Let's talk</a>
    <button class="burger" id="burger" aria-label="Menu" aria-expanded="false"><span></span><span></span></button>
  </div>
</header>

<!-- mobile overlay menu -->
<div class="mob-menu" id="mobMenu">
  <nav>
    <a class="mob-link" style="--i:0" href="#home"><span>01</span>Home</a>
    <a class="mob-link" style="--i:1" href="#about"><span>02</span>About</a>
    <a class="mob-link" style="--i:2" href="#skills"><span>03</span>Skills</a>
    <a class="mob-link" style="--i:3" href="#experience"><span>04</span>Experience</a>
    <a class="mob-link" style="--i:4" href="#projects"><span>05</span>Projects</a>
    <a class="mob-link" style="--i:5" href="#services"><span>06</span>Services</a>
    <a class="mob-link" style="--i:6" href="#contact"><span>07</span>Contact</a>
  </nav>
  <div class="mob-foot">
    <div id="mobSoc" style="display:flex;gap:12px"></div>
    <div class="st"><span class="pdot"></span>Available</div>
  </div>
</div>

<main>

<!-- ═══ 2. HERO ═════════════════════════════════════════════════ -->
<section class="hero" id="home">
  <div class="wrap hero-grid">
    <div class="hero-copy">
      <p class="hero-hello hr" style="--d:.05s"><span class="tick"></span>Hello, I'm</p>
      <h1 class="hero-name" aria-label="Ashokan">
        <span class="ln">
          <span class="l" style="--i:0">A</span><span class="l" style="--i:1">S</span><span class="l" style="--i:2">H</span><span class="l" style="--i:3">O</span><span class="l" style="--i:4">K</span><span class="l" style="--i:5">A</span><span class="l" style="--i:6">N</span><span class="l nd" style="--i:7">.</span>
        </span>
      </h1>
      <div class="hero-type hr" style="--d:.55s" aria-live="polite">
        <span class="tp">&gt;_</span><span id="typeText"></span><span class="caret" aria-hidden="true"></span>
      </div>
      <p class="hero-sub hr" style="--d:.7s">Building scalable web experiences, solving real-time production problems, and turning ideas into reliable digital products.</p>
      <div class="hero-cta hr" style="--d:.85s">
        <a href="#projects" class="btn btn-solid magnetic"><span>View my work</span><i class="fa-solid fa-arrow-right"></i></a>
        <a href="#contact" class="btn btn-ghost magnetic"><span>Let's connect</span><i class="fa-solid fa-paper-plane"></i></a>
      </div>
    </div>

    <!-- abstract developer visual: orb + orbiting tech chips + live code card -->
    <div class="hero-visual" aria-hidden="true">
      <div class="hv-tilt" id="hvTilt">
        <div class="orb"></div>
        <div class="ring r1"></div><div class="ring r2"></div><div class="ring r3"></div>
        <div class="orbit o1"><span class="chip"><i class="fa-brands fa-angular"></i>angular</span></div>
        <div class="orbit o2"><span class="chip"><i class="fa-solid fa-database"></i>database</span></div>
        <div class="orbit o3"><span class="chip"><i class="fa-brands fa-python"></i>python</span></div>
        <div class="code-card">
          <div class="cc-bar"><i></i><i></i><i></i><em>app.component.ts</em></div>
          <div class="cc-code"><span class="c">// always shipping</span>
<span class="k">export class</span> <span class="f">Ashokan</span> {
  stack = [<span class="s">'Angular'</span>, <span class="s">'Django'</span>];
  mode  = <span class="s">'problem-solving'</span>;

  <span class="f">deploy</span>(target: <span class="t">string</span>) {
    <span class="k">return</span> <span class="s">'stable ✓'</span>;
  }
} <span class="code-caret"></span></div>
        </div>
        <span class="fc fc1"><span class="fc-dot"></span>GET /api/orders · 200 OK</span>
        <span class="fc fc2"><i class="fa-solid fa-bolt"></i>latency 42ms</span>
        <span class="fc fc3"><i class="fa-solid fa-shield-halved"></i>auth · verified</span>
      </div>
    </div>
  </div>
  <div class="hero-scroll" id="heroScroll"><div class="mouse"><span></span></div>scroll</div>
  <div class="hero-side" aria-hidden="true">Portfolio — 2026</div>
</section>

<!-- ═══ 3. ABOUT ════════════════════════════════════════════════ -->
<section id="about">
  <div class="wrap">
    <div class="sec-head" data-reveal>
      <p class="kicker"><b>01</b> About</p>
      <h2 class="sec-title">More than<br><span class="o">just code</span></h2>
    </div>
    <div class="about-grid">
      <div class="about-lead" data-reveal data-delay=".1">
        <p class="lead">I'm a developer who enjoys building things, solving difficult problems, understanding client requirements, and turning ideas into practical products.</p>
        <p class="support">From the first client conversation to the final deploy, I stay close to the details — the pixel, the query, the deadline — because that's where good products are actually made.</p>
      </div>
      <!-- EDIT: the three about cards -->
      <div class="about-cards">
        <article class="a-card glass" data-reveal data-delay=".15">
          <div class="a-top"><span class="a-ico"><i class="fa-solid fa-code"></i></span><span class="a-idx">/ 01</span></div>
          <h3>Code</h3><p>Building modern, scalable and responsive web applications.</p>
        </article>
        <article class="a-card glass" data-reveal data-delay=".28">
          <div class="a-top"><span class="a-ico"><i class="fa-solid fa-pen-ruler"></i></span><span class="a-idx">/ 02</span></div>
          <h3>Create</h3><p>Designing clean interfaces and meaningful digital experiences.</p>
        </article>
        <article class="a-card glass" data-reveal data-delay=".41">
          <div class="a-top"><span class="a-ico"><i class="fa-solid fa-bug"></i></span><span class="a-idx">/ 03</span></div>
          <h3>Solve</h3><p>Debugging real-time production issues and finding practical solutions under pressure.</p>
        </article>
      </div>
    </div>
    <!-- statistics (rendered from CONFIG.stats) -->
    <div class="stats" data-reveal id="statsRow"></div>
  </div>
</section>

<!-- ═══ 4. SKILLS ═══════════════════════════════════════════════ -->
<section id="skills">
  <div class="wrap">
    <div class="sec-head" data-reveal>
      <p class="kicker"><b>02</b> Skills</p>
      <h2 class="sec-title">The stack I<br><span class="o">think in</span></h2>
    </div>
    <div class="skill-grid" id="skillGrid"><!-- rendered from CONFIG.skills --></div>
  </div>
</section>

<!-- ═══ 5. WORKFLOW — "HOW I WORK" (nav: Experience) ════════════ -->
<section id="experience">
  <div class="wrap">
    <div class="sec-head" data-reveal>
      <p class="kicker"><b>03</b> Experience · How I work</p>
      <h2 class="sec-title">A process<br>that <span class="o">ships</span></h2>
    </div>
    <!-- EDIT: the six workflow steps -->
    <div class="wf" data-reveal>
      <div class="wf-line"><span class="wf-fill"></span></div>
      <div class="wf-step" style="--i:0"><span class="wf-num">01</span><span class="wf-node"></span>
        <div class="wf-card glass"><h3>Understand</h3><p>Understand the client's requirement and business goal before writing a single line.</p></div></div>
      <div class="wf-step" style="--i:1"><span class="wf-num">02</span><span class="wf-node"></span>
        <div class="wf-card glass"><h3>Plan</h3><p>Break the requirement into technical tasks, a timeline and a realistic budget.</p></div></div>
      <div class="wf-step" style="--i:2"><span class="wf-num">03</span><span class="wf-node"></span>
        <div class="wf-card glass"><h3>Design</h3><p>Create a clean, practical and user-friendly experience around the real use case.</p></div></div>
      <div class="wf-step" style="--i:3"><span class="wf-num">04</span><span class="wf-node"></span>
        <div class="wf-card glass"><h3>Develop</h3><p>Build the frontend, backend, APIs and integrations — tested as they grow.</p></div></div>
      <div class="wf-step" style="--i:4"><span class="wf-num">05</span><span class="wf-node"></span>
        <div class="wf-card glass"><h3>Solve</h3><p>Hunt bugs, production issues and real-time problems all the way down to the root cause.</p></div></div>
      <div class="wf-step" style="--i:5"><span class="wf-num">06</span><span class="wf-node"></span>
        <div class="wf-card glass"><h3>Deliver</h3><p>Test, deploy — and stay around to support the product after launch.</p></div></div>
    </div>
  </div>
</section>

<!-- ═══ 6. PROJECTS ═════════════════════════════════════════════ -->
<section id="projects">
  <div class="wrap">
    <div class="sec-head" data-reveal>
      <p class="kicker"><b>04</b> Projects</p>
      <h2 class="sec-title">Selected <span class="o">work</span></h2>
      <p class="sec-sub">Each project carries a story: the challenge that started it, the solution that fixed it, and the result that stayed.</p>
    </div>
    <div class="proj-list" id="projList"><!-- rendered from CONFIG.projects --></div>
  </div>
</section>

<!-- ═══ 7. REAL-TIME PROBLEM SOLVER ═════════════════════════════ -->
<section id="solver">
  <div class="wrap solver-grid">
    <div class="solver-copy">
      <div class="sec-head" data-reveal>
        <p class="kicker"><b>05</b> Problem Solver</p>
        <h2 class="sec-title">When production<br>breaks, <span class="o">I debug</span>.</h2>
      </div>
      <p class="sec-sub" data-reveal data-delay=".1">From frontend bugs to backend failures, API problems and real-time production issues — I enjoy finding the root cause instead of just hiding the symptom.</p>
      <ul class="fix-list" data-reveal data-delay=".2">
        <li><i class="fa-solid fa-check"></i>Frontend &amp; rendering bugs</li>
        <li><i class="fa-solid fa-check"></i>API failures &amp; integration issues</li>
        <li><i class="fa-solid fa-check"></i>Real-time data &amp; WebSocket problems</li>
        <li><i class="fa-solid fa-check"></i>Production incidents under pressure</li>
      </ul>
    </div>
    <div data-reveal data-delay=".15">
      <div class="term" id="terminal">
        <div class="term-bar"><i></i><i></i><i></i><em>ashokan@prod — zsh</em>
          <button class="t-replay magnetic" id="termReplay" aria-label="Replay terminal"><i class="fa-solid fa-rotate-right"></i></button>
        </div>
        <div class="term-body" id="termBody"></div>
      </div>
    </div>
  </div>
</section>

<!-- ═══ 8. CLIENT & PROJECT MANAGEMENT (nav: Services) ══════════ -->
<section id="services">
  <div class="wrap">
    <div class="sec-head split" data-reveal>
      <div>
        <p class="kicker"><b>06</b> Services</p>
        <h2 class="sec-title">From requirement<br><span class="o">to delivery</span></h2>
      </div>
      <div>
        <p class="split-p">Ten stations every project travels through — so nothing gets lost between what a client imagines and what actually ships.</p>
        <div class="track-arrows">
          <button class="ta magnetic" id="tPrev" aria-label="Previous"><i class="fa-solid fa-arrow-left"></i></button>
          <button class="ta magnetic" id="tNext" aria-label="Next"><i class="fa-solid fa-arrow-right"></i></button>
        </div>
      </div>
    </div>
    <div class="track-zone" data-reveal>
      <div class="track" id="track">
        <div class="track-inner" id="trackInner">
          <div class="track-linewrap"><span class="track-line"></span></div>
          <!-- 10 process stations rendered from CONFIG.process -->
        </div>
      </div>
      <div class="track-foot">
        <div class="track-progress"><span id="trackFill"></span></div>
        <span class="hint mono">drag · scroll · swipe</span>
      </div>
    </div>
  </div>
</section>

<!-- ═══ 9. PHOTOGRAPHY + TRAVEL ═════════════════════════════════ -->
<section id="gallery">
  <div class="wrap">
    <div class="ph-head" data-reveal>
      <div>
        <p class="kicker"><b>07</b> Beyond the code</p>
        <h2 class="sec-title">Beyond<br>the <span class="o">code</span></h2>
        <p class="sec-sub">Sometimes I debug code. Sometimes I capture moments.</p>
      </div>
      <div class="tag-pills"><span>Photography</span><span>Travel</span><span>Visual Design</span></div>
    </div>
    <div class="ph-grid" data-reveal id="phGrid"><!-- rendered from CONFIG.photos --></div>
  </div>
</section>

<!-- ═══ 10. DESIGNER ════════════════════════════════════════════ -->
<section id="design">
  <div class="wrap dsn-grid">
    <div class="dsn-copy">
      <div class="sec-head" data-reveal>
        <p class="kicker"><b>08</b> Design</p>
        <h2 class="sec-title">Designed,<br>then <span class="o">built</span></h2>
      </div>
      <p class="sec-sub" data-reveal data-delay=".1">Code is only half the product. I design what I build — so nothing gets lost in translation between the mockup and the deploy.</p>
      <!-- hover / tap a row to switch the preview -->
      <div class="dsn-list" data-reveal id="dsnList">
        <button class="dsn-item on" style="--i:0" data-scene="ui"><span class="di-idx">01</span><span class="di-t">UI Design</span><i class="fa-solid fa-arrow-right"></i></button>
        <button class="dsn-item" style="--i:1" data-scene="ux"><span class="di-idx">02</span><span class="di-t">UX Thinking</span><i class="fa-solid fa-arrow-right"></i></button>
        <button class="dsn-item" style="--i:2" data-scene="hier"><span class="di-idx">03</span><span class="di-t">Visual Hierarchy</span><i class="fa-solid fa-arrow-right"></i></button>
        <button class="dsn-item" style="--i:3" data-scene="resp"><span class="di-idx">04</span><span class="di-t">Responsive Design</span><i class="fa-solid fa-arrow-right"></i></button>
        <button class="dsn-item" style="--i:4" data-scene="d2c"><span class="di-idx">05</span><span class="di-t">Design-to-Code</span><i class="fa-solid fa-arrow-right"></i></button>
        <button class="dsn-item" style="--i:5" data-scene="cd"><span class="di-idx">06</span><span class="di-t">Creative Direction</span><i class="fa-solid fa-arrow-right"></i></button>
      </div>
    </div>
    <div class="dsn-stage glass" data-reveal data-delay=".15">
      <div class="stage-chrome"><span class="m-d"></span><span class="m-d"></span><span class="m-d"></span><em>design.ashokan — live preview</em></div>
      <div class="stage-body">
        <!-- scene: UI design -->
        <div class="scene sc-ui is-on" data-scene="ui">
          <div class="sk sk-bar"><span class="sk sk-c"></span><span class="sk sk-l w2"></span><span class="sk sk-l w1"></span><span class="sk sk-b"></span></div>
          <div class="sk sk-hero"><span class="sk sk-l w4"></span><span class="sk sk-l w3"></span><span class="sk sk-b"></span></div>
          <div class="sk-cards"><span class="sk sk-card" style="--sd:.2s"></span><span class="sk sk-card" style="--sd:.5s"></span><span class="sk sk-card" style="--sd:.8s"></span></div>
        </div>
        <!-- scene: UX thinking -->
        <div class="scene sc-ux" data-scene="ux">
          <svg viewBox="0 0 320 190" aria-hidden="true">
            <path class="ux-p" d="M30 95 C 75 30, 120 30, 160 95 S 245 160, 290 95"/>
            <path class="ux-p" d="M30 95 C 75 160, 120 160, 160 95"/>
            <path class="ux-p" d="M160 95 C 200 45, 240 55, 290 95"/>
            <circle class="ux-n" cx="30" cy="95" r="9"/><circle class="ux-c" cx="30" cy="95" r="3"/>
            <circle class="ux-n ux-pulse" cx="95" cy="52" r="9"/><circle class="ux-c" cx="95" cy="52" r="3"/>
            <circle class="ux-n" cx="160" cy="95" r="9"/><circle class="ux-c" cx="160" cy="95" r="3"/>
            <circle class="ux-n" cx="228" cy="132" r="9"/><circle class="ux-c" cx="228" cy="132" r="3"/>
            <circle class="ux-n" cx="290" cy="95" r="9"/><circle class="ux-c" cx="290" cy="95" r="3"/>
          </svg>
        </div>
        <!-- scene: visual hierarchy -->
        <div class="scene sc-hier" data-scene="hier">
          <span class="hi-guide hg1"></span><span class="hi-guide hg2"></span>
          <div class="hi-row"><span class="hi-aa">Aa</span><div class="hi-lines"><span class="hi-l hl1"></span><span class="hi-l hl2"></span></div></div>
          <span class="hi-l hl3"></span><span class="hi-l hl4"></span><span class="hi-l hl5"></span>
        </div>
        <!-- scene: responsive -->
        <div class="scene sc-resp" data-scene="resp">
          <div class="rs rs-d"><span></span><span></span><span></span><span class="rs-lab"></span></div>
          <div class="rs rs-t"><span></span><span></span><span class="rs-lab"></span></div>
          <div class="rs rs-p"><span></span><span class="rs-lab"></span></div>
        </div>
        <!-- scene: design to code -->
        <div class="scene sc-d2c" data-scene="d2c">
          <div class="d2-col"><span class="sk"></span><span class="sk"></span><span class="sk"></span></div>
          <div class="d2-arrow"><i class="fa-solid fa-angle-right" style="--i:0"></i><i class="fa-solid fa-angle-right" style="--i:1"></i><i class="fa-solid fa-angle-right" style="--i:2"></i></div>
          <div class="d2-code"><span class="k">.hero</span> {
  <span class="p">display</span>: <span class="v">grid</span>;
  <span class="p">place-items</span>: <span class="v">center</span>;
}</div>
        </div>
        <!-- scene: creative direction -->
        <div class="scene sc-cd" data-scene="cd">
          <div class="sw-t sel"><span style="--c:#6fe3ff;--sd:0s"></span><em>primary</em></div>
          <div class="sw-t"><span style="--c:#a8a3ff;--sd:.4s"></span><em>secondary</em></div>
          <div class="sw-t"><span style="--c:#57e6a8;--sd:.8s"></span><em>success</em></div>
          <div class="sw-t"><span style="--c:#8b93a3;--sd:1.2s"></span><em>muted</em></div>
          <div class="sw-t"><span style="--c:#ffcf8a;--sd:1.6s"></span><em>warm</em></div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ═══ 11. GITHUB-STYLE ACTIVITY ═══════════════════════════════ -->
<section id="activity">
  <div class="wrap">
    <div class="sec-head" data-reveal>
      <p class="kicker"><b>09</b> GitHub Activity</p>
      <h2 class="sec-title">A year of <span class="o">commits</span></h2>
    </div>
    <div class="gh-card glass" id="ghCard" data-reveal data-delay=".1">
      <div class="gh-head">
        <div class="gt-l"><i class="fa-brands fa-github"></i><span>contribution activity</span></div>
        <span class="mono" id="ghTotal"></span>
      </div>
      <div class="gh-scroll">
        <div class="gh-days"><span>Mon</span><span></span><span>Wed</span><span></span><span>Fri</span><span></span><span></span></div>
        <div class="gh-main">
          <div class="gh-months" id="ghMonths"></div>
          <div class="gh-grid" id="ghGrid"></div>
        </div>
      </div>
      <div class="gh-foot">
        <span class="gh-legend">Less <i class="l0"></i><i class="l1"></i><i class="l2"></i><i class="l3"></i><i class="l4"></i> More</span>
        <span class="mono" id="ghBest" style="font-size:.66rem;color:var(--faint)"></span>
      </div>
    </div>
  </div>
</section>

<!-- ═══ 12. CONTACT ═════════════════════════════════════════════ -->
<section id="contact">
  <div class="wrap contact-wrap">
    <div class="sec-head" data-reveal style="display:flex;flex-direction:column;align-items:center">
      <p class="kicker"><b>10</b> Contact</p>
      <h2 class="sec-title">Let's build<br><span class="o">something</span></h2>
    </div>
    <p class="contact-sub" data-reveal data-delay=".1">Have an idea, a project, a production issue, or something that needs to be built?</p>
    <div class="contact-card" data-reveal data-delay=".2">
      <span class="cc-spin" aria-hidden="true"></span>
      <div class="cc-inner">
        <div class="cc-status"><span class="pdot"></span><span>Available for interesting projects</span><em>reply within 24h</em></div>
        <div class="cc-mailrow">
          <a class="cc-mail" id="mailLink" href="#">hello@ashokan.dev</a>
          <button class="cc-copy magnetic" id="copyMail"><i class="fa-regular fa-copy"></i><span>copy</span></button>
        </div>
        <div class="cc-soc" id="socialRow"><!-- rendered from CONFIG.socials --></div>
      </div>
    </div>
  </div>
</section>

</main>

<!-- ═══ 13. FOOTER ══════════════════════════════════════════════ -->
<footer>
  <div class="wrap">
    <div class="foot-status" data-reveal><span class="pdot"></span>Available for interesting projects</div>
    <p class="foot-motto" data-reveal data-delay=".1">Code<span>•</span>Create<span>•</span>Travel<span>•</span>Repeat.</p>
    <div class="foot-meta">
      <span>Designed &amp; Developed by <strong>Ashokan</strong></span>
      <span class="foot-year">© <span id="footYear"></span> — built with one file &amp; too much coffee</span>
    </div>
  </div>
</footer>

<!-- back to top (scroll-progress ring) -->
<button id="toTop" class="magnetic" aria-label="Back to top"><i class="fa-solid fa-arrow-up"></i></button>

<!-- contribution tooltip -->
<div class="gh-tip" id="ghTip" role="tooltip"></div>

<script>
/* ═══════════════════════════════════════════════════════════════
   ASHOKAN — interactions & rendering (vanilla JS, no dependencies)
   ═══════════════════════════════════════════════════════════════ */
(function(){
'use strict';
const $  = (s,c=document)=>c.querySelector(s);
const $$ = (s,c=document)=>[...c.querySelectorAll(s)];
const RM   = matchMedia('(prefers-reduced-motion: reduce)').matches;
const FINE = matchMedia('(pointer: fine)').matches;

/* ── hero entrance ─────────────────────────────────────────── */
requestAnimationFrame(()=>setTimeout(()=>document.body.classList.add('loaded'),60));
 $('#footYear').textContent = new Date().getFullYear();

/* ── typing roles ──────────────────────────────────────────── */
  const el = $('#typeText'); if(!el) return;
  const roles = CONFIG.roles;
  if(RM){ el.textContent = roles[0]; return; }
  let ri=0, ci=0, del=false;
  (function tick(){
    const w = roles[ri];
    let wait = del ? 42 : 68 + Math.random()*70;
    if(!del){ ci++; if(ci === w.length){ del = true; wait = 1900; } }
    else    { ci--; if(ci === 0){ del=false; ri=(ri+1)%roles.length; wait = 340; } }
    el.textContent = w.slice(0,ci);
    setTimeout(tick, wait);
  })();
})();

/* ── render: statistics ────────────────────────────────────── */
CONFIG.stats.forEach((s,i)=>{
  const d = document.createElement('div');
  d.className='stat'; d.style.setProperty('--i',i);
  d.innerHTML = `<div class="stat-n"><span class="n" data-t="${s.value}">0</span><span class="suf">${s.suffix}</span></div><p>${s.label}</p>`;
  $('#statsRow').appendChild(d);
});

/* ── render: skills ────────────────────────────────────────── */
CONFIG.skills.forEach((cat,i)=>{
  const p = document.createElement('article');
  p.className = `sk-panel glass ${cat.span||''}`;
  p.setAttribute('data-reveal',''); p.dataset.delay = (i*0.12).toFixed(2);
  const chips = cat.items.map(it =>
    `<span class="chip-s">${it.icon?`<i class="${it.icon}"></i>`:'<span class="cdot"></span>'}${it.name}</span>`).join('');
  const bars = (cat.bars||[]).map(b =>
    `<div class="bar"><div class="bar-top"><span>${b.label}</span><b>${b.level}%</b></div>
     <div class="bar-track"><span class="bar-fill" style="--p:${b.level/100}"></span></div></div>`).join('');
  p.innerHTML =
    `<div class="sk-head"><i class="${cat.icon}"></i><h3>${cat.title}</h3><span class="sk-idx">0${i+1}</span></div>
     <div class="sk-chips">${chips}</div>${bars?`<div class="sk-bars">${bars}</div>`:''}
     <p class="sk-note">${cat.note}</p>`;
  $('#skillGrid').appendChild(p);
});

/* ── render: projects (with pure-CSS mock UIs) ─────────────── */
const CHART = [38,55,42,70,58,84,64,92,76];
const FEED  = [['ok','GET /api/stream','200'],['ok','POST /events','201'],['warn','GET /metrics','429'],['ok','WS heartbeat','ok'],['bad','GET /legacy','500']];
function mock(type){
  const chrome = url => `<div class="chrome"><span class="m-d"></span><span class="m-d"></span><span class="m-d"></span><em>${url}</em></div>`;
  if(type==='dashboard') return chrome('orbit-commerce/admin') + `
    <div class="m-dash"><div class="m-side"><span></span><span></span><span></span><span></span></div>
    <div class="m-main"><div class="m-stats"><div><span></span><b></b></div><div><span></span><b></b></div><div><span></span><b></b></div></div>
    <div class="m-chart">${CHART.map((h,i)=>`<span style="--h:${h};--i:${i}"></span>`).join('')}</div></div></div>`;
  if(type==='realtime') return chrome('pulseboard.io/live') + `<span class="live"><i></i>LIVE</span>` + `
    <div class="m-rt"><div class="m-feed">${FEED.map((r,i)=>`<span class="fr" style="--i:${i}"><i class="fd ${r[0]}"></i>${r[1]}<em>${r[2]}</em></span>`).join('')}</div>
    <div class="m-spark"><em>error rate · live</em>
      <svg viewBox="0 0 120 42" preserveAspectRatio="none">
        <polygon class="sparkfill" points="0,34 12,29 24,31 36,22 48,26 60,15 72,19 84,9 96,13 120,5 120,42 0,42"/>
        <polyline class="spark" pathLength="1" points="0,34 12,29 24,31 36,22 48,26 60,15 72,19 84,9 96,13 120,5"/>
      </svg></div></div>`;
  /* gallery */
  const G = ['radial-gradient(circle at 30% 30%,#22303f,#12181f)','linear-gradient(150deg,#28233a,#141221)',
             'linear-gradient(150deg,#1e2b2a,#0f1614)','radial-gradient(circle at 60% 30%,#33261f,#171310)',
             'linear-gradient(150deg,#213040,#111820)','linear-gradient(150deg,#2a2430,#141118)'];
  return chrome('framely.app/gallery') + `
    <div class="m-gl">${G.map((g,i)=>`<span class="gt ${i===0?'big':''}" style="--i:${i};background:${g}"></span>`).join('')}</div>`;
}
CONFIG.projects.forEach((pr,i)=>{
  const a = document.createElement('article');
  a.className='proj'; a.setAttribute('data-reveal',''); a.dataset.delay='0';
  a.innerHTML =
    `<div class="proj-visual"><div class="pv-inner"><div class="mock">${mock(pr.visual)}</div></div></div>
     <div class="proj-body">
       <p class="p-idx mono">Project 0${i+1}</p>
       <h3>${pr.name}</h3>
       <p class="p-desc">${pr.desc}</p>
       <ul class="csr">
         <li><span>Challenge</span><p>${pr.challenge}</p></li>
         <li><span>Solution</span><p>${pr.solution}</p></li>
         <li><span>Result</span><p>${pr.result}</p></li>
       </ul>
       <div class="tags">${pr.tags.map(t=>`<span>${t}</span>`).join('')}</div>
       <div class="p-links">
         <a class="p-btn solid magnetic" href="${pr.github}" target="_blank" rel="noopener"><i class="fa-brands fa-github"></i>GitHub</a>
         <a class="p-btn ghost magnetic" href="${pr.demo}" target="_blank" rel="noopener"><i class="fa-solid fa-arrow-up-right"></i>Live Demo</a>
       </div>
     </div>`;
  $('#projList').appendChild(a);
});

/* ── render: process track ──────────────────────────────────── */
CONFIG.process.forEach((st,i)=>{
  const d = document.createElement('div');
  d.className='track-item'; d.style.setProperty('--i',i);
  d.innerHTML =
    `<div class="t-node"><span class="t-dot"></span><span class="t-idx">0${i+1}</span></div>
     <div class="t-card glass"><i class="${st.icon}"></i><h4>${st.title}</h4><p>${st.desc}</p></div>`;
  $('#trackInner').appendChild(d);
});

/* ── render: photography gallery ────────────────────────────── */
CONFIG.photos.forEach((ph,i)=>{
  const f = document.createElement('figure');
  f.className = `ph-item ${ph.cls}`; f.style.setProperty('--d',(i*0.09)+'s');
  f.innerHTML =
    `<div class="ph-zoom"><div class="ph-fb" style="background:${ph.fb}"></div>
       <img src="${ph.url}" alt="${ph.caption}" loading="lazy" decoding="async"
            onerror="this.closest('.ph-item').classList.add('no-img')"></div>
     <figcaption><span class="ph-cap">${ph.caption}</span><span class="ph-meta">${ph.meta}</span></figcaption>`;
  $('#phGrid').appendChild(f);
});

/* ── render: socials + email ────────────────────────────────── */
 $('#mailLink').textContent = CONFIG.email;
 $('#mailLink').href = 'mailto:'+CONFIG.email;
CONFIG.socials.forEach((s,i)=>{
  const a = document.createElement('a');
  a.className='s-btn magnetic'; a.href=s.url; a.target='_blank'; a.rel='noopener';
  a.style.setProperty('--i',i);
  a.innerHTML = `<i class="${s.icon}"></i><div><b>${s.label}</b><small>${s.handle}</small></div><i class="fa-solid fa-arrow-up-right go"></i>`;
  $('#socialRow').appendChild(a);
});
CONFIG.socials.slice(0,3).forEach(s=>{
  const m = document.createElement('a');
  m.href=s.url; m.target='_blank'; m.rel='noopener'; m.setAttribute('aria-label',s.label);
  m.innerHTML = `<i class="${s.icon}"></i>`;
  $('#mobSoc').appendChild(m);
});

/* ── scroll reveal system ─────────────────────────────────────
   Elements with [data-reveal] fade/slide in once when visible.
   Inline styles are cleaned up afterwards so component hover
   transitions stay untouched. Pattern "B": parents carry
   data-reveal and children stagger via CSS (.in hooks).        */
(function reveal(){
  const els = $$('[data-reveal]');
  if(RM){ els.forEach(el=>el.classList.add('in')); return; }
  const io = new IntersectionObserver(entries=>{
    entries.forEach(en=>{
      if(!en.isIntersecting) return;
      const el = en.target; io.unobserve(el);
      const d = parseFloat(el.dataset.delay)||0;
      el.style.opacity='0';
      el.style.translate = '0 30px';
      el.style.transition = `opacity .85s var(--ease) ${d}s, translate .85s var(--ease) ${d}s`;
      requestAnimationFrame(()=>requestAnimationFrame(()=>{
        el.classList.add('in');
        el.style.opacity='1'; el.style.translate='0 0';
        setTimeout(()=>{ ['opacity','translate','transition'].forEach(p=>el.style.removeProperty(p)); }, 900+d*1000);
      }));
    });
  },{threshold:.15, rootMargin:'0px 0px -6% 0px'});
  els.forEach(el=>io.observe(el));
})();

/* ── number counters ────────────────────────────────────────── */
(function counters(){
  const io = new IntersectionObserver(es=>{
    es.forEach(en=>{
      if(!en.isIntersecting) return; io.unobserve(en.target);
      const el = en.target, t = +el.dataset.t;
      if(RM){ el.textContent = t; return; }
      const t0 = performance.now(), dur = 1600;
      (function step(now){
        const p = Math.min(1,(now-t0)/dur), e = 1-Math.pow(1-p,3);
        el.textContent = Math.round(t*e);
        if(p<1) requestAnimationFrame(step);
      })(t0);
    });
  },{threshold:.6});
  $$('.stat .n').forEach(el=>io.observe(el));
})();

/* ── navigation: shrink, spy, burger ────────────────────────── */
(function nav(){
  const nav = $('#nav'), heroScroll = $('#heroScroll');
  const onScroll = ()=>{
    nav.classList.toggle('scrolled', scrollY>40);
    heroScroll.classList.toggle('hide', scrollY>90);
  };
  addEventListener('scroll', onScroll, {passive:true}); onScroll();
  /* scroll-spy */
  const links = {}; $$('.nav-link').forEach(l=>links[l.getAttribute('href').slice(1)]=l);
  const spy = new IntersectionObserver(es=>{
    es.forEach(en=>{
      if(en.isIntersecting){
        $$('.nav-link').forEach(l=>l.classList.remove('active'));
        const l = links[en.target.id]; if(l) l.classList.add('active');
      }
    });
  },{rootMargin:'-38% 0px -55% 0px'});
  ['home','about','skills','experience','projects','services','contact']
    .forEach(id=>{ const s=document.getElementById(id); if(s) spy.observe(s); });
  /* burger / mobile menu */
  const burger = $('#burger');
  burger.addEventListener('click',()=>{
    const open = document.body.classList.toggle('menu-open');
    burger.setAttribute('aria-expanded', open);
  });
  $$('.mob-link, .mob-foot a').forEach(a=>a.addEventListener('click',()=>{
    document.body.classList.remove('menu-open'); burger.setAttribute('aria-expanded','false');
  }));
})();

/* ── terminal typing ────────────────────────────────────────── */
(function terminal(){
  const body = $('#termBody'); if(!body) return;
  /* EDIT: the story the terminal tells */
  const LINES = [
    {cmd:'deploy --status production'},
    {h:'system_status: <span class="g">production</span>'},
    {h:'issue_detected: <span class="r">true</span>', p:600},
    {h:'analyzing logs<span class="dots"></span>', c:'d', p:900},
    {h:'trace: connection_pool <span class="r">→ exhausted (48/48)</span>', c:'d', p:450},
    {h:'root_cause_found: <span class="y">pool exhaustion under peak load</span>', p:650},
    {cmd:'hotfix apply --pool 128 --retry 3', p:400},
    {h:'applying_fix<span class="dots"></span>', c:'d', p:900},
    {h:'deploying hotfix → v2.4.1', c:'d', p:650},
    {h:'system_status: <span class="g">stable ✓</span>', p:350},
    {h:'<span class="g">✔</span> issue resolved in 3m 12s — monitoring', c:'ok'}
  ];
  let started = false, busy = false;
  function addLine(l){
    const d = document.createElement('div');
    d.className = 'tl ' + (l.c||'');
    d.innerHTML = (l.cmd ? '<span class="pr">ashokan@prod:~$ </span>' : '') + (l.h || l.cmd);
    body.appendChild(d);
  }
  function prompt(){
    const d = document.createElement('div'); d.className='tl';
    d.innerHTML = '<span class="pr">ashokan@prod:~$ </span><span class="t-caret"></span>';
    body.appendChild(d);
  }
  function typeCmd(l, done){
    const d = document.createElement('div'); d.className='tl';
    d.innerHTML = '<span class="pr">ashokan@prod:~$ </span><span class="cmd"></span>';
    body.appendChild(d);
    const span = d.querySelector('.cmd'); let i = 0;
    (function t(){
      span.textContent = l.cmd.slice(0,++i);
      if(i < l.cmd.length) setTimeout(t, 26 + Math.random()*40);
      else setTimeout(done, 300);
    })();
  }
  function run(){
    if(busy) return; busy = true;
    body.innerHTML = '';
    if(RM){ LINES.forEach(addLine); prompt(); busy=false; return; }
    let i = 0;
    (function next(){
      if(i >= LINES.length){ prompt(); busy = false; return; }
      const l = LINES[i++];
      if(l.cmd) typeCmd(l, next);
      else { addLine(l); setTimeout(next, (l.p||350) + 220); }
    })();
  }
  const io = new IntersectionObserver(es=>{
    if(es[0].isIntersecting && !started){ started = true; io.disconnect(); setTimeout(run, 400); }
  },{threshold:.35});
  io.observe($('#terminal'));
  $('#termReplay').addEventListener('click', run);
})();

/* ── horizontal process track ───────────────────────────────── */
(function track(){
  const tr = $('#track'), fill = $('#trackFill');
  const prev = $('#tPrev'), next = $('#tNext');
  const upd = ()=>{
    const max = tr.scrollWidth - tr.clientWidth;
    fill.style.transform = `scaleX(${max ? .06 + (tr.scrollLeft/max)*.94 : 1})`;
    prev.disabled = tr.scrollLeft <= 4;
    next.disabled = tr.scrollLeft >= max - 4;
  };
  tr.addEventListener('scroll', upd, {passive:true}); upd();
  prev.addEventListener('click',()=>tr.scrollBy({left:-340, behavior:RM?'auto':'smooth'}));
  next.addEventListener('click',()=>tr.scrollBy({left: 340, behavior:RM?'auto':'smooth'}));
  /* desktop drag-to-scroll */
  let down=false, sx=0, sl=0;
  tr.addEventListener('pointerdown',e=>{
    if(e.pointerType!=='mouse') return;
    down=true; sx=e.clientX; sl=tr.scrollLeft; tr.classList.add('drag');
  });
  addEventListener('pointermove',e=>{ if(down) tr.scrollLeft = sl - (e.clientX - sx); });
  addEventListener('pointerup',()=>{ down=false; tr.classList.remove('drag'); });
})();

/* ── design section: list ↔ scene switcher ──────────────────── */
(function scenes(){
  const items = $$('.dsn-item'), scenes = $$('.scene');
  function set(k){
    items.forEach(b=>b.classList.toggle('on', b.dataset.scene===k));
    scenes.forEach(s=>s.classList.toggle('is-on', s.dataset.scene===k));
  }
  items.forEach(b=>{
    b.addEventListener('click',()=>set(b.dataset.scene));
    if(FINE) b.addEventListener('pointerenter',()=>set(b.dataset.scene));
  });
})();

/* ── contribution heatmap (generated locally) ───────────────── */
(function heatmap(){
  const grid = $('#ghGrid'); if(!grid) return;
  const {seed, density} = CONFIG.activity;
  let s = (seed>>>0) || 7;
  const rng = ()=>((s = (s*1664525 + 1013904223) >>> 0) / 4294967296);
  const hot = new Set(); while(hot.size < 9) hot.add(Math.floor(rng()*52));
  const weeks=52, days=7, today=new Date();
  const counts = [0,0,0,0,0,0,0]; let total=0; let lastMonth=-1;
  const monthsEl = $('#ghMonths');
  for(let w=0; w<weeks; w++){
    for(let d=0; d<days; d++){
      const date = new Date(today);
      date.setDate(today.getDate() - ((weeks-1-w)*days + (6-d)));
      let base = density * (0.2 + 0.8*rng());
      if(d>=5) base *= 0.5;
      if(hot.has(w)) base *= 1.7;
      const level = base<.16?0 : base<.36?1 : base<.56?2 : base<.78?3 : 4;
      const count = level===0 ? 0 : Math.round(level*1.6 + rng()*3*level);
      total += count; counts[d] += count;
      if(d===0){
        const m = date.getMonth();
        if(m!==lastMonth){
          lastMonth = m;
          const lb = document.createElement('span');
          lb.textContent = date.toLocaleString('en',{month:'short'});
          lb.style.left = (w/weeks*100)+'%';
          monthsEl.appendChild(lb);
        }
      }
      const el = document.createElement('i');
      el.className = 'sq l'+level;
      el.style.setProperty('--w', w);
      el.dataset.count = count;
      el.dataset.date = date.toLocaleDateString(undefined,{weekday:'short',month:'short',day:'numeric'});
      grid.appendChild(el);
    }
  }
  $('#ghTotal').innerHTML = `<b>${total.toLocaleString()}</b> contributions in the last year`;
  const best = counts.indexOf(Math.max(...counts));
  $('#ghBest').textContent = 'most productive: '+['Mon','Tue','Wed','Thu','Fri','Sat','Sun'][best].toUpperCase()+'S'.replace('S','')+'day';
  /* staged reveal */
  const io = new IntersectionObserver((es,o)=>{
    if(es[0].isIntersecting){ grid.classList.add('on'); o.disconnect(); }
  },{threshold:.25});
  io.observe($('#ghCard'));
  /* hover tooltip */
  if(FINE){
    const tip = $('#ghTip');
    grid.addEventListener('mousemove', e=>{
      const t = e.target.closest('.sq');
      if(!t){ tip.style.opacity = 0; return; }
      const n = +t.dataset.count;
      tip.textContent = `${n} contribution${n===1?'':'s'} · ${t.dataset.date}`;
      tip.style.opacity = 1;
      tip.style.left = Math.min(Math.max(e.clientX,110), innerWidth-110)+'px';
      tip.style.top  = e.clientY+'px';
    });
    grid.addEventListener('mouseleave',()=>tip.style.opacity=0);
  }
})();

/* ── copy email micro-interaction ───────────────────────────── */
 $('#copyMail').addEventListener('click', function(){
  const label = this.querySelector('span');
  const done = ok=>{
    this.classList.toggle('ok', ok);
    label.textContent = ok ? 'copied ✓' : 'copy failed';
    setTimeout(()=>{ this.classList.remove('ok'); label.textContent='copy'; }, 1800);
  };
  if(navigator.clipboard) navigator.clipboard.writeText(CONFIG.email).then(()=>done(true)).catch(()=>done(false));
  else done(false);
});

/* ── magnetic buttons ───────────────────────────────────────── */
if(FINE && !RM){
  $$('.magnetic').forEach(m=>{
    m.addEventListener('pointermove', e=>{
      const r = m.getBoundingClientRect();
      m.style.setProperty('--mx', ((e.clientX - r.left - r.width/2)*.3).toFixed(1)+'px');
      m.style.setProperty('--my', ((e.clientY - r.top - r.height/2)*.3).toFixed(1)+'px');
    });
    m.addEventListener('pointerleave', ()=>{
      m.style.setProperty('--mx','0px'); m.style.setProperty('--my','0px');
    });
  });
}

/* ── tilt: hero visual + project visuals ────────────────────── */
if(FINE && !RM){
  const hv = $('#hvTilt');
  let trx=0, try_=0, crx=0, cry=0;
  addEventListener('pointermove', e=>{
    try_ = (e.clientX/innerWidth - .5) * 9;
    trx  = -(e.clientY/innerHeight - .5) * 7;
  }, {passive:true});
  (function tiltLoop(){
    crx += (trx-crx)*.06; cry += (try_-cry)*.06;
    if(hv) hv.style.transform = `perspective(1000px) rotateX(${crx.toFixed(2)}deg) rotateY(${cry.toFixed(2)}deg)`;
    requestAnimationFrame(tiltLoop);
  })();
  $$('.proj-visual').forEach(el=>{
    el.addEventListener('pointermove', e=>{
      const r = el.getBoundingClientRect();
      const x = (e.clientX - r.left)/r.width - .5, y = (e.clientY - r.top)/r.height - .5;
      el.style.transform = `perspective(900px) rotateX(${(-y*7).toFixed(2)}deg) rotateY(${(x*9).toFixed(2)}deg)`;
    });
    el.addEventListener('pointerleave', ()=>{ el.style.transform=''; });
  });
}

/* ── custom cursor + glow (desktop, motion allowed) ─────────── */
if(FINE && !RM){
  document.documentElement.classList.add('cur');
  const dot = $('#cursorDot'), ring = $('#cursorRing'), glow = $('#cursorGlow');
  let mx = innerWidth/2, my = innerHeight/2, rx = mx, ry = my, gx = mx, gy = my;
  addEventListener('pointermove', e=>{
    mx = e.clientX; my = e.clientY;
    dot.style.translate = mx+'px '+my+'px';
  }, {passive:true});
  const SEL = 'a, button, .chip-s, .sq, .dsn-item, .ph-item, .nav-link, .gh-grid';
  document.addEventListener('mouseover', e=>{ if(e.target.closest(SEL)) ring.classList.add('big'); });
  document.addEventListener('mouseout',  e=>{ if(e.target.closest(SEL)) ring.classList.remove('big'); });
  document.addEventListener('mouseleave', ()=>{ ring.style.opacity=0; dot.style.opacity=0; });
  document.addEventListener('mouseenter', ()=>{ ring.style.opacity=''; dot.style.opacity=''; });
  (function loop(){
    rx += (mx-rx)*.16; ry += (my-ry)*.16;
    gx += (mx-gx)*.055; gy += (my-gy)*.055;
    ring.style.translate = rx.toFixed(1)+'px '+ry.toFixed(1)+'px';
    glow.style.translate = gx.toFixed(1)+'px '+gy.toFixed(1)+'px';
    requestAnimationFrame(loop);
  })();
}

/* ── background particles ───────────────────────────────────── */
(function particles(){
  if(RM) return;
  const cv = $('#bgParticles'), ctx = cv.getContext('2d');
  const dpr = Math.min(devicePixelRatio||1, 1.5);
  let W, H, ps = [];
  function size(){
    W = cv.width  = innerWidth*dpr;
    H = cv.height = innerHeight*dpr;
    cv.style.width = innerWidth+'px'; cv.style.height = innerHeight+'px';
    const n = Math.min(64, Math.round(innerWidth*innerHeight/26000));
    ps = Array.from({length:n}, ()=>({
      x:Math.random()*W, y:Math.random()*H,
      r:(Math.random()*1.3+.4)*dpr,
      vx:(Math.random()-.5)*.12*dpr, vy:(Math.random()-.5)*.12*dpr,
      a:Math.random()*.4+.1, ph:Math.random()*Math.PI*2
    }));
  }
  size(); addEventListener('resize', size);
  (function draw(t){
    requestAnimationFrame(draw);
    if(document.hidden) return;
    ctx.clearRect(0,0,W,H);
    for(const p of ps){
      p.x += p.vx; p.y += p.vy;
      if(p.x<0) p.x=W; if(p.x>W) p.x=0; if(p.y<0) p.y=H; if(p.y>H) p.y=0;
      const tw = .55 + .45*Math.sin(t/1400 + p.ph);
      ctx.beginPath(); ctx.arc(p.x, p.y, p.r, 0, 7);
      ctx.fillStyle = `rgba(140,195,220,${(p.a*tw*.35).toFixed(3)})`;
      ctx.fill();
    }
  })(0);
})();

/* ── photo parallax on scroll ───────────────────────────────── */
(function parallax(){
  if(RM) return;
  const imgs = $$('.ph-zoom img'); if(!imgs.length) return;
  let queued = false;
  function up(){
    queued = false;
    const vh = innerHeight;
    imgs.forEach(im=>{
      const r = im.parentElement.getBoundingClientRect();
      if(r.bottom < -80 || r.top > vh+80) return;
      const c = (r.top + r.height/2 - vh/2) / vh;   /* -0.5 … 0.5 */
      im.style.setProperty('--py', (c*-26).toFixed(1)+'px');
    });
  }
  addEventListener('scroll', ()=>{ if(!queued){ queued = true; requestAnimationFrame(up); } }, {passive:true});
  up();
})();

/* ── back-to-top with scroll progress ring ──────────────────── */
(function toTop(){
  const btn = $('#toTop');
  addEventListener('scroll', ()=>{
    const max = document.documentElement.scrollHeight - innerHeight;
    btn.style.setProperty('--sp', (max ? (scrollY/max*100).toFixed(1) : 0));
    btn.classList.toggle('show', scrollY > 600);
  }, {passive:true});
  btn.addEventListener('click', ()=>scrollTo({top:0, behavior:RM?'auto':'smooth'}));
})();

})();
</script>
</body>
</html>
