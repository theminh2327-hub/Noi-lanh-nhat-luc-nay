<!doctype html>
<html lang="vi">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>Thiệp 20/10 — Có nhạc</title>
<style>
  :root{--accent:#ff5c8a;--bg1:#fce3ec;--bg2:#f9f1ff}
  *{box-sizing:border-box}
  body{
    margin:0; min-height:100vh; display:flex; align-items:center; justify-content:center;
    font-family:Inter, system-ui, -apple-system, "Segoe UI", Roboto, Arial;
    background: linear-gradient(135deg,var(--bg1),var(--bg2));
    color:#333; padding:28px;
  }
  .card{
    width:100%; max-width:720px; background:rgba(255,255,255,0.92);
    border-radius:14px; padding:28px; text-align:center; box-shadow:0 18px 40px rgba(10,10,30,0.08);
    position:relative;
  }
  h1{margin:0 0 6px; color:var(--accent); font-size:1.6rem}
  p{margin:8px 0 0; color:#444; line-height:1.6}
  .btn{
    display:inline-block; margin-top:22px; padding:12px 20px; border-radius:24px;
    background:var(--accent); color:white; border:0; cursor:pointer; font-weight:600;
    position:relative; z-index:20;
  }
  audio{ position:fixed; left:-9999px; width:1px; height:1px; } /* hide but don't overlay */
  .modal{ position:fixed; inset:0; display:flex; align-items:center; justify-content:center;
    background:rgba(0,0,0,0.45); visibility:hidden; opacity:0; transition:opacity .18s; }
  .modal.show{ visibility:visible; opacity:1; }
  .modal .box{ background:white; padding:18px; border-radius:12px; max-width:90%; text-align:center;}
</style>
</head>
<body>
  <div class="card" id="card">
    <h1>💐 Chúc em 20/10 thật vui</h1>
    <p>Luôn xinh đẹp và rạng rỡ như chính nụ cười của em 💫</p>
    <button class="btn" id="smallBtn" type="button">Gửi một điều nhỏ xíu 💌</button>
  </div>

  <div class="modal" id="modal">
    <div class="box" role="dialog" aria-modal="true">
      <p id="modalText">Cảm ơn em vì đã làm ngày thường của anh đặc biệt hơn một chút ❤️</p>
      <button id="closeModal" style="margin-top:12px;padding:8px 14px;border-radius:10px;border:0;background:#ddd;">Đóng</button>
    </div>
  </div>

  <!-- audio hidden off-screen so it doesn't capture clicks -->
  <audio id="bgAudio" autoplay loop>
    <source src="https://cdn.pixabay.com/download/audio/2022/03/15/audio_10d85e1f6a.mp3?filename=lofi-study-112191.mp3" type="audio/mpeg">
  </audio>

<script>
document.addEventListener('DOMContentLoaded', function(){
  const btn = document.getElementById('smallBtn');
  const modal = document.getElementById('modal');
  const close = document.getElementById('closeModal');
  const audio = document.getElementById('bgAudio');

  // ensure button is clickable
  btn.style.pointerEvents = 'auto';

  btn.addEventListener('click', function(e){
    // some mobile browsers require user interaction to play audio — resume on click
    if (audio && typeof audio.play === 'function') {
      audio.play().catch(()=>{/* autoplay may fail, ignore */});
    }
    modal.classList.add('show');
  });

  close.addEventListener('click', function(){ modal.classList.remove('show'); });

  modal.addEventListener('click', function(ev){
    if(ev.target === modal) modal.classList.remove('show');
  });
});
</script>
</body>
</html>