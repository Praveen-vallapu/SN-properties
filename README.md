<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>SN Properties UK — Student Living</title>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;0,700;1,300;1,400&family=DM+Sans:wght@300;400;500;600&display=swap" rel="stylesheet">
<style>
*,*::before,*::after{margin:0;padding:0;box-sizing:border-box}
:root{
  --gold:#C9A84C;--gold-light:#E8CB7A;--gold-dim:rgba(201,168,76,0.25);--gold-faint:rgba(201,168,76,0.08);
  --black:#080808;--off:#111;--dark:#181818;--mid:#222;--surf:#141414;
  --white:#FAFAF7;--dim:rgba(250,250,247,0.65);--faint:rgba(250,250,247,0.1);
}
html{scroll-behavior:smooth}
body{font-family:'DM Sans',sans-serif;background:var(--black);color:var(--white);overflow-x:hidden;cursor:none}

/* CURSOR */
#cur{width:8px;height:8px;background:var(--gold);border-radius:50%;position:fixed;top:0;left:0;pointer-events:none;z-index:9999;transition:transform .08s}
#ring{width:32px;height:32px;border:1px solid var(--gold);border-radius:50%;position:fixed;top:0;left:0;pointer-events:none;z-index:9998;opacity:.5;transition:width .3s,height .3s,opacity .3s}

/* NAV */
nav{position:fixed;top:0;width:100%;z-index:1000;padding:22px 64px;display:flex;align-items:center;justify-content:space-between;transition:background .4s,padding .4s}
nav.on{background:rgba(8,8,8,.96);backdrop-filter:blur(24px);padding:14px 64px;border-bottom:.5px solid var(--gold-dim)}
.logo{display:flex;align-items:center;gap:14px;text-decoration:none}
.logomark{width:42px;height:42px;background:var(--gold);display:grid;place-items:center;font-family:'Cormorant Garamond',serif;font-size:18px;font-weight:700;color:var(--black);clip-path:polygon(50% 0%,100% 25%,100% 75%,50% 100%,0% 75%,0% 25%)}
.logotext{font-family:'Cormorant Garamond',serif;font-size:19px;font-weight:600;color:var(--white);letter-spacing:2.5px}
.logotext b{color:var(--gold);font-weight:600}
.nav-links{display:flex;gap:38px;align-items:center}
.nav-links a{color:var(--dim);text-decoration:none;font-size:12px;letter-spacing:1.8px;text-transform:uppercase;font-weight:500;transition:color .3s}
.nav-links a:hover{color:var(--gold)}
.ncta{border:1px solid var(--gold) !important;color:var(--gold) !important;padding:9px 26px;transition:background .3s,color .3s !important}
.ncta:hover{background:var(--gold) !important;color:var(--black) !important}

/* HERO */
.hero{height:100vh;min-height:680px;position:relative;display:flex;align-items:flex-end;padding:0 64px 88px;overflow:hidden}

/* Pure CSS architectural illustration — hero bg */
.hero-art{position:absolute;inset:0;z-index:0}

/* Grid overlay */
.hero-art::before{
  content:'';position:absolute;inset:0;
  background-image:linear-gradient(rgba(201,168,76,.035) 1px,transparent 1px),linear-gradient(90deg,rgba(201,168,76,.035) 1px,transparent 1px);
  background-size:72px 72px;
}

/* Diagonal accent */
.hero-art::after{
  content:'';position:absolute;top:0;right:0;width:56%;height:100%;
  background:linear-gradient(135deg,transparent 0%,rgba(201,168,76,.04) 50%,transparent 100%);
  border-left:.5px solid var(--gold-dim);
}

/* Building silhouettes via SVG embedded inline */
.hero-buildings{position:absolute;right:0;top:0;width:56%;height:100%;z-index:1;opacity:.9}

.hero-grad{position:absolute;inset:0;z-index:2;
  background:linear-gradient(to right,rgba(8,8,8,1) 0%,rgba(8,8,8,.85) 44%,rgba(8,8,8,.15) 100%),
             linear-gradient(to top,rgba(8,8,8,.9) 0%,transparent 50%)}

.hero-content{position:relative;z-index:3;max-width:640px}
.eyebrow{display:flex;align-items:center;gap:12px;margin-bottom:28px}
.eline{width:36px;height:1px;background:var(--gold)}
.eyebrow span{font-size:10px;letter-spacing:4px;text-transform:uppercase;color:var(--gold);font-weight:500}
.hero-title{font-family:'Cormorant Garamond',serif;font-size:clamp(52px,7.5vw,100px);line-height:.92;font-weight:300;margin-bottom:28px}
.hero-title i{color:var(--gold);font-style:italic;display:block}
.hero-sub{font-size:15px;color:var(--dim);line-height:1.75;max-width:460px;margin-bottom:48px;font-weight:300}
.hero-btns{display:flex;gap:16px;align-items:center}
.btn-g{background:var(--gold);color:var(--black);padding:15px 38px;font-size:11px;letter-spacing:3px;text-transform:uppercase;font-weight:600;text-decoration:none;display:inline-block;transition:background .3s,transform .2s}
.btn-g:hover{background:var(--gold-light);transform:translateY(-2px)}
.btn-ghost{color:var(--dim);font-size:11px;letter-spacing:2.5px;text-transform:uppercase;font-weight:500;text-decoration:none;display:flex;align-items:center;gap:8px;transition:color .3s}
.btn-ghost::after{content:'→';font-size:15px}
.btn-ghost:hover{color:var(--gold)}

.hero-stats{position:absolute;bottom:88px;right:64px;display:flex;gap:48px;z-index:3}
.hstat{text-align:right}
.hstat-n{font-family:'Cormorant Garamond',serif;font-size:44px;font-weight:300;color:var(--gold);line-height:1}
.hstat-l{font-size:9px;letter-spacing:2.5px;text-transform:uppercase;color:var(--dim);margin-top:4px}

.scroll-hint{position:absolute;bottom:36px;left:50%;transform:translateX(-50%);z-index:3;display:flex;flex-direction:column;align-items:center;gap:8px;animation:bob 2.2s ease-in-out infinite}
.scroll-hint span{font-size:8px;letter-spacing:3px;text-transform:uppercase;color:var(--dim)}
.sline{width:1px;height:44px;background:linear-gradient(to bottom,var(--gold),transparent);animation:sline 2s ease-in-out infinite}
@keyframes bob{0%,100%{transform:translateX(-50%) translateY(0)}50%{transform:translateX(-50%) translateY(6px)}}
@keyframes sline{0%{opacity:0;transform:scaleY(0);transform-origin:top}50%{opacity:1;transform:scaleY(1)}100%{opacity:0;transform:scaleY(0);transform-origin:bottom}}

/* TICKER */
.ticker{background:var(--gold);padding:13px 0;overflow:hidden;white-space:nowrap}
.ticker-track{display:inline-flex;animation:tick 22s linear infinite}
.ticker-item{font-size:10px;letter-spacing:3.5px;text-transform:uppercase;font-weight:700;color:var(--black);padding:0 36px}
.ticker-sep{opacity:.35;margin:0 4px}
@keyframes tick{from{transform:translateX(0)}to{transform:translateX(-50%)}}

/* SEARCH */
.search-sec{background:var(--surf);padding:72px 64px;border-top:.5px solid var(--gold-dim);border-bottom:.5px solid var(--gold-dim)}
.search-label{font-size:9px;letter-spacing:4px;text-transform:uppercase;color:var(--gold);font-weight:600;margin-bottom:28px;display:block}
.sbar{display:grid;grid-template-columns:1fr 1fr 1fr 180px;gap:1px;background:var(--gold-dim);border:1px solid var(--gold-dim)}
.sfield{background:var(--dark);padding:22px 26px;display:flex;flex-direction:column;gap:7px}
.sfield label{font-size:8px;letter-spacing:3.5px;text-transform:uppercase;color:var(--gold);font-weight:700}
.sfield input,.sfield select{background:transparent;border:none;outline:none;color:var(--white);font-family:'DM Sans',sans-serif;font-size:14px;font-weight:300;width:100%;-webkit-appearance:none}
.sfield input::placeholder{color:rgba(250,250,247,.25)}
.sfield select option{background:var(--dark)}
.sbtn{background:var(--gold);border:none;color:var(--black);font-family:'DM Sans',sans-serif;font-size:10px;letter-spacing:3px;text-transform:uppercase;font-weight:700;cursor:none;transition:background .3s}
.sbtn:hover{background:var(--gold-light)}
.stags{display:flex;flex-wrap:wrap;gap:9px;margin-top:22px}
.stag{font-size:10px;padding:6px 16px;border:.5px solid var(--gold-dim);color:var(--dim);cursor:none;transition:all .2s;letter-spacing:1px}
.stag:hover,.stag.active{border-color:var(--gold);color:var(--gold);background:var(--gold-faint)}

/* SECTION */
section{padding:112px 64px}
.sec-head{margin-bottom:64px}
.sec-eye{display:flex;align-items:center;gap:12px;margin-bottom:18px}
.sec-eye .l{width:28px;height:1px;background:var(--gold)}
.sec-eye span{font-size:9px;letter-spacing:4px;text-transform:uppercase;color:var(--gold);font-weight:500}
.sec-title{font-family:'Cormorant Garamond',serif;font-size:clamp(34px,4vw,54px);font-weight:300;line-height:1.1}
.sec-title em{color:var(--gold);font-style:italic}

/* PROPERTIES — pure CSS cards */
.props-sec{background:var(--off)}
.pgrid{display:grid;grid-template-columns:repeat(3,1fr);gap:2px}
.pcard{position:relative;overflow:hidden;cursor:none;min-height:380px;display:flex;flex-direction:column;justify-content:flex-end}
.pcard.feat{grid-column:span 2;min-height:480px}
.pcard-art{position:absolute;inset:0;transition:transform .6s}
.pcard:hover .pcard-art{transform:scale(1.04)}
.pcard-overlay{position:absolute;inset:0;background:linear-gradient(to top,rgba(8,8,8,.96) 0%,rgba(8,8,8,.4) 50%,rgba(8,8,8,.1) 100%)}
.pcard-body{position:relative;z-index:1;padding:28px}
.pbadge{display:inline-block;font-size:8px;letter-spacing:3px;text-transform:uppercase;background:var(--gold);color:var(--black);padding:5px 12px;font-weight:700;margin-bottom:12px}
.pname{font-family:'Cormorant Garamond',serif;font-size:22px;font-weight:400;line-height:1.2;margin-bottom:8px}
.pcard.feat .pname{font-size:36px}
.pmeta{display:flex;gap:16px;font-size:10px;color:var(--dim);letter-spacing:.8px}
.pprice{font-family:'Cormorant Garamond',serif;font-size:20px;color:var(--gold);margin-top:12px}
.pprice small{font-size:11px;color:var(--dim);font-family:'DM Sans',sans-serif;letter-spacing:1px}
.ptop{position:absolute;top:20px;right:20px;z-index:1;display:flex;gap:8px}
.ptag{font-size:8px;letter-spacing:2px;text-transform:uppercase;padding:5px 10px;background:rgba(8,8,8,.7);border:.5px solid var(--gold-dim);color:var(--gold);backdrop-filter:blur(8px)}

/* Card art styles — pure CSS geometry */
.art-premium{background:radial-gradient(ellipse at 40% 35%,rgba(201,168,76,.18) 0%,transparent 60%),linear-gradient(145deg,#1f1a08,#2a2008,#111)}
.art-ensuite{background:radial-gradient(ellipse at 60% 60%,rgba(40,120,80,.12) 0%,transparent 55%),linear-gradient(160deg,#0d1a0d,#101e10,#0a0a0a)}
.art-studio{background:radial-gradient(ellipse at 30% 50%,rgba(60,80,180,.1) 0%,transparent 50%),linear-gradient(135deg,#0d0d1e,#12121e,#0a0a0a)}
.art-shared{background:radial-gradient(ellipse at 70% 40%,rgba(180,80,60,.08) 0%,transparent 50%),linear-gradient(150deg,#1a0d0d,#1a1010,#0a0a0a)}

/* SVG floor plan lines on cards */
.fp{position:absolute;inset:0;opacity:.18}

/* SERVICES */
.services-sec{background:var(--black)}
.sgrid{display:grid;grid-template-columns:repeat(4,1fr);gap:1px;background:var(--gold-dim);border:.5px solid var(--gold-dim);margin-top:56px}
.svc{background:var(--off);padding:44px 32px;transition:background .3s;cursor:none}
.svc:hover{background:var(--dark)}
.svc-n{font-family:'Cormorant Garamond',serif;font-size:48px;font-weight:300;color:var(--gold-dim);line-height:1;margin-bottom:24px;transition:color .3s}
.svc:hover .svc-n{color:var(--gold)}
.svc-icon{width:46px;height:46px;border:.5px solid var(--gold-dim);display:grid;place-items:center;margin-bottom:18px;transition:border-color .3s}
.svc:hover .svc-icon{border-color:var(--gold)}
.svc-icon svg{width:20px;height:20px;stroke:var(--gold);fill:none;stroke-width:1.5;stroke-linecap:round;stroke-linejoin:round}
.svc-name{font-family:'Cormorant Garamond',serif;font-size:21px;font-weight:400;margin-bottom:10px;line-height:1.3}
.svc-desc{font-size:12px;color:var(--dim);line-height:1.75;font-weight:300}

/* ABOUT */
.about-wrap{display:grid;grid-template-columns:1fr 1fr;gap:0}
.about-left{background:var(--dark);position:relative;min-height:580px;overflow:hidden;display:flex;align-items:flex-end}
.about-left-art{position:absolute;inset:0}
.dir-card{position:relative;z-index:1;padding:52px}
.dir-avatar{width:110px;height:110px;border:2px solid var(--gold);display:grid;place-items:center;font-family:'Cormorant Garamond',serif;font-size:38px;color:var(--gold);font-weight:300;background:rgba(201,168,76,.05);margin-bottom:22px;position:relative}
.dir-avatar::after{content:'';position:absolute;bottom:-8px;right:-8px;width:100%;height:100%;border:1px solid rgba(201,168,76,.25)}
.dir-name{font-family:'Cormorant Garamond',serif;font-size:30px;font-weight:400;margin-bottom:5px}
.dir-role{font-size:9px;letter-spacing:4px;text-transform:uppercase;color:var(--gold);font-weight:500;margin-bottom:18px}
.dir-quote{font-family:'Cormorant Garamond',serif;font-size:17px;font-weight:300;font-style:italic;color:var(--dim);line-height:1.65;max-width:340px}
.about-right{background:var(--surf);padding:72px 64px;display:flex;flex-direction:column;justify-content:center}
.about-p{font-size:14px;color:var(--dim);line-height:1.85;font-weight:300;margin-bottom:20px}
.vals{display:grid;grid-template-columns:1fr 1fr;gap:1px;background:var(--gold-dim);border:.5px solid var(--gold-dim);margin-top:44px}
.val{background:var(--dark);padding:22px 24px}
.val-sym{font-size:18px;color:var(--gold);margin-bottom:8px}
.val-name{font-size:10px;letter-spacing:2.5px;text-transform:uppercase;font-weight:600;margin-bottom:5px}
.val-desc{font-size:11px;color:var(--dim);line-height:1.6}

/* TESTIMONIALS */
.test-sec{background:var(--off);position:relative}
.test-sec::before{content:'';position:absolute;top:0;left:50%;width:1px;height:100%;background:var(--gold-dim)}
.tgrid{display:grid;grid-template-columns:1fr 1fr;gap:72px;margin-top:60px}
.titem{}
.tquote{font-family:'Cormorant Garamond',serif;font-size:22px;font-weight:300;font-style:italic;line-height:1.6;margin-bottom:28px}
.tquote::before{content:'"';font-size:72px;color:var(--gold);display:block;line-height:0;margin-bottom:22px;font-style:normal;margin-left:-4px}
.tauthor{display:flex;align-items:center;gap:14px}
.tavatar{width:44px;height:44px;border-radius:50%;background:var(--gold);display:grid;place-items:center;font-family:'Cormorant Garamond',serif;font-size:16px;font-weight:600;color:var(--black);flex-shrink:0}
.tname{font-size:13px;font-weight:500;margin-bottom:3px}
.trole{font-size:10px;color:var(--gold);letter-spacing:2px;text-transform:uppercase}
.stars{color:var(--gold);font-size:11px;margin-bottom:10px;letter-spacing:2px}

/* AREAS */
.areas-sec{background:var(--black)}
.agrid{display:grid;grid-template-columns:repeat(5,1fr);gap:1px;background:var(--gold-dim);border:.5px solid var(--gold-dim);margin-top:60px}
.aitem{background:var(--off);padding:34px 22px;cursor:none;position:relative;overflow:hidden;transition:background .3s}
.aitem::after{content:'';position:absolute;bottom:0;left:0;right:0;height:2px;background:var(--gold);transform:scaleX(0);transform-origin:left;transition:transform .4s}
.aitem:hover{background:var(--dark)}
.aitem:hover::after{transform:scaleX(1)}
.aname{font-family:'Cormorant Garamond',serif;font-size:20px;font-weight:400;margin-bottom:7px}
.acount{font-size:10px;color:var(--gold);letter-spacing:2px}
.auni{font-size:10px;color:var(--dim);margin-top:7px;line-height:1.5}

/* CTA */
.cta-sec{background:var(--gold);padding:96px 64px;position:relative;overflow:hidden}
.cta-sec::before{content:'SN';position:absolute;right:-20px;top:-40px;font-family:'Cormorant Garamond',serif;font-size:280px;font-weight:700;color:rgba(0,0,0,.06);line-height:1;pointer-events:none}
.cta-inner{position:relative;max-width:680px}
.cta-title{font-family:'Cormorant Garamond',serif;font-size:clamp(38px,5vw,68px);font-weight:300;color:var(--black);line-height:1.1;margin-bottom:20px}
.cta-sub{font-size:15px;color:rgba(8,8,8,.55);margin-bottom:44px;font-weight:300}
.cta-btns{display:flex;gap:14px}
.btn-dark{background:var(--black);color:var(--white);padding:15px 38px;font-size:11px;letter-spacing:3px;text-transform:uppercase;font-weight:600;text-decoration:none;display:inline-block;transition:background .3s}
.btn-dark:hover{background:#222}
.btn-od{border:1.5px solid rgba(8,8,8,.35);color:var(--black);padding:15px 38px;font-size:11px;letter-spacing:3px;text-transform:uppercase;font-weight:600;text-decoration:none;display:inline-block;transition:border-color .3s}
.btn-od:hover{border-color:var(--black)}

/* CONTACT */
.contact-wrap{display:grid;grid-template-columns:1fr 1fr;gap:0}
.cinfo{background:var(--surf);padding:72px 64px}
.cdet{display:flex;gap:18px;align-items:flex-start;margin-bottom:32px}
.cdet-icon{width:42px;height:42px;border:.5px solid var(--gold-dim);display:grid;place-items:center;flex-shrink:0;font-size:17px}
.cdet-label{font-size:8px;letter-spacing:3px;text-transform:uppercase;color:var(--gold);font-weight:700;margin-bottom:4px}
.cdet-val{font-size:13px;color:var(--dim);line-height:1.65}
.cform{background:var(--dark);padding:72px 64px}
.form-tag{font-size:9px;letter-spacing:4px;text-transform:uppercase;color:var(--gold);font-weight:600;margin-bottom:28px;display:block}
.frow{display:grid;grid-template-columns:1fr 1fr;gap:14px;margin-bottom:14px}
.fg{margin-bottom:14px}
.fg label{display:block;font-size:8px;letter-spacing:3px;text-transform:uppercase;color:var(--gold);font-weight:700;margin-bottom:9px}
.fg input,.fg select,.fg textarea{width:100%;background:var(--surf);border:.5px solid var(--gold-dim);color:var(--white);font-family:'DM Sans',sans-serif;font-size:13px;padding:13px 16px;outline:none;transition:border-color .3s;-webkit-appearance:none}
.fg input:focus,.fg select:focus,.fg textarea:focus{border-color:var(--gold)}
.fg input::placeholder,.fg textarea::placeholder{color:rgba(250,250,247,.2)}
.fg select option{background:var(--dark)}
.fg textarea{resize:vertical;min-height:110px}
.fsub{width:100%;background:var(--gold);border:none;color:var(--black);font-family:'DM Sans',sans-serif;font-size:11px;letter-spacing:3px;text-transform:uppercase;font-weight:700;padding:17px;cursor:none;transition:background .3s;margin-top:6px}
.fsub:hover{background:var(--gold-light)}

/* FOOTER */
footer{background:var(--black);padding:60px 64px 28px;border-top:.5px solid var(--gold-dim)}
.ftop{display:grid;grid-template-columns:2fr 1fr 1fr 1fr;gap:52px;margin-bottom:52px}
.ftagline{font-family:'Cormorant Garamond',serif;font-size:15px;color:var(--dim);font-weight:300;font-style:italic;margin:18px 0 24px;line-height:1.65}
.fcol h4{font-size:8px;letter-spacing:4px;text-transform:uppercase;color:var(--gold);font-weight:700;margin-bottom:22px}
.fcol a{display:block;color:var(--dim);text-decoration:none;font-size:12px;margin-bottom:11px;transition:color .3s}
.fcol a:hover{color:var(--gold)}
.fbot{border-top:.5px solid var(--faint);padding-top:24px;display:flex;justify-content:space-between;align-items:center}
.fbot p{font-size:11px;color:rgba(250,250,247,.28)}
.fmark{font-family:'Cormorant Garamond',serif;font-size:12px;color:var(--gold);letter-spacing:3px;text-transform:uppercase}

/* REVEAL */
.rev{opacity:0;transform:translateY(28px);transition:opacity .75s ease,transform .75s ease}
.rev.in{opacity:1;transform:translateY(0)}
.d1{transition-delay:.1s}.d2{transition-delay:.2s}.d3{transition-delay:.3s}

/* Decorative geometry for about section background */
.geo-lines{position:absolute;inset:0;opacity:.07}
</style>
</head>
<body>

<div id="cur"></div>
<div id="ring"></div>

<!-- NAV -->
<nav id="nav">
  <a href="#" class="logo">
    <div class="logomark">SN</div>
    <div class="logotext"><b>SN</b> Properties</div>
  </a>
  <div class="nav-links">
    <a href="#props">Properties</a>
    <a href="#services">Services</a>
    <a href="#areas">Areas</a>
    <a href="#about">About</a>
    <a href="#contact" class="ncta">Book Viewing</a>
  </div>
</nav>

<!-- HERO -->
<div class="hero" id="top">
  <div class="hero-art"></div>

  <!-- Pure SVG building illustration -->
  <svg class="hero-buildings" viewBox="0 0 700 800" preserveAspectRatio="xMaxYMax slice" xmlns="http://www.w3.org/2000/svg">
    <defs>
      <linearGradient id="gW" x1="0" y1="0" x2="0" y2="1">
        <stop offset="0%" stop-color="#C9A84C" stop-opacity=".18"/>
        <stop offset="100%" stop-color="#C9A84C" stop-opacity=".04"/>
      </linearGradient>
      <linearGradient id="gW2" x1="0" y1="0" x2="0" y2="1">
        <stop offset="0%" stop-color="#C9A84C" stop-opacity=".1"/>
        <stop offset="100%" stop-color="#C9A84C" stop-opacity=".02"/>
      </linearGradient>
    </defs>
    <!-- Sky glow -->
    <ellipse cx="420" cy="200" rx="300" ry="180" fill="rgba(201,168,76,.06)"/>
    <!-- Tall tower left -->
    <rect x="80" y="120" width="90" height="680" fill="url(#gW2)" stroke="rgba(201,168,76,.2)" stroke-width=".5"/>
    <rect x="84" y="130" width="18" height="26" fill="rgba(201,168,76,.12)"/>
    <rect x="108" y="130" width="18" height="26" fill="rgba(201,168,76,.08)"/>
    <rect x="132" y="130" width="18" height="26" fill="rgba(201,168,76,.1)"/>
    <rect x="84" y="170" width="18" height="26" fill="rgba(201,168,76,.07)"/>
    <rect x="108" y="170" width="18" height="26" fill="rgba(201,168,76,.15)"/>
    <rect x="132" y="170" width="18" height="26" fill="rgba(201,168,76,.08)"/>
    <rect x="84" y="210" width="18" height="26" fill="rgba(201,168,76,.1)"/>
    <rect x="108" y="210" width="18" height="26" fill="rgba(201,168,76,.06)"/>
    <rect x="132" y="210" width="18" height="26" fill="rgba(201,168,76,.12)"/>
    <rect x="84" y="250" width="18" height="26" fill="rgba(201,168,76,.08)"/>
    <rect x="108" y="250" width="18" height="26" fill="rgba(201,168,76,.1)"/>
    <rect x="132" y="250" width="18" height="26" fill="rgba(201,168,76,.07)"/>
    <rect x="84" y="290" width="18" height="26" fill="rgba(201,168,76,.13)"/>
    <rect x="108" y="290" width="18" height="26" fill="rgba(201,168,76,.08)"/>
    <rect x="132" y="290" width="18" height="26" fill="rgba(201,168,76,.1)"/>
    <!-- Needle spire -->
    <line x1="125" y1="0" x2="125" y2="120" stroke="rgba(201,168,76,.35)" stroke-width="1.5"/>
    <polygon points="118,120 132,120 128,0 122,0" fill="rgba(201,168,76,.12)"/>

    <!-- Wide mid building -->
    <rect x="200" y="280" width="140" height="520" fill="url(#gW)" stroke="rgba(201,168,76,.25)" stroke-width=".5"/>
    <rect x="210" y="295" width="24" height="36" fill="rgba(201,168,76,.15)"/>
    <rect x="242" y="295" width="24" height="36" fill="rgba(201,168,76,.1)"/>
    <rect x="274" y="295" width="24" height="36" fill="rgba(201,168,76,.18)"/>
    <rect x="306" y="295" width="24" height="36" fill="rgba(201,168,76,.1)"/>
    <rect x="210" y="345" width="24" height="36" fill="rgba(201,168,76,.08)"/>
    <rect x="242" y="345" width="24" height="36" fill="rgba(201,168,76,.14)"/>
    <rect x="274" y="345" width="24" height="36" fill="rgba(201,168,76,.1)"/>
    <rect x="306" y="345" width="24" height="36" fill="rgba(201,168,76,.12)"/>
    <rect x="210" y="395" width="24" height="36" fill="rgba(201,168,76,.16)"/>
    <rect x="242" y="395" width="24" height="36" fill="rgba(201,168,76,.07)"/>
    <rect x="274" y="395" width="24" height="36" fill="rgba(201,168,76,.12)"/>
    <rect x="306" y="395" width="24" height="36" fill="rgba(201,168,76,.09)"/>
    <rect x="210" y="445" width="24" height="36" fill="rgba(201,168,76,.11)"/>
    <rect x="242" y="445" width="24" height="36" fill="rgba(201,168,76,.15)"/>
    <rect x="274" y="445" width="24" height="36" fill="rgba(201,168,76,.08)"/>
    <rect x="306" y="445" width="24" height="36" fill="rgba(201,168,76,.13)"/>
    <!-- Roof terrace line -->
    <line x1="200" y1="282" x2="340" y2="282" stroke="rgba(201,168,76,.5)" stroke-width=".75"/>

    <!-- Right tower -->
    <rect x="390" y="180" width="100" height="620" fill="url(#gW2)" stroke="rgba(201,168,76,.18)" stroke-width=".5"/>
    <rect x="400" y="195" width="20" height="30" fill="rgba(201,168,76,.12)"/>
    <rect x="428" y="195" width="20" height="30" fill="rgba(201,168,76,.08)"/>
    <rect x="456" y="195" width="20" height="30" fill="rgba(201,168,76,.14)"/>
    <rect x="400" y="240" width="20" height="30" fill="rgba(201,168,76,.09)"/>
    <rect x="428" y="240" width="20" height="30" fill="rgba(201,168,76,.15)"/>
    <rect x="456" y="240" width="20" height="30" fill="rgba(201,168,76,.08)"/>
    <rect x="400" y="285" width="20" height="30" fill="rgba(201,168,76,.13)"/>
    <rect x="428" y="285" width="20" height="30" fill="rgba(201,168,76,.07)"/>
    <rect x="456" y="285" width="20" height="30" fill="rgba(201,168,76,.11)"/>
    <rect x="400" y="330" width="20" height="30" fill="rgba(201,168,76,.1)"/>
    <rect x="428" y="330" width="20" height="30" fill="rgba(201,168,76,.14)"/>
    <rect x="456" y="330" width="20" height="30" fill="rgba(201,168,76,.08)"/>

    <!-- Far right low building -->
    <rect x="520" y="420" width="180" height="380" fill="url(#gW2)" stroke="rgba(201,168,76,.15)" stroke-width=".5"/>
    <rect x="534" y="436" width="22" height="32" fill="rgba(201,168,76,.1)"/>
    <rect x="564" y="436" width="22" height="32" fill="rgba(201,168,76,.14)"/>
    <rect x="594" y="436" width="22" height="32" fill="rgba(201,168,76,.08)"/>
    <rect x="624" y="436" width="22" height="32" fill="rgba(201,168,76,.12)"/>
    <rect x="654" y="436" width="22" height="32" fill="rgba(201,168,76,.09)"/>
    <rect x="534" y="485" width="22" height="32" fill="rgba(201,168,76,.13)"/>
    <rect x="564" y="485" width="22" height="32" fill="rgba(201,168,76,.08)"/>
    <rect x="594" y="485" width="22" height="32" fill="rgba(201,168,76,.11)"/>
    <rect x="624" y="485" width="22" height="32" fill="rgba(201,168,76,.15)"/>
    <rect x="654" y="485" width="22" height="32" fill="rgba(201,168,76,.08)"/>

    <!-- Ground line -->
    <line x1="0" y1="798" x2="700" y2="798" stroke="rgba(201,168,76,.3)" stroke-width=".5"/>
    <!-- Horizon glow -->
    <rect x="0" y="780" width="700" height="20" fill="url(#gW2)"/>
  </svg>

  <div class="hero-grad"></div>

  <div class="hero-content">
    <div class="eyebrow">
      <div class="eline"></div>
      <span>Student Living · United Kingdom</span>
    </div>
    <h1 class="hero-title">
      Your Home<br>
      <i>Away From</i><br>
      Home.
    </h1>
    <p class="hero-sub">Premium student accommodation across the UK's top university cities. Bills included, fully furnished, zero hassle.</p>
    <div class="hero-btns">
      <a href="#props" class="btn-g">View Properties</a>
      <a href="#contact" class="btn-ghost">Book a Viewing</a>
    </div>
  </div>

  <div class="hero-stats">
    <div class="hstat"><div class="hstat-n">500+</div><div class="hstat-l">Properties</div></div>
    <div class="hstat"><div class="hstat-n">12+</div><div class="hstat-l">UK Cities</div></div>
    <div class="hstat"><div class="hstat-n">98%</div><div class="hstat-l">Satisfaction</div></div>
  </div>

  <div class="scroll-hint"><span>Scroll</span><div class="sline"></div></div>
</div>

<!-- TICKER -->
<div class="ticker">
  <div class="ticker-track">
    <span class="ticker-item">Student Accommodation <span class="ticker-sep">◆</span></span>
    <span class="ticker-item">Bills Included <span class="ticker-sep">◆</span></span>
    <span class="ticker-item">En-Suite Rooms <span class="ticker-sep">◆</span></span>
    <span class="ticker-item">Studio Flats <span class="ticker-sep">◆</span></span>
    <span class="ticker-item">Shared Houses <span class="ticker-sep">◆</span></span>
    <span class="ticker-item">London · Manchester · Birmingham <span class="ticker-sep">◆</span></span>
    <span class="ticker-item">Student Accommodation <span class="ticker-sep">◆</span></span>
    <span class="ticker-item">Bills Included <span class="ticker-sep">◆</span></span>
    <span class="ticker-item">En-Suite Rooms <span class="ticker-sep">◆</span></span>
    <span class="ticker-item">Studio Flats <span class="ticker-sep">◆</span></span>
    <span class="ticker-item">Shared Houses <span class="ticker-sep">◆</span></span>
    <span class="ticker-item">London · Manchester · Birmingham <span class="ticker-sep">◆</span></span>
  </div>
</div>

<!-- SEARCH -->
<div class="search-sec">
  <span class="search-label">Find Your Perfect Room</span>
  <div class="sbar">
    <div class="sfield">
      <label>Location</label>
      <input type="text" placeholder="City or University...">
    </div>
    <div class="sfield">
      <label>Room Type</label>
      <select>
        <option value="">All Types</option>
        <option>En-Suite Room</option>
        <option>Studio Flat</option>
        <option>Shared House</option>
        <option>Premium Studio</option>
      </select>
    </div>
    <div class="sfield">
      <label>Max Budget / Week</label>
      <select>
        <option value="">Any Price</option>
        <option>Up to £100/week</option>
        <option>Up to £150/week</option>
        <option>Up to £200/week</option>
        <option>£200+/week</option>
      </select>
    </div>
    <button class="sbtn" id="sbtn">Search</button>
  </div>
  <div class="stags">
    <span class="stag">Bills Included</span>
    <span class="stag">WiFi Included</span>
    <span class="stag">Furnished</span>
    <span class="stag">Near Campus</span>
    <span class="stag">City Centre</span>
    <span class="stag">Short-term</span>
    <span class="stag">Pet Friendly</span>
    <span class="stag">International Welcome</span>
  </div>
</div>

<!-- PROPERTIES -->
<section class="props-sec" id="props">
  <div class="sec-head rev">
    <div class="sec-eye"><div class="l"></div><span>Featured Listings</span></div>
    <h2 class="sec-title">Premium Student <em>Accommodation</em></h2>
  </div>
  <div class="pgrid">

    <!-- Featured — large floor plan SVG -->
    <div class="pcard feat">
      <div class="pcard-art art-premium">
        <svg class="fp" viewBox="0 0 600 480" xmlns="http://www.w3.org/2000/svg" preserveAspectRatio="xMidYMid slice">
          <rect x="40" y="30" width="520" height="420" rx="2" fill="none" stroke="#C9A84C" stroke-width="1"/>
          <rect x="60" y="50" width="200" height="160" rx="1" fill="rgba(201,168,76,.15)" stroke="#C9A84C" stroke-width=".5"/>
          <rect x="280" y="50" width="260" height="80" rx="1" fill="rgba(201,168,76,.1)" stroke="#C9A84C" stroke-width=".5"/>
          <rect x="280" y="145" width="120" height="65" rx="1" fill="rgba(201,168,76,.12)" stroke="#C9A84C" stroke-width=".5"/>
          <rect x="415" y="145" width="125" height="65" rx="1" fill="rgba(201,168,76,.08)" stroke="#C9A84C" stroke-width=".5"/>
          <rect x="60" y="225" width="540" height="205" rx="1" fill="rgba(201,168,76,.08)" stroke="#C9A84C" stroke-width=".5"/>
          <text x="155" y="138" text-anchor="middle" fill="#C9A84C" font-size="9" font-family="DM Sans" opacity=".6" letter-spacing="2">BEDROOM</text>
          <text x="408" y="96" text-anchor="middle" fill="#C9A84C" font-size="9" font-family="DM Sans" opacity=".6" letter-spacing="2">KITCHEN</text>
          <text x="338" y="182" text-anchor="middle" fill="#C9A84C" font-size="9" font-family="DM Sans" opacity=".5" letter-spacing="1.5">BATH</text>
          <text x="475" y="182" text-anchor="middle" fill="#C9A84C" font-size="9" font-family="DM Sans" opacity=".5" letter-spacing="1.5">WC</text>
          <text x="330" y="330" text-anchor="middle" fill="#C9A84C" font-size="9" font-family="DM Sans" opacity=".6" letter-spacing="2">LIVING ROOM</text>
          <!-- Compass -->
          <circle cx="556" cy="46" r="12" fill="none" stroke="#C9A84C" stroke-width=".5" opacity=".5"/>
          <line x1="556" y1="36" x2="556" y2="56" stroke="#C9A84C" stroke-width=".5" opacity=".5"/>
          <line x1="546" y1="46" x2="566" y2="46" stroke="#C9A84C" stroke-width=".5" opacity=".5"/>
          <text x="556" y="40" text-anchor="middle" fill="#C9A84C" font-size="6" opacity=".6">N</text>
        </svg>
      </div>
      <div class="pcard-overlay"></div>
      <div class="ptop"><span class="ptag">Bills Incl.</span><span class="ptag">New</span></div>
      <div class="pcard-body">
        <span class="pbadge">Premium Studio</span>
        <div class="pname">The Icon Residences, London</div>
        <div class="pmeta"><span>📍 North Eastham</span><span>Private Studio · 1 Bath</span></div>
        <div class="pprice">£195 <small>/ week · all bills included</small></div>
      </div>
    </div>

    <!-- En-Suite -->
    <div class="pcard">
      <div class="pcard-art art-ensuite">
        <svg class="fp" viewBox="0 0 300 400" xmlns="http://www.w3.org/2000/svg" preserveAspectRatio="xMidYMid slice">
          <rect x="20" y="20" width="260" height="360" rx="2" fill="none" stroke="#4a9a6a" stroke-width=".75"/>
          <rect x="36" y="36" width="110" height="140" rx="1" fill="rgba(74,154,106,.12)" stroke="#4a9a6a" stroke-width=".5"/>
          <rect x="160" y="36" width="100" height="80" rx="1" fill="rgba(74,154,106,.1)" stroke="#4a9a6a" stroke-width=".5"/>
          <rect x="160" y="130" width="100" height="46" rx="1" fill="rgba(74,154,106,.08)" stroke="#4a9a6a" stroke-width=".5"/>
          <rect x="36" y="192" width="224" height="168" rx="1" fill="rgba(74,154,106,.08)" stroke="#4a9a6a" stroke-width=".5"/>
          <text x="91" y="112" text-anchor="middle" fill="#4a9a6a" font-size="8" font-family="DM Sans" opacity=".6" letter-spacing="1.5">BEDROOM</text>
          <text x="208" y="82" text-anchor="middle" fill="#4a9a6a" font-size="8" font-family="DM Sans" opacity=".5" letter-spacing="1">ENSUITE</text>
          <text x="148" y="285" text-anchor="middle" fill="#4a9a6a" font-size="8" font-family="DM Sans" opacity=".5" letter-spacing="1.5">SHARED AREAS</text>
        </svg>
      </div>
      <div class="pcard-overlay"></div>
      <div class="ptop"><span class="ptag">Popular</span></div>
      <div class="pcard-body">
        <span class="pbadge">En-Suite</span>
        <div class="pname">University Quarter, Manchester</div>
        <div class="pmeta"><span>Shared House</span><span>5 Rooms</span></div>
        <div class="pprice">£130 <small>/ week</small></div>
      </div>
    </div>

    <!-- Studio -->
    <div class="pcard">
      <div class="pcard-art art-studio">
        <svg class="fp" viewBox="0 0 300 400" xmlns="http://www.w3.org/2000/svg" preserveAspectRatio="xMidYMid slice">
          <rect x="20" y="20" width="260" height="360" rx="2" fill="none" stroke="#6464c8" stroke-width=".75"/>
          <rect x="36" y="36" width="224" height="180" rx="1" fill="rgba(100,100,200,.1)" stroke="#6464c8" stroke-width=".5"/>
          <rect x="36" y="230" width="104" height="130" rx="1" fill="rgba(100,100,200,.1)" stroke="#6464c8" stroke-width=".5"/>
          <rect x="155" y="230" width="105" height="58" rx="1" fill="rgba(100,100,200,.08)" stroke="#6464c8" stroke-width=".5"/>
          <rect x="155" y="302" width="105" height="58" rx="1" fill="rgba(100,100,200,.06)" stroke="#6464c8" stroke-width=".5"/>
          <text x="148" y="132" text-anchor="middle" fill="#6464c8" font-size="8" font-family="DM Sans" opacity=".6" letter-spacing="1.5">OPEN PLAN STUDIO</text>
          <text x="88" y="298" text-anchor="middle" fill="#6464c8" font-size="8" font-family="DM Sans" opacity=".5" letter-spacing="1">BEDROOM</text>
          <text x="205" y="264" text-anchor="middle" fill="#6464c8" font-size="8" font-family="DM Sans" opacity=".5" letter-spacing="1">BATH</text>
          <text x="205" y="335" text-anchor="middle" fill="#6464c8" font-size="8" font-family="DM Sans" opacity=".5" letter-spacing="1">WC</text>
        </svg>
      </div>
      <div class="pcard-overlay"></div>
      <div class="ptop"><span class="ptag">WiFi+Bills</span></div>
      <div class="pcard-body">
        <span class="pbadge">Studio</span>
        <div class="pname">Meridian House, Birmingham</div>
        <div class="pmeta"><span>Self-Contained</span><span>WiFi + Bills</span></div>
        <div class="pprice">£165 <small>/ week</small></div>
      </div>
    </div>

    <!-- Shared -->
    <div class="pcard">
      <div class="pcard-art art-shared">
        <svg class="fp" viewBox="0 0 300 400" xmlns="http://www.w3.org/2000/svg" preserveAspectRatio="xMidYMid slice">
          <rect x="20" y="20" width="260" height="360" rx="2" fill="none" stroke="#c86464" stroke-width=".75"/>
          <rect x="36" y="36" width="104" height="120" rx="1" fill="rgba(200,100,100,.08)" stroke="#c86464" stroke-width=".5"/>
          <rect x="156" y="36" width="104" height="120" rx="1" fill="rgba(200,100,100,.08)" stroke="#c86464" stroke-width=".5"/>
          <rect x="36" y="172" width="104" height="120" rx="1" fill="rgba(200,100,100,.08)" stroke="#c86464" stroke-width=".5"/>
          <rect x="156" y="172" width="104" height="120" rx="1" fill="rgba(200,100,100,.08)" stroke="#c86464" stroke-width=".5"/>
          <rect x="36" y="308" width="224" height="72" rx="1" fill="rgba(200,100,100,.06)" stroke="#c86464" stroke-width=".5"/>
          <text x="88" y="100" text-anchor="middle" fill="#c86464" font-size="7" font-family="DM Sans" opacity=".5" letter-spacing="1">ROOM 1</text>
          <text x="208" y="100" text-anchor="middle" fill="#c86464" font-size="7" font-family="DM Sans" opacity=".5" letter-spacing="1">ROOM 2</text>
          <text x="88" y="236" text-anchor="middle" fill="#c86464" font-size="7" font-family="DM Sans" opacity=".5" letter-spacing="1">ROOM 3</text>
          <text x="208" y="236" text-anchor="middle" fill="#c86464" font-size="7" font-family="DM Sans" opacity=".5" letter-spacing="1">ROOM 4</text>
          <text x="148" y="348" text-anchor="middle" fill="#c86464" font-size="7" font-family="DM Sans" opacity=".5" letter-spacing="1.5">SHARED KITCHEN</text>
        </svg>
      </div>
      <div class="pcard-overlay"></div>
      <div class="ptop"><span class="ptag">2 Left</span></div>
      <div class="pcard-body">
        <span class="pbadge">Shared House</span>
        <div class="pname">Scholars Court, Leeds</div>
        <div class="pmeta"><span>6 Bedrooms</span><span>Near Uni</span></div>
        <div class="pprice">£95 <small>/ week</small></div>
      </div>
    </div>

  </div>
  <div style="text-align:center;margin-top:48px">
    <a href="#contact" class="btn-g">View All 500+ Properties</a>
  </div>
</section>

<!-- SERVICES -->
<section class="services-sec" id="services">
  <div class="sec-head rev">
    <div class="sec-eye"><div class="l"></div><span>What We Offer</span></div>
    <h2 class="sec-title">Everything a Student <em>Needs</em></h2>
  </div>
  <div class="sgrid">
    <div class="svc rev">
      <div class="svc-n">01</div>
      <div class="svc-icon">
        <svg viewBox="0 0 24 24"><path d="M3 9l9-7 9 7v11a2 2 0 01-2 2H5a2 2 0 01-2-2z"/><polyline points="9,22 9,12 15,12 15,22"/></svg>
      </div>
      <div class="svc-name">Student Lettings</div>
      <p class="svc-desc">Rooms in shared houses and private studios near campuses across the UK. Flexible tenancies from 6–52 weeks.</p>
    </div>
    <div class="svc rev d1">
      <div class="svc-n">02</div>
      <div class="svc-icon">
        <svg viewBox="0 0 24 24"><circle cx="12" cy="12" r="10"/><path d="M12 8v4l3 3"/></svg>
      </div>
      <div class="svc-name">Bills Management</div>
      <p class="svc-desc">All-inclusive packages covering gas, electric, water, broadband, and TV licence. One payment, zero surprises.</p>
    </div>
    <div class="svc rev d2">
      <div class="svc-n">03</div>
      <div class="svc-icon">
        <svg viewBox="0 0 24 24"><path d="M17 21v-2a4 4 0 00-4-4H5a4 4 0 00-4 4v2"/><circle cx="9" cy="7" r="4"/><path d="M23 21v-2a4 4 0 00-3-3.87"/><path d="M16 3.13a4 4 0 010 7.75"/></svg>
      </div>
      <div class="svc-name">Property Management</div>
      <p class="svc-desc">24/7 tenant support, maintenance, cleaning and inspection. Your comfort is our constant priority.</p>
    </div>
    <div class="svc rev d3">
      <div class="svc-n">04</div>
      <div class="svc-icon">
        <svg viewBox="0 0 24 24"><line x1="12" y1="1" x2="12" y2="23"/><path d="M17 5H9.5a3.5 3.5 0 100 7h5a3.5 3.5 0 110 7H6"/></svg>
      </div>
      <div class="svc-name">Investment Consultancy</div>
      <p class="svc-desc">Strategic advice for landlords and investors entering the profitable UK student property sector.</p>
    </div>
  </div>
</section>

<!-- ABOUT -->
<div class="about-wrap" id="about">
  <div class="about-left">
    <div class="about-left-art">
      <!-- Architectural blueprint SVG -->
      <svg class="geo-lines" viewBox="0 0 500 600" xmlns="http://www.w3.org/2000/svg" style="position:absolute;inset:0;width:100%;height:100%;opacity:.12">
        <rect x="50" y="40" width="400" height="520" rx="2" fill="none" stroke="#C9A84C" stroke-width="1"/>
        <rect x="80" y="80" width="160" height="200" rx="1" fill="none" stroke="#C9A84C" stroke-width=".75"/>
        <rect x="260" y="80" width="160" height="90" rx="1" fill="none" stroke="#C9A84C" stroke-width=".75"/>
        <rect x="260" y="185" width="73" height="95" rx="1" fill="none" stroke="#C9A84C" stroke-width=".75"/>
        <rect x="347" y="185" width="73" height="95" rx="1" fill="none" stroke="#C9A84C" stroke-width=".75"/>
        <rect x="80" y="295" width="340" height="240" rx="1" fill="none" stroke="#C9A84C" stroke-width=".75"/>
        <circle cx="250" cy="540" r="8" fill="none" stroke="#C9A84C" stroke-width=".5"/>
        <line x1="242" y1="540" x2="258" y2="540" stroke="#C9A84C" stroke-width=".5"/>
        <line x1="250" y1="532" x2="250" y2="548" stroke="#C9A84C" stroke-width=".5"/>
        <line x1="50" y1="300" x2="80" y2="300" stroke="#C9A84C" stroke-width=".5"/>
        <line x1="420" y1="300" x2="450" y2="300" stroke="#C9A84C" stroke-width=".5"/>
      </svg>
      <!-- Ambient gold glow -->
      <div style="position:absolute;inset:0;background:radial-gradient(ellipse at 50% 40%,rgba(201,168,76,.1) 0%,transparent 65%)"></div>
    </div>
    <div class="dir-card">
      <div class="dir-avatar">NK</div>
      <div class="dir-name">Nagesh Kadari</div>
      <div class="dir-role">Director, SN Properties UK</div>
      <p class="dir-quote">"Every student deserves a space that feels like home — safe, comfortable, and ready to support their best years."</p>
    </div>
  </div>
  <div class="about-right">
    <div class="sec-eye" style="margin-bottom:18px"><div class="l"></div><span>Our Story</span></div>
    <h2 class="sec-title" style="margin-bottom:26px">Building Spaces.<br><em>Building Trust.</em></h2>
    <p class="about-p">SN Properties UK was founded on a single belief: that finding student accommodation should never be stressful. Led by Director Nagesh Kadari, we have spent years building a portfolio of premium, well-maintained properties close to the UK's finest universities.</p>
    <p class="about-p">From our iconic offices in North Eastham, London, we manage lettings across 12 cities — offering everything from cosy en-suite rooms in shared houses to fully self-contained studio flats, always with bills included and local teams on the ground.</p>
    <div class="vals">
      <div class="val"><div class="val-sym">✦</div><div class="val-name">Integrity</div><div class="val-desc">Honest advice. Always.</div></div>
      <div class="val"><div class="val-sym">◈</div><div class="val-name">Trust</div><div class="val-desc">Built on reliability and transparency.</div></div>
      <div class="val"><div class="val-sym">⬡</div><div class="val-name">Client Focus</div><div class="val-desc">Your goals, our priority.</div></div>
      <div class="val"><div class="val-sym">▲</div><div class="val-name">Results Driven</div><div class="val-desc">Delivering lasting value.</div></div>
    </div>
  </div>
</div>

<!-- TESTIMONIALS -->
<section class="test-sec">
  <div class="sec-head rev">
    <div class="sec-eye"><div class="l"></div><span>Student Reviews</span></div>
    <h2 class="sec-title">What Our <em>Students Say</em></h2>
  </div>
  <div class="tgrid">
    <div class="titem rev"><div class="stars">★★★★★</div><p class="tquote">SN Properties made moving to London for university completely stress-free. My studio was immaculate, bills sorted, and the team responded to every query within hours.</p><div class="tauthor"><div class="tavatar">AS</div><div><div class="tname">Aisha Sharma</div><div class="trole">MSc Finance · UCL</div></div></div></div>
    <div class="titem rev d1"><div class="stars">★★★★★</div><p class="tquote">I found my shared house through SN Properties and it was the best decision. Nagesh's team is professional, transparent, and genuinely cares about students.</p><div class="tauthor"><div class="tavatar">JC</div><div><div class="tname">James Carter</div><div class="trole">LLB Law · University of Manchester</div></div></div></div>
    <div class="titem rev"><div class="stars">★★★★★</div><p class="tquote">The en-suite room was everything the listing promised and more. Perfect location, 10 minutes from campus. Recommending SN Properties to every student I know.</p><div class="tauthor"><div class="tavatar">PM</div><div><div class="tname">Priya Mehta</div><div class="trole">BEng Engineering · Aston University</div></div></div></div>
    <div class="titem rev d1"><div class="stars">★★★★★</div><p class="tquote">As an international student I was nervous about the whole process. SN Properties guided me through everything — deposit, contracts, move-in. Absolute lifesavers.</p><div class="tauthor"><div class="tavatar">LW</div><div><div class="tname">Li Wei</div><div class="trole">MBA Business · Leeds Beckett</div></div></div></div>
  </div>
</section>

<!-- AREAS -->
<section class="areas-sec" id="areas">
  <div class="sec-head rev">
    <div class="sec-eye"><div class="l"></div><span>Where We Operate</span></div>
    <h2 class="sec-title">Your City, <em>Our Expertise</em></h2>
  </div>
  <div class="agrid">
    <div class="aitem rev"><div class="aname">London</div><div class="acount">180+ Rooms</div><div class="auni">UCL · King's · LSE · Imperial</div></div>
    <div class="aitem rev d1"><div class="aname">Manchester</div><div class="acount">95+ Rooms</div><div class="auni">UoM · MMU · Salford</div></div>
    <div class="aitem rev d2"><div class="aname">Birmingham</div><div class="acount">72+ Rooms</div><div class="auni">Aston · UoB · BCU</div></div>
    <div class="aitem rev d3"><div class="aname">Leeds</div><div class="acount">58+ Rooms</div><div class="auni">UoL · Leeds Beckett</div></div>
    <div class="aitem rev"><div class="aname">Sheffield</div><div class="acount">44+ Rooms</div><div class="auni">UoS · Sheffield Hallam</div></div>
  </div>
</section>

<!-- CTA -->
<div class="cta-sec">
  <div class="cta-inner rev">
    <h2 class="cta-title">Ready to Find Your Perfect Student Home?</h2>
    <p class="cta-sub">Browse 500+ properties across the UK. Bills included. Flexible tenancies. Zero-stress moves.</p>
    <div class="cta-btns">
      <a href="#contact" class="btn-dark">Book a Free Viewing</a>
      <a href="tel:+447424794571" class="btn-od">Call Us Now</a>
    </div>
  </div>
</div>

<!-- CONTACT -->
<div class="contact-wrap" id="contact">
  <div class="cinfo">
    <div class="sec-eye" style="margin-bottom:18px"><div class="l"></div><span>Get In Touch</span></div>
    <h2 class="sec-title" style="margin-bottom:40px">We're Here <em>For You</em></h2>
    <div class="cdet"><div class="cdet-icon">📍</div><div><div class="cdet-label">Icon Offices</div><div class="cdet-val">182–184 High Street<br>North Eastham, London<br>E62JA, United Kingdom</div></div></div>
    <div class="cdet"><div class="cdet-icon">✉</div><div><div class="cdet-label">Email</div><div class="cdet-val">snlettingsproperties@gmail.com<br>info@snproperties.co.uk</div></div></div>
    <div class="cdet"><div class="cdet-icon">📞</div><div><div class="cdet-label">Phone</div><div class="cdet-val">+44 7424 794571</div></div></div>
    <div style="margin-top:44px;padding-top:44px;border-top:.5px solid rgba(201,168,76,.2)">
      <p style="font-size:8px;letter-spacing:4px;text-transform:uppercase;color:var(--gold);font-weight:700;margin-bottom:18px">Office Hours</p>
      <p style="font-size:12px;color:var(--dim);line-height:2.1">Monday – Friday: 9:00am – 6:00pm<br>Saturday: 10:00am – 4:00pm<br>Sunday: By Appointment</p>
    </div>
  </div>
  <div class="cform">
    <span class="form-tag">Book a Viewing</span>
    <div class="frow">
      <div class="fg"><label>First Name</label><input type="text" placeholder="First name"></div>
      <div class="fg"><label>Last Name</label><input type="text" placeholder="Last name"></div>
    </div>
    <div class="fg"><label>Email Address</label><input type="email" placeholder="your@email.com"></div>
    <div class="fg"><label>Phone</label><input type="tel" placeholder="+44 ..."></div>
    <div class="frow">
      <div class="fg"><label>City Preference</label><select><option value="">Select City</option><option>London</option><option>Manchester</option><option>Birmingham</option><option>Leeds</option><option>Sheffield</option></select></div>
      <div class="fg"><label>Room Type</label><select><option value="">Select Type</option><option>En-Suite Room</option><option>Studio Flat</option><option>Shared House</option></select></div>
    </div>
    <div class="fg"><label>Message</label><textarea placeholder="Requirements, budget, move-in date..."></textarea></div>
    <button class="fsub" id="fsub">Send Enquiry →</button>
  </div>
</div>

<!-- FOOTER -->
<footer>
  <div class="ftop">
    <div>
      <div style="display:flex;align-items:center;gap:14px">
        <div class="logomark">SN</div>
        <div class="logotext"><b>SN</b> Properties</div>
      </div>
      <p class="ftagline">"Building Connections. Creating Opportunities. Shaping Futures."</p>
      <p style="font-size:11px;color:rgba(250,250,247,.28);line-height:1.7">Premium student lettings & property management<br>across the United Kingdom.</p>
    </div>
    <div class="fcol"><h4>Properties</h4><a href="#">En-Suite Rooms</a><a href="#">Studio Flats</a><a href="#">Shared Houses</a><a href="#">Premium Listings</a><a href="#">New Additions</a></div>
    <div class="fcol"><h4>Services</h4><a href="#">Student Lettings</a><a href="#">Property Management</a><a href="#">Investment Consultancy</a><a href="#">Commercial & Residential</a></div>
    <div class="fcol"><h4>Cities</h4><a href="#">London</a><a href="#">Manchester</a><a href="#">Birmingham</a><a href="#">Leeds</a><a href="#">Sheffield</a></div>
  </div>
  <div class="fbot">
    <p>© 2025 SN Properties UK Ltd. All rights reserved. | 182–184 High Street, North Eastham, London E62JA</p>
    <div class="fmark">SN Properties · United Kingdom</div>
  </div>
</footer>

<script>
// Cursor
const cur=document.getElementById('cur'),ring=document.getElementById('ring');
let mx=0,my=0,rx=0,ry=0;
document.addEventListener('mousemove',e=>{
  mx=e.clientX;my=e.clientY;
  cur.style.transform=`translate(${mx-4}px,${my-4}px)`;
});
(function anim(){rx+=(mx-rx)*.1;ry+=(my-ry)*.1;ring.style.transform=`translate(${rx-16}px,${ry-16}px)`;requestAnimationFrame(anim)})();
document.querySelectorAll('a,button,.stag,.aitem,.svc,.pcard').forEach(el=>{
  el.addEventListener('mouseenter',()=>{ring.style.width=ring.style.height='52px';ring.style.opacity='0.9'});
  el.addEventListener('mouseleave',()=>{ring.style.width=ring.style.height='32px';ring.style.opacity='0.5'});
});

// Nav scroll
const nav=document.getElementById('nav');
window.addEventListener('scroll',()=>nav.classList.toggle('on',scrollY>50));

// Reveal
const revs=document.querySelectorAll('.rev');
new IntersectionObserver(e=>e.forEach(x=>x.isIntersecting&&x.target.classList.add('in')),{threshold:.12}).observe||(()=>{});
const io=new IntersectionObserver(e=>e.forEach(x=>{if(x.isIntersecting)x.target.classList.add('in')}),{threshold:.12});
revs.forEach(el=>io.observe(el));

// Tags
document.querySelectorAll('.stag').forEach(t=>t.addEventListener('click',()=>t.classList.toggle('active')));

// Search
document.getElementById('sbtn').addEventListener('click',function(){
  this.textContent='Searching...';
  setTimeout(()=>{this.textContent='Search';document.getElementById('props').scrollIntoView({behavior:'smooth'})},800);
});

// Form
document.getElementById('fsub').addEventListener('click',function(){
  this.textContent='Enquiry Sent ✓';this.style.background='#3a7a4a';
  setTimeout(()=>{this.textContent='Send Enquiry →';this.style.background=''},3000);
});
</script>
</body>
</html>
