# for-madam-jii<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Sorry, Madam Ji 🌸</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Caveat:wght@500;700&family=Quicksand:wght@400;500;600;700&display=swap" rel="stylesheet">
<style>
  :root{
    --cream:#FFF8F2;
    --blush:#FFD9E3;
    --rose:#E8607D;
    --deep-rose:#C2415E;
    --leaf:#8FAE8B;
    --brown:#5B4442;
    --gold:#E8B84B;
  }

  *{ box-sizing:border-box; }

  html{ scroll-behavior:smooth; }

  body{
    margin:0;
    min-height:100vh;
    background:
      radial-gradient(circle at 15% 10%, #FFE8EE 0%, transparent 45%),
      radial-gradient(circle at 85% 25%, #FFF0DE 0%, transparent 50%),
      linear-gradient(180deg, #FFF8F2 0%, #FFF1F4 60%, #FFE9EE 100%);
    font-family:'Quicksand', sans-serif;
    color:var(--brown);
    overflow-x:hidden;
    position:relative;
  }

  /* ---------- Falling petals ---------- */
  .petals{
    position:fixed;
    inset:0;
    pointer-events:none;
    z-index:1;
    overflow:hidden;
  }
  .petal{
    position:absolute;
    top:-40px;
    font-size:22px;
    animation:fall linear infinite, sway ease-in-out infinite;
    opacity:0.85;
    user-select:none;
  }
  @keyframes fall{
    to{ transform:translateY(110vh); }
  }
  @keyframes sway{
    0%,100%{ margin-left:0px; }
    50%{ margin-left:40px; }
  }

  @media (prefers-reduced-motion: reduce){
    .petal{ animation:none; display:none; }
    *{ animation-duration:0.001ms !important; }
  }

  /* ---------- Layout ---------- */
  main{
    position:relative;
    z-index:2;
    max-width:720px;
    margin:0 auto;
    padding:64px 24px 120px;
    text-align:center;
  }

  .eyebrow{
    display:inline-block;
    font-size:14px;
    letter-spacing:0.14em;
    text-transform:uppercase;
    color:var(--deep-rose);
    background:rgba(255,255,255,0.6);
    border:1px solid rgba(232,96,125,0.25);
    padding:6px 18px;
    border-radius:999px;
    margin-bottom:28px;
  }

  h1{
    font-family:'Caveat', cursive;
    font-weight:700;
    font-size:clamp(48px, 10vw, 84px);
    line-height:1.05;
    margin:0 0 8px;
    color:var(--deep-rose);
    text-shadow:0 2px 0 rgba(255,255,255,0.6);
  }

  .subtitle{
    font-size:17px;
    color:#8a6f6d;
    margin-bottom:44px;
  }

  .bouquet{
    font-size:56px;
    margin:8px 0 48px;
    letter-spacing:6px;
    filter:drop-shadow(0 6px 10px rgba(194,65,94,0.15));
  }

  /* ---------- Letter card ---------- */
  .letter{
    background:rgba(255,255,255,0.75);
    backdrop-filter:blur(6px);
    border:1px solid rgba(255,255,255,0.9);
    border-radius:28px;
    padding:44px 36px;
    box-shadow:0 24px 60px -20px rgba(194,65,94,0.25);
    text-align:left;
    position:relative;
    margin-bottom:56px;
  }

  .letter::before{
    content:"🌷";
    position:absolute;
    top:-26px;
    left:50%;
    transform:translateX(-50%);
    font-size:36px;
    background:var(--cream);
    border-radius:50%;
    padding:6px 10px;
    box-shadow:0 6px 14px rgba(194,65,94,0.2);
  }

  .letter p{
    font-size:17px;
    line-height:1.85;
    margin:0 0 18px;
    color:#5B4442;
  }

  .letter p:last-child{ margin-bottom:0; }

  .signoff{
    font-family:'Caveat', cursive;
    font-size:30px;
    color:var(--deep-rose);
    margin-top:22px;
  }

  .to-line{
    font-family:'Caveat', cursive;
    font-size:34px;
    color:var(--deep-rose);
    margin-bottom:6px;
    display:block;
  }

  /* ---------- Button ---------- */
  .cta{
    font-family:'Quicksand', sans-serif;
    font-weight:700;
    font-size:18px;
    color:#fff;
    background:linear-gradient(135deg, var(--rose), var(--deep-rose));
    border:none;
    padding:16px 40px;
    border-radius:999px;
    cursor:pointer;
    box-shadow:0 14px 30px -10px rgba(194,65,94,0.55);
    transition:transform 0.15s ease, box-shadow 0.15s ease;
  }
  .cta:hover{ transform:translateY(-2px) scale(1.03); box-shadow:0 18px 34px -8px rgba(194,65,94,0.6); }
  .cta:active{ transform:translateY(0) scale(0.98); }
  .cta:focus-visible{ outline:3px solid var(--gold); outline-offset:3px; }

  .after-cta{
    margin-top:24px;
    font-size:16px;
    color:#8a6f6d;
    min-height:24px;
  }

  .choice-row{
    display:flex;
    flex-wrap:wrap;
    gap:16px;
    justify-content:center;
  }

  .cta-no{
    background:#fff;
    color:var(--deep-rose);
    border:2px solid var(--rose);
    box-shadow:none;
  }
  .cta-no:hover{
    background:rgba(232,96,125,0.08);
    box-shadow:none;
  }

  /* ---------- Modal loop ---------- */
  .modal-overlay{
    position:fixed;
    inset:0;
    background:rgba(91,68,66,0.45);
    backdrop-filter:blur(4px);
    display:none;
    align-items:center;
    justify-content:center;
    z-index:10;
    padding:20px;
  }
  .modal-overlay.show{
    display:flex;
    animation:fadeIn 0.25s ease;
  }
  @keyframes fadeIn{
    from{ opacity:0; }
    to{ opacity:1; }
  }

  .modal-card{
    background:var(--cream);
    border-radius:24px;
    padding:36px 28px;
    max-width:360px;
    width:100%;
    text-align:center;
    box-shadow:0 30px 70px -20px rgba(91,68,66,0.5);
    animation:popIn 0.3s cubic-bezier(.34,1.56,.64,1);
  }
  @keyframes popIn{
    from{ transform:scale(0.8); opacity:0; }
    to{ transform:scale(1); opacity:1; }
  }

  .modal-emoji{
    font-size:44px;
    margin-bottom:12px;
  }

  .modal-text{
    font-family:'Caveat', cursive;
    font-size:28px;
    color:var(--deep-rose);
    margin:0 0 22px;
    line-height:1.3;
  }

  .modal-buttons{
    display:flex;
    flex-direction:column;
    gap:12px;
  }
  .modal-buttons .cta{
    width:100%;
    padding:14px 20px;
    font-size:16px;
  }

  .burst{
    position:fixed;
    inset:0;
    pointer-events:none;
    z-index:5;
  }
  .burst span{
    position:absolute;
    font-size:26px;
    animation:pop 1.4s ease-out forwards;
  }
  @keyframes pop{
    0%{ transform:translate(0,0) scale(0.4); opacity:0; }
    15%{ opacity:1; }
    100%{ transform:translate(var(--dx), var(--dy)) scale(1.1) rotate(180deg); opacity:0; }
  }

  footer{
    position:relative;
    z-index:2;
    text-align:center;
    padding-bottom:40px;
    font-size:13px;
    color:#b78a8f;
  }
</style>
</head>
<body>

<div class="petals" id="petals" aria-hidden="true"></div>

<main>
  <span class="eyebrow">a very important delivery</span>
  <h1>I'm Sorry, Madam Ji 🙇‍♂️💐</h1>
  <p class="subtitle">please read till the end… there might be flowers involved 🌸</p>
  <div class="bouquet">🌹🌷🌻🌼🌺</div>

  <section class="letter">
    <span class="to-line">Dear Madam Ji,</span>
    <p>I know you're upset with me, and honestly, you have every right to be. I messed up, and instead of making excuses, I just want to say — I'm sorry. Truly, from the bottom of my heart.</p>
    <p>You mean the world to me, and seeing you upset because of something I did is honestly the worst feeling. I hate that I made you feel that way, even for a second. 🥺</p>
    <p>I promise I'm listening, I'm learning, and I want to do better — not because I'm scared of your anger (okay, maybe a little 😅), but because you deserve so much better than to feel hurt by the person who loves you the most.</p>
    <p>So here's a little bouquet of digital flowers 💐, a whole lot of emojis, and all of my heart — begging for one more chance to make you smile again.</p>
    <p class="signoff">Forever your (sorry) person 🐻❤️</p>
  </section>

  <div class="choice-row">
    <button class="cta" id="forgiveBtn">I forgive you 🥹💕</button>
    <button class="cta cta-no" id="noForgiveBtn">I won't forgive you 😤</button>
  </div>
  <div class="after-cta" id="afterMsg"></div>
</main>

<div class="burst" id="burst" aria-hidden="true"></div>

<div class="modal-overlay" id="modalOverlay">
  <div class="modal-card">
    <div class="modal-emoji" id="modalEmoji">🥺</div>
    <p class="modal-text" id="modalText">please forgive me?</p>
    <div class="modal-buttons">
      <button class="cta" id="modalYes">I forgive you 💕</button>
      <button class="cta cta-no" id="modalNo">I won't forgive you</button>
    </div>
  </div>
</div>

<footer>made with a lot of overthinking and a little bit of love 🌼</footer>

<script>
  // Falling petals
  const petalEmojis = ['🌸','🌷','🌹','🌺','💮','🌼'];
  const petalsContainer = document.getElementById('petals');
  const petalCount = window.innerWidth < 600 ? 14 : 24;

  for (let i = 0; i < petalCount; i++) {
    const p = document.createElement('span');
    p.className = 'petal';
    p.textContent = petalEmojis[Math.floor(Math.random() * petalEmojis.length)];
    p.style.left = Math.random() * 100 + 'vw';
    const duration = 8 + Math.random() * 10;
    const swayDuration = 3 + Math.random() * 3;
    p.style.animationDuration = duration + 's, ' + swayDuration + 's';
    p.style.animationDelay = (-Math.random() * duration) + 's, ' + (-Math.random() * swayDuration) + 's';
    p.style.fontSize = (16 + Math.random() * 14) + 'px';
    petalsContainer.appendChild(p);
  }

  // Forgive flow
  const forgiveBtn = document.getElementById('forgiveBtn');
  const noForgiveBtn = document.getElementById('noForgiveBtn');
  const burst = document.getElementById('burst');
  const afterMsg = document.getElementById('afterMsg');

  const modalOverlay = document.getElementById('modalOverlay');
  const modalText = document.getElementById('modalText');
  const modalEmoji = document.getElementById('modalEmoji');
  const modalYes = document.getElementById('modalYes');
  const modalNo = document.getElementById('modalNo');

  const happyMessages = [
    "yayyy 🥳 my heart just did a little happy dance 💃",
    "best news I've heard all day 😭❤️",
    "I owe you a real bouquet now, Madam Ji 🌹",
    "okay now go smile, I can feel it from here 😄"
  ];

  const pleadSequence = [
    { emoji: "🥺", text: "please forgive me?" },
    { emoji: "😭", text: "pleaseee, I really am sorry" },
    { emoji: "🙏", text: "okay but actually, please forgive me" },
    { emoji: "🌹", text: "I brought (digital) flowers... forgive me?" },
    { emoji: "😢", text: "I'm not closing this until you say yes 😅" },
    { emoji: "🐶", text: "even this doesn't want you angry anymore, please?" },
    { emoji: "🤲", text: "one tiny 'I forgive you' is all I need" }
  ];
  let pleadIndex = 0;

  function fireConfetti(fromEl) {
    const emojis = ['🌸','💐','❤️','🌷','✨','🌹'];
    const rect = fromEl.getBoundingClientRect();
    for (let i = 0; i < 26; i++) {
      const s = document.createElement('span');
      s.textContent = emojis[Math.floor(Math.random() * emojis.length)];
      s.style.left = (rect.left + rect.width / 2) + 'px';
      s.style.top = (rect.top + rect.height / 2) + 'px';
      const angle = Math.random() * Math.PI * 2;
      const dist = 80 + Math.random() * 220;
      s.style.setProperty('--dx', Math.cos(angle) * dist + 'px');
      s.style.setProperty('--dy', Math.sin(angle) * dist + 'px');
      s.style.animationDelay = (Math.random() * 0.2) + 's';
      burst.appendChild(s);
      setTimeout(() => s.remove(), 1600);
    }
  }

  function celebrate(fromEl) {
    fireConfetti(fromEl);
    forgiveBtn.textContent = "yayy! 🎉";
    afterMsg.textContent = happyMessages[Math.floor(Math.random() * happyMessages.length)];
    modalOverlay.classList.remove('show');
  }

  function showModal() {
    const step = pleadSequence[pleadIndex % pleadSequence.length];
    modalEmoji.textContent = step.emoji;
    modalText.textContent = step.text;
    modalOverlay.classList.add('show');
  }

  forgiveBtn.addEventListener('click', () => celebrate(forgiveBtn));

  noForgiveBtn.addEventListener('click', () => {
    pleadIndex = 0;
    showModal();
  });

  modalYes.addEventListener('click', () => celebrate(modalYes));

  modalNo.addEventListener('click', () => {
    pleadIndex++;
    showModal();
  });
</script>

</body>
</html>
