<!DOCTYPE html>
<html lang="tr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Çıkma Teklifi</title>
<style>
  body {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    height: 100vh;
    background: radial-gradient(#ffe6e6, #ffd6f0);
    overflow: hidden;
    font-family: Arial, sans-serif;
    position: relative;
  }

  /* Zarf */
  #envelope {
    width: 200px;
    height: 120px;
    background: #ffffff;
    clip-path: polygon(0 0, 100% 0, 100% 100%, 0% 100%, 50% 50%);
    cursor: pointer;
    position: relative;
    transition: transform 0.5s;
    z-index: 2;
  }

  /* Kalp balonları */
  .heart {
    position: absolute;
    width: 25px;
    height: 25px;
    transform: rotate(-45deg);
    border-radius: 15px 15px 0 0;
    animation: float linear infinite;
  }
  .heart:before,
  .heart:after {
    content: '';
    position: absolute;
    width: 25px;
    height: 25px;
    border-radius: 50%;
  }
  .heart:before { top: -12.5px; left: 0; }
  .heart:after { top: 0; left: 12.5px; }

  @keyframes float {
    0% { transform: translateY(0) rotate(-45deg); opacity: 1; }
    100% { transform: translateY(-400px) rotate(-45deg); opacity: 0; }
  }

  /* Kedi videosu */
  #catVideo {
    display: none;
    width: 250px;
    height: 250px;
    border-radius: 50%;
    overflow: hidden;
    margin-top: 20px;
    animation: zoomIn 0.8s ease forwards;
  }

  #catVideo iframe {
    width: 100%;
    height: 100%;
    border-radius: 50%;
  }

  @keyframes zoomIn {
    0% { transform: scale(0); opacity: 0; }
    100% { transform: scale(1); opacity: 1; }
  }

  /* Mesaj */
  #message {
    display: none;
    text-align: center;
    font-size: 24px;
    color: #ff1a75;
    font-weight: bold;
    margin-top: 20px;
    padding: 0 20px;
    animation: fadeIn 1s ease forwards;
  }

  @keyframes fadeIn {
    from { opacity: 0; }
    to { opacity: 1; }
  }

  /* Yıldız efekti */
  .star {
    position: absolute;
    width: 3px;
    height: 3px;
    background: white;
    border-radius: 50%;
    opacity: 0.8;
    animation: twinkle 2s infinite alternate;
  }

  @keyframes twinkle {
    from { opacity: 0.3; }
    to { opacity: 1; }
  }
</style>
</head>
<body>

<div id="envelope"></div>

<div id="catVideo">
  <iframe src="https://www.youtube.com/embed/xsmA_QLSo5Q?autoplay=1&mute=1&loop=1&playlist=xsmA_QLSo5Q"
          frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>
</div>

<div id="message">Bundan sonraki hayatımda kalbimin atma sebebi olur musun? <br>Benimle çıkar mısın? ❤️</div>

<!-- Müzik -->
<iframe id="musicFrame" width="0" height="0"
        src="https://www.youtube.com/embed/esVxFGu2Tro?autoplay=0&loop=1&playlist=esVxFGu2Tro"
        frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

<script>
  const envelope = document.getElementById('envelope');
  const message = document.getElementById('message');
  const catVideo = document.getElementById('catVideo');
  const musicFrame = document.getElementById('musicFrame');

  // Arka plan yıldızları
  for(let i=0;i<50;i++){
    const star=document.createElement('div');
    star.className='star';
    star.style.top=Math.random()*100+'%';
    star.style.left=Math.random()*100+'%';
    star.style.width=1+Math.random()*2+'px';
    star.style.height=1+Math.random()*2+'px';
    star.style.animationDuration=1+Math.random()*2+'s';
    document.body.appendChild(star);
  }

  envelope.addEventListener('click', () => {
    envelope.style.transform = 'scale(0)';
    catVideo.style.display = 'block';
    message.style.display = 'block';

    // Müzik 1.24 saniye sonra başlasın
    setTimeout(() => {
      musicFrame.src += "&autoplay=1";
    }, 1240);

    // Kalp balonları
    const colors=['#ff1a75','#ff66a3','#ff99cc'];
    for (let i = 0; i < 15; i++) {
      const heart = document.createElement('div');
      heart.className = 'heart';
      heart.style.background = colors[Math.floor(Math.random()*colors.length)];
      heart.style.left = `${Math.random() * 90}%`;
      heart.style.width = 20 + Math.random()*15 + 'px';
      heart.style.height = 20 + Math.random()*15 + 'px';
      heart.style.animationDuration = `${3 + Math.random() * 3}s`;
      document.body.appendChild(heart);
    }
  });
</script>

</body>
</html>

