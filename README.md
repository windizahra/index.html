<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Watch Full Video</title>

<style>
body{
    margin:0;
    padding:0;
    background:#111;
    font-family:Arial, sans-serif;
    display:flex;
    justify-content:center;
    align-items:center;
    min-height:100vh;
}

.container{
    text-align:center;
    padding:20px;
    color:white;
}

.video-box{
    position:relative;
    display:inline-block;
    max-width:400px;
    width:100%;
}

.video-box img{
    width:100%;
    border-radius:12px;
    box-shadow:0 4px 15px rgba(0,0,0,0.4);
}

.play-button{
    position:absolute;
    top:50%;
    left:50%;
    transform:translate(-50%, -50%);
    width:80px;
    height:80px;
    background:rgba(255,0,0,0.85);
    border-radius:50%;
    display:flex;
    justify-content:center;
    align-items:center;
    animation:pulse 1.5s infinite;
}

.play-button:before{
    content:'';
    border-left:24px solid white;
    border-top:14px solid transparent;
    border-bottom:14px solid transparent;
    margin-left:6px;
}

.watch-btn{
    display:inline-block;
    margin-top:20px;
    padding:14px 24px;
    background:#ff2d2d;
    color:white;
    text-decoration:none;
    border-radius:8px;
    font-size:18px;
    transition:0.3s;
}

.watch-btn:hover{
    transform:scale(1.05);
}

.desc{
    margin-top:15px;
    color:#ddd;
    font-size:16px;
}

@keyframes pulse{
    0%{
        transform:translate(-50%, -50%) scale(1);
        box-shadow:0 0 0 0 rgba(255,0,0,0.7);
    }
    70%{
        transform:translate(-50%, -50%) scale(1.1);
        box-shadow:0 0 0 20px rgba(255,0,0,0);
    }
    100%{
        transform:translate(-50%, -50%) scale(1);
        box-shadow:0 0 0 0 rgba(255,0,0,0);
    }
}
</style>
</head>

<body>

<div class="container">

    <h1>Watch the Full Video 👇</h1>

    <a href="https://t.co/qOMTl1m4Wu" target="_blank" class="video-box">

        <img src="https://cdn2.aceimg.com/a0aef2e61.png" alt="Thumbnail">

        <div class="play-button"></div>

    </a>

    <p class="desc">
        Don’t miss what happens next… 👀
    </p>

    <a href="https://t.co/qOMTl1m4Wu" target="_blank" class="watch-btn">
        ▶ Click Here To Watch
    </a>

</div>

</body>
</html>
