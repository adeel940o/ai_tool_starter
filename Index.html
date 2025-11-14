<!--
AI Hybrid Tool - Single Page Starter (HTML + JS)

Instructions (read before using):
1) This is a client-side starter to prototype:
   - Stable Horde (text->image/cartoon generation) calls are attempted directly from client.
   - Replicate / other face-swap providers commonly require server-side proxy (CORS + secret token).

2) Replace API placeholders below with your keys.
   - STABLE_HORDE_API_KEY -> get from Stable Horde (or use anonymous endpoints)
   - REPLICATE_PROXY_ENDPOINT -> recommended: create a small server proxy that accepts image uploads and calls Replicate.

3) Security NOTE: Never publish secret API keys in a public repo or on GitHub Pages. For production, put keys on a server and call the server from the frontend.

4) Deploy: create a GitHub repo, add this file as index.html, enable GitHub Pages (main branch) — site will be live.

--><!doctype html>

<html lang="ur">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width,initial-scale=1">
  <title>AI FaceSwap + Avatar Starter (Prototype)</title>
  <style>
    body{font-family:system-ui,-apple-system,"Segoe UI",Roboto,'Noto Sans',Arial; padding:18px; max-width:980px;margin:0 auto;color:#111}
    h1{font-size:20px;margin-bottom:6px}
    p.lead{color:#333;margin-top:0}
    label{display:block;margin:10px 0 6px}
    .row{display:flex;gap:10px;flex-wrap:wrap}
    .col{flex:1 1 280px}
    input[type=file]{display:block}
    button{padding:10px 14px;border-radius:8px;border:0;background:#0b70ff;color:#fff;cursor:pointer}
    button[disabled]{opacity:.5;cursor:not-allowed}
    .card{border:1px solid #eee;padding:12px;border-radius:10px;background:#fafafa}
    img.preview{max-width:100%;height:auto;border-radius:8px;display:block;margin-top:8px}
    .resultBox{margin-top:12px}
    .note{font-size:13px;color:#666}
    small{color:#666}
    .danger{color:#b21}
    footer{margin-top:18px;font-size:13px;color:#444}
    .controls{display:flex;gap:8px;align-items:center;flex-wrap:wrap}
    select{padding:8px;border-radius:8px}
    .progress{height:10px;background:#eee;border-radius:10px;overflow:hidden}
    .progress > i{height:100%;display:block;background:linear-gradient(90deg,#0b70ff,#36f);width:0}
  </style>
</head>
<body>
  <h1>AI Hybrid Tool — Starter (FaceSwap + Cartoon + Text→Image)</h1>
  <p class="lead">یہ پروٹو ٹائپ ہے — mobile-friendly۔ شروع کرنے کے لیے images اپلوڈ کریں، Zustimmung دیں، اور Generate یا Swap کریں۔</p>  <div class="card">
    <label>آپشن منتخب کریں:</label>
    <div class="controls">
      <select id="mode">
        <option value="face-swap">Face Swap (image → image)</option>
        <option value="cartoon">Cartoon / Avatar (image → stylized)</option>
        <option value="txt2img">Text → Image (prompt)</option>
      </select>
      <button id="actionBtn">شروع کریں</button>
      <div style="flex:1"></div>
    </div><div id="inputs" style="margin-top:12px">
  <!-- Face swap inputs -->
  <div id="faceSwapInputs">
    <label>Source Image (جس کا چہرہ replace ہوگا)</label>
    <input type="file" id="sourceFile" accept="image/*">
    <img id="sourcePreview" class="preview" style="display:none">

    <label>Target Image (جس کا چہرہ استعمال ہوگا)</label>
    <input type="file" id="targetFile" accept="image/*">
    <img id="targetPreview" class="preview" style="display:none">

    <label><input type="checkbox" id="consentChk"> میں تصدیق کرتا/کرتی ہوں کہ میرے پاس دونوں تصاویر کے استعمال کی اجازت ہے۔</label>
    <small class="note">Consent ضروری ہے — Deepfake/face-swap tools کے لیے قانونی اور اخلاقی ذمہ داری بہت اہم ہے۔</small>
  </div>

  <!-- Cartoon inputs -->
  <div id="cartoonInputs" style="display:none">
    <label>Upload Image</label>
    <input type="file" id="cartoonFile" accept="image/*">
    <img id="cartoonPreview" class="preview" style="display:none">
    <label>Style (optional)</label>
    <select id="cartoonStyle">
      <option value="cartoon">Cartoon</option>
      <option value="anime">Anime</option>
      <option value="digital-painting">Digital Painting</option>
    </select>
    <label><input type="checkbox" id="consentCartoon"> I consent to process this image.</label>
  </div>

  <!-- Text to image inputs -->
  <div id="txt2imgInputs" style="display:none">
    <label>Prompt (انگریزی میں)</label>
    <input type="text" id="txtPrompt" placeholder="e.g. portrait of a smiling man in cinematic film lighting">
    <label>Optional Seed</label>
    <input type="number" id="seed" placeholder="leave blank for random">
    <label><input type="checkbox" id="consentTxt"> I agree to the TOS and confirm prompt is allowed.</label>
  </div>
</div>

<div style="margin-top:12px">
  <div class="progress" aria-hidden><i id="progressBar"></i></div>
  <div id="status" style="margin-top:8px"></div>
</div>

<div class="resultBox" id="resultBox"></div>

<div style="margin-top:12px">
  <small class="note">NOTE: This starter uses public endpoints for prototyping. For production keep your API keys on a server and call the server from frontend to avoid exposing secrets.</small>
</div>

  </div>  <footer>
    <p>Deploy steps: 1) Create GitHub repo, add this as index.html, enable GitHub Pages (main branch). 2) Replace API placeholders in the code below. 3) For Replicate face-swap use server proxy (example code available on request).</p>
  </footer>  <script>
  // ====== CONFIG - REPLACE THESE ======
  const STABLE_HORDE_API_KEY = "REPLACE_WITH_STABLE_HORDE_KEY_OR_LEAVE_EMPTY";
  // For Replicate face-swap we recommend a proxy endpoint on your server that accepts files and calls Replicate.
  // Example: const REPLICATE_PROXY_ENDPOINT = "https://your-server.com/api/replicate-face-swap";
  const REPLICATE_PROXY_ENDPOINT = "REPLACE_WITH_REPLICATE_PROXY_ENDPOINT_IF_AVAILABLE";
  // ====================================

  const modeSel = document.getElementById('mode');
  const faceSwapInputs = document.getElementById('faceSwapInputs');
  const cartoonInputs = document.getElementById('cartoonInputs');
  const txt2imgInputs = document.getElementById('txt2imgInputs');
  const actionBtn = document.getElementById('actionBtn');
  const status = document.getElementById('status');
  const progressBar = document.getElementById('progressBar');
  const resultBox = document.getElementById('resultBox');

  modeSel.addEventListener('change',()=>updateUI());
  function updateUI(){
    const v = modeSel.value;
    faceSwapInputs.style.display = (v==='face-swap')? 'block':'none';
    cartoonInputs.style.display = (v==='cartoon')? 'block':'none';
    txt2imgInputs.style.display = (v==='txt2img')? 'block':'none';
    resultBox.innerHTML=''; status.innerText=''; setProgress(0);
  }
  updateUI();

  // file previews
  function readPreview(fileEl, imgEl){
    const f = fileEl.files && fileEl.files[0];
    if(!f){ imgEl.style.display='none'; imgEl.src=''; return; }
    const url = URL.createObjectURL(f);
    imgEl.src = url; imgEl.style.display='block';
  }
  document.getElementById('sourceFile').addEventListener('change',()=>readPreview(document.getElementById('sourceFile'),document.getElementById('sourcePreview')));
  document.getElementById('targetFile').addEventListener('change',()=>readPreview(document.getElementById('targetFile'),document.getElementById('targetPreview')));
  document.getElementById('cartoonFile').addEventListener('change',()=>readPreview(document.getElementById('cartoonFile'),document.getElementById('cartoonPreview')));

  function setStatus(txt){ status.innerText = txt; }
  function setProgress(p){ progressBar.style.width = Math.max(0,Math.min(100,p)) + '%'; }

  actionBtn.addEventListener('click', async ()=>{
    const mode = modeSel.value;
    if(mode==='face-swap') return await handleFaceSwap();
    if(mode==='cartoon') return await handleCartoon();
    if(mode==='txt2img') return await handleTxt2Img();
  });

  async function handleFaceSwap(){
    const src = document.getElementById('sourceFile').files && document.getElementById('sourceFile').files[0];
    const tgt = document.getElementById('targetFile').files && document.getElementById('targetFile').files[0];
    const consent = document.getElementById('consentChk').checked;
    if(!src || !tgt){ alert('براہ مہربانی source اور target دونوں تصاویر اپ لوڈ کریں۔'); return; }
    if(!consent){ alert('Consent درکار ہے۔'); return; }

    resultBox.innerHTML=''; setStatus('Uploading files...'); setProgress(8);

    // If you have a replicate proxy endpoint (recommended), send both files there.
    if(REPLICATE_PROXY_ENDPOINT && !REPLICATE_PROXY_ENDPOINT.startsWith('REPLACE')){
      try{
        setStatus('Sending to Replicate proxy...'); setProgress(18);
        const fd = new FormData(); fd.append('source', src); fd.append('target', tgt);
        const res = await fetch(REPLICATE_PROXY_ENDPOINT, { method:'POST', body:fd });
        if(!res.ok) throw new Error('Proxy call failed: '+res.status);
        const data = await res.json();
        // Expect proxy to return { imageUrl: 'https://...' } or base64 data
        showResultImage(data.imageUrl || data.base64);
        setStatus('Face-swap complete (via proxy)'); setProgress(100);
        return;
      }catch(err){ console.error(err); setStatus('Proxy error: '+err.message); }
    }

    // No proxy: try a simple client-side upload to a free model provider (may fail due to CORS or policy).
    // We'll attempt to send to a demo endpoint for educational purposes (this may not work reliably).
    try{
      setStatus('Attempting community face-swap (may require server)...'); setProgress(30);
      // Demo fallback: we convert both images to base64 and show a combined preview as a naive "swap" (placeholder)
      const srcB = await fileToBase64(src);
      const tgtB = await fileToBase64(tgt);
      // Placeholder: show target image (real face-swap requires model)
      showResultImage(tgtB);
      setStatus('Placeholder result shown — for real face-swap use a server proxy to Replicate/HuggingFace'); setProgress(100);
    }catch(e){ setStatus('Failed: '+e.message); }
  }

  async function handleCartoon(){
    const f = document.getElementById('cartoonFile').files && document.getElementById('cartoonFile').files[0];
    const consent = document.getElementById('consentCartoon').checked;
    if(!f){ alert('براہ مہربانی تصویر اپ لوڈ کریں۔'); return; }
    if(!consent){ alert('Consent درکار ہے۔'); return; }

    resultBox.innerHTML=''; setStatus('Preparing...'); setProgress(12);
    // Send to Stable Horde (example). Stable Horde uses a job-based API.
    // Docs: https://stablehorde.net/docs (replace with your own check)

    try{
      setStatus('Uploading to Stable Horde...'); setProgress(28);
      const imageData = await fileToBase64(f); // data:image/...;base64,...
      // Compose payload
      const payload = {
        "worker": "stable_diffusion", // example
        "params": {
          "prompt": "a high quality cartoon avatar of the person in the uploaded image, clean background, detailed, 4k",
          "init_image": imageData,
          "steps": 20,
          "cfg_scale": 7.0
        }
      };

      const res = await fetch('https://stablehorde.net/api/v2/generate/async',{
        method:'POST',
        headers: {
          'Api-Key': STABLE_HORDE_API_KEY,
          'Content-Type':'application/json'
        },
        body: JSON.stringify(payload)
      });

      if(!res.ok){ const txt = await res.text(); throw new Error('Stable Horde error: '+txt); }
      const job = await res.json();
      setStatus('Job queued. Polling for result...'); setProgress(48);
      // Polling — job.id assumed
      const jobId = job.id || job.job_id || job.breed_id || job.request_id;
      if(!jobId){ setStatus('No job id returned — check response in console.'); console.log(job); return; }

      // Poll (naive)
      let finished=false; let attempts=0;
      while(!finished && attempts<30){
        attempts++; setProgress(48 + attempts*1.6);
        await sleep(2500);
        const poll = await fetch('https://stablehorde.net/api/v2/generate/status/'+jobId);
        if(!poll.ok) { console.log('poll err', await poll.text()); continue; }
        const p = await poll.json();
        if(p.done && p.generations && p.generations.length){
          const gen = p.generations[0];
          const img = gen.img || gen.base64 || gen.url;
          showResultImage(img);
          setStatus('Cartoon ready'); setProgress(100);
          finished=true; break;
        }
      }
      if(!finished) setStatus('Timed out waiting for Stable Horde result — check job on dashboard.');
    }catch(err){ console.error(err); setStatus('Error: '+err.message); }
  }

  async function handleTxt2Img(){
    const prompt = document.getElementById('txtPrompt').value.trim();
    const consent = document.getElementById('consentTxt').checked;
    if(!prompt){ alert('Prompt لکھیں۔'); return; }
    if(!consent){ alert('Consent درکار ہے۔'); return; }

    resultBox.innerHTML=''; setStatus('Sending prompt to Stable Horde...'); setProgress(18);
    try{
      const payload = { worker: 'stable_diffusion', params:{ prompt, steps:20, cfg_scale:7 }};
      const res = await fetch('https://stablehorde.net/api/v2/generate/async',{
        method:'POST', headers:{ 'Api-Key': STABLE_HORDE_API_KEY, 'Content-Type':'application/json' }, body: JSON.stringify(payload)
      });
      if(!res.ok) throw new Error('Stable Horde returned non-200');
      const job = await res.json(); const jobId = job.id || job.request_id;
      setStatus('Job queued. Polling...'); setProgress(45);
      let done=false; let t=0;
      while(!done && t<30){ t++; await sleep(2500); setProgress(45 + t*1.6);
        const poll = await fetch('https://stablehorde.net/api/v2/generate/status/'+jobId);
        if(!poll.ok) continue;
        const p = await poll.json();
        if(p.done && p.generations && p.generations.length){ showResultImage(p.generations[0].img || p.generations[0].base64); setStatus('Image ready'); setProgress(100); done=true; }
      }
      if(!done) setStatus('Timeout waiting for result.');
    }catch(e){ setStatus('Error: '+e.message); }
  }

  function showResultImage(imgDataOrUrl){
    resultBox.innerHTML='';
    if(!imgDataOrUrl){ resultBox.innerHTML = '<div class="danger">کوئی تصویر نہیں ملی — console دیکھیں</div>'; return; }
    // if base64 without data: prefix, try to detect
    if(typeof imgDataOrUrl === 'string' && imgDataOrUrl.startsWith('/')){
      // probably path
    }
    const img = document.createElement('img'); img.className='preview';
    if(imgDataOrUrl.startsWith('data:') || imgDataOrUrl.startsWith('http')){
      img.src = imgDataOrUrl;
    } else if(imgDataOrUrl.startsWith('/')){
      img.src = imgDataOrUrl;
    } else {
      // assume base64 without prefix
      img.src = 'data:image/png;base64,' + imgDataOrUrl;
    }
    resultBox.appendChild(img);

    // add download
    const dl = document.createElement('a'); dl.innerText='Download Image'; dl.href = img.src; dl.download='result.png'; dl.style.display='inline-block'; dl.style.marginTop='8px'; dl.style.marginRight='8px'; dl.className='';
    resultBox.appendChild(dl);
  }

  // helpers
  function fileToBase64(file){
    return new Promise((res,rej)=>{
      const r = new FileReader(); r.onload = ()=>res(r.result); r.onerror = e=>rej(e); r.readAsDataURL(file);
    });
  }
  function sleep(ms){ return new Promise(r=>setTimeout(r,ms)); }

  // lightweight: show small startup tip
  setTimeout(()=>{
    setStatus('Ready — select mode and try.'); setProgress(0);
  },200);
  </script></body>
</html>
