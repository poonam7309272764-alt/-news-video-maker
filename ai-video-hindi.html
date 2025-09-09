<!DOCTYPE html>
<html lang="hi">
<head>
  <meta charset="UTF-8">
  <title>Pro News Style Hindi AI Video Maker</title>
  <link href="https://fonts.googleapis.com/css2?family=Noto+Sans+Devanagari:wght@400;700&display=swap" rel="stylesheet">
  <style>
    body{font-family:'Noto Sans Devanagari',Arial,sans-serif;background:#eef2f7;margin:20px;color:#333;}
    textarea,input,button{width:100%;padding:10px;margin:6px 0;font-size:16px;border-radius:6px;border:1px solid #ccc;}
    button{background:#1caf90;color:#fff;border:none;cursor:pointer;transition:0.3s;}
    button:hover{background:#15906f;}
    canvas{display:block;margin:20px auto;border-radius:12px;box-shadow:0 8px 24px rgba(0,0,0,0.3);}
    video{display:block;margin:20px auto;max-width:100%;border-radius:8px;box-shadow:0 6px 18px rgba(0,0,0,0.2);}
    #downloadArea a{display:inline-block;margin-top:10px;padding:10px 20px;background:#1caf90;color:#fff;text-decoration:none;border-radius:6px;}
    #downloadArea a:hover{background:#15906f;}
    @media (max-width:600px){
      h2 { font-size:20px; text-align:center; }
      textarea { font-size:14px; }
      button { font-size:14px; padding:8px; }
    }
  </style>
  <script src="https://cdn.jsdelivr.net/npm/@ffmpeg/ffmpeg@0.12.2/dist/ffmpeg.min.js"></script>
</head>
<body>
<h2>🎥 Pro News Style Hindi AI Video Maker</h2>
<textarea id="textInput" placeholder="हर line अलग स्लाइड के लिए लिखा जाए">नमस्कार, आप News Studio देख रहे हैं।
Bihar Vidyalay Pareeksha Samiti ne STAIT 2025 ka notification jaari kar diya hai।
Dhanyavaad!</textarea>
<input type="number" id="pauseTime" value="500" placeholder="Slide Pause (ms)">
<input type="text" id="bgURL" value="https://images.unsplash.com/photo-1506744038136-46273834b3fb?auto=format&fit=crop&w=800&q=80" placeholder="Background URL">
<input type="text" id="logoLeft" value="https://upload.wikimedia.org/wikipedia/commons/4/47/React.svg" placeholder="Left Logo URL">
<input type="text" id="logoRight" value="https://upload.wikimedia.org/wikipedia/commons/4/47/React.svg" placeholder="Right Logo URL">
<input type="text" id="tickerText" value="Breaking News: Bihar Vidyalay Pareeksha Samiti STAIT 2025 Notification Live!" placeholder="Bottom ticker text">
<input type="text" id="bgMusicURL" placeholder="Background Music URL (Optional)" value="">
<button id="previewBtn">▶ Preview Slides</button>
<button id="recordBtn">💾 Record + Download MP4</button>
<p id="status">Status: ready</p>
<canvas id="canvas" width="1280" height="620"></canvas>
<video id="videoPreview" controls></video>
<div id="downloadArea"></div>

<script>
const canvas = document.getElementById('canvas');
const ctx = canvas.getContext('2d');
const textInput = document.getElementById('textInput');
const pauseCtrl = document.getElementById('pauseTime');
const bgURL = document.getElementById('bgURL');
const logoLeftURL = document.getElementById('logoLeft');
const logoRightURL = document.getElementById('logoRight');
const tickerTextInput = document.getElementById('tickerText');
const bgMusicURL = document.getElementById('bgMusicURL');
const statusEl = document.getElementById('status');
const videoPreview = document.getElementById('videoPreview');
const downloadArea = document.getElementById('downloadArea');
let bgImg = new Image(), logoLeft = new Image(), logoRight = new Image();
let tickerOffset = 0, blockY = -100, animationId;

function wrapText(ctx, text, maxWidth){
  const words = text.split(' ');
  let lines = [], line = '';
  for(let n=0;n<words.length;n++){
    const testLine = line + words[n] + ' ';
    if(ctx.measureText(testLine).width>maxWidth && n>0){
      lines.push(line);
      line = words[n] + ' ';
    } else line = testLine;
  }
  lines.push(line);
  return lines;
}
function drawTicker(text){
  const fontSize=36;
  ctx.fillStyle="red";
  ctx.fillRect(0,canvas.height-fontSize-20,canvas.width,fontSize+20);
  ctx.fillStyle="white";
  ctx.font=`bold ${fontSize}px Noto Sans Devanagari`;
  ctx.textAlign="left";
  ctx.textBaseline="middle";
  tickerOffset -= 4;
  if(tickerOffset < -ctx.measureText(text).width) tickerOffset=canvas.width;
  ctx.fillText(text,tickerOffset,canvas.height-fontSize/2-10);
}
function drawParagraphDown(text){
  ctx.clearRect(0,0,canvas.width,canvas.height);
  if(bgImg.complete) ctx.drawImage(bgImg,0,0,canvas.width,canvas.height);
  ctx.fillStyle="rgba(0,0,0,0.3)";
  ctx.fillRect(0,0,canvas.width,canvas.height);
  if(logoLeft.complete) ctx.drawImage(logoLeft,30,30,200,80);
  if(logoRight.complete) ctx.drawImage(logoRight,canvas.width-230,30,200,80);
  ctx.fillStyle="white";
  ctx.font="bold 40px Noto Sans Devanagari";
  ctx.textAlign="center";
  ctx.textBaseline="top";
  const lines=wrapText(ctx,text,canvas.width-200);
  const lineHeight=60;
  const totalHeight=lines.length*lineHeight;
  const safeBottom=canvas.height-120;
  for(let i=0;i<lines.length;i++){
    ctx.fillText(lines[i].trim(),canvas.width/2,blockY+i*lineHeight);
  }
  if(blockY<(safeBottom-totalHeight)/2){
    blockY+=2;
  }
  drawTicker(tickerTextInput.value);
}
// सिर्फ प्रीव्यू
document.getElementById('previewBtn').onclick=async()=>{
  const lines=textInput.value.split('\n').filter(Boolean);
  bgImg.src=bgURL.value; logoLeft.src=logoLeftURL.value; logoRight.src=logoRightURL.value;
  await new Promise(r=>{bgImg.onload=logoLeft.onload=logoRight.onload=r;});
  statusEl.textContent="Status: previewing...";
  for(let line of lines){
    blockY=-150;
    function animate(){
      drawParagraphDown(line);
      animationId=requestAnimationFrame(animate);
    }
    animate();
    await new Promise(res=>setTimeout(res,1500 + parseInt(pauseCtrl.value)));
    cancelAnimationFrame(animationId);
  }
  statusEl.textContent="Status: ready";
};

// Record + Download, MP4 via ffmpeg.js
async function convertWebMtoMP4(webmBlob) {
  const { createFFmpeg, fetchFile } = FFmpeg;
  const ffmpeg = createFFmpeg({ log: false });
  await ffmpeg.load();
  ffmpeg.FS('writeFile', 'input.webm', await fetchFile(webmBlob));
  await ffmpeg.run('-i', 'input.webm', '-c:v', 'libx264', '-preset', 'fast', '-pix_fmt', 'yuv420p', 'output.mp4');
  const data = ffmpeg.FS('readFile', 'output.mp4');
  return new Blob([data.buffer], { type: 'video/mp4' });
}

document.getElementById('recordBtn').onclick=async()=>{
  const lines = textInput.value.split('\n').filter(Boolean);
  bgImg.src = bgURL.value;
  logoLeft.src = logoLeftURL.value;
  logoRight.src = logoRightURL.value;
  await new Promise(r=>{bgImg.onload=logoLeft.onload=logoRight.onload=r;});
  const stream=canvas.captureStream(30);
  let chunks=[];
  const mediaRecorder=new MediaRecorder(stream,{mimeType:'video/webm;codecs=vp9'});
  mediaRecorder.ondataavailable=e=>chunks.push(e.data);
  mediaRecorder.start();
  statusEl.textContent="Recording...";
  for(let line of lines){
    blockY = -150;
    function animate(){
      drawParagraphDown(line);
      animationId = requestAnimationFrame(animate);
    }
    animate();
    await new Promise(res=>setTimeout(res,1500 + parseInt(pauseCtrl.value)));
    cancelAnimationFrame(animationId);
  }
  mediaRecorder.stop();
  mediaRecorder.onstop=async()=>{
    statusEl.textContent="Converting video to MP4...";
    const webmBlob = new Blob(chunks, { type: 'video/webm' });
    const mp4Blob = await convertWebMtoMP4(webmBlob);
    statusEl.textContent = "Conversion done. Ready for download.";
    const url = URL.createObjectURL(mp4Blob);
    videoPreview.src = url;
    const a = document.createElement('a');
    a.href = url;
    a.download = 'news-video.mp4';
    a.textContent = '⬇ Download Video MP4';
    downloadArea.innerHTML = '';
    downloadArea.appendChild(a);
  };
};
</script>
</body>
</html>
