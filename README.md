# Kajatec-page
<!doctype html>
<html lang="id">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Would you be my kaJaTEC — Clone</title>
  <style>
    :root{--bg:#f5f7fb;--card:#ffffff;--accent:#ff6b81;--muted:#6b7280}
    html,body{height:100%;margin:0;font-family:Inter, system-ui, -apple-system, "Segoe UI", Roboto}
    body{display:flex;align-items:center;justify-content:center;background:linear-gradient(180deg,#ffe6eb 0%,var(--bg) 100%);padding:20px}
    .card{width:100%;max-width:520px;background:var(--card);border-radius:16px;box-shadow:0 10px 30px rgba(16,24,40,0.08);padding:32px;text-align:center;cursor:pointer}
    h1{margin:0 0 8px;font-size:28px;color:#0f172a}
    p.lead{margin:0 0 18px;color:var(--muted)}
    .question{font-weight:600;margin:18px 0;font-size:20px}
    .btns{display:flex;gap:12px;justify-content:center;margin-top:10px}
    button{padding:12px 20px;border-radius:10px;border:0;font-weight:600;cursor:pointer;font-size:16px}
    .btn-yes{background:linear-gradient(90deg,#ff8fa3,#ff6b81);color:white}
    .btn-no{background:#eef2f8;color:#0b1220}
    .hidden{display:none}

    .thanks{font-size:18px;margin-top:18px;color:#0f172a}
    .subthanks{color:var(--muted);margin-top:6px}

    /* efek love-love */
    .love-container{position:fixed;left:0;top:0;width:100%;height:100%;pointer-events:none;overflow:hidden}
    .love{position:absolute;font-size:24px;animation:floatUp 2.2s linear forwards;opacity:0}
    @keyframes floatUp{
      0%{transform:translateY(20px) scale(0.6);opacity:1}
      50%{transform:translateY(-60px) scale(1)}
      100%{transform:translateY(-140px) scale(1.3);opacity:0}
    }
  </style>
</head>
<body>
  <div class="card" role="main" id="card">
    <h1>Hai Kak Delvia</h1>
    <p class="lead">Klik kartu ini dulu untuk membuka sesuatu ✨</p>

    <div id="intro"></div>

    <div id="content" class="hidden">
      <div class="question">Would you be my <strong>kaJaTEC</strong>?</div>
      <div class="btns">
        <button class="btn-yes" id="yesBtn">Yes</button>
        <button class="btn-no" id="noBtn">No</button>
      </div>
    </div>

    <div id="response" class="hidden">
      <div class="thanks">Makasiii banyak kakkk!!!!</div>
      <div class="subthanks">Tengkyuu kak udah nerima akuu, semoga kita bisa menjadi DeJaTEC dan KaJaTEC yg solidd, gacorr, dan kecee selalu 💖</div>
    </div>
  </div>

  <div class="love-container" id="loveContainer"></div>

  <script>
    const card = document.getElementById('card');
    const content = document.getElementById('content');
    const yesBtn = document.getElementById('yesBtn');
    const noBtn = document.getElementById('noBtn');
    const response = document.getElementById('response');
    const loveContainer = document.getElementById('loveContainer');

    let opened = false;

    card.addEventListener('click', ()=>{
      if(opened) return;
      opened = true;
      content.classList.remove('hidden');
      card.style.cursor = 'default';
    });

    function createLove(){
      const love = document.createElement('div');
      love.className = 'love';
      love.textContent = '💖';
      love.style.left = Math.random()*90 + '%';
      love.style.bottom = '20px';
      loveContainer.appendChild(love);
      setTimeout(()=> love.remove(), 2200);
    }

    function burstLove(count = 35){
      for(let i=0;i<count;i++){
        setTimeout(()=> createLove(), i * 60);
      }
    }

    yesBtn.addEventListener('click', ()=>{
      content.classList.add('hidden');
      response.classList.remove('hidden');
      burstLove(40);
    });

    noBtn.addEventListener('click', ()=>{
      const cardAnim = document.querySelector('.card');
      cardAnim.animate([
        { transform: 'translateX(0)' },
        { transform: 'translateX(-12px)' },
        { transform: 'translateX(10px)' },
        { transform: 'translateX(-8px)' },
        { transform: 'translateX(6px)' },
        { transform: 'translateX(0)' }
      ], { duration: 500, easing: 'ease-out' });
    });
  </script>
</body>
</html>
