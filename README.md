<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>PEPITO — Officiel</title>
  <meta name="description" content="Pepito — Artiste RAP, Trap, Shatta & Afro. Un univers authentique, brut, visionnaire." />

  <meta http-equiv="Content-Security-Policy" content="default-src 'self'; script-src 'self' 'unsafe-inline' https://cdnjs.cloudflare.com; style-src 'self' 'unsafe-inline' https://fonts.googleapis.com; font-src https://fonts.gstatic.com; img-src 'self' data: https://img.youtube.com https://*.ytimg.com; frame-src https://www.youtube.com https://www.youtube-nocookie.com; connect-src 'self'; object-src 'none'; base-uri 'self'; form-action 'none';" />
  <meta http-equiv="X-Content-Type-Options" content="nosniff" />
  <meta http-equiv="Referrer-Policy" content="strict-origin-when-cross-origin" />
  <meta http-equiv="Permissions-Policy" content="camera=(), microphone=(), geolocation=()" />
  <meta name="robots" content="index, follow" />

  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Space+Grotesk:wght@300;400;500;600;700&family=DM+Serif+Display:ital@0;1&display=swap" rel="stylesheet" />

  <style>
    /* ─── RESET & VARS ─── */
    *, *::before, *::after { margin:0; padding:0; box-sizing:border-box; }

    :root {
      --bg:     #030303;
      --bg2:    #0b0b0b;
      --accent: #c6ff3e;
      --red:    #ff2020;
      --gold:   #f0c43a;
      --white:  #f0f0f0;
      --muted:  #4a4a4a;
      --border: rgba(255,255,255,.07);
      --ff-d: 'Bebas Neue', sans-serif;
      --ff-b: 'Space Grotesk', sans-serif;
      --ff-s: 'DM Serif Display', serif;
    }

    html {
      scroll-behavior: smooth;
      scrollbar-gutter: stable;          /* prevents layout shift */
      scrollbar-width: thin;             /* Firefox */
      scrollbar-color: var(--accent) var(--bg2);
    }
    ::-webkit-scrollbar       { width: 3px; }
    ::-webkit-scrollbar-track { background: var(--bg2); }
    ::-webkit-scrollbar-thumb { background: var(--accent); border-radius: 2px; }

    body {
      background: var(--bg);
      color: var(--white);
      font-family: var(--ff-b);
      overflow-x: hidden;
    }

    /* ─── GRAIN ─── */
    #grain {
      position:fixed; top:-50%; left:-50%; width:200%; height:200%;
      opacity:.03; pointer-events:none; z-index:9000;
      background-image:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='300' height='300'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='.85' numOctaves='4' stitchTiles='stitch'/%3E%3CfeColorMatrix type='saturate' values='0'/%3E%3C/filter%3E%3Crect width='300' height='300' filter='url(%23n)'/%3E%3C/svg%3E");
      animation: grain 8s steps(10) infinite;
    }
    @keyframes grain {
      0%  {transform:translate(0,0)}    10% {transform:translate(-5%,-10%)}
      20% {transform:translate(-15%,5%)} 30% {transform:translate(7%,-15%)}
      40% {transform:translate(-5%,15%)} 50% {transform:translate(-10%,5%)}
      60% {transform:translate(15%,0)}   70% {transform:translate(0,10%)}
      80% {transform:translate(-15%,0)}  90% {transform:translate(10%,5%)}
      100%{transform:translate(5%,0)}
    }

    /* ─── SCROLL PROGRESS ─── */
    #prog {
      position:fixed; top:0; left:0; right:0; height:2px;
      background:var(--accent); transform-origin:left;
      transform:scaleX(0); z-index:9001; pointer-events:none;
    }

    /* ─── LOADER ─── */
    #loader {
      position:fixed; inset:0; z-index:9999;
      background:var(--bg);
      display:flex; align-items:center; justify-content:center;
      flex-direction:column; gap:1.5rem;
      transition:opacity .8s ease, visibility .8s ease;
    }
    #loader.gone { opacity:0; visibility:hidden; }
    .ld-letters { display:flex; gap:0; overflow:hidden; }
    .ld-l {
      font-family:var(--ff-d);
      font-size:clamp(2.5rem,8vw,5rem);
      letter-spacing:10px;
      display:inline-block;
      animation:ldrise .6s cubic-bezier(.76,0,.24,1) both;
    }
    .ld-l:nth-child(1){animation-delay:.05s}
    .ld-l:nth-child(2){animation-delay:.1s}
    .ld-l:nth-child(3){animation-delay:.15s}
    .ld-l:nth-child(4){animation-delay:.2s;color:var(--accent)}
    .ld-l:nth-child(5){animation-delay:.25s}
    .ld-l:nth-child(6){animation-delay:.3s}
    @keyframes ldrise { from{transform:translateY(110%);opacity:0} to{transform:none;opacity:1} }
    .ld-bar-wrap { width:160px; height:1px; background:var(--muted); overflow:hidden; }
    .ld-bar { height:100%; width:0; background:var(--accent); animation:ldbar 1.4s .4s ease-out forwards; }
    @keyframes ldbar { to{width:100%} }

    /* ─── CURSOR ─── */
    #cur  { position:fixed; width:6px; height:6px; background:var(--accent); border-radius:50%; pointer-events:none; z-index:8999; transform:translate(-50%,-50%); }
    #curR { position:fixed; width:28px; height:28px; border:1px solid rgba(198,255,62,.3); border-radius:50%; pointer-events:none; z-index:8998; transform:translate(-50%,-50%); transition:width .3s,height .3s,border-color .3s,background .3s; }
    #curR.big { width:56px; height:56px; border-color:rgba(198,255,62,.6); background:rgba(198,255,62,.04); }
    @media(hover:none){ #cur,#curR{display:none} }

    /* ─── NAV ─── */
    nav {
      position:fixed; top:0; left:0; right:0; z-index:500;
      padding:1.4rem 3rem;
      display:flex; justify-content:space-between; align-items:center;
      transition:background .4s, border-color .4s, padding .4s;
    }
    nav.solid {
      background:rgba(3,3,3,.9); backdrop-filter:blur(16px);
      border-bottom:1px solid var(--border); padding:1rem 3rem;
    }
    .nav-logo { font-family:var(--ff-d); font-size:1.4rem; letter-spacing:6px; color:var(--white); text-decoration:none; }
    .nav-links { list-style:none; display:flex; gap:2.5rem; }
    .nav-links a {
      color:var(--muted); text-decoration:none;
      font-size:.68rem; letter-spacing:2.5px; text-transform:uppercase; font-weight:500;
      transition:color .3s; position:relative;
    }
    .nav-links a::after {
      content:''; position:absolute; bottom:-3px; left:0; right:0; height:1px;
      background:var(--accent); transform:scaleX(0); transform-origin:left;
      transition:transform .35s cubic-bezier(.76,0,.24,1);
    }
    .nav-links a:hover { color:var(--white); }
    .nav-links a:hover::after { transform:scaleX(1); }
    .nav-burger { display:none; flex-direction:column; gap:5px; background:none; border:none; cursor:pointer; padding:0; }
    .nav-burger span { display:block; width:22px; height:1px; background:var(--white); transition:all .35s; }
    .nav-burger.x span:nth-child(1){ transform:rotate(45deg) translate(4px,4px); }
    .nav-burger.x span:nth-child(2){ transform:rotate(-45deg) translate(4px,-4px); }

    /* ─── MOBILE MENU ─── */
    #mmenu {
      position:fixed; inset:0; z-index:499;
      background:rgba(3,3,3,.98);
      display:flex; flex-direction:column; align-items:center; justify-content:center; gap:2.5rem;
      clip-path:inset(0 0 100% 0);
      transition:clip-path .6s cubic-bezier(.76,0,.24,1);
    }
    #mmenu.open { clip-path:inset(0 0 0% 0); }
    #mmenu a {
      font-family:var(--ff-d); font-size:clamp(3rem,9vw,5rem);
      letter-spacing:4px; color:var(--white); text-decoration:none; text-transform:uppercase;
      transition:color .3s, letter-spacing .3s;
    }
    #mmenu a:hover { color:var(--accent); letter-spacing:8px; }

    /* ─── HERO ─── */
    #hero {
      position:relative; width:100%; height:100vh; min-height:600px;
      display:flex; align-items:center; justify-content:center; overflow:hidden;
    }
    .h-orb {
      position:absolute; border-radius:50%; filter:blur(140px); opacity:.12; pointer-events:none;
    }
    .h-o1 { width:700px;height:700px;background:radial-gradient(circle,#c6ff3e,transparent 70%);top:-250px;right:-150px; animation:o1 14s ease-in-out infinite; }
    .h-o2 { width:500px;height:500px;background:radial-gradient(circle,#ff2020,transparent 70%);bottom:-150px;left:0; animation:o2 18s ease-in-out infinite; }
    .h-o3 { width:350px;height:350px;background:radial-gradient(circle,#f0c43a,transparent 70%);top:40%;left:30%; animation:o3 11s ease-in-out infinite; }
    @keyframes o1 { 0%,100%{transform:translate(0,0) scale(1)} 50%{transform:translate(-50px,40px) scale(1.1)} }
    @keyframes o2 { 0%,100%{transform:translate(0,0) scale(1)} 50%{transform:translate(60px,-50px) scale(1.15)} }
    @keyframes o3 { 0%,100%{transform:translate(0,0) scale(1)} 50%{transform:translate(-30px,-40px) scale(1.2)} }

    .h-grid {
      position:absolute; inset:0; opacity:.03;
      background-image:
        repeating-linear-gradient(90deg,transparent,transparent calc(100vw/12 - 1px),rgba(255,255,255,.5) calc(100vw/12 - 1px),rgba(255,255,255,.5) calc(100vw/12)),
        repeating-linear-gradient(0deg,transparent,transparent calc(100vh/8 - 1px),rgba(255,255,255,.2) calc(100vh/8 - 1px),rgba(255,255,255,.2) calc(100vh/8));
    }

    .h-content { position:relative; z-index:2; text-align:center; padding:0 2rem; }

    .h-eyebrow {
      font-size:.65rem; letter-spacing:6px; text-transform:uppercase;
      color:var(--accent); font-weight:500; margin-bottom:1.5rem;
      opacity:0; transform:translateY(14px);
      animation:fu .9s .2s cubic-bezier(.76,0,.24,1) forwards;
    }

    .h-title {
      font-family:var(--ff-d);
      font-size:clamp(6rem,19vw,22rem);
      line-height:.8; letter-spacing:-2px;
      overflow:visible;
    }
    .h-word { display:inline-block; overflow:hidden; }
    .h-letter {
      display:inline-block;
      transform:translateY(110%);
      animation:slideup 1s cubic-bezier(.76,0,.24,1) forwards;
    }
    .h-letter:nth-child(1){animation-delay:.3s}
    .h-letter:nth-child(2){animation-delay:.36s}
    .h-letter:nth-child(3){animation-delay:.42s}
    .h-letter:nth-child(4){animation-delay:.48s;color:var(--accent)}
    .h-letter:nth-child(5){animation-delay:.54s}
    .h-letter:nth-child(6){animation-delay:.6s}
    @keyframes slideup { to{transform:translateY(0)} }

    .h-tag {
      font-family:var(--ff-s); font-style:italic;
      font-size:clamp(1rem,2.2vw,1.5rem); color:rgba(240,240,240,.5);
      margin-top:1.8rem; letter-spacing:.5px;
      opacity:0; transform:translateY(14px);
      animation:fu .9s .9s cubic-bezier(.76,0,.24,1) forwards;
    }
    .h-genres {
      display:flex; justify-content:center; gap:.75rem; flex-wrap:wrap; margin-top:2.2rem;
      opacity:0; transform:translateY(14px);
      animation:fu .9s 1.1s cubic-bezier(.76,0,.24,1) forwards;
    }
    .h-genre {
      font-size:.6rem; letter-spacing:3px; text-transform:uppercase;
      color:var(--muted); padding:.35rem .9rem; border:1px solid var(--border); font-weight:500;
      transition:color .3s, border-color .3s;
    }
    .h-genre:hover { color:var(--accent); border-color:rgba(198,255,62,.3); }
    .h-scroll {
      position:absolute; bottom:2.5rem; left:50%; transform:translateX(-50%);
      display:flex; flex-direction:column; align-items:center; gap:.5rem;
      opacity:0; animation:fu .9s 1.5s forwards;
    }
    .h-sline { width:1px; height:40px; background:var(--muted); animation:sline 2.2s ease-in-out infinite; }
    .h-scroll span { font-size:.56rem; letter-spacing:3px; text-transform:uppercase; color:var(--muted); }
    @keyframes fu    { to{opacity:1;transform:translateY(0)} }
    @keyframes sline {
      0%  {transform:scaleY(0);transform-origin:top}
      49% {transform:scaleY(1);transform-origin:top}
      50% {transform:scaleY(1);transform-origin:bottom}
      100%{transform:scaleY(0);transform-origin:bottom}
    }

    /* ─── MARQUEE (fixed loop) ─── */
    .mq-wrap {
      overflow:hidden; border-top:1px solid var(--border); border-bottom:1px solid var(--border);
      padding:.85rem 0; background:var(--bg2); user-select:none;
    }
    .mq-track {
      display:flex; gap:0; white-space:nowrap;
      animation:mq 22s linear infinite;
      width:max-content;
    }
    .mq-track:hover { animation-play-state:paused; }
    .mq-group { display:flex; gap:2.5rem; padding-right:2.5rem; }
    .mq-group span { font-family:var(--ff-d); font-size:1rem; letter-spacing:4px; color:var(--muted); }
    .mq-group span.a { color:var(--accent); }
    @keyframes mq { from{transform:translateX(0)} to{transform:translateX(-50%)} }

    /* ─── ABOUT ─── */
    #about { padding:10rem 0; position:relative; }
    .about-wrap {
      max-width:1360px; margin:0 auto; padding:0 3rem;
      display:grid; grid-template-columns:1.15fr 0.85fr; gap:7rem; align-items:center;
    }
    .sec-label {
      font-size:.62rem; letter-spacing:4px; text-transform:uppercase;
      color:var(--accent); font-weight:500; margin-bottom:1.8rem;
      display:flex; align-items:center; gap:1rem;
    }
    .sec-label::before { content:''; width:26px; height:1px; background:var(--accent); }
    .about-title {
      font-family:var(--ff-d);
      font-size:clamp(3rem,5vw,5.5rem); line-height:.92; margin-bottom:3rem;
    }
    .about-title em {
      font-family:var(--ff-s); font-size:.55em; color:var(--muted);
      font-style:italic; display:block; margin-top:.6rem; letter-spacing:1px;
    }
    .about-body p { font-size:.97rem; line-height:1.9; color:rgba(240,240,240,.65); font-weight:300; margin-bottom:1.3rem; }
    .about-body p.lead { font-size:1.12rem; color:var(--white); font-weight:400; }
    .about-quote {
      margin-top:2.8rem; padding-left:1.8rem; border-left:2px solid var(--accent);
    }
    .about-quote p { font-family:var(--ff-s); font-style:italic; font-size:1.2rem; color:var(--white); line-height:1.65; }

    /* About card */
    .about-card { position:relative; }
    .about-card-deco { position:absolute; top:-20px; right:-20px; width:90px; height:90px; border:1px solid var(--accent); z-index:0; }
    .about-card-deco2 { position:absolute; bottom:-18px; left:-18px; width:60px; height:60px; background:var(--red); opacity:.22; z-index:0; }
    .about-card-frame {
      background:var(--bg2); border:1px solid var(--border);
      aspect-ratio:3/4; position:relative; overflow:hidden;
      display:flex; align-items:center; justify-content:center;
    }
    .about-bg-letter {
      position:absolute; inset:0; font-family:var(--ff-d);
      font-size:clamp(16rem,45vw,32rem); color:rgba(255,255,255,.016);
      display:flex; align-items:center; justify-content:center;
      user-select:none; pointer-events:none;
    }
    .about-stats { position:relative; z-index:2; display:flex; flex-direction:column; align-items:center; gap:3rem; }
    .stat { text-align:center; }
    .stat-n { font-family:var(--ff-d); line-height:1; letter-spacing:2px; }
    .stat-l { font-size:.58rem; letter-spacing:3px; text-transform:uppercase; color:var(--muted); margin-top:.3rem; }
    .c1{color:var(--accent)} .c2{color:var(--red)} .c3{color:var(--gold)}

    /* ─── VIDEOS ─── */
    #videos { padding-top:6rem; }
    .vid-header {
      max-width:1360px; margin:0 auto 5rem; padding:0 3rem;
      display:flex; justify-content:space-between; align-items:flex-end;
    }
    .sec-title { font-family:var(--ff-d); font-size:clamp(3rem,5.5vw,6rem); line-height:.92; }
    .vid-count { font-family:var(--ff-d); font-size:8rem; color:rgba(255,255,255,.04); line-height:1; user-select:none; }

    /* Video chapter */
    .vid-ch {
      min-height:90vh; display:flex; align-items:center;
      position:relative; overflow:hidden;
      border-top:1px solid var(--border);
      padding:5rem 0;
    }
    .vid-ch-inner {
      max-width:1360px; margin:0 auto; padding:0 3rem;
      display:grid; grid-template-columns:1.1fr 0.9fr; gap:5rem; align-items:center;
      width:100%;
    }
    .vid-ch.flip .vid-ch-inner { direction:rtl; }
    .vid-ch.flip .vid-ch-inner > * { direction:ltr; }

    /* per-chapter atmospheric tint */
    .vid-ch-1 { background:radial-gradient(ellipse 80% 80% at 20% 50%,rgba(198,255,62,.025) 0%,transparent 70%); }
    .vid-ch-2 { background:radial-gradient(ellipse 80% 80% at 80% 50%,rgba(255,32,32,.025) 0%,transparent 70%); }
    .vid-ch-3 { background:radial-gradient(ellipse 80% 80% at 20% 50%,rgba(240,196,58,.025) 0%,transparent 70%); }

    /* Big chapter number watermark */
    .vid-ch-num {
      position:absolute; top:50%; right:3rem; transform:translateY(-50%);
      font-family:var(--ff-d); font-size:clamp(10rem,18vw,20rem);
      line-height:1; user-select:none; pointer-events:none; letter-spacing:-5px;
      color:rgba(255,255,255,.025); z-index:0;
    }
    .vid-ch.flip .vid-ch-num { right:auto; left:3rem; }

    /* Embed */
    .vid-embed {
      position:relative; aspect-ratio:16/9; overflow:hidden;
      background:#060606; cursor:pointer; z-index:1;
      box-shadow:0 40px 100px rgba(0,0,0,.7);
      transition:box-shadow .4s;
    }
    .vid-embed:hover { box-shadow:0 60px 120px rgba(0,0,0,.9); }
    .vid-embed iframe { position:absolute; inset:0; width:100%; height:100%; border:none; z-index:5; }
    .vid-embed::after { content:''; position:absolute; inset:0; border:1px solid var(--border); pointer-events:none; z-index:6; }
    .vid-thumb { position:absolute; inset:0; width:100%; height:100%; object-fit:cover; display:block; filter:brightness(.75); transition:transform .7s cubic-bezier(.16,1,.3,1),filter .4s; }
    .vid-embed:hover .vid-thumb { transform:scale(1.06); filter:brightness(.55); }
    .vid-play { position:absolute; inset:0; z-index:3; display:flex; align-items:center; justify-content:center; background:rgba(0,0,0,.2); transition:background .3s; }
    .vid-embed:hover .vid-play { background:transparent; }
    .vid-pbtn {
      width:72px; height:72px; border-radius:50%;
      background:rgba(255,255,255,.08); border:1.5px solid rgba(255,255,255,.3);
      backdrop-filter:blur(8px);
      display:flex; align-items:center; justify-content:center;
      transition:transform .4s cubic-bezier(.16,1,.3,1), background .3s, border-color .3s;
    }
    .vid-ch-1 .vid-embed:hover .vid-pbtn { background:rgba(198,255,62,.18); border-color:var(--accent); transform:scale(1.15); }
    .vid-ch-2 .vid-embed:hover .vid-pbtn { background:rgba(255,32,32,.18); border-color:var(--red); transform:scale(1.15); }
    .vid-ch-3 .vid-embed:hover .vid-pbtn { background:rgba(240,196,58,.18); border-color:var(--gold); transform:scale(1.15); }
    .vid-pbtn svg { width:20px; height:20px; fill:var(--white); margin-left:4px; }
    .vid-embed.active .vid-thumb,.vid-embed.active .vid-play { display:none; }
    .vid-embed.active { cursor:default; }

    /* Video info */
    .vid-info { position:relative; z-index:1; padding:.5rem 0; }
    .vid-n { font-family:var(--ff-d); font-size:clamp(6rem,10vw,9rem); line-height:.85; color:rgba(255,255,255,.04); letter-spacing:-4px; margin-bottom:-1.5rem; user-select:none; }
    .vid-tag { font-size:.6rem; letter-spacing:3px; text-transform:uppercase; font-weight:500; position:relative; z-index:1; }
    .v-acc { color:var(--accent) }
    .v-red { color:var(--red) }
    .v-gld { color:var(--gold) }
    .vid-title { font-family:var(--ff-d); font-size:clamp(2rem,3.5vw,3.2rem); line-height:.93; margin:.9rem 0; position:relative; z-index:1; }
    .vid-line { width:36px; height:2px; margin:1.3rem 0; position:relative; z-index:1; }
    .vid-line.a { background:var(--accent) } .vid-line.r { background:var(--red) } .vid-line.g { background:var(--gold) }
    .vid-desc { font-size:.9rem; line-height:1.85; color:var(--muted); font-weight:300; position:relative; z-index:1; }
    .vid-yt-link {
      display:inline-flex; align-items:center; gap:.5rem;
      margin-top:1.5rem; font-size:.65rem; letter-spacing:2px; text-transform:uppercase;
      color:var(--muted); text-decoration:none; font-weight:500;
      transition:color .3s; position:relative; z-index:1;
    }
    .vid-yt-link:hover { color:var(--white); }
    .vid-yt-link svg { width:14px; height:14px; fill:currentColor; }

    /* ─── CTA ─── */
    #contact {
      padding:10rem 3rem; text-align:center; position:relative; overflow:hidden;
    }
    .cta-ghost {
      position:absolute; top:50%; left:50%; transform:translate(-50%,-50%);
      font-family:var(--ff-d); font-size:clamp(10rem,26vw,26rem);
      color:rgba(255,255,255,.018); white-space:nowrap;
      pointer-events:none; user-select:none; letter-spacing:-8px;
    }
    .cta-label {
      font-size:.62rem; letter-spacing:4px; text-transform:uppercase;
      color:var(--accent); font-weight:500; margin-bottom:2rem;
      display:flex; align-items:center; justify-content:center; gap:1rem;
    }
    .cta-label::before,.cta-label::after { content:''; width:26px; height:1px; background:var(--accent); }
    .cta-title { font-family:var(--ff-d); font-size:clamp(3rem,9vw,9rem); line-height:.9; margin-bottom:1.5rem; position:relative; z-index:1; }
    .cta-sub { font-size:.95rem; color:var(--muted); max-width:460px; margin:0 auto 4rem; font-weight:300; line-height:1.75; position:relative; z-index:1; }

    .socials { display:flex; justify-content:center; gap:1rem; flex-wrap:wrap; position:relative; z-index:1; }
    .soc {
      display:inline-flex; align-items:center; gap:.7rem;
      padding:.85rem 1.6rem; border:1px solid var(--border);
      color:var(--white); text-decoration:none;
      font-size:.68rem; letter-spacing:2px; text-transform:uppercase; font-weight:500;
      position:relative; overflow:hidden; transition:color .3s, border-color .3s;
    }
    .soc::before {
      content:''; position:absolute; inset:0; background:var(--accent);
      transform:translateX(-101%);
      transition:transform .4s cubic-bezier(.76,0,.24,1); z-index:0;
    }
    .soc:hover { color:var(--bg); border-color:var(--accent); }
    .soc:hover::before { transform:translateX(0); }
    .soc svg,.soc span { position:relative; z-index:1; }
    .soc svg { width:15px; height:15px; fill:currentColor; }

    .cta-mail { margin-top:3rem; font-size:.68rem; color:var(--muted); letter-spacing:1.5px; position:relative; z-index:1; }
    .cta-mail a { color:var(--white); text-decoration:none; transition:color .3s; }
    .cta-mail a:hover { color:var(--accent); }

    /* ─── FOOTER ─── */
    footer { padding:2rem 3rem; border-top:1px solid var(--border); display:flex; justify-content:space-between; align-items:center; }
    .ft-logo { font-family:var(--ff-d); font-size:1.1rem; letter-spacing:6px; }
    .ft-copy  { font-size:.6rem; color:var(--muted); letter-spacing:1px; }
    .ft-top {
      font-size:.6rem; letter-spacing:2px; text-transform:uppercase;
      color:var(--muted); text-decoration:none;
      display:flex; align-items:center; gap:.5rem; transition:color .3s;
    }
    .ft-top:hover { color:var(--accent); }

    /* ─── LOCAL BANNER ─── */
    #local-banner {
      display:none; position:fixed; bottom:1.2rem; left:50%; transform:translateX(-50%);
      z-index:8000; background:rgba(198,255,62,.08); border:1px solid rgba(198,255,62,.25);
      backdrop-filter:blur(12px); padding:.6rem 1.3rem;
      font-family:var(--ff-b); font-size:.65rem; letter-spacing:1.5px;
      color:var(--accent); text-align:center; white-space:nowrap;
    }
    #local-banner button { background:none; border:none; color:var(--accent); cursor:pointer; margin-left:.8rem; }

    /* ─── GSAP REVEAL BASE ─── */
    .rv { opacity:0; }

    /* ─── RESPONSIVE ─── */
    @media(max-width:1024px){
      .about-wrap { grid-template-columns:1fr; gap:4rem; }
      .about-card  { max-width:360px; }
      .vid-ch-inner { grid-template-columns:1fr; gap:2.5rem; }
      .vid-ch.flip .vid-ch-inner { direction:ltr; }
      .vid-ch-num { display:none; }
    }
    @media(max-width:768px){
      nav { padding:1.1rem 1.4rem; }
      nav.solid { padding:.9rem 1.4rem; }
      .nav-links  { display:none; }
      .nav-burger { display:flex; }
      .about-wrap,.vid-header { padding-left:1.4rem; padding-right:1.4rem; }
      .vid-ch-inner { padding-left:1.4rem; padding-right:1.4rem; }
      .vid-ch { min-height:unset; padding:4rem 0; }
      .vid-header { flex-direction:column; align-items:flex-start; gap:.5rem; }
      .vid-count  { font-size:4rem; }
      footer { flex-direction:column; gap:1rem; text-align:center; padding:1.8rem 1.4rem; }
      #contact { padding:6rem 1.4rem; }
    }
    @media(max-width:480px){
      .h-genres { gap:.5rem; }
      .socials  { flex-direction:column; align-items:center; }
      .soc      { width:100%; max-width:300px; justify-content:center; }
    }
  </style>
</head>
<body>

<div id="grain" aria-hidden="true"></div>
<div id="prog"  aria-hidden="true"></div>
<div id="cur"   aria-hidden="true"></div>
<div id="curR"  aria-hidden="true"></div>

<!-- LOADER -->
<div id="loader">
  <div class="ld-letters" aria-label="Chargement Pepito">
    <span class="ld-l">P</span><span class="ld-l">E</span><span class="ld-l">P</span>
    <span class="ld-l">I</span><span class="ld-l">T</span><span class="ld-l">O</span>
  </div>
  <div class="ld-bar-wrap"><div class="ld-bar"></div></div>
</div>

<!-- LOCAL BANNER -->
<div id="local-banner">
  ▶&nbsp; Clic = ouvre YouTube &nbsp;·&nbsp; Pour l'embed intégré : servir via HTTP
  <button onclick="this.parentElement.style.display='none'" aria-label="Fermer">✕</button>
</div>

<!-- MOBILE MENU -->
<div id="mmenu">
  <a href="#about"   onclick="mmClose()">Identité</a>
  <a href="#videos"  onclick="mmClose()">Clips</a>
  <a href="#contact" onclick="mmClose()">Contact</a>
</div>

<!-- NAV -->
<nav id="nav">
  <a href="#hero" class="nav-logo">PEPITO</a>
  <ul class="nav-links">
    <li><a href="#about">Identité</a></li>
    <li><a href="#videos">Clips</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
  <button class="nav-burger" id="burger" aria-label="Menu">
    <span></span><span></span>
  </button>
</nav>

<!-- ═══════════════════════════════ HERO -->
<section id="hero">
  <div class="h-orb h-o1" aria-hidden="true"></div>
  <div class="h-orb h-o2" aria-hidden="true"></div>
  <div class="h-orb h-o3" aria-hidden="true"></div>
  <div class="h-grid"     aria-hidden="true"></div>
  <div class="h-content">
    <div class="h-eyebrow">Artiste Officiel &nbsp;·&nbsp; RAP / TRAP / SHATTA / AFRO</div>
    <h1 class="h-title" aria-label="Pepito">
      <span class="h-word">
        <span class="h-letter">P</span><span class="h-letter">E</span>
        <span class="h-letter">P</span><span class="h-letter">I</span>
        <span class="h-letter">T</span><span class="h-letter">O</span>
      </span>
    </h1>
    <p class="h-tag">Né du béton.&nbsp; Sculpté par le feu.</p>
    <div class="h-genres">
      <span class="h-genre">Rap</span>
      <span class="h-genre">Trap</span>
      <span class="h-genre">Shatta</span>
      <span class="h-genre">Afro</span>
    </div>
  </div>
  <div class="h-scroll" aria-hidden="true">
    <div class="h-sline"></div>
    <span>Défiler</span>
  </div>
</section>

<!-- MARQUEE -->
<div class="mq-wrap" aria-hidden="true">
  <div class="mq-track">
    <div class="mq-group">
      <span>PEPITO</span><span class="a">✦</span>
      <span>RAP</span><span class="a">✦</span>
      <span>TRAP</span><span class="a">✦</span>
      <span>SHATTA</span><span class="a">✦</span>
      <span>AFRO</span><span class="a">✦</span>
      <span>AUTHENTICITÉ</span><span class="a">✦</span>
      <span>VISION</span><span class="a">✦</span>
      <span>STREET</span><span class="a">✦</span>
    </div>
    <div class="mq-group" aria-hidden="true">
      <span>PEPITO</span><span class="a">✦</span>
      <span>RAP</span><span class="a">✦</span>
      <span>TRAP</span><span class="a">✦</span>
      <span>SHATTA</span><span class="a">✦</span>
      <span>AFRO</span><span class="a">✦</span>
      <span>AUTHENTICITÉ</span><span class="a">✦</span>
      <span>VISION</span><span class="a">✦</span>
      <span>STREET</span><span class="a">✦</span>
    </div>
  </div>
</div>

<!-- ═══════════════════════════════ ABOUT -->
<section id="about">
  <div class="about-wrap">
    <div>
      <div class="sec-label rv">Identité</div>
      <h2 class="about-title rv">
        UNE VOIX<br>QUE LA RUE<br>A FAÇONNÉE
        <em>— et que rien n'a pu taire</em>
      </h2>
      <div class="about-body">
        <p class="lead rv">Pepito ne s'est pas inventé artiste. Il l'est devenu par nécessité — la musique comme seul langage assez grand pour tout ce qu'il avait à dire.</p>
        <p class="rv">Chaque titre est une page arrachée d'une vie réelle. Entre les cadences trap, la chaleur du shatta et la force brute du rap, il tisse un univers où l'authenticité n'est pas une posture — c'est une survie.</p>
        <p class="rv">18 ans. Aucun compromis. Juste la vérité, mise en son.</p>
        <div class="about-quote rv">
          <p>« Je rap pas pour être connu.<br>Je rap pour être compris. »</p>
        </div>
      </div>
    </div>

    <div class="about-card rv">
      <div class="about-card-deco"  aria-hidden="true"></div>
      <div class="about-card-deco2" aria-hidden="true"></div>
      <div class="about-card-frame">
        <div class="about-bg-letter" aria-hidden="true">P</div>
        <div class="about-stats">
          <div class="stat">
            <div class="stat-n c1" style="font-size:5rem" data-count="18">0</div>
            <div class="stat-l">Ans · Déjà une vision</div>
          </div>
          <div class="stat">
            <div class="stat-n c2" style="font-size:2.8rem">RAW</div>
            <div class="stat-l">Authenticité totale</div>
          </div>
          <div class="stat">
            <div class="stat-n c3" style="font-size:2.4rem">∞</div>
            <div class="stat-l">Zéro limite</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ═══════════════════════════════ VIDEOS -->
<section id="videos">
  <div class="vid-header">
    <div>
      <div class="sec-label rv">Les Clips</div>
      <h2 class="sec-title rv">CHAQUE<br>TRACK,<br>UNE HISTOIRE</h2>
    </div>
    <div class="vid-count rv" aria-hidden="true">03</div>
  </div>

  <!-- ── Clip 1 ── -->
  <div class="vid-ch vid-ch-1">
    <div class="vid-ch-num" aria-hidden="true">01</div>
    <div class="vid-ch-inner">
      <div class="vid-embed rv" data-vid="3wv1EaIwjLs" role="button" tabindex="0" aria-label="Lancer : Un Cri du Bitume">
        <img class="vid-thumb" src="https://img.youtube.com/vi/3wv1EaIwjLs/maxresdefault.jpg" alt="Pepito — Un Cri du Bitume" loading="lazy" onerror="this.src='https://img.youtube.com/vi/3wv1EaIwjLs/hqdefault.jpg'" />
        <div class="vid-play"><div class="vid-pbtn"><svg viewBox="0 0 16 16" aria-hidden="true"><path d="M3 2l11 6-11 6z"/></svg></div></div>
      </div>
      <div class="vid-info">
        <div class="vid-n" aria-hidden="true">01</div>
        <div class="vid-tag v-acc rv">Clip Officiel</div>
        <h3 class="vid-title rv">UN CRI DU BITUME</h3>
        <div class="vid-line a rv"></div>
        <p class="vid-desc rv">Une ode à la réalité. Le béton comme toile, la douleur comme instrument. Ce titre est une photographie sonore d'une jeunesse qui refuse de se taire — qui crie sa vérité là où d'autres choisissent le silence.</p>
        <a href="https://www.youtube.com/watch?v=3wv1EaIwjLs" class="vid-yt-link rv" target="_blank" rel="noopener noreferrer">
          <svg viewBox="0 0 24 24"><path d="M19.6 3.3a3 3 0 0 0-2.1-2.1C15.6 0.7 12 0.7 12 0.7s-3.6 0-5.5.5A3 3 0 0 0 4.4 3.3 31 31 0 0 0 4 9a31 31 0 0 0 .4 5.7 3 3 0 0 0 2.1 2.1c1.9.5 5.5.5 5.5.5s3.6 0 5.5-.5a3 3 0 0 0 2.1-2.1A31 31 0 0 0 20 9a31 31 0 0 0-.4-5.7zM9.7 11.5V6.5l4.6 2.5-4.6 2.5z"/></svg>
          <span>Voir sur YouTube</span>
        </a>
      </div>
    </div>
  </div>

  <!-- ── Clip 2 ── -->
  <div class="vid-ch vid-ch-2 flip">
    <div class="vid-ch-num" aria-hidden="true">02</div>
    <div class="vid-ch-inner">
      <div class="vid-embed rv" data-vid="S_PfD2bn4yk" role="button" tabindex="0" aria-label="Lancer : Cœur Abîmé">
        <img class="vid-thumb" src="https://img.youtube.com/vi/S_PfD2bn4yk/maxresdefault.jpg" alt="Pepito — Cœur Abîmé" loading="lazy" onerror="this.src='https://img.youtube.com/vi/S_PfD2bn4yk/hqdefault.jpg'" />
        <div class="vid-play"><div class="vid-pbtn"><svg viewBox="0 0 16 16" aria-hidden="true"><path d="M3 2l11 6-11 6z"/></svg></div></div>
      </div>
      <div class="vid-info">
        <div class="vid-n" aria-hidden="true">02</div>
        <div class="vid-tag v-red rv">Clip Officiel</div>
        <h3 class="vid-title rv">CŒUR ABÎMÉ</h3>
        <div class="vid-line r rv"></div>
        <p class="vid-desc rv">La vulnérabilité comme force. Quand l'intime devient universel — Pepito expose les blessures que l'on cache, celles qui font de nous ce que l'on est. Un titre qui touche là où ça fait mal, et qui guérit en même temps.</p>
        <a href="https://www.youtube.com/watch?v=S_PfD2bn4yk" class="vid-yt-link rv" target="_blank" rel="noopener noreferrer">
          <svg viewBox="0 0 24 24"><path d="M19.6 3.3a3 3 0 0 0-2.1-2.1C15.6 0.7 12 0.7 12 0.7s-3.6 0-5.5.5A3 3 0 0 0 4.4 3.3 31 31 0 0 0 4 9a31 31 0 0 0 .4 5.7 3 3 0 0 0 2.1 2.1c1.9.5 5.5.5 5.5.5s3.6 0 5.5-.5a3 3 0 0 0 2.1-2.1A31 31 0 0 0 20 9a31 31 0 0 0-.4-5.7zM9.7 11.5V6.5l4.6 2.5-4.6 2.5z"/></svg>
          <span>Voir sur YouTube</span>
        </a>
      </div>
    </div>
  </div>

  <!-- ── Clip 3 ── -->
  <div class="vid-ch vid-ch-3">
    <div class="vid-ch-num" aria-hidden="true">03</div>
    <div class="vid-ch-inner">
      <div class="vid-embed rv" data-vid="v0ZC_ZJ_sIw" role="button" tabindex="0" aria-label="Lancer : Fiesta">
        <img class="vid-thumb" src="https://img.youtube.com/vi/v0ZC_ZJ_sIw/maxresdefault.jpg" alt="Pepito — Fiesta" loading="lazy" onerror="this.src='https://img.youtube.com/vi/v0ZC_ZJ_sIw/hqdefault.jpg'" />
        <div class="vid-play"><div class="vid-pbtn"><svg viewBox="0 0 16 16" aria-hidden="true"><path d="M3 2l11 6-11 6z"/></svg></div></div>
      </div>
      <div class="vid-info">
        <div class="vid-n" aria-hidden="true">03</div>
        <div class="vid-tag v-gld rv">Clip Officiel</div>
        <h3 class="vid-title rv">FIESTA</h3>
        <div class="vid-line g rv"></div>
        <p class="vid-desc rv">L'énergie à l'état pur. Les vibrations afro rencontrent la rage trap — et le résultat est une déflagration. Fiesta, c'est la célébration de ceux qui dansent sur leurs douleurs et font du bruit pour exister.</p>
        <a href="https://www.youtube.com/watch?v=v0ZC_ZJ_sIw" class="vid-yt-link rv" target="_blank" rel="noopener noreferrer">
          <svg viewBox="0 0 24 24"><path d="M19.6 3.3a3 3 0 0 0-2.1-2.1C15.6 0.7 12 0.7 12 0.7s-3.6 0-5.5.5A3 3 0 0 0 4.4 3.3 31 31 0 0 0 4 9a31 31 0 0 0 .4 5.7 3 3 0 0 0 2.1 2.1c1.9.5 5.5.5 5.5.5s3.6 0 5.5-.5a3 3 0 0 0 2.1-2.1A31 31 0 0 0 20 9a31 31 0 0 0-.4-5.7zM9.7 11.5V6.5l4.6 2.5-4.6 2.5z"/></svg>
          <span>Voir sur YouTube</span>
        </a>
      </div>
    </div>
  </div>
</section>

<!-- ═══════════════════════════════ CTA -->
<section id="contact">
  <div class="cta-ghost" aria-hidden="true">PEPITO</div>
  <div style="position:relative;z-index:2">
    <div class="cta-label rv">Rejoins l'univers</div>
    <h2 class="cta-title rv">SUIS<br>L'AVENTURE</h2>
    <p class="cta-sub rv">Écoute, partage, commente. Rejoins une communauté qui croit en la musique authentique.</p>

    <div class="socials rv">
      <a href="https://www.youtube.com/@pepito" class="soc mag" target="_blank" rel="noopener noreferrer">
        <svg viewBox="0 0 24 24"><path d="M23.5 6.2a3 3 0 0 0-2.1-2.1C19.5 3.6 12 3.6 12 3.6s-7.5 0-9.4.5A3 3 0 0 0 .5 6.2 31 31 0 0 0 0 12a31 31 0 0 0 .5 5.8 3 3 0 0 0 2.1 2.1c1.9.5 9.4.5 9.4.5s7.5 0 9.4-.5a3 3 0 0 0 2.1-2.1A31 31 0 0 0 24 12a31 31 0 0 0-.5-5.8zM9.7 15.5V8.5l6.3 3.5-6.3 3.5z"/></svg>
        <span>YouTube</span>
      </a>
      <a href="https://www.instagram.com/pepito" class="soc mag" target="_blank" rel="noopener noreferrer">
        <svg viewBox="0 0 24 24"><path d="M12 2.2c3.2 0 3.6 0 4.8.1 3.3.1 4.8 1.7 4.9 4.9.1 1.3.1 1.6.1 4.8s0 3.6-.1 4.8c-.2 3.2-1.7 4.8-4.9 4.9-1.2.1-1.6.1-4.8.1s-3.6 0-4.8-.1c-3.3-.2-4.8-1.7-4.9-4.9C2.2 15.6 2.2 15.2 2.2 12s0-3.6.1-4.8C2.4 3.9 3.9 2.4 7.2 2.3 8.4 2.2 8.8 2.2 12 2.2zM12 0C8.7 0 8.3 0 7.1.1 2.7.3.3 2.7.1 7.1 0 8.3 0 8.7 0 12s0 3.7.1 4.9c.2 4.4 2.6 6.8 7 7C8.3 24 8.7 24 12 24s3.7 0 4.9-.1c4.4-.2 6.8-2.6 7-7C24 15.7 24 15.3 24 12s0-3.7-.1-4.9C23.7 2.7 21.3.3 16.9.1 15.7 0 15.3 0 12 0zm0 5.8a6.2 6.2 0 1 0 0 12.4A6.2 6.2 0 0 0 12 5.8zm0 10.2a4 4 0 1 1 0-8 4 4 0 0 1 0 8zm6.4-11.8a1.4 1.4 0 1 0 0 2.8 1.4 1.4 0 0 0 0-2.8z"/></svg>
        <span>Instagram</span>
      </a>
      <a href="https://open.spotify.com" class="soc mag" target="_blank" rel="noopener noreferrer">
        <svg viewBox="0 0 24 24"><path d="M12 0C5.4 0 0 5.4 0 12s5.4 12 12 12 12-5.4 12-12S18.7 0 12 0zm5.5 17.3c-.2.4-.7.5-1 .2-2.8-1.7-6.4-2.1-10.6-1.1-.4.1-.8-.2-.9-.5-.1-.4.2-.8.6-.9 4.6-1 8.5-.6 11.6 1.3.4.2.5.7.3 1zm1.5-3.3c-.3.4-.8.6-1.3.3-3.2-2-8.1-2.6-11.9-1.4-.5.1-1-.1-1.1-.6-.1-.5.1-1 .6-1.1 4.3-1.3 9.7-.7 13.4 1.6.4.2.6.8.3 1.2zm.1-3.4c-3.9-2.3-10.2-2.5-13.9-1.4-.6.2-1.2-.2-1.4-.7-.2-.6.2-1.2.7-1.4 4.3-1.3 11.3-1 15.7 1.6.5.3.7 1 .4 1.6-.3.5-1 .7-1.5.3z"/></svg>
        <span>Spotify</span>
      </a>
      <a href="https://www.tiktok.com/@pepito" class="soc mag" target="_blank" rel="noopener noreferrer">
        <svg viewBox="0 0 24 24"><path d="M19.6 3.3A4.5 4.5 0 0 1 16.8.9H13v13a2.6 2.6 0 1 1-2-2.5V8.1A6 6 0 0 0 6.3 14a5.9 5.9 0 0 0 11.8 0V9.6a7.8 7.8 0 0 0 4.6 1.5V7.8a4.5 4.5 0 0 1-3.1-4.5z"/></svg>
        <span>TikTok</span>
      </a>
    </div>

    <div class="cta-mail rv">
      Bookings &amp; Collabs &nbsp;·&nbsp;
      <a href="mailto:contact@pepito-officiel.com">contact@pepito-officiel.com</a>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="ft-logo">PEPITO</div>
  <div class="ft-copy">© 2025 Pepito · Tous droits réservés</div>
  <a href="#hero" class="ft-top">
    <svg width="11" height="11" viewBox="0 0 12 12" fill="none" stroke="currentColor" stroke-width="1.5" aria-hidden="true"><path d="M6 10V2M2 6l4-4 4 4"/></svg>
    Haut de page
  </a>
</footer>

<!-- ═══ SCRIPTS ═══ -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/gsap.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/ScrollTrigger.min.js"></script>
<script>
(function() {
  /* ── LOADER ── */
  window.addEventListener('load', () => {
    setTimeout(() => document.getElementById('loader').classList.add('gone'), 1700);
  });

  /* ── SCROLL PROGRESS ── */
  if (window.gsap && window.ScrollTrigger) {
    gsap.registerPlugin(ScrollTrigger);

    gsap.to('#prog', {
      scaleX: 1, ease: 'none',
      scrollTrigger: { start:0, end:'max', scrub:0 }
    });

    /* ── SCROLL REVEALS ── */
    gsap.utils.toArray('.rv').forEach(el => {
      gsap.fromTo(el,
        { y: 36, opacity: 0 },
        { y: 0, opacity: 1, duration: 1.1, ease: 'expo.out',
          scrollTrigger: { trigger: el, start: 'top 88%', once: true }
        }
      );
    });

    /* ── VIDEO CHAPTERS — slide in from sides ── */
    document.querySelectorAll('.vid-ch').forEach((ch, i) => {
      const embed = ch.querySelector('.vid-embed');
      const info  = ch.querySelector('.vid-info');
      const isFlip = ch.classList.contains('flip');

      if (embed) {
        gsap.fromTo(embed,
          { x: isFlip ? 60 : -60, opacity: 0 },
          { x: 0, opacity: 1, duration: 1.2, ease: 'expo.out',
            scrollTrigger: { trigger: embed, start: 'top 85%', once: true }
          }
        );
      }
      if (info) {
        gsap.fromTo(info,
          { x: isFlip ? -60 : 60, opacity: 0 },
          { x: 0, opacity: 1, duration: 1.2, ease: 'expo.out', delay: 0.12,
            scrollTrigger: { trigger: info, start: 'top 85%', once: true }
          }
        );
      }
    });

    /* ── NUMBER COUNTER ── */
    const counterEl = document.querySelector('[data-count]');
    if (counterEl) {
      const target = parseInt(counterEl.dataset.count);
      ScrollTrigger.create({
        trigger: counterEl,
        start: 'top 80%',
        once: true,
        onEnter() {
          let n = 0;
          const step = Math.ceil(target / 30);
          const t = setInterval(() => {
            n = Math.min(n + step, target);
            counterEl.textContent = n;
            if (n >= target) clearInterval(t);
          }, 40);
        }
      });
    }

    /* ── HERO PARALLAX (scroll) ── */
    gsap.to('.h-content', {
      y: 80, ease: 'none',
      scrollTrigger: { trigger: '#hero', start: 'top top', end: 'bottom top', scrub: 1 }
    });

  } else {
    /* Fallback: pure CSS reveal if GSAP fails to load */
    const io = new IntersectionObserver(entries => {
      entries.forEach(e => { if (e.isIntersecting) e.target.style.opacity = '1'; });
    }, { threshold: 0.1 });
    document.querySelectorAll('.rv').forEach(el => {
      el.style.transition = 'opacity .8s ease';
      io.observe(el);
    });
  }

  /* ── CURSOR ── */
  const cur  = document.getElementById('cur');
  const curR = document.getElementById('curR');
  let cx = 0, cy = 0, rx = 0, ry = 0;

  if (window.matchMedia('(hover:hover)').matches) {
    document.addEventListener('mousemove', e => {
      cx = e.clientX; cy = e.clientY;
      cur.style.left = cx + 'px'; cur.style.top = cy + 'px';
    });

    /* Smooth ring follow */
    (function loop() {
      rx += (cx - rx) * 0.12;
      ry += (cy - ry) * 0.12;
      curR.style.left = rx + 'px'; curR.style.top = ry + 'px';
      requestAnimationFrame(loop);
    })();

    document.querySelectorAll('a, button, .vid-embed, .h-genre').forEach(el => {
      el.addEventListener('mouseenter', () => { cur.style.opacity='0'; curR.classList.add('big'); });
      el.addEventListener('mouseleave', () => { cur.style.opacity='1'; curR.classList.remove('big'); });
    });
  }

  /* ── MAGNETIC BUTTONS ── */
  document.querySelectorAll('.mag').forEach(el => {
    el.addEventListener('mousemove', e => {
      const r = el.getBoundingClientRect();
      const x = (e.clientX - r.left - r.width  / 2) * 0.28;
      const y = (e.clientY - r.top  - r.height / 2) * 0.28;
      el.style.transform = `translate(${x}px,${y}px)`;
    });
    el.addEventListener('mouseleave', () => {
      el.style.transform = '';
      el.style.transition = 'transform .6s cubic-bezier(.23,1,.32,1)';
      setTimeout(() => el.style.transition = '', 600);
    });
  });

  /* ── NAV ── */
  const nav = document.getElementById('nav');
  window.addEventListener('scroll', () => nav.classList.toggle('solid', scrollY > 50), { passive:true });

  /* ── MOBILE MENU ── */
  const burger = document.getElementById('burger');
  const mmenu  = document.getElementById('mmenu');
  burger.addEventListener('click', () => {
    burger.classList.toggle('x');
    mmenu.classList.toggle('open');
    document.body.style.overflow = mmenu.classList.contains('open') ? 'hidden' : '';
  });
  window.mmClose = () => {
    burger.classList.remove('x');
    mmenu.classList.remove('open');
    document.body.style.overflow = '';
  };

  /* ── SMOOTH ANCHORS ── */
  document.querySelectorAll('a[href^="#"]').forEach(a => {
    a.addEventListener('click', e => {
      const t = document.querySelector(a.getAttribute('href'));
      if (t) { e.preventDefault(); t.scrollIntoView({ behavior:'smooth' }); }
    });
  });

  /* ── CLICK-TO-PLAY ── */
  const isLocal = location.protocol === 'file:' || location.hostname === '';
  if (isLocal) document.getElementById('local-banner').style.display = 'block';

  document.querySelectorAll('.vid-embed[data-vid]').forEach(wrap => {
    function launch() {
      if (wrap.classList.contains('active')) return;
      const id = wrap.dataset.vid;
      if (isLocal) {
        window.open('https://www.youtube.com/watch?v=' + id, '_blank', 'noopener,noreferrer');
        return;
      }
      const f = document.createElement('iframe');
      f.src = `https://www.youtube-nocookie.com/embed/${id}?autoplay=1&rel=0&modestbranding=1`;
      f.allow = 'autoplay; encrypted-media; picture-in-picture; fullscreen';
      f.allowFullscreen = true;
      f.style.cssText = 'position:absolute;inset:0;width:100%;height:100%;border:none;z-index:10;';
      wrap.appendChild(f);
      wrap.classList.add('active');
    }
    wrap.addEventListener('click', launch);
    wrap.addEventListener('keydown', e => { if (e.key==='Enter'||e.key===' ') launch(); });
  });

})();
</script>
</body>
</html>
