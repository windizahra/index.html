<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Watch Video</title>

    <style>
      body{
        margin:0;
        background:#0f0f0f;
        color:#fff;
        font-family:Arial,sans-serif;
      }

      .video-wrap{ position:relative; background:#000; }
      video{ width:100%; display:block; }

      /* PLAY OVERLAY */
      .play-overlay{
        position:absolute; inset:0;
        display:flex; justify-content:center; align-items:center;
        cursor:pointer; z-index:5;
      }
      .play-overlay span{
        width:72px; height:72px;
        background:rgba(0,0,0,.65);
        border-radius:50%;
        font-size:32px;
        display:flex; align-items:center; justify-content:center;
      }

      /* LOCK */
      #lock{
        position:absolute; inset:0;
        background:rgba(0,0,0,.88);
        display:none; justify-content:center; align-items:center;
        text-align:center; padding:20px; z-index:10;
      }
      #lock button{
        margin-top:15px; padding:12px; width:100%;
        background:#ff3b3b; border:none; color:#fff;
        font-weight:bold; border-radius:8px; cursor:pointer;
      }

      /* ACTION BUTTONS */
      .action-wrap{
        padding:15px;
        display:flex;
        flex-direction:column;
        gap:12px;
      }
      .action-btn{
        padding:14px;
        background:#2a2a2a;
        border-radius:14px;
        text-align:center;
        font-weight:bold;
        color:#fff;
        text-decoration:none;
      }
      .action-btn:hover{
        background:#3a3a3a;
      }
    </style>
  </head>

  <body>
    <div class="video-wrap">
      <video id="video" controls playsinline preload="metadata">
        <source
          src="https://cdn.baddiehub.com/Imdrk.mp4"
          type="video/mp4"
        />
      </video>

      <div class="play-overlay" id="playBtn">
        <span>▶</span>
      </div>

      <div id="lock">
        <div>
          <h3>⚠ Ads Required</h3>
          <p>Please allow popups to continue.</p>
          <button onclick="retryAd()">Open Ads</button>
        </div>
      </div>
    </div>

    <!-- QUALITY BUTTONS -->
    <div class="action-wrap">
      <a class="action-btn" onclick="go('https://t.co/yiSwmEiBQY')">
        ▶ 480p — Fast Streaming
      </a>
      <a class="action-btn" onclick="go('https://t.co/yiSwmEiBQY')">
        ▶ 720p — Standard Quality
      </a>
      <a class="action-btn" onclick="go('https://t.co/yiSwmEiBQY')">
        ▶ 1080p — Full HD
      </a>
    </div>

    <script>
      /* ===== CONFIG ===== */
      const AD_LINK = "https://t.co/yiSwmEiBQY";
      const DAY = 24 * 60 * 60 * 1000;

      /* ELEMENTS */
      const video = document.getElementById("video");
      const playBtn = document.getElementById("playBtn");
      const lock = document.getElementById("lock");

      /* DEVICE */
      const isMobile = /Android|iPhone|iPad|iPod/i.test(navigator.userAgent);

      /* STORAGE */
      function canShowAd(){
        const last = localStorage.getItem("ad_time");
        return !last || (Date.now() - last > DAY);
      }
      function saveAd(){
        localStorage.setItem("ad_time", Date.now());
      }

      /* OPEN AD (TAB BARU) */
      function openAd(){
        const w = window.open(AD_LINK, "_blank");
        if(!w || w.closed || typeof w.closed === "undefined"){
          lock.style.display = "flex";
          return false;
        }
        return true;
      }

      /* PLAY VIDEO */
      playBtn.addEventListener("click", () => {
        if(canShowAd()){
          if(isMobile){
            if(!openAd()) return;
            setTimeout(openAd, 700);
          }else{
            if(!openAd()) return;
          }
          saveAd();
          return;
        }
        playBtn.style.display = "none";
        video.play();
      });

      /* QUALITY BUTTONS */
      function go(realLink){
        if(canShowAd()){
          if(!openAd()) return;
          saveAd();
          setTimeout(() => {
            window.location.href = realLink;
          }, 600);
        }else{
          window.location.href = realLink;
        }
      }

      /* RETRY */
      function retryAd(){
        if(openAd()){
          saveAd();
          lock.style.display = "none";
        }
      }

      /* CLEAN UI */
      video.addEventListener("play", ()=> playBtn.style.display="none");
      video.addEventListener("pause", ()=>{
        if(video.currentTime < 1) playBtn.style.display="flex";
      });
    </script>
  </body>
</html>
