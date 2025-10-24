
<html lang="vi">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Phiếu học tập Chương 1 - Toán 11 (Kết nối tri thức) - Trắc nghiệm</title>
  <style>
    :root{--bg:#f7f9fc;--card:#ffffff;--accent:#0ea5a4;--muted:#6b7280}
    body{font-family:Inter, system-ui, -apple-system, 'Segoe UI', Roboto, 'Helvetica Neue', Arial; background:var(--bg); color:#0f172a; margin:0; padding:20px}
    .wrap{max-width:980px; margin:0 auto}
    header{display:flex;align-items:center;gap:12px;margin-bottom:18px}
    header h1{font-size:20px;margin:0}
    .card{background:var(--card);border-radius:12px;box-shadow:0 6px 18px rgba(2,6,23,0.06);padding:18px;margin-bottom:14px}
    .lesson-head{display:flex;justify-content:space-between;align-items:center;margin-bottom:12px}
    .q{margin:10px 0;padding:12px;border-radius:8px;border:1px solid #eef2ff;background:linear-gradient(180deg,#fff,#fbfdff)}
    .options{display:flex;flex-direction:column;gap:6px;margin-top:8px}
    label.option{display:flex;align-items:center;gap:10px;padding:8px;border-radius:8px;border:1px solid transparent}
    label.option input{transform:scale(1.1)}
    label.option.correct{border-color:rgba(34,197,94,0.12);background:#ecfdf5}
    label.option.wrong{border-color:rgba(249,115,22,0.12);background:#fff7ed}
    .controls{display:flex;gap:8px;flex-wrap:wrap}
    button{background:var(--accent);color:white;border:none;padding:8px 12px;border-radius:8px;cursor:pointer}
    button.secondary{background:#e6eef0;color:#0f172a}
    .result{margin-top:12px;font-weight:600}
    .meta{font-size:13px;color:var(--muted)}
    .small{font-size:13px;color:var(--muted);margin-top:8px}
    footer{margin-top:18px;text-align:center;color:var(--muted);font-size:13px}
    @media (max-width:600px){body{padding:12px}}
  </style>
</head>
<body>
  <div class="wrap">
    <header>
      <h1>Phiếu học tập — Chương 1: Lượng giác (Toán 11)</h1>
  
    </header>

    <!-- Lessons container -->
    <div id="lessons"></div>

    <footer class="small">Phiếu này gồm 5 bài, mỗi bài 5 câu trắc nghiệm. Nhấn "Kiểm tra" để chấm, "Hiện đáp án" để xem đáp án đúng.</footer>
  </div>

  <script>
  // Dữ liệu câu hỏi cho 5 bài (mỗi bài 5 câu)
  const data = [
    {
      title: 'Bài 1: Hàm số lượng giác',
      qs: [
        {q:'Hàm số nào sau đây có chu kỳ nhỏ nhất là π?', opts:['y = sin x','y = cos x','y = tan x','y = sin 2x'], a:2},
        {q:'Hàm số nào là hàm chẵn?', opts:['y = sin x','y = cos x','y = tan x','y = cot x'], a:1},
        {q:'Tập xác định của hàm y = tan x là:', opts:['R','R \ {kπ}','R \ {π/2 + kπ}','R \ {2kπ}'], a:2},
        {q:'Tập giá trị của y = sin x là:', opts:['[0;1]','(−∞;∞)','[−1;1]','(−1;1)'], a:2},
        {q:'Hàm y = cos x có tính chất nào sau đây?', opts:['lẻ','chẵn','không xác định','đơn điệu trên R'], a:1}
      ]
    },
    {
      title: 'Bài 2: Công thức lượng giác',
      qs: [
        {q:'Công thức nào đúng về sin(a+b)?', opts:['sin a + sin b','sin a cos b + cos a sin b','cos a cos b − sin a sin b','tan a + tan b'], a:1},
        {q:'cos(a−b) = ?', opts:['cos a cos b − sin a sin b','cos a cos b + sin a sin b','sin a sin b − cos a cos b','tan a tan b'], a:0},
        {q:'sin 2a = ?', opts:['2 sin a cos a','sin^2 a + cos^2 a','2 cos^2 a','cos^2 a − sin^2 a'], a:0},
        {q:'Tan(a+b) bằng ?', opts:['(tan a + tan b)/(1 − tan a tan b)','tan a + tan b','(tan a − tan b)/(1 + tan a tan b)','(tan a + tan b)/(1 + tan a tan b)'], a:0},
        {q:'Đẳng thức nào đúng?', opts:['sin^2 x − cos^2 x = 1','sin^2 x + cos^2 x = 1','tan x · cot x = 2','tan^2 x + 1 = cos^2 x'], a:1}
      ]
    },
    {
      title: 'Bài 3: Phương trình lượng giác',
      qs: [
        {q:'Phương trình sin x = 1 có nghiệm nào sau đây?', opts:['x = 0 + 2kπ','x = π/2 + 2kπ','x = π + 2kπ','x = π/4 + kπ'], a:1},
        {q:'Nghiệm nguyên thủy (thông dụng) của cos x = 0 là:', opts:['x = π/2 + kπ','x = kπ','x = π/4 + kπ','x = π + 2kπ'], a:0},
        {q:'Phương trình tan x = 1 có nghiệm nào sau đây?', opts:['x = π/4 + kπ','x = π/2 + kπ','x = π/6 + kπ','x = kπ'], a:0},
        {q:'Phương trình 2 sin x = 0 tương đương với:', opts:['sin x = 2','sin x = 0','sin x = 1/2','sin x = −1'], a:1},
        {q:'Số nghiệm của sin x = 2 trong R là:', opts:['vô hạn','2','1','0'], a:3}
      ]
    },
    {
      title: 'Bài 4: Giá trị lượng giác của các góc đặc biệt',
      qs: [
        {q:'sin(π/6) = ?', opts:['1/2','√2/2','√3/2','0'], a:0},
        {q:'cos(π/3) = ?', opts:['1/2','√2/2','√3/2','−1/2'], a:0},
        {q:'tan(π/4) = ?', opts:['0','1','√3','−1'], a:1},
        {q:'sin(π/3) = ?', opts:['1/2','√2/2','√3/2','−√3/2'], a:2},
        {q:'cos(π/2) = ?', opts:['1','0','−1','√2/2'], a:1}
      ]
    },
    {
      title: 'Bài 5: Ứng dụng lượng giác trong thực tiễn',
      qs: [
        {q:'Một mặt nghiêng tạo với mặt ngang góc 30°. Nếu đoạn dọc cao 5 m, thì cạnh huyền (độ dài) là ?', opts:['10 m','5√3 m','5 m','(5/√3) m'], a:1},
        {q:'Trong tam giác vuông, nếu góc nhọn A = 30° và cạnh huyền = 10, thì sin A bằng?', opts:['1/2','√3/2','√3/3','1'], a:0},
        {q:'Biểu thức mô tả dao động điều hòa: x(t) = A sin(ωt + φ). Ở đây A là:', opts:['tần số','pha ban đầu','biên độ','góc quay'], a:2},
        {q:'Góc phương vị của mặt trời có thể mô tả bằng hàm sin/cos vì:', opts:['là hàm tuyến tính','là chu kỳ theo thời gian','không đổi theo ngày','luôn dương'], a:1},
        {q:'Đơn vị đo góc thường dùng trong lượng giác là:', opts:['radian và độ','mét và kilômét','giây và phút','lux và lumen'], a:0}
      ]
    }
  ];

  // render lessons
  const lessonsEl = document.getElementById('lessons');
  data.forEach((lesson, li)=>{
    const card = document.createElement('section');
    card.className = 'card';
    card.innerHTML = `
      <div class="lesson-head">
        <strong>${lesson.title}</strong>
        <div class="controls">
          <button class="check">Kiểm tra</button>
          <button class="show secondary">Hiện đáp án</button>
          <button class="reset secondary">Làm lại</button>
        </div>
      </div>
      <div class="small">Mỗi bài ${lesson.qs.length} câu. Chọn đáp án rồi nhấn "Kiểm tra".</div>
      <div class="questions"></div>
      <div class="result" aria-live="polite"></div>
    `;

    lessonsEl.appendChild(card);

    const qsEl = card.querySelector('.questions');
    lesson.qs.forEach((q, qi)=>{
      const qdiv = document.createElement('div');
      qdiv.className = 'q';
      qdiv.dataset.answer = q.a;
      qdiv.innerHTML = `
        <div><strong>Câu ${qi+1}.</strong> ${q.q}</div>
        <div class="options">${q.opts.map((opt, oi)=>{
          const id = `l${li}q${qi}o${oi}`;
          return `<label class="option" for="${id}"><input type="radio" name="l${li}q${qi}" id="${id}" value="${oi}"> <span>${String.fromCharCode(65+oi)}. ${opt}</span></label>`;
        }).join('')}</div>
      `;
      qsEl.appendChild(qdiv);
    });

    // buttons behavior
    const btnCheck = card.querySelector('.check');
    const btnShow = card.querySelector('.show');
    const btnReset = card.querySelector('.reset');
    const resultEl = card.querySelector('.result');

    btnCheck.addEventListener('click', ()=>{
      let correct = 0; let total = lesson.qs.length;
      const qblocks = card.querySelectorAll('.q');
      qblocks.forEach((qb, idx)=>{
        const trueAns = Number(qb.dataset.answer);
        const chosen = qb.querySelector('input[type=radio]:checked');
        // clear classes
        qb.querySelectorAll('.option').forEach(o=>o.classList.remove('correct','wrong'));
        if(chosen){
          const chosenVal = Number(chosen.value);
          if(chosenVal === trueAns){
            correct++;
            qb.querySelectorAll('.option')[chosenVal].classList.add('correct');
          } else {
            qb.querySelectorAll('.option')[chosenVal].classList.add('wrong');
            qb.querySelectorAll('.option')[trueAns].classList.add('correct');
          }
        } else {
          // no answer: mark correct option
          qb.querySelectorAll('.option')[trueAns].classList.add('correct');
        }
      });
      resultEl.textContent = `Điểm: ${correct} / ${total} — ${Math.round(correct/total*100)}%`;
    });

    btnShow.addEventListener('click', ()=>{
      const qblocks = card.querySelectorAll('.q');
      qblocks.forEach(qb=>{
        const trueAns = Number(qb.dataset.answer);
        qb.querySelectorAll('.option').forEach((o, i)=>{
          o.classList.remove('wrong');
          if(i === trueAns) o.classList.add('correct'); else o.classList.remove('correct');
        });
      });
      // show score based on selected answers (but do not mark wrongs)
      let correct = 0, total = lesson.qs.length;
      qblocks.forEach(qb=>{
        const chosen = qb.querySelector('input[type=radio]:checked');
        if(chosen && Number(chosen.value)===Number(qb.dataset.answer)) correct++;
      });
      resultEl.textContent = `Đã hiển thị đáp án. Điểm hiện tại (chọn sẵn): ${correct}/${total}`;
    });

    btnReset.addEventListener('click', ()=>{
      card.querySelectorAll('input[type=radio]').forEach(r=>r.checked=false);
      card.querySelectorAll('.option').forEach(o=>{o.classList.remove('correct','wrong')});
      resultEl.textContent = '';
    });
  });

  // Optional: keyboard accessibility - Enter to check focused lesson
  document.addEventListener('keydown', (e)=>{
    if(e.key === 'Enter'){
      const active = document.activeElement;
      if(active && active.closest && active.closest('.card')){
        const checkBtn = active.closest('.card').querySelector('.check');
        if(checkBtn) checkBtn.click();
      }
    }
  });
  </script>
</body>
</html>
