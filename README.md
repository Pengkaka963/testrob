<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>顔追跡モジュールDemo</title>

  <style>
    body {
        font-family: Arial, sans-serif;
        max-width: 1100px;
        margin: 20px auto;
        padding: 10px;
    }

    h1 {
        text-align: center;
        margin-bottom: 30px;
    }

    .container {
        display: flex;
        justify-content: center; /* 视频居中 */
        gap: 20px;
        align-items: center;
    }

    .video-block {
        flex: 1;
    }

    .video-block video {
        width: 100%;
        border-radius: 10px;
    }

    .note {
        margin-top: 25px;
        font-size: 15px;
        line-height: 1.6;
    }

    .note span {
        color: red;
        font-weight: bold;
    }
  </style>
</head>

<body>

<h1>顔追跡モジュールDemo</h1>

<div class="container">
  <div class="video-block">
    <video id="video-main" controls playsinline>
      <source src="stare.mp4" type="video/mp4">
    </video>
  </div>
</div>

<div class="note">
  <span>※</span> ROS制御により <br>
  シミュレータと実機Furhatはそのまま置き換え可能（デジタルツイン）
</div>

<script>
  // 自动把视频第一帧设置为 poster
  function setPosterFromFirstFrame(video) {
    const canvas = document.createElement('canvas');
    video.addEventListener('loadeddata', () => {
      canvas.width = video.videoWidth;
      canvas.height = video.videoHeight;
      const ctx = canvas.getContext('2d');
      ctx.drawImage(video, 0, 0, canvas.width, canvas.height);
      video.setAttribute('poster', canvas.toDataURL());
    });
  }

  const video = document.getElementById('video-main');
  setPosterFromFirstFrame(video);
</script>

</body>
</html>
