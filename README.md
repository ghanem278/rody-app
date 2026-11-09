<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<meta name="theme-color" content="#B8A4E8">
<title>RODY | رودي</title>
<style>
/* ============ 1. VARIABLES ============ */
:root{
  --lav:#B8A4E8; --soft:#D1C4F0; --lilac:#E5DCF8; --pale:#F0EAFB; --deep:#8975B8; --mist:#C7B8E8;
  --pink:#F4DFF0; --cloud:#FAF8FF; --cream:#FFF9F0; --ink:#594A78; --ink2:#3b2f58;
  --accent:#B8A4E8; --gold:#E8C77A;
  --glass:rgba(250,248,255,.58); --glass-b:rgba(255,255,255,.75);
  --serif:"Amiri","Noto Naskh Arabic","Scheherazade New","Traditional Arabic",serif;
  --sans:"Segoe UI","Noto Sans Arabic",Tahoma,system-ui,sans-serif;
}
*{box-sizing:border-box;margin:0;padding:0;-webkit-tap-highlight-color:transparent}
html,body{height:100%}
body{font-family:var(--sans);color:var(--ink);background:var(--pale);overflow:hidden;line-height:1.9}
button{font:inherit;color:inherit;cursor:pointer;border:0;background:none}
:focus-visible{outline:3px solid var(--deep);outline-offset:3px}
svg.sym{width:0;height:0;position:absolute}

/* ============ 2. LAVENDER WORLD BACKGROUND ============ */
#bg{position:fixed;inset:0;z-index:0;overflow:hidden;
  background:radial-gradient(ellipse at 80% 5%,#fff 0%,transparent 45%),
             radial-gradient(ellipse at 10% 40%,rgba(244,223,240,.9),transparent 55%),
             linear-gradient(180deg,#F0EAFB 0%,#E5DCF8 40%,#D1C4F0 75%,#C7B8E8 100%)}
.layer{position:absolute;inset:0;transition:transform .9s ease-out}
.star{position:absolute;width:10px;height:10px;opacity:0;animation:twinkle 7s ease-in-out infinite;color:#fff}
@keyframes twinkle{0%,100%{opacity:0;transform:scale(.6)}50%{opacity:.9;transform:scale(1)}}
.cloud{position:absolute;width:240px;height:64px;border-radius:50%;background:rgba(255,255,255,.7);filter:blur(14px);animation:drift 110s linear infinite}
.cloud.v{background:rgba(184,164,232,.35)}
@keyframes drift{from{transform:translateX(120vw)}to{transform:translateX(-340px)}}
.bubble{position:absolute;bottom:-40px;border-radius:50%;border:1px solid rgba(255,255,255,.8);background:radial-gradient(circle at 30% 30%,rgba(255,255,255,.7),rgba(255,255,255,.08));animation:rise 26s linear infinite}
@keyframes rise{to{transform:translateY(-110vh) translateX(30px)}}
.fly{position:absolute;width:26px;height:20px;animation:path 38s ease-in-out infinite}
.fly svg{width:100%;height:100%;animation:flap .55s ease-in-out infinite alternate}
@keyframes flap{to{transform:scaleX(.45)}}
@keyframes path{0%{transform:translate(0,0)}25%{transform:translate(-30vw,-12vh)}50%{transform:translate(-10vw,-30vh)}75%{transform:translate(-40vw,-8vh)}100%{transform:translate(0,0)}}
.ring{position:absolute;border:1px solid rgba(137,117,184,.25);border-radius:50%;animation:ring 16s ease-out infinite;opacity:0}
@keyframes ring{0%{transform:scale(.2);opacity:.6}100%{transform:scale(1.5);opacity:0}}
.waves{position:absolute;bottom:0;left:0;width:200%;height:24vh;animation:wave 44s linear infinite}
.waves.w2{animation-duration:66s;animation-direction:reverse;bottom:-2vh}
@keyframes wave{to{transform:translateX(-50%)}}
.lav{position:absolute;bottom:0;width:40px;height:120px;transform-origin:50% 100%;animation:sway 7s ease-in-out infinite alternate}
@keyframes sway{from{transform:rotate(-4deg)}to{transform:rotate(4deg)}}
.mote{position:absolute;width:5px;height:5px;border-radius:50%;background:#fff;opacity:.6;filter:blur(.5px);animation:floaty 24s ease-in-out infinite}
@keyframes floaty{50%{transform:translate(24px,-50px)}}

/* ============ 3. LAYOUT ============ */
#app{position:relative;z-index:1;height:100%;max-width:560px;margin:0 auto;display:flex;flex-direction:column}
header{display:flex;align-items:center;justify-content:space-between;gap:8px;padding:calc(10px + env(safe-area-inset-top)) 14px 6px}
.logo{font-family:var(--serif);font-size:1.45rem;color:var(--ink2);letter-spacing:.03em}
.logo small{font-family:var(--sans);font-size:.7rem;opacity:.7;margin-inline-start:6px}
.icon-btn{width:44px;height:44px;border-radius:50%;background:var(--glass);border:1px solid var(--glass-b);backdrop-filter:blur(10px);font-size:1.15rem;box-shadow:0 4px 14px rgba(137,117,184,.25)}
main{flex:1;overflow-y:auto;padding:6px 16px 160px;scrollbar-width:none}
main::-webkit-scrollbar{display:none}
.view{display:none}
.view.active{display:block;animation:fade .7s ease both}
@keyframes fade{from{opacity:0;transform:translateY(8px)}to{opacity:1;transform:none}}
h2{font-family:var(--serif);font-weight:700;font-size:1.65rem;line-height:1.5;margin:12px 0 4px;color:var(--ink2)}
h3{font-family:var(--serif);font-size:1.25rem;color:var(--ink2);margin-bottom:6px}
.sub{opacity:.9;font-size:.95rem;margin-bottom:12px}
.card{background:var(--glass);border:1px solid var(--glass-b);border-radius:28px;padding:20px;margin:14px 0;
  backdrop-filter:blur(16px);-webkit-backdrop-filter:blur(16px);box-shadow:0 12px 36px rgba(137,117,184,.22)}
.card.hero{background:linear-gradient(145deg,rgba(255,255,255,.85),rgba(244,223,240,.7))}
.msg{font-family:var(--serif);font-size:1.4rem;line-height:2;text-align:center;min-height:3.5em;color:var(--ink2)}
.tiny{font-size:.82rem;opacity:.8}
.btn{position:relative;overflow:hidden;display:inline-flex;align-items:center;justify-content:center;gap:8px;min-height:44px;
  padding:11px 22px;border-radius:999px;color:var(--ink2);font-weight:600;
  background:linear-gradient(135deg,var(--pink),var(--lav));border:1px solid var(--glass-b);box-shadow:0 8px 20px rgba(137,117,184,.35);transition:transform .25s,box-shadow .25s}
.btn:hover{transform:translateY(-2px)}
.btn.big{padding:15px 34px;font-size:1.1rem}
.btn.soft{background:var(--glass);box-shadow:0 4px 12px rgba(137,117,184,.2)}
.btn.gold{background:linear-gradient(135deg,#fff3cf,var(--gold))}
.btn.sm{padding:8px 16px;font-size:.9rem;min-height:40px}
.row{display:flex;flex-wrap:wrap;gap:10px;justify-content:center;margin-top:12px}
.rip{position:absolute;border-radius:50%;background:rgba(255,255,255,.6);transform:scale(0);animation:rip .7s ease-out forwards;pointer-events:none}
@keyframes rip{to{transform:scale(3);opacity:0}}

/* Nav */
nav{position:fixed;bottom:0;left:50%;transform:translateX(-50%);width:min(560px,100%);z-index:5;display:flex;justify-content:space-around;
  padding:6px 4px calc(6px + env(safe-area-inset-bottom));background:rgba(250,248,255,.82);backdrop-filter:blur(18px);-webkit-backdrop-filter:blur(18px);
  border-top:1px solid var(--glass-b);border-radius:24px 24px 0 0;box-shadow:0 -8px 30px rgba(137,117,184,.2)}
nav button{flex:1;display:flex;flex-direction:column;align-items:center;font-size:.66rem;padding:4px 2px;border-radius:14px;opacity:.7;transition:.3s;line-height:1.4;min-height:48px}
nav button span{font-size:1.25rem}
nav button.on{opacity:1;background:var(--lilac);font-weight:700}
#cant{position:fixed;z-index:6;inset-inline-start:12px;bottom:calc(76px + env(safe-area-inset-bottom));font-size:.74rem;padding:6px 12px;border-radius:999px;
  background:rgba(250,248,255,.9);border:1px solid var(--glass-b);opacity:.85;box-shadow:0 4px 12px rgba(137,117,184,.2)}

/* Moods & chips */
.moods{display:grid;grid-template-columns:1fr 1fr;gap:10px}
.mood{padding:12px 10px;border-radius:20px;background:rgba(255,255,255,.6);border:1px solid var(--glass-b);text-align:center;transition:.3s;font-size:.95rem;min-height:56px}
.mood.on,.mood:hover{background:var(--lilac);transform:translateY(-2px);box-shadow:0 6px 16px rgba(137,117,184,.3)}
.chips{display:flex;flex-wrap:wrap;gap:8px;justify-content:center}
.chip{padding:8px 14px;border-radius:999px;background:rgba(255,255,255,.65);border:1px solid var(--glass-b);font-size:.88rem;transition:.3s;min-height:40px}
.chip.on{background:var(--lav);color:var(--ink2);font-weight:700}

/* Gift box */
.gift{position:relative;display:block;width:180px;height:200px;margin:26px auto 6px;background:none}
.glow{position:absolute;left:50%;top:50%;width:320px;height:320px;margin:-160px;border-radius:50%;background:radial-gradient(circle,rgba(184,164,232,.6),transparent 65%);opacity:.6;transition:.8s;animation:gl 5s ease-in-out infinite}
.gift.open .glow{opacity:1;transform:scale(1.25)}
@keyframes gl{50%{transform:scale(1.1)}}
.gbody{position:absolute;bottom:0;left:14px;right:14px;height:118px;border-radius:16px;background:linear-gradient(160deg,#C7B8E8,#8975B8);box-shadow:inset -10px -10px 24px rgba(89,74,120,.35),inset 8px 8px 18px rgba(255,255,255,.35),0 18px 30px rgba(89,74,120,.35)}
.gbody::after{content:"";position:absolute;left:50%;width:24px;margin-left:-12px;top:0;bottom:0;background:linear-gradient(90deg,#fbe9f6,var(--pink),#e9c8e0)}
.glid{position:absolute;bottom:108px;left:3px;right:3px;height:46px;border-radius:16px;transform-origin:left bottom;background:linear-gradient(160deg,#D1C4F0,#9c88cc);
  transition:transform .8s cubic-bezier(.3,1.4,.5,1);box-shadow:inset 6px 6px 14px rgba(255,255,255,.4),0 8px 16px rgba(89,74,120,.3)}
.glid::after{content:"";position:absolute;left:50%;width:24px;margin-left:-12px;top:0;bottom:0;background:linear-gradient(90deg,#fbe9f6,var(--pink),#e9c8e0)}
.glid::before{content:"";position:absolute;top:-24px;left:50%;width:50px;height:30px;margin-left:-25px;z-index:2;
  background:radial-gradient(ellipse at 25% 60%,var(--pink) 45%,transparent 47%),radial-gradient(ellipse at 75% 60%,var(--pink) 45%,transparent 47%)}
.gift.open .glid{transform:translateY(-28px) rotate(-26deg)}
.gift.shake{animation:shake .5s}
@keyframes shake{20%{transform:rotate(-4deg)}40%{transform:rotate(4deg)}60%{transform:rotate(-3deg)}80%{transform:rotate(2deg)}}
.burst{position:fixed;pointer-events:none;z-index:30;width:20px;height:20px;animation:burst 1.5s ease-out forwards}
@keyframes burst{to{transform:translate(var(--dx),var(--dy)) scale(.4);opacity:0}}
.bup{position:fixed;pointer-events:none;z-index:31;width:30px;height:24px;animation:bup 3s ease-out forwards}
.bup svg{width:100%;height:100%;animation:flap .5s ease-in-out infinite alternate}
@keyframes bup{to{transform:translate(var(--dx),var(--dy));opacity:0}}
.fall{position:fixed;top:-30px;z-index:40;pointer-events:none;animation:fall linear forwards}
@keyframes fall{to{transform:translateY(110vh) rotate(360deg);opacity:.3}}
.flystar{position:fixed;z-index:35;width:30px;height:30px;pointer-events:none;animation:fs 1.2s ease-out forwards}
@keyframes fs{to{transform:translateY(-160px) scale(1.5) rotate(40deg);opacity:0}}

/* Points */
.big{font-family:var(--serif);font-size:2.2rem;text-align:center;color:var(--ink2)}
.bar{height:16px;border-radius:99px;background:rgba(137,117,184,.2);overflow:hidden;margin:10px 0}
.bar i{display:block;height:100%;width:0;border-radius:99px;background:linear-gradient(90deg,var(--lav),var(--pink),var(--gold));transition:width 1s cubic-bezier(.3,1,.4,1)}
.bump{animation:bump .6s}
@keyframes bump{40%{transform:scale(1.15)}}
.stars-row{display:flex;flex-wrap:wrap;gap:6px;justify-content:center;min-height:34px}
.stars-row svg{width:30px;height:30px}

/* Activities */
.grid7{display:flex;flex-wrap:wrap;gap:10px;justify-content:center}
.pick{width:52px;height:52px;border-radius:50%;background:rgba(255,255,255,.6);display:grid;place-items:center;transition:.3s}
.pick svg{width:34px;height:34px}
.pick:hover,.pick.on{transform:scale(1.15);background:var(--lilac);box-shadow:0 0 18px var(--gold)}
.bstage{position:relative;height:200px;border-radius:22px;overflow:hidden;background:linear-gradient(180deg,rgba(255,255,255,.5),rgba(209,196,240,.5))}
.bfly{position:absolute;width:60px;height:46px;transition:transform 3.2s ease-in-out;cursor:pointer;background:none}
.bfly svg{width:100%;height:100%;animation:flap .5s ease-in-out infinite alternate;filter:drop-shadow(0 4px 8px rgba(137,117,184,.4))}
.swatches{display:grid;grid-template-columns:repeat(5,1fr);gap:10px}
.sw{aspect-ratio:1;border-radius:50%;border:3px solid #fff;box-shadow:0 4px 10px rgba(137,117,184,.3);transition:.3s}
.sw.on{transform:scale(1.15);border-color:var(--ink2)}

/* Nature */
svg.scene{width:100%;height:auto;display:block;border-radius:22px;box-shadow:0 12px 30px rgba(137,117,184,.3)}
.scene .c1{animation:scl 60s linear infinite}.scene .c2{animation:scl 90s linear infinite reverse}
@keyframes scl{from{transform:translateX(-60px)}to{transform:translateX(60px)}}
.scene .w1{animation:sw 8s ease-in-out infinite alternate}.scene .w2{animation:sw 11s ease-in-out infinite alternate-reverse}.scene .w3{animation:sw 14s ease-in-out infinite alternate}
@keyframes sw{to{transform:translateX(-50px)}}
.scene .sh{animation:sh 3.5s ease-in-out infinite alternate}
@keyframes sh{from{opacity:.2}to{opacity:.8}}
.scene .bd{animation:bd 30s linear infinite}
@keyframes bd{from{transform:translateX(420px)}to{transform:translateX(-60px)}}
.srow{display:grid;grid-template-columns:auto 1fr;gap:6px 12px;align-items:center;padding:12px 0;border-bottom:1px solid rgba(137,117,184,.2)}
.srow .nm{font-weight:700}
.srow .ctl{grid-column:1/-1;display:flex;align-items:center;gap:10px}
.srow .st{grid-column:1/-1;font-size:.8rem;opacity:.85;min-height:1.2em}
.sbtn{min-width:96px}
.sbtn.on{background:linear-gradient(135deg,#fff3cf,var(--gold))}
input[type=range]{accent-color:var(--deep);flex:1}
textarea,input[type=date]{width:100%;border-radius:18px;padding:14px;border:1px solid var(--glass-b);background:rgba(255,255,255,.75);color:var(--ink2);font:inherit;resize:vertical}
textarea{min-height:130px}
.note{padding:12px 14px;border-radius:16px;background:rgba(255,255,255,.6);margin-top:10px;white-space:pre-wrap;word-break:break-word}
.note small{display:block;opacity:.7;margin-top:4px}

/* Overlays */
.ov{position:fixed;inset:0;z-index:50;display:none;place-items:center;padding:22px;background:rgba(89,74,120,.45);backdrop-filter:blur(8px)}
.ov.show{display:grid;animation:fade .5s both}
.ov .card{max-width:440px;width:100%;max-height:88vh;overflow-y:auto;background:rgba(250,248,255,.92)}
.ov.rw{background:radial-gradient(circle,rgba(184,164,232,.75),rgba(89,74,120,.55))}
.bigstar{width:96px;height:96px;margin:0 auto;display:block;animation:spin 6s ease-in-out infinite;filter:drop-shadow(0 0 18px var(--gold))}
@keyframes spin{50%{transform:scale(1.15) rotate(8deg)}}
.set-row{display:flex;justify-content:space-between;align-items:center;padding:10px 0;border-bottom:1px solid rgba(137,117,184,.25);gap:10px}
.set-row input[type=checkbox]{width:24px;height:24px;accent-color:var(--deep)}
.welcome{position:fixed;inset:0;z-index:60;display:grid;place-items:center;padding:28px;text-align:center;overflow:hidden;
  background:radial-gradient(ellipse at 50% 20%,#fff,transparent 60%),linear-gradient(180deg,#E5DCF8,#D1C4F0 60%,#B8A4E8);transition:opacity 1.1s}
.welcome.gone{opacity:0;pointer-events:none}
.welcome h1{font-family:var(--serif);font-size:3.2rem;letter-spacing:.15em;color:var(--ink2);text-shadow:0 4px 24px rgba(255,255,255,.9)}
.welcome p{margin:12px auto;max-width:360px}
.welcome .l{font-family:var(--serif);font-size:1.4rem;color:var(--ink2)}
.welcome .fly{opacity:.9}
.reduce *,.reduce *::before,.reduce *::after{animation:none!important}
.reduce .star{opacity:.6}
@media (prefers-reduced-motion:reduce){*,*::before,*::after{animation:none!important}.star{opacity:.6}}
</style>
</head>
<body>

<!-- SVG symbols -->
<svg class="sym" aria-hidden="true"><defs>
  <linearGradient id="gStar" x1="0" y1="0" x2="1" y2="1"><stop offset="0" stop-color="#FFF3CF"/><stop offset="1" stop-color="#E8C77A"/></linearGradient>
  <linearGradient id="gWing" x1="0" y1="0" x2="1" y2="1"><stop offset="0" stop-color="#F4DFF0"/><stop offset="1" stop-color="#B8A4E8"/></linearGradient>
  <symbol id="st" viewBox="0 0 24 24"><polygon points="12,2 14.9,8.6 22,9.3 16.6,14 18.2,21 12,17.3 5.8,21 7.4,14 2,9.3 9.1,8.6" stroke-linejoin="round" stroke="#fff" stroke-width="1"/></symbol>
  <symbol id="bf" viewBox="0 0 40 30"><path d="M20 15 C12 1 1 4 4 14 C6 21 14 22 20 15Z" fill="url(#gWing)" stroke="#8975B8" stroke-width=".8"/><path d="M20 15 C28 1 39 4 36 14 C34 21 26 22 20 15Z" fill="url(#gWing)" stroke="#8975B8" stroke-width=".8"/><path d="M20 15 C14 20 9 27 14 28 C18 29 20 22 20 15Z" fill="#C7B8E8"/><path d="M20 15 C26 20 31 27 26 28 C22 29 20 22 20 15Z" fill="#C7B8E8"/><ellipse cx="20" cy="15" rx="1.4" ry="7" fill="#594A78"/></symbol>
  <symbol id="lv" viewBox="0 0 40 120"><path d="M20 120 C20 80 18 50 20 20" stroke="#91AA9B" stroke-width="2" fill="none"/><g fill="#B8A4E8"><ellipse cx="20" cy="14" rx="4" ry="7"/><ellipse cx="14" cy="28" rx="4" ry="7" transform="rotate(-20 14 28)"/><ellipse cx="26" cy="30" rx="4" ry="7" transform="rotate(20 26 30)"/><ellipse cx="13" cy="46" rx="4" ry="7" transform="rotate(-18 13 46)"/><ellipse cx="27" cy="48" rx="4" ry="7" transform="rotate(18 27 48)"/></g><g fill="#8975B8"><ellipse cx="20" cy="38" rx="4" ry="7"/><ellipse cx="20" cy="58" rx="4" ry="7"/></g></symbol>
</defs></svg>

<!-- Living background -->
<div id="bg" aria-hidden="true">
  <div class="layer" id="lyFar"></div>
  <div class="layer" id="lyMid"></div>
  <div class="layer" id="lyNear">
    <svg class="waves" viewBox="0 0 1440 200" preserveAspectRatio="none"><defs><linearGradient id="wg1" x1="0" y1="0" x2="0" y2="1"><stop offset="0" stop-color="#E5DCF8" stop-opacity=".8"/><stop offset="1" stop-color="#B8A4E8" stop-opacity=".9"/></linearGradient></defs><path fill="url(#wg1)" d="M0 100 C120 60 240 140 360 100 S600 60 720 100 S960 140 1080 100 S1320 60 1440 100 V200 H0Z"/></svg>
    <svg class="waves w2" viewBox="0 0 1440 200" preserveAspectRatio="none"><path fill="rgba(137,117,184,.55)" d="M0 120 C120 80 240 160 360 120 S600 80 720 120 S960 160 1080 120 S1320 80 1440 120 V200 H0Z"/></svg>
    <div id="lavBox"></div>
  </div>
</div>

<!-- Welcome -->
<div class="welcome" id="welcome">
  <div id="wfly"></div>
  <div style="position:relative">
    <h1>🦋 RODY 🦋</h1>
    <p class="l">أهلاً يا رودي يا جميلة! 🌷</p>
    <p>مستعدة نشوف إيه الحاجات الحلوة اللي مستنياكي النهارده؟</p>
    <div class="row"><button class="btn big" id="startBtn">يلا نبدأ يا قمر ✨</button></div>
    <p class="tiny" style="margin-top:22px">خلي يومك مليان حاجات حلوة ولو صغيرة.</p>
  </div>
</div>

<div id="app">
  <header>
    <button class="icon-btn" id="back" aria-label="رجوع" style="visibility:hidden">➜</button>
    <div class="logo">RODY<small>رودي</small></div>
    <button class="icon-btn" id="setBtn" aria-label="الإعدادات">⚙️</button>
  </header>

  <main id="main">
    <!-- HOME -->
    <section class="view active" id="v-home">
      <div class="card hero">
        <h3>رسالة صغيرة ليكي يا رودي 💜</h3>
        <div class="tiny" id="today"></div>
        <div class="msg" id="dailyMsg"></div>
        <div class="row"><button class="btn sm soft" id="dailyMore">رسالة تانية 🦋</button></div>
      </div>

      <div class="card">
        <h3>إيه مود رودي النهارده؟</h3>
        <div class="moods" id="moods"></div>
        <div class="msg" id="moodReply" style="font-size:1.2rem;min-height:0;margin-top:12px"></div>
      </div>

      <div class="card">
        <h3>كمان حاجات حلوة</h3>
        <div class="row" style="margin-top:0">
          <button class="btn sm" data-go="box">🎁 صندوق المفاجآت</button>
          <button class="btn sm" data-go="act">🦋 الأنشطة</button>
          <button class="btn sm" data-go="nature">🌊 عالم الطبيعة</button>
        </div>
      </div>
    </section>

    <!-- BOX -->
    <section class="view" id="v-box">
      <h2>صندوق المفاجآت 🎁</h2>
      <p class="sub">فيه رسالة جديدة مستنياكي يا قمر.. افتحيه.</p>
      <button class="gift" id="gift" aria-label="افتحي الصندوق"><div class="glow"></div><div class="gbody"></div><div class="glid"></div></button>
      <div class="card hero" id="boxCard" style="display:none"><div class="msg" id="boxMsg"></div></div>
      <div class="row"><button class="btn" id="boxMore">افتحي مفاجأة تانية ✨</button></div>
    </section>

    <!-- STARS -->
    <section class="view" id="v-stars">
      <h2>نجوم رودي الحلوة</h2>
      <p class="sub">كل حاجة حلوة بتعمليها تستاهل نجمة. إنتِ اللي بتقرري إمتى، ومفيش عدد ولا ميعاد.</p>
      <div class="card hero">
        <div class="big" id="ptsBig">0 / 100</div>
        <div class="bar"><i id="ptsBar"></i></div>
        <div class="tiny" style="text-align:center" id="ptsPct">0%</div>
        <div class="msg" id="ptsMsg" style="min-height:2em;font-size:1.15rem"></div>
        <div class="row"><button class="btn gold big" id="plus">أضيفي نجمة لنفسك +1 ⭐</button></div>
      </div>
      <div class="card">
        <div class="tiny" style="text-align:center">النجوم المميزة اللي معاكي</div>
        <div class="stars-row" id="starsRow"></div>
        <div class="tiny" style="text-align:center;margin-top:6px" id="totalTxt"></div>
      </div>
      <div class="card hero" id="finalCard" style="display:none"><div class="msg" id="finalTxt" style="font-size:1.15rem;text-align:start;white-space:pre-line"></div></div>
    </section>

    <!-- ACTIVITIES -->
    <section class="view" id="v-act">
      <h2>الأنشطة اللطيفة 🦋</h2>
      <p class="sub">كلها اختيارية وللمرح بس.</p>

      <div class="card">
        <h3>اختاري نجمتك ⭐</h3>
        <div class="grid7" id="pickStars"></div>
        <div class="msg" id="pickMsg" style="font-size:1.15rem;min-height:2em;margin-top:10px"></div>
      </div>

      <div class="card">
        <h3>فراشة الحظ 🦋</h3>
        <div class="bstage" id="bstage"><button class="bfly" id="bfly" aria-label="فراشة الحظ"><svg viewBox="0 0 40 30"><use href="#bf"/></svg></button></div>
        <div class="msg" id="bfMsg" style="font-size:1.15rem;min-height:2em;margin-top:10px">اضغطي على الفراشة لو قدرتي تمسكيها 😄</div>
      </div>

      <div class="card">
        <h3>صندوق الألوان 🎨</h3>
        <div class="swatches" id="swatches"></div>
        <div class="msg" id="colMsg" style="font-size:1.1rem;min-height:2em;margin-top:10px">اختاري لون لافندر بيفرحك.</div>
      </div>

      <div class="card">
        <h3>تحدي اليوم اللطيف 🌷</h3>
        <div class="msg" id="chMsg" style="font-size:1.2rem"></div>
        <div class="row"><button class="btn sm soft" id="chMore">فكرة تانية</button><button class="btn sm" id="chDone">جربتها ✨</button></div>
        <p class="tiny" style="text-align:center;margin-top:8px">مش لازم تعمليه، هو مجرد فكرة حلوة لو حبيتي.</p>
      </div>
    </section>

    <!-- NATURE -->
    <section class="view" id="v-nature">
      <h2>عالم الطبيعة 🌊</h2>
      <p class="sub">خدي لحظة لنفسك يا جميلة.. واستمتعي بصوت الطبيعة.</p>

      <svg class="scene" viewBox="0 0 400 230" aria-label="مشهد البحر">
        <defs>
          <linearGradient id="sk" x1="0" y1="0" x2="0" y2="1"><stop offset="0" stop-color="#B8A4E8"/><stop offset=".55" stop-color="#E5DCF8"/><stop offset="1" stop-color="#F4DFF0"/></linearGradient>
          <linearGradient id="sea" x1="0" y1="0" x2="0" y2="1"><stop offset="0" stop-color="#C7B8E8"/><stop offset="1" stop-color="#8975B8"/></linearGradient>
          <radialGradient id="sun"><stop offset="0" stop-color="#fff" stop-opacity=".95"/><stop offset="1" stop-color="#fff" stop-opacity="0"/></radialGradient>
        </defs>
        <rect width="400" height="230" fill="url(#sk)"/>
        <circle cx="290" cy="95" r="60" fill="url(#sun)"/><circle cx="290" cy="95" r="15" fill="#FFF9F0"/>
        <g class="c1" fill="#fff" opacity=".8"><ellipse cx="90" cy="50" rx="50" ry="12"/><ellipse cx="120" cy="42" rx="30" ry="10"/></g>
        <g class="c2" fill="#FAF8FF" opacity=".7"><ellipse cx="300" cy="32" rx="45" ry="10"/><ellipse cx="270" cy="38" rx="28" ry="8"/></g>
        <g class="bd" fill="none" stroke="#594A78" stroke-width="1.5" stroke-linecap="round"><path d="M0 70 q5 -6 10 0 q5 -6 10 0"/><path d="M30 82 q4 -5 8 0 q4 -5 8 0"/></g>
        <rect y="112" width="400" height="118" fill="url(#sea)"/>
        <g stroke="#fff" stroke-width="2" stroke-linecap="round" fill="none"><path class="sh" d="M270 124 h40"/><path class="sh" d="M278 134 h26" style="animation-delay:.8s"/><path class="sh" d="M265 146 h50" style="animation-delay:1.6s"/><path class="sh" d="M283 160 h18" style="animation-delay:2.2s"/></g>
        <path class="w1" fill="rgba(229,220,248,.55)" d="M-60 150 C0 134 60 166 120 150 S240 134 300 150 S420 166 480 150 V230 H-60Z"/>
        <path class="w2" fill="rgba(184,164,232,.6)" d="M-60 178 C0 162 60 194 120 178 S240 162 300 178 S420 194 480 178 V230 H-60Z"/>
        <path class="w3" fill="rgba(250,248,255,.5)" d="M-60 205 C0 190 60 220 120 205 S240 190 300 205 S420 220 480 205 V230 H-60Z"/>
      </svg>

      <div class="card">
        <h3>أصوات الطبيعة</h3>
        <p class="tiny">مفيش أي صوت بيشتغل لوحده. دوسي على اللي بتحبيه، وتقدري توقفيه وقت ما تحبي.</p>
        <div id="sounds"></div>
        <div class="row">
          <button class="btn sm soft" id="muteAll">🔇 كتم كل الأصوات</button>
        </div>
        <p class="tiny" style="margin-top:10px">الأصوات بتتحمّل من فولدر <b>sounds</b> جنب الملف (اسم الملف زي sea.mp3). ولو الصوت مش موجود، اختاري ملف من جهازك بزرار 📁 وهيتحفظ هنا.</p>
      </div>
    </section>

    <!-- MESSAGES -->
    <section class="view" id="v-msgs">
      <h2>رسائلي 💌</h2>
      <p class="sub">اختاري اللي يعجبك، وهتلاقي رسالة حلوة.</p>
      <div class="chips" id="chips"></div>
      <div class="card hero" id="libCard" style="display:none"><div class="msg" id="libMsg" style="font-size:1.25rem"></div></div>

      <h2 style="font-size:1.3rem;margin-top:26px">مساحتي الصغيرة 📝</h2>
      <p class="sub">اللي بتكتبيه بيتحفظ على جهازك إنتِ بس، ومش بيتبعت لأي مكان.</p>
      <div class="card">
        <textarea id="noteTxt" placeholder="اكتبي أي حاجة تحبي تحتفظي بيها.."></textarea>
        <div class="row">
          <button class="btn sm" id="noteSave">احفظي لنفسك</button>
          <button class="btn sm soft" id="noteClear">امسحي الكلام</button>
          <button class="btn sm gold" id="toLetter">رسالة لنفسي بعد فترة</button>
        </div>
      </div>
      <div class="card" id="letterBox" style="display:none">
        <div class="sub">اكتبي رسالة، واختاري يوم تتفتح فيه.</div>
        <textarea id="letTxt" placeholder="يا رودي.. "></textarea>
        <div style="margin-top:10px"><input type="date" id="letDate"></div>
        <div class="row"><button class="btn sm gold" id="letSave">اقفلي الرسالة لحد الميعاد</button></div>
      </div>
      <h3 style="margin-top:14px">رسايلك لنفسك</h3><div id="letters"></div>
      <h3 style="margin-top:14px">اللي حفظتيه</h3><div id="notes"></div>
      <p class="tiny" style="text-align:center;padding:14px 6px">المساحة دي للبهجة واللحظات الحلوة، ومش بديل عن دعم شخص تثقي فيه أو مساعدة متخصصة لما تحتاجيها.</p>
    </section>
  </main>

  <button id="cant">مش قادرة أتكلم</button>

  <nav id="nav">
    <button data-v="home" class="on"><span>🏠</span>الرئيسية</button>
    <button data-v="box"><span>🎁</span>صندوق المفاجآت</button>
    <button data-v="stars"><span>⭐</span>نجومي</button>
    <button data-v="act"><span>🦋</span>الأنشطة</button>
    <button data-v="nature"><span>🌊</span>عالم الطبيعة</button>
    <button data-v="msgs"><span>💌</span>رسائلي</button>
  </nav>
</div>

<!-- Overlays -->
<div class="ov" id="ovCant"><div class="card hero">
  <div class="msg">مش لازم تتكلمي.. ممكن بس تاخدي وقتك، وممكن تطلبي من شخص تثقي فيه يقعد جنبك.</div>
  <p class="tiny" style="text-align:center">ومفيش حاجة مطلوبة منك هنا.</p>
  <div class="row"><button class="btn sm" id="cantOk">تمام</button><button class="btn sm soft" id="cantNat">عالم الطبيعة</button></div>
</div></div>

<div class="ov rw" id="ovReward"><div class="card hero">
  <svg class="bigstar" viewBox="0 0 24 24"><use href="#st" fill="url(#gStar)"/></svg>
  <div class="msg" id="rwTitle" style="min-height:0;font-size:1.5rem"></div>
  <div class="msg" id="rwTxt" style="font-size:1.1rem;text-align:start;white-space:pre-line;min-height:0"></div>
  <div class="row"><button class="btn gold big" id="rwClaim">استلمي نجمتك ⭐</button></div>
</div></div>

<div class="ov" id="ovSet"><div class="card">
  <h3>الإعدادات</h3>
  <p class="tiny">كل حاجة بإيدك، ومفيش أي صوت بيبدأ لوحده.</p>
  <label class="set-row"><span>🍃 مؤثرات طبيعية صغيرة (لو ملفاتها موجودة)</span><input type="checkbox" id="setFx"></label>
  <label class="set-row"><span>🕊️ تقليل الحركة</span><input type="checkbox" id="setReduce"></label>
  <div class="row"><button class="btn sm soft" id="setMute">🔇 كتم كل الأصوات</button><button class="btn sm" id="setOk">تمام</button></div>
</div></div>

<script>
/* ==========================================================
   RODY | رودي  -  الرسائل + منطق اللعبة
   ========================================================== */

/* ---------- A. صندوق المفاجآت: 156 رسالة في 12 تصنيف ---------- */
const BOX = {
  motivation:[
    "يا جميلة، النهارده فرصة جديدة تعملي فيها حاجة تفرحك.",
    "ابدأي بخطوة صغيرة، والباقي بيتظبط وإنتِ ماشية يا بطلة.",
    "يا شطورة، مش لازم تكوني جاهزة 100% علشان تبدئي.",
    "كل حاجة كبيرة بدأت بحاجة صغيرة، وإنتِ بدأتي فعلاً.",
    "جربي حاجة واحدة بس مختلفة النهارده، وشوفي هتحسي بإيه.",
    "يا نجمة، لو الطريق طويل يبقى نفرح بكل خطوة فيه.",
    "إنتِ أقدر مما بتتخيلي بكتير، جربي وشوفي.",
    "الحماس بييجي لما نبدأ، فابدأي من أي حتة.",
    "اعملي حاجة صغيرة بتحبيها، وخلي اليوم يمشي وراكي.",
    "يا رودي، خطوتك مهما كانت صغيرة بتقربك لحاجة حلوة.",
    "خلي عندك فضول تشوفي الحاجات الحلوة اللي لسه جاية.",
    "ماتستنيش الوقت المناسب، اصنعيه بنفسك يا قمر.",
    "اللي بيحاول بيكسب، حتى لو النتيجة ماظهرتش لسه."],
  confidence:[
    "إنتِ مش محتاجة تكوني مثالية علشان تكوني مميزة.",
    "يا قمر، متنسيش إنك تستاهلي كل الحاجات الحلوة.",
    "رأيك ليه وزن، وصوتك يستاهل يتسمع يا جميلة.",
    "ثقي في نفسك، إنتِ عدّيتي من أصعب من كده.",
    "فيكي حاجات مميزة مفيش حد غيرك عنده.",
    "إنتِ نسخة واحدة في الدنيا، وده ميزة مش عيب.",
    "يا شطورة، ثقتك بنفسك بتكبر كل ما تجربي.",
    "مش لازم توافقي الكل علشان تكوني على حق.",
    "اللي بتعمليه بإخلاص بيبان حتى لو محدش قال.",
    "اقفي بضهرك مفرود، إنتِ تستاهلي مكانك يا رودي.",
    "لما تترددي، افتكري آخر مرة نجحتي فيها.",
    "قيمتك ثابتة، مهما كان اليوم زحمة أو هادي.",
    "إنتِ قادرة تتعلمي أي حاجة بتحبيها."],
  pamper:[
    "ابتسامتك تستاهل تشوفيها كتير، فمتنسيش تدلعي نفسك شوية.",
    "اعملي لنفسك مشروب بتحبيه وخديه براحتك.",
    "النهارده يوم يستاهل حاجة حلوة بجد يا جميلة.",
    "حطي ريحة حلوة، شغلي صوت بتحبيه، واعتبريه يوم دلع.",
    "إنتِ تستاهلي حاجة صغيرة تفرحك النهارده.",
    "خدي دش دافي وحسي إن اليوم اتغسل معاه.",
    "البسي حاجة بتحبيها بس علشان نفسك يا قمر.",
    "الدلع مش رفاهية، ده حق صغير ليكي.",
    "اقعدي في أحلى ركن في البيت واستمتعي بيه.",
    "دلعي نفسك زي ما بتدلعي أغلى صحابك.",
    "كوباية شاي وكتاب أو فيلم حلو.. خطة مظبوطة.",
    "خدي لنفسك عشر دقايق من غير مطالب، دي هدية.",
    "حاجة حلوة صغيرة النهارده، وإنتِ اللي تختاريها."],
  encourage:[
    "يا شطورة، كل خطوة بتاخديها ناحية حلمك تستاهل الفخر.",
    "برافو عليكي على كل محاولة، حتى اللي ماكملتش.",
    "إنتِ بتتحسني أكتر مما بتلاحظي.",
    "كملي يا بطلة، إنتِ ماشية صح بطريقتك.",
    "الغلطة جزء من الطريق، وإنتِ بتتعلمي منها.",
    "افتكري إنك تقدري تتعلمي وتجربي وتغلطي وتبدئي من جديد.",
    "حتى لو بالراحة، المهم إنك بتتحركي.",
    "فخورة بيكي على اللي حاولتيه النهارده.",
    "إنتِ عملتي أكتر مما تتخيلي، بصي ورا شوية.",
    "كل مرة بتجربي فيها حاجة جديدة بتكبري.",
    "ماتستسلميش بدري، الحلو لسه جاي يا نجمة.",
    "إنتِ سند لنفسك، وده أحلى حاجة.",
    "ضحكتك وإصرارك مع بعض قوة حلوة أوي."],
  morning:[
    "صباح الخير يا جميلة، يوم جديد وحاجات حلوة مستنياكي.",
    "صباح الورد يا قمر، افتحي الشباك وخدي نفس حلو.",
    "صباح اللافندر يا رودي، يومك يبدأ بابتسامة.",
    "قومي براحتك، مفيش حاجة هتهرب النهارده.",
    "ابدأي يومك بحاجة بسيطة بتحبيها.",
    "صباحك سكر يا نجمة، والنهارده فيه مفاجأة صغيرة.",
    "الشمس طلعت علشانك برضه، فاستقبليها بابتسامة.",
    "خلي أول حاجة تعمليها النهارده حاجة بتفرحك.",
    "كل صباح صفحة جديدة، اكتبي فيها حاجة حلوة.",
    "صباح الخير يا شطورة، يومك محتاج منك إنتِ زي ما إنتِ.",
    "كوباية الصبح هي أجمل بداية لليوم.",
    "يلا نفتح اليوم بنفس هادي وابتسامة.",
    "صباح الفل، خلي نيتك النهارده إنك تفرحي."],
  evening:[
    "مساء الجمال يا قمر، اليوم عدّى وإنتِ كنتي فيه حلوة.",
    "اقفلي يومك بحاجة بتحبيها، وسيبي الباقي لبكرة.",
    "يا جميلة، النهارده ينفع تقولي: كفاية كده وأرتاح.",
    "مساء الخير يا رودي، فكري في حاجة حلوة حصلت النهارده.",
    "نامي بدري لو قدرتي، بكرة مستنيكي.",
    "الليل هادي، والنجوم طالعة علشان تونّسك.",
    "اطفي الدنيا شوية وخليكي مع نفسك وحاجة حلوة.",
    "اكتبي حاجة واحدة اتبسطتي بيها النهارده.",
    "تصبحي على خير يا نجمة، وأحلام لافندر حلوة.",
    "يومك كان فيه جمال حتى لو ما لاحظتيهوش.",
    "مساء الورد يا شطورة، ريّحي بالك.",
    "سيبي اللي مخلصش لبكرة، وفرحي بنفسك شوية.",
    "الليلة دي تستاهل بطانية دافية وحاجة حلوة تتفرجي عليها."],
  dreams:[
    "أحلامك تستاهل خطة صغيرة وخطوة النهارده.",
    "يا رودي، إنتِ بطلة حكايتك، اكتبي فيها حاجات حلوة.",
    "الحلم الكبير بيتقسم لخطوات صغيرة، وإنتِ تقدري.",
    "اللي بتحلمي بيه مش بعيد زي ما بتتخيلي.",
    "ماتستهونيش بحلم مهما كان بسيط.",
    "احكي لنفسك حلمك بصوت عالي، هتحسي بقوته.",
    "كل نجمة في السما كانت حلم لحد.",
    "يا قمر، حلمك محتاج بس نفسك الطويل وثقتك بيه.",
    "اكتبي حلم جديد النهارده، ولو صغير.",
    "الطريق لأي حلم بيبدأ بخطوة، وإنتِ بدأتي.",
    "مش لازم تعرفي كل التفاصيل، كفاية تعرفي إنك عايزاه.",
    "فيه أحلام كتير حلوة مستنياكي تتحقق.",
    "اللي بتحلمي بيه بيشبهك، وده أجمل ما فيه."],
  success:[
    "مفيش حاجة أجمل من إنك تشوفي نفسك بتتقدمي.",
    "كل تقدم صغير بيتجمع ويبقى إنجاز كبير يا شطورة.",
    "النجاح مش سباق، ده مشوار وإنتِ ماشية فيه بشياكة.",
    "بصي كام حاجة اتعلمتيها السنة دي، إنتِ بتتطوري.",
    "النجاح ليه أشكال كتير، وإنتِ حققتي منه كتير.",
    "يا نجمة، كل إنجاز بتعمليه بتبنيه بإيدك.",
    "إنتِ في مكان أحلى من أمس، ودي حاجة تتحسب.",
    "متقارنيش نجاحك بحد، إنتِ ليكي مقياسك.",
    "تقدمك مش لازم يكون سريع، المهم إنه حقيقي.",
    "كل مرة بتخلصي حاجة، وسّعي ابتسامتك.",
    "الإصرار عندك أجمل من أي موهبة.",
    "يا رودي، قريب هتبصي ورا وتتفاجئي بالمسافة اللي قطعتيها.",
    "الاحتفال بالإنجازات الصغيرة بيجيب إنجازات أكبر."],
  enjoy:[
    "خلي ضحكتك حاضرة، حتى لو على حاجة صغيرة جداً.",
    "يا قمر، ادي لنفسك فرصة تستمتعي من غير ما تفكري في كل حاجة.",
    "الدنيا فيها تفاصيل حلوة، بصي حواليكي.",
    "امشي في مكان بتحبيه، حتى لو قريب.",
    "صوت المطر وريحة التراب والنسمة، كلها هدايا بسيطة.",
    "ماتستناش مناسبة علشان تفرحي، اصنعي لنفسك مناسبة صغيرة.",
    "اتفرجي على الغروب النهارده لو قدرتي.",
    "جربي أكلة جديدة أو مكان جديد، من غير أي خطة.",
    "خلي في يومك دقيقة تضحكي فيها من قلبك.",
    "الحياة حلوة بالتفاصيل: كوباية، أغنية، ضحكة، ونسمة.",
    "يا جميلة، خلي عندك مساحة للحاجات اللي بتحبيها.",
    "اتصوري مع حاجة بتفرحك النهارده.",
    "اللحظة الحلوة مش بتستنى إجازة، هي بتحصل دلوقتي."],
  funny:[
    "لو الدنيا ضغطت عليكي، افتكري إن القطط برضه بتقع وتعمل نفسها مقصودة 😄",
    "قانون الحياة: الأكل الحلو بيخلص أسرع من أي حاجة تانية.",
    "إنتِ مش بتتأخري، إنتِ بتعملي دخول مهم يا شطورة.",
    "مين قال إن الفطار ماينفعش يبقى عشا؟ الحرية في الأكل مكفولة 😄",
    "لو لقيتي نفسك بتتكلمي مع القطة، عادي جداً، هي بتفهم.",
    "يا نجمة، الكسل الجميل شغلانة محترمة ساعات.",
    "القاعدة الذهبية: مفيش حد بيقدر يقاوم لقمة حلوة.",
    "كوباية مية الأول، وبعدين نشوف أي حاجة 😄",
    "لو ضحكتي على نفسك النهارده، يبقى إنتِ أخف دم من اللي بتتخيلي.",
    "حظك النهارده: ممكن تلاقي حاجة كنتي دايرة عليها من أسبوع.",
    "إنتِ بتضحكي الدنيا بس بتتكسفي تقولي.",
    "الضحك بدون سبب هو أحلى أنواع الضحك يا رودي.",
    "لو الموبايل فضل في إيدك ساعة، خدي استراحة وبصي لحاجة حقيقية 😅"],
  surprise:[
    "يا رودي، عندي إحساس إن فيه حاجات جميلة مستنياكي.",
    "مفاجأة: النهارده هتتبسطي من حاجة ماكنتيش متوقعاها.",
    "جربي تفتحي صندوق تاني.. يمكن فيه مفاجأة أحلى 🎁",
    "النهارده محتاج منك ابتسامة صغيرة ومغامرة لطيفة.",
    "فيه نجمة بتلمع مخصوص علشانك الليلة.",
    "يمكن حد يبعتلك رسالة حلوة النهارده، خلي بالك.",
    "افتحي الشباك، ممكن تلاقي فراشة بتقولك صباح الخير 🦋",
    "يا قمر، النهارده فيه لقطة صغيرة حلوة هتحصل.",
    "مفاجأة صغيرة: إنتِ أجمل مما فاكرة.",
    "حاجة بسيطة هتفرحك قريب، شوفي بقى.",
    "النهارده جربي تعملي حاجة مختلفة وممتعة.",
    "الفراشة دي جاية تقولك إن التغيير حلو 🦋",
    "فيه حاجة حلوة مستخبية ورا اللحظة دي."],
  appreciate:[
    "إنتِ تستاهلي تفتخري بنفسك يا رودي.",
    "تقدير نفسك مش غرور، ده اعتراف بمجهودك.",
    "اشكري نفسك على كل مرة كملتي فيها.",
    "فيكي لطف وقوة وروح حلوة، وده مش قليل.",
    "يا جميلة، شوفي نفسك بنفس العين الحلوة اللي بيشوفوكي بيها.",
    "إنتِ نعمة لمن حواليكي، حتى لو ما بتقوليش.",
    "مفيش حد بيعمل اللي بتعمليه بنفس طريقتك الحلوة.",
    "اقدري خطواتك، حتى الصغيرة.",
    "إنتِ شطورة في حاجات كتير مش واخدة بالك منها.",
    "كلمة حلوة منك لنفسك دلوقتي، قوليها بصوت عالي.",
    "يا قمر، إنتِ تستاهلي الاحتفال بنفسك كل شوية.",
    "روحك الحلوة بتخلي المكان أحلى.",
    "افتخري بنفسك من غير ما تستني حد يقول."]
};

/* ---------- B. مكتبة العبارات: 150 عبارة في 10 تصنيفات ---------- */
const LIB = {
  "يا جميلة 💜":[
    "يا جميلة، يومك يستاهل يبدأ بابتسامة.","يا جميلة، وجودك في الدنيا حاجة حلوة.","يا جميلة، سيبي الدنيا شوية وفرحي نفسك.",
    "يا جميلة، التفاصيل الصغيرة هي اللي بتعمل اليوم.","يا جميلة، الحاجات الحلوة بتيجي لما نستناها بهدوء.","يا جميلة، إنتِ أنعم مما بتفتكري وأقوى كمان.",
    "يا جميلة، كل يوم جديد فرصة لحاجة حلوة.","يا جميلة، خدي لحظة وبصي للسما.","يا جميلة، روحك الحلوة بتبان في أبسط حاجة.",
    "يا جميلة، متنسيش تضحكي النهارده.","يا جميلة، إنتِ مش لازم تثبتي حاجة لحد.","يا جميلة، شوية هدوء وكتير ابتسامة.",
    "يا جميلة، قلبك الطيب هو أجمل حاجة فيكي.","يا جميلة، يومك زي ما تحبي، مش زي ما الدنيا عايزة.","يا جميلة، افتكري إن اللافندر بيفتح حتى في أهدى الأماكن."],
  "يا قمر 🌙":[
    "يا قمر، إنتِ منوّرة المكان حتى وإنتِ ساكتة.","يا قمر، الليل حلو بس بنورك أحلى.","يا قمر، مش لازم تكوني كاملة علشان تنوّري.",
    "يا قمر، كل مرحلة في حياتك ليها جمالها زي مراحل القمر.","يا قمر، النهارده دلعي نفسك بحاجة بسيطة.","يا قمر، ضحكتك بتفرق في يوم ناس كتير.",
    "يا قمر، إنتِ تستاهلي ليلة هادية ونوم حلو.","يا قمر، خليكي دايماً على طبيعتك.","يا قمر، النجوم نفسها بتتمنى تلمع زيك.",
    "يا قمر، فرحي نفسك بحاجة تحبيها.","يا قمر، متقلقيش، كل حاجة بتتظبط في وقتها.","يا قمر، لو عايزة تستريحي، استريحي.",
    "يا قمر، إنتِ أجمل مما بتشوفي في المراية.","يا قمر، خلي بالك من نفسك زي ما بتخلي بالك من اللي بتحبيهم.","يا قمر، النهارده يومك، اعمليه حلو."],
  "يا بطلة ⭐":[
    "يا بطلة، إنتِ عدّيتي كتير وهتعدّي كتير.","يا بطلة، كل محاولة تتحسب.","يا بطلة، التعلم رحلة مش امتحان.",
    "يا بطلة، الخطوة الجاية أسهل مما بتفتكري.","يا بطلة، ابدأي بالأسهل واكسبي حماسك.","يا بطلة، كل مرة بتقفي فيها بعد تعثر بتبقي أقوى.",
    "يا بطلة، إنتِ مش لوحدك في الطريق.","يا بطلة، اللي بتحاولي فيه يستاهل.","يا بطلة، فخورة بإصرارك الجميل.",
    "يا بطلة، مش لازم تكسبي كل جولة علشان تفوزي في الحكاية.","يا بطلة، خدي استراحة محارب وارجعي بنفس جديد.","يا بطلة، شجاعتك مش إنك مبتخافيش، شجاعتك إنك بتكملي.",
    "يا بطلة، إنتِ بتكتبي فصل جديد حلو.","يا بطلة، شوفي كام حاجة نجحتي فيها وابتسمي.","يا بطلة، التاج بتاعك مش لازم يكون ظاهر، إنتِ عارفة قيمتك."],
  "صباح الخير 🌷":[
    "صباح الخير، يوم جديد ولون جديد.","صباح الورد، النهارده هتلاقي حاجة تفرحك.","صباح الفل يا جميلة، ابدأي بنفس هادي.",
    "صباح اللافندر، خلي يومك ناعم وحلو.","صباح النور، افتحي الشباك وسيبي النسمة تدخل.","صباح الخير، كوباية حلوة وأغنية بتحبيها.",
    "صباح الأمل، اللي فات فات واللي جاي حلو.","صباح السكر، النهارده يوم بطيء ولذيذ.","صباح الخير، خدي وقتك في أول ساعة من اليوم.",
    "صباح العصافير، ابتسمي لأول حاجة تشوفيها.","صباح الخير يا قمر، قولي لنفسك: أنا شاطرة.","صباح البهجة، اختاري لبس بيفرحك.",
    "صباح الخير، مش لازم تبدئي بسرعة، ابدئي بحب.","صباح الياسمين، ريحة اليوم حلوة.","صباح الخير يا رودي، الدنيا مستنياكي بابتسامة."],
  "مساء الجمال ☁️":[
    "مساء الجمال، اليوم خلص وإنتِ كملتيه.","مساء الورد، سيبي الشاشة شوية وبصي للنجوم.","مساء الخير، حاجة دافية وحاجة حلوة تتفرجي عليها.",
    "مساء اللافندر، يا رب ليلتك هادية.","مساء الهدوء، ريّحي بالك لحد بكرة.","مساء النور يا قمر، اسمحي لنفسك تنامي بدري.",
    "مساء الفل، كفاية كده النهارده.","مساء السلام، سيبي كل حاجة مخلصتش لبكرة.","مساء الحنية، إنتِ استحقيتي ليلة حلوة.",
    "مساء الخير، ضوء خافت وبطانية وراحة بال.","مساء الجمال يا رودي، اتنفسي براحة.","مساء الغيم الحلو، سيبي أفكارك تعدّي.",
    "مساء الخير، فكري في ضحكة حلوة النهارده.","مساء النجوم، أحلام سعيدة بتستناكي.","مساء الليلك، النهارده كان يوم تستاهلي تفتخري بيه."],
  "يومك جميل 🦋":[
    "يومك جميل بالتفاصيل الصغيرة، دوري عليها.","يومك جميل لما تفرحي بأبسط حاجة.","يومك جميل لما تضحكي من قلبك.",
    "يومك جميل لما تسمحي لنفسك تستمتعي.","فراشة صغيرة ممكن تبدّل مزاج اليوم كله.","يومك جميل لو شفتي لون حلو واحد بس.",
    "يومك جميل لما تاخدي استراحة وتبصي حواليكي.","اختاري لنفسك حاجة حلوة تعمليها بعد الضهر.","يومك جميل لو كلمتي حد بتحبيه.",
    "يومك جميل لما تسمعي صوت بتحبيه.","اليوم الحلو مش لازم يكون مثالي، يكفي يكون لطيف.","يومك جميل بكل حاجة بتعمليها بحب.",
    "جربي تتفرجي على لون السما دلوقتي.","يومك جميل لما يبقى هادي وملوّن زي اللافندر.","يومك جميل زي ما إنتِ بتختاريه."],
  "ثقة بالنفس ✨":[
    "ثقي في إحساسك، هو غالباً صح.","إنتِ كفاية بجد، حتى لو الدنيا بتقول غير كده.","قولي لا من غير ما تتبرري لو مش مرتاحة.",
    "إنتِ قادرة تتعلمي أي حاجة جديدة.","صوتك له وزن، فاتكلمي بثقة.","مش لازم تعجبي الكل علشان تكوني جميلة.",
    "إنتِ ماشية بخطوتك الخاصة، وده حلو.","إنتِ مش محتاجة تاخدي إذن من حد علشان تفرحي.","اللي يشوفك بعين حلوة يستاهل، واللي مش شايف مش مشكلتك.",
    "كل ما تجربي، ثقتك بتكبر.","اعتزي بنفسك، فيكي حاجات نادرة.","إنتِ بتتعلمي وده بيكسبك قوة.",
    "متخافيش من الغلط، هو جزء من التعلم.","ثقتك بنفسك زي الزرع، بتكبر بالاهتمام.","اتصرفي كإنك واثقة، والثقة هتيجي."],
  "أحلامك تستاهل 🌸":[
    "أحلامك تستاهل خطوة النهارده، حتى لو صغيرة.","اكتبي حلمك في ورقة وحطيها مكان تشوفيها.","الحلم اللي بتخبيه بيستاهل يتحط في النور.",
    "كل حلم محتاج صبر وحب وشوية شجاعة.","ماتسيبيش حلم لأن حد قال إنه صعب.","فيه حلم جميل بيتكون جواكي، اسقيه بالثقة.",
    "مش لازم تعرفي الطريق كله، كفاية أول خطوة.","أحلامك بتشبهك، فاهتمي بيها.","قسّمي حلمك لحتت صغيرة ونفذي واحدة.",
    "الحلم بيكبر كل ما بتحكي عنه بحماس.","جرّبي النهارده حاجة بتقربك لحلمك ولو بسيطة.","فيه حلم بكرة هتبصي عليه وتقولي: حققته.",
    "إنتِ تستاهلي تحققي اللي بتتمنيه.","الأحلام الحلوة محتاجة ناس تصدق فيها، وأولهم إنتِ.","خلي الأمل رفيقك في الطريق."],
  "ابتسمي 😄":[
    "ابتسمي، الدنيا بتحلو بابتسامتك.","ابتسمي حتى بدون سبب، وشوفي هتحسي بإيه.","لو حسيتي إن اليوم تقيل، ابتسمي ابتسامة صغيرة بس.",
    "الابتسامة أسهل هدية ممكن تدّيها لنفسك.","افتكري موقف مضحك وسيبي ضحكتك تطلع.","ابتسمي للمراية، هي بتحب تشوفك مبتسمة.",
    "الضحك بيخفف الدنيا حتى لو لثواني.","ابتسمي.. فيه حاجة حلوة جاية في الطريق.","ابتسامتك أحلى فلتر في الدنيا.",
    "شغلي حاجة بتضحكك النهارده.","ضحكة من القلب بتغسل اليوم كله.","ابتسمي لنفسك قبل ما تبتسمي لحد.",
    "الحياة بتبتسم لمن يبتسم لها.","لو مفيش سبب، اخترعي سبب صغير للابتسام.","ابتسمي واتنفسي، وسيبي اللحظة تحلو."],
  "مفاجأة ليكي 🎁":[
    "مفاجأة: فيكي سحر صغير بيبان في الأوقات اللي مش متوقعاها.","هدية صغيرة: دقيقة من الهدوء ليكي إنتِ بس.","مفاجأة: النهارده ممكن يحصل حاجة حلوة غير متوقعة.",
    "لقيتي نجمة جديدة النهارده، خديها ⭐","مفاجأة صغيرة: فراشة بتقولك إنتِ مميزة 🦋","هدية من الكون: نسمة حلوة في وقت مناسب.",
    "مفاجأة: إنتِ تستاهلي أحلى الحاجات.","فيه حاجة حلوة قريب، خلي بالك منها.","هدية صغيرة: خدي نفس وابتسمي دلوقتي.",
    "مفاجأة: القمر النهارده بيسلم عليكي.","هدية: كلمة حلوة تقوليها لنفسك دلوقتي.","مفاجأة لطيفة: كل يوم بيحمل لحظة تستاهل تتصور.",
    "هدية صغيرة: اختاري لون النهارده وخلي يومك بيه.","مفاجأة: فيه ناس بتفتكرك بالخير ومتعرفيش.","هدية: ضحكة حلوة من قلبك دلوقتي 😄"]
};

/* ---------- C. حالات المزاج ---------- */
const MOODS = [
  {t:"😍 مبسوطة جداً.", r:["يا سلام يا قمر! خدي اللحظة دي وعيشيها كلها.","حلو أوي الفرحة دي، ودّيها لحد يحبك.","ضحكتك دي تستاهل تتصور وتتحفظ في قلبك."]},
  {t:"🌷 رايقة وهادية.", r:["جميل أوي الرواقة دي يا رودي، استمتعي بيها.","يوم هادي ولطيف زي لون اللافندر 💜","خليكي في الإحساس الحلو ده، مفيش استعجال."]},
  {t:"😄 نفسي أضحك وأهزر.", r:["ضحكتك أحلى حاجة! دوري على مقطع يضحكك النهارده.","يلا نهزر! افتحي صندوق المفاجآت واضحكي على رسالة خفيفة 😄","الضحك على أبسط حاجة هو أجمل نوع، شغّلي موقف مضحك."]},
  {t:"✨ عندي طاقة أعمل حاجات حلوة.", r:["يا شطورة! استغلي الطاقة دي في حاجة بتحبيها.","طاقتك الحلوة دي تستاهل مشروع صغير النهارده ✨","ابدأي بحاجة بسيطة وخلي الطاقة تقودك."]},
  {t:"☁️ محتاجة شوية هدوء.", r:["تعالي لعالم الطبيعة وخدي لحظة هادية يا جميلة 🌊","اقفلي عينيكي دقيقة واتخيلي بحر لافندر هادي.","الهدوء ليكي دلوقتي، خدي وقتك من غير أي استعجال."]},
  {t:"🦋 مود مفاجآت.", r:["يلا نفتح صندوق المفاجآت ونشوف إيه اللي فيه 🎁","جربي فراشة الحظ في الأنشطة، يمكن تضحكك 🦋","النهارده يوم لقطات صغيرة حلوة، افتحي عينيكي عليها."]}
];

/* ---------- D. رسائل النقاط والمكافآت ---------- */
const PTS = ["برافو يا شطورة! نجمة جديدة ⭐","يا قمر، حلو إنك فرحتي نفسك.","نجمة حلوة لإنسانة حلوة.","كملي يا نجمة، إنتِ بتلمعي.","حاجة حلوة تتحسب يا جميلة.","فخورة بيكي يا بطلة.","النجمة دي بتقولك: عملتي كويس.","ضحكتك تستاهل نجمة كمان 😄","إنتِ بتعملي حاجات لطيفة أكتر مما تتخيلي.","نجمة صغيرة وفرحة كبيرة ✨","خدي لحظة واحتفلي بنفسك.","كل نجمة بتنوّر حتة جواكي."];

const REWARDS = [
  {t:"يا رودي يا قمر! ⭐", x:"وصلتي لـ 100 نقطة!\n\nعارفة ده معناه إيه؟\n\nإن عندك 100 لحظة قررتي فيها تفرحي بنفسك وتقدري خطواتك.\n\nإنتِ تستاهلي كل نجمة وكل حاجة حلوة.\n\nخدي نجمتك يا جميلة، وكملي رحلتك بطريقتك الخاصة. 🦋"},
  {t:"يا شطورة يا رودي! 🌟", x:"100 لحظة حلوة جديدة اتضافت لحكايتك.\n\nكل نجمة جمعتيها بتقول إنك بتفرحي نفسك وتلاحظي الحاجات الصغيرة الجميلة.\n\nاستمتعي بالنجمة دي، وكملي بنفس الروح الحلوة. 💜"},
  {t:"نجمة جديدة لنجمة! ✨", x:"يا رودي، إنتِ بتثبتي إن الفرحة بتتجمع حتة حتة.\n\nمش مهم السرعة، المهم إنك بتلتفتي لحاجات حلوة في يومك.\n\nمبروك النجمة، وكملي براحتك يا قمر. 🌷"},
  {t:"يا بطلة الحكاية! 🦋", x:"وصلتي لـ 100 نقطة تانية!\n\nبتكتبي حكايتك بإيدك، وفيها لحظات حلوة كتير.\n\nخدي النجمة دي، وخلي ضحكتك دايماً حاضرة. ⭐"},
  {t:"يا جميلة، إنتِ بتلمعي! 🌸", x:"كل نجمة هنا بتمثل ابتسامة أو لحظة أو فكرة حلوة.\n\nوإنتِ عندك كتير منهم.\n\nافتخري بنفسك، وكملي مشوارك الحلو. 💜"},
  {t:"مبروك يا قمر! 🌙", x:"النجمة دي ليكي إنتِ بالذات.\n\nعلشان بتهتمي بالتفاصيل الحلوة وبتفرحي بيها.\n\nاستمري بنفس اللطف والروح الجميلة. ✨"},
  {t:"يا نجمة النجوم! ⭐", x:"100 خطوة صغيرة بقت نجمة كبيرة.\n\nكل حاجة حلوة عملتيها كان ليها قيمة.\n\nخدي نجمتك بفخر يا رودي. 🌷"},
  {t:"يا صاحبة الروح الجميلة! 🦋", x:"روحك الحلوة هي اللي بتخلي النجوم دي تتجمع.\n\nمبروك على اللحظات اللي اخترتي تفرحي فيها.\n\nالجاي أحلى بإذن الله. 💜"},
  {t:"يا رودي يا شطورة! 🌈", x:"إنتِ بتحوّلي أبسط الحاجات لفرحة.\n\nوده شيء مميز جداً.\n\nكملي، وخلي اللافندر يملا يومك. 🌸"},
  {t:"احتفال لافندر ليكي! 💜", x:"نجمة جديدة، ولحظات حلوة جديدة.\n\nإنتِ تستاهلي كل الأيام الحلوة.\n\nيلا نكمل الرحلة سوا، خطوة خطوة. 🦋"}
];
const FINAL_MSG = "يا رودي يا قمر..\n\nعايزاكي تعرفي إن كل نجمة جمعتيها ليها معنى حلو.\n\nإنتِ بتفرحي نفسك وبتلاحظي الجمال في التفاصيل الصغيرة، وده مش سهل.\n\nكملي بالطريقة اللي تحبيها، ومتنسيش إنك تستاهلي كل حاجة حلوة.\n\nوكل ما تحتاجي رسالة جديدة، الصندوق دايماً مستنيكي. 🦋";
const FINAL_AT = 3;

const PICKS = ["يا نجمة، النهارده ليكي حاجة حلوة صغيرة في الطريق.","النجمة دي بتقولك: ضحكتك ليها سحر.","اختارتي نجمة محظوظة! فيه مفاجأة لطيفة جاية.","النجمة دي فرحانة بيكي يا قمر.","نجمتك بتقولك: كملي بنفس الروح الحلوة.","نجمة هادية وحنينة، زيك بالظبط.","النجمة دي بتقولك: افتكري إنك تستاهلي كل الحاجات الحلوة."];
const LUCK = ["مسكتيني! 🦋 يومك هيبقى أحلى من ما تتخيلي.","الفراشة بتقولك: جربي حاجة جديدة النهارده.","حظك حلو يا قمر، ابتسمي وشوفي.","فيه رسالة حلوة جاية ليكي قريب.","الفراشة دي حطت على كتفك فرحة صغيرة.","يا جميلة، كل حاجة بتتظبط في وقتها."];
const CHALL = ["جربي حاجة جديدة بتحبيها.","شوفي صورة بتفكرك بذكرى حلوة.","اتعلمي معلومة جديدة النهارده.","خدي صورة لحاجة عجبتك.","اعملي لنفسك مشروب بتحبيه.","اسمعي صوت المطر أو البحر من عالم الطبيعة.","اضحكي على موقف مضحك.","اكتبي حاجة حلوة عن نفسك.","اتمشي في مكان بتحبيه ولو قريب.","اتصلي أو ابعتي رسالة حلوة لحد بتحبيه."];
const COLORS = [["Lavender","#B8A4E8"],["Soft Lavender","#D1C4F0"],["Light Lilac","#E5DCF8"],["Pale Violet","#F0EAFB"],["Deep Lavender","#8975B8"],["Mist Purple","#C7B8E8"],["Soft Pink","#F4DFF0"],["Cloud White","#FAF8FF"],["Cream","#FFF9F0"],["Muted Purple","#594A78"]];

/* ---------- E. أدوات ---------- */
const $ = s => document.querySelector(s), $$ = s => [...document.querySelectorAll(s)];
const ALLBOX = Object.values(BOX).flat();
const RM = matchMedia('(prefers-reduced-motion: reduce)').matches;
const noMotion = () => S.set.reduce || RM;
function bag(arr){let q=[],last=-1;return()=>{if(!q.length){q=arr.map((_,i)=>i);for(let i=q.length-1;i>0;i--){const j=Math.random()*(i+1)|0;[q[i],q[j]]=[q[j],q[i]];}}
  let i=q.pop();if(i===last&&q.length){const k=q.pop();q.push(i);i=k;}last=i;return arr[i];};}
const ymd = d => d.getFullYear()+'-'+String(d.getMonth()+1).padStart(2,'0')+'-'+String(d.getDate()).padStart(2,'0');
const starSVG = (sz) => `<svg viewBox="0 0 24 24" width="${sz}" height="${sz}"><use href="#st" fill="url(#gStar)"/></svg>`;
const bfSVG = '<svg viewBox="0 0 40 30"><use href="#bf"/></svg>';

/* ---------- F. الحفظ المحلي ---------- */
const KEY = 'rody_v1';
let S = {points:0, stars:0, reward:0, total:0, color:null, notes:[], letters:[], set:{fx:false, reduce:false, vol:{}}};
function load(){try{const r=JSON.parse(localStorage.getItem(KEY));if(r)S={...S,...r,set:{...S.set,...(r.set||{}),vol:{...(r.set&&r.set.vol||{})}}};}catch(e){}}
function save(){try{localStorage.setItem(KEY,JSON.stringify(S));}catch(e){}}

/* ---------- G. أصوات الطبيعة (ملفات حقيقية فقط، من غير توليد صوتي) ---------- */
const SOUNDS = [
  {k:'sea',n:'أمواج البحر الهادية',e:'🌊'},{k:'rain',n:'مطر خفيف',e:'🌧️'},{k:'birds',n:'عصافير',e:'🐦'},
  {k:'wind',n:'رياح بين الأشجار',e:'🍃'},{k:'stream',n:'مياه جارية',e:'💧'},{k:'forest',n:'أصوات الغابة',e:'🌲'},{k:'leaves',n:'أوراق الشجر',e:'🍂'}
];
const EXT = ['mp3','ogg','m4a','wav'];
const snd = {}, playing = new Set(), blobUrl = {};

/* IndexedDB: حفظ ملف الصوت اللي بتختاره من جهازها */
const idb = () => new Promise((res,rej)=>{const r=indexedDB.open('rody_audio',1);r.onupgradeneeded=()=>r.result.createObjectStore('f');r.onsuccess=()=>res(r.result);r.onerror=()=>rej(r.error);});
async function idbGet(k){try{const d=await idb();return await new Promise(res=>{const q=d.transaction('f').objectStore('f').get(k);q.onsuccess=()=>res(q.result||null);q.onerror=()=>res(null);});}catch(e){return null;}}
async function idbPut(k,v){try{const d=await idb();return await new Promise(res=>{const t=d.transaction('f','readwrite');t.objectStore('f').put(v,k);t.oncomplete=()=>res(true);t.onerror=()=>res(false);});}catch(e){return false;}}

function setStatus(k,t){const el=$('#snd-'+k+' .st');if(el)el.textContent=t;}
function setBtn(k){const b=$('#snd-'+k+' .sbtn'),on=playing.has(k);b.classList.toggle('on',on);b.textContent=on?'⏸ وقّفي':'▶ شغّلي';}
function makeAudio(k){
  const a=document.createElement('audio');a.loop=true;a.preload='auto';
  const urls=blobUrl[k]?[blobUrl[k]]:EXT.map(e=>`sounds/${k}.${e}`);
  urls.forEach((u,i)=>{const s=document.createElement('source');s.src=u;
    if(i===urls.length-1)s.addEventListener('error',()=>unavailable(k));a.appendChild(s);});
  a.addEventListener('playing',()=>setStatus(k,'شغّال دلوقتي 🌿'));
  a.addEventListener('error',()=>unavailable(k));
  return a;
}
function unavailable(k){
  const a=snd[k];if(a){try{a.pause();}catch(e){}}
  delete snd[k];playing.delete(k);setBtn(k);
  setStatus(k,'الصوت ده مش متاح دلوقتي. تقدري تختاري ملف من جهازك بزرار 📁');
}
function toggleSound(k){
  if(playing.has(k)){stopSound(k);return;}
  let a=snd[k];if(!a){a=makeAudio(k);snd[k]=a;}
  a.volume=S.set.vol[k]??.6;setStatus(k,'بحمّل الصوت…');
  playing.add(k);setBtn(k);
  let p;try{p=a.play();}catch(e){unavailable(k);return;}
  if(p&&p.catch)p.catch(err=>{
    if(!snd[k])return;
    if(err&&err.name==='NotAllowedError'){playing.delete(k);setBtn(k);setStatus(k,'المتصفح منع التشغيل، دوسي تاني.');}
    else if(err&&err.name!=='AbortError')unavailable(k);
  });
}
function stopSound(k){const a=snd[k];if(a)try{a.pause();}catch(e){}playing.delete(k);setBtn(k);setStatus(k,'');}
function stopAll(){[...playing].forEach(stopSound);}
function buildSounds(){
  const box=$('#sounds');
  SOUNDS.forEach(s=>{
    const row=document.createElement('div');row.className='srow';row.id='snd-'+s.k;
    row.innerHTML=`<span style="font-size:1.6rem">${s.e}</span><span class="nm">${s.n}</span>
      <div class="ctl"><button class="btn sm sbtn">▶ شغّلي</button>
      <input type="range" min="0" max="1" step="0.05" aria-label="مستوى الصوت">
      <label class="btn sm soft" style="cursor:pointer" title="اختاري ملف صوت من جهازك">📁<input type="file" accept="audio/*" hidden></label></div>
      <div class="st" aria-live="polite"></div>`;
    const rng=row.querySelector('input[type=range]');rng.value=S.set.vol[s.k]??.6;
    row.querySelector('.sbtn').onclick=()=>toggleSound(s.k);
    rng.oninput=()=>{S.set.vol[s.k]=+rng.value;if(snd[s.k])snd[s.k].volume=+rng.value;save();};
    row.querySelector('input[type=file]').onchange=async e=>{
      const f=e.target.files[0];if(!f)return;
      stopSound(s.k);delete snd[s.k];
      if(blobUrl[s.k])URL.revokeObjectURL(blobUrl[s.k]);
      blobUrl[s.k]=URL.createObjectURL(f);
      const ok=await idbPut(s.k,f);
      setStatus(s.k,ok?'تم حفظ الملف على جهازك ✓ دوسي شغّلي.':'الملف جاهز للجلسة دي بس.');
    };
    box.appendChild(row);
  });
  SOUNDS.forEach(async s=>{const b=await idbGet(s.k);if(b){blobUrl[s.k]=URL.createObjectURL(b);}});
}
/* مؤثرات طبيعية قصيرة اختيارية: لو الملف مش موجود، ولا صوت */
const fxCache={};
function fxPlay(name){
  if(!S.set.fx)return;
  try{
    let a=fxCache[name];
    if(a===false)return;
    if(!a){a=document.createElement('audio');EXT.forEach(e=>{const s=document.createElement('source');s.src=`sounds/fx-${name}.${e}`;a.appendChild(s);});
      a.volume=.4;a.addEventListener('error',()=>{fxCache[name]=false;},true);fxCache[name]=a;}
    a.currentTime=0;const p=a.play();if(p&&p.catch)p.catch(()=>{});
  }catch(e){}
}

/* ---------- H. مؤثرات بصرية ---------- */
function typeInto(el,text){clearInterval(el._t);if(noMotion()){el.textContent=text;return;}
  el.textContent='';let i=0;el._t=setInterval(()=>{el.textContent=text.slice(0,++i);if(i>=text.length)clearInterval(el._t);},24);}
function sparks(x,y,n){if(noMotion())return;
  for(let i=0;i<n;i++){const s=document.createElement('span');s.className='burst';s.innerHTML=starSVG(20);
    s.style.left=x+'px';s.style.top=y+'px';s.style.setProperty('--dx',(Math.random()*240-120)+'px');s.style.setProperty('--dy',(-Math.random()*200-20)+'px');
    document.body.appendChild(s);setTimeout(()=>s.remove(),1600);}}
function butterflies(x,y,n){if(noMotion())return;
  for(let i=0;i<n;i++){const s=document.createElement('span');s.className='bup';s.innerHTML=bfSVG;
    s.style.left=x+'px';s.style.top=y+'px';s.style.setProperty('--dx',(Math.random()*280-140)+'px');s.style.setProperty('--dy',(-Math.random()*300-60)+'px');
    s.style.animationDelay=(i*.12)+'s';document.body.appendChild(s);setTimeout(()=>s.remove(),3300+i*120);}}
function confetti(n){if(noMotion())return;
  const cols=['#B8A4E8','#F4DFF0','#D1C4F0','#E8C77A','#FAF8FF','#8975B8'];
  for(let i=0;i<n;i++){const s=document.createElement('span');s.className='fall';
    if(i%3===0)s.innerHTML=starSVG(20);else{s.style.width=s.style.height=(6+Math.random()*7)+'px';s.style.background=cols[i%cols.length];s.style.borderRadius=i%2?'50%':'2px';}
    s.style.left=Math.random()*100+'vw';s.style.animationDuration=(3.5+Math.random()*3)+'s';s.style.animationDelay=(Math.random()*1.5)+'s';
    document.body.appendChild(s);setTimeout(()=>s.remove(),8000);}}
document.addEventListener('pointerdown',e=>{const b=e.target.closest('.btn');if(!b)return;
  const r=b.getBoundingClientRect(),s=document.createElement('span'),d=Math.max(r.width,r.height);
  s.className='rip';s.style.width=s.style.height=d+'px';s.style.left=(e.clientX-r.left-d/2)+'px';s.style.top=(e.clientY-r.top-d/2)+'px';
  b.appendChild(s);setTimeout(()=>s.remove(),700);});

/* الخلفية (عدد عناصر قليل علشان الأداء) */
(function bg(){
  const far=$('#lyFar'),mid=$('#lyMid'),near=$('#lavBox');
  for(let i=0;i<22;i++){const s=document.createElement('div');s.className='star';s.innerHTML=starSVG(10);
    s.style.left=Math.random()*100+'%';s.style.top=Math.random()*55+'%';s.style.animationDelay=(Math.random()*7)+'s';s.style.animationDuration=(5+Math.random()*5)+'s';far.appendChild(s);}
  for(let i=0;i<5;i++){const c=document.createElement('div');c.className='cloud'+(i%2?' v':'');c.style.top=(4+i*13)+'%';c.style.animationDelay=(-i*22)+'s';c.style.animationDuration=(100+i*18)+'s';mid.appendChild(c);}
  for(let i=0;i<7;i++){const b=document.createElement('div');b.className='bubble';const z=10+Math.random()*26;b.style.width=b.style.height=z+'px';
    b.style.left=Math.random()*100+'%';b.style.animationDelay=(-Math.random()*26)+'s';b.style.animationDuration=(22+Math.random()*14)+'s';mid.appendChild(b);}
  for(let i=0;i<10;i++){const m=document.createElement('div');m.className='mote';m.style.left=Math.random()*100+'%';m.style.top=(25+Math.random()*60)+'%';m.style.animationDelay=(-Math.random()*20)+'s';mid.appendChild(m);}
  for(let i=0;i<3;i++){const r=document.createElement('div');r.className='ring';const z=150+i*40;r.style.width=r.style.height=z+'px';r.style.left=(10+i*32)+'%';r.style.bottom=(5+i*3)+'%';r.style.animationDelay=(i*5)+'s';mid.appendChild(r);}
  [[8,"#B8A4E8"],[88,"#C7B8E8"],[30,"#B8A4E8"],[66,"#D1C4F0"]].forEach(([x],i)=>{const l=document.createElement('div');l.className='lav';
    l.style.left=x+'%';l.style.height=(90+i*18)+'px';l.style.animationDelay=(-i*2)+'s';l.innerHTML='<svg viewBox="0 0 40 120" width="40" height="100%"><use href="#lv"/></svg>';near.appendChild(l);});
  for(let i=0;i<3;i++){const f=document.createElement('div');f.className='fly';f.style.left=(60+i*12)+'%';f.style.top=(40+i*14)+'%';
    f.style.animationDelay=(-i*11)+'s';f.style.animationDuration=(36+i*8)+'s';f.innerHTML=bfSVG;mid.appendChild(f);}
  addEventListener('pointermove',e=>{if(noMotion())return;const x=e.clientX/innerWidth-.5,y=e.clientY/innerHeight-.5;
    $('#lyFar').style.transform=`translate(${x*-10}px,${y*-8}px)`;$('#lyNear').style.transform=`translate(${x*14}px,${y*6}px)`;});
})();

/* ---------- I. التنقل + زر الرجوع ---------- */
let hist=['home'];
function show(v,isBack){
  if(!isBack&&hist[hist.length-1]!==v)hist.push(v);
  $$('.view').forEach(x=>x.classList.toggle('active',x.id==='v-'+v));
  $$('#nav button').forEach(b=>b.classList.toggle('on',b.dataset.v===v));
  $('#back').style.visibility=v==='home'?'hidden':'visible';
  $('#main').scrollTop=0;
  if(v==='stars')renderStars();
  if(v==='msgs')renderWrite();
}
$$('#nav button').forEach(b=>b.onclick=()=>show(b.dataset.v));
$$('[data-go]').forEach(b=>b.onclick=()=>show(b.dataset.go));
$('#back').onclick=()=>{if(hist.length>1){hist.pop();show(hist[hist.length-1],true);}else show('home',true);};

/* ---------- J. الرئيسية ---------- */
const nextDaily=bag(ALLBOX);
function initHome(){
  $('#today').textContent=new Date().toLocaleDateString('ar-EG',{weekday:'long',day:'numeric',month:'long'});
  const d=new Date();const idx=Math.floor(new Date(d.getFullYear(),d.getMonth(),d.getDate()).getTime()/864e5)%ALLBOX.length;
  $('#dailyMsg').textContent=ALLBOX[idx];
  $('#dailyMore').onclick=()=>typeInto($('#dailyMsg'),nextDaily());
  const box=$('#moods');
  MOODS.forEach(m=>{const pick=bag(m.r);const b=document.createElement('button');b.className='mood';b.textContent=m.t;
    b.onclick=()=>{$$('.mood').forEach(x=>x.classList.remove('on'));b.classList.add('on');typeInto($('#moodReply'),pick());};box.appendChild(b);});
}

/* ---------- K. صندوق المفاجآت ---------- */
const nextBox=bag(ALLBOX);
function openBox(){
  const g=$('#gift');g.classList.remove('open');g.classList.add('shake');
  setTimeout(()=>{g.classList.remove('shake');g.classList.add('open');fxPlay('breeze');
    const r=g.getBoundingClientRect();sparks(r.left+r.width/2,r.top+30,12);butterflies(r.left+r.width/2,r.top+20,4);
    $('#boxCard').style.display='block';typeInto($('#boxMsg'),nextBox());},g.classList.contains('open')?350:500);
}
$('#gift').onclick=openBox;$('#boxMore').onclick=openBox;

/* ---------- L. النقاط والنجوم ---------- */
const nextPts=bag(PTS);
function renderStars(){
  $('#ptsBig').textContent=S.points+' / 100';
  $('#ptsBar').style.width=Math.min(S.points,100)+'%';
  $('#ptsPct').textContent=Math.min(S.points,100)+'% من النجمة الجاية';
  const row=$('#starsRow');row.innerHTML='';
  if(!S.stars)row.innerHTML='<span class="tiny">أول نجمة مميزة مستنياكي ⭐</span>';
  for(let i=0;i<Math.min(S.stars,40);i++)row.insertAdjacentHTML('beforeend',starSVG(30));
  if(S.stars>40)row.insertAdjacentHTML('beforeend','<span> ×'+S.stars+'</span>');
  $('#totalTxt').textContent=S.total?('إجمالي لحظاتك الحلوة: '+S.total):'';
  const f=S.stars>=FINAL_AT;$('#finalCard').style.display=f?'block':'none';if(f)$('#finalTxt').textContent=FINAL_MSG;
}
function showReward(){
  const r=REWARDS[S.reward%REWARDS.length];
  $('#rwTitle').textContent=r.t;$('#rwTxt').textContent=r.x;$('#ovReward').classList.add('show');
  confetti(34);butterflies(innerWidth/2,innerHeight*.6,5);
}
$('#plus').onclick=e=>{
  S.points+=1;S.total+=1;save();renderStars();fxPlay('drop');
  const big=$('#ptsBig');big.classList.remove('bump');void big.offsetWidth;big.classList.add('bump');
  const r=e.currentTarget.getBoundingClientRect();
  if(!noMotion()){const f=document.createElement('span');f.className='flystar';f.innerHTML=starSVG(30);f.style.left=(r.left+r.width/2-15)+'px';f.style.top=(r.top-10)+'px';document.body.appendChild(f);setTimeout(()=>f.remove(),1300);}
  typeInto($('#ptsMsg'),nextPts());
  if(S.points>=100)setTimeout(showReward,800);
};
$('#rwClaim').onclick=()=>{S.stars+=1;S.reward+=1;S.points=0;save();$('#ovReward').classList.remove('show');renderStars();};

/* ---------- M. الأنشطة ---------- */
function initActivities(){
  const pickMsg=bag(PICKS),grid=$('#pickStars');
  for(let i=0;i<7;i++){const b=document.createElement('button');b.className='pick';b.innerHTML=starSVG(34);b.setAttribute('aria-label','نجمة '+(i+1));
    b.onclick=()=>{$$('.pick').forEach(x=>x.classList.remove('on'));b.classList.add('on');typeInto($('#pickMsg'),pickMsg());const r=b.getBoundingClientRect();sparks(r.left+r.width/2,r.top,6);};grid.appendChild(b);}
  const luck=bag(LUCK),bf=$('#bfly'),stage=$('#bstage');
  const move=()=>{const w=stage.clientWidth-70,h=stage.clientHeight-56;bf.style.transform=`translate(${Math.random()*w}px,${Math.random()*h}px)`;};
  move();setInterval(()=>{if(!noMotion())move();},3400);
  bf.onclick=()=>{typeInto($('#bfMsg'),luck());fxPlay('butterfly');move();const r=bf.getBoundingClientRect();sparks(r.left+30,r.top+20,5);};
  const sw=$('#swatches');
  COLORS.forEach(([n,c])=>{const b=document.createElement('button');b.className='sw';b.style.background=c;b.setAttribute('aria-label',n);b.dataset.c=c;
    b.onclick=()=>{S.color=c;save();applyColor();$('#colMsg').textContent='لونك المفضل '+n+'، حلو أوي يا رودي 💜';};sw.appendChild(b);});
  const ch=bag(CHALL);const setCh=()=>typeInto($('#chMsg'),ch());setCh();
  $('#chMore').onclick=setCh;
  $('#chDone').onclick=e=>{$('#chMsg').textContent='يا شطورة! حلو إنك جربتي 🌷';const r=e.currentTarget.getBoundingClientRect();sparks(r.left+r.width/2,r.top,8);};
}
function applyColor(){
  if(S.color)document.documentElement.style.setProperty('--accent',S.color);
  $$('.sw').forEach(s=>s.classList.toggle('on',s.dataset.c===S.color));
}

/* ---------- N. الرسائل + المساحة الصغيرة ---------- */
function initLib(){
  const c=$('#chips');
  Object.keys(LIB).forEach(k=>{const pick=bag(LIB[k]);const b=document.createElement('button');b.className='chip';b.textContent=k;
    b.onclick=()=>{$$('.chip').forEach(x=>x.classList.remove('on'));b.classList.add('on');$('#libCard').style.display='block';typeInto($('#libMsg'),pick());};c.appendChild(b);});
}
function renderWrite(){
  const n=$('#notes');n.innerHTML='';if(!S.notes.length)n.innerHTML='<p class="tiny">لسه مفيش حاجة محفوظة.</p>';
  S.notes.slice().reverse().forEach(x=>{const d=document.createElement('div');d.className='note';d.textContent=x.text;
    const s=document.createElement('small');s.textContent=new Date(x.at).toLocaleDateString('ar-EG')+' ';
    const del=document.createElement('button');del.textContent='🗑️ مسح';del.onclick=()=>{S.notes=S.notes.filter(y=>y.id!==x.id);save();renderWrite();};
    s.appendChild(del);d.appendChild(s);n.appendChild(d);});
  const L=$('#letters');L.innerHTML='';const today=ymd(new Date());
  if(!S.letters.length)L.innerHTML='<p class="tiny">لسه ماكتبتيش رسالة لنفسك.</p>';
  S.letters.forEach(x=>{const d=document.createElement('div');d.className='note';const open=today>=x.date;
    d.textContent=open?'✉️ رسالة وصلتك من نفسك':'🔒 رسالة مقفولة لحد '+new Date(x.date+'T00:00').toLocaleDateString('ar-EG',{day:'numeric',month:'long',year:'numeric'});
    const s=document.createElement('small');
    if(open){const b=document.createElement('button');b.textContent='افتحيها';b.onclick=()=>{d.textContent=x.text;};s.appendChild(b);s.appendChild(document.createTextNode('  '));}
    const del=document.createElement('button');del.textContent='🗑️ مسح';del.onclick=()=>{S.letters=S.letters.filter(y=>y.id!==x.id);save();renderWrite();};
    s.appendChild(del);d.appendChild(s);L.appendChild(d);});
}
$('#noteSave').onclick=()=>{const t=$('#noteTxt').value.trim();if(!t)return;S.notes.push({id:Date.now(),text:t,at:Date.now()});save();$('#noteTxt').value='';renderWrite();};
$('#noteClear').onclick=()=>{$('#noteTxt').value='';};
$('#toLetter').onclick=()=>{const b=$('#letterBox');b.style.display=b.style.display==='none'?'block':'none';
  const t=new Date();t.setDate(t.getDate()+1);$('#letDate').min=ymd(t);if(!$('#letDate').value)$('#letDate').value=ymd(new Date(Date.now()+7*864e5));};
$('#letSave').onclick=()=>{const t=$('#letTxt').value.trim(),d=$('#letDate').value;if(!t||!d)return;
  S.letters.push({id:Date.now(),text:t,date:d});save();$('#letTxt').value='';$('#letterBox').style.display='none';renderWrite();};

/* ---------- O. "مش قادرة أتكلم" + الإعدادات ---------- */
$('#cant').onclick=()=>$('#ovCant').classList.add('show');
$('#cantOk').onclick=()=>$('#ovCant').classList.remove('show');
$('#cantNat').onclick=()=>{$('#ovCant').classList.remove('show');show('nature');};
function applySettings(){document.documentElement.classList.toggle('reduce',S.set.reduce);$('#setFx').checked=S.set.fx;$('#setReduce').checked=S.set.reduce;}
$('#setBtn').onclick=()=>$('#ovSet').classList.add('show');
$('#setOk').onclick=()=>$('#ovSet').classList.remove('show');
$('#setFx').onchange=e=>{S.set.fx=e.target.checked;save();};
$('#setReduce').onchange=e=>{S.set.reduce=e.target.checked;save();applySettings();};
$('#muteAll').onclick=stopAll;$('#setMute').onclick=stopAll;

/* ---------- P. البداية ---------- */
$('#startBtn').onclick=e=>{
  const r=e.currentTarget.getBoundingClientRect();sparks(r.left+r.width/2,r.top,10);butterflies(r.left+r.width/2,r.top,5);
  $('#welcome').classList.add('gone');setTimeout(()=>$('#welcome').remove(),1200);
};
(function welcomeFly(){const w=$('#wfly');for(let i=0;i<4;i++){const f=document.createElement('div');f.className='fly';f.style.left=(15+i*22)+'%';f.style.top=(20+(i%2)*45)+'%';
  f.style.animationDelay=(-i*8)+'s';f.innerHTML=bfSVG;w.appendChild(f);}})();

load();applySettings();buildSounds();initHome();initActivities();initLib();applyColor();renderStars();
if(S.points>=100)setTimeout(showReward,1500);
</script>
</body>
</html>
