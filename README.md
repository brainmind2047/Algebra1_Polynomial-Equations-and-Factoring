<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Sopaan · Polynomial Equations and Factoring</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Fraunces:opsz,wght@9..144,500;9..144,700&family=Source+Sans+3:wght@400;600;700&family=IBM+Plex+Mono:wght@500;600&display=swap">
<style>
  html,body{margin:0;} img{max-width:100%;} [hidden]{display:none !important;}
  :root{
    --navy:#16264A; --navy-2:#1F3B6B; --gold:#C79A3E; --gold-soft:#F3E7C9;
    --paper:#FBF9F4; --paper-2:#F1EAD8; --card:#FFFFFF;
    --ink:#211E1A; --ink-soft:#655D4C; --rule:#E4DCC8;
    --success:#2E8B57; --success-soft:#E1F2E7;
    --danger:#BF4B45; --danger-soft:#FAE3E1;
    --locked:#C7BEA9;
    --focus:#1F3B6B;
    --accent-text:#1F3B6B; --retry-text:#8A661F;
    color-scheme:light;
  }
  @media (prefers-color-scheme: dark){
    :root:not([data-theme="light"]){
      --navy:#0E1830; --navy-2:#16264A; --gold:#E0B75B; --gold-soft:#3A2F16;
      --paper:#141210; --paper-2:#1C1914; --card:#1C1914;
      --ink:#EDE7DA; --ink-soft:#B2A996; --rule:#3A342A;
      --success:#7BC79A; --success-soft:#1B2E22;
      --danger:#E38884; --danger-soft:#331D1B;
      --locked:#4A4436;
      --focus:#E0B75B;
      --accent-text:#E0B75B; --retry-text:#E0B75B;
      color-scheme:dark;
    }
  }
  :root[data-theme="dark"]{
    --navy:#0E1830; --navy-2:#16264A; --gold:#E0B75B; --gold-soft:#3A2F16;
    --paper:#141210; --paper-2:#1C1914; --card:#1C1914;
    --ink:#EDE7DA; --ink-soft:#B2A996; --rule:#3A342A;
    --success:#7BC79A; --success-soft:#1B2E22;
    --danger:#E38884; --danger-soft:#331D1B;
    --locked:#4A4436;
    --focus:#E0B75B;
    --accent-text:#E0B75B; --retry-text:#E0B75B;
    color-scheme:dark;
  }

  *{box-sizing:border-box;}
  body{background:var(--paper); color:var(--ink); font-family:'Source Sans 3',-apple-system,'Segoe UI',sans-serif; padding-inline:0; padding-block:0;}
  h1,h2,h3{font-family:'Fraunces',Georgia,serif; text-wrap:balance; margin:0;}
  .num{font-family:'IBM Plex Mono',ui-monospace,monospace; font-variant-numeric:tabular-nums;}

  header.brand{
    background:linear-gradient(155deg,var(--navy) 0%, var(--navy-2) 100%);
    color:#F4EFDF; padding-block:calc(20px + env(safe-area-inset-top,0px)) 18px; padding-inline:20px;
  }
  .brand-row{display:flex; align-items:center; gap:12px; max-width:900px; margin:0 auto;}
  .crest{
    width:42px; height:42px; border-radius:10px; background:var(--gold); color:var(--navy);
    display:flex; align-items:center; justify-content:center; font-family:'Fraunces',serif; font-weight:700; font-size:18px; flex-shrink:0;
  }
  .brand-name{font-size:12px; letter-spacing:.08em; text-transform:uppercase; color:var(--gold); font-weight:700;}
  .series-name{font-size:19px; font-weight:700; font-family:'Fraunces',serif;}
  .chapter-eyebrow{max-width:900px; margin:14px auto 0; font-size:12px; letter-spacing:.06em; text-transform:uppercase; color:#AEB9D6;}
  .chapter-title{font-size:28px; max-width:900px; margin:2px auto 0;}
  .chapter-sub{font-size:14.5px; color:var(--gold); font-weight:700; max-width:900px; margin:3px auto 0;}

  .chapter-progress{max-width:900px; margin:14px auto 0; display:flex; align-items:center; gap:10px;}
  .cp-track{flex:1; height:6px; border-radius:99px; background:rgba(255,255,255,.18); overflow:hidden;}
  .cp-fill{height:100%; background:var(--gold); border-radius:99px; transition:width .3s ease;}
  .cp-label{font-size:11.5px; color:#CFD7EA; white-space:nowrap;}

  .tabbar{position:sticky; top:env(safe-area-inset-top,0px); z-index:15; background:var(--paper); border-bottom:1px solid var(--rule); overflow-x:auto; white-space:nowrap;}
  .tabbar-inner{max-width:900px; margin:0 auto; display:flex; padding-inline:16px;}
  .tab-btn{font-family:inherit; font-size:14px; font-weight:600; color:var(--ink-soft); background:none; border:none; padding:13px 16px; cursor:pointer; position:relative; flex-shrink:0;}
  .tab-btn.active{color:var(--accent-text);}
  .tab-btn.active::after{content:''; position:absolute; left:12px; right:12px; bottom:0; height:3px; background:var(--gold); border-radius:3px 3px 0 0;}
  .tab-count{font-size:11px; color:var(--ink-soft); margin-left:5px;}

  .slide-progress{max-width:900px; margin:0 auto; padding:10px 16px 0; display:flex; align-items:center; gap:10px;}
  .sp-track{flex:1; height:5px; border-radius:99px; background:var(--rule); overflow:hidden;}
  .sp-fill{height:100%; background:var(--accent-text); border-radius:99px; transition:width .3s ease;}
  .sp-label{font-size:12px; color:var(--ink-soft); white-space:nowrap; font-weight:600;}

  .wrap{max-width:900px; margin:0 auto; padding:16px 16px calc(110px + env(safe-area-inset-bottom,0px));}

  .qcard{background:var(--card); border:1px solid var(--rule); border-radius:14px; padding:18px;}
  .qhead{display:flex; align-items:flex-start; gap:10px; margin-bottom:10px;}
  .qnum{width:32px; height:32px; border-radius:8px; background:var(--gold-soft); color:var(--accent-text); display:flex; align-items:center; justify-content:center; font-weight:700; font-family:'Fraunces',serif; flex-shrink:0; font-size:14px;}
  .qtext{font-size:16px; line-height:1.55; flex:1;}
  .qtag{font-size:10.5px; color:var(--gold); background:var(--gold-soft); padding:2px 7px; border-radius:99px; font-weight:700; margin-left:6px; white-space:nowrap;}
  .marks-pill{font-size:11px; font-weight:700; color:var(--ink-soft); border:1px solid var(--rule); padding:3px 9px; border-radius:99px; margin-left:auto; flex-shrink:0; white-space:nowrap;}
  .step-badge{font-size:11px; font-weight:700; color:var(--accent-text); background:var(--paper-2); border:1px solid var(--rule); padding:3px 9px; border-radius:99px; display:inline-block; margin-bottom:12px;}

  .options{display:flex; flex-direction:column; gap:8px; margin-top:10px;}
  .opt{display:flex; align-items:center; gap:10px; padding:11px 12px; border:1.5px solid var(--rule); border-radius:10px; cursor:pointer; font-size:15px; background:var(--paper);}
  .opt input{accent-color:var(--navy-2);}
  .opt.is-correct{border-color:var(--success); background:var(--success-soft);}
  .opt.is-wrong{border-color:var(--danger); background:var(--danger-soft);}
  .opt.locked{cursor:not-allowed;}

  .subpart-label{font-weight:700; font-size:12.5px; color:var(--accent-text); text-transform:uppercase; letter-spacing:.03em; margin:14px 0 6px;}
  .or-divider{text-align:center; font-size:11px; font-weight:700; letter-spacing:.08em; color:var(--ink-soft); margin:8px 0;}

  .steps{display:flex; flex-direction:column; gap:10px;}
  .step-line{font-size:14.5px; line-height:1.9; background:var(--paper); border:1px dashed var(--rule); border-radius:10px; padding:9px 12px;}
  .step-line.resolved{opacity:.9;}
  .blank-input{font-family:'IBM Plex Mono',monospace; font-size:14px; border:1.5px solid var(--rule); border-radius:6px; padding:3px 8px; width:120px; background:var(--card); color:var(--ink); margin:0 2px;}
  .blank-input:focus{outline:none; border-color:var(--focus); box-shadow:0 0 0 3px var(--gold-soft);}
  .blank-input.is-correct{border-color:var(--success); background:var(--success-soft);}
  .blank-input.is-wrong{border-color:var(--danger); background:var(--danger-soft);}
  .blank-input[disabled]{opacity:.85;}
  .reveal-note{font-size:12px; color:var(--danger); padding-left:2px; margin-top:-2px;}

  .feedback{font-size:13.5px; padding:10px 12px; border-radius:9px; margin-top:14px; display:none;}
  .feedback.show{display:block;}
  .feedback.ok{background:var(--success-soft); color:var(--success);}
  .feedback.retry{background:var(--gold-soft); color:var(--retry-text);}
  .feedback.reveal{background:var(--danger-soft); color:var(--danger);}
  .feedback.err{background:var(--danger-soft); color:var(--danger);}
  .attempts-dots{display:inline-flex; gap:4px; margin-left:2px;}
  .attempts-dots span{width:6px; height:6px; border-radius:50%; background:var(--ink-soft); opacity:.3; display:inline-block;}
  .attempts-dots span.used{opacity:1; background:var(--danger);}

  .ar-box{background:var(--paper-2); border-radius:10px; padding:10px 12px; margin-bottom:12px; font-size:13px; color:var(--ink-soft);}

  .navbar{
    position:fixed; left:0; right:0; bottom:0; z-index:30; background:var(--paper);
    border-top:1px solid var(--rule); padding:10px 16px calc(10px + env(safe-area-inset-bottom,0px));
  }
  .navbar-inner{max-width:900px; margin:0 auto; display:flex; gap:8px; flex-wrap:wrap; align-items:center;}
  .btn{font-family:inherit; font-size:13.5px; font-weight:700; padding:10px 14px; border-radius:9px; border:1.5px solid var(--rule); background:var(--card); color:var(--ink); cursor:pointer;}
  .btn:hover{border-color:var(--navy-2);}
  .btn:disabled{opacity:.4; cursor:not-allowed;}
  .btn-primary{background:var(--navy-2); color:#fff; border-color:var(--navy-2);}
  .navbar .spacer{flex:1;}

  .fab{position:fixed; right:16px; bottom:calc(74px + env(safe-area-inset-bottom,0px)); background:var(--gold); color:var(--navy); border:none; border-radius:999px; padding:11px 16px; font-family:inherit; font-weight:700; font-size:13px; display:flex; align-items:center; gap:7px; cursor:pointer; box-shadow:0 6px 16px rgba(0,0,0,.18); z-index:35;}
  .fab-badge{background:rgba(255,255,255,.55); border-radius:99px; padding:1px 7px; font-size:11px;}

  .overlay{position:fixed; inset:0; background:rgba(20,18,14,.45); z-index:50; display:none; align-items:flex-end; justify-content:center;}
  .overlay.show{display:flex;}
  .palette{background:var(--card); width:min(480px,100%); max-height:78vh; overflow-y:auto; border-radius:18px 18px 0 0; padding:18px 18px calc(18px + env(safe-area-inset-bottom,0px)); border:1px solid var(--rule); border-bottom:none;}
  @media (min-width:640px){ .overlay{align-items:center;} .palette{border-radius:18px; border-bottom:1px solid var(--rule); max-height:74vh;} }
  .palette-head{display:flex; align-items:center; justify-content:space-between; margin-bottom:6px;}
  .palette-head h2{font-size:16px;}
  .palette-close{background:none; border:none; font-size:20px; color:var(--ink-soft); cursor:pointer; padding:4px;}
  .palette-legend{display:flex; gap:12px; flex-wrap:wrap; font-size:11px; color:var(--ink-soft); margin:10px 0 14px;}
  .palette-legend span{display:inline-flex; align-items:center; gap:5px;}
  .dot{width:9px; height:9px; border-radius:50%; display:inline-block;}
  .dot.correct{background:var(--success);} .dot.revealed{background:var(--danger);}
  .dot.skipped{background:var(--gold);} .dot.locked{background:var(--locked);}
  .dot.current{background:var(--navy-2);}
  .chip-grid{display:grid; grid-template-columns:repeat(auto-fill,minmax(48px,1fr)); gap:8px;}
  .chip{border:1.5px solid var(--rule); border-radius:9px; padding:8px 4px; text-align:center; font-family:'IBM Plex Mono',monospace; font-size:12.5px; font-weight:600; cursor:pointer; background:var(--paper); color:var(--ink);}
  .chip[data-status="correct"]{border-color:var(--success); background:var(--success-soft); color:var(--success);}
  .chip[data-status="revealed"]{border-color:var(--danger); background:var(--danger-soft); color:var(--danger);}
  .chip[data-status="skipped"]{border-color:var(--gold); background:var(--gold-soft); color:var(--retry-text);}
  .chip[data-status="locked"]{border-color:var(--rule); color:var(--locked); cursor:not-allowed; background:var(--paper-2);}
  .chip[data-status="current"]{outline:2px solid var(--navy-2); outline-offset:1px;}

  .toast{position:fixed; left:50%; bottom:calc(140px + env(safe-area-inset-bottom,0px)); transform:translateX(-50%); background:var(--ink); color:var(--paper); padding:9px 16px; border-radius:99px; font-size:13px; opacity:0; pointer-events:none; transition:opacity .25s ease; z-index:60;}
  .toast.show{opacity:1;}

  .done-card{text-align:center; padding:36px 20px;}
  .done-card .big{font-size:38px; margin-bottom:6px;}
  .score-pills{display:flex; gap:10px; justify-content:center; flex-wrap:wrap; margin:16px 0;}
  .score-pill{padding:8px 16px; border-radius:99px; font-size:13px; font-weight:700;}

  footer.brandfoot{max-width:900px; margin:14px auto 0; padding:0 16px calc(110px + env(safe-area-inset-bottom,0px)); text-align:center; font-size:12px; color:var(--ink-soft);}

  .mode-pill{font-family:inherit; font-size:12.5px; font-weight:700; color:var(--navy); background:var(--gold); border:none; border-radius:99px; padding:6px 14px; cursor:pointer; margin-top:12px; display:inline-flex; align-items:center; gap:6px;}
  .mode-pick{display:flex; flex-direction:column; gap:14px; padding:8px 0 24px;}
  .mode-card{background:var(--card); border:1.5px solid var(--rule); border-radius:16px; padding:22px; cursor:pointer; text-align:left;}
  .mode-card:hover{border-color:var(--navy-2);}
  .mode-card .mode-icon{font-size:26px; margin-bottom:8px;}
  .mode-card h3{font-size:18px; margin-bottom:6px;}
  .mode-card p{font-size:13.5px; color:var(--ink-soft); line-height:1.5; margin:0;}
  .quiz-hint{font-size:12.5px; color:var(--ink-soft); background:var(--paper-2); border-radius:9px; padding:8px 12px; margin-bottom:14px;}
  .review-row{border:1px solid var(--rule); border-radius:10px; padding:11px 13px; margin-bottom:10px;}
  .review-tag{font-size:11.5px; font-weight:700; margin-bottom:4px; display:block;}
  .review-tag.ok{color:var(--success);} .review-tag.bad{color:var(--danger);} .review-tag.na{color:var(--ink-soft);}
  .review-q{font-size:13.5px; margin-bottom:6px; color:var(--ink-soft);}
  .review-ans{font-size:13px; margin-bottom:2px;}

  .who-row{max-width:900px; margin:12px auto 0; display:flex; flex-wrap:wrap; gap:8px; align-items:center;}
  .who-row .mode-pill{margin-top:0;}
  .who{display:inline-flex; flex-wrap:wrap; align-items:center; gap:6px; font-size:12.5px; color:#CFD7EA;}
  .who b{color:#F4EFDF;}
  .who button{font-family:inherit; font-size:12px; font-weight:700; color:#F4EFDF; background:rgba(255,255,255,.12); border:1px solid rgba(255,255,255,.22); border-radius:99px; padding:5px 11px; cursor:pointer;}
  .who button:hover{background:rgba(255,255,255,.2);}
  .login-card{max-width:460px; margin:8px auto 0; background:var(--card); border:1px solid var(--rule); border-radius:16px; padding:22px;}
  .login-card h2{font-size:21px; margin-bottom:4px;}
  .login-card p.lead{font-size:13.5px; color:var(--ink-soft); margin:0 0 16px; line-height:1.5;}
  .fld{display:flex; flex-direction:column; gap:5px; margin-bottom:12px;}
  .fld label{font-size:12px; font-weight:700; letter-spacing:.04em; text-transform:uppercase; color:var(--ink-soft);}
  .fld input{font-family:inherit; font-size:15px; padding:10px 12px; border:1.5px solid var(--rule); border-radius:9px; background:var(--paper); color:var(--ink);}
  .fld input:focus{outline:none; border-color:var(--focus); box-shadow:0 0 0 3px var(--gold-soft);}
  .fld-row{display:grid; grid-template-columns:1fr 1fr; gap:10px;}
  .login-err{font-size:13px; color:var(--danger); background:var(--danger-soft); border-radius:8px; padding:8px 10px; margin-bottom:12px;}
  .login-note{font-size:12px; color:var(--ink-soft); margin-top:12px; line-height:1.5;}
  .known{margin:0 0 16px; display:flex; flex-direction:column; gap:6px;}
  .known-label{font-size:12px; font-weight:700; letter-spacing:.04em; text-transform:uppercase; color:var(--ink-soft);}
  .known-btn{display:flex; justify-content:space-between; align-items:center; gap:10px; text-align:left; font-family:inherit; font-size:14.5px; padding:10px 12px; border:1.5px solid var(--rule); border-radius:10px; background:var(--paper); color:var(--ink); cursor:pointer;}
  .known-btn:hover{border-color:var(--navy-2);}
  .known-btn small{font-size:12px; color:var(--ink-soft);}
  .rec-card{background:var(--card); border:1px solid var(--rule); border-radius:14px; padding:18px; margin-bottom:14px;}
  .rec-card h2{font-size:19px; margin-bottom:10px;}
  .rec-card h3{font-size:15px; margin:4px 0 8px;}
  .rec-table-wrap{overflow-x:auto;}
  .rec-table{width:100%; border-collapse:collapse; font-size:13.5px; font-variant-numeric:tabular-nums;}
  .rec-table th{text-align:left; font-size:11.5px; text-transform:uppercase; letter-spacing:.04em; color:var(--ink-soft); padding:6px 8px; border-bottom:1px solid var(--rule); white-space:nowrap;}
  .rec-table td{padding:8px; border-bottom:1px solid var(--rule); white-space:nowrap;}
  .rec-bar{display:inline-block; width:70px; height:6px; border-radius:99px; background:var(--rule); overflow:hidden; vertical-align:middle; margin-right:6px;}
  .rec-bar i{display:block; height:100%; background:var(--success);}
  .rec-empty{font-size:13.5px; color:var(--ink-soft);}
  .sec-sub{max-width:900px; margin:0 auto; padding:10px 16px 0; font-size:12.5px; font-weight:700; color:var(--accent-text); letter-spacing:.02em;}
  .opt{flex-wrap:wrap;}
  .opt-l{font-family:'IBM Plex Mono',monospace; font-size:13px; font-weight:600; color:var(--ink-soft);}
  .opt-t{flex:1; min-width:0;}
  .opt.is-chosen:not(.is-correct):not(.is-wrong){border-color:var(--navy-2); background:var(--gold-soft);}
  .opt-tag{font-size:11px; font-weight:700; padding:2px 8px; border-radius:99px; background:var(--card); border:1px solid currentColor; white-space:nowrap;}
  .opt.is-correct .opt-tag{color:var(--success);} .opt.is-wrong .opt-tag{color:var(--danger);} .opt.is-chosen:not(.is-correct):not(.is-wrong) .opt-tag{color:var(--accent-text);}
  .chosen{font-size:13.5px; margin-top:10px; padding:8px 12px; border-radius:9px;}
  .chosen.ok{background:var(--success-soft); color:var(--success);} .chosen.bad{background:var(--danger-soft); color:var(--danger);}
  .chosen + .chosen{margin-top:6px;}
  .solution{margin-top:14px; border:1px solid var(--rule); border-left:4px solid var(--gold); background:var(--paper-2); border-radius:10px; padding:12px 14px;}
  .sol-h{font-family:'Fraunces',Georgia,serif; font-weight:700; font-size:14px; color:var(--accent-text); margin-bottom:6px;}
  .sol-line{font-size:14.5px; line-height:1.7;}
  .rev-sol summary{cursor:pointer; font-size:12.5px; font-weight:700; color:var(--accent-text); margin-top:6px;}
  .rev-sol .solution{margin-top:8px;}
  .chapter-credit{max-width:900px; margin:4px auto 0; font-size:12px; color:#CFD7EA;}
  footer.brandfoot a{color:inherit;}
  .blank-input.wide{width:260px; max-width:100%; font-family:'Source Sans 3',sans-serif;}
  .blank-input.expr{width:170px; max-width:100%;}
  /*fix-layout*/ .cp-fill,.sp-fill{width:0;} .fld{min-width:0;} .fld input{width:100%; min-width:0; box-sizing:border-box;}
  .fig{margin:6px 0 10px; display:flex; justify-content:center;}
  .figsvg{width:100%; max-width:340px; height:auto; overflow:visible;}
  .figsvg .ln,.figsvg .arm{stroke:var(--ink); stroke-width:1.6; fill:none;}
  .figsvg .arm{stroke:var(--accent-text); stroke-width:2;}
  .figsvg .pt{fill:var(--ink);}
  .figsvg .lb{fill:var(--ink); font:600 13px 'Source Sans 3',sans-serif;}
  .figsvg .al{fill:var(--accent-text); font:700 12px 'Source Sans 3',sans-serif;}
  .figsvg .wg{fill:var(--gold-soft); stroke:var(--gold); stroke-width:1.2;}
  .figsvg .wg2{fill:rgba(199,154,62,.35); stroke:var(--gold); stroke-width:1.2;}
  .figsvg .ra{fill:none; stroke:var(--ink); stroke-width:1.2;}
  .figsvg .ahd{fill:var(--ink);}
  .figsvg .pr{fill:var(--paper-2); stroke:var(--ink-soft); stroke-width:1.2;}
  .figsvg .tk{stroke:var(--ink-soft); stroke-width:.8;}
  .figsvg .po{fill:var(--ink); font:600 8.5px 'IBM Plex Mono',monospace;}
  .figsvg .pi{fill:var(--danger); font:600 7.5px 'IBM Plex Mono',monospace;}
  .figsvg .sh{fill:var(--gold-soft); stroke:var(--ink); stroke-width:1.5; stroke-linejoin:round;}
  .figsvg .sh2{fill:rgba(199,154,62,.38); stroke:var(--ink); stroke-width:1.5; stroke-linejoin:round;}
  .figsvg .sh3{fill:rgba(199,154,62,.22); stroke:var(--ink); stroke-width:1.5; stroke-linejoin:round;}
  .figsvg .none{fill:none;}
  .figsvg .hid{stroke-dasharray:5 4; fill:none;}
  .figsvg .tick{stroke:var(--ink); stroke-width:1.4; fill:none;}
  .figsvg .shd{fill:var(--accent-text); fill-opacity:.55;}
  .figsvg .cell{fill:var(--card); stroke:var(--ink); stroke-width:1.1;}
  .figsvg .dr{fill:var(--danger);} .figsvg .dw{fill:var(--card); stroke:var(--ink); stroke-width:1.2;}
  .figsvg .dotfill{fill:var(--danger);}
  .tt{border-collapse:collapse; font-size:13.5px; margin:4px auto; font-variant-numeric:tabular-nums;} .tt th,.tt td{border:1px solid var(--rule); padding:4px 9px; text-align:left;} .tt th{background:var(--paper-2); font-weight:700;} .ttw{overflow-x:auto; max-width:100%;}
  .fq{display:inline-flex; flex-direction:column; vertical-align:middle; text-align:center; font-size:.82em; line-height:1.12; margin:0 2px;}
  .fq>span:first-child{border-bottom:1.5px solid currentColor; padding:0 2px;}
  .fq>span:last-child{padding:0 2px;}
  .mx{white-space:nowrap;}
  .blank-input.fr{width:110px;}
  @media (prefers-reduced-motion:reduce){ *{transition:none !important;} }
.datline{display:block;margin-top:8px;padding:8px 10px;border-radius:8px;background:var(--paper-2);font:500 14px/1.7 'IBM Plex Mono',monospace;word-spacing:2px;overflow-wrap:anywhere;}

  .theory{display:flex;flex-direction:column;gap:16px;padding-bottom:40px;}
  .hub{display:grid;grid-template-columns:1fr;gap:12px;}
  @media (min-width:640px){ .hub{grid-template-columns:repeat(3,1fr);} }
  .hub-card{background:var(--card);border:1px solid var(--rule);border-radius:14px;padding:16px;display:flex;flex-direction:column;gap:8px;}
  .hub-card h3{font-family:'Fraunces',serif;font-size:18px;margin:0;color:var(--accent-text);}
  .hub-card p{margin:0;font-size:14px;color:var(--ink-soft);line-height:1.5;}
  .hub-btns{display:flex;flex-wrap:wrap;gap:8px;margin-top:auto;}
  .hub-btn{min-height:40px;border:1.5px solid var(--rule);background:var(--paper-2);color:var(--ink);border-radius:10px;padding:8px 12px;font:600 14px 'Source Sans 3',sans-serif;cursor:pointer;text-align:left;}
  .hub-btn:hover{border-color:var(--gold);}
  .hub-btn.primary{background:var(--navy);color:#F4EFDF;border-color:var(--navy);}
  .note{background:var(--card);border:1px solid var(--rule);border-radius:14px;padding:18px;scroll-margin-top:120px;}
  .note h2{font-family:'Fraunces',serif;font-size:22px;margin:0 0 4px;color:var(--ink);}
  .note .lt{font-size:13.5px;color:var(--ink-soft);margin:0 0 12px;}
  .note .lt b{color:var(--accent-text);}
  .note h4{font:700 15px 'Source Sans 3',sans-serif;margin:16px 0 6px;color:var(--accent-text);}
  .note p,.note li{font-size:15.5px;line-height:1.6;}
  .note ul{padding-left:20px;margin:6px 0;}
  .keybox{background:var(--gold-soft);border-left:4px solid var(--gold);border-radius:8px;padding:10px 12px;margin:10px 0;font-size:15px;line-height:1.6;}
  .keybox b{color:var(--ink);}
  .ex{background:var(--paper-2);border-radius:10px;padding:12px;margin:10px 0;}
  .ex .exh{font-family:'Fraunces',serif;font-weight:700;color:var(--accent-text);margin-bottom:4px;}
  .ex .exl{font-size:15px;line-height:1.7;}
  .ttab{width:100%;border-collapse:collapse;font-size:14.5px;margin:8px 0;}
  .ttab th,.ttab td{border:1px solid var(--rule);padding:7px 8px;text-align:left;vertical-align:top;}
  .ttab th{background:var(--paper-2);}
  .tscroll{overflow-x:auto;}
  .mono{font-family:'IBM Plex Mono',monospace;font-size:.92em;}
  @media (max-width:480px){ .ttab{font-size:13.5px;} .ttab th,.ttab td{padding:6px;} }
  .note .figsvg{max-width:100%;height:auto;display:block;margin:8px auto;}


  .rep-top{display:flex;flex-wrap:wrap;gap:18px;align-items:center;justify-content:center;margin-top:8px;}
  .rep-legend{flex:1;min-width:220px;display:flex;flex-direction:column;gap:8px;}
  .rep-cap{font:700 13px 'Source Sans 3',sans-serif;color:var(--ink-soft);text-transform:uppercase;letter-spacing:.05em;}
  .rep-li{display:flex;align-items:center;gap:6px;font-size:15px;}
  .rep-n{margin-left:auto;white-space:nowrap;padding-left:8px;font-family:'IBM Plex Mono',monospace;font-weight:600;}
  .sw{display:inline-block;width:12px;height:12px;border-radius:3px;flex:none;}
  .rep-grid{display:grid;grid-template-columns:1fr;gap:12px;}
  @media (min-width:640px){ .rep-grid{grid-template-columns:1fr 1fr;} }
  .rep-card{background:var(--card);border:1px solid var(--rule);border-radius:14px;padding:14px;display:flex;flex-direction:column;gap:10px;}
  .rep-h{display:flex;align-items:center;gap:8px;font:700 16px 'Source Sans 3',sans-serif;}
  .crit{display:inline-grid;place-items:center;width:28px;height:28px;border-radius:50%;color:var(--card);font:700 15px Fraunces,serif;flex:none;}
  .rep-row{display:flex;gap:14px;align-items:center;}
  .rep-stats{display:flex;flex-direction:column;gap:5px;font-size:14.5px;}
  .rep-stats div{display:flex;align-items:center;gap:6px;}
  .rep-lvl{margin-top:4px;color:var(--accent-text);} .rep-lvl span{color:var(--ink-soft);font-size:13px;}
  .rep-note{font-size:13px;color:var(--ink-soft);}


  .skip-chips{display:flex;flex-wrap:wrap;gap:8px;justify-content:center;margin:12px 0;}
  .skip-chips .chip{min-width:48px;min-height:40px;cursor:pointer;border:1.5px solid var(--gold);background:var(--gold-soft);color:var(--retry-text);border-radius:10px;font:600 14px 'IBM Plex Mono',monospace;}
  .skip-btns{display:flex;flex-wrap:wrap;gap:10px;justify-content:center;margin-top:12px;}


  .kb-toggle{border:none;background:transparent;font-size:15px;cursor:pointer;padding:0 2px;vertical-align:middle;opacity:.7;}
  .vkb{position:fixed;left:0;right:0;bottom:0;z-index:80;background:var(--paper-2);border-top:1px solid var(--rule);box-shadow:0 -6px 20px rgba(0,0,0,.12);padding:6px 6px 8px;display:none;}
  .vkb.show{display:block;}
  .vkb-top{display:flex;justify-content:space-between;align-items:center;max-width:640px;margin:0 auto 4px;font:600 12px 'Source Sans 3',sans-serif;color:var(--ink-soft);}
  .vkb-link{border:none;background:none;color:var(--accent-text);font:600 12px 'Source Sans 3',sans-serif;cursor:pointer;text-decoration:underline;}
  .vkb-row{display:flex;gap:5px;max-width:640px;margin:0 auto 5px;}
  .vkb-k{flex:1;min-height:42px;border:1px solid var(--rule);border-radius:8px;background:var(--card);color:var(--ink);font:600 17px 'IBM Plex Mono',monospace;cursor:pointer;padding:0;}
  .vkb-k.fn{font:600 13px 'Source Sans 3',sans-serif;background:var(--gold-soft);}
  .vkb-k.done{background:var(--navy);color:#F4EFDF;border-color:var(--navy);}
  .vkb-k:active{transform:scale(.96);}
  body.kb-open .wrap{padding-bottom:360px;}
  body.kb-open .fab{display:none;}
  .tool-bar{display:flex;gap:8px;flex-wrap:wrap;margin:-4px 0 10px;}
  .tool-btn{min-height:36px;border:1.5px solid var(--gold);background:var(--gold-soft);color:var(--ink);border-radius:18px;padding:4px 12px;font:600 13.5px 'Source Sans 3',sans-serif;cursor:pointer;}
  .tool-panel{position:fixed;z-index:85;background:var(--card);border:1px solid var(--rule);border-radius:14px;box-shadow:0 10px 30px rgba(0,0,0,.25);display:none;}
  .tool-panel.show{display:block;}
  .tp-head{display:flex;align-items:center;gap:8px;padding:8px 10px;border-bottom:1px solid var(--rule);font:600 14px 'Source Sans 3',sans-serif;}
  .tp-note{font-size:12px;color:var(--ink-soft);font-weight:500;}
  .tp-x{margin-left:auto;border:1px solid var(--rule);background:var(--paper-2);color:var(--ink);border-radius:8px;min-height:32px;padding:2px 10px;cursor:pointer;font:600 13px 'Source Sans 3',sans-serif;}
  .tp-x + .tp-x{margin-left:0;}
  .calc{right:12px;bottom:84px;width:min(330px,calc(100vw - 24px));}
  body.calc-open .wrap{padding-bottom:440px;}
  body.calc-open .fab{display:none;}
  @media (max-width:640px){ .calc{left:6px;right:6px;width:auto;} .calc-keys button{min-height:36px;} }
  .calc-disp{padding:8px 12px;text-align:right;background:var(--paper-2);}
  .calc-expr{font:500 13px 'IBM Plex Mono',monospace;color:var(--ink-soft);min-height:18px;word-break:break-all;}
  .calc-res{font:600 24px 'IBM Plex Mono',monospace;color:var(--ink);word-break:break-all;}
  .calc-keys{display:grid;grid-template-columns:repeat(6,1fr);gap:5px;padding:8px;}
  .calc-keys button{min-height:40px;border:1px solid var(--rule);border-radius:8px;background:var(--card);color:var(--ink);font:600 14px 'IBM Plex Mono',monospace;cursor:pointer;padding:0;}
  .calc-keys button.fn{background:var(--gold-soft);font-family:'Source Sans 3',sans-serif;font-size:13px;}
  .calc-keys button.eq{grid-column:span 2;background:var(--navy);color:#F4EFDF;border-color:var(--navy);}
  .desmos{left:50%;top:50%;transform:translate(-50%,-50%);width:min(760px,calc(100vw - 16px));height:min(560px,calc(100vh - 90px));flex-direction:column;}
  .desmos.show{display:flex;}
  #desmosBox{flex:1;min-height:0;border-radius:0 0 14px 14px;overflow:hidden;}
  .desmos-msg{padding:24px;text-align:center;color:var(--ink-soft);}
  .chip[data-status="skipped"]{cursor:pointer;}
  .chip[data-status="answered"]{border-color:var(--accent-text);color:var(--accent-text);}


  button.crest-home{border:none;padding:0;position:relative;cursor:pointer;transition:transform .15s ease;}
  button.crest-home:hover,button.crest-home:focus-visible{transform:scale(1.06);outline:2px solid var(--gold);outline-offset:2px;}
  .crest-h{position:absolute;right:-7px;bottom:-7px;width:18px;height:18px;border-radius:50%;background:#F4EFDF;color:var(--navy);font:700 12px/18px 'Source Sans 3',sans-serif;text-align:center;box-shadow:0 1px 3px rgba(0,0,0,.3);}
  .brand .brand-row{position:relative;}
  .bmasw{position:absolute;left:50%;top:50%;transform:translate(-50%,-50%);display:flex;flex-shrink:0;white-space:nowrap;align-items:center;gap:6px;background:rgba(255,255,255,.12);border:1px solid rgba(255,255,255,.25);border-radius:99px;padding:5px 14px;color:#F4EFDF;}
  .bmasw-ic{font-size:16px;} .bmasw-t{font:600 20px 'IBM Plex Mono',monospace;letter-spacing:.02em;min-width:62px;text-align:center;}
  .bmasw-b{border:none;background:rgba(255,255,255,.18);color:#F4EFDF;border-radius:50%;width:30px;height:30px;cursor:pointer;font-size:13px;}
  .bmasw.off{display:none;}
  @media (max-width:560px){ .bmasw{position:static;transform:none;margin-left:auto;padding:4px 5px 4px 8px;gap:4px;} .bmasw-ic{display:none;} .bmasw-t{font-size:16px;min-width:48px;} .bmasw-b{width:26px;height:26px;} .brand .series-name{font-size:15px;} .brand .brand-name{font-size:10.5px;} .brand .brand-row>div:not(.bmasw){min-width:0;} }
  .bmasw-done{font:600 15px 'IBM Plex Mono',monospace;color:var(--accent-text);margin:4px 0 8px;}
  .sp-fab{position:fixed;left:14px;bottom:84px;z-index:60;border:1.5px solid var(--navy-2);background:var(--card);color:var(--ink);border-radius:99px;padding:9px 14px;font:700 14px 'Source Sans 3',sans-serif;box-shadow:0 4px 14px rgba(0,0,0,.15);cursor:pointer;}
  .sp-fab.on{background:var(--navy);color:#F4EFDF;}
  body.kb-open .sp-fab{display:none;}
  .sp-canvas{position:absolute;z-index:55;display:none;touch-action:none;cursor:crosshair;}
  .sp-canvas.passive{pointer-events:none;cursor:default;}
  .sp-bar{position:fixed;top:8px;left:8px;right:8px;margin:0 auto;width:max-content;z-index:90;display:none;align-items:center;gap:6px;background:var(--card);border:1px solid var(--rule);border-radius:14px;padding:6px 8px;box-shadow:0 6px 20px rgba(0,0,0,.2);max-width:calc(100vw - 16px);flex-wrap:wrap;justify-content:center;}
  .sp-lbl{font:700 13px 'Source Sans 3',sans-serif;color:var(--ink-soft);margin-right:2px;}
  .sp-pen,.sp-tool{width:38px;height:38px;border-radius:10px;border:1.5px solid var(--rule);background:var(--paper);cursor:pointer;display:inline-flex;align-items:center;justify-content:center;font-size:17px;padding:0;color:var(--ink);}
  .sp-pen i{width:20px;height:20px;border-radius:50%;display:block;}
  .sp-pen.on,.sp-tool.on{border-color:var(--navy-2);box-shadow:0 0 0 3px var(--gold-soft);}
  @media (max-width:560px){ .sp-lbl{display:none;} .sp-pen,.sp-tool{width:34px;height:34px;} .sp-fab span{display:none;} }

  /* larger reading sizes */
  .chapter-eyebrow{font-size:13.5px;}
  .chapter-title{font-size:36px;line-height:1.15;}
  .chapter-sub{font-size:16.5px;}
  .tab-btn{font-size:15.5px;}
  .sec-sub{font-size:15px;}
  .qtext{font-size:19px;line-height:1.55;}
  .qnum{width:36px;height:36px;font-size:16px;}
  .opt{font-size:17.5px;padding:12px 14px;}
  .step-line{font-size:17.5px;line-height:2;}
  .blank-input{font-size:16px;}
  .sol-line{font-size:16.5px;}
  .feedback{font-size:15px;}
  .note h2{font-size:28px;}
  .note h4{font-size:19px;}
  .note p,.note li{font-size:17.5px;line-height:1.65;}
  .note .lt{font-size:15.5px;}
  .ex .exh{font-size:18px;} .ex .exl{font-size:16.5px;}
  .keybox{font-size:16.5px;}
  .ttab{font-size:15.5px;}
  .hub-card h3{font-size:21px;} .hub-card p{font-size:15.5px;} .hub-btn{font-size:15px;}
  @media (max-width:480px){ .chapter-title{font-size:30px;} .qtext{font-size:18px;} .opt,.step-line{font-size:16.5px;} .note h2{font-size:24px;} .note p,.note li{font-size:16.5px;} }

  /* v4 celebration */
  .v4conf{position:fixed;inset:0;width:100vw;height:100vh;pointer-events:none;z-index:9999;}
  .v4ban{background:linear-gradient(135deg,var(--gold-soft),var(--card));border:2px solid var(--gold);border-radius:18px;padding:18px 14px 16px;margin:-4px 0 18px;text-align:center;animation:v4pop .55s cubic-bezier(.2,1.6,.4,1);}
  @keyframes v4pop{0%{transform:scale(.6);opacity:0}100%{transform:scale(1);opacity:1}}
  .v4trophy{font-size:54px;line-height:1;animation:v4bob 1.4s ease-in-out infinite;}
  @keyframes v4bob{0%,100%{transform:translateY(0) rotate(-6deg)}50%{transform:translateY(-6px) rotate(6deg)}}
  .v4h{font-size:28px;font-weight:800;color:var(--accent-text);margin-top:6px;}
  .v4m{font-size:19px;color:var(--ink);margin-top:4px;}
  .v4pills{display:flex;flex-wrap:wrap;gap:8px;justify-content:center;margin-top:12px;}
  .v4p{font-size:16px;font-weight:700;border-radius:999px;padding:6px 12px;}
  .v4p.g{background:var(--success-soft);color:var(--success);} .v4p.o{background:var(--gold-soft);color:var(--retry-text);}
  .v4p.r{background:var(--danger-soft);color:var(--danger);} .v4p.s{background:var(--rule);color:var(--ink);}
  .v4next{margin-top:14px;} .v4go{font-size:18px !important;padding:13px 20px !important;}
  .v4rec td.v4g{color:var(--success);font-weight:700;} .v4rec td.v4o{color:var(--retry-text);font-weight:700;} .v4rec td.v4r{color:var(--danger);font-weight:700;}
  .v4rec tr.v4tot td{font-weight:800;border-top:2px solid var(--rule);}
  .v4rec th{font-size:12.5px;padding:6px 3px !important;white-space:nowrap;} .v4rec td{font-size:15px;padding:7px 3px !important;text-align:center;}
  .v4rec td:first-child,.v4rec th:first-child{text-align:left;white-space:normal;min-width:92px;max-width:150px;font-size:14.5px;}
  @media(max-width:460px){ .v4left{display:none;} }
  .v4leg{font-size:14.5px;color:var(--ink-soft);margin:2px 0 8px;line-height:1.5;}
  body.v4done .fab-q,body.v4done #qFab{display:none;}
  .v4sum{font-size:16px;margin-top:10px;}
  /* v4 larger reading sizes */
  body{font-size:18px;}
  .chapter-title{font-size:38px !important;line-height:1.15;}
  .chapter-sub{font-size:17px !important;}
  .tab-btn{font-size:16.5px !important;}
  .sec-sub{font-size:16.5px !important;}
  .qtext{font-size:21px !important;line-height:1.6 !important;}
  .qnum{width:38px !important;height:38px !important;font-size:17px !important;}
  .opt{font-size:19.5px !important;padding:13px 15px !important;}
  .step-line{font-size:19.5px !important;line-height:2.1 !important;}
  .blank-input{font-size:18px !important;min-height:40px;}
  .sol-line{font-size:18px !important;line-height:1.6;}
  .feedback{font-size:16.5px !important;}
  .note h2{font-size:29px !important;}
  .note h3{font-size:22px !important;}
  .note h4{font-size:20px !important;}
  .note p,.note li,.note td,.note th{font-size:18.5px !important;line-height:1.7 !important;}
  .ex .exh{font-size:19px !important;} .ex .exl{font-size:18px !important;}
  .keybox{font-size:18px !important;}
  .hub-card p{font-size:17.5px !important;} .hub-btn{font-size:16.5px !important;}
  .review-q,.review-ans{font-size:17.5px !important;}
  .rec-table td{font-size:16px;}
  .vkb-k{font-size:19px !important;}
  .fq{font-size:0.95em;}
</style>
</head>
<body>
<header class="brand">
  <div class="brand-row">
    <div class="crest">BM</div>
    <div>
      <div class="brand-name">Brain &amp; Mind Academy</div>
      <div class="series-name">Sopaan <span style="font-weight:400;font-size:14px;color:#CFD7EA;">Practice Series</span></div>
    </div>
  </div>
  <div class="chapter-eyebrow">Algebra 1 · Chapter 7</div>
  <div class="chapter-title">Polynomial Equations and Factoring</div>
  <div class="chapter-sub">Theory Notes · Practice by Section · Learning Assessment</div><div class="chapter-credit">Follows the sections of Big Ideas Math Algebra 1, Chapter 7</div>
  <div class="chapter-progress">
    <div class="cp-track"><div class="cp-fill" id="cpFill"></div></div>
    <div class="cp-label" id="cpLabel">0% complete</div>
  </div>
  <div class="who-row"><button class="mode-pill" id="modePill" hidden>Choose a mode</button><span class="who" id="whoBar" hidden></span></div>
</header>

<nav class="tabbar"><div class="tabbar-inner" id="tabbar"></div></nav>
<div class="sec-sub" id="secSub"></div><div class="slide-progress"><div class="sp-track"><div class="sp-fill" id="spFill"></div></div><div class="sp-label" id="spLabel">Question 1 of 49</div></div>
<div class="wrap" id="wrap"></div>
<footer class="brandfoot">Brain &amp; Mind Academy · Sopaan Practice Series · Algebra 1 · Chapter 7<br>Lessons follow the chapter and section structure of <i>Big Ideas Math Algebra 1</i> (2015), Chapter 7. Theory notes, questions, learning assessments and worked solutions are written by Brain &amp; Mind Academy.</footer>

<div class="navbar"><div class="navbar-inner" id="navbarInner"></div></div>
<button class="fab" id="paletteFab"><span>Questions</span><span class="fab-badge" id="fabBadge">0/49</span></button>

<div class="overlay" id="overlay">
  <div class="palette" role="dialog" aria-label="Question palette">
    <div class="palette-head"><h2 id="paletteTitle">Question palette</h2><button class="palette-close" id="paletteClose">&times;</button></div>
    <div class="palette-legend">
      <span><i class="dot current"></i>Current</span><span><i class="dot correct"></i>Correct</span>
      <span><i class="dot revealed"></i>Revealed</span><span><i class="dot skipped"></i>Skipped</span>
      <span><i class="dot locked"></i>Locked</span>
    </div>
    <div class="chip-grid" id="paletteBody"></div>
  </div>
</div>
<div class="toast" id="toast"></div>

<script>
(function(){
"use strict";

/* ================= audio ================= */
var audioCtx=null;
function ensureAudio(){ if(!audioCtx){ try{ audioCtx=new (window.AudioContext||window.webkitAudioContext)(); }catch(e){} } return audioCtx; }
function playTone(freqs,dur,type){
  var ctx=ensureAudio(); if(!ctx) return;
  try{
    var t0=ctx.currentTime;
    freqs.forEach(function(f,i){
      var o=ctx.createOscillator(), g=ctx.createGain();
      o.type=type||'sine'; o.frequency.value=f;
      var start=t0+i*dur;
      g.gain.setValueAtTime(0.0001,start);
      g.gain.exponentialRampToValueAtTime(0.16,start+0.02);
      g.gain.exponentialRampToValueAtTime(0.0001,start+dur);
      o.connect(g); g.connect(ctx.destination);
      o.start(start); o.stop(start+dur+0.02);
    });
  }catch(e){}
}
function playSuccess(){ playTone([523.25,659.25,783.99],0.11,'sine'); }
function playWrong(){ playTone([220,185],0.14,'square'); }
function playReveal(){ playTone([300,220],0.16,'triangle'); }

/* ================= helpers ================= */
function norm(s){
  return String(s===undefined||s===null?'':s).trim().toLowerCase().replace(/\s+/g,'')
    .replace(/[×∗*·]/g,'x').replace(/÷/g,'/').replace(/–|—|−/g,'-')
    .replace(/[²]/g,'^2').replace(/[³]/g,'^3').replace(/[⁴]/g,'^4').replace(/[⁵]/g,'^5')
    .replace(/[⁶]/g,'^6').replace(/[⁷]/g,'^7').replace(/[⁸]/g,'^8').replace(/[⁹]/g,'^9')
    .replace(/\^/g,'');
}
function parseNum(s){
  if(s===undefined||s===null) return null;
  var t=String(s).trim().replace(/,/g,'').replace(/[−–—]/g,'-').replace(/\s+/g,''); if(t==='') return null;
  var neg=false; if(t[0]==='-'){neg=true;t=t.slice(1);}
  var m=t.match(/^(\d+)\/(\d+)$/);
  if(m){ var v=parseInt(m[1],10)/parseInt(m[2],10); return neg?-v:v; }
  if(/^\d+(\.\d+)?$/.test(t)){ var v2=parseFloat(t); return neg?-v2:v2; }
  return null;
}
/* ---- expression checker: compares answers like (P-2w)/2 and P/2-w at random values ---- */
function exprPrep(s){
  return String(s).toLowerCase().replace(/\s+/g,'').replace(/^[a-z]\(x\)=/i,'').replace(/^[a-z]=/i,'').replace(/[×∗·]/g,'*').replace(/÷/g,'/').replace(/[−–—]/g,'-')
    .replace(/²/g,'^2').replace(/³/g,'^3').replace(/⁴/g,'^4').replace(/⁵/g,'^5').replace(/⁶/g,'^6').replace(/⁷/g,'^7').replace(/⁸/g,'^8').replace(/⁹/g,'^9').replace(/π/g,'#').replace(/pi/gi,'#').replace(/½/g,'(1/2)');
}
function exprCompile(src){
  var s=exprPrep(src), i=0, toks=[], absDepth=0;
  while(i<s.length){
    var ch=s[i];
    if(/[0-9.]/.test(ch)){ var j=i; while(j<s.length && /[0-9.]/.test(s[j])) j++; toks.push({k:'n',v:parseFloat(s.slice(i,j))}); i=j; continue; }
    if(/[a-zA-Z#]/.test(ch)){ toks.push({k:'v',v:ch}); i++; continue; }
    if(ch==='|'){ var pv=toks[toks.length-1]; var opn=(absDepth===0)||!pv||('+-*/^(['.indexOf(pv.k)>=0); if(opn){ absDepth++; toks.push({k:'['}); } else { absDepth--; toks.push({k:']'}); } i++; continue; }
    if('+-*/^()'.indexOf(ch)>=0){ toks.push({k:ch}); i++; continue; }
    return null;
  }
  var out=[];
  for(var t=0;t<toks.length;t++){
    var a=toks[t], b=out[out.length-1];
    if(b && (b.k==='n'||b.k==='v'||b.k===')'||b.k===']') && (a.k==='n'||a.k==='v'||a.k==='('||a.k==='[')) out.push({k:'&'});
    out.push(a);
  }
  var p=0;
  function peek(){ return out[p]; }
  function parseE(){ var n=parseT(); while(peek() && (peek().k==='+'||peek().k==='-')){ var o=out[p++].k, r=parseT(); n=(function(l,r,o){return function(e){ return o==='+'?l(e)+r(e):l(e)-r(e); };})(n,r,o); } return n; }
  function parseI(){ var n=parseU(); while(peek() && peek().k==='&'){ p++; var r=parseP(); n=(function(l,r){return function(e){ return l(e)*r(e); };})(n,r); } return n; }
  function parseT(){ var n=parseI(); while(peek() && (peek().k==='*'||peek().k==='/')){ var o=out[p++].k, r=parseI(); n=(function(l,r,o){return function(e){ return o==='*'?l(e)*r(e):l(e)/r(e); };})(n,r,o); } return n; }
  function parseU(){ if(peek() && peek().k==='-'){ p++; var u=parseU(); return function(e){ return -u(e); }; } if(peek() && peek().k==='+'){ p++; return parseU(); } return parseP(); }
  function parseP(){ var b=parseA(); if(peek() && peek().k==='^'){ p++; var x=parseU(); return function(e){ return Math.pow(b(e),x(e)); }; } return b; }
  function parseA(){
    var t=out[p++]; if(!t) throw 0;
    if(t.k==='n') return function(){ return t.v; };
    if(t.k==='v') return t.v==='#' ? function(){ return Math.PI; } : function(e){ return e[t.v]; };
    if(t.k==='('){ var n=parseE(); if(!peek()||peek().k!==')') throw 0; p++; return n; }
    if(t.k==='['){ var m=parseE(); if(!peek()||peek().k!==']') throw 0; p++; return function(e){ return Math.abs(m(e)); }; }
    throw 0;
  }
  try{ var f=parseE(); if(p!==out.length) return null; return f; }catch(e){ return null; }
}
function exprEqual(input,answer){
  var f=exprCompile(input), g=exprCompile(answer); if(!f||!g) return false;
  var hits=0;
  for(var trial=0;trial<8;trial++){
    var env={}; 'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ'.split('').forEach(function(c){ env[c]=1.3+Math.random()*4.1; });
    var x=f(env), y=g(env);
    if(!isFinite(x)||!isFinite(y)) continue;
    if(Math.abs(x-y)>1e-7*Math.max(1,Math.abs(x),Math.abs(y))) return false;
    hits++;
  }
  return hits>=3;
}
function wordsNorm(s){ return String(s||'').toLowerCase().replace(/\band\b/g,' ').replace(/[^a-z]/g,''); }
function listNorm(s){ return (String(s||'').replace(/[−–—]/g,'-').replace(/(\d) (?=\d{3}\b)/g,'$1').match(/-?\d+(\.\d+)?/g)||[]).join(','); }
function powNorm(s){ return String(s||'').toLowerCase().replace(/\s+/g,'').replace(/[×∗*·.]/g,'x').replace(/[⁰¹²³⁴⁵⁶⁷⁸⁹]+/g,function(m){ return '^'+m.split('').map(function(c){ return '⁰¹²³⁴⁵⁶⁷⁸⁹'.indexOf(c); }).join(''); }).replace(/\^1(?!\d)/g,''); }
function fr(s){ return String(s).replace(/\{(\d+) (\d+)\/(\d+)\}/g,'<span class="mx">$1<span class="fq"><span>$2</span><span>$3</span></span></span>').replace(/\{(\d+)\/(\d+)\}/g,'<span class="fq"><span>$1</span><span>$2</span></span>'); }
function gcdI(a,b){ a=Math.abs(a); b=Math.abs(b); while(b){ var t=a%b; a=b; b=t; } return a; }
function fracParse(s){ s=String(s===undefined||s===null?'':s).trim().replace(/[\u2044\u2215\u00f7]/g,'/').replace(/\s+/g,' ').replace(/\s*\/\s*/g,'/'); var m;
  if((m=s.match(/^(-?\d+)$/))) return {v:+m[1],form:'int',n:+m[1],d:1};
  if((m=s.match(/^(-?\d+)\/(\d+)$/))){ if(+m[2]===0) return null; return {v:m[1]/m[2],form:'frac',n:+m[1],d:+m[2]}; }
  if((m=s.match(/^(-?)(\d+)(?: |\+)(\d+)\/(\d+)$/))){ if(+m[4]===0) return null; var sg=m[1]?-1:1; return {v:sg*(+m[2]+m[3]/m[4]),form:'mixed',w:sg*m[2],n:+m[3],d:+m[4]}; }
  if((m=s.match(/^-?\d*\.\d+$/))) return {v:parseFloat(s),form:'dec'};
  return null; }
function fracOK(mode,input,answer){
  if(mode==='flist'){ var A=String(input).split(/[,;]/).map(function(x){return x.trim();}).filter(Boolean), K=String(answer).split(/[,;]/).map(function(x){return x.trim();});
    if(A.length!==K.length) return false; return A.every(function(x,i){ var a=fracParse(x), k=fracParse(K[i]); return a&&k&&Math.abs(a.v-k.v)<1e-9; }); }
  var a=fracParse(input), k=fracParse(answer); if(!a||!k) return false;
  var same=Math.abs(a.v-k.v)<1e-9; if(!same) return false;
  if(mode==='fv') return true;
  if(mode==='dec') return a.form==='dec'||a.form==='int';
  if(mode==='fe') return (a.form==='frac'&&k.form==='frac'&&a.n===k.n&&a.d===k.d)||(a.form==='int'&&k.form==='int');
  if(mode==='fi') return a.form==='frac'||(a.form==='int'&&k.form==='int');
  if(mode==='fl') return a.form==='int'||(a.form==='frac'&&gcdI(a.n,a.d)===1)||(a.form==='mixed'&&a.n<a.d&&gcdI(a.n,a.d)===1);
  if(mode==='fm') return a.form==='int'||(a.form==='mixed'&&a.n>0&&a.n<a.d&&gcdI(a.n,a.d)===1);
  return false; }
function answerMatches(input,answer,accept,expr){
  if(expr==='dec'||expr==='fv'||expr==='fe'||expr==='fl'||expr==='fm'||expr==='fi'||expr==='flist'){ if(input===undefined||input===null||String(input).trim()==='') return false; return fracOK(expr,input,answer); }
  if(input===undefined||input===null||String(input).trim()==='') return false;
  if(expr==='words'){ return [answer].concat(accept||[]).some(function(a){ if(/\d/.test(a)) return norm(a)===norm(input); var w=wordsNorm(a); return w!=='' && w===wordsNorm(input); }); }
  if(expr==='list'){ return [answer].concat(accept||[]).some(function(a){ return listNorm(a)===listNorm(input); }); }
  if(expr==='pow'){ return [answer].concat(accept||[]).some(function(a){ return powNorm(a)===powNorm(input); }); }
  if(expr==='time'){ var tn=function(x){ var t=String(x).toLowerCase().replace(/[\s.]/g,'').replace(/[:h]/g,''); if(/^\d{3}(am|pm)?$/.test(t)) t='0'+t; return t; }; return [answer].concat(accept||[]).some(function(a){ return tn(a)===tn(input); }); }
  if(expr==='glist'){ var gn=function(x){ return String(x).toUpperCase().split(/[\s,;]+/).filter(Boolean).sort().join(','); }; return [answer].concat(accept||[]).some(function(a){ return gn(a)===gn(input); }); }
  if(expr==='coord'){ var cn=function(x){ return String(x).replace(/[\u2212\u2013\u2014]/g,'-').replace(/[\s()\[\]]/g,''); }; return [answer].concat(accept||[]).some(function(a){ return cn(a)===cn(input); }); }
  if(expr==='dlist'){ var dn=function(x){ return (String(x).replace(/[−–—]/g,'-').match(/-?\d*\.?\d+/g)||[]).map(Number).join(','); }; return [answer].concat(accept||[]).some(function(a){ return dn(a)===dn(input); }); }
  if(expr==='set'){ var sn=function(x){ return (String(x).match(/-?\d+/g)||[]).map(Number).sort(function(a,b){return a-b;}).join(','); }; return [answer].concat(accept||[]).some(function(a){ return sn(a)===sn(input); }); }
  if(expr==='primes'){ var pn=function(x){ var t=powNorm(x).replace(/[^0-9x^]/g,''); var out=[]; t.split('x').forEach(function(tok){ if(!tok) return; var m=tok.split('^'); var b=+m[0], e=m[1]?+m[1]:1; for(var i=0;i<e;i++) out.push(b); }); return out.sort(function(a,b){return a-b;}).join(','); }; return [answer].concat(accept||[]).some(function(a){ return pn(a)===pn(input); }); }
  if(expr==='angle'){ var an=function(x){ return String(x).toUpperCase().replace(/[^A-Z]/g,''); }; var k=an(answer), v=an(input); return v===k || v===k.split('').reverse().join(''); }
  if(expr==='trans'){ var tv=function(x){ var s=String(x).toLowerCase().replace(/[−–—]/g,'-').replace(/\b(units?|squares?|and|then|steps?|to|the|a)\b/g,' ').replace(/[,;.]/g,' '); var re=/(\d+)\s*(right|left|up|down|r|l|u|d)\b/g, m, dx=0, dy=0, n=0; while((m=re.exec(s))){ var v=+m[1], d=m[2][0]; if(d==='r')dx+=v; else if(d==='l')dx-=v; else if(d==='u')dy+=v; else dy-=v; n++; } if(!n||s.replace(re,'').replace(/\s+/g,'')!=='') return null; return dx+','+dy; }; var ti=tv(input); return ti!==null && [answer].concat(accept||[]).some(function(a){ return tv(a)===ti; }); }
  if(expr==='rot'){ var rv=function(x){ var s=String(x).toLowerCase().replace(/quarter[\s-]*turn/g,'90').replace(/half[\s-]*turn/g,'180').replace(/three[\s-]*quarter[\s-]*turn/g,'270'); var m=s.match(/\b(90|180|270)\b/); if(!m) return null; var a=+m[1]; if(a===180) return '180'; var dir=/anti|counter|acw|ccw/.test(s)?-1:(/clockwise|\bcw\b/.test(s)?1:0); if(!dir) return null; return String(((a*dir)%360+360)%360); }; var ri=rv(input); return ri!==null && ri===rv(answer); }
  if(expr==='expanded'){ var f=function(x){ return String(x).replace(/\s+/g,'').replace(/,/g,''); }; return [answer].concat(accept||[]).some(function(a){ return f(a)===f(input); }); }
  if(expr===true && input!==undefined && input!==null && String(input).trim()!==''){
    if(exprEqual(input,answer)) return true;
    var alt=String(input).replace(/\/\s*(\d+(?:\.\d+)?)\s*([a-zA-Z(])/g,'/$1*$2'); if(alt!==String(input) && exprEqual(alt,answer)) return true;
    return (accept||[]).some(function(a){ return exprEqual(input,a); });
  }
  if(input===undefined||input===null||String(input).trim()==='') return false;
  var n1=parseNum(input), n2=parseNum(answer);
  if(n1!==null && n2!==null){ if(Math.abs(n1-n2)<1e-3) return true; return (accept||[]).some(function(a){ var n3=parseNum(a); return n3!==null && Math.abs(n1-n3)<1e-3; }); }
  var cands=[answer].concat(accept||[]); var ni=norm(input);
  for(var i=0;i<cands.length;i++){ if(norm(cands[i])===ni) return true; }
  return false;
}
function esc(s){ return String(s).replace(/&/g,'&amp;').replace(/</g,'&lt;'); }

/* ================= DATA ================= */
var AR_OPTIONS = ["Both A and R are true, and R is the correct explanation of A","Both A and R are true, but R is NOT the correct explanation of A","A is true but R is false","A is false but R is true"];
var THEORY = "<div class=\"hub\"><div class=\"hub-card\"><h3>📖 Theory notes</h3><p>Explained notes for every section of the chapter, with key vocabulary, rules, area models, graphs and worked examples.</p><div class=\"hub-btns\"><button class=\"hub-btn\" data-jump=\"n71\">7.1 notes</button><button class=\"hub-btn\" data-jump=\"n72\">7.2 notes</button><button class=\"hub-btn\" data-jump=\"n73\">7.3 notes</button><button class=\"hub-btn\" data-jump=\"n74\">7.4 notes</button><button class=\"hub-btn\" data-jump=\"n75\">7.5 notes</button><button class=\"hub-btn\" data-jump=\"n76\">7.6 notes</button><button class=\"hub-btn\" data-jump=\"n77\">7.7 notes</button><button class=\"hub-btn\" data-jump=\"n78\">7.8 notes</button></div></div><div class=\"hub-card\"><h3>🎯 Practice by section</h3><p>One sheet for each section, mixing multiple-choice and fill-in-the-blank questions from easy to harder, with real-life problems and error analysis. Every question has a worked solution.</p><div class=\"hub-btns\"><button class=\"hub-btn\" data-go=\"s1\">7.1 · Adding and Subtracting Polynomials</button><button class=\"hub-btn\" data-go=\"s2\">7.2 · Multiplying Polynomials</button><button class=\"hub-btn\" data-go=\"s3\">7.3 · Special Products of Polynomials</button><button class=\"hub-btn\" data-go=\"s4\">7.4 · Solving Polynomial Equations in Factored Form</button><button class=\"hub-btn\" data-go=\"s5\">7.5 · Factoring x² + bx + c</button><button class=\"hub-btn\" data-go=\"s6\">7.6 · Factoring ax² + bx + c</button><button class=\"hub-btn\" data-go=\"s7\">7.7 · Factoring Special Products</button><button class=\"hub-btn\" data-go=\"s8\">7.8 · Factoring Polynomials Completely</button></div></div><div class=\"hub-card\"><h3>📝 Learning assessment</h3><p>Four short assessments, one per skill area, mixing questions from the whole chapter. Take them in Quiz mode and open the report to see your results as pie charts.</p><div class=\"hub-btns\"><button class=\"hub-btn\" data-go=\"s9\">A · Knowing and understanding</button><button class=\"hub-btn\" data-go=\"s10\">B · Investigating patterns</button><button class=\"hub-btn\" data-go=\"s11\">C · Communicating</button><button class=\"hub-btn\" data-go=\"s12\">D · Applying mathematics in real-life contexts</button><button class=\"hub-btn primary\" data-go=\"report\">📊 View my report</button></div></div></div><section class=\"note\" id=\"nintro\"><h2>About this chapter</h2><p>Polynomials are the expressions built from numbers and variables with whole-number exponents. In this chapter you will add, subtract and multiply them, learn the special patterns for squares and products, and then run the process backwards: <b>factoring</b>. Factoring turns a polynomial equation into a product equal to zero, which you can solve with the Zero-Product Property.</p><h4>Maintaining mathematical proficiency</h4><ul><li><b>Combining like terms:</b> like terms have the same variables with the same exponents: 5x<sup>2</sup> − 2x + 3x<sup>2</sup> = 8x<sup>2</sup> − 2x. The terms 5x<sup>2</sup> and −2x are <i>not</i> like terms.</li><li><b>Distributive Property:</b> a(b + c) = ab + ac, so −3(2y − 4) = −6y + 12. Watch the sign of every term.</li><li><b>Product of powers:</b> x<sup>m</sup> · x<sup>n</sup> = x<sup>m+n</sup>, so 4x<sup>2</sup> · 3x<sup>3</sup> = 12x<sup>5</sup>.</li><li><b>Greatest common factor (GCF):</b> the largest number that divides each number: GCF(18, 30) = 6.</li></ul><div class=\"ex\"><div class=\"exh\">Warm-up</div><div class=\"exl\">Simplify 7a − 4 − 2a + 9: (7a − 2a) + (−4 + 9) = <b>5a + 5</b>.<br>Simplify −2(5 − 3m): −10 + 6m = <b>6m − 10</b>.<br>Find GCF(24, 36): 24 = 2<sup>3</sup> · 3 and 36 = 2<sup>2</sup> · 3<sup>2</sup>, so the GCF is 2<sup>2</sup> · 3 = <b>12</b>.</div></div><div class=\"tscroll\"><table class=\"ttab\"><tr><th>Sheet</th><th>Section</th><th>Learning target</th></tr><tr><td>7.1</td><td>Adding and Subtracting Polynomials</td><td>I can classify polynomials by degree and number of terms, write them in standard form, and add and subtract them.</td></tr><tr><td>7.2</td><td>Multiplying Polynomials</td><td>I can multiply a monomial by a polynomial and multiply binomials and larger polynomials using the Distributive Property, FOIL and area models.</td></tr><tr><td>7.3</td><td>Special Products of Polynomials</td><td>I can use the square of a binomial pattern and the sum and difference pattern to multiply quickly.</td></tr><tr><td>7.4</td><td>Solving Polynomial Equations in Factored Form</td><td>I can use the Zero-Product Property and the greatest common monomial factor to solve polynomial equations.</td></tr><tr><td>7.5</td><td>Factoring x² + bx + c</td><td>I can factor trinomials whose leading coefficient is 1 and use factoring to solve equations.</td></tr><tr><td>7.6</td><td>Factoring ax² + bx + c</td><td>I can factor trinomials with a leading coefficient other than 1, including negative ones, and solve related equations.</td></tr><tr><td>7.7</td><td>Factoring Special Products</td><td>I can factor differences of two squares and perfect square trinomials.</td></tr><tr><td>7.8</td><td>Factoring Polynomials Completely</td><td>I can factor by grouping, factor polynomials completely and solve equations by factoring completely.</td></tr></table></div><div class=\"tscroll\"><table class=\"ttab\"><tr><th>Assessment</th><th>Skill area</th><th>What it checks</th></tr><tr><td>A</td><td>Knowing and understanding</td><td>Adding, multiplying and factoring polynomials and solving equations correctly.</td></tr><tr><td>B</td><td>Investigating patterns</td><td>Special-product patterns, number tricks, factor-pair tables and graphs.</td></tr><tr><td>C</td><td>Communicating</td><td>Vocabulary, explaining steps and spotting errors.</td></tr><tr><td>D</td><td>Applying mathematics in real-life contexts</td><td>Area, volume, profit and falling-object problems.</td></tr></table></div><p><b>Tools:</b> ⏱ at the top times each tab (pause or reset it). ✏️ opens a scratchpad for rough work. Some questions have a 📈 Desmos graph button. Tap the BM badge to go back to the home page.</p><p><b>Typing answers:</b> type powers with the &#94; key, for example <span class=\"mono\">3x&#94;2-5x+2</span>. Type fractions as <span class=\"mono\">-3/2</span> and lists of solutions with commas, such as <span class=\"mono\">-4, 3</span>. When a question shows the brackets of a factored form, type only the missing number in each box. When a question asks for the two numbers in (x + p)(x + q), type both, in any order, such as <span class=\"mono\">-6, 2</span>.</p></section><section class=\"note\" id=\"n71\"><h2>7.1 Adding and Subtracting Polynomials</h2><p class=\"lt\"><b>Learning target:</b> I can classify polynomials by degree and number of terms, write them in standard form, and add and subtract them.</p><p>A <b>monomial</b> is a number, a variable, or a product of a number and variables with whole-number exponents: 7, y, −3x<sup>2</sup>, 5ab<sup>3</sup>. The <b>degree of a monomial</b> is the sum of the exponents of its variables (5ab<sup>3</sup> has degree 1 + 3 = 4; a nonzero constant has degree 0).</p><p>A <b>polynomial</b> is a monomial or a sum of monomials; each monomial is a <b>term</b>. A polynomial with two terms is a <b>binomial</b>, with three terms a <b>trinomial</b>. The <b>degree of a polynomial</b> is the greatest degree of its terms.</p><div class=\"keybox\"><b>Standard form:</b> write the terms in order of decreasing degree. The first term is the <b>leading term</b> and its coefficient is the <b>leading coefficient</b>.<br>6 + 4x<sup>3</sup> − x<sup>2</sup> → <b>4x<sup>3</sup> − x<sup>2</sup> + 6</b>: degree 3 (cubic), leading coefficient 4, trinomial.</div><div class=\"tscroll\"><table class=\"ttab\"><tr><th>Degree</th><th>0</th><th>1</th><th>2</th><th>3</th><th>4</th></tr><tr><td>Name</td><td>constant</td><td>linear</td><td>quadratic</td><td>cubic</td><td>quartic</td></tr></table></div><p>Expressions such as 3x<sup>−1</sup> + 2, √x or {5/x} are <b>not</b> polynomials: the exponents must be whole numbers.</p><h4>Adding and subtracting</h4><p>To add, combine like terms (horizontally, or line them up vertically). To subtract, add the <b>opposite</b>: change the sign of <i>every</i> term of the polynomial being subtracted, then add.</p><div class=\"ex\"><div class=\"exh\">Example 1 · Add</div><div class=\"exl\">(5x<sup>2</sup> − 3x + 2) + (x<sup>2</sup> + 7x − 9)<br>= (5x<sup>2</sup> + x<sup>2</sup>) + (−3x + 7x) + (2 − 9) = <b>6x<sup>2</sup> + 4x − 7</b>.</div></div><div class=\"ex\"><div class=\"exh\">Example 2 · Subtract</div><div class=\"exl\">(4y<sup>3</sup> + 2y − 1) − (y<sup>3</sup> − 5y<sup>2</sup> + 2y + 6)<br>= 4y<sup>3</sup> + 2y − 1 − y<sup>3</sup> + 5y<sup>2</sup> − 2y − 6 = <b>3y<sup>3</sup> + 5y<sup>2</sup> − 7</b>.</div></div><div class=\"ex\"><div class=\"exh\">Example 3 · Real life</div><div class=\"exl\">A shop's revenue is R = 15x − 0.01x<sup>2</sup> and its cost is C = 4x + 200 dollars for x items.<br>Profit P = R − C = 15x − 0.01x<sup>2</sup> − 4x − 200 = <b>−0.01x<sup>2</sup> + 11x − 200</b>.</div></div><div class=\"keybox\"><b>Common mistake:</b> in (a − b) − (c − d) the minus sign applies to <b>both</b> c and −d: the result is a − b − c + d. Changing only the first sign is the most frequent error in this section.</div><div class=\"hub-btns\" style=\"margin-top:12px\"><button class=\"hub-btn primary\" data-go=\"s1\">Practise 7.1 →</button></div></section><section class=\"note\" id=\"n72\"><h2>7.2 Multiplying Polynomials</h2><p class=\"lt\"><b>Learning target:</b> I can multiply a monomial by a polynomial and multiply binomials and larger polynomials using the Distributive Property, FOIL and area models.</p><p>To multiply a monomial by a polynomial, use the <b>Distributive Property</b>: multiply every term. To multiply two polynomials, multiply <b>each term of the first by each term of the second</b>, then combine like terms.</p><div class=\"ex\"><div class=\"exh\">Example 1 · Monomial × polynomial</div><div class=\"exl\">−2x<sup>2</sup>(3x<sup>2</sup> − x + 4) = −6x<sup>4</sup> + 2x<sup>3</sup> − 8x<sup>2</sup>.</div></div><div class=\"keybox\"><b>FOIL</b> for two binomials: <b>F</b>irst, <b>O</b>uter, <b>I</b>nner, <b>L</b>ast.<br>(x + 3)(x − 7) = x · x + x · (−7) + 3 · x + 3 · (−7) = x<sup>2</sup> − 7x + 3x − 21 = <b>x<sup>2</sup> − 4x − 21</b>.</div><p>An <b>area model</b> organises the same products in a table. Each cell is the product of its row and column headings.</p><svg class=\"figsvg\" viewBox=\"0 0 300 146\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><text class=\"lb\" x=\"150.0\" y=\"11.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">(x + 3)(2x + 5)</text><text class=\"lb\" x=\"124.0\" y=\"38.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2x</text><text class=\"lb\" x=\"204.0\" y=\"38.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">+5</text><text class=\"lb\" x=\"74.0\" y=\"71.0\" text-anchor=\"end\" dominant-baseline=\"middle\">x</text><text class=\"lb\" x=\"74.0\" y=\"113.0\" text-anchor=\"end\" dominant-baseline=\"middle\">+3</text><rect x=\"84.0\" y=\"50.0\" width=\"80\" height=\"42\" style=\"fill:none;stroke:var(--ink-soft);stroke-width:1.4\"/><text class=\"lb\" x=\"124.0\" y=\"71.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2x²</text><rect x=\"164.0\" y=\"50.0\" width=\"80\" height=\"42\" style=\"fill:none;stroke:var(--ink-soft);stroke-width:1.4\"/><text class=\"lb\" x=\"204.0\" y=\"71.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">5x</text><rect x=\"84.0\" y=\"92.0\" width=\"80\" height=\"42\" style=\"fill:none;stroke:var(--ink-soft);stroke-width:1.4\"/><text class=\"lb\" x=\"124.0\" y=\"113.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">6x</text><rect x=\"164.0\" y=\"92.0\" width=\"80\" height=\"42\" style=\"fill:none;stroke:var(--ink-soft);stroke-width:1.4\"/><text class=\"lb\" x=\"204.0\" y=\"113.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">15</text></svg><div class=\"ex\"><div class=\"exh\">Example 2 · Area model</div><div class=\"exl\">(x + 3)(2x + 5): the cells are 2x<sup>2</sup>, 5x, 6x and 15.<br>Add them: 2x<sup>2</sup> + (5x + 6x) + 15 = <b>2x<sup>2</sup> + 11x + 15</b>.</div></div><div class=\"ex\"><div class=\"exh\">Example 3 · Binomial × trinomial</div><div class=\"exl\">(x − 2)(x<sup>2</sup> + 3x − 1) = x<sup>3</sup> + 3x<sup>2</sup> − x − 2x<sup>2</sup> − 6x + 2<br>= <b>x<sup>3</sup> + x<sup>2</sup> − 7x + 2</b>. (2 terms × 3 terms = 6 products before combining.)</div></div><div class=\"keybox\"><b>Common mistake:</b> (x + 4)(x + 5) is <b>not</b> x<sup>2</sup> + 20. The outer and inner products 5x and 4x give the middle term: x<sup>2</sup> + 9x + 20. The degree of a product is the <b>sum</b> of the degrees of the factors.</div><div class=\"hub-btns\" style=\"margin-top:12px\"><button class=\"hub-btn primary\" data-go=\"s2\">Practise 7.2 →</button></div></section><section class=\"note\" id=\"n73\"><h2>7.3 Special Products of Polynomials</h2><p class=\"lt\"><b>Learning target:</b> I can use the square of a binomial pattern and the sum and difference pattern to multiply quickly.</p><p>Some products appear so often that it pays to know their patterns.</p><div class=\"keybox\"><b>Square of a binomial</b><br>(a + b)<sup>2</sup> = a<sup>2</sup> + 2ab + b<sup>2</sup> &nbsp;·&nbsp; (a − b)<sup>2</sup> = a<sup>2</sup> − 2ab + b<sup>2</sup><br><b>Sum and difference</b><br>(a + b)(a − b) = a<sup>2</sup> − b<sup>2</sup></div><svg class=\"figsvg\" viewBox=\"0 0 300 146\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><text class=\"lb\" x=\"150.0\" y=\"11.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">(a + b)² = a² + 2ab + b²</text><text class=\"lb\" x=\"124.0\" y=\"38.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">a</text><text class=\"lb\" x=\"204.0\" y=\"38.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">+b</text><text class=\"lb\" x=\"74.0\" y=\"71.0\" text-anchor=\"end\" dominant-baseline=\"middle\">a</text><text class=\"lb\" x=\"74.0\" y=\"113.0\" text-anchor=\"end\" dominant-baseline=\"middle\">+b</text><rect x=\"84.0\" y=\"50.0\" width=\"80\" height=\"42\" style=\"fill:none;stroke:var(--ink-soft);stroke-width:1.4\"/><text class=\"lb\" x=\"124.0\" y=\"71.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">a²</text><rect x=\"164.0\" y=\"50.0\" width=\"80\" height=\"42\" style=\"fill:none;stroke:var(--ink-soft);stroke-width:1.4\"/><text class=\"lb\" x=\"204.0\" y=\"71.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">ab</text><rect x=\"84.0\" y=\"92.0\" width=\"80\" height=\"42\" style=\"fill:none;stroke:var(--ink-soft);stroke-width:1.4\"/><text class=\"lb\" x=\"124.0\" y=\"113.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">ab</text><rect x=\"164.0\" y=\"92.0\" width=\"80\" height=\"42\" style=\"fill:none;stroke:var(--ink-soft);stroke-width:1.4\"/><text class=\"lb\" x=\"204.0\" y=\"113.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">b²</text></svg><div class=\"ex\"><div class=\"exh\">Example 1 · Square of a binomial</div><div class=\"exl\">(x + 7)<sup>2</sup> = x<sup>2</sup> + 2(x)(7) + 7<sup>2</sup> = <b>x<sup>2</sup> + 14x + 49</b>.<br>(3y − 2)<sup>2</sup> = (3y)<sup>2</sup> − 2(3y)(2) + 2<sup>2</sup> = <b>9y<sup>2</sup> − 12y + 4</b>.</div></div><div class=\"ex\"><div class=\"exh\">Example 2 · Sum and difference</div><div class=\"exl\">(4m + 5)(4m − 5) = (4m)<sup>2</sup> − 5<sup>2</sup> = <b>16m<sup>2</sup> − 25</b>. The middle terms +20m and −20m cancel.</div></div><div class=\"ex\"><div class=\"exh\">Example 3 · Mental math</div><div class=\"exl\">38 · 42 = (40 − 2)(40 + 2) = 1600 − 4 = <b>1596</b>.<br>61<sup>2</sup> = (60 + 1)<sup>2</sup> = 3600 + 120 + 1 = <b>3721</b>.</div></div><p><b>Punnett squares:</b> if each parent passes gene B or b with probability 0.5, the offspring model is (0.5B + 0.5b)<sup>2</sup> = 0.25BB + 0.5Bb + 0.25bb: 25% BB, 50% Bb, 25% bb.</p><div class=\"keybox\"><b>Common mistake:</b> (x + 5)<sup>2</sup> ≠ x<sup>2</sup> + 25. Squaring a sum always produces the middle term 2ab: (x + 5)<sup>2</sup> = x<sup>2</sup> + 10x + 25.</div><div class=\"hub-btns\" style=\"margin-top:12px\"><button class=\"hub-btn primary\" data-go=\"s3\">Practise 7.3 →</button></div></section><section class=\"note\" id=\"n74\"><h2>7.4 Solving Polynomial Equations in Factored Form</h2><p class=\"lt\"><b>Learning target:</b> I can use the Zero-Product Property and the greatest common monomial factor to solve polynomial equations.</p><p>A polynomial is in <b>factored form</b> when it is written as a product of factors, such as (x + 2)(x − 3) or 4x(x − 5).</p><div class=\"keybox\"><b>Zero-Product Property:</b> if a · b = 0, then a = 0 <b>or</b> b = 0.</div><p>So to solve a factored equation equal to zero, set <b>each factor</b> equal to zero. The solutions are called <b>roots</b> of the equation; they are the x-intercepts (zeros) of the graph of y = the polynomial.</p><div class=\"ex\"><div class=\"exh\">Example 1 · Use the Zero-Product Property</div><div class=\"exl\">(x + 2)(x − 3) = 0 → x + 2 = 0 or x − 3 = 0 → <b>x = −2 or x = 3</b>.<br>(2n − 5)(n + 1) = 0 → 2n = 5 or n = −1 → <b>n = {5/2} or n = −1</b>.<br>(y − 4)<sup>2</sup> = 0 → y − 4 = 0 → <b>y = 4</b> (a <b>repeated root</b>).</div></div><svg class=\"figsvg\" viewBox=\"0 0 300 230\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><text class=\"lb\" x=\"150.0\" y=\"10.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">The zeros are −2 and 3</text><line x1=\"16.0\" y1=\"214.0\" x2=\"16.0\" y2=\"18.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"45.8\" y1=\"214.0\" x2=\"45.8\" y2=\"18.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"75.6\" y1=\"214.0\" x2=\"75.6\" y2=\"18.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"105.3\" y1=\"214.0\" x2=\"105.3\" y2=\"18.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"135.1\" y1=\"214.0\" x2=\"135.1\" y2=\"18.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"164.9\" y1=\"214.0\" x2=\"164.9\" y2=\"18.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"194.7\" y1=\"214.0\" x2=\"194.7\" y2=\"18.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"224.4\" y1=\"214.0\" x2=\"224.4\" y2=\"18.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"254.2\" y1=\"214.0\" x2=\"254.2\" y2=\"18.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"284.0\" y1=\"214.0\" x2=\"284.0\" y2=\"18.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"214.0\" x2=\"284.0\" y2=\"214.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"198.9\" x2=\"284.0\" y2=\"198.9\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"183.8\" x2=\"284.0\" y2=\"183.8\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"168.8\" x2=\"284.0\" y2=\"168.8\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"153.7\" x2=\"284.0\" y2=\"153.7\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"138.6\" x2=\"284.0\" y2=\"138.6\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"123.5\" x2=\"284.0\" y2=\"123.5\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"108.5\" x2=\"284.0\" y2=\"108.5\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"93.4\" x2=\"284.0\" y2=\"93.4\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"78.3\" x2=\"284.0\" y2=\"78.3\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"63.2\" x2=\"284.0\" y2=\"63.2\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"48.2\" x2=\"284.0\" y2=\"48.2\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"33.1\" x2=\"284.0\" y2=\"33.1\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"18.0\" x2=\"284.0\" y2=\"18.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"108.5\" x2=\"284.0\" y2=\"108.5\" style=\"stroke:var(--ink-soft);stroke-width:1.3\"/><line x1=\"135.1\" y1=\"214.0\" x2=\"135.1\" y2=\"18.0\" style=\"stroke:var(--ink-soft);stroke-width:1.3\"/><text class=\"po\" x=\"16.0\" y=\"117.5\" text-anchor=\"middle\" dominant-baseline=\"middle\">−4</text><text class=\"po\" x=\"75.6\" y=\"117.5\" text-anchor=\"middle\" dominant-baseline=\"middle\">−2</text><text class=\"po\" x=\"194.7\" y=\"117.5\" text-anchor=\"middle\" dominant-baseline=\"middle\">2</text><text class=\"po\" x=\"254.2\" y=\"117.5\" text-anchor=\"middle\" dominant-baseline=\"middle\">4</text><text class=\"po\" x=\"131.1\" y=\"214.0\" text-anchor=\"end\" dominant-baseline=\"middle\">−7</text><text class=\"po\" x=\"131.1\" y=\"183.8\" text-anchor=\"end\" dominant-baseline=\"middle\">−5</text><text class=\"po\" x=\"131.1\" y=\"153.7\" text-anchor=\"end\" dominant-baseline=\"middle\">−3</text><text class=\"po\" x=\"131.1\" y=\"123.5\" text-anchor=\"end\" dominant-baseline=\"middle\">−1</text><text class=\"po\" x=\"131.1\" y=\"93.4\" text-anchor=\"end\" dominant-baseline=\"middle\">1</text><text class=\"po\" x=\"131.1\" y=\"63.2\" text-anchor=\"end\" dominant-baseline=\"middle\">3</text><text class=\"po\" x=\"131.1\" y=\"33.1\" text-anchor=\"end\" dominant-baseline=\"middle\">5</text><text class=\"po\" x=\"280.0\" y=\"100.5\" text-anchor=\"end\" dominant-baseline=\"middle\">x</text><text class=\"po\" x=\"143.1\" y=\"24.0\" text-anchor=\"start\" dominant-baseline=\"middle\">y</text><clipPath id=\"c8841\"><rect x=\"16.0\" y=\"18.0\" width=\"268.0\" height=\"196.0\"/></clipPath><path d=\"M16.0,-102.6 L16.7,-99.6 L17.3,-96.5 L18.0,-93.5 L18.7,-90.5 L19.3,-87.5 L20.0,-84.6 L20.7,-81.6 L21.4,-78.7 L22.0,-75.8 L22.7,-72.8 L23.4,-70.0 L24.0,-67.1 L24.7,-64.2 L25.4,-61.4 L26.0,-58.5 L26.7,-55.7 L27.4,-52.9 L28.1,-50.1 L28.7,-47.4 L29.4,-44.6 L30.1,-41.9 L30.7,-39.1 L31.4,-36.4 L32.1,-33.7 L32.8,-31.1 L33.4,-28.4 L34.1,-25.7 L34.8,-23.1 L35.4,-20.5 L36.1,-17.9 L36.8,-15.3 L37.4,-12.7 L38.1,-10.2 L38.8,-7.6 L39.5,-5.1 L40.1,-2.6 L40.8,-0.1 L41.5,2.4 L42.1,4.8 L42.8,7.3 L43.5,9.7 L44.1,12.1 L44.8,14.6 L45.5,16.9 L46.2,19.3 L46.8,21.7 L47.5,24.0 L48.2,26.3 L48.8,28.7 L49.5,31.0 L50.2,33.2 L50.8,35.5 L51.5,37.8 L52.2,40.0 L52.8,42.2 L53.5,44.4 L54.2,46.6 L54.9,48.8 L55.5,50.9 L56.2,53.1 L56.9,55.2 L57.5,57.3 L58.2,59.4 L58.9,61.5 L59.5,63.6 L60.2,65.6 L60.9,67.7 L61.6,69.7 L62.2,71.7 L62.9,73.7 L63.6,75.7 L64.2,77.6 L64.9,79.6 L65.6,81.5 L66.2,83.4 L66.9,85.3 L67.6,87.2 L68.3,89.1 L68.9,90.9 L69.6,92.8 L70.3,94.6 L70.9,96.4 L71.6,98.2 L72.3,100.0 L73.0,101.7 L73.6,103.5 L74.3,105.2 L75.0,106.9 L75.6,108.6 L76.3,110.3 L77.0,112.0 L77.6,113.7 L78.3,115.3 L79.0,116.9 L79.7,118.5 L80.3,120.1 L81.0,121.7 L81.7,123.3 L82.3,124.8 L83.0,126.4 L83.7,127.9 L84.3,129.4 L85.0,130.9 L85.7,132.3 L86.3,133.8 L87.0,135.2 L87.7,136.7 L88.4,138.1 L89.0,139.5 L89.7,140.9 L90.4,142.2 L91.0,143.6 L91.7,144.9 L92.4,146.2 L93.0,147.5 L93.7,148.8 L94.4,150.1 L95.1,151.4 L95.7,152.6 L96.4,153.8 L97.1,155.1 L97.7,156.3 L98.4,157.4 L99.1,158.6 L99.8,159.8 L100.4,160.9 L101.1,162.0 L101.8,163.1 L102.4,164.2 L103.1,165.3 L103.8,166.4 L104.4,167.4 L105.1,168.4 L105.8,169.4 L106.5,170.4 L107.1,171.4 L107.8,172.4 L108.5,173.4 L109.1,174.3 L109.8,175.2 L110.5,176.1 L111.1,177.0 L111.8,177.9 L112.5,178.8 L113.2,179.6 L113.8,180.4 L114.5,181.3 L115.2,182.1 L115.8,182.8 L116.5,183.6 L117.2,184.4 L117.8,185.1 L118.5,185.8 L119.2,186.5 L119.8,187.2 L120.5,187.9 L121.2,188.6 L121.9,189.2 L122.5,189.9 L123.2,190.5 L123.9,191.1 L124.5,191.7 L125.2,192.2 L125.9,192.8 L126.5,193.3 L127.2,193.9 L127.9,194.4 L128.6,194.9 L129.2,195.4 L129.9,195.8 L130.6,196.3 L131.2,196.7 L131.9,197.1 L132.6,197.5 L133.2,197.9 L133.9,198.3 L134.6,198.7 L135.3,199.0 L135.9,199.3 L136.6,199.6 L137.3,199.9 L137.9,200.2 L138.6,200.5 L139.3,200.7 L139.9,201.0 L140.6,201.2 L141.3,201.4 L142.0,201.6 L142.6,201.8 L143.3,201.9 L144.0,202.1 L144.6,202.2 L145.3,202.3 L146.0,202.4 L146.7,202.5 L147.3,202.6 L148.0,202.6 L148.7,202.7 L149.3,202.7 L150.0,202.7 L150.7,202.7 L151.3,202.7 L152.0,202.6 L152.7,202.6 L153.3,202.5 L154.0,202.4 L154.7,202.3 L155.4,202.2 L156.0,202.1 L156.7,201.9 L157.4,201.8 L158.0,201.6 L158.7,201.4 L159.4,201.2 L160.1,201.0 L160.7,200.7 L161.4,200.5 L162.1,200.2 L162.7,199.9 L163.4,199.6 L164.1,199.3 L164.7,199.0 L165.4,198.7 L166.1,198.3 L166.8,197.9 L167.4,197.5 L168.1,197.1 L168.8,196.7 L169.4,196.3 L170.1,195.8 L170.8,195.4 L171.4,194.9 L172.1,194.4 L172.8,193.9 L173.4,193.3 L174.1,192.8 L174.8,192.2 L175.5,191.7 L176.1,191.1 L176.8,190.5 L177.5,189.9 L178.1,189.2 L178.8,188.6 L179.5,187.9 L180.2,187.2 L180.8,186.5 L181.5,185.8 L182.2,185.1 L182.8,184.4 L183.5,183.6 L184.2,182.8 L184.8,182.1 L185.5,181.3 L186.2,180.4 L186.8,179.6 L187.5,178.8 L188.2,177.9 L188.9,177.0 L189.5,176.1 L190.2,175.2 L190.9,174.3 L191.5,173.4 L192.2,172.4 L192.9,171.4 L193.6,170.4 L194.2,169.4 L194.9,168.4 L195.6,167.4 L196.2,166.4 L196.9,165.3 L197.6,164.2 L198.2,163.1 L198.9,162.0 L199.6,160.9 L200.2,159.8 L200.9,158.6 L201.6,157.4 L202.3,156.3 L202.9,155.1 L203.6,153.8 L204.3,152.6 L204.9,151.4 L205.6,150.1 L206.3,148.8 L206.9,147.5 L207.6,146.2 L208.3,144.9 L209.0,143.6 L209.6,142.2 L210.3,140.9 L211.0,139.5 L211.6,138.1 L212.3,136.7 L213.0,135.2 L213.7,133.8 L214.3,132.3 L215.0,130.9 L215.7,129.4 L216.3,127.9 L217.0,126.4 L217.7,124.8 L218.3,123.3 L219.0,121.7 L219.7,120.1 L220.3,118.5 L221.0,116.9 L221.7,115.3 L222.4,113.7 L223.0,112.0 L223.7,110.3 L224.4,108.6 L225.0,106.9 L225.7,105.2 L226.4,103.5 L227.1,101.7 L227.7,100.0 L228.4,98.2 L229.1,96.4 L229.7,94.6 L230.4,92.8 L231.1,90.9 L231.7,89.1 L232.4,87.2 L233.1,85.3 L233.8,83.4 L234.4,81.5 L235.1,79.6 L235.8,77.6 L236.4,75.7 L237.1,73.7 L237.8,71.7 L238.4,69.7 L239.1,67.7 L239.8,65.6 L240.4,63.6 L241.1,61.5 L241.8,59.4 L242.5,57.3 L243.1,55.2 L243.8,53.1 L244.5,50.9 L245.1,48.8 L245.8,46.6 L246.5,44.4 L247.2,42.2 L247.8,40.0 L248.5,37.8 L249.2,35.5 L249.8,33.2 L250.5,31.0 L251.2,28.7 L251.8,26.3 L252.5,24.0 L253.2,21.7 L253.8,19.3 L254.5,16.9 L255.2,14.6 L255.9,12.1 L256.5,9.7 L257.2,7.3 L257.9,4.8 L258.5,2.4 L259.2,-0.1 L259.9,-2.6 L260.6,-5.1 L261.2,-7.6 L261.9,-10.2 L262.6,-12.7 L263.2,-15.3 L263.9,-17.9 L264.6,-20.5 L265.2,-23.1 L265.9,-25.7 L266.6,-28.4 L267.2,-31.1 L267.9,-33.7 L268.6,-36.4 L269.3,-39.1 L269.9,-41.9 L270.6,-44.6 L271.3,-47.4 L271.9,-50.1 L272.6,-52.9 L273.3,-55.7 L273.9,-58.5 L274.6,-61.4 L275.3,-64.2 L276.0,-67.1 L276.6,-70.0 L277.3,-72.8 L278.0,-75.8 L278.6,-78.7 L279.3,-81.6 L280.0,-84.6 L280.6,-87.5 L281.3,-90.5 L282.0,-93.5 L282.7,-96.5 L283.3,-99.6 L284.0,-102.6\" clip-path=\"url(#c8841)\" style=\"fill:none;stroke:var(--danger);stroke-width:2.2\"/><text x=\"251.2\" y=\"21.4\" text-anchor=\"middle\" style=\"fill:var(--danger);font:700 12px 'Source Sans 3',sans-serif;paint-order:stroke;stroke:var(--card);stroke-width:4px;stroke-linejoin:round\">y = (x + 2)(x − 3)</text><circle cx=\"75.6\" cy=\"108.5\" r=\"3.2\" style=\"fill:var(--accent-text)\"/><circle cx=\"224.4\" cy=\"108.5\" r=\"3.2\" style=\"fill:var(--accent-text)\"/></svg><h4>Greatest common monomial factor</h4><p>The GCF of the terms of a polynomial is the greatest monomial that divides each term. Factoring it out is the first step of all factoring.</p><div class=\"ex\"><div class=\"exh\">Example 2 · Factor out the GCF, then solve</div><div class=\"exl\">6x<sup>2</sup> + 15x: GCF(6, 15) = 3 and the lowest power of x is x<sup>1</sup>, so the GCF is 3x: 6x<sup>2</sup> + 15x = <b>3x(2x + 5)</b>.<br>Solve 6x<sup>2</sup> + 15x = 0: 3x = 0 or 2x + 5 = 0, so <b>x = 0 or x = −{5/2}</b>.</div></div><div class=\"ex\"><div class=\"exh\">Example 3 · Rewrite first</div><div class=\"exl\">4t<sup>2</sup> = 12t → 4t<sup>2</sup> − 12t = 0 → 4t(t − 3) = 0 → <b>t = 0 or t = 3</b>.</div></div><div class=\"keybox\"><b>Common mistakes:</b> the product must equal <b>zero</b>: (x − 1)(x + 2) = 4 does not give x − 1 = 4. And never divide both sides by the variable (4t<sup>2</sup> = 12t → t = 3): you lose the solution t = 0.</div><div class=\"hub-btns\" style=\"margin-top:12px\"><button class=\"hub-btn primary\" data-go=\"s4\">Practise 7.4 →</button></div></section><section class=\"note\" id=\"n75\"><h2>7.5 Factoring x² + bx + c</h2><p class=\"lt\"><b>Learning target:</b> I can factor trinomials whose leading coefficient is 1 and use factoring to solve equations.</p><p>Factoring reverses multiplication. Since (x + p)(x + q) = x<sup>2</sup> + (p + q)x + pq, to factor x<sup>2</sup> + bx + c you look for two integers p and q with</p><div class=\"keybox\"><b>p · q = c</b> &nbsp;and&nbsp; <b>p + q = b</b>. Then x<sup>2</sup> + bx + c = (x + p)(x + q).</div><div class=\"tscroll\"><table class=\"ttab\"><tr><th>c</th><th>b</th><th>Signs of p and q</th><th>Example</th></tr><tr><td>positive</td><td>positive</td><td>both positive</td><td>x<sup>2</sup> + 7x + 10 = (x + 2)(x + 5)</td></tr><tr><td>positive</td><td>negative</td><td>both negative</td><td>x<sup>2</sup> − 9x + 14 = (x − 2)(x − 7)</td></tr><tr><td>negative</td><td>either</td><td>opposite signs</td><td>x<sup>2</sup> + 4x − 12 = (x + 6)(x − 2)</td></tr></table></div><svg class=\"figsvg\" viewBox=\"0 0 300 146\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><text class=\"lb\" x=\"150.0\" y=\"11.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">x² + 5x + 6 = (x + 2)(x + 3)</text><text class=\"lb\" x=\"124.0\" y=\"38.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">x</text><text class=\"lb\" x=\"204.0\" y=\"38.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">+3</text><text class=\"lb\" x=\"74.0\" y=\"71.0\" text-anchor=\"end\" dominant-baseline=\"middle\">x</text><text class=\"lb\" x=\"74.0\" y=\"113.0\" text-anchor=\"end\" dominant-baseline=\"middle\">+2</text><rect x=\"84.0\" y=\"50.0\" width=\"80\" height=\"42\" style=\"fill:none;stroke:var(--ink-soft);stroke-width:1.4\"/><text class=\"lb\" x=\"124.0\" y=\"71.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">x²</text><rect x=\"164.0\" y=\"50.0\" width=\"80\" height=\"42\" style=\"fill:none;stroke:var(--ink-soft);stroke-width:1.4\"/><text class=\"lb\" x=\"204.0\" y=\"71.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">3x</text><rect x=\"84.0\" y=\"92.0\" width=\"80\" height=\"42\" style=\"fill:none;stroke:var(--ink-soft);stroke-width:1.4\"/><text class=\"lb\" x=\"124.0\" y=\"113.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2x</text><rect x=\"164.0\" y=\"92.0\" width=\"80\" height=\"42\" style=\"fill:none;stroke:var(--ink-soft);stroke-width:1.4\"/><text class=\"lb\" x=\"204.0\" y=\"113.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">6</text></svg><div class=\"ex\"><div class=\"exh\">Example 1 · List factor pairs</div><div class=\"exl\">Factor x<sup>2</sup> − 3x − 18. Pairs with product −18: (1, −18), (−1, 18), (2, −9), (−2, 9), (3, −6), (−3, 6).<br>Sums: −17, 17, −7, 7, <b>−3</b>, 3. So p = 3, q = −6: <b>(x + 3)(x − 6)</b>.<br>Check: x<sup>2</sup> − 6x + 3x − 18 = x<sup>2</sup> − 3x − 18 ✓</div></div><div class=\"ex\"><div class=\"exh\">Example 2 · Solve by factoring</div><div class=\"exl\">x<sup>2</sup> + 2x = 15 → x<sup>2</sup> + 2x − 15 = 0 → (x + 5)(x − 3) = 0 → <b>x = −5 or x = 3</b>.</div></div><div class=\"ex\"><div class=\"exh\">Example 3 · Real life</div><div class=\"exl\">A rectangle has area 60 cm<sup>2</sup> and its length is 4 cm more than its width w: w(w + 4) = 60.<br>w<sup>2</sup> + 4w − 60 = 0 → (w + 10)(w − 6) = 0 → w = 6 (a width cannot be −10). The rectangle is <b>6 cm by 10 cm</b>.</div></div><div class=\"keybox\"><b>Common mistake:</b> getting the signs swapped. (x − 5)(x + 3) = x<sup>2</sup> − 2x − 15 but (x + 5)(x − 3) = x<sup>2</sup> + 2x − 15. Always multiply back to check the middle term.</div><div class=\"hub-btns\" style=\"margin-top:12px\"><button class=\"hub-btn primary\" data-go=\"s5\">Practise 7.5 →</button></div></section><section class=\"note\" id=\"n76\"><h2>7.6 Factoring ax² + bx + c</h2><p class=\"lt\"><b>Learning target:</b> I can factor trinomials with a leading coefficient other than 1, including negative ones, and solve related equations.</p><p><b>Step 1:</b> factor out any GCF: 4x<sup>2</sup> + 10x + 6 = 2(2x<sup>2</sup> + 5x + 3). If a is negative, factor out −1 so the leading coefficient becomes positive.</p><div class=\"keybox\"><b>The ac method (factoring by grouping)</b><br>1. Find two integers whose product is <b>ac</b> and whose sum is <b>b</b>.<br>2. Use them to split the middle term.<br>3. Group in pairs and factor out the common binomial.</div><div class=\"ex\"><div class=\"exh\">Example 1 · ac method</div><div class=\"exl\">Factor 3x<sup>2</sup> + 11x + 6. ac = 3 · 6 = 18; pairs of 18 with sum 11: <b>2 and 9</b>.<br>3x<sup>2</sup> + 9x + 2x + 6 = 3x(x + 3) + 2(x + 3) = <b>(3x + 2)(x + 3)</b>.</div></div><div class=\"ex\"><div class=\"exh\">Example 2 · Guess and check with negative c</div><div class=\"exl\">Factor 2x<sup>2</sup> − 5x − 3: try (2x + ?)(x + ?) with factors of −3.<br>(2x + 1)(x − 3) = 2x<sup>2</sup> − 6x + x − 3 = 2x<sup>2</sup> − 5x − 3 ✓ So <b>(2x + 1)(x − 3)</b>.</div></div><div class=\"ex\"><div class=\"exh\">Example 3 · Negative leading coefficient</div><div class=\"exl\">−3x<sup>2</sup> + 7x − 2 = −(3x<sup>2</sup> − 7x + 2). ac = 6, pair −1 and −6.<br>3x<sup>2</sup> − 6x − x + 2 = 3x(x − 2) − (x − 2) = (3x − 1)(x − 2), so the answer is <b>−(3x − 1)(x − 2)</b>.</div></div><div class=\"ex\"><div class=\"exh\">Example 4 · Solve</div><div class=\"exl\">6x<sup>2</sup> + x − 2 = 0 → (2x − 1)(3x + 2) = 0 → <b>x = {1/2} or x = −{2/3}</b>.</div></div><div class=\"keybox\"><b>Common mistake:</b> in (2x + 5)(x + 1) the 5 is multiplied by x but the 1 is multiplied by 2x, so the order of the numbers matters: (2x + 5)(x + 1) = 2x<sup>2</sup> + 7x + 5, while (2x + 1)(x + 5) = 2x<sup>2</sup> + 11x + 5.</div><div class=\"hub-btns\" style=\"margin-top:12px\"><button class=\"hub-btn primary\" data-go=\"s6\">Practise 7.6 →</button></div></section><section class=\"note\" id=\"n77\"><h2>7.7 Factoring Special Products</h2><p class=\"lt\"><b>Learning target:</b> I can factor differences of two squares and perfect square trinomials.</p><p>Read the special product patterns from right to left.</p><div class=\"keybox\"><b>Difference of two squares:</b> a<sup>2</sup> − b<sup>2</sup> = (a + b)(a − b)<br><b>Perfect square trinomials:</b> a<sup>2</sup> + 2ab + b<sup>2</sup> = (a + b)<sup>2</sup> &nbsp;·&nbsp; a<sup>2</sup> − 2ab + b<sup>2</sup> = (a − b)<sup>2</sup></div><p>To recognise a perfect square trinomial, check that the first and last terms are squares and that the middle term is <b>twice</b> the product of their square roots.</p><div class=\"ex\"><div class=\"exh\">Example 1 · Difference of two squares</div><div class=\"exl\">x<sup>2</sup> − 64 = x<sup>2</sup> − 8<sup>2</sup> = <b>(x + 8)(x − 8)</b>.<br>25y<sup>2</sup> − 9 = (5y)<sup>2</sup> − 3<sup>2</sup> = <b>(5y + 3)(5y − 3)</b>.<br>Mental math: 47<sup>2</sup> − 43<sup>2</sup> = (47 + 43)(47 − 43) = 90 · 4 = <b>360</b>.</div></div><div class=\"ex\"><div class=\"exh\">Example 2 · Perfect square trinomial</div><div class=\"exl\">x<sup>2</sup> − 16x + 64: 64 = 8<sup>2</sup> and 2 · x · 8 = 16x, so it is <b>(x − 8)<sup>2</sup></b>.<br>9m<sup>2</sup> + 30m + 25 = (3m)<sup>2</sup> + 2(3m)(5) + 5<sup>2</sup> = <b>(3m + 5)<sup>2</sup></b>.</div></div><div class=\"ex\"><div class=\"exh\">Example 3 · Solve</div><div class=\"exl\">4x<sup>2</sup> − 12x + 9 = 0 → (2x − 3)<sup>2</sup> = 0 → <b>x = {3/2}</b> (repeated root).</div></div><div class=\"keybox\"><b>Common mistake:</b> a <b>sum</b> of two squares such as x<sup>2</sup> + 25 does <b>not</b> factor over the integers: (x + 5)(x − 5) = x<sup>2</sup> − 25 and (x + 5)<sup>2</sup> = x<sup>2</sup> + 10x + 25.</div><div class=\"hub-btns\" style=\"margin-top:12px\"><button class=\"hub-btn primary\" data-go=\"s7\">Practise 7.7 →</button></div></section><section class=\"note\" id=\"n78\"><h2>7.8 Factoring Polynomials Completely</h2><p class=\"lt\"><b>Learning target:</b> I can factor by grouping, factor polynomials completely and solve equations by factoring completely.</p><p>A polynomial is <b>factored completely</b> when it is written as a product of <b>unfactorable</b> polynomials with integer coefficients (and possibly a monomial). A polynomial that cannot be factored at all, such as x<sup>2</sup> + 4 or x<sup>2</sup> + x + 1, is called <b>prime</b>.</p><h4>Factoring by grouping</h4><p>For four terms, group them in pairs, factor each pair, and look for a common binomial factor.</p><div class=\"ex\"><div class=\"exh\">Example 1 · Grouping</div><div class=\"exl\">x<sup>3</sup> + 5x<sup>2</sup> + 2x + 10 = x<sup>2</sup>(x + 5) + 2(x + 5) = <b>(x + 5)(x<sup>2</sup> + 2)</b>.</div></div><div class=\"keybox\"><b>Checklist for factoring completely</b><br>1. Factor out the GCF.<br>2. Two terms: is it a difference of two squares?<br>3. Three terms: a perfect square trinomial? Otherwise x<sup>2</sup> + bx + c or ax<sup>2</sup> + bx + c.<br>4. Four terms: try grouping.<br>5. Check every factor again: can any factor be factored further?</div><div class=\"ex\"><div class=\"exh\">Example 2 · GCF, then a trinomial</div><div class=\"exl\">3x<sup>3</sup> − 6x<sup>2</sup> − 24x = 3x(x<sup>2</sup> − 2x − 8) = <b>3x(x − 4)(x + 2)</b>.</div></div><div class=\"ex\"><div class=\"exh\">Example 3 · Solve by factoring completely</div><div class=\"exl\">x<sup>3</sup> − x<sup>2</sup> − 4x + 4 = 0 → x<sup>2</sup>(x − 1) − 4(x − 1) = (x − 1)(x<sup>2</sup> − 4) = (x − 1)(x + 2)(x − 2) = 0.<br>So <b>x = 1, x = −2 or x = 2</b>: the three x-intercepts of the graph.</div></div><svg class=\"figsvg\" viewBox=\"0 0 300 230\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><text class=\"lb\" x=\"150.0\" y=\"10.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">y = x³ − x² − 4x + 4 = (x − 1)(x + 2)(x − 2)</text><line x1=\"16.0\" y1=\"214.0\" x2=\"16.0\" y2=\"18.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"49.5\" y1=\"214.0\" x2=\"49.5\" y2=\"18.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"83.0\" y1=\"214.0\" x2=\"83.0\" y2=\"18.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"116.5\" y1=\"214.0\" x2=\"116.5\" y2=\"18.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"150.0\" y1=\"214.0\" x2=\"150.0\" y2=\"18.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"183.5\" y1=\"214.0\" x2=\"183.5\" y2=\"18.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"217.0\" y1=\"214.0\" x2=\"217.0\" y2=\"18.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"250.5\" y1=\"214.0\" x2=\"250.5\" y2=\"18.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"284.0\" y1=\"214.0\" x2=\"284.0\" y2=\"18.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"214.0\" x2=\"284.0\" y2=\"214.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"200.0\" x2=\"284.0\" y2=\"200.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"186.0\" x2=\"284.0\" y2=\"186.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"172.0\" x2=\"284.0\" y2=\"172.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"158.0\" x2=\"284.0\" y2=\"158.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"144.0\" x2=\"284.0\" y2=\"144.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"130.0\" x2=\"284.0\" y2=\"130.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"116.0\" x2=\"284.0\" y2=\"116.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"102.0\" x2=\"284.0\" y2=\"102.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"88.0\" x2=\"284.0\" y2=\"88.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"74.0\" x2=\"284.0\" y2=\"74.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"60.0\" x2=\"284.0\" y2=\"60.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"46.0\" x2=\"284.0\" y2=\"46.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"32.0\" x2=\"284.0\" y2=\"32.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"18.0\" x2=\"284.0\" y2=\"18.0\" style=\"stroke:var(--rule);stroke-width:.8\"/><line x1=\"16.0\" y1=\"130.0\" x2=\"284.0\" y2=\"130.0\" style=\"stroke:var(--ink-soft);stroke-width:1.3\"/><line x1=\"150.0\" y1=\"214.0\" x2=\"150.0\" y2=\"18.0\" style=\"stroke:var(--ink-soft);stroke-width:1.3\"/><text class=\"po\" x=\"16.0\" y=\"139.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−4</text><text class=\"po\" x=\"83.0\" y=\"139.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−2</text><text class=\"po\" x=\"217.0\" y=\"139.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2</text><text class=\"po\" x=\"284.0\" y=\"139.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">4</text><text class=\"po\" x=\"146.0\" y=\"214.0\" text-anchor=\"end\" dominant-baseline=\"middle\">−6</text><text class=\"po\" x=\"146.0\" y=\"186.0\" text-anchor=\"end\" dominant-baseline=\"middle\">−4</text><text class=\"po\" x=\"146.0\" y=\"158.0\" text-anchor=\"end\" dominant-baseline=\"middle\">−2</text><text class=\"po\" x=\"146.0\" y=\"102.0\" text-anchor=\"end\" dominant-baseline=\"middle\">2</text><text class=\"po\" x=\"146.0\" y=\"74.0\" text-anchor=\"end\" dominant-baseline=\"middle\">4</text><text class=\"po\" x=\"146.0\" y=\"46.0\" text-anchor=\"end\" dominant-baseline=\"middle\">6</text><text class=\"po\" x=\"146.0\" y=\"18.0\" text-anchor=\"end\" dominant-baseline=\"middle\">8</text><text class=\"po\" x=\"280.0\" y=\"122.0\" text-anchor=\"end\" dominant-baseline=\"middle\">x</text><text class=\"po\" x=\"158.0\" y=\"24.0\" text-anchor=\"start\" dominant-baseline=\"middle\">y</text><clipPath id=\"c5960\"><rect x=\"16.0\" y=\"18.0\" width=\"268.0\" height=\"196.0\"/></clipPath><path d=\"M16.0,970.0 L16.7,955.5 L17.3,941.2 L18.0,927.0 L18.7,912.9 L19.4,899.0 L20.0,885.2 L20.7,871.6 L21.4,858.1 L22.0,844.8 L22.7,831.6 L23.4,818.5 L24.0,805.6 L24.7,792.8 L25.4,780.1 L26.0,767.6 L26.7,755.2 L27.4,743.0 L28.1,730.9 L28.7,718.9 L29.4,707.0 L30.1,695.3 L30.7,683.7 L31.4,672.3 L32.1,660.9 L32.8,649.8 L33.4,638.7 L34.1,627.7 L34.8,616.9 L35.4,606.3 L36.1,595.7 L36.8,585.3 L37.4,575.0 L38.1,564.8 L38.8,554.7 L39.5,544.8 L40.1,535.0 L40.8,525.3 L41.5,515.7 L42.1,506.2 L42.8,496.9 L43.5,487.7 L44.1,478.6 L44.8,469.6 L45.5,460.8 L46.1,452.0 L46.8,443.4 L47.5,434.9 L48.2,426.5 L48.8,418.2 L49.5,410.0 L50.2,401.9 L50.8,394.0 L51.5,386.1 L52.2,378.4 L52.9,370.8 L53.5,363.3 L54.2,355.9 L54.9,348.6 L55.5,341.4 L56.2,334.3 L56.9,327.3 L57.5,320.4 L58.2,313.7 L58.9,307.0 L59.5,300.4 L60.2,294.0 L60.9,287.6 L61.6,281.3 L62.2,275.2 L62.9,269.1 L63.6,263.1 L64.2,257.3 L64.9,251.5 L65.6,245.8 L66.2,240.2 L66.9,234.8 L67.6,229.4 L68.3,224.1 L68.9,218.9 L69.6,213.8 L70.3,208.8 L70.9,203.8 L71.6,199.0 L72.3,194.3 L73.0,189.6 L73.6,185.0 L74.3,180.6 L75.0,176.2 L75.6,171.9 L76.3,167.6 L77.0,163.5 L77.6,159.4 L78.3,155.5 L79.0,151.6 L79.7,147.8 L80.3,144.1 L81.0,140.4 L81.7,136.9 L82.3,133.4 L83.0,130.0 L83.7,126.7 L84.3,123.4 L85.0,120.3 L85.7,117.2 L86.4,114.2 L87.0,111.2 L87.7,108.4 L88.4,105.6 L89.0,102.9 L89.7,100.2 L90.4,97.6 L91.0,95.1 L91.7,92.7 L92.4,90.3 L93.0,88.0 L93.7,85.8 L94.4,83.7 L95.1,81.6 L95.7,79.5 L96.4,77.6 L97.1,75.7 L97.7,73.9 L98.4,72.1 L99.1,70.4 L99.8,68.8 L100.4,67.2 L101.1,65.7 L101.8,64.2 L102.4,62.8 L103.1,61.5 L103.8,60.2 L104.4,59.0 L105.1,57.8 L105.8,56.7 L106.5,55.6 L107.1,54.6 L107.8,53.7 L108.5,52.8 L109.1,51.9 L109.8,51.2 L110.5,50.4 L111.1,49.7 L111.8,49.1 L112.5,48.5 L113.1,48.0 L113.8,47.5 L114.5,47.0 L115.2,46.7 L115.8,46.3 L116.5,46.0 L117.2,45.7 L117.8,45.5 L118.5,45.4 L119.2,45.2 L119.9,45.1 L120.5,45.1 L121.2,45.1 L121.9,45.1 L122.5,45.2 L123.2,45.3 L123.9,45.5 L124.5,45.7 L125.2,45.9 L125.9,46.2 L126.5,46.5 L127.2,46.8 L127.9,47.2 L128.6,47.6 L129.2,48.0 L129.9,48.5 L130.6,49.0 L131.2,49.5 L131.9,50.0 L132.6,50.6 L133.2,51.2 L133.9,51.9 L134.6,52.6 L135.3,53.3 L135.9,54.0 L136.6,54.7 L137.3,55.5 L137.9,56.3 L138.6,57.1 L139.3,58.0 L139.9,58.8 L140.6,59.7 L141.3,60.6 L142.0,61.6 L142.6,62.5 L143.3,63.5 L144.0,64.5 L144.6,65.5 L145.3,66.5 L146.0,67.5 L146.7,68.6 L147.3,69.6 L148.0,70.7 L148.7,71.8 L149.3,72.9 L150.0,74.0 L150.7,75.1 L151.3,76.3 L152.0,77.4 L152.7,78.6 L153.3,79.7 L154.0,80.9 L154.7,82.1 L155.4,83.3 L156.0,84.5 L156.7,85.6 L157.4,86.8 L158.0,88.1 L158.7,89.3 L159.4,90.5 L160.0,91.7 L160.7,92.9 L161.4,94.1 L162.1,95.3 L162.7,96.5 L163.4,97.7 L164.1,99.0 L164.7,100.2 L165.4,101.4 L166.1,102.6 L166.8,103.8 L167.4,104.9 L168.1,106.1 L168.8,107.3 L169.4,108.5 L170.1,109.6 L170.8,110.8 L171.4,111.9 L172.1,113.0 L172.8,114.2 L173.5,115.3 L174.1,116.4 L174.8,117.4 L175.5,118.5 L176.1,119.6 L176.8,120.6 L177.5,121.6 L178.1,122.6 L178.8,123.6 L179.5,124.6 L180.2,125.5 L180.8,126.5 L181.5,127.4 L182.2,128.3 L182.8,129.1 L183.5,130.0 L184.2,130.8 L184.8,131.6 L185.5,132.4 L186.2,133.2 L186.8,133.9 L187.5,134.6 L188.2,135.3 L188.9,135.9 L189.5,136.6 L190.2,137.2 L190.9,137.7 L191.5,138.3 L192.2,138.8 L192.9,139.3 L193.5,139.7 L194.2,140.1 L194.9,140.5 L195.6,140.8 L196.2,141.1 L196.9,141.4 L197.6,141.7 L198.2,141.9 L198.9,142.0 L199.6,142.2 L200.2,142.2 L200.9,142.3 L201.6,142.3 L202.3,142.3 L202.9,142.2 L203.6,142.1 L204.3,141.9 L204.9,141.7 L205.6,141.5 L206.3,141.2 L207.0,140.9 L207.6,140.5 L208.3,140.1 L209.0,139.6 L209.6,139.1 L210.3,138.5 L211.0,137.9 L211.6,137.2 L212.3,136.5 L213.0,135.7 L213.7,134.9 L214.3,134.0 L215.0,133.1 L215.7,132.1 L216.3,131.1 L217.0,130.0 L217.7,128.9 L218.3,127.6 L219.0,126.4 L219.7,125.1 L220.3,123.7 L221.0,122.2 L221.7,120.7 L222.4,119.2 L223.0,117.6 L223.7,115.9 L224.4,114.1 L225.0,112.3 L225.7,110.5 L226.4,108.5 L227.0,106.5 L227.7,104.5 L228.4,102.3 L229.1,100.1 L229.7,97.8 L230.4,95.5 L231.1,93.1 L231.7,90.6 L232.4,88.1 L233.1,85.4 L233.8,82.8 L234.4,80.0 L235.1,77.1 L235.8,74.2 L236.4,71.2 L237.1,68.2 L237.8,65.0 L238.4,61.8 L239.1,58.5 L239.8,55.1 L240.5,51.7 L241.1,48.2 L241.8,44.6 L242.5,40.9 L243.1,37.1 L243.8,33.2 L244.5,29.3 L245.1,25.3 L245.8,21.2 L246.5,17.0 L247.2,12.7 L247.8,8.3 L248.5,3.9 L249.2,-0.7 L249.8,-5.3 L250.5,-10.0 L251.2,-14.8 L251.8,-19.7 L252.5,-24.7 L253.2,-29.8 L253.8,-34.9 L254.5,-40.2 L255.2,-45.6 L255.9,-51.0 L256.5,-56.6 L257.2,-62.2 L257.9,-67.9 L258.5,-73.8 L259.2,-79.7 L259.9,-85.7 L260.5,-91.9 L261.2,-98.1 L261.9,-104.4 L262.6,-110.8 L263.2,-117.4 L263.9,-124.0 L264.6,-130.8 L265.2,-137.6 L265.9,-144.5 L266.6,-151.6 L267.2,-158.8 L267.9,-166.0 L268.6,-173.4 L269.3,-180.9 L269.9,-188.4 L270.6,-196.1 L271.3,-203.9 L271.9,-211.9 L272.6,-219.9 L273.3,-228.0 L273.9,-236.3 L274.6,-244.6 L275.3,-253.1 L276.0,-261.7 L276.6,-270.4 L277.3,-279.2 L278.0,-288.2 L278.6,-297.2 L279.3,-306.4 L280.0,-315.7 L280.7,-325.1 L281.3,-334.7 L282.0,-344.3 L282.7,-354.1 L283.3,-364.0 L284.0,-374.0\" clip-path=\"url(#c5960)\" style=\"fill:none;stroke:var(--danger);stroke-width:2.2\"/><circle cx=\"83.0\" cy=\"130.0\" r=\"3.2\" style=\"fill:var(--accent-text)\"/><circle cx=\"183.5\" cy=\"130.0\" r=\"3.2\" style=\"fill:var(--accent-text)\"/><circle cx=\"217.0\" cy=\"130.0\" r=\"3.2\" style=\"fill:var(--accent-text)\"/></svg><div class=\"keybox\"><b>Common mistake:</b> stopping too early. 2x<sup>3</sup> − 18x = 2x(x<sup>2</sup> − 9) is factored, but not completely: x<sup>2</sup> − 9 = (x + 3)(x − 3), so the answer is 2x(x + 3)(x − 3).</div><div class=\"hub-btns\" style=\"margin-top:12px\"><button class=\"hub-btn primary\" data-go=\"s8\">Practise 7.8 →</button></div></section><section class=\"note\" id=\"nsum\"><h2>Chapter checklist</h2><ul><li>I can classify polynomials by degree and number of terms, write them in standard form, and add and subtract them.</li><li>I can multiply a monomial by a polynomial and multiply binomials and larger polynomials using the Distributive Property, FOIL and area models.</li><li>I can use the square of a binomial pattern and the sum and difference pattern to multiply quickly.</li><li>I can use the Zero-Product Property and the greatest common monomial factor to solve polynomial equations.</li><li>I can factor trinomials whose leading coefficient is 1 and use factoring to solve equations.</li><li>I can factor trinomials with a leading coefficient other than 1, including negative ones, and solve related equations.</li><li>I can factor differences of two squares and perfect square trinomials.</li><li>I can factor by grouping, factor polynomials completely and solve equations by factoring completely.</li></ul><div class=\"hub-btns\" style=\"margin-top:10px\"><button class=\"hub-btn\" data-go=\"s9\">Assessment A</button><button class=\"hub-btn\" data-go=\"s10\">Assessment B</button><button class=\"hub-btn\" data-go=\"s11\">Assessment C</button><button class=\"hub-btn\" data-go=\"s12\">Assessment D</button><button class=\"hub-btn primary\" data-go=\"report\">📊 Report</button></div></section>";
var REPORT = [["s9", "A", "Knowing and understanding"], ["s10", "B", "Investigating patterns"], ["s11", "C", "Communicating"], ["s12", "D", "Applying mathematics in real-life contexts"]];
var SECTIONS = [{"id": "s1", "label": "7.1 Adding and Subtracting Polynomials", "sub": "I can classify polynomials by degree and number of terms, write them in standard form, and add and subtract them.", "slides": [{"kind": "mcq", "text": "What is the degree of the monomial −4x<sup>3</sup>y<sup>2</sup>?", "opts": ["6", "3", "5", "−4"], "correct": 2, "tag": "", "sol": "The degree of a monomial is the sum of the exponents of its variables: 3 + 2 = 5. (3 is only the exponent of x, −4 is the coefficient, and 6 multiplies the exponents.)"}, {"kind": "blank", "p": "Look at the polynomial 7 − 2x<sup>3</sup> + 5x.", "tag": "", "marks": "", "flat": [{"t": "Its degree is __B1__", "a": {"B1": "3"}}, {"t": "Its leading coefficient is __B1__", "a": {"B1": "-2"}}, {"t": "By its number of terms it is a __B1__ (monomial / binomial / trinomial).", "a": {"B1": "trinomial"}, "expr": "words"}], "sol": "The term with the greatest degree is −2x<sup>3</sup>, so the degree is 3. In standard form the polynomial is −2x<sup>3</sup> + 5x + 7.\nThe leading term is −2x<sup>3</sup>, so the leading coefficient is −2 (not 7, which is only the first term as written).\nIt has three terms: 7, −2x<sup>3</sup> and 5x, so it is a trinomial."}, {"kind": "mcq", "text": "Which expression is a polynomial?", "opts": ["{1/2}x<sup>3</sup> − 4x", "{6/x} − x<sup>2</sup>", "5x<sup>−2</sup> + 3", "√x + 7"], "correct": 0, "tag": "", "sol": "Every exponent of a polynomial must be a whole number. {1/2}x<sup>3</sup> − 4x qualifies (a fraction coefficient is fine). 5x<sup>−2</sup> has a negative exponent, √x = x<sup>{1/2}</sup> has a fraction exponent, and {6/x} = 6x<sup>−1</sup>."}, {"kind": "blank", "p": "Add (4x<sup>2</sup> − 3x + 6) + (2x<sup>2</sup> + 8x − 9) by combining like terms.", "tag": "", "marks": "", "flat": [{"t": "x<sup>2</sup>-terms: 4x<sup>2</sup> + 2x<sup>2</sup> = __B1__x<sup>2</sup>", "a": {"B1": "6"}}, {"t": "x-terms: −3x + 8x = __B1__x", "a": {"B1": "5"}}, {"t": "Constants: 6 + (−9) = __B1__", "a": {"B1": "-3"}}], "sol": "Add the coefficients of the x<sup>2</sup>-terms: 4 + 2 = 6.\n−3 + 8 = 5.\n6 − 9 = −3. The sum is 6x<sup>2</sup> + 5x − 3."}, {"kind": "mcq", "text": "Subtract: (5y<sup>2</sup> + 2y − 7) − (3y<sup>2</sup> − 4y + 1).", "opts": ["8y<sup>2</sup> − 2y − 6", "2y<sup>2</sup> − 2y − 6", "2y<sup>2</sup> + 6y − 6", "2y<sup>2</sup> + 6y − 8"], "correct": 3, "tag": "", "sol": "Add the opposite of every term: 5y<sup>2</sup> + 2y − 7 − 3y<sup>2</sup> + 4y − 1 = 2y<sup>2</sup> + 6y − 8. (2y<sup>2</sup> − 2y − 6 changes only the first sign; 2y<sup>2</sup> + 6y − 6 forgets to change the sign of +1; 8y<sup>2</sup> − 2y − 6 adds instead of subtracting.)"}, {"kind": "blank", "p": "Subtract (6x<sup>3</sup> − x + 4) − (2x<sup>3</sup> + 3x<sup>2</sup> − 5x − 2).", "tag": "", "marks": "", "flat": [{"t": "The opposite of the second polynomial is −2x<sup>3</sup> − 3x<sup>2</sup> + __B1__x + __B2__", "a": {"B1": "5", "B2": "2"}}, {"t": "The difference is 4x<sup>3</sup> − 3x<sup>2</sup> + __B1__x + __B2__", "a": {"B1": "4", "B2": "6"}}], "sol": "Change the sign of every term: −(2x<sup>3</sup> + 3x<sup>2</sup> − 5x − 2) = −2x<sup>3</sup> − 3x<sup>2</sup> + 5x + 2.\nAdd to the first polynomial: (6x<sup>3</sup> − 2x<sup>3</sup>) − 3x<sup>2</sup> + (−x + 5x) + (4 + 2) = 4x<sup>3</sup> − 3x<sup>2</sup> + 4x + 6."}, {"kind": "mcq", "text": "<b>Error analysis.</b> Ava wrote (3a<sup>2</sup> − 5a) − (a<sup>2</sup> − 2a) = 2a<sup>2</sup> − 7a. What is the correct difference?", "opts": ["2a<sup>2</sup> − 3a", "2a<sup>2</sup> − 7a", "4a<sup>2</sup> − 7a", "2a<sup>2</sup> + 3a"], "correct": 0, "tag": "", "sol": "Subtracting −2a means adding 2a: 3a<sup>2</sup> − 5a − a<sup>2</sup> + 2a = 2a<sup>2</sup> − 3a. Ava subtracted 2a instead of changing its sign."}, {"kind": "blank", "p": "A bakery sells x cakes a week. Its revenue is R = −x<sup>2</sup> + 40x dollars and its cost is C = 6x + 120 dollars. Profit is P = R − C.", "tag": "", "marks": "", "flat": [{"t": "P = −x<sup>2</sup> + __B1__x − __B2__", "a": {"B1": "34", "B2": "120"}}, {"t": "The profit when 10 cakes are sold is $__B1__", "a": {"B1": "120"}}], "sol": "P = −x<sup>2</sup> + 40x − 6x − 120 = −x<sup>2</sup> + 34x − 120.\nP = −100 + 340 − 120 = 120 dollars."}, {"kind": "mcq", "text": "A triangle has sides (2x + 3), (x<sup>2</sup> − x) and (4x − 5) centimetres. Which expression gives its perimeter?", "opts": ["x<sup>2</sup> + 6x + 2", "x<sup>2</sup> + 5x + 8", "x<sup>2</sup> + 5x − 2", "x<sup>2</sup> + 7x − 2"], "correct": 2, "tag": "", "sol": "Add the three sides: x<sup>2</sup> + (2x − x + 4x) + (3 − 5) = x<sup>2</sup> + 5x − 2. (x<sup>2</sup> + 7x − 2 ignores the −x; x<sup>2</sup> + 5x + 8 treats −5 as +5.)"}, {"kind": "blank", "p": "Find the missing polynomial: ( ? ) + (3x<sup>2</sup> − 2x + 5) = 7x<sup>2</sup> + x − 1.", "tag": "", "marks": "", "flat": [{"t": "Missing polynomial = __B1__x<sup>2</sup> + __B2__x − __B3__", "a": {"B1": "4", "B2": "3", "B3": "6"}}], "sol": "Subtract: (7x<sup>2</sup> + x − 1) − (3x<sup>2</sup> − 2x + 5) = 4x<sup>2</sup> + 3x − 6. Check: 4x<sup>2</sup> + 3x − 6 + 3x<sup>2</sup> − 2x + 5 = 7x<sup>2</sup> + x − 1 ✓"}, {"kind": "mcq", "text": "<b>Reasoning.</b> Which statement is always true?", "opts": ["The difference of two trinomials is a trinomial", "The sum of two binomials is a binomial", "The sum of two polynomials is a polynomial", "The sum of two quadratic polynomials has degree 2"], "correct": 2, "tag": "", "sol": "Adding or subtracting polynomials only combines like terms, so the result is always a polynomial (polynomials are closed under addition and subtraction). Counter-examples for the others: (x + 1) + (x − 1) = 2x is a monomial; (x<sup>2</sup> + x + 1) − (x<sup>2</sup> + x + 2) = −1; (x<sup>2</sup> + 1) + (−x<sup>2</sup> + x) = x + 1 has degree 1."}, {"kind": "blank", "p": "Two stones are dropped at the same time. Their heights after t seconds are h₁ = −16t<sup>2</sup> + 64 and h₂ = −16t<sup>2</sup> + 40 feet.", "tag": "", "marks": "", "flat": [{"t": "h₁ − h₂ = __B1__ ft", "a": {"B1": "24"}}, {"t": "As t increases, the difference in height __B1__ (stays the same / grows).", "a": {"B1": "stays the same"}, "expr": "words", "accept": ["same", "constant", "stays constant", "stays same", "the same"]}], "sol": "(−16t<sup>2</sup> + 64) − (−16t<sup>2</sup> + 40) = −16t<sup>2</sup> + 64 + 16t<sup>2</sup> − 40 = 24.\nThe t<sup>2</sup>-terms cancel, so the difference is 24 ft at every moment until the first stone lands."}, {"kind": "mcq", "text": "Which shows 8 + 3x<sup>2</sup> − x<sup>4</sup> in standard form with its leading coefficient?", "opts": ["−x<sup>4</sup> + 3x<sup>2</sup> + 8; leading coefficient −1", "8 + 3x<sup>2</sup> − x<sup>4</sup>; leading coefficient 8", "−x<sup>4</sup> + 3x<sup>2</sup> + 8; leading coefficient 8", "3x<sup>2</sup> − x<sup>4</sup> + 8; leading coefficient 3"], "correct": 0, "tag": "", "sol": "Standard form lists terms by decreasing degree: −x<sup>4</sup> (degree 4), 3x<sup>2</sup>, 8. The leading coefficient is the coefficient of the first term, −1."}]}, {"id": "s2", "label": "7.2 Multiplying Polynomials", "sub": "I can multiply a monomial by a polynomial and multiply binomials and larger polynomials using the Distributive Property, FOIL and area models.", "slides": [{"kind": "mcq", "text": "Find −3x(2x<sup>2</sup> − 5x + 4).", "opts": ["−6x<sup>3</sup> − 5x + 4", "−6x<sup>3</sup> − 15x<sup>2</sup> − 12x", "−6x<sup>2</sup> + 15x − 12", "−6x<sup>3</sup> + 15x<sup>2</sup> − 12x"], "correct": 3, "tag": "", "sol": "Multiply every term by −3x: −3x · 2x<sup>2</sup> = −6x<sup>3</sup>, −3x · (−5x) = 15x<sup>2</sup>, −3x · 4 = −12x. (−6x<sup>3</sup> − 5x + 4 multiplies only the first term; −6x<sup>2</sup> + 15x − 12 forgets to add exponents.)"}, {"kind": "blank", "p": "Use FOIL to find (x + 4)(x + 7).", "tag": "", "marks": "", "flat": [{"t": "Outer + Inner: 7x + 4x = __B1__x", "a": {"B1": "11"}}, {"t": "Last: 4 · 7 = __B1__", "a": {"B1": "28"}}], "sol": "First: x · x = x<sup>2</sup>. Outer: x · 7 = 7x. Inner: 4 · x = 4x. Together 11x.\nLast: 28. So (x + 4)(x + 7) = x<sup>2</sup> + 11x + 28."}, {"kind": "mcq", "text": "Find (x − 6)(x + 2).", "opts": ["x<sup>2</sup> + 4x − 12", "x<sup>2</sup> − 12", "x<sup>2</sup> − 4x − 12", "x<sup>2</sup> − 8x − 12"], "correct": 2, "tag": "", "sol": "FOIL: x<sup>2</sup> + 2x − 6x − 12 = x<sup>2</sup> − 4x − 12. (x<sup>2</sup> − 12 leaves out the outer and inner products; x<sup>2</sup> + 4x − 12 has the sign of the middle term wrong.)"}, {"kind": "blank", "p": "Complete the area model to find (2x + 5)(3x − 1).", "tag": "", "marks": "", "flat": [{"t": "Top-right cell: 2x · (−1) = __B1__x", "a": {"B1": "-2"}}, {"t": "Bottom-left cell: 5 · 3x = __B1__x", "a": {"B1": "15"}}, {"t": "(2x + 5)(3x − 1) = 6x<sup>2</sup> + __B1__x − 5", "a": {"B1": "13"}}], "sol": "Row 2x times column −1 gives −2x.\nRow +5 times column 3x gives 15x.\nAdd the cells: 6x<sup>2</sup> − 2x + 15x − 5 = 6x<sup>2</sup> + 13x − 5.", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 146\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><text class=\"lb\" x=\"150.0\" y=\"11.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">(2x + 5)(3x − 1)</text><text class=\"lb\" x=\"124.0\" y=\"38.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">3x</text><text class=\"lb\" x=\"204.0\" y=\"38.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−1</text><text class=\"lb\" x=\"74.0\" y=\"71.0\" text-anchor=\"end\" dominant-baseline=\"middle\">2x</text><text class=\"lb\" x=\"74.0\" y=\"113.0\" text-anchor=\"end\" dominant-baseline=\"middle\">+5</text><rect x=\"84.0\" y=\"50.0\" width=\"80\" height=\"42\" style=\"fill:none;stroke:var(--ink-soft);stroke-width:1.4\"/><text class=\"lb\" x=\"124.0\" y=\"71.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">6x²</text><rect x=\"164.0\" y=\"50.0\" width=\"80\" height=\"42\" style=\"fill:none;stroke:var(--ink-soft);stroke-width:1.4\"/><text class=\"po\" x=\"204.0\" y=\"71.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">?</text><rect x=\"84.0\" y=\"92.0\" width=\"80\" height=\"42\" style=\"fill:none;stroke:var(--ink-soft);stroke-width:1.4\"/><text class=\"po\" x=\"124.0\" y=\"113.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">?</text><rect x=\"164.0\" y=\"92.0\" width=\"80\" height=\"42\" style=\"fill:none;stroke:var(--ink-soft);stroke-width:1.4\"/><text class=\"lb\" x=\"204.0\" y=\"113.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−5</text></svg>"}, {"kind": "mcq", "text": "<b>Error analysis.</b> Mia wrote (2x − 3)(x + 4) = 2x<sup>2</sup> − 12. What is the correct product?", "opts": ["2x<sup>2</sup> + 11x − 12; she added 8x and 3x", "2x<sup>2</sup> − 5x − 12; she mixed up the signs", "2x<sup>2</sup> + 5x − 12; she left out the outer and inner products", "2x<sup>2</sup> − 12; her answer is correct"], "correct": 2, "tag": "", "sol": "(2x − 3)(x + 4) = 2x<sup>2</sup> + 8x − 3x − 12 = 2x<sup>2</sup> + 5x − 12. Multiplying only the first terms and the last terms misses 8x and −3x."}, {"kind": "blank", "p": "Find (x − 2)(x<sup>2</sup> + 3x − 5) by multiplying each term of the binomial by the trinomial.", "tag": "", "marks": "", "flat": [{"t": "−2(x<sup>2</sup> + 3x − 5) = −2x<sup>2</sup> − __B1__x + 10", "a": {"B1": "6"}}, {"t": "The product is x<sup>3</sup> + x<sup>2</sup> − __B1__x + 10", "a": {"B1": "11"}}], "sol": "x(x<sup>2</sup> + 3x − 5) = x<sup>3</sup> + 3x<sup>2</sup> − 5x, and −2 times each term gives −2x<sup>2</sup> − 6x + 10.\nCombine like terms: x<sup>3</sup> + (3x<sup>2</sup> − 2x<sup>2</sup>) + (−5x − 6x) + 10 = x<sup>3</sup> + x<sup>2</sup> − 11x + 10."}, {"kind": "mcq", "text": "A rectangular garden is (x + 6) m long and (x + 2) m wide. Which expression gives its area?", "opts": ["x<sup>2</sup> + 8x + 8", "x<sup>2</sup> + 12", "2x + 8", "x<sup>2</sup> + 8x + 12"], "correct": 3, "tag": "", "sol": "Area = length × width = (x + 6)(x + 2) = x<sup>2</sup> + 2x + 6x + 12 = x<sup>2</sup> + 8x + 12. (2x + 8 adds the sides instead of multiplying.)"}, {"kind": "blank", "p": "Look at the product (3x<sup>2</sup> + 1)(x<sup>3</sup> − 2x).", "tag": "", "marks": "", "flat": [{"t": "Before combining like terms there are __B1__ products", "a": {"B1": "4"}}, {"t": "The product has degree __B1__", "a": {"B1": "5"}}, {"t": "The coefficient of x<sup>3</sup> in the product is __B1__", "a": {"B1": "-5"}}], "sol": "Each of the 2 terms of the first factor multiplies each of the 2 terms of the second: 2 × 2 = 4.\n3x<sup>2</sup> · x<sup>3</sup> = 3x<sup>5</sup>: degrees add, 2 + 3 = 5.\nThe products are 3x<sup>5</sup>, −6x<sup>3</sup>, x<sup>3</sup> and −2x, so the x<sup>3</sup>-terms combine to −5x<sup>3</sup>. The product is 3x<sup>5</sup> − 5x<sup>3</sup> − 2x."}, {"kind": "mcq", "text": "Find (4y − 1)(2y − 3).", "opts": ["8y<sup>2</sup> − 10y + 3", "8y<sup>2</sup> + 3", "8y<sup>2</sup> − 14y + 3", "8y<sup>2</sup> − 14y − 3"], "correct": 2, "tag": "", "sol": "F: 8y<sup>2</sup>. O: 4y · (−3) = −12y. I: −1 · 2y = −2y. L: (−1)(−3) = +3. Total: 8y<sup>2</sup> − 14y + 3. (−10y comes from −12y + 2y; −3 forgets that a negative times a negative is positive.)"}, {"kind": "blank", "p": "An 8 in by 10 in photo has a frame of width x inches all the way around it.", "tag": "", "marks": "", "flat": [{"t": "The area of photo and frame together is (8 + 2x)(10 + 2x) = 4x<sup>2</sup> + __B1__x + 80 square inches", "a": {"B1": "36"}}, {"t": "When the frame is 1.5 in wide, the total area is __B1__ square inches", "a": {"B1": "143"}}], "sol": "FOIL: 80 + 16x + 20x + 4x<sup>2</sup> = 4x<sup>2</sup> + 36x + 80.\n4(2.25) + 36(1.5) + 80 = 9 + 54 + 80 = 143. Check: the outer size is 11 in by 13 in, and 11 × 13 = 143 ✓", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 180\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><text class=\"lb\" x=\"150.0\" y=\"10.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">Photo 8 in by 10 in, frame x in wide</text><rect x=\"46.0\" y=\"42\" width=\"180\" height=\"110\" style=\"fill:none;stroke:var(--ink-soft);stroke-width:1.6\"/><text class=\"lb\" x=\"136.0\" y=\"31.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">10 + 2x</text><text class=\"lb\" x=\"234.0\" y=\"97.0\" text-anchor=\"start\" dominant-baseline=\"middle\">8 + 2x</text><rect x=\"62.0\" y=\"58\" width=\"148\" height=\"78\" style=\"fill:none;stroke:var(--accent-text);stroke-width:1.4;stroke-dasharray:5 4\"/><text class=\"lb\" x=\"136.0\" y=\"97.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">8 × 10</text></svg>"}, {"kind": "mcq", "text": "<b>Reasoning.</b> Which product has degree 4?", "opts": ["(x + 2)(x − 2)", "(x<sup>2</sup> + 4)(x + 4)", "(x<sup>3</sup> + x)(x<sup>3</sup> − x)", "(x<sup>2</sup> + 1)(x<sup>2</sup> − 3)"], "correct": 3, "tag": "", "sol": "The degree of a product is the sum of the degrees of the factors: 2 + 2 = 4. The others have degree 2 + 1 = 3, 1 + 1 = 2 and 3 + 3 = 6."}, {"kind": "blank", "p": "A box is x cm high, (x + 2) cm long and (x − 1) cm wide.", "tag": "", "marks": "", "flat": [{"t": "(x + 2)(x − 1) = x<sup>2</sup> + __B1__x − 2", "a": {"B1": "1"}}, {"t": "Volume V = x<sup>3</sup> + x<sup>2</sup> − __B1__x", "a": {"B1": "2"}}, {"t": "When x = 4, V = __B1__ cm³", "a": {"B1": "72"}}], "sol": "x<sup>2</sup> − x + 2x − 2 = x<sup>2</sup> + x − 2.\nMultiply by x: V = x(x<sup>2</sup> + x − 2) = x<sup>3</sup> + x<sup>2</sup> − 2x.\n64 + 16 − 8 = 72. Check: 4 × 6 × 3 = 72 ✓", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 190\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><text class=\"lb\" x=\"150.0\" y=\"10.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">Box (cm)</text><rect x=\"60\" y=\"70\" width=\"140\" height=\"90\" style=\"stroke:var(--ink-soft);stroke-width:1.6;fill:none\"/><polyline points=\"60,70 100,42.0 240,42.0 240,132.0 200,160\" style=\"stroke:var(--ink-soft);stroke-width:1.6;fill:none\"/><line x1=\"200\" y1=\"70\" x2=\"240\" y2=\"42.0\" style=\"stroke:var(--ink-soft);stroke-width:1.6;fill:none\"/><text class=\"lb\" x=\"130.0\" y=\"174.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">x + 2</text><text class=\"lb\" x=\"230.0\" y=\"150.0\" text-anchor=\"start\" dominant-baseline=\"middle\">x − 1</text><text class=\"lb\" x=\"52.0\" y=\"115.0\" text-anchor=\"end\" dominant-baseline=\"middle\">x</text></svg>"}, {"kind": "mcq", "text": "Find (a + 2b)(3a − b).", "opts": ["3a<sup>2</sup> + 5ab + 2b<sup>2</sup>", "3a<sup>2</sup> + 7ab − 2b<sup>2</sup>", "3a<sup>2</sup> + 5ab − 2b<sup>2</sup>", "3a<sup>2</sup> − 2b<sup>2</sup>"], "correct": 2, "tag": "", "sol": "F: 3a<sup>2</sup>. O: −ab. I: 6ab. L: −2b<sup>2</sup>. So 3a<sup>2</sup> + 5ab − 2b<sup>2</sup>. (7ab comes from adding ab instead of −ab.)"}]}, {"id": "s3", "label": "7.3 Special Products of Polynomials", "sub": "I can use the square of a binomial pattern and the sum and difference pattern to multiply quickly.", "slides": [{"kind": "mcq", "text": "Find (x + 6)<sup>2</sup>.", "opts": ["x<sup>2</sup> + 36", "x<sup>2</sup> + 6x + 36", "x<sup>2</sup> + 12x + 36", "x<sup>2</sup> + 12x + 12"], "correct": 2, "tag": "", "sol": "Square of a binomial: (a + b)<sup>2</sup> = a<sup>2</sup> + 2ab + b<sup>2</sup> = x<sup>2</sup> + 2(x)(6) + 36 = x<sup>2</sup> + 12x + 36. (x<sup>2</sup> + 36 forgets the middle term 2ab.)"}, {"kind": "blank", "p": "Use the pattern (a − b)<sup>2</sup> = a<sup>2</sup> − 2ab + b<sup>2</sup> to find (3y − 4)<sup>2</sup>.", "tag": "", "marks": "", "flat": [{"t": "First term: (3y)<sup>2</sup> = __B1__y<sup>2</sup>", "a": {"B1": "9"}}, {"t": "Middle term: −2(3y)(4) = −__B1__y", "a": {"B1": "24"}}, {"t": "Last term: 4<sup>2</sup> = __B1__", "a": {"B1": "16"}}], "sol": "Square the whole first term, including the 3: 9y<sup>2</sup>.\n2 · 3y · 4 = 24y, with a minus sign.\n(3y − 4)<sup>2</sup> = 9y<sup>2</sup> − 24y + 16."}, {"kind": "mcq", "text": "Find (5m + 2)(5m − 2).", "opts": ["5m<sup>2</sup> − 4", "25m<sup>2</sup> − 20m − 4", "25m<sup>2</sup> − 4", "25m<sup>2</sup> + 4"], "correct": 2, "tag": "", "sol": "Sum and difference pattern: (a + b)(a − b) = a<sup>2</sup> − b<sup>2</sup> = (5m)<sup>2</sup> − 2<sup>2</sup> = 25m<sup>2</sup> − 4. The middle terms +10m and −10m cancel."}, {"kind": "blank", "p": "Use special products to calculate mentally.", "tag": "", "marks": "", "flat": [{"t": "49 × 51 = (50 − 1)(50 + 1) = __B1__", "a": {"B1": "2499"}}, {"t": "103<sup>2</sup> = (100 + 3)<sup>2</sup> = __B1__", "a": {"B1": "10609"}, "accept": ["10,609"]}], "sol": "50<sup>2</sup> − 1<sup>2</sup> = 2500 − 1 = 2499.\n100<sup>2</sup> + 2(100)(3) + 3<sup>2</sup> = 10000 + 600 + 9 = 10609."}, {"kind": "mcq", "text": "<b>Error analysis.</b> Ben wrote (2x − 5)<sup>2</sup> = 4x<sup>2</sup> − 25. What is correct?", "opts": ["4x<sup>2</sup> − 20x + 25", "4x<sup>2</sup> − 10x + 25", "4x<sup>2</sup> − 25", "4x<sup>2</sup> + 25"], "correct": 0, "tag": "", "sol": "(2x − 5)<sup>2</sup> = (2x)<sup>2</sup> − 2(2x)(5) + 5<sup>2</sup> = 4x<sup>2</sup> − 20x + 25. Ben squared each term separately; that only works for products, not sums or differences. (−10x forgets the 2 in 2ab.)"}, {"kind": "blank", "p": "Find (2a + 3b)<sup>2</sup>.", "tag": "", "marks": "", "flat": [{"t": "(2a)<sup>2</sup> = __B1__a<sup>2</sup>", "a": {"B1": "4"}}, {"t": "2(2a)(3b) = __B1__ab", "a": {"B1": "12"}}, {"t": "(3b)<sup>2</sup> = __B1__b<sup>2</sup>", "a": {"B1": "9"}}], "sol": "Square the first term.\nTwice the product of the two terms.\nSquare the last term: (2a + 3b)<sup>2</sup> = 4a<sup>2</sup> + 12ab + 9b<sup>2</sup>."}, {"kind": "mcq", "text": "In a plant, each parent carries one gene G and one gene g, and passes on G or g with probability 0.5 each. The model (0.5G + 0.5g)<sup>2</sup> = 0.25GG + 0.5Gg + 0.25gg describes the offspring. What percent of the offspring are expected to be Gg?", "opts": ["100%", "75%", "50%", "25%"], "correct": 2, "tag": "", "sol": "The middle term 2ab = 2(0.5G)(0.5g) = 0.5Gg, so 50% are expected to be Gg. 25% are GG and 25% are gg."}, {"kind": "blank", "p": "A square garden has sides of x metres. Each side is made 3 m longer.", "tag": "", "marks": "", "flat": [{"t": "Increase in area: (x + 3)<sup>2</sup> − x<sup>2</sup> = __B1__x + __B2__ m²", "a": {"B1": "6", "B2": "9"}}, {"t": "If x = 10, the area increases by __B1__ m²", "a": {"B1": "69"}}], "sol": "(x + 3)<sup>2</sup> = x<sup>2</sup> + 6x + 9, so the increase is 6x + 9.\n6(10) + 9 = 69. Check: 13<sup>2</sup> − 10<sup>2</sup> = 169 − 100 = 69 ✓"}, {"kind": "mcq", "text": "Which product is a difference of two squares when multiplied out?", "opts": ["(4k − 7)(7 − 4k)", "(4k + 7)(7k − 4)", "(4k − 7)(4k + 7)", "(4k − 7)(4k − 7)"], "correct": 2, "tag": "", "sol": "(4k − 7)(4k + 7) = 16k<sup>2</sup> − 49: same terms, opposite signs. (4k − 7)(4k − 7) is a square, 16k<sup>2</sup> − 56k + 49; the others have a middle term too."}, {"kind": "blank", "p": "Use the sum and difference pattern.", "tag": "", "marks": "", "flat": [{"t": "(x + 8)(x − 8) = x<sup>2</sup> − __B1__", "a": {"B1": "64"}}, {"t": "(6 − 2t)(6 + 2t) = 36 − __B1__t<sup>2</sup>", "a": {"B1": "4"}}], "sol": "a<sup>2</sup> − b<sup>2</sup> with a = x and b = 8.\na = 6 and b = 2t, so b<sup>2</sup> = 4t<sup>2</sup>."}, {"kind": "mcq", "text": "<b>Reasoning.</b> How do (a − b)<sup>2</sup> and (b − a)<sup>2</sup> compare?", "opts": ["They are equal, because b − a = −(a − b) and (−1)<sup>2</sup> = 1", "They are equal only when a = b, because then both are 0", "(b − a)<sup>2</sup> is the opposite of (a − b)<sup>2</sup>, because b − a = −(a − b)", "They differ in the sign of the middle term, −2ab or +2ab"], "correct": 0, "tag": "", "sol": "(b − a)<sup>2</sup> = b<sup>2</sup> − 2ab + a<sup>2</sup> = a<sup>2</sup> − 2ab + b<sup>2</sup> = (a − b)<sup>2</sup>. Squaring removes the sign: (−1)<sup>2</sup> = 1."}, {"kind": "blank", "p": "A square poster has sides (2x + 5) inches. A square card has sides (2x − 5) inches.", "tag": "", "marks": "", "flat": [{"t": "(2x + 5)<sup>2</sup> − (2x − 5)<sup>2</sup> = __B1__x", "a": {"B1": "40"}}, {"t": "When x = 6, the poster is __B1__ square inches larger", "a": {"B1": "240"}}], "sol": "(4x<sup>2</sup> + 20x + 25) − (4x<sup>2</sup> − 20x + 25) = 40x.\n40 × 6 = 240. Check: 17<sup>2</sup> − 7<sup>2</sup> = 289 − 49 = 240 ✓"}, {"kind": "mcq", "text": "For which value of k is x<sup>2</sup> + kx + 49 equal to (x + 7)<sup>2</sup>?", "opts": ["7", "14", "49", "2"], "correct": 1, "tag": "", "sol": "(x + 7)<sup>2</sup> = x<sup>2</sup> + 2(7)x + 49 = x<sup>2</sup> + 14x + 49, so k = 14."}]}, {"id": "s4", "label": "7.4 Solving Polynomial Equations in Factored Form", "sub": "I can use the Zero-Product Property and the greatest common monomial factor to solve polynomial equations.", "slides": [{"kind": "mcq", "text": "Solve (x − 4)(x + 9) = 0.", "opts": ["x = −36", "x = −4 or x = 9", "x = 4 or x = −9", "x = 4 or x = 9"], "correct": 2, "tag": "", "sol": "Zero-Product Property: x − 4 = 0 or x + 9 = 0, so x = 4 or x = −9. (The signs flip: the factor x + 9 is zero at −9.)"}, {"kind": "blank", "p": "Solve (2n + 3)(n − 5) = 0. Type fractions like -3/2.", "tag": "", "marks": "", "flat": [{"t": "2n + 3 = 0 gives n = __B1__", "a": {"B1": "-3/2"}, "expr": "fv"}, {"t": "n − 5 = 0 gives n = __B1__", "a": {"B1": "5"}}], "sol": "2n = −3, so n = −{3/2}.\nn = 5. The solutions are −{3/2} and 5."}, {"kind": "mcq", "text": "Solve 4x(x − 7) = 0.", "opts": ["x = 4 or x = 7", "x = −4 or x = −7", "x = 7 only", "x = 0 or x = 7"], "correct": 3, "tag": "", "sol": "The factors are 4x and x − 7. 4x = 0 gives x = 0; x − 7 = 0 gives x = 7. The number 4 is a constant factor and is never zero."}, {"kind": "blank", "p": "Solve (y + 6)(y − 1)(y − 8) = 0.", "tag": "", "marks": "", "flat": [{"t": "All solutions, separated by commas: y = __B1__", "a": {"B1": "-6, 1, 8"}, "expr": "set"}], "sol": "Set each factor equal to zero: y = −6, y = 1 or y = 8."}, {"kind": "mcq", "text": "What is the greatest common monomial factor of 12x<sup>3</sup> − 18x<sup>2</sup>?", "opts": ["6x<sup>2</sup>", "6x", "12x<sup>3</sup>", "3x<sup>2</sup>"], "correct": 0, "tag": "", "sol": "GCF(12, 18) = 6 and the lowest power of x is x<sup>2</sup>, so the GCF is 6x<sup>2</sup>: 12x<sup>3</sup> − 18x<sup>2</sup> = 6x<sup>2</sup>(2x − 3)."}, {"kind": "blank", "p": "Factor, then solve 10y<sup>2</sup> + 25y = 0. Type fractions like -5/2.", "tag": "", "marks": "", "flat": [{"t": "10y<sup>2</sup> + 25y = 5y(2y + __B1__)", "a": {"B1": "5"}}, {"t": "The solutions are y = 0 and y = __B1__", "a": {"B1": "-5/2"}, "expr": "fv"}], "sol": "The GCF is 5y: 10y<sup>2</sup> ÷ 5y = 2y and 25y ÷ 5y = 5.\n5y = 0 gives y = 0; 2y + 5 = 0 gives y = −{5/2}."}, {"kind": "mcq", "text": "<b>Error analysis.</b> Zoe solved 3x<sup>2</sup> = 15x by dividing both sides by x and got x = 5. What is wrong?", "opts": ["She should have divided by 3x to get x = −5", "The solutions are x = 5 and x = −5", "Nothing; x = 5 is the only solution", "She lost a solution; the solutions are x = 0 and x = 5"], "correct": 3, "tag": "", "sol": "Dividing by x is not allowed when x could be 0. Instead: 3x<sup>2</sup> − 15x = 0 → 3x(x − 5) = 0 → x = 0 or x = 5. Check: 3(0)<sup>2</sup> = 15(0) ✓"}, {"kind": "blank", "p": "Solve 6t<sup>2</sup> = 30t.", "tag": "", "marks": "", "flat": [{"t": "Rewrite: 6t<sup>2</sup> − 30t = 0, so 6t(t − __B1__) = 0", "a": {"B1": "5"}}, {"t": "Solutions: t = __B1__", "a": {"B1": "0, 5"}, "expr": "set"}], "sol": "The GCF of 6t<sup>2</sup> and 30t is 6t.\n6t = 0 gives t = 0; t − 5 = 0 gives t = 5."}, {"kind": "mcq", "text": "A frog's leap is modelled by y = −{1/4}x(x − 8), where y is its height above the ground and x is the horizontal distance, both in inches. How far does it travel horizontally from take-off to landing?", "opts": ["8 in", "{1/4} in", "16 in", "4 in"], "correct": 0, "tag": "", "sol": "The frog is on the ground (y = 0) when x = 0 or x − 8 = 0, so it lands 8 in from where it took off. (4 in is where it is highest.)"}, {"kind": "blank", "p": "Look at y = (x + 3)(x − 1).", "tag": "", "marks": "", "flat": [{"t": "The x-intercepts of its graph: x = __B1__", "a": {"B1": "-3, 1"}, "expr": "set"}, {"t": "The y-intercept: y = __B1__", "a": {"B1": "-3"}}], "sol": "The graph crosses the x-axis where y = 0: x + 3 = 0 or x − 1 = 0, so x = −3 or x = 1.\nAt x = 0: y = (3)(−1) = −3.", "tools": ["desmos"], "desmos": ["y=(x+3)(x-1)"]}, {"kind": "mcq", "text": "<b>Reasoning.</b> Which equation has exactly the solutions −2 and 5?", "opts": ["(x + 2)(x − 5) = 0", "(x − 2)(x + 5) = 0", "(x − 2)(x − 5) = 0", "(x + 2)(x + 5) = 0"], "correct": 0, "tag": "", "sol": "x + 2 = 0 at x = −2 and x − 5 = 0 at x = 5. A solution r comes from the factor (x − r)."}, {"kind": "blank", "p": "A football is kicked from the ground. Its height after t seconds is h = −16t<sup>2</sup> + 40t feet.", "tag": "", "marks": "", "flat": [{"t": "−16t<sup>2</sup> + 40t = −8t(2t − __B1__)", "a": {"B1": "5"}}, {"t": "The ball lands after t = __B1__ s", "a": {"B1": "2.5"}}], "sol": "The GCF is −8t: −16t<sup>2</sup> ÷ (−8t) = 2t and 40t ÷ (−8t) = −5.\nh = 0 when t = 0 (the kick) or 2t − 5 = 0, so it lands at t = 2.5 s."}, {"kind": "mcq", "text": "Solve (x − 7)<sup>2</sup> = 0.", "opts": ["x = 7 or x = −7", "x = 49", "x = 7 only (a repeated solution)", "x = −7 only"], "correct": 2, "tag": "", "sol": "(x − 7)<sup>2</sup> = (x − 7)(x − 7). Both factors give x = 7, so 7 is a repeated root. (x = −7 makes (x − 7)<sup>2</sup> = 196.)"}]}, {"id": "s5", "label": "7.5 Factoring x² + bx + c", "sub": "I can factor trinomials whose leading coefficient is 1 and use factoring to solve equations.", "slides": [{"kind": "mcq", "text": "Factor x<sup>2</sup> + 8x + 15.", "opts": ["(x + 3)(x + 5)", "(x − 3)(x − 5)", "(x + 4)(x + 4)", "(x + 1)(x + 15)"], "correct": 0, "tag": "", "sol": "Find two numbers with product 15 and sum 8: 3 and 5. Check: (x + 3)(x + 5) = x<sup>2</sup> + 5x + 3x + 15 ✓ (1 and 15 have sum 16; −3 and −5 have sum −8.)"}, {"kind": "blank", "p": "Factor x<sup>2</sup> − 9x + 20 = (x + p)(x + q).", "tag": "", "marks": "", "flat": [{"t": "p and q must have product __B1__ and sum −9", "a": {"B1": "20"}}, {"t": "The two numbers p and q, separated by a comma: __B1__", "a": {"B1": "-4, -5"}, "expr": "set"}], "sol": "In (x + p)(x + q) = x<sup>2</sup> + (p + q)x + pq, the product pq is the constant term 20.\nc is positive and b is negative, so both numbers are negative: −4 · (−5) = 20 and −4 + (−5) = −9. So x<sup>2</sup> − 9x + 20 = (x − 4)(x − 5)."}, {"kind": "mcq", "text": "Factor x<sup>2</sup> + 2x − 24.", "opts": ["(x − 6)(x + 4)", "(x + 6)(x − 4)", "(x + 12)(x − 2)", "(x + 8)(x − 3)"], "correct": 1, "tag": "", "sol": "c = −24 is negative, so the numbers have opposite signs: 6 · (−4) = −24 and 6 + (−4) = 2. ((x − 6)(x + 4) gives −2x; 8 and −3 give 5x; 12 and −2 give 10x.)"}, {"kind": "blank", "p": "Factor and solve x<sup>2</sup> − 3x − 28 = 0.", "tag": "", "marks": "", "flat": [{"t": "x<sup>2</sup> − 3x − 28 = (x − 7)(x + __B1__)", "a": {"B1": "4"}}, {"t": "Solutions: x = __B1__", "a": {"B1": "7, -4"}, "expr": "set"}], "sol": "−7 · 4 = −28 and −7 + 4 = −3.\nx − 7 = 0 or x + 4 = 0, so x = 7 or x = −4."}, {"kind": "mcq", "text": "<b>Error analysis.</b> Kai factored x<sup>2</sup> + x − 12 as (x − 4)(x + 3). What is the correct factorisation?", "opts": ["(x + 4)(x − 3)", "(x + 6)(x − 2)", "(x − 4)(x + 3)", "(x − 12)(x + 1)"], "correct": 0, "tag": "", "sol": "(x − 4)(x + 3) = x<sup>2</sup> − x − 12, so the middle sign is wrong. We need sum +1: 4 + (−3) = 1. (x + 4)(x − 3) = x<sup>2</sup> + x − 12 ✓"}, {"kind": "blank", "p": "Factor x<sup>2</sup> + 11x + 24 using a table of factor pairs of 24.", "tag": "", "marks": "", "flat": [{"t": "1 and 24 have sum 25, 2 and 12 have sum 14, 3 and 8 have sum __B1__", "a": {"B1": "11"}}, {"t": "So x<sup>2</sup> + 11x + 24 = (x + 3)(x + __B1__)", "a": {"B1": "8"}}], "sol": "3 + 8 = 11, which is the middle coefficient.\nCheck: (x + 3)(x + 8) = x<sup>2</sup> + 8x + 3x + 24 = x<sup>2</sup> + 11x + 24 ✓"}, {"kind": "mcq", "text": "A rectangle has area x<sup>2</sup> + 10x + 21 square units and width (x + 3) units. What is its length?", "opts": ["x + 7", "x + 18", "x − 7", "x + 10"], "correct": 0, "tag": "", "sol": "x<sup>2</sup> + 10x + 21 = (x + 3)(x + 7), because 3 · 7 = 21 and 3 + 7 = 10. So the length is x + 7."}, {"kind": "blank", "p": "Solve x<sup>2</sup> + 4x = 21.", "tag": "", "marks": "", "flat": [{"t": "Write it equal to zero: x<sup>2</sup> + 4x − __B1__ = 0", "a": {"B1": "21"}}, {"t": "Solutions: x = __B1__", "a": {"B1": "-7, 3"}, "expr": "set"}], "sol": "Subtract 21 from both sides so the Zero-Product Property can be used.\n(x + 7)(x − 3) = 0, so x = −7 or x = 3. Check: 9 + 12 = 21 ✓"}, {"kind": "mcq", "text": "Which trinomial cannot be factored using integers?", "opts": ["x<sup>2</sup> − 7x + 6", "x<sup>2</sup> + 5x + 8", "x<sup>2</sup> + 2x − 8", "x<sup>2</sup> + 6x + 8"], "correct": 1, "tag": "", "sol": "The factor pairs of 8 are 1, 8 (sum 9) and 2, 4 (sum 6); none has sum 5, so x<sup>2</sup> + 5x + 8 is prime. The others are (x + 2)(x + 4), (x − 1)(x − 6) and (x + 4)(x − 2)."}, {"kind": "blank", "p": "A rectangular patio has an area of 48 m². Its length is 2 m more than its width w, so w(w + 2) = 48.", "tag": "", "marks": "", "flat": [{"t": "w<sup>2</sup> + 2w − 48 = 0 has the solutions w = __B1__", "a": {"B1": "-8, 6"}, "expr": "set"}, {"t": "The width is __B1__ m", "a": {"B1": "6"}}, {"t": "The length is __B1__ m", "a": {"B1": "8"}}], "sol": "(w + 8)(w − 6) = 0, so w = −8 or w = 6.\nA width cannot be negative, so w = 6.\n6 + 2 = 8 m. Check: 6 × 8 = 48 ✓", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 180\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><text class=\"lb\" x=\"150.0\" y=\"10.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">Patio: area 48 m²</text><rect x=\"46.0\" y=\"42\" width=\"180\" height=\"110\" style=\"fill:none;stroke:var(--ink-soft);stroke-width:1.6\"/><text class=\"lb\" x=\"136.0\" y=\"31.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">w + 2</text><text class=\"lb\" x=\"234.0\" y=\"97.0\" text-anchor=\"start\" dominant-baseline=\"middle\">w</text></svg>"}, {"kind": "mcq", "text": "<b>Reasoning.</b> For which value of b can x<sup>2</sup> + bx + 18 be factored using integers?", "opts": ["9", "8", "10", "12"], "correct": 0, "tag": "", "sol": "The positive factor pairs of 18 are 1, 18 (sum 19), 2, 9 (sum 11) and 3, 6 (sum 9). Only 9 is in the list: x<sup>2</sup> + 9x + 18 = (x + 3)(x + 6)."}, {"kind": "blank", "p": "Complete each factorisation.", "tag": "", "marks": "", "flat": [{"t": "x<sup>2</sup> + 7xy + 12y<sup>2</sup> = (x + 3y)(x + __B1__y)", "a": {"B1": "4"}}, {"t": "m<sup>2</sup> − 14m + 48 = (m − 6)(m − __B1__)", "a": {"B1": "8"}}], "sol": "3y · 4y = 12y<sup>2</sup> and 3y + 4y = 7y.\n(−6)(−8) = 48 and −6 + (−8) = −14."}, {"kind": "mcq", "text": "The product of two consecutive positive integers is 72. Write n(n + 1) = 72 and solve. What are the integers?", "opts": ["8 and 9", "7 and 8", "6 and 12", "9 and 10"], "correct": 0, "tag": "", "sol": "n<sup>2</sup> + n − 72 = 0 → (n + 9)(n − 8) = 0 → n = 8 (n = −9 is not positive). The integers are 8 and 9: 8 × 9 = 72 ✓"}]}, {"id": "s6", "label": "7.6 Factoring ax² + bx + c", "sub": "I can factor trinomials with a leading coefficient other than 1, including negative ones, and solve related equations.", "slides": [{"kind": "mcq", "text": "Factor 2x<sup>2</sup> + 7x + 3.", "opts": ["(2x + 1)(x + 3)", "(2x + 6)(x + 1)", "(2x + 3)(x + 1)", "(2x − 1)(x − 3)"], "correct": 0, "tag": "", "sol": "Try (2x + ?)(x + ?) with factors of 3. (2x + 1)(x + 3) = 2x<sup>2</sup> + 6x + x + 3 = 2x<sup>2</sup> + 7x + 3 ✓ ((2x + 3)(x + 1) gives 5x.)"}, {"kind": "blank", "p": "Factor 3x<sup>2</sup> + 10x + 8 by the ac method.", "tag": "", "marks": "", "flat": [{"t": "ac = __B1__", "a": {"B1": "24"}}, {"t": "Two numbers with product 24 and sum 10: __B1__", "a": {"B1": "4, 6"}, "expr": "set"}, {"t": "3x<sup>2</sup> + 10x + 8 = (3x + __B1__)(x + __B2__)", "a": {"B1": "4", "B2": "2"}}], "sol": "a · c = 3 · 8 = 24.\n4 · 6 = 24 and 4 + 6 = 10.\nSplit the middle term: 3x<sup>2</sup> + 6x + 4x + 8 = 3x(x + 2) + 4(x + 2) = (3x + 4)(x + 2)."}, {"kind": "mcq", "text": "Factor 5x<sup>2</sup> − 13x + 6.", "opts": ["(5x − 3)(x − 2)", "(5x − 6)(x − 1)", "(5x − 2)(x − 3)", "(5x + 3)(x + 2)"], "correct": 0, "tag": "", "sol": "c is positive and b is negative, so both numbers are negative. (5x − 3)(x − 2) = 5x<sup>2</sup> − 10x − 3x + 6 = 5x<sup>2</sup> − 13x + 6 ✓ ((5x − 2)(x − 3) gives −17x; (5x − 6)(x − 1) gives −11x.)"}, {"kind": "blank", "p": "Factor and solve 4x<sup>2</sup> + 4x − 3 = 0. Type fractions like 1/2.", "tag": "", "marks": "", "flat": [{"t": "4x<sup>2</sup> + 4x − 3 = (2x + __B1__)(2x − __B2__)", "a": {"B1": "3", "B2": "1"}}, {"t": "The solutions are x = −{3/2} and x = __B1__", "a": {"B1": "1/2"}, "expr": "fv"}], "sol": "ac = −12; the numbers 6 and −2 have sum 4: 4x<sup>2</sup> + 6x − 2x − 3 = 2x(2x + 3) − (2x + 3) = (2x + 3)(2x − 1).\n2x + 3 = 0 gives x = −{3/2}; 2x − 1 = 0 gives x = {1/2}."}, {"kind": "mcq", "text": "<b>Error analysis.</b> Noor factored 2x<sup>2</sup> + 11x + 5 as (2x + 5)(x + 1). What is correct?", "opts": ["(x + 1)(x + 5)", "(2x + 1)(x + 5)", "(2x + 5)(x + 1)", "(2x + 10)(x + 1)"], "correct": 1, "tag": "", "sol": "(2x + 5)(x + 1) = 2x<sup>2</sup> + 7x + 5. The positions of 5 and 1 matter: (2x + 1)(x + 5) = 2x<sup>2</sup> + 10x + x + 5 = 2x<sup>2</sup> + 11x + 5 ✓"}, {"kind": "blank", "p": "Factor 6x<sup>2</sup> + 15x + 9 completely.", "tag": "", "marks": "", "flat": [{"t": "First take out the GCF: 6x<sup>2</sup> + 15x + 9 = __B1__(2x<sup>2</sup> + 5x + 3)", "a": {"B1": "3"}}, {"t": "6x<sup>2</sup> + 15x + 9 = 3(2x + __B1__)(x + __B2__)", "a": {"B1": "3", "B2": "1"}}], "sol": "GCF(6, 15, 9) = 3.\nac = 6, and 2 + 3 = 5: 2x<sup>2</sup> + 2x + 3x + 3 = 2x(x + 1) + 3(x + 1) = (2x + 3)(x + 1)."}, {"kind": "mcq", "text": "Factor −2x<sup>2</sup> + x + 6.", "opts": ["−(2x − 3)(x + 2)", "−(2x + 2)(x − 3)", "−(2x + 3)(x − 2)", "(2x + 3)(x − 2)"], "correct": 2, "tag": "", "sol": "Factor out −1 first: −(2x<sup>2</sup> − x − 6). Then 2x<sup>2</sup> − x − 6 = (2x + 3)(x − 2), so the answer is −(2x + 3)(x − 2). ((2x + 3)(x − 2) without the − sign has leading coefficient +2.)"}, {"kind": "blank", "p": "A rectangle has area 2x<sup>2</sup> + 9x + 4 square feet and width (x + 4) feet.", "tag": "", "marks": "", "flat": [{"t": "Its length is (2x + __B1__) feet", "a": {"B1": "1"}}, {"t": "When x = 5 its perimeter is __B1__ feet", "a": {"B1": "40"}}], "sol": "2x<sup>2</sup> + 9x + 4 = (2x + 1)(x + 4), because 2x · 4 + 1 · x = 9x.\nLength 11 ft and width 9 ft: 2(11) + 2(9) = 40 ft.", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 180\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><text class=\"lb\" x=\"150.0\" y=\"10.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">Area 2x² + 9x + 4</text><rect x=\"46.0\" y=\"42\" width=\"180\" height=\"110\" style=\"fill:none;stroke:var(--ink-soft);stroke-width:1.6\"/><text class=\"lb\" x=\"136.0\" y=\"31.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2x + 1</text><text class=\"lb\" x=\"234.0\" y=\"97.0\" text-anchor=\"start\" dominant-baseline=\"middle\">x + 4</text></svg>"}, {"kind": "mcq", "text": "Solve 3x<sup>2</sup> − 5x − 2 = 0.", "opts": ["x = −{1/3} or x = 2", "x = −3 or x = 2", "x = {1/3} or x = −2", "x = −1 or x = 2"], "correct": 0, "tag": "", "sol": "3x<sup>2</sup> − 5x − 2 = (3x + 1)(x − 2). 3x + 1 = 0 gives x = −{1/3}; x − 2 = 0 gives x = 2. (x = −3 forgets to divide by 3.)"}, {"kind": "blank", "p": "A diver jumps from a platform. Her height after t seconds is h = −16t<sup>2</sup> + 8t + 48 feet.", "tag": "", "marks": "", "flat": [{"t": "−16t<sup>2</sup> + 8t + 48 = −8(2t<sup>2</sup> − t − __B1__)", "a": {"B1": "6"}}, {"t": "= −8(2t + 3)(t − __B1__)", "a": {"B1": "2"}}, {"t": "She reaches the water (h = 0) after t = __B1__ s", "a": {"B1": "2"}}], "sol": "Divide each term by the GCF −8.\n(2t + 3)(t − 2) = 2t<sup>2</sup> − 4t + 3t − 6 = 2t<sup>2</sup> − t − 6 ✓\nt = −{3/2} or t = 2; time cannot be negative, so t = 2 s."}, {"kind": "mcq", "text": "<b>Reasoning.</b> When factoring 6x<sup>2</sup> + 7x + 2 by the ac method, which two numbers are used to split the middle term?", "opts": ["2 and 5", "1 and 6", "3 and 4", "1 and 12"], "correct": 2, "tag": "", "sol": "ac = 12 and b = 7: 3 · 4 = 12 and 3 + 4 = 7. Then 6x<sup>2</sup> + 3x + 4x + 2 = 3x(2x + 1) + 2(2x + 1) = (3x + 2)(2x + 1)."}, {"kind": "blank", "p": "Factor and solve 10x<sup>2</sup> − 11x − 6 = 0. Type fractions like -2/5.", "tag": "", "marks": "", "flat": [{"t": "10x<sup>2</sup> − 11x − 6 = (5x + __B1__)(2x − __B2__)", "a": {"B1": "2", "B2": "3"}}, {"t": "The negative solution is x = __B1__", "a": {"B1": "-2/5"}, "expr": "fv"}, {"t": "The positive solution is x = __B1__", "a": {"B1": "3/2"}, "expr": "fv"}], "sol": "ac = −60; 4 and −15 have sum −11: 10x<sup>2</sup> + 4x − 15x − 6 = 2x(5x + 2) − 3(5x + 2) = (5x + 2)(2x − 3).\n5x + 2 = 0 gives x = −{2/5}.\n2x − 3 = 0 gives x = {3/2}."}, {"kind": "mcq", "text": "A rectangular rug has area 3x<sup>2</sup> + 14x + 8 square feet. One side is (3x + 2) feet. What is the other side?", "opts": ["x + 4", "x + 12", "3x + 4", "x + 6"], "correct": 0, "tag": "", "sol": "(3x + 2)(x + 4) = 3x<sup>2</sup> + 12x + 2x + 8 = 3x<sup>2</sup> + 14x + 8 ✓ So the other side is x + 4 feet."}]}, {"id": "s7", "label": "7.7 Factoring Special Products", "sub": "I can factor differences of two squares and perfect square trinomials.", "slides": [{"kind": "mcq", "text": "Factor x<sup>2</sup> − 81.", "opts": ["(x + 9)(x − 9)", "(x − 9)<sup>2</sup>", "(x + 81)(x − 1)", "(x + 9)<sup>2</sup>"], "correct": 0, "tag": "", "sol": "x<sup>2</sup> − 81 = x<sup>2</sup> − 9<sup>2</sup>, a difference of two squares: a<sup>2</sup> − b<sup>2</sup> = (a + b)(a − b) = (x + 9)(x − 9). ((x − 9)<sup>2</sup> = x<sup>2</sup> − 18x + 81.)"}, {"kind": "blank", "p": "Factor each difference of two squares.", "tag": "", "marks": "", "flat": [{"t": "49y<sup>2</sup> − 16 = (7y + __B1__)(7y − __B2__)", "a": {"B1": "4", "B2": "4"}}, {"t": "36m<sup>2</sup> − 1 = (__B1__m + 1)(__B2__m − 1)", "a": {"B1": "6", "B2": "6"}}], "sol": "49y<sup>2</sup> = (7y)<sup>2</sup> and 16 = 4<sup>2</sup>.\n36m<sup>2</sup> = (6m)<sup>2</sup> and 1 = 1<sup>2</sup>."}, {"kind": "mcq", "text": "Use a difference of squares to find 53<sup>2</sup> − 47<sup>2</sup>.", "opts": ["1000", "600", "36", "6000"], "correct": 1, "tag": "", "sol": "53<sup>2</sup> − 47<sup>2</sup> = (53 + 47)(53 − 47) = 100 × 6 = 600. (36 = 6<sup>2</sup> comes from (53 − 47)<sup>2</sup>.)"}, {"kind": "blank", "p": "Perfect square trinomials.", "tag": "", "marks": "", "flat": [{"t": "x<sup>2</sup> − 18x + 81 = (x − __B1__)<sup>2</sup>", "a": {"B1": "9"}}, {"t": "Is 4x<sup>2</sup> + 10x + 25 a perfect square trinomial? __B1__ (yes / no)", "a": {"B1": "no"}, "expr": "words"}], "sol": "81 = 9<sup>2</sup> and 2 · x · 9 = 18x, so it is (x − 9)<sup>2</sup>.\n4x<sup>2</sup> = (2x)<sup>2</sup> and 25 = 5<sup>2</sup>, but 2 · 2x · 5 = 20x, not 10x. So it is not a perfect square trinomial."}, {"kind": "mcq", "text": "<b>Error analysis.</b> Ravi says x<sup>2</sup> + 36 = (x + 6)(x − 6). Which reply is correct?", "opts": ["x<sup>2</sup> + 36 = (x + 6)<sup>2</sup>, because 6<sup>2</sup> = 36", "He is right, because 6 · 6 = 36 and x · x = x<sup>2</sup>", "x<sup>2</sup> + 36 is prime; (x + 6)(x − 6) = x<sup>2</sup> − 36", "x<sup>2</sup> + 36 = (x − 6)<sup>2</sup>, because (−6)<sup>2</sup> = 36"], "correct": 2, "tag": "", "sol": "(x + 6)(x − 6) = x<sup>2</sup> − 36, a difference. A sum of two squares such as x<sup>2</sup> + 36 cannot be factored over the integers, and (x + 6)<sup>2</sup> = x<sup>2</sup> + 12x + 36."}, {"kind": "blank", "p": "Factor and solve 9m<sup>2</sup> + 30m + 25 = 0. Type fractions like -2/3.", "tag": "", "marks": "", "flat": [{"t": "9m<sup>2</sup> + 30m + 25 = (__B1__m + __B2__)<sup>2</sup>", "a": {"B1": "3", "B2": "5"}}, {"t": "The only solution is m = __B1__", "a": {"B1": "-5/3"}, "expr": "fv"}], "sol": "9m<sup>2</sup> = (3m)<sup>2</sup>, 25 = 5<sup>2</sup> and 2 · 3m · 5 = 30m.\n3m + 5 = 0 gives m = −{5/3} (a repeated solution)."}, {"kind": "mcq", "text": "Which is a perfect square trinomial?", "opts": ["16x<sup>2</sup> − 24x + 9", "16x<sup>2</sup> + 24x − 9", "4x<sup>2</sup> + 24x + 9", "16x<sup>2</sup> − 12x + 9"], "correct": 0, "tag": "", "sol": "16x<sup>2</sup> = (4x)<sup>2</sup>, 9 = 3<sup>2</sup> and 2 · 4x · 3 = 24x, so 16x<sup>2</sup> − 24x + 9 = (4x − 3)<sup>2</sup>. 12x is not twice the product; −9 is not a square; for 4x<sup>2</sup> + … + 9 the middle term would need to be 12x."}, {"kind": "blank", "p": "A stone is dropped from a 64-foot cliff. Its height after t seconds is h = −16t<sup>2</sup> + 64 feet.", "tag": "", "marks": "", "flat": [{"t": "−16t<sup>2</sup> + 64 = −16(t<sup>2</sup> − __B1__)", "a": {"B1": "4"}}, {"t": "= −16(t + 2)(t − 2), so the stone lands after __B1__ s", "a": {"B1": "2"}}], "sol": "Take out the GCF −16: 64 ÷ (−16) = −4.\nt<sup>2</sup> − 4 = (t + 2)(t − 2); t = −2 is not a sensible time, so t = 2 s."}, {"kind": "mcq", "text": "Solve x<sup>2</sup> − 12x + 36 = 0.", "opts": ["x = 6", "x = 6 or x = −6", "x = 36", "x = −6"], "correct": 0, "tag": "", "sol": "x<sup>2</sup> − 12x + 36 = (x − 6)<sup>2</sup>, so x − 6 = 0 and x = 6 (a repeated solution). x = −6 gives 36 + 72 + 36 ≠ 0."}, {"kind": "blank", "p": "A square garden has an area of x<sup>2</sup> + 14x + 49 square metres.", "tag": "", "marks": "", "flat": [{"t": "Each side is (x + __B1__) m", "a": {"B1": "7"}}, {"t": "If the area is 225 m², then x = __B1__", "a": {"B1": "8"}}], "sol": "x<sup>2</sup> + 14x + 49 = (x + 7)<sup>2</sup>.\n(x + 7)<sup>2</sup> = 225 = 15<sup>2</sup> with x + 7 positive, so x + 7 = 15 and x = 8.", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 180\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><text class=\"lb\" x=\"150.0\" y=\"10.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">Square garden: area x² + 14x + 49</text><rect x=\"46.0\" y=\"42\" width=\"180\" height=\"110\" style=\"fill:none;stroke:var(--ink-soft);stroke-width:1.6\"/><text class=\"lb\" x=\"136.0\" y=\"31.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">x + 7</text><text class=\"lb\" x=\"234.0\" y=\"97.0\" text-anchor=\"start\" dominant-baseline=\"middle\">x + 7</text></svg>"}, {"kind": "mcq", "text": "<b>Reasoning.</b> For which value of c is x<sup>2</sup> + 10x + c a perfect square trinomial?", "opts": ["100", "5", "25", "10"], "correct": 2, "tag": "", "sol": "(x + b)<sup>2</sup> = x<sup>2</sup> + 2bx + b<sup>2</sup>. Here 2b = 10, so b = 5 and c = b<sup>2</sup> = 25: x<sup>2</sup> + 10x + 25 = (x + 5)<sup>2</sup>."}, {"kind": "blank", "p": "Factor 3x<sup>2</sup> − 75 completely, then solve 3x<sup>2</sup> − 75 = 0.", "tag": "", "marks": "", "flat": [{"t": "3x<sup>2</sup> − 75 = 3(x<sup>2</sup> − __B1__)", "a": {"B1": "25"}}, {"t": "= 3(x + __B1__)(x − 5)", "a": {"B1": "5"}}, {"t": "Solutions: x = __B1__", "a": {"B1": "-5, 5"}, "expr": "set"}], "sol": "The GCF is 3.\nx<sup>2</sup> − 25 is a difference of two squares: (x + 5)(x − 5).\nx + 5 = 0 or x − 5 = 0."}, {"kind": "mcq", "text": "A square tile of side 14 cm has a square of side 6 cm cut from one corner. The remaining area is 14<sup>2</sup> − 6<sup>2</sup>. What is it?", "opts": ["80 cm²", "64 cm²", "160 cm²", "232 cm²"], "correct": 2, "tag": "", "sol": "14<sup>2</sup> − 6<sup>2</sup> = (14 + 6)(14 − 6) = 20 × 8 = 160 cm². Check: 196 − 36 = 160 ✓ (64 = (14 − 6)<sup>2</sup>; 232 adds the areas.)"}]}, {"id": "s8", "label": "7.8 Factoring Polynomials Completely", "sub": "I can factor by grouping, factor polynomials completely and solve equations by factoring completely.", "slides": [{"kind": "mcq", "text": "Factor x<sup>3</sup> + 4x<sup>2</sup> + 3x + 12 by grouping.", "opts": ["(x + 4)(x<sup>2</sup> + 3)", "x(x + 4)(x + 3)", "(x + 3)(x<sup>2</sup> + 4)", "(x + 4)(x<sup>2</sup> − 3)"], "correct": 0, "tag": "", "sol": "Group: x<sup>2</sup>(x + 4) + 3(x + 4) = (x + 4)(x<sup>2</sup> + 3). ((x + 3)(x<sup>2</sup> + 4) = x<sup>3</sup> + 3x<sup>2</sup> + 4x + 12.)"}, {"kind": "blank", "p": "Factor y<sup>3</sup> − 2y<sup>2</sup> − 5y + 10 by grouping.", "tag": "", "marks": "", "flat": [{"t": "y<sup>2</sup>(y − 2) − 5(y − __B1__)", "a": {"B1": "2"}}, {"t": "= (y − 2)(y<sup>2</sup> − __B1__)", "a": {"B1": "5"}}], "sol": "From the second pair take out −5: −5y + 10 = −5(y − 2).\nThe common binomial is (y − 2). y<sup>2</sup> − 5 cannot be factored with integers, so this is complete."}, {"kind": "mcq", "text": "Which shows 2x<sup>3</sup> − 18x factored completely?", "opts": ["2x(x + 3)(x − 3)", "x(2x<sup>2</sup> − 18)", "2x(x<sup>2</sup> − 9)", "(2x<sup>2</sup> + 6x)(x − 3)"], "correct": 0, "tag": "", "sol": "2x<sup>3</sup> − 18x = 2x(x<sup>2</sup> − 9) = 2x(x + 3)(x − 3). All four expressions are equal, but only the first has no factor that can be factored further."}, {"kind": "blank", "p": "Factor 3x<sup>3</sup> − 12x completely, then solve 3x<sup>3</sup> − 12x = 0.", "tag": "", "marks": "", "flat": [{"t": "3x<sup>3</sup> − 12x = 3x(x<sup>2</sup> − __B1__)", "a": {"B1": "4"}}, {"t": "= 3x(x + 2)(x − __B1__)", "a": {"B1": "2"}}, {"t": "Solutions: x = __B1__", "a": {"B1": "-2, 0, 2"}, "expr": "set"}], "sol": "The GCF is 3x.\nx<sup>2</sup> − 4 is a difference of two squares.\n3x = 0, x + 2 = 0 or x − 2 = 0."}, {"kind": "mcq", "text": "<b>Error analysis.</b> Ana factored 2x<sup>3</sup> − 8x<sup>2</sup> − 10x as x(2x<sup>2</sup> − 8x − 10) and stopped. What should she have written?", "opts": ["2x(x<sup>2</sup> − 4x − 5)", "x(2x − 10)(x + 1)", "2x(x + 5)(x − 1)", "2x(x − 5)(x + 1)"], "correct": 3, "tag": "", "sol": "The GCF is 2x, not x: 2x(x<sup>2</sup> − 4x − 5). Then −5 · 1 = −5 and −5 + 1 = −4, so x<sup>2</sup> − 4x − 5 = (x − 5)(x + 1). Complete: 2x(x − 5)(x + 1). (x(2x − 10)(x + 1) still has a common factor 2 inside.)"}, {"kind": "blank", "p": "Factor 4x<sup>3</sup> + 12x<sup>2</sup> + 9x completely, then solve 4x<sup>3</sup> + 12x<sup>2</sup> + 9x = 0. Type fractions like -3/2.", "tag": "", "marks": "", "flat": [{"t": "4x<sup>3</sup> + 12x<sup>2</sup> + 9x = x(2x + __B1__)<sup>2</sup>", "a": {"B1": "3"}}, {"t": "The solutions are x = 0 and x = __B1__", "a": {"B1": "-3/2"}, "expr": "fv"}], "sol": "Take out x: x(4x<sup>2</sup> + 12x + 9), and 4x<sup>2</sup> + 12x + 9 = (2x + 3)<sup>2</sup> because 2 · 2x · 3 = 12x.\n2x + 3 = 0 gives x = −{3/2} (a repeated root)."}, {"kind": "mcq", "text": "Which polynomial is prime?", "opts": ["x<sup>3</sup> + 9x", "x<sup>2</sup> − 9", "x<sup>2</sup> + 6x + 9", "x<sup>2</sup> + 9"], "correct": 3, "tag": "", "sol": "x<sup>2</sup> + 9 is a sum of two squares and has no integer factors. x<sup>2</sup> − 9 = (x + 3)(x − 3), x<sup>2</sup> + 6x + 9 = (x + 3)<sup>2</sup> and x<sup>3</sup> + 9x = x(x<sup>2</sup> + 9)."}, {"kind": "blank", "p": "A box has volume V = x<sup>3</sup> + 6x<sup>2</sup> + 8x cubic centimetres, where x is its height.", "tag": "", "marks": "", "flat": [{"t": "x<sup>3</sup> + 6x<sup>2</sup> + 8x = x(x<sup>2</sup> + 6x + __B1__)", "a": {"B1": "8"}}, {"t": "= x(x + 2)(x + __B1__)", "a": {"B1": "4"}}, {"t": "When x = 2, the volume is __B1__ cm³", "a": {"B1": "48"}}], "sol": "Take out the GCF x.\n2 · 4 = 8 and 2 + 4 = 6.\nThe box is 2 cm by 4 cm by 6 cm: 2 × 4 × 6 = 48 cm³.", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 190\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><text class=\"lb\" x=\"150.0\" y=\"10.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">Volume x³ + 6x² + 8x</text><rect x=\"60\" y=\"70\" width=\"140\" height=\"90\" style=\"stroke:var(--ink-soft);stroke-width:1.6;fill:none\"/><polyline points=\"60,70 100,42.0 240,42.0 240,132.0 200,160\" style=\"stroke:var(--ink-soft);stroke-width:1.6;fill:none\"/><line x1=\"200\" y1=\"70\" x2=\"240\" y2=\"42.0\" style=\"stroke:var(--ink-soft);stroke-width:1.6;fill:none\"/><text class=\"lb\" x=\"130.0\" y=\"174.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">x + 4</text><text class=\"lb\" x=\"230.0\" y=\"150.0\" text-anchor=\"start\" dominant-baseline=\"middle\">x + 2</text><text class=\"lb\" x=\"52.0\" y=\"115.0\" text-anchor=\"end\" dominant-baseline=\"middle\">x</text></svg>"}, {"kind": "mcq", "text": "Solve x<sup>3</sup> + 2x<sup>2</sup> − 9x − 18 = 0.", "opts": ["x = 2, x = −3 or x = 3", "x = −2 or x = 9", "x = −3, x = −2 or x = 3", "x = −2 or x = 3"], "correct": 2, "tag": "", "sol": "Group: x<sup>2</sup>(x + 2) − 9(x + 2) = (x + 2)(x<sup>2</sup> − 9) = (x + 2)(x + 3)(x − 3) = 0, so x = −2, −3 or 3. (x = 9 forgets to factor x<sup>2</sup> − 9.)"}, {"kind": "blank", "p": "Factor 5x<sup>4</sup> − 80 completely, then find its real solutions.", "tag": "", "marks": "", "flat": [{"t": "5x<sup>4</sup> − 80 = 5(x<sup>4</sup> − __B1__)", "a": {"B1": "16"}}, {"t": "= 5(x<sup>2</sup> + 4)(x<sup>2</sup> − __B1__)", "a": {"B1": "4"}}, {"t": "Real solutions of 5x<sup>4</sup> − 80 = 0: x = __B1__", "a": {"B1": "-2, 2"}, "expr": "set"}], "sol": "The GCF is 5.\nx<sup>4</sup> − 16 = (x<sup>2</sup>)<sup>2</sup> − 4<sup>2</sup> = (x<sup>2</sup> + 4)(x<sup>2</sup> − 4).\nx<sup>2</sup> − 4 = (x + 2)(x − 2), while x<sup>2</sup> + 4 is never 0 for real x. So x = −2 or x = 2."}, {"kind": "mcq", "text": "A box has volume V = 2x<sup>3</sup> + 10x<sup>2</sup> + 12x. Which could be its three dimensions?", "opts": ["2x, x + 2 and x + 3", "2x, x + 1 and x + 6", "x, x + 2 and x + 6", "2x, x + 4 and x + 3"], "correct": 0, "tag": "", "sol": "2x<sup>3</sup> + 10x<sup>2</sup> + 12x = 2x(x<sup>2</sup> + 5x + 6) = 2x(x + 2)(x + 3). The others multiply to x<sup>3</sup> + 8x<sup>2</sup> + 12x, 2x<sup>3</sup> + 14x<sup>2</sup> + 12x and 2x<sup>3</sup> + 14x<sup>2</sup> + 24x."}, {"kind": "blank", "p": "A jewellery box has volume V = x<sup>3</sup> + 3x<sup>2</sup> − 4x − 12 cubic centimetres.", "tag": "", "marks": "", "flat": [{"t": "Grouping: x<sup>2</sup>(x + 3) − 4(x + 3) = (x + 3)(x<sup>2</sup> − __B1__)", "a": {"B1": "4"}}, {"t": "The dimensions are (x + 3), (x + 2) and (x − __B1__) cm", "a": {"B1": "2"}}, {"t": "When x = 4, V = __B1__ cm³", "a": {"B1": "84"}}], "sol": "Take x<sup>2</sup> from the first pair and −4 from the second.\nx<sup>2</sup> − 4 = (x + 2)(x − 2).\n7 × 6 × 2 = 84 cm³. Check: 64 + 48 − 16 − 12 = 84 ✓"}, {"kind": "mcq", "text": "<b>Reasoning.</b> What is the best first step for factoring 12x<sup>2</sup> − 27 completely?", "opts": ["Use the difference of two squares straight away", "Factor by grouping", "Use the ac method with ac = −324", "Factor out the GCF 3"], "correct": 3, "tag": "", "sol": "12 and 27 are not perfect squares, but both are multiples of 3: 12x<sup>2</sup> − 27 = 3(4x<sup>2</sup> − 9) = 3(2x + 3)(2x − 3). Always look for a GCF first."}]}, {"id": "s9", "label": "Assessment A", "sub": "Knowing and understanding", "slides": [{"kind": "mcq", "text": "Simplify (3x<sup>2</sup> − 4x + 1) − (x<sup>2</sup> + 2x − 5).", "opts": ["4x<sup>2</sup> − 2x − 4", "2x<sup>2</sup> − 2x − 4", "2x<sup>2</sup> − 6x − 4", "2x<sup>2</sup> − 6x + 6"], "correct": 3, "tag": "", "sol": "Change every sign of the second polynomial and add: 3x<sup>2</sup> − 4x + 1 − x<sup>2</sup> − 2x + 5 = 2x<sup>2</sup> − 6x + 6."}, {"kind": "blank", "p": "Multiply.", "tag": "", "marks": "", "flat": [{"t": "(2x − 3)(x + 5) = 2x<sup>2</sup> + __B1__x − 15", "a": {"B1": "7"}}, {"t": "(x + 9)<sup>2</sup> = x<sup>2</sup> + __B1__x + 81", "a": {"B1": "18"}}], "sol": "FOIL: 2x<sup>2</sup> + 10x − 3x − 15 = 2x<sup>2</sup> + 7x − 15.\nSquare of a binomial: 2 · 9 · x = 18x."}, {"kind": "mcq", "text": "Factor x<sup>2</sup> − 10x + 21.", "opts": ["(x − 3)(x + 7)", "(x − 3)(x − 7)", "(x − 1)(x − 21)", "(x + 3)(x + 7)"], "correct": 1, "tag": "", "sol": "Product 21, sum −10: −3 and −7. (x − 3)(x − 7) = x<sup>2</sup> − 7x − 3x + 21 ✓"}, {"kind": "blank", "p": "Solve (x + 5)(3x − 2) = 0. Type fractions like 2/3.", "tag": "", "marks": "", "flat": [{"t": "x + 5 = 0 gives x = __B1__", "a": {"B1": "-5"}}, {"t": "3x − 2 = 0 gives x = __B1__", "a": {"B1": "2/3"}, "expr": "fv"}], "sol": "x = −5.\n3x = 2, so x = {2/3}."}, {"kind": "mcq", "text": "Factor 4x<sup>2</sup> − 25.", "opts": ["(4x − 5)(x + 5)", "(2x + 25)(2x − 1)", "(2x − 5)<sup>2</sup>", "(2x + 5)(2x − 5)"], "correct": 3, "tag": "", "sol": "4x<sup>2</sup> − 25 = (2x)<sup>2</sup> − 5<sup>2</sup> = (2x + 5)(2x − 5)."}, {"kind": "blank", "p": "Factor 3x<sup>2</sup> + 11x − 4.", "tag": "", "marks": "", "flat": [{"t": "3x<sup>2</sup> + 11x − 4 = (3x − __B1__)(x + __B2__)", "a": {"B1": "1", "B2": "4"}}], "sol": "ac = −12; 12 and −1 have sum 11: 3x<sup>2</sup> + 12x − x − 4 = 3x(x + 4) − (x + 4) = (3x − 1)(x + 4)."}, {"kind": "mcq", "text": "Which shows 5x<sup>3</sup> − 20x factored completely?", "opts": ["x(5x<sup>2</sup> − 20)", "5x(x<sup>2</sup> − 4)", "5x(x + 2)(x − 2)", "5x(x − 2)<sup>2</sup>"], "correct": 2, "tag": "", "sol": "GCF 5x: 5x(x<sup>2</sup> − 4), then x<sup>2</sup> − 4 = (x + 2)(x − 2). Only 5x(x + 2)(x − 2) is complete; 5x(x − 2)<sup>2</sup> is not even equal to 5x<sup>3</sup> − 20x."}, {"kind": "blank", "p": "Solve x<sup>2</sup> + x − 30 = 0.", "tag": "", "marks": "", "flat": [{"t": "x<sup>2</sup> + x − 30 = (x + 6)(x − __B1__)", "a": {"B1": "5"}}, {"t": "Solutions: x = __B1__", "a": {"B1": "-6, 5"}, "expr": "set"}], "sol": "6 · (−5) = −30 and 6 + (−5) = 1.\nx + 6 = 0 or x − 5 = 0."}, {"kind": "mcq", "text": "Solve 4x<sup>2</sup> = 20x.", "opts": ["x = 0 or x = −5", "x = 5 only", "x = 4 or x = 5", "x = 0 or x = 5"], "correct": 3, "tag": "", "sol": "4x<sup>2</sup> − 20x = 0 → 4x(x − 5) = 0 → x = 0 or x = 5. Dividing by x would lose x = 0."}]}, {"id": "s10", "label": "Assessment B", "sub": "Investigating patterns", "slides": [{"kind": "blank", "p": "(x + 1)<sup>2</sup> = x<sup>2</sup> + 2x + 1, (x + 2)<sup>2</sup> = x<sup>2</sup> + 4x + 4, … Continue the pattern.", "tag": "", "marks": "", "flat": [{"t": "(x + 3)<sup>2</sup> = x<sup>2</sup> + __B1__x + __B2__", "a": {"B1": "6", "B2": "9"}}, {"t": "(x + 10)<sup>2</sup> = x<sup>2</sup> + __B1__x + __B2__", "a": {"B1": "20", "B2": "100"}}], "sol": "The middle coefficient is twice the number and the constant is its square: 2 · 3 = 6 and 3<sup>2</sup> = 9.\n2 · 10 = 20 and 10<sup>2</sup> = 100."}, {"kind": "mcq", "text": "9 × 11 = 99, 19 × 21 = 399, 29 × 31 = 899. What is 39 × 41, and why?", "opts": ["1601, because (40 + 1)<sup>2</sup> = 1601", "1599, because (40 − 1)(40 + 1) = 40<sup>2</sup> − 1", "1600, because 40 × 40 = 1600", "1499, because the answers go up by 500"], "correct": 1, "tag": "", "sol": "Each product is (10n − 1)(10n + 1) = (10n)<sup>2</sup> − 1: 100 − 1, 400 − 1, 900 − 1, so 39 × 41 = 1600 − 1 = 1599. (The jumps are 300, 500, 700, …)"}, {"kind": "blank", "p": "4<sup>2</sup> − 3<sup>2</sup> = 7, 5<sup>2</sup> − 4<sup>2</sup> = 9, 6<sup>2</sup> − 5<sup>2</sup> = 11, …", "tag": "", "marks": "", "flat": [{"t": "In general, (n + 1)<sup>2</sup> − n<sup>2</sup> = __B1__n + __B2__", "a": {"B1": "2", "B2": "1"}}, {"t": "So 51<sup>2</sup> − 50<sup>2</sup> = __B1__", "a": {"B1": "101"}}], "sol": "n<sup>2</sup> + 2n + 1 − n<sup>2</sup> = 2n + 1.\n2(50) + 1 = 101."}, {"kind": "mcq", "text": "x<sup>2</sup> + bx + 12 is factored with positive integers. Which list gives all possible values of b?", "opts": ["12, 6, 4", "13, 8, 7, 6", "13, 8, 7", "7 only"], "correct": 2, "tag": "", "sol": "The positive factor pairs of 12 are 1, 12; 2, 6; 3, 4 with sums 13, 8 and 7."}, {"kind": "blank", "p": "For which positive values of c can x<sup>2</sup> + 5x + c be factored using integers?", "tag": "", "marks": "", "flat": [{"t": "c = 6 works: x<sup>2</sup> + 5x + 6 = (x + 2)(x + __B1__)", "a": {"B1": "3"}}, {"t": "The only other positive value of c that works is __B1__", "a": {"B1": "4"}}], "sol": "2 · 3 = 6 and 2 + 3 = 5.\nThe numbers must add to 5. With positive integers the only pairs are 1, 4 and 2, 3, giving c = 4 or c = 6: x<sup>2</sup> + 5x + 4 = (x + 1)(x + 4)."}, {"kind": "mcq", "text": "(x − 1)(x + 1) = x<sup>2</sup> − 1, (x − 1)(x<sup>2</sup> + x + 1) = x<sup>3</sup> − 1. What is (x − 1)(x<sup>3</sup> + x<sup>2</sup> + x + 1)?", "opts": ["x<sup>4</sup> − 1", "x<sup>4</sup> + 1", "x<sup>3</sup> − 1", "x<sup>4</sup> − x − 1"], "correct": 0, "tag": "", "sol": "x(x<sup>3</sup> + x<sup>2</sup> + x + 1) − (x<sup>3</sup> + x<sup>2</sup> + x + 1) = x<sup>4</sup> + x<sup>3</sup> + x<sup>2</sup> + x − x<sup>3</sup> − x<sup>2</sup> − x − 1 = x<sup>4</sup> − 1. All the middle terms cancel."}, {"kind": "blank", "p": "Count the products before combining like terms.", "tag": "", "marks": "", "flat": [{"t": "Binomial × binomial: 4 products. Binomial × trinomial: __B1__ products", "a": {"B1": "6"}}, {"t": "Trinomial × trinomial: __B1__ products", "a": {"B1": "9"}}], "sol": "Each of the 2 terms multiplies each of the 3 terms: 2 × 3 = 6.\n3 × 3 = 9."}, {"kind": "mcq", "text": "2<sup>2</sup> + 2 = 6, 3<sup>2</sup> + 3 = 12, 4<sup>2</sup> + 4 = 20. Why is n<sup>2</sup> + n always even for a whole number n?", "opts": ["It is not always even: it is odd whenever n is odd", "n<sup>2</sup> and n are always both even, so their sum is even", "n<sup>2</sup> + n = 2n, and every multiple of 2 is even", "n<sup>2</sup> + n = n(n + 1), and one of two consecutive integers is even"], "correct": 3, "tag": "", "sol": "Factor: n<sup>2</sup> + n = n(n + 1). Of n and n + 1 one is even, so the product is even. (n<sup>2</sup> is odd when n is odd, and n<sup>2</sup> + n ≠ 2n.)"}, {"kind": "blank", "p": "(x − 2)(x + 2) = x<sup>2</sup> − 4, (x − 3)(x + 3) = x<sup>2</sup> − 9, …", "tag": "", "marks": "", "flat": [{"t": "(x − k)(x + k) = x<sup>2</sup> − __B1__", "a": {"B1": "k^2"}, "expr": true, "accept": ["k*k", "kk"]}, {"t": "Use it: 98 × 102 = __B1__", "a": {"B1": "9996"}, "accept": ["9,996"]}], "sol": "The outer and inner products −kx and +kx cancel, leaving x<sup>2</sup> − k<sup>2</sup>.\n(100 − 2)(100 + 2) = 10000 − 4 = 9996."}]}, {"id": "s11", "label": "Assessment C", "sub": "Communicating", "slides": [{"kind": "mcq", "text": "A polynomial of degree 1 or more that cannot be written as a product of polynomials of lower degree with integer coefficients is called", "opts": ["a perfect square trinomial", "a monomial", "a prime polynomial", "a factored form"], "correct": 2, "tag": "", "sol": "For example, x<sup>2</sup> + 4 and x<sup>2</sup> + x + 1 are prime polynomials."}, {"kind": "blank", "p": "Complete the definitions.", "tag": "", "marks": "", "flat": [{"t": "In ax<sup>2</sup> + bx + c written in standard form, a is called the leading __B1__.", "a": {"B1": "coefficient"}, "expr": "words"}, {"t": "A polynomial with three terms is called a __B1__.", "a": {"B1": "trinomial"}, "expr": "words"}], "sol": "The leading coefficient is the coefficient of the term with the greatest degree.\nMono = 1 term, bi = 2 terms, tri = 3 terms."}, {"kind": "mcq", "text": "<b>Error analysis.</b> Sam solved (x − 2)(x + 5) = 8 by writing x − 2 = 8 or x + 5 = 8. What is correct?", "opts": ["Set each factor equal to 0 instead, so x = 2 or x = −5", "Make one side 0: x<sup>2</sup> + 3x − 18 = 0, so x = −6 or x = 3", "Sam is right: x − 2 = 8 or x + 5 = 8, so x = 10 or x = 3", "Use 2 · 4 = 8: x − 2 = 2 or x + 5 = 4, so x = 4 or x = −1"], "correct": 1, "tag": "", "sol": "The Zero-Product Property only works for a product equal to 0. Expand: x<sup>2</sup> + 3x − 10 = 8 → x<sup>2</sup> + 3x − 18 = 0 → (x + 6)(x − 3) = 0 → x = −6 or 3. Check: (−8)(−1) = 8 ✓ and (1)(8) = 8 ✓"}, {"kind": "blank", "p": "Explain how to solve x<sup>2</sup> = 6x.", "tag": "", "marks": "", "flat": [{"t": "Subtract 6x and factor: x(x − __B1__) = 0", "a": {"B1": "6"}}, {"t": "By the Zero-Product Property, x = __B1__", "a": {"B1": "0, 6"}, "expr": "set"}], "sol": "x<sup>2</sup> − 6x = 0 and the GCF is x.\nx = 0 or x − 6 = 0."}, {"kind": "mcq", "text": "Which statement of the Zero-Product Property is correct?", "opts": ["If ab = 0, then a = 0 or b = 0", "If ab = 6, then a = 6 or b = 6", "If a + b = 0, then a = 0 or b = 0", "If ab = 0, then a = 0 and b = 0"], "correct": 0, "tag": "", "sol": "A product is zero only when at least one factor is zero. It works only for 0 (2 × 3 = 6 with neither factor 6), and both factors need not be zero (0 × 5 = 0)."}, {"kind": "blank", "p": "Describe each binomial.", "tag": "", "marks": "", "flat": [{"t": "x<sup>2</sup> − 49 is a difference of two __B1__.", "a": {"B1": "squares"}, "expr": "words", "accept": ["square", "perfect squares"]}, {"t": "x<sup>2</sup> + 49 is __B1__ (prime / factorable).", "a": {"B1": "prime"}, "expr": "words"}], "sol": "x<sup>2</sup> − 49 = x<sup>2</sup> − 7<sup>2</sup> = (x + 7)(x − 7).\nA sum of two squares has no factors with integer coefficients."}, {"kind": "mcq", "text": "<b>Error analysis.</b> Lena wrote (3x + 2)<sup>2</sup> = 9x<sup>2</sup> + 6x + 4. What is her mistake?", "opts": ["The last term should be 2", "The middle term should be 2(3x)(2) = 12x", "The first term should be 3x<sup>2</sup>", "There is no mistake"], "correct": 1, "tag": "", "sol": "(3x + 2)<sup>2</sup> = 9x<sup>2</sup> + 2(3x)(2) + 4 = 9x<sup>2</sup> + 12x + 4. Lena forgot the factor 2 in 2ab."}, {"kind": "blank", "p": "Explain how to factor 6x<sup>2</sup> + 11x + 4 by the ac method.", "tag": "", "marks": "", "flat": [{"t": "ac = __B1__", "a": {"B1": "24"}}, {"t": "The two numbers with product 24 and sum 11: __B1__", "a": {"B1": "3, 8"}, "expr": "set"}, {"t": "6x<sup>2</sup> + 11x + 4 = (2x + 1)(3x + __B1__)", "a": {"B1": "4"}}], "sol": "a · c = 6 · 4 = 24.\n3 · 8 = 24 and 3 + 8 = 11.\n6x<sup>2</sup> + 3x + 8x + 4 = 3x(2x + 1) + 4(2x + 1) = (2x + 1)(3x + 4)."}, {"kind": "mcq", "text": "Which description fits 5x<sup>3</sup> − 2x + 7?", "opts": ["Cubic trinomial with leading coefficient 5", "Cubic trinomial with leading coefficient 7", "Cubic binomial with leading coefficient 7", "Quadratic trinomial with leading coefficient 5"], "correct": 0, "tag": "", "sol": "The greatest degree is 3 (cubic), there are three terms (trinomial) and the leading term is 5x<sup>3</sup>."}]}, {"id": "s12", "label": "Assessment D", "sub": "Applying mathematics in real-life contexts", "slides": [{"kind": "mcq", "text": "A rectangular plot is (2x + 3) m long and (x − 1) m wide. Which expression gives its area?", "opts": ["2x<sup>2</sup> + 5x − 3", "3x + 2", "2x<sup>2</sup> + x − 3", "2x<sup>2</sup> − 3"], "correct": 2, "tag": "", "sol": "(2x + 3)(x − 1) = 2x<sup>2</sup> − 2x + 3x − 3 = 2x<sup>2</sup> + x − 3. (3x + 2 adds the sides.)"}, {"kind": "blank", "p": "A ball is thrown from a 64-foot roof. Its height after t seconds is h = −16t<sup>2</sup> + 48t + 64 feet.", "tag": "", "marks": "", "flat": [{"t": "−16t<sup>2</sup> + 48t + 64 = −16(t − __B1__)(t + 1)", "a": {"B1": "4"}}, {"t": "The ball hits the ground after __B1__ s", "a": {"B1": "4"}}], "sol": "−16(t<sup>2</sup> − 3t − 4), and t<sup>2</sup> − 3t − 4 = (t − 4)(t + 1).\nh = 0 at t = 4 or t = −1; time is positive, so t = 4 s."}, {"kind": "mcq", "text": "A 12 in by 8 in picture has a border of width x inches all round. The total area is 140 in², so (12 + 2x)(8 + 2x) = 140. How wide is the border?", "opts": ["3.5 in", "11 in", "2 in", "1 in"], "correct": 3, "tag": "", "sol": "4x<sup>2</sup> + 40x + 96 = 140 → 4x<sup>2</sup> + 40x − 44 = 0 → x<sup>2</sup> + 10x − 11 = 0 → (x + 11)(x − 1) = 0, so x = 1 (a width cannot be −11). Check: 14 × 10 = 140 ✓"}, {"kind": "blank", "p": "A square garden has sides of x m. One side is made 4 m longer and the other 2 m longer.", "tag": "", "marks": "", "flat": [{"t": "The new area is (x + 4)(x + 2) = x<sup>2</sup> + __B1__x + 8 m²", "a": {"B1": "6"}}, {"t": "If the new area is 80 m², then x = __B1__", "a": {"B1": "6"}}], "sol": "FOIL: x<sup>2</sup> + 2x + 4x + 8.\nx<sup>2</sup> + 6x + 8 = 80 → x<sup>2</sup> + 6x − 72 = 0 → (x + 12)(x − 6) = 0, so x = 6 m. Check: 10 × 8 = 80 ✓"}, {"kind": "mcq", "text": "A diver leaves a 10 m platform. Her height after t seconds is h = −5t<sup>2</sup> + 5t + 10 metres, which factors as −5(t − 2)(t + 1). When does she reach the water?", "opts": ["After 1 s", "After 5 s", "After 2 s", "After 10 s"], "correct": 2, "tag": "", "sol": "h = 0 when t = 2 or t = −1. Time cannot be negative, so after 2 s. Check: −20 + 10 + 10 = 0 ✓"}, {"kind": "blank", "p": "A box is x cm wide, (x + 5) cm long and 3 cm high.", "tag": "", "marks": "", "flat": [{"t": "Volume V = __B1__x<sup>2</sup> + __B2__x cm³", "a": {"B1": "3", "B2": "15"}}, {"t": "If V = 150 cm³, then x = __B1__", "a": {"B1": "5"}}], "sol": "V = 3x(x + 5) = 3x<sup>2</sup> + 15x.\n3x<sup>2</sup> + 15x − 150 = 0 → 3(x<sup>2</sup> + 5x − 50) = 0 → 3(x + 10)(x − 5) = 0, so x = 5. Check: 5 × 10 × 3 = 150 ✓"}, {"kind": "mcq", "text": "<b>Is this reasonable?</b> A rectangle is 3 m longer than it is wide and has area 40 m². Raj solves w(w + 3) = 40 and says, “The width is −8 m or 5 m.” What should he conclude?", "opts": ["Both are reasonable, because both make w(w + 3) = 40 true", "Neither answer is reasonable, because 40 is not a square number", "Only 5 m is reasonable, because a width cannot be negative", "Only −8 m is reasonable, because it has the larger size"], "correct": 2, "tag": "", "sol": "w<sup>2</sup> + 3w − 40 = 0 → (w + 8)(w − 5) = 0 gives w = −8 or w = 5. Both solve the equation, but a length must be positive, so the width is 5 m and the length 8 m (5 × 8 = 40 ✓)."}, {"kind": "blank", "p": "Two square rooms have sides x m and (x + 6) m. The larger room has 84 m² more floor area.", "tag": "", "marks": "", "flat": [{"t": "(x + 6)<sup>2</sup> − x<sup>2</sup> = __B1__x + 36", "a": {"B1": "12"}}, {"t": "x = __B1__", "a": {"B1": "4"}}], "sol": "x<sup>2</sup> + 12x + 36 − x<sup>2</sup> = 12x + 36.\n12x + 36 = 84 → 12x = 48 → x = 4. Check: 10<sup>2</sup> − 4<sup>2</sup> = 100 − 16 = 84 ✓"}, {"kind": "mcq", "text": "A theatre sells (200 + 10x) tickets when the price is $(30 − x). Which expression gives its revenue?", "opts": ["10x<sup>2</sup> + 100x + 6000", "−10x<sup>2</sup> + 100x + 6000", "6000 − 10x<sup>2</sup>", "−10x<sup>2</sup> + 500x + 6000"], "correct": 1, "tag": "", "sol": "(200 + 10x)(30 − x) = 6000 − 200x + 300x − 10x<sup>2</sup> = −10x<sup>2</sup> + 100x + 6000."}]}];
/* ================= build slide lists ================= */
var SLIDES = {}; SECTIONS.forEach(function(sec){ SLIDES[sec.id]=sec.slides; });
var TAB_DEFS = SECTIONS.map(function(sec){ return {id:sec.id, label:sec.label, sub:sec.sub}; });

/* ================= state ================= */
function blankItem(slide){
  if(slide.kind==='mcq'||slide.kind==='ar'){
    return {status:'unanswered', attempts:0, choice:undefined};
  }
  return {status:'unanswered', curStep:0, stepStates: slide.flat.map(function(){ return {status:'unanswered', attempts:0, inputs:{}}; })};
}
function defaultState(){
  var s={tabs:{}};
  TAB_DEFS.forEach(function(td){
    s.tabs[td.id] = { idx:0, maxReached:0, items: SLIDES[td.id].map(function(sl){ return blankItem(sl); }) };
  });
  return s;
}
var appState = {mode:null, learning:null, quiz:null};
var state = null;      // alias for appState[appState.mode]
var MODE = null;
var activeTab=TAB_DEFS[0].id;

function setMode(m){
  appState.mode = m;
  if(!appState[m]) appState[m] = defaultState();
  state = appState[m];
  MODE = m;
}
/* ================= student accounts (saved on this device) ================= */
var SHEET_KEY='sopaan-bim-ch7';
var ACC_KEY='sopaan-students-v1';
var storageOK=true;
var MEM={};
function lsGet(k){ var r=null; try{ r=localStorage.getItem(k); }catch(e){ storageOK=false; }
  if(r===null||r===undefined) r=MEM[k]||null; try{ return r?JSON.parse(r):null; }catch(e){ return null; } }
function lsSet(k,v){ var j=JSON.stringify(v); MEM[k]=j; try{ localStorage.setItem(k,j); return true; }catch(e){ storageOK=false; return false; } }
try{ localStorage.setItem('sopaan-probe','1'); localStorage.removeItem('sopaan-probe'); }catch(e){ storageOK=false; }
function hashPin(pin,salt){ var h=2166136261, str=salt+'|'+pin; for(var i=0;i<str.length;i++){ h^=str.charCodeAt(i); h=Math.imul(h,16777619)>>>0; } return h.toString(36); }
function accKey(name,roll){ return (name.trim().toLowerCase().replace(/\s+/g,' ')+'#'+roll.trim().toLowerCase()); }
function accounts(){ return lsGet(ACC_KEY)||{students:{}}; }
var student=null; // {key,name,roll}
var records=[];   // finished-tab history for this student on this sheet
function progKey(){ return SHEET_KEY+'::'+student.key; }

function loadState(){
  appState = {mode:null, learning:null, quiz:null}; records=[]; activeTab=TAB_DEFS[0].id;
  var saved=lsGet(progKey());
  if(!saved) return;
  try{
    ['learning','quiz'].forEach(function(m){
      if(saved[m] && saved[m].tabs){
        var fresh = defaultState();
        TAB_DEFS.forEach(function(td){
          if(saved[m].tabs[td.id] && saved[m].tabs[td.id].items && saved[m].tabs[td.id].items.length===SLIDES[td.id].length){
            fresh.tabs[td.id] = saved[m].tabs[td.id];
          }
        });
        appState[m] = fresh;
      }
    });
    if(saved.mode==='learning' || saved.mode==='quiz') appState.mode = saved.mode;
    if(saved.activeTab && TAB_DEFS.some(function(t){ return t.id===saved.activeTab; })) activeTab = saved.activeTab;
    if(Array.isArray(saved.records)) records = saved.records;
  }catch(e){}
}
function saveState(){
  if(!student) return;
  lsSet(progKey(), {mode:appState.mode, learning:appState.learning, quiz:appState.quiz, activeTab:activeTab, records:records, updated:Date.now()});
  var acc=accounts(); if(acc.students[student.key]){ acc.students[student.key].last=Date.now(); lsSet(ACC_KEY,acc); }
}
function addRecord(mode, tabId, correct, revealed, skipped, total){
  records.unshift({at:Date.now(), mode:mode, tab:tabId, correct:correct, revealed:revealed, skipped:skipped, total:total});
  if(records.length>60) records.length=60;
  saveState();
}
function fmtDate(ms){ try{ return new Date(ms).toLocaleString(undefined,{day:'numeric',month:'short',hour:'2-digit',minute:'2-digit'}); }catch(e){ return ''; } }

function renderWho(){
  var el=document.getElementById('whoBar');
  if(!student){ el.hidden=true; el.innerHTML=''; return; }
  el.hidden=false;
  el.innerHTML='Signed in as <b>'+esc(student.name)+'</b> · Roll '+esc(student.roll)+
    ' <button id="btnRecord">My record</button> <button id="btnSignOut">Sign out</button>';
  document.getElementById('btnRecord').addEventListener('click', renderRecord);
  document.getElementById('btnSignOut').addEventListener('click', signOut);
}
function signOut(){
  saveState(); student=null; state=null; MODE=null;
  var acc=accounts(); delete acc.current; lsSet(ACC_KEY,acc);
  document.getElementById('modePill').hidden=true;
  renderWho(); renderLogin();
}
function signIn(key){
  var acc=accounts(); var st=acc.students[key]; if(!st) return;
  student={key:key, name:st.name, roll:st.roll};
  acc.current=key; st.last=Date.now(); lsSet(ACC_KEY,acc);
  loadState(); renderWho();
  if(appState.mode==='learning' || appState.mode==='quiz'){
    setMode(appState.mode); document.getElementById('modePill').hidden=false; updateModePill();
    showChrome(true); buildTabbar(); renderSlide();
    showToast('Welcome back, '+st.name.split(' ')[0]+'. Picking up where you left off.');
  } else {
    renderModePicker();
  }
}
function renderLogin(msg){
  showChrome(false);
  var acc=accounts(); var keys=Object.keys(acc.students).sort(function(a,b){ return (acc.students[b].last||0)-(acc.students[a].last||0); });
  var h='<div class="login-card"><h2>Student sign-in</h2>'+
    '<p class="lead">Sign in to save your answers, see your record and continue where you left off next time.</p>';
  if(!storageOK) h+='<div class="login-err">This browser is blocking saved data (for example, a private window). You can still practise, but progress will not be kept after you close the page.</div>';
  if(msg) h+='<div class="login-err">'+esc(msg)+'</div>';
  if(keys.length){
    h+='<div class="known"><span class="known-label">Continue as</span>';
    keys.slice(0,6).forEach(function(k){ var st=acc.students[k];
      h+='<button class="known-btn" data-k="'+esc(k)+'"><span>'+esc(st.name)+' <small>· Roll '+esc(st.roll)+'</small></span><small>'+(st.last?'Last active '+fmtDate(st.last):'')+'</small></button>'; });
    h+='</div>';
  }
  h+='<form id="loginForm" novalidate>'+
    '<div class="fld"><label for="lgName">Full name</label><input id="lgName" autocomplete="name" required></div>'+
    '<div class="fld-row"><div class="fld"><label for="lgRoll">Roll no.</label><input id="lgRoll" required></div>'+
    '<div class="fld"><label for="lgPin">4-digit PIN</label><input id="lgPin" type="password" inputmode="numeric" maxlength="4" autocomplete="off" required></div></div>'+
    '<button class="btn btn-primary" type="submit" style="width:100%;">Sign in</button>'+
    '<p class="login-note">New here? Enter your name, roll no. and a PIN you will remember, and your profile is created. Progress is saved on this device, so use the same device and browser to continue.</p>'+
    '</form></div>';
  var wrap=document.getElementById('wrap'); wrap.innerHTML=h;
  wrap.querySelectorAll('.known-btn').forEach(function(b){
    b.addEventListener('click', function(){
      var st=accounts().students[b.dataset.k];
      document.getElementById('lgName').value=st.name; document.getElementById('lgRoll').value=st.roll;
      document.getElementById('lgPin').focus();
    });
  });
  document.getElementById('loginForm').addEventListener('submit', function(e){
    e.preventDefault();
    var name=document.getElementById('lgName').value.trim(), roll=document.getElementById('lgRoll').value.trim(), pin=document.getElementById('lgPin').value.trim();
    if(!name||!roll){ renderLoginErr('Enter your name and roll no.'); return; }
    if(!/^\d{4}$/.test(pin)){ renderLoginErr('Your PIN must be exactly 4 digits.'); return; }
    var k=accKey(name,roll); var acc=accounts();
    if(acc.students[k]){
      if(acc.students[k].pin!==hashPin(pin,k)){ renderLoginErr('That PIN does not match this name and roll no. Try again.'); return; }
    } else {
      acc.students[k]={name:name.replace(/\s+/g,' '), roll:roll, pin:hashPin(pin,k), created:Date.now()};
      lsSet(ACC_KEY,acc);
    }
    signIn(k);
  });
}
function renderLoginErr(m){
  var n=document.getElementById('lgName').value, r=document.getElementById('lgRoll').value;
  renderLogin(m); document.getElementById('lgName').value=n; document.getElementById('lgRoll').value=r; document.getElementById('lgPin').focus();
}
function tabSummary(m){
  var st=appState[m]; if(!st) return null;
  return TAB_DEFS.map(function(td){
    var items=st.tabs[td.id].items, n=items.length;
    var c=items.filter(function(i){return i.status==='correct';}).length;
    var done=items.filter(function(i){return i.status!=='unanswered';}).length;
    return {label:td.label, n:n, done:done, correct:c};
  });
}
function renderRecord(){
  showChrome(false);
  var tabLabel=function(id){ var t=TAB_DEFS.find(function(x){return x.id===id;}); return t?t.label:id; };
  var h='<div class="rec-card"><h2>'+esc(student.name)+'’s record</h2><p class="rec-empty" style="margin:0 0 12px;">Roll '+esc(student.roll)+' · Polynomial Equations and Factoring</p>';
  ['learning','quiz'].forEach(function(m){
    var sum=tabSummary(m);
    h+='<h3>'+(m==='learning'?'📘 Learning Sheet':'📝 Quiz Mode')+'</h3>';
    if(!sum){ h+='<p class="rec-empty">Not started yet.</p>'; return; }
    h+='<div class="rec-table-wrap"><table class="rec-table"><thead><tr><th>Section</th><th>Progress</th><th>Correct first time</th></tr></thead><tbody>';
    sum.forEach(function(r){ var pct=Math.round(r.done/r.n*100);
      h+='<tr><td>'+r.label+'</td><td><span class="rec-bar"><i style="width:'+pct+'%"></i></span>'+r.done+' / '+r.n+'</td><td>'+(m==='quiz'?'—':r.correct+' / '+r.n)+'</td></tr>'; });
    h+='</tbody></table></div>';
  });
  h+='</div><div class="rec-card"><h3>Finished sections</h3>';
  if(!records.length){ h+='<p class="rec-empty">No sections finished yet. Each time you finish a tab, your score is recorded here.</p>'; }
  else {
    h+='<div class="rec-table-wrap"><table class="rec-table"><thead><tr><th>When</th><th>Mode</th><th>Section</th><th>Score</th></tr></thead><tbody>';
    records.forEach(function(r){ h+='<tr><td>'+fmtDate(r.at)+'</td><td>'+(r.mode==='quiz'?'Quiz':'Learning')+'</td><td>'+tabLabel(r.tab)+'</td><td>'+r.correct+' / '+r.total+(r.mode==='learning'?' <span class="rec-empty">('+r.revealed+' revealed, '+r.skipped+' skipped)</span>':'')+'</td></tr>'; });
    h+='</tbody></table></div>';
  }
  h+='</div><button class="btn btn-primary" id="btnBack">'+(MODE?'Back to practice':'Choose a mode')+'</button>';
  document.getElementById('wrap').innerHTML=h;
  document.getElementById('btnBack').addEventListener('click', function(){
    if(MODE){ showChrome(true); buildTabbar(); renderSlide(); } else renderModePicker();
  });
  window.scrollTo({top:0});
}

/* ================= tab bar ================= */
function buildTabbar(){
  var el=document.getElementById('tabbar');
  el.innerHTML = '<button class="tab-btn'+(activeTab==='theory'?' active':'')+'" data-tab="theory">Theory<span class="tab-count">notes</span></button>' + TAB_DEFS.map(function(t){
    return '<button class="tab-btn'+(t.id===activeTab?' active':'')+'" data-tab="'+t.id+'">'+t.label+'<span class="tab-count">'+SLIDES[t.id].length+'</span></button>';
  }).join('') + '<button class="tab-btn'+(activeTab==='report'?' active':'')+'" data-tab="report">📊 Report<span class="tab-count">pie</span></button>';
  el.querySelectorAll('.tab-btn').forEach(function(btn){
    btn.addEventListener('click', function(){ activeTab=btn.dataset.tab; buildTabbar(); renderSlide(); window.scrollTo({top:0,behavior:'smooth'}); });
  });
}

/* ================= rendering ================= */
function canProceed(item){ return item.status==='correct'||item.status==='revealed'||item.status==='skipped'; }

function renderSlide(){
  if(!state.tabs[activeTab]){ activeTab=TAB_DEFS[0].id; }
  var ts = state.tabs[activeTab];
  var slides = SLIDES[activeTab];
  if(ts.idx>=slides.length||ts.idx<0) ts.idx=0;
  var idx = ts.idx;
  var slide = slides[idx];
  var item = ts.items[idx];

  var tdef=TAB_DEFS.find(function(t){return t.id===activeTab;});
  document.getElementById('spLabel').textContent = tdef.label+' · Question '+(idx+1)+' of '+slides.length;
  document.getElementById('secSub').textContent = tdef.label+' — '+tdef.sub;
  document.getElementById('spFill').style.width = Math.round(((idx)/(Math.max(slides.length-1,1)))*100)+'%';

  var h='<div class="qcard">';
  if(slide.kind==='mcq' || slide.kind==='ar'){
    h += renderChoiceBody(slide, item, idx);
  } else {
    h += renderBlankBody(slide, item, idx);
  }
  h += '<div class="feedback" id="feedbackBox"></div>';
  if(MODE==='learning' && (item.status==='correct'||item.status==='revealed')) h += solutionHTML(slide);
  h += '</div>';

  document.getElementById('wrap').innerHTML = h;
  wireSlideEvents(slide, item, idx);
  restoreFeedback(item);
  renderNavbar(item);
  updateFab();
  saveState();
}

function solutionHTML(slide){
  if(!slide.sol) return '';
  return '<div class="solution"><div class="sol-h">Solution</div>'+slide.sol.split('\n').map(function(l){ return '<div class="sol-line">'+fr(esc(l))+'</div>'; }).join('')+'</div>';
}
var LETTERS=['a','b','c','d','e','f'];
function chosenHTML(slide,item){
  var opts = slide.kind==='mcq' ? slide.opts : AR_OPTIONS;
  if(item.choice===undefined) return '';
  var ok=item.choice===slide.correct;
  var h='<div class="chosen '+(ok?'ok':'bad')+'"><b>Your answer:</b> ('+LETTERS[item.choice]+') '+fr(esc(opts[item.choice]))+(ok?' ✓':' ✗')+'</div>';
  if(!ok) h+='<div class="chosen ok"><b>Correct answer:</b> ('+LETTERS[slide.correct]+') '+fr(esc(opts[slide.correct]))+'</div>';
  return h;
}
function renderChoiceBody(slide, item, idx){
  var h='<div class="qhead"><div class="qnum">'+(idx+1)+'</div>';
  if(slide.kind==='mcq'){
    h += '<div class="qtext">'+fr(esc(slide.text))+(slide.tag?'<span class="qtag">'+esc(slide.tag)+'</span>':'')+'</div>';
  } else {
    h += '<div class="qtext"><span class="qtag" style="margin-left:0;margin-right:6px;">A / R</span>Assertion (A): '+fr(esc(slide.a))+'<br>Reason (R): '+fr(esc(slide.r))+(slide.tag?'<span class="qtag">'+esc(slide.tag)+'</span>':'')+'</div>';
  }
  h += '</div>';
  if(slide.fig) h += '<div class="fig">'+slide.fig+'</div>';
  var opts = slide.kind==='mcq' ? slide.opts : AR_OPTIONS;
  if(MODE==='quiz') h += '<div class="quiz-hint">Quiz mode — pick an option. The correct answer is revealed once you finish this tab.</div>';
  var locked = MODE==='learning' && (item.status==='correct' || item.status==='revealed');
  h += '<div class="options">';
  opts.forEach(function(opt,i){
    var cls='opt';
    if(locked){
      if(i===slide.correct) cls+=' is-correct';
      else if(item.choice===i) cls+=' is-wrong';
      cls+=' locked';
    }
    if(item.choice===i) cls+=' is-chosen';
    h += '<label class="'+cls+'"><input type="radio" name="choice" value="'+i+'" '+(item.choice===i?'checked':'')+' '+(locked?'disabled':'')+'> <span class="opt-l">('+LETTERS[i]+')</span> <span class="opt-t">'+fr(esc(opt))+'</span>'+(item.choice===i?'<span class="opt-tag">'+(locked?(i===slide.correct?'Your answer ✓':'Your answer ✗'):'Selected')+'</span>':'')+'</label>';
  });
  h += '</div>';
  if(locked) h += chosenHTML(slide,item);
  return h;
}

function renderBlankBody(slide, item, idx){
  var h='<div class="qhead"><div class="qnum">'+(idx+1)+'</div><div class="qtext">';
  if(slide.kind==='case'){ h += '<b>'+esc(slide.title)+'.</b> '+esc(slide.body); }
  else { var pp=fr(esc(slide.p)).split('\n'); h += pp[0]+pp.slice(1).map(function(x){return '<span class="datline">'+x+'</span>';}).join(''); }
  h += (slide.tag?'<span class="qtag">'+esc(slide.tag)+'</span>':'')+'</div>';
  if(slide.marks) h += '<div class="marks-pill">'+slide.marks+'</div>';
  h += '</div>';
  if(slide.fig) h += '<div class="fig">'+slide.fig+'</div>';

  var total = slide.flat.length;
  var hasExpr = slide.flat.some(function(s){ return s.expr===true; });
  var hasFrac = slide.flat.some(function(s){ return ['fv','fe','fl','fm','fi','flist'].indexOf(s.expr)>=0; });
  var blankCount=0; slide.flat.forEach(function(s){ blankCount+=Object.keys(s.a).length; });

  if(MODE==='quiz'){
    h += '<div class="step-badge">'+blankCount+' blank'+(blankCount===1?'':'s')+' in this question</div>';
    h += '<div class="quiz-hint">Quiz mode — fill in what you can. Correct answers are revealed once you finish this tab.</div>';
    if(hasFrac) h += '<div class="quiz-hint">Type fractions like <b>3/4</b> and mixed numbers like <b>2 3/4</b> (whole number, space, fraction).</div>';
    if(hasExpr) h += '<div class="quiz-hint">Type answers like <b>2x-5</b>, <b>x^2-4</b> or <b>3+2i</b>. Use ^ for powers, | | for absolute value and pi for π. Any equivalent form is accepted.</div>';
    h += '<div class="steps">';
    for(var qi=0; qi<total; qi++){
      var qstep = slide.flat[qi];
      var qss = item.stepStates[qi];
      if(qstep.partLabel) h += '<div class="subpart-label">'+esc(qstep.partLabel)+'</div>';
      if(qstep.orDivider) h += '<div class="or-divider">OR</div>';
      var qline = fr(qstep.t);
      Object.keys(qstep.a).forEach(function(bkey){
        var val = qss.inputs[bkey]||'';
        var inp='<input class="blank-input'+(['fv','fe','fl','fm','fi','dec'].indexOf(qstep.expr)>=0?' fr':(qstep.expr==='flist'||qstep.expr==='dlist'||qstep.expr==='glist')?' wide':qstep.expr===true?' expr':(qstep.expr==='words'||qstep.expr==='list'||qstep.expr==='expanded'||qstep.expr==='set'||qstep.expr==='primes'||qstep.expr==='trans'||qstep.expr==='rot'?' wide':''))+'" data-step="'+qi+'" data-bkey="'+bkey+'" value="'+esc(val)+'">';
        qline = qline.replace('__'+bkey+'__', inp);
      });
      if(qstep.fig) h += '<div class="fig">'+qstep.fig+'</div>';
      h += '<div class="step-line">'+qline+'</div>';
    }
    h += '</div>';
    return h;
  }

  if(hasFrac) h += '<div class="quiz-hint">Type fractions like <b>3/4</b> and mixed numbers like <b>2 3/4</b> (whole number, space, fraction).</div>';
  if(hasExpr) h += '<div class="quiz-hint">Type answers like <b>2x-5</b>, <b>x^2-4</b> or <b>3+2i</b>. Use ^ for powers, | | for absolute value and pi for π. Any equivalent form is accepted.</div>';
  var locked = item.status==='correct' || item.status==='revealed';
  var upto = locked ? total-1 : item.curStep;
  h += '<div class="step-badge">Step '+(Math.min(item.curStep,total-1)+1)+' of '+total+'</div>';
  h += '<div class="steps">';
  for(var i=0;i<=upto;i++){
    var step = slide.flat[i];
    var ss = item.stepStates[i];
    if(step.partLabel) h += '<div class="subpart-label">'+esc(step.partLabel)+'</div>';
    if(step.orDivider) h += '<div class="or-divider">OR</div>';
    var resolved = ss.status==='correct' || ss.status==='revealed';
    var line = fr(step.t);
    Object.keys(step.a).forEach(function(bkey){
      var fs = ss.inputs['fs_'+bkey];
      var cls = fs==='correct'?'is-correct':(fs==='wrong'?'is-wrong':'');
      var val = ss.inputs[bkey]||'';
      var dis = resolved ? 'disabled':'';
      var inp='<input class="blank-input '+cls+(['fv','fe','fl','fm','fi','dec'].indexOf(step.expr)>=0?' fr':(step.expr==='flist'||step.expr==='dlist'||step.expr==='glist')?' wide':step.expr===true?' expr':(step.expr==='words'||step.expr==='list'||step.expr==='expanded'||step.expr==='set'||step.expr==='primes'||step.expr==='trans'||step.expr==='rot'?' wide':''))+'" data-step="'+i+'" data-bkey="'+bkey+'" value="'+esc(val)+'" '+dis+'>';
      line = line.replace('__'+bkey+'__', inp);
    });
    if(step.fig) h += '<div class="fig">'+step.fig+'</div>';
    h += '<div class="step-line'+(resolved?' resolved':'')+'">'+line+'</div>';
    if(ss.status==='revealed'){
      var reveals=[];
      Object.keys(step.a).forEach(function(bkey){ reveals.push(bkey+' = '+esc(step.a[bkey])); });
      h += '<div class="reveal-note">correct: '+reveals.join(', ')+'</div>';
    }
  }
  h += '</div>';
  return h;
}

var __flash=null;
function restoreFeedback(item){
  var fb=document.getElementById('feedbackBox'); if(!fb) return;
  if(__flash){ fb.className='feedback show '+__flash.c; fb.innerHTML=__flash.h; __flash=null; return; }
  if(MODE==='quiz'){ fb.className='feedback'; fb.innerHTML=''; return; }
  if(item.status==='correct'){ fb.className='feedback show ok'; fb.innerHTML='<b>All done — correct!</b>'; }
  else if(item.status==='revealed'){ fb.className='feedback show reveal'; fb.innerHTML='<b>Answer revealed above.</b> Move on whenever you’re ready.'; }
  else if(item.status==='skipped'){ fb.className='feedback show retry'; fb.innerHTML='Skipped — you can answer it now and press <b>Check</b>, or come back later from the Question Palette.'; }
  else { fb.className='feedback'; fb.innerHTML=''; }
}

function slideIsAnswered(slide,item){
  if(slide.kind==='mcq'||slide.kind==='ar') return item.choice!==undefined;
  return item.stepStates.some(function(ss){ return Object.keys(ss.inputs).some(function(k){ return k.indexOf('fs_')!==0 && ss.inputs[k] && String(ss.inputs[k]).trim()!==''; }); });
}
function renderNavbar(item){
  var ts = state.tabs[activeTab];
  var slides = SLIDES[activeTab];
  var slide = slides[ts.idx];
  var isLast = ts.idx === slides.length-1;
  var h='';
  h += '<button class="btn" id="btnPrev" '+(ts.idx===0?'disabled':'')+'>&larr; Previous</button>';

  if(MODE==='quiz'){
    h += '<button class="btn" id="btnSkip">Skip</button>';
    h += '<span class="spacer"></span>';
    h += '<button class="btn btn-primary" id="btnNext">'+(isLast?'Finish':'Next →')+'</button>';
  } else {
    h += '<button class="btn" id="btnSkip" '+(item.status!=='unanswered'?'disabled':'')+'>Skip</button>';
    h += '<span class="spacer"></span>';
    h += '<button class="btn btn-primary" id="btnCheck" '+((item.status!=='unanswered'&&item.status!=='skipped')?'disabled':'')+'>Check</button>';
    h += '<button class="btn btn-primary" id="btnNext" '+(canProceed(item)?'':'disabled')+'>'+(isLast?'Finish':'Next →')+'</button>';
  }
  document.getElementById('navbarInner').innerHTML = h;

  document.getElementById('btnPrev').addEventListener('click', function(){ if(ts.idx>0){ ts.idx--; renderSlide(); } });

  if(MODE==='quiz'){
    document.getElementById('btnSkip').addEventListener('click', function(){
      item.status='skipped';
      advanceQuiz(ts, slides);
    });
    document.getElementById('btnNext').addEventListener('click', function(){
      item.status = slideIsAnswered(slide,item) ? 'answered' : 'unanswered';
      advanceQuiz(ts, slides);
    });
  } else {
    document.getElementById('btnSkip').addEventListener('click', function(){
      if(item.status==='unanswered'){ item.status='skipped'; renderSlide(); }
    });
    document.getElementById('btnNext').addEventListener('click', function(){
      if(!canProceed(item)) return;
      if(ts.idx < slides.length-1){ ts.idx++; ts.maxReached=Math.max(ts.maxReached, ts.idx); renderSlide(); }
      else { renderFinished(); }
    });
    document.getElementById('btnCheck').addEventListener('click', function(){ handleCheck(); });
  }
}
function advanceQuiz(ts, slides){
  if(ts.idx < slides.length-1){ ts.idx++; ts.maxReached=Math.max(ts.maxReached, ts.idx); renderSlide(); }
  else { renderFinished(); }
}

function wireSlideEvents(slide, item, idx){
  document.querySelectorAll('input[type="radio"][name="choice"]').forEach(function(r){
    r.addEventListener('change', function(){ item.choice=parseInt(r.value,10); saveState();
      document.querySelectorAll('.opt').forEach(function(l){ l.classList.remove('is-chosen'); var t=l.querySelector('.opt-tag'); if(t) t.remove(); });
      var lab=r.closest('.opt'); lab.classList.add('is-chosen'); var tg=document.createElement('span'); tg.className='opt-tag'; tg.textContent='Selected'; lab.appendChild(tg); });
  });
  document.querySelectorAll('.blank-input').forEach(function(inp){
    inp.addEventListener('input', function(){
      var si=parseInt(inp.dataset.step,10), bk=inp.dataset.bkey;
      item.stepStates[si].inputs[bk]=inp.value;
      saveState();
    });
  });
}

function handleCheck(){
  var ts = state.tabs[activeTab];
  var slide = SLIDES[activeTab][ts.idx];
  var item = ts.items[ts.idx];
  if(item.status==='skipped') item.status='unanswered';
  var fb = document.getElementById('feedbackBox');

  if(slide.kind==='mcq' || slide.kind==='ar'){
    if(item.choice===undefined){ fb.className='feedback show err'; fb.innerHTML='Please choose an option first.'; return; }
    var ok = item.choice===slide.correct;
    if(ok){
      item.status='correct'; playSuccess();
      fb.className='feedback show ok'; fb.innerHTML='<b>Correct!</b>';
    } else {
      item.attempts=(item.attempts||0)+1;
      if(item.attempts>=2){ item.status='revealed'; playReveal(); }
      else { playWrong(); fb.className='feedback show retry'; fb.innerHTML='<b>Not quite — try again</b> (attempt 1 of 2) <span class="attempts-dots"><span class="used"></span><span></span></span>'; __flash={c:'retry',h:'<b>Not quite — try again</b> (attempt 1 of 2) <span class="attempts-dots"><span class="used"></span><span></span></span>'}; }
    }
    renderSlide();
    return;
  }

  // blank / case
  var step = slide.flat[item.curStep];
  var ss = item.stepStates[item.curStep];
  var blanks = Object.keys(step.a);
  var missing = blanks.some(function(k){ return !ss.inputs[k] || String(ss.inputs[k]).trim()===''; });
  if(missing){ fb.className='feedback show err'; fb.innerHTML='Fill in every blank in this step before checking.'; return; }

  var allGood=true;
  blanks.forEach(function(k){
    var good=answerMatches(ss.inputs[k], step.a[k], step.accept, step.expr);
    ss.inputs['fs_'+k]=good?'correct':'wrong';
    if(!good) allGood=false;
  });

  if(allGood){
    ss.status='correct'; playSuccess();
    advanceStepOrFinish(item, slide);
  } else {
    ss.attempts=(ss.attempts||0)+1;
    if(ss.attempts>=2){
      ss.status='revealed'; playReveal();
      advanceStepOrFinish(item, slide);
    } else {
      playWrong();
      fb.className='feedback show retry';
      fb.innerHTML='<b>Not quite — try again</b> (attempt 1 of 2) <span class="attempts-dots"><span class="used"></span><span></span></span>'; __flash={c:'retry',h:'<b>Not quite — try again</b> (attempt 1 of 2) <span class="attempts-dots"><span class="used"></span><span></span></span>'};
      renderSlide();
      return;
    }
  }
  renderSlide();
}

function advanceStepOrFinish(item, slide){
  var total = slide.flat.length;
  var hasExpr = slide.flat.some(function(s){ return s.expr===true; });
  var hasFrac = slide.flat.some(function(s){ return ['fv','fe','fl','fm','fi','flist'].indexOf(s.expr)>=0; });
  if(item.curStep < total-1){
    item.curStep++;
  } else {
    var anyRevealed = item.stepStates.some(function(ss){ return ss.status==='revealed'; });
    item.status = anyRevealed ? 'revealed' : 'correct';
  }
}

/* ================= palette ================= */
var overlay=document.getElementById('overlay');
function statusOf(tabId,i){
  var ts=state.tabs[tabId];
  if(i>ts.maxReached) return 'locked';
  if(i===ts.idx) return 'current';
  return ts.items[i].status==='unanswered' ? 'locked' : ts.items[i].status;
}
function buildPalette(){
  var slides=SLIDES[activeTab];
  document.getElementById('paletteTitle').textContent = TAB_DEFS.find(function(t){return t.id===activeTab;}).label+' · Question palette';
  var body=document.getElementById('paletteBody');
  var html='';
  for(var i=0;i<slides.length;i++){
    html += '<div class="chip" data-status="'+statusOf(activeTab,i)+'" data-idx="'+i+'">'+(i+1)+'</div>';
  }
  body.innerHTML = html;
  body.querySelectorAll('.chip').forEach(function(chip){
    chip.addEventListener('click', function(){
      var i=parseInt(chip.dataset.idx,10);
      var ts=state.tabs[activeTab];
      if(i>ts.maxReached){ showToast('Finish the earlier questions to unlock this one.'); return; }
      ts.idx=i; closePalette(); renderSlide();
    });
  });
}
function openPalette(){ buildPalette(); overlay.classList.add('show'); }
function closePalette(){ overlay.classList.remove('show'); }
var toastTimer;
function showToast(msg){
  var t=document.getElementById('toast'); t.textContent=msg; t.classList.add('show');
  clearTimeout(toastTimer); toastTimer=setTimeout(function(){ t.classList.remove('show'); },2200);
}
document.getElementById('paletteFab').addEventListener('click', openPalette);
document.getElementById('paletteClose').addEventListener('click', closePalette);
overlay.addEventListener('click', function(e){ if(e.target===overlay) closePalette(); });

function updateFab(){
  var slides=SLIDES[activeTab];
  var done=state.tabs[activeTab].items.filter(function(it){ return it.status==='correct'||it.status==='revealed'||it.status==='skipped'; }).length;
  document.getElementById('fabBadge').textContent = done+'/'+slides.length;
}

/* ================= overall progress + finish ================= */
function updateChapterProgress(){
  var total=0, done=0;
  TAB_DEFS.forEach(function(td){
    state.tabs[td.id].items.forEach(function(it){
      total++;
      if(it.status==='correct'||it.status==='revealed'||it.status==='skipped') done++;
    });
  });
  var pct = total>0 ? Math.round((done/total)*100) : 0;
  document.getElementById('cpFill').style.width=pct+'%';
  document.getElementById('cpLabel').textContent=pct+'% complete';
}
function isSlideCorrect(tabId,i){
  var slide=SLIDES[tabId][i], item=state.tabs[tabId].items[i];
  if(slide.kind==='mcq'||slide.kind==='ar') return item.choice===slide.correct;
  return slide.flat.every(function(step,si){
    var ss=item.stepStates[si];
    return Object.keys(step.a).every(function(k){ return answerMatches(ss.inputs[k], step.a[k], step.accept, step.expr); });
  });
}
function isSlideAttempted(tabId,i){
  var slide=SLIDES[tabId][i], item=state.tabs[tabId].items[i];
  if(slide.kind==='mcq'||slide.kind==='ar') return item.choice!==undefined;
  return slide.flat.some(function(step,si){
    var ss=item.stepStates[si];
    return Object.keys(step.a).some(function(k){ return ss.inputs[k] && String(ss.inputs[k]).trim()!==''; });
  });
}
function slideLabel(slide){
  var t = slide.kind==='case' ? slide.title : (slide.kind==='ar' ? slide.a : (slide.p||slide.text||''));
  t = String(t);
  return t.length>90 ? t.slice(0,90)+'…' : t;
}
function slideAnswerText(slide, item, correctSide){
  if(slide.kind==='mcq'||slide.kind==='ar'){
    var opts = slide.kind==='mcq' ? slide.opts : AR_OPTIONS;
    if(correctSide) return '('+LETTERS[slide.correct]+') '+opts[slide.correct];
    return item.choice!==undefined ? '('+LETTERS[item.choice]+') '+opts[item.choice] : '— not attempted —';
  }
  return slide.flat.map(function(step,si){
    var ss=item.stepStates[si];
    return Object.keys(step.a).map(function(k){
      return correctSide ? step.a[k] : (ss.inputs[k] || '—');
    }).join(', ');
  }).join('  |  ');
}

function renderFinished(){
  if(MODE==='quiz'){ renderQuizResults(); return; }
  var ts=state.tabs[activeTab];
  var correct=ts.items.filter(function(i){return i.status==='correct';}).length;
  var revealed=ts.items.filter(function(i){return i.status==='revealed';}).length;
  var skipped=ts.items.filter(function(i){return i.status==='skipped';}).length;
  var h='<div class="qcard done-card"><div class="big">✨</div><h2>Tab complete</h2>';
  h+='<p style="color:var(--ink-soft);font-size:14px;">You worked through all '+ts.items.length+' questions in this tab.</p>';
  if(!ts.recorded){ ts.recorded=true; addRecord('learning', activeTab, correct, revealed, skipped, ts.items.length); }
  h+='<div class="score-pills">'+
     '<span class="score-pill" style="background:var(--success-soft);color:var(--success);">'+correct+' correct</span>'+
     '<span class="score-pill" style="background:var(--danger-soft);color:var(--danger);">'+revealed+' revealed</span>'+
     '<span class="score-pill" style="background:var(--gold-soft);color:var(--retry-text);">'+skipped+' skipped</span></div>'+
     '<button class="btn btn-primary" id="btnReview">Review from question 1</button></div>';
  document.getElementById('wrap').innerHTML=h;
  document.getElementById('navbarInner').innerHTML='';
  document.getElementById('btnReview').addEventListener('click', function(){ ts.idx=0; ts.recorded=false; renderSlide(); });
  updateChapterProgress(); saveState();
}

function renderQuizResults(){
  var ts=state.tabs[activeTab];
  var slides=SLIDES[activeTab];
  var correctCount=0, attemptedCount=0;
  var rowsHtml = slides.map(function(slide,i){
    var item=ts.items[i];
    var ok=isSlideCorrect(activeTab,i);
    var att=isSlideAttempted(activeTab,i);
    if(ok) correctCount++;
    if(att) attemptedCount++;
    var tagCls = ok?'ok':(att?'bad':'na');
    var tagText = ok?'Correct':(att?'Incorrect':'Not attempted');
    var row='<div class="review-row">';
    row+='<span class="review-tag '+tagCls+'">Q'+(i+1)+' · '+tagText+'</span>';
    row+='<div class="review-q">'+fr(esc(slideLabel(slide)))+'</div>';
    row+='<div class="review-ans"><b>Your answer:</b> '+fr(esc(slideAnswerText(slide,item,false)))+'</div>';
    if(!ok) row+='<div class="review-ans" style="color:var(--success);"><b>Correct answer:</b> '+fr(esc(slideAnswerText(slide,item,true)))+'</div>';
    if(slide.sol) row+='<details class="rev-sol"><summary>Show solution</summary>'+solutionHTML(slide)+'</details>';
    row+='</div>';
    return row;
  }).join('');

  addRecord('quiz', activeTab, correctCount, 0, 0, slides.length);
  var h='<div class="qcard done-card" style="text-align:left;">';
  h+='<div style="text-align:center;"><div class="big">🏁</div><h2>Quiz complete</h2>';
  h+='<p style="color:var(--ink-soft);font-size:14px;">'+correctCount+' / '+slides.length+' correct · '+attemptedCount+' attempted</p></div>';
  h+='<div style="margin-top:16px;">'+rowsHtml+'</div>';
  h+='<div style="text-align:center;margin-top:6px;"><button class="btn btn-primary" id="btnReview">Review from question 1</button></div>';
  h+='</div>';
  document.getElementById('wrap').innerHTML=h;
  document.getElementById('navbarInner').innerHTML='';
  document.getElementById('btnReview').addEventListener('click', function(){ ts.idx=0; renderSlide(); });
  playSuccess();
  updateChapterProgress(); saveState();
}

/* ================= mode picker ================= */
function updateModePill(){
  var btn=document.getElementById('modePill');
  if(!btn) return;
  btn.textContent = MODE==='quiz' ? '📝 Quiz Mode · switch' : '📘 Learning Sheet · switch';
}
function showChrome(show){
  document.querySelector('.tabbar').style.display = show?'':'none';
  document.querySelector('.slide-progress').style.display = show?'':'none';
  document.querySelector('.navbar').style.display = show?'':'none';
  document.getElementById('paletteFab').style.display = show?'':'none';
}
function renderModePicker(){
  showChrome(false);
  var wrap=document.getElementById('wrap');
  wrap.innerHTML =
    '<div class="mode-pick">'+
      '<div class="mode-card" data-pick="learning"><div class="mode-icon">📘</div><h3>Learning Sheet</h3>'+
      '<p>Work through each question step by step with instant feedback — two tries, then the correct value is revealed right there so you can keep moving.</p></div>'+
      '<div class="mode-card" data-pick="quiz"><div class="mode-icon">📝</div><h3>Quiz Mode</h3>'+
      '<p>Attempt every question with no hints along the way. Your score and the full answer key are shown together once you finish the tab — just like the real exam.</p></div>'+
    '</div>';
  wrap.querySelectorAll('[data-pick]').forEach(function(card){
    card.addEventListener('click', function(){
      setMode(card.dataset.pick); activeTab='theory';
      document.getElementById('modePill').hidden=false;
      updateModePill();
      showChrome(true);
      buildTabbar();
      renderSlide();
    });
  });
}
document.getElementById('modePill').addEventListener('click', function(){
  if(!appState.mode){ return; }
  setMode(appState.mode==='quiz' ? 'learning' : 'quiz');
  updateModePill();
  showChrome(true);
  buildTabbar();
  renderSlide();
});

/* ================= boot ================= */
var _origRenderSlide = renderSlide;
renderSlide = function(){ _origRenderSlide(); updateChapterProgress(); updateModePill(); };


/* ================= theory tab ================= */
function renderTheory(){
  var wrap=document.getElementById('wrap');
  wrap.innerHTML='<div class="theory">'+fr(THEORY)+'</div>';
  document.querySelector('.slide-progress').style.display='none';
  document.querySelector('.navbar').style.display='none';
  document.getElementById('paletteFab').style.display='none';
  document.getElementById('secSub').textContent='Theory — notes, key ideas and worked examples';
  wrap.querySelectorAll('[data-go]').forEach(function(b){ b.addEventListener('click',function(){ activeTab=b.dataset.go; buildTabbar(); renderSlide(); window.scrollTo({top:0,behavior:'smooth'}); }); });
  wrap.querySelectorAll('[data-jump]').forEach(function(b){ b.addEventListener('click',function(){ var t=document.getElementById(b.dataset.jump); if(t) t.scrollIntoView({behavior:'smooth',block:'start'}); }); });
}
var _rsTheory = renderSlide;
renderSlide = function(){
  if(activeTab==='theory'){ renderTheory(); buildTabbar(); updateChapterProgress(); updateModePill(); saveState(); return; }
  document.querySelector('.slide-progress').style.display='';
  document.querySelector('.navbar').style.display='';
  document.getElementById('paletteFab').style.display='';
  _rsTheory();
};


/* ================= MYP criterion report ================= */
var CRIT_COL={A:'var(--accent-text)',B:'var(--gold)',C:'#8A6FC4',D:'#2F9AA0'};
function critStats(){
  return REPORT.map(function(r){
    var tabId=r[0], slides=SLIDES[tabId], ts=state&&state.tabs[tabId];
    var c=0,w=0,n=0;
    slides.forEach(function(sl,i){
      if(!ts||!ts.items[i]){ n++; return; }
      var it=ts.items[i];
      if(MODE==='learning'){
        if(it.status==='correct') c++; else if(it.status==='revealed') w++; else n++;
      } else {
        if(isSlideCorrect(tabId,i)) c++; else if(isSlideAttempted(tabId,i)) w++; else n++;
      }
    });
    var tot=slides.length, pct=tot?Math.round(c/tot*100):0;
    var lvl=Math.round(c/Math.max(tot,1)*8);
    return {tab:tabId,letter:r[1],name:r[2],c:c,w:w,n:n,tot:tot,pct:pct,lvl:lvl};
  });
}
function arcPath(cx,cy,r,a0,a1){
  if(a1-a0>=Math.PI*2-1e-6){ return 'M'+(cx-r)+','+cy+' a'+r+','+r+' 0 1,0 '+(2*r)+',0 a'+r+','+r+' 0 1,0 '+(-2*r)+',0 Z'; }
  var x0=cx+r*Math.sin(a0), y0=cy-r*Math.cos(a0), x1=cx+r*Math.sin(a1), y1=cy-r*Math.cos(a1);
  return 'M'+cx+','+cy+' L'+x0.toFixed(2)+','+y0.toFixed(2)+' A'+r+','+r+' 0 '+((a1-a0)>Math.PI?1:0)+',1 '+x1.toFixed(2)+','+y1.toFixed(2)+' Z';
}
function pieSVG(parts,size,hole,center,sub){
  var tot=parts.reduce(function(s,p){return s+p.v;},0), cx=size/2, cy=size/2, r=size/2-4, a=0, h='';
  if(!tot){ h+='<circle cx="'+cx+'" cy="'+cy+'" r="'+r+'" style="fill:var(--paper-2);stroke:var(--rule)"/>'; }
  parts.forEach(function(p){ if(!p.v) return; var b=a+p.v/tot*Math.PI*2; h+='<path d="'+arcPath(cx,cy,r,a,b)+'" style="fill:'+p.col+';stroke:var(--card);stroke-width:2"><title>'+esc(p.label)+': '+p.v+'</title></path>'; a=b; });
  if(hole) h+='<circle cx="'+cx+'" cy="'+cy+'" r="'+(r*hole)+'" style="fill:var(--card)"/>';
  if(center) h+='<text x="'+cx+'" y="'+(cy-(sub?4:0))+'" text-anchor="middle" dominant-baseline="middle" style="fill:var(--ink);font:700 '+(size>150?22:15)+'px Fraunces,serif">'+center+'</text>';
  if(sub) h+='<text x="'+cx+'" y="'+(cy+16)+'" text-anchor="middle" style="fill:var(--ink-soft);font:600 11px \'Source Sans 3\',sans-serif">'+sub+'</text>';
  return '<svg viewBox="0 0 '+size+' '+size+'" width="'+size+'" height="'+size+'" role="img">'+h+'</svg>';
}
function band(l){ return l===0?'0':(l<=2?'1–2':(l<=4?'3–4':(l<=6?'5–6':'7–8'))); }
function renderReport(){
  var st=critStats(), totC=0, totQ=0;
  st.forEach(function(s){ totC+=s.c; totQ+=s.tot; });
  var h='<div class="theory">';
  h+='<section class="note"><h2>Chapter test report</h2><p class="lt">'+(MODE==='quiz'?'<b>Quiz mode</b> results: answers are marked when you finish each test tab.':'<b>Learning mode</b> results: a question counts as correct only if you got it without the answer being revealed. Switch to Quiz mode for an exam-style score.')+'</p>';
  h+='<div class="rep-top"><div class="rep-pie">'+pieSVG(st.map(function(s){return {v:s.c,col:CRIT_COL[s.letter],label:'Criterion '+s.letter};}),200,0.55,totC+'/'+totQ,'correct')+'</div>';
  h+='<div class="rep-legend"><div class="rep-cap">Marks earned, by criterion</div>'+st.map(function(s){ return '<div class="rep-li"><span class="sw" style="background:'+CRIT_COL[s.letter]+'"></span><b>'+s.letter+'</b>&nbsp;'+esc(s.name)+'<span class="rep-n">'+s.c+' / '+s.tot+'</span></div>'; }).join('')+'</div></div></section>';
  h+='<div class="rep-grid">'+st.map(function(s){
    return '<div class="rep-card"><div class="rep-h"><span class="crit" style="background:'+CRIT_COL[s.letter]+'">'+s.letter+'</span>'+esc(s.name)+'</div>'+
      '<div class="rep-row">'+pieSVG([{v:s.c,col:'var(--success)',label:'Correct'},{v:s.w,col:'var(--danger)',label:'Incorrect'},{v:s.n,col:'var(--locked)',label:'Not attempted'}],120,0.5,s.pct+'%')+
      '<div class="rep-stats"><div><span class="sw" style="background:var(--success)"></span>Correct <b>'+s.c+'</b></div><div><span class="sw" style="background:var(--danger)"></span>Incorrect <b>'+s.w+'</b></div><div><span class="sw" style="background:var(--locked)"></span>Not attempted <b>'+s.n+'</b></div>'+
      '<div class="rep-lvl">Indicative level <b>'+s.lvl+'</b> / 8 <span>(band '+band(s.lvl)+')</span></div></div></div>'+
      '<button class="hub-btn" data-go="'+s.tab+'">Open Test '+s.letter+' →</button></div>';
  }).join('')+'</div>';
  h+='<p class="rep-note">Indicative level = fraction of questions correct × 8, rounded. It is a practice guide only; your teacher awards the real MYP criterion levels.</p></div>';
  var wrap=document.getElementById('wrap'); wrap.innerHTML=h;
  document.querySelector('.slide-progress').style.display='none';
  document.querySelector('.navbar').style.display='none';
  document.getElementById('paletteFab').style.display='none';
  document.getElementById('secSub').textContent='Report — chapter test results by MYP criterion';
  wrap.querySelectorAll('[data-go]').forEach(function(b){ b.addEventListener('click',function(){ activeTab=b.dataset.go; buildTabbar(); renderSlide(); window.scrollTo({top:0,behavior:'smooth'}); }); });
}
var _rsReport = renderSlide;
renderSlide = function(){
  if(activeTab==='report'){ renderReport(); buildTabbar(); updateChapterProgress(); updateModePill(); saveState(); return; }
  _rsReport();
};


/* ================= skipped-question return ================= */
function firstSkippedIdx(ts){
  for(var i=0;i<ts.items.length;i++){
    var it=ts.items[i];
    if(MODE==='quiz'){ if(!isSlideAttempted(activeTab,i)) return i; }
    else if(it.status==='skipped'||it.status==='unanswered') return i;
  }
  return -1;
}
function skippedList(ts){
  var out=[]; for(var i=0;i<ts.items.length;i++){ var it=ts.items[i];
    if(MODE==='quiz' ? !isSlideAttempted(activeTab,i) : (it.status==='skipped'||it.status==='unanswered')) out.push(i); }
  return out;
}
function renderSkipGate(ts){
  var list=skippedList(ts);
  var h='<div class="qcard done-card"><div class="big">⏭️</div><h2>You skipped '+list.length+' question'+(list.length>1?'s':'')+'</h2>'+
    '<p style="color:var(--ink-soft);font-size:14px;">Answer them now, or submit the tab as it is. Answers are marked only when you submit.</p>'+
    '<div class="skip-chips">'+list.map(function(i){ return '<button class="chip skip-go" data-i="'+i+'">Q'+(i+1)+'</button>'; }).join('')+'</div>'+
    '<div class="skip-btns"><button class="btn btn-primary" id="btnGoSkipped">Answer skipped questions</button><button class="btn" id="btnSubmitAnyway">Submit anyway</button></div></div>';
  document.getElementById('wrap').innerHTML=h;
  document.getElementById('navbarInner').innerHTML='';
  var go=function(i){ ts.idx=i; ts.maxReached=Math.max(ts.maxReached,i); renderSlide(); window.scrollTo({top:0,behavior:'smooth'}); };
  document.getElementById('btnGoSkipped').addEventListener('click',function(){ go(list[0]); });
  document.querySelectorAll('.skip-go').forEach(function(b){ b.addEventListener('click',function(){ go(parseInt(b.dataset.i,10)); }); });
  document.getElementById('btnSubmitAnyway').addEventListener('click',function(){ ts.submitOK=true; renderFinished(); ts.submitOK=false; });
  saveState();
}
var _rfSkip = renderFinished;
renderFinished = function(){
  var ts=state.tabs[activeTab];
  if(MODE==='quiz' && !ts.submitOK && skippedList(ts).length){ renderSkipGate(ts); return; }
  _rfSkip();
  if(MODE==='learning'){
    var list=skippedList(ts);
    if(list.length){
      var card=document.querySelector('.done-card');
      if(card){ var d=document.createElement('div'); d.className='skip-btns';
        d.innerHTML='<button class="btn btn-primary" id="btnGoSkipped">Attempt skipped questions ('+list.length+')</button>';
        card.appendChild(d);
        document.getElementById('btnGoSkipped').addEventListener('click',function(){ ts.idx=list[0]; ts.recorded=false; renderSlide(); window.scrollTo({top:0,behavior:'smooth'}); }); }
    }
  }
};


/* ================= approx answers (physics: within 1%) ================= */
var _amTools = answerMatches;
answerMatches = function(input,answer,accept,expr){
  if(expr==='approx'){
    var n1=parseNum(input); if(n1===null) return false;
    return [answer].concat(accept||[]).some(function(a){ var n2=parseNum(a); if(n2===null) return false; return Math.abs(n1-n2) <= Math.max(0.011*Math.abs(n2), 1e-9); });
  }
  return _amTools(input,answer,accept,expr);
};

/* ================= palette: every question already reached can be opened ================= */
statusOf = function(tabId,i){
  var ts=state.tabs[tabId];
  if(i>ts.maxReached) return 'locked';
  if(i===ts.idx) return 'current';
  var s=ts.items[i].status;
  if(s==='unanswered') return 'skipped';
  return s;
};

/* ================= on-screen keyboard ================= */
var KB={on:true, page:'num', target:null};
try{ var kbp=localStorage.getItem('sopaan-kb-pref'); if(kbp==='off') KB.on=false; }catch(e){}
function kbSave(){ try{ localStorage.setItem('sopaan-kb-pref', KB.on?'on':'off'); }catch(e){} }
var KEYS_NUM=[['7','8','9','(',')'],['4','5','6','−','/'],['1','2','3','.',','],['0',':','%','°','⌫'],['abc','←','→','Clear','Done']];
var KEYS_FRAC=[['7','8','9','/'],['4','5','6','−'],['1','2','3','space'],['0',',','⌫','Clear'],['abc','←','→','Done']];
var KEYS_ALG=[['7','8','9','x','y','n'],['4','5','6','+','−','a'],['1','2','3','×','÷','b'],['0','.','(',')','^','²'],['/','π','|','t','⌫','Clear'],['abc','←','→','Done']];
function kbLayoutFor(inp){ try{ var ts=state.tabs[activeTab], sl=SLIDES[activeTab][ts.idx], stp=sl.flat[parseInt(inp.dataset.step,10)]; var m=stp.expr, key=String(stp.a[inp.dataset.bkey]||'');
  if(m==='words'||m==='glist'||m==='angle') return 'abc'; if(m===true||m==='pow'||m==='primes') return 'alg';
  if(['fv','fe','fl','fm','fi','flist'].indexOf(m)>=0) return 'frac'; if(m==='dec'||m==='approx'||m==='dlist'||m==='set'||m==='coord'||m==='list'||m==='time') return 'num';
  if(/^[\-−]?\d+ \d+\/\d+$/.test(key)||/^[\-−]?\d+\/\d+$/.test(key)) return 'frac'; if(/[a-df-z]/i.test(key.replace(/pi/gi,''))) return /\d/.test(key)?'alg':'abc'; return 'num'; }catch(e){ return 'num'; } }
var KEYS_CALC=[['7','8','9','x','(',')'],['4','5','6','+','−','^'],['1','2','3','×','/','²'],['0','.','e','eˣ','√','ln'],['sin','cos','tan','t','⌫','Clear'],['abc','←','→','Done']];
var KEYS_ABC=[['q','w','e','r','t','y','u','i','o','p'],['a','s','d','f','g','h','j','k','l','-'],['z','x','c','v','b','n','m',',',':','/'],['123','space','←','→','⌫','Done']];
function kbBuild(){
  var el=document.getElementById('vkb'); if(!el){ el=document.createElement('div'); el.id='vkb'; el.className='vkb'; document.body.appendChild(el);
    el.addEventListener('pointerdown',function(e){ var b=e.target.closest('button[data-k]'); e.preventDefault(); if(b) kbPress(b.dataset.k); });
    el.addEventListener('mousedown',function(e){ e.preventDefault(); }); }
  var rows={num:KEYS_NUM,frac:KEYS_FRAC,alg:KEYS_ALG,abc:KEYS_ABC,calc:KEYS_CALC}[KB.page]||KEYS_NUM;
  el.innerHTML='<div class="vkb-top"><span>⌨️ Keyboard</span><button data-k="device" class="vkb-link">Use device keyboard</button></div>'+
    rows.map(function(r){ return '<div class="vkb-row">'+r.map(function(k){
      var cls='vkb-k'+(/^(abc|123|Done|Clear|⌫|←|→|space)$/.test(k)?' fn':'')+(k==='Done'?' done':'');
      return '<button type="button" class="'+cls+'" data-k="'+k+'">'+(k==='space'?'space':k)+'</button>'; }).join('')+'</div>'; }).join('');
  return el;
}
function kbShow(inp){ KB.target=inp; KB.home=kbLayoutFor(inp); KB.page=KB.home; if(!KB.on) return; var cp=document.getElementById('calcPanel'); if(cp&&cp.classList.contains('show')) return; var el=kbBuild(); var nb=document.querySelector('.navbar'); el.style.bottom=(nb?nb.getBoundingClientRect().height:0)+'px'; el.classList.add('show'); document.body.classList.add('kb-open'); setTimeout(function(){ var r=inp.getBoundingClientRect(), top=el.getBoundingClientRect().top; if(r.bottom>top-12) window.scrollBy({top:r.bottom-top+60,behavior:'smooth'}); else if(r.top<60) window.scrollBy({top:r.top-80,behavior:'smooth'}); },30); }
function kbHide(){ var el=document.getElementById('vkb'); if(el) el.classList.remove('show'); document.body.classList.remove('kb-open'); }
function kbInsert(s){
  var t=KB.target; if(!t||t.disabled) return;
  var a=t.selectionStart==null?t.value.length:t.selectionStart, b=t.selectionEnd==null?a:t.selectionEnd;
  t.value=t.value.slice(0,a)+s+t.value.slice(b); var p=a+s.length; try{ t.setSelectionRange(p,p); }catch(e){}
  t.dispatchEvent(new Event('input',{bubbles:true}));
}
function kbPress(k){
  var t=KB.target; if(k==='device'){ KB.on=false; kbSave(); kbHide(); document.querySelectorAll('.blank-input').forEach(function(i){ i.removeAttribute('inputmode'); }); if(t){ t.blur(); setTimeout(function(){ t.focus(); },50); } showToast('Device keyboard on. Tap ⌨️ on any blank to bring the on-screen keyboard back.'); return; }
  if(k==='Done'){ kbHide(); if(t) t.blur(); return; }
  if(k==='abc'||k==='123'){ KB.page=(k==='abc')?'abc':(KB.home&&KB.home!=='abc'?KB.home:'num'); kbBuild(); return; }
  if(!t) return;
  if(k==='⌫'){ var a=t.selectionStart, b=t.selectionEnd; if(a===b&&a>0){ t.value=t.value.slice(0,a-1)+t.value.slice(b); try{t.setSelectionRange(a-1,a-1);}catch(e){} } else { t.value=t.value.slice(0,a)+t.value.slice(b); try{t.setSelectionRange(a,a);}catch(e){} } t.dispatchEvent(new Event('input',{bubbles:true})); return; }
  if(k==='Clear'){ t.value=''; t.dispatchEvent(new Event('input',{bubbles:true})); return; }
  if(k==='←'||k==='→'){ var p=(t.selectionStart||0)+(k==='←'?-1:1); p=Math.max(0,Math.min(t.value.length,p)); try{t.setSelectionRange(p,p);}catch(e){} return; }
  var map={'−':'-','space':' '}; kbInsert(map[k]!==undefined?map[k]:k);
}
function kbWire(){
  document.querySelectorAll('.blank-input').forEach(function(inp){
    if(inp.dataset.kb) return; inp.dataset.kb='1';
    if(KB.on) inp.setAttribute('inputmode','none');
    inp.addEventListener('focus',function(){ kbShow(inp); });
    var btn=document.createElement('button'); btn.type='button'; btn.className='kb-toggle'; btn.title='On-screen keyboard'; btn.textContent='⌨️'; btn.tabIndex=-1;
    btn.addEventListener('mousedown',function(e){ e.preventDefault(); });
    btn.addEventListener('click',function(){ KB.on=true; kbSave(); document.querySelectorAll('.blank-input').forEach(function(i){ i.setAttribute('inputmode','none'); }); inp.focus(); kbShow(inp); });
    if(!inp.disabled) inp.insertAdjacentElement('afterend',btn);
  });
}
document.addEventListener('focusout',function(e){ setTimeout(function(){ var a=document.activeElement; if(!a||!a.classList||!a.classList.contains('blank-input')){ if(!document.querySelector('#vkb:hover')) kbHide(); } },120); });

/* ================= calculator ================= */
var CALC={expr:'', ans:0};
function calcEval(src){
  var s=String(src).replace(/×/g,'*').replace(/÷/g,'/').replace(/−/g,'-').replace(/π/g,'(PI)').replace(/Ans/g,'('+CALC.ans+')').replace(/\^/g,'**').replace(/√\(/g,'sqrt(').replace(/²/g,'**2').replace(/E/g,'*10**');
  s=s.replace(/(^|[(*\/+\-,])-/g,'$1(-1)*');
  if(/[^0-9+\-*/().,a-z A-Z]/.test(s)) throw 0;
  var ok=s.replace(/sin|cos|tan|asin|acos|atan|sqrt|log|ln|PI|abs/g,''); if(/[a-zA-Z]/.test(ok)) throw 0;
  var f=new Function('sin','cos','tan','asin','acos','atan','sqrt','log','ln','PI','abs','return ('+s+');');
  var d=Math.PI/180;
  var v=f(function(x){return Math.sin(x*d);},function(x){return Math.cos(x*d);},function(x){return Math.tan(x*d);},
    function(x){return Math.asin(x)/d;},function(x){return Math.acos(x)/d;},function(x){return Math.atan(x)/d;},Math.sqrt,Math.log10,Math.log,Math.PI,Math.abs);
  if(typeof v!=='number'||!isFinite(v)) throw 0; return v;
}
function fmtNum(v){ if(Math.abs(v)>=1e10||(Math.abs(v)<1e-6&&v!==0)) return v.toExponential(6).replace(/\.?0+e/,'e'); return String(parseFloat(v.toPrecision(10))); }
var CKEYS=[['sin(','cos(','tan(','√(','^','²'],['asin(','acos(','atan(','(',')','π'],['7','8','9','÷','⌫','AC'],['4','5','6','×','E','Ans'],['1','2','3','−','(−)','Insert'],['0','.','=','+']];
function openCalc(){
  var p=document.getElementById('calcPanel');
  if(!p){ p=document.createElement('div'); p.id='calcPanel'; p.className='tool-panel calc';
    p.innerHTML='<div class="tp-head"><b>🧮 Calculator</b><span class="tp-note">degrees · tap a blank, then Insert</span><button class="tp-x" data-c="close">✕</button></div>'+
      '<div class="calc-disp"><div class="calc-expr" id="calcExpr"></div><div class="calc-res" id="calcRes">0</div></div>'+
      '<div class="calc-keys">'+CKEYS.map(function(r){ return r.map(function(k){ return '<button type="button" data-c="'+k+'" class="'+(k==='='?'eq':(/^(AC|⌫|Insert)$/.test(k)?'fn':''))+'">'+({'sin(':'sin','cos(':'cos','tan(':'tan','asin(':'sin⁻¹','acos(':'cos⁻¹','atan(':'tan⁻¹','√(':'√'}[k]||k)+'</button>'; }).join(''); }).join('')+'</div>';
    document.body.appendChild(p);
    p.addEventListener('mousedown',function(e){ if(e.target.closest('button')) e.preventDefault(); });
    p.addEventListener('click',function(e){ var b=e.target.closest('button[data-c]'); if(!b) return; calcKey(b.dataset.c); });
  }
  kbHide(); var nb=document.querySelector('.navbar'); p.style.bottom=((nb?nb.getBoundingClientRect().height:0)+8)+'px'; p.classList.add('show'); document.body.classList.add('calc-open'); calcShow();
}
function calcShow(res){ document.getElementById('calcExpr').textContent=CALC.expr||' '; if(res!==undefined) document.getElementById('calcRes').textContent=res; }
function calcKey(k){
  if(k==='close'){ document.getElementById('calcPanel').classList.remove('show'); document.body.classList.remove('calc-open'); return; }
  if(k==='AC'){ CALC.expr=''; calcShow('0'); return; }
  if(k==='⌫'){ CALC.expr=CALC.expr.replace(/(asin\(|acos\(|atan\(|sin\(|cos\(|tan\(|√\(|Ans|.)$/,''); calcShow(); return; }
  if(k==='='){ try{ var v=calcEval(CALC.expr); CALC.ans=v; calcShow(fmtNum(v)); }catch(e){ calcShow('Error'); } return; }
  if(k==='(−)'){ CALC.expr+='−'; calcShow(); return; }
  if(k==='Insert'){ var r=document.getElementById('calcRes').textContent; if(KB.target && !KB.target.disabled && r!=='Error'){ KB.target.value=r; KB.target.dispatchEvent(new Event('input',{bubbles:true})); showToast('Inserted '+r+' into the blank.'); } else showToast('Tap a blank first, then press Insert.'); return; }
  CALC.expr+=k; calcShow();
}

/* ================= Desmos ================= */
var DESMOS_KEY='dcb31709b452b1cf9dc26972add0fda6', desmosCalc=null, desmosLoading=false;
function openDesmos(exprs){
  var p=document.getElementById('desmosPanel');
  if(!p){ p=document.createElement('div'); p.id='desmosPanel'; p.className='tool-panel desmos';
    p.innerHTML='<div class="tp-head"><b>📈 Desmos graphing calculator</b><button class="tp-x" id="desmosReset">Reset graph</button><button class="tp-x" id="desmosClose">✕</button></div><div id="desmosBox"><div class="desmos-msg">Loading Desmos…</div></div>';
    document.body.appendChild(p);
    document.getElementById('desmosClose').addEventListener('click',function(){ p.classList.remove('show'); });
    document.getElementById('desmosReset').addEventListener('click',function(){ if(desmosCalc) desmosSet(p._exprs||[]); });
  }
  p._exprs=exprs||[]; p.classList.add('show');
  if(window.Desmos){ desmosInit(); desmosSet(p._exprs); return; }
  if(desmosLoading) return; desmosLoading=true;
  var sc=document.createElement('script'); sc.src='https://www.desmos.com/api/v1.9/calculator.js?apiKey='+DESMOS_KEY;
  sc.onload=function(){ desmosInit(); desmosSet(p._exprs); };
  sc.onerror=function(){ desmosLoading=false; document.getElementById('desmosBox').innerHTML='<div class="desmos-msg">Desmos needs an internet connection. <a href="https://www.desmos.com/calculator" target="_blank" rel="noopener">Open Desmos in a new tab</a>.</div>'; };
  document.head.appendChild(sc);
}
function desmosInit(){ if(desmosCalc) return; var box=document.getElementById('desmosBox'); box.innerHTML=''; desmosCalc=Desmos.GraphingCalculator(box,{expressionsCollapsed:false,settingsMenu:false,border:false,degreeMode:true}); }
function desmosSet(exprs){ if(!desmosCalc) return; desmosCalc.setBlank(); (exprs||[]).forEach(function(e,i){ if(typeof e==='string') desmosCalc.setExpression({id:'e'+i,latex:e}); else desmosCalc.setExpression(Object.assign({id:'e'+i},e)); }); }

/* ================= toolbar on each question ================= */
var _rsTools = renderSlide;
renderSlide = function(){
  _rsTools();
  kbHide();
  if(activeTab==='theory'||activeTab==='report') return;
  var ts=state.tabs[activeTab]; if(!ts) return;
  var slide=SLIDES[activeTab][ts.idx], card=document.querySelector('#wrap .qcard');
  if(card && slide && slide.tools && slide.tools.length && !card.querySelector('.tool-bar')){
    var bar=document.createElement('div'); bar.className='tool-bar';
    bar.innerHTML=(slide.tools.indexOf('calc')>=0?'<button type="button" class="tool-btn" data-t="calc">🧮 Calculator</button>':'')+
                  (slide.tools.indexOf('desmos')>=0?'<button type="button" class="tool-btn" data-t="desmos">📈 Desmos graph</button>':'');
    card.insertBefore(bar, card.firstChild);
    bar.addEventListener('click',function(e){ var b=e.target.closest('[data-t]'); if(!b) return; if(b.dataset.t==='calc') openCalc(); else openDesmos(slide.desmos||[]); });
  }
  kbWire();
};



/* ================= signed fractions in text: {−3/4}, {3/−4}, {−2 1/3}, {p/q} ================= */
fr = function(s){ return String(s).replace(/&lt;(\/?)(b|sup|sub|i)>/g,'<$1$2>')
  .replace(/\{([−-]?\d+) (\d+)\/(\d+)\}/g,'<span class="mx">$1<span class="fq"><span>$2</span><span>$3</span></span></span>')
  .replace(/\{([−-]?[A-Za-z0-9]+)\/([−-]?[A-Za-z0-9]+)\}/g,'<span class="fq"><span>$1</span><span>$2</span></span>'); };
/* ================= BMA badge → main page of this sheet (theory hub) ================= */
(function(){
  var c=document.querySelector('.brand .crest'); if(!c) return;
  var a=document.createElement('button'); a.type='button'; a.className='crest crest-home'; a.title='Back to the main page (theory notes)'; a.setAttribute('aria-label','Main page');
  a.innerHTML='BM<span class="crest-h">⌂</span>'; c.parentNode.replaceChild(a,c);
  a.addEventListener('click',function(){
    if(!student||!MODE){ window.scrollTo({top:0,behavior:'smooth'}); return; }
    if(typeof kbHide==='function') kbHide(); if(typeof SP!=='undefined'&&SP.on) spToggle(false);
    var cp=document.getElementById('calcPanel'); if(cp) cp.classList.remove('show'); document.body.classList.remove('calc-open');
    activeTab = (typeof THEORY!=='undefined') ? 'theory' : TAB_DEFS[0].id;
    buildTabbar(); renderSlide(); window.scrollTo({top:0,behavior:'smooth'});
  });
})();

/* ================= session clock: starts at sign-in and keeps running ================= */
var CLK={t0:null};
(function(){
  var row=document.querySelector('.brand .brand-row'); if(!row) return;
  var d=document.createElement('div'); d.className='bmasw off'; d.id='swBox'; d.title='Time since you signed in';
  d.innerHTML='<span class="bmasw-ic">⏱</span><span class="bmasw-t" id="swT">00:00</span>';
  row.appendChild(d); setInterval(swTick,1000);
})();
function swFmt(s){ s=Math.floor(s||0); var h=Math.floor(s/3600), m=Math.floor(s%3600/60), x=s%60; return (h?h+':'+String(m).padStart(2,'0'):String(m).padStart(2,'0'))+':'+String(x).padStart(2,'0'); }
function swTick(){
  var box=document.getElementById('swBox'); if(!box) return;
  if(student && !CLK.t0) CLK.t0=Date.now();
  if(!student) CLK.t0=null;
  box.classList.toggle('off',!CLK.t0);
  document.getElementById('swT').textContent = CLK.t0 ? swFmt((Date.now()-CLK.t0)/1000) : '00:00';
}
function swTab(){ try{ if(!state||!state.tabs||activeTab==='theory'||activeTab==='report') return null; return state.tabs[activeTab]||null; }catch(e){ return null; } }
var _rsSW = renderSlide;
renderSlide = function(){ _rsSW(); swTick(); };
var _rfSW = renderFinished;
renderFinished = function(){ _rfSW(); var done=document.querySelector('#wrap .done-card'); if(CLK.t0 && done && !done.querySelector('.bmasw-done')){ var p=document.createElement('p'); p.className='bmasw-done'; p.textContent='⏱ Time since sign-in: '+swFmt((Date.now()-CLK.t0)/1000); var h2=done.querySelector('h2'); if(h2) h2.insertAdjacentElement('afterend',p); else done.appendChild(p); } };

/* ================= scratchpad (Khan-style, 4 pens) ================= */
var SP={on:false, draw:true, color:'ink', size:3, erase:false, store:{}, key:null, cv:null, ctx:null, down:false, last:null};
var SP_COL={ink:null, blue:'#2563EB', red:'#DC2626', green:'#16A34A'};
function spInk(){ return getComputedStyle(document.documentElement).getPropertyValue('--ink').trim()||'#211E1A'; }
function spKey(){ var ts=swTab(); return ts ? (MODE+'|'+activeTab+'|'+ts.idx) : null; }
function spBuild(){
  if(SP.cv) return;
  var cv=document.createElement('canvas'); cv.id='spCanvas'; cv.className='sp-canvas'; document.body.appendChild(cv);
  var bar=document.createElement('div'); bar.id='spBar'; bar.className='sp-bar';
  bar.innerHTML='<span class="sp-lbl">✏️ Scratchpad</span>'+
    ['ink','blue','red','green'].map(function(c){ return '<button type="button" class="sp-pen" data-c="'+c+'" title="'+(c==='ink'?'black':c)+' pen"><i style="background:'+(c==='ink'?'var(--ink)':SP_COL[c])+'"></i></button>'; }).join('')+
    '<button type="button" class="sp-tool" data-t="erase" title="Eraser">🧽</button><button type="button" class="sp-tool" data-t="size" title="Pen size">●</button><button type="button" class="sp-tool" data-t="scroll" title="Pause drawing to scroll or answer">✋</button>'+
    '<button type="button" class="sp-tool" data-t="clear" title="Clear page">🗑</button><button type="button" class="sp-tool" data-t="close" title="Close scratchpad">✕</button>';
  document.body.appendChild(bar);
  bar.addEventListener('click',function(e){ var b=e.target.closest('button'); if(!b) return;
    if(b.dataset.c){ SP.color=b.dataset.c; SP.erase=false; SP.draw=true; }
    else if(b.dataset.t==='erase'){ SP.erase=true; SP.draw=true; }
    else if(b.dataset.t==='size'){ SP.size = SP.size===3?6:(SP.size===6?1.5:3); b.textContent = SP.size===6?'⬤':(SP.size===1.5?'·':'●'); }
    else if(b.dataset.t==='scroll'){ SP.draw=!SP.draw; }
    else if(b.dataset.t==='clear'){ spClear(); }
    else if(b.dataset.t==='close'){ spToggle(false); return; }
    spUI(); });
  SP.cv=cv; SP.ctx=cv.getContext('2d');
  cv.addEventListener('pointerdown',function(e){ if(!SP.draw) return; e.preventDefault(); cv.setPointerCapture(e.pointerId); SP.down=true; SP.last=spPt(e); spDot(SP.last); });
  cv.addEventListener('pointermove',function(e){ if(!SP.down) return; e.preventDefault(); var p=spPt(e); spLine(SP.last,p); SP.last=p; });
  var up=function(){ if(SP.down){ SP.down=false; spSave(); } };
  cv.addEventListener('pointerup',up); cv.addEventListener('pointercancel',up); cv.addEventListener('pointerleave',up);
  window.addEventListener('resize',function(){ if(SP.on) spFit(true); });
}
function spPt(e){ var r=SP.cv.getBoundingClientRect(); return {x:e.clientX-r.left, y:e.clientY-r.top}; }
function spStyle(){ var c=SP.ctx; c.lineCap='round'; c.lineJoin='round'; c.globalCompositeOperation=SP.erase?'destination-out':'source-over'; c.strokeStyle=c.fillStyle=(SP.color==='ink'?spInk():SP_COL[SP.color]); c.lineWidth=SP.erase?22:SP.size; }
function spDot(p){ spStyle(); var c=SP.ctx; c.beginPath(); c.arc(p.x,p.y,(SP.erase?11:SP.size/2),0,Math.PI*2); c.fill(); }
function spLine(a,b){ spStyle(); var c=SP.ctx; c.beginPath(); c.moveTo(a.x,a.y); c.lineTo(b.x,b.y); c.stroke(); }
function spSave(){ if(SP.key&&SP.cv){ try{ SP.store[SP.key]=SP.cv.toDataURL(); }catch(e){} } }
function spClear(){ if(!SP.ctx) return; SP.ctx.save(); SP.ctx.setTransform(1,0,0,1,0,0); SP.ctx.clearRect(0,0,SP.cv.width,SP.cv.height); SP.ctx.restore(); if(SP.key) delete SP.store[SP.key]; }
function spFit(keep){
  var wrap=document.getElementById('wrap'); if(!wrap||!SP.cv) return;
  var r=wrap.getBoundingClientRect(), top=r.top+window.scrollY, h=Math.max(wrap.scrollHeight, window.innerHeight-r.top)+40, w=document.documentElement.clientWidth;
  var old=keep&&SP.key?SP.store[SP.key]:null, dpr=window.devicePixelRatio||1;
  SP.cv.style.top=top+'px'; SP.cv.style.left='0px'; SP.cv.style.width=w+'px'; SP.cv.style.height=h+'px';
  SP.cv.width=Math.round(w*dpr); SP.cv.height=Math.round(h*dpr); SP.ctx.setTransform(dpr,0,0,dpr,0,0);
  if(old){ var im=new Image(); im.onload=function(){ SP.ctx.save(); SP.ctx.setTransform(1,0,0,1,0,0); SP.ctx.drawImage(im,0,0); SP.ctx.restore(); }; im.src=old; }
}
function spLoad(){ spSave(); SP.key=spKey(); spFit(false); var d=SP.key&&SP.store[SP.key]; if(d){ var im=new Image(); im.onload=function(){ SP.ctx.save(); SP.ctx.setTransform(1,0,0,1,0,0); SP.ctx.drawImage(im,0,0); SP.ctx.restore(); }; im.src=d; } }
function spUI(){
  var bar=document.getElementById('spBar'); if(!bar) return;
  bar.querySelectorAll('.sp-pen').forEach(function(b){ b.classList.toggle('on', !SP.erase && SP.draw && b.dataset.c===SP.color); });
  bar.querySelector('[data-t=erase]').classList.toggle('on', SP.erase && SP.draw);
  bar.querySelector('[data-t=scroll]').classList.toggle('on', !SP.draw);
  SP.cv.classList.toggle('passive', !SP.draw);
  var fb=document.getElementById('spFab'); if(fb) fb.classList.toggle('on',SP.on);
}
function spToggle(on){
  spBuild(); SP.on=(on===undefined)?!SP.on:on;
  document.body.classList.toggle('sp-open',SP.on); SP.cv.style.display=SP.on?'block':'none'; document.getElementById('spBar').style.display=SP.on?'flex':'none';
  if(SP.on){ SP.draw=true; SP.erase=false; spLoad(); if(typeof kbHide==='function') kbHide(); } else { spSave(); }
  spUI();
}
(function(){ var f=document.createElement('button'); f.type='button'; f.id='spFab'; f.className='sp-fab'; f.innerHTML='✏️ <span>Scratchpad</span>'; f.title='Open a scratchpad to write your working'; f.addEventListener('click',function(){ spToggle(); }); document.body.appendChild(f); })();
var _rsSP = renderSlide;
renderSlide = function(){ _rsSP(); var fab=document.getElementById('spFab'); var q=!!swTab(); if(fab) fab.style.display=q?'':'none'; if(!q && SP.on) spToggle(false); if(SP.on) setTimeout(spLoad,30); };


/* ================= v4: attempt classification ================= */
function v4Class(item){
  if(!item) return 'un';
  if(item.status==='skipped') return 'sk';
  if(item.status==='unanswered') return 'un';
  if(item.stepStates){ // step question
    if(item.status!=='correct' && item.status!=='revealed') return 'un';
    if(item.status==='revealed' || item.stepStates.some(function(s){return s.status==='revealed';})) return 'w';
    return item.stepStates.some(function(s){return (s.attempts||0)>0;}) ? 'c2' : 'c1';
  }
  if(item.status==='revealed') return 'w';
  if(item.status==='correct') return (item.attempts||0)>0 ? 'c2' : 'c1';
  if(item.status==='wrong'||item.status==='incorrect') return 'w';
  return 'un';
}
function v4Counts(items){ var c={n:items.length,c1:0,c2:0,w:0,sk:0,un:0}; items.forEach(function(it){ c[v4Class(it)]++; }); return c; }

/* ================= v4: My record with attempt columns ================= */
renderRecord = function(){
  showChrome(false);
  var tabLabel=function(id){ var t=TAB_DEFS.find(function(x){return x.id===id;}); return t?t.label:id; };
  var title=(document.querySelector('.chapter-title')||{}).textContent||'';
  var h='<div class="rec-card"><h2>'+esc(student.name)+'’s record</h2><p class="rec-empty" style="margin:0 0 12px;">Roll '+esc(student.roll)+(title?' · '+esc(title):'')+'</p>';
  var st=appState.learning;
  h+='<h3>📘 Learning Sheet — attempts</h3><p class="v4leg"><b>1st ✓</b> correct on the first attempt · <b>2nd ✓</b> correct on the second attempt · <b>Wrong</b> still wrong after two attempts (answer revealed) · <b>Skip</b> skipped<span class="v4left"> · <b>Left</b> not done yet</span></p>';
  if(!st){ h+='<p class="rec-empty">Not started yet.</p>'; }
  else {
    var T={n:0,c1:0,c2:0,w:0,sk:0,un:0};
    h+='<div class="rec-table-wrap"><table class="rec-table v4rec"><thead><tr><th>Sheet</th><th>Qs</th><th>1st ✓</th><th>2nd ✓</th><th>Wrong</th><th>Skip</th><th class="v4left">Left</th></tr></thead><tbody>';
    TAB_DEFS.forEach(function(td){ var tt=st.tabs[td.id]; if(!tt||!tt.items||!tt.items.length) return; var c=v4Counts(tt.items);
      ['n','c1','c2','w','sk','un'].forEach(function(k){ T[k]+=c[k]; });
      h+='<tr><td>'+td.label+'</td><td>'+c.n+'</td><td class="v4g">'+c.c1+'</td><td class="v4o">'+c.c2+'</td><td class="v4r">'+c.w+'</td><td>'+c.sk+'</td><td class="v4left">'+c.un+'</td></tr>'; });
    h+='<tr class="v4tot"><td>Total</td><td>'+T.n+'</td><td class="v4g">'+T.c1+'</td><td class="v4o">'+T.c2+'</td><td class="v4r">'+T.w+'</td><td>'+T.sk+'</td><td class="v4left">'+T.un+'</td></tr>';
    h+='</tbody></table></div>';
    var doneN=T.c1+T.c2+T.w; if(doneN){ h+='<p class="v4sum">Of '+doneN+' questions answered: <b>'+Math.round(T.c1/doneN*100)+'%</b> right first time, <b>'+Math.round(T.c2/doneN*100)+'%</b> right on the second try, <b>'+Math.round(T.w/doneN*100)+'%</b> still wrong after two tries.</p>'; }
  }
  var q=appState.quiz;
  h+='<h3>📝 Quiz Mode</h3>';
  if(!q){ h+='<p class="rec-empty">Not started yet.</p>'; }
  else {
    h+='<div class="rec-table-wrap"><table class="rec-table v4rec"><thead><tr><th>Sheet</th><th>Qs</th><th>Status</th><th>Correct</th><th>Wrong</th></tr></thead><tbody>';
    TAB_DEFS.forEach(function(td){ var tt=q.tabs[td.id]; if(!tt||!tt.items||!tt.items.length) return; var n=tt.items.length, cor=0, att=0;
      tt.items.forEach(function(it){ if(it.status!=='unanswered'||it.choice!==undefined) att++; });
      var rec=records.filter(function(r){ return r.mode==='quiz'&&r.tab===td.id; })[0];
      if(rec){ cor=rec.correct; att=Math.max(att,rec.total); }
      h+='<tr><td>'+td.label+'</td><td>'+n+'</td><td>'+(rec?'Finished':att+' / '+n)+'</td><td class="v4g">'+(rec?cor:'—')+'</td><td class="v4r">'+(rec?(rec.total-cor):'—')+'</td></tr>'; });
    h+='</tbody></table></div>';
  }
  h+='</div><div class="rec-card"><h3>Finished sheets (latest first)</h3>';
  if(!records.length){ h+='<p class="rec-empty">No sheets finished yet. Each time you finish a sheet, your score is recorded here.</p>'; }
  else {
    h+='<div class="rec-table-wrap"><table class="rec-table v4rec"><thead><tr><th>When</th><th>Mode</th><th>Sheet</th><th>Score</th><th>1st ✓</th><th>2nd ✓</th><th>Wrong</th></tr></thead><tbody>';
    records.forEach(function(r){ h+='<tr><td>'+fmtDate(r.at)+'</td><td>'+(r.mode==='quiz'?'Quiz':'Learning')+'</td><td>'+tabLabel(r.tab)+'</td><td>'+r.correct+' / '+r.total+'</td><td>'+(r.c1!=null?r.c1:'—')+'</td><td>'+(r.c2!=null?r.c2:'—')+'</td><td>'+(r.w!=null?r.w:(r.mode==='quiz'?r.total-r.correct:'—'))+'</td></tr>'; });
    h+='</tbody></table></div>';
  }
  h+='</div><button class="btn btn-primary" id="btnBack">'+(MODE?'Back to practice':'Choose a mode')+'</button>';
  document.getElementById('wrap').innerHTML=h;
  document.getElementById('btnBack').addEventListener('click', function(){ if(MODE){ showChrome(true); buildTabbar(); renderSlide(); } else renderModePicker(); });
  window.scrollTo({top:0});
};
var _v4add = addRecord;
addRecord = function(mode, tabId, correct, revealed, skipped, total){
  _v4add(mode, tabId, correct, revealed, skipped, total);
  try{ if(mode==='learning'&&records[0]){ var c=v4Counts(state.tabs[tabId].items); records[0].c1=c.c1; records[0].c2=c.c2; records[0].w=c.w; saveState(); } }catch(e){}
};

/* ================= v4: celebration ================= */
function v4Cracker(){
  var ctx=ensureAudio(); if(!ctx) return; try{ if(ctx.state==='suspended') ctx.resume(); }catch(e){}
  var now=ctx.currentTime;
  function pop(t, vol, dur, hp){
    var len=Math.floor(ctx.sampleRate*dur), buf=ctx.createBuffer(1,len,ctx.sampleRate), d=buf.getChannelData(0);
    for(var i=0;i<len;i++){ d[i]=(Math.random()*2-1)*Math.pow(1-i/len,3); }
    var src=ctx.createBufferSource(); src.buffer=buf;
    var f=ctx.createBiquadFilter(); f.type='highpass'; f.frequency.value=hp;
    var g=ctx.createGain(); g.gain.setValueAtTime(vol,t); g.gain.exponentialRampToValueAtTime(0.001,t+dur);
    src.connect(f); f.connect(g); g.connect(ctx.destination); src.start(t); src.stop(t+dur+0.02);
  }
  pop(now,0.9,0.35,300);                                   // big bang
  for(var k=0;k<14;k++){ pop(now+0.35+Math.random()*1.3, 0.25+Math.random()*0.35, 0.05+Math.random()*0.08, 1500+Math.random()*2500); } // crackles
  [523.25,659.25,783.99,1046.5].forEach(function(fq,i){ var o=ctx.createOscillator(), g=ctx.createGain(); o.type='triangle'; o.frequency.value=fq;
    var t=now+0.15+i*0.12; g.gain.setValueAtTime(0.0001,t); g.gain.exponentialRampToValueAtTime(0.18,t+0.03); g.gain.exponentialRampToValueAtTime(0.001,t+0.5);
    o.connect(g); g.connect(ctx.destination); o.start(t); o.stop(t+0.55); });
}
function v4Confetti(){
  var cv=document.createElement('canvas'); cv.className='v4conf'; document.body.appendChild(cv);
  var W=cv.width=window.innerWidth*(window.devicePixelRatio||1), H=cv.height=window.innerHeight*(window.devicePixelRatio||1), s=(window.devicePixelRatio||1);
  var ctx=cv.getContext('2d'), cols=['#e8b13a','#d9534f','#2e86de','#27ae60','#9b59b6','#f39c12','#1abc9c','#ff6b9a'], P=[];
  function burst(x,y,n){ for(var i=0;i<n;i++){ var a=Math.random()*Math.PI*2, v=(4+Math.random()*9)*s;
    P.push({x:x,y:y,vx:Math.cos(a)*v,vy:Math.sin(a)*v-6*s,w:(6+Math.random()*7)*s,h:(4+Math.random()*5)*s,r:Math.random()*6,vr:(Math.random()-.5)*.4,c:cols[i%cols.length],life:0,flyer:Math.random()<.25}); } }
  burst(W*0.2,H*0.35,90); burst(W*0.8,H*0.35,90); setTimeout(function(){ burst(W*0.5,H*0.25,120); },380); setTimeout(function(){ burst(W*0.35,H*0.3,70); burst(W*0.65,H*0.3,70); },800);
  var t0=performance.now();
  (function frame(t){
    ctx.clearRect(0,0,W,H);
    P.forEach(function(p){ p.vy+=0.22*s; p.vx*=0.985; p.vy*=0.985; p.x+=p.vx; p.y+=p.vy; p.r+=p.vr; p.life++;
      ctx.save(); ctx.translate(p.x,p.y); ctx.rotate(p.r); ctx.fillStyle=p.c;
      if(p.flyer){ ctx.fillRect(-p.w*1.4,-1.5*s,p.w*2.8,3*s); } else { ctx.fillRect(-p.w/2,-p.h/2,p.w,p.h*Math.abs(Math.cos(p.life/6))); }
      ctx.restore(); });
    if(t-t0<4200) requestAnimationFrame(frame); else cv.remove();
  })(t0);
}
function v4NextTab(){
  var i=TAB_DEFS.findIndex(function(t){return t.id===activeTab;});
  for(var j=i+1;j<TAB_DEFS.length;j++){ var id=TAB_DEFS[j].id; if(id!=='theory' && SLIDES[id] && SLIDES[id].length) return TAB_DEFS[j]; }
  return null;
}
function v4Celebrate(){
  var done=document.querySelector('#wrap .done-card'); if(!done || done.dataset.v4) return; done.dataset.v4='1';
  var ts=state.tabs[activeTab], c=v4Counts(ts.items), n=ts.items.length;
  var first=(student&&student.name)?String(student.name).split(' ')[0]:'';
  var pct=MODE==='quiz'?null:Math.round((c.c1+c.c2)/Math.max(n,1)*100);
  var msg = pct===null ? 'You finished this sheet!' : (pct>=90?'Outstanding work!':pct>=75?'Excellent effort!':pct>=50?'Well done — keep going!':'Great persistence — every try makes you stronger!');
  var banner=document.createElement('div'); banner.className='v4ban';
  banner.innerHTML='<div class="v4trophy">🏆</div><div class="v4h">Congratulations'+(first?', '+esc(first):'')+'!</div><div class="v4m">'+msg+'</div>'+
    (MODE==='quiz'?'':'<div class="v4pills"><span class="v4p g">✅ '+c.c1+' first attempt</span><span class="v4p o">🔁 '+c.c2+' second attempt</span><span class="v4p r">❌ '+c.w+' finally wrong</span>'+(c.sk?'<span class="v4p s">⏭ '+c.sk+' skipped</span>':'')+'</div>');
  done.insertBefore(banner, done.firstChild);
  var nx=v4NextTab(), wrapB=document.createElement('div'); wrapB.className='v4next';
  if(nx){ wrapB.innerHTML='<button class="btn btn-primary v4go" id="v4Next">Next sheet: '+nx.label+' →</button>'; }
  else if(SLIDES.report!==undefined || TAB_DEFS.some(function(t){return t.id==='report';})){ wrapB.innerHTML='<button class="btn btn-primary v4go" id="v4Next">📊 View my report →</button>'; }
  else { wrapB.innerHTML='<button class="btn btn-primary v4go" id="v4Next">⌂ Back to the home page</button>'; }
  banner.appendChild(wrapB);
  document.getElementById('v4Next').addEventListener('click',function(){
    var t=nx?nx.id:(TAB_DEFS.some(function(x){return x.id==='report';})?'report':(TAB_DEFS[0]&&TAB_DEFS[0].id));
    activeTab=t; showChrome(true); buildTabbar(); renderSlide(); window.scrollTo({top:0,behavior:'smooth'}); });
  setTimeout(function(){ var r=banner.getBoundingClientRect(); window.scrollBy({top:r.top-110,behavior:'smooth'}); },60);
  v4Confetti(); v4Cracker();
}
var _v4rf = renderFinished;
renderFinished = function(){ _v4rf.apply(this,arguments); try{ v4Celebrate(); }catch(e){ console.log('v4',e); } };


/* ================= calculus answer mode ================= */
function calcCompile(src){
  var s=String(src).replace(/\s+/g,'').replace(/[×∗·]/g,'*').replace(/÷/g,'/').replace(/[−–—]/g,'-')
    .replace(/²/g,'^2').replace(/³/g,'^3').replace(/π/g,'#').replace(/eˣ/g,'e^x');
  if(s.indexOf('=')>=0) s=s.slice(s.lastIndexOf('=')+1);
  var FN=['sqrt','abs','ln','log','exp','sin','cos','tan','sec','csc','cot','pi'];
  var i=0,toks=[];
  while(i<s.length){
    var ch=s[i];
    if(/[0-9.]/.test(ch)){ var j=i; while(j<s.length&&/[0-9.]/.test(s[j])) j++; toks.push({k:'n',v:parseFloat(s.slice(i,j))}); i=j; continue; }
    if(ch==='√'){ toks.push({k:'f',v:'sqrt'}); i++; continue; }
    if(/[a-zA-Z#]/.test(ch)){
      var hit=null; for(var q=0;q<FN.length;q++){ if(s.substr(i,FN[q].length).toLowerCase()===FN[q]){ hit=FN[q]; break; } }
      if(hit==='pi'){ toks.push({k:'v',v:'#'}); i+=2; continue; }
      if(hit){ toks.push({k:'f',v:hit}); i+=hit.length; continue; }
      toks.push({k:'v',v:ch}); i++; continue; }
    if('+-*/^()|'.indexOf(ch)>=0){ toks.push({k:ch}); i++; continue; }
    return null;
  }
  // absolute value bars -> abs( )
  var t2=[],open=false; for(var a=0;a<toks.length;a++){ var tk=toks[a]; if(tk.k==='|'){ if(!open){ t2.push({k:'f',v:'abs'}); t2.push({k:'('}); open=true; } else { t2.push({k:')'}); open=false; } } else t2.push(tk); }
  toks=t2;
  var out=[];
  for(var t=0;t<toks.length;t++){ var A=toks[t], B=out[out.length-1];
    if(B&&(B.k==='n'||B.k==='v'||B.k===')')&&(A.k==='n'||A.k==='v'||A.k==='('||A.k==='f')) out.push({k:'&'});
    out.push(A); }
  var p=0; function pk(){ return out[p]; }
  var F={sqrt:Math.sqrt,ln:Math.log,log:function(x){return Math.log(x)/Math.LN10;},exp:Math.exp,sin:Math.sin,cos:Math.cos,tan:Math.tan,
    sec:function(x){return 1/Math.cos(x);},csc:function(x){return 1/Math.sin(x);},cot:function(x){return 1/Math.tan(x);},abs:Math.abs};
  function E(){ var n=T(); while(pk()&&(pk().k==='+'||pk().k==='-')){ var o=out[p++].k,r=T(); n=(function(l,r,o){return function(e){return o==='+'?l(e)+r(e):l(e)-r(e);};})(n,r,o);} return n; }
  function T(){ var n=I(); while(pk()&&(pk().k==='*'||pk().k==='/')){ var o=out[p++].k,r=I(); n=(function(l,r,o){return function(e){return o==='*'?l(e)*r(e):l(e)/r(e);};})(n,r,o);} return n; }
  function I(){ var n=U(); while(pk()&&pk().k==='&'){ p++; var r=P(); n=(function(l,r){return function(e){return l(e)*r(e);};})(n,r);} return n; }
  function U(){ if(pk()&&pk().k==='-'){ p++; var u=U(); return function(e){return -u(e);}; } if(pk()&&pk().k==='+'){ p++; return U(); } return P(); }
  function P(){ var b=Aa(); if(pk()&&pk().k==='^'){ p++; var x=U(); return function(e){return Math.pow(b(e),x(e));}; } return b; }
  function Aa(){ var t=out[p++]; if(!t) throw 0;
    if(t.k==='n') return function(){return t.v;};
    if(t.k==='v'){ if(t.v==='#') return function(){return Math.PI;}; if(t.v==='e') return function(){return Math.E;}; return function(e){return e[t.v];}; }
    if(t.k==='('){ var n=E(); if(!pk()||pk().k!==')') throw 0; p++; return n; }
    if(t.k==='f'){ var fn=F[t.v]; var ex=null;
      if(pk()&&pk().k==='^'){ p++; ex=Aa(); if(pk()&&pk().k==='&') p++; }            // sin^2(x)
      var arg; if(pk()&&pk().k==='('){ p++; arg=E(); if(!pk()||pk().k!==')') throw 0; p++; } else arg=P();
      return ex? function(e){ return Math.pow(fn(arg(e)),ex(e)); } : function(e){ return fn(arg(e)); }; }
    throw 0; }
  try{ var f=E(); if(p!==out.length) return null; return f; }catch(e){ return null; }
}
function calcEqual(input,answer){
  var f=calcCompile(input), g=calcCompile(answer); if(!f||!g) return false;
  var hits=0;
  for(var trial=0;trial<14;trial++){
    var env={}; 'abcdfghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ'.split('').forEach(function(c){ env[c]=0.35+Math.random()*2.3; });
    var x=f(env), y=g(env); if(!isFinite(x)||!isFinite(y)) continue;
    if(Math.abs(x-y)>1e-6*Math.max(1,Math.abs(x),Math.abs(y))) return false; hits++;
  }
  return hits>=4;
}
(function(){
  var _am=answerMatches;
  answerMatches=function(input,answer,accept,expr){
    if(expr==='calc'){ if(input===undefined||input===null||String(input).trim()==='') return false;
      if(calcEqual(input,answer)) return true; return (accept||[]).some(function(a){ return calcEqual(input,a); }); }
    return _am.apply(this,arguments); };
  var _kl=kbLayoutFor;
  kbLayoutFor=function(inp){ try{ var ts=state.tabs[activeTab], sl=SLIDES[activeTab][ts.idx], stp=sl.flat[parseInt(inp.dataset.step,10)]; if(stp.expr==='calc') return 'calc'; }catch(e){} return _kl(inp); };
  var _kp=kbPress;
  kbPress=function(k){ var m={'eˣ':'e^(','√':'√(','ln':'ln(','sin':'sin(','cos':'cos(','tan':'tan('}; if(KB.page==='calc'&&m[k]){ kbInsert(m[k]); return; } return _kp(k); };
})();

renderLogin();
})();
</script>
</body>
</html>
