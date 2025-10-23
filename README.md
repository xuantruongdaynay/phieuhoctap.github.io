
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
      <div class="meta">Dạng trắc nghiệm A–B–C–D • Tự kiểm tra ngay</div>
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



<html lang="vi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>
body {
  font-family: "Segoe UI", Arial, sans-serif;
  background-color: #f9f9f9;
  color: #222;
  margin: 20px;
  line-height: 1.6;
}
h1, h2, h3 { text-align: center; color: #004aad; }
section {
  background: #fff;
  border-radius: 12px;
  box-shadow: 0 2px 6px rgba(0,0,0,0.1);
  padding: 20px;
  margin-bottom: 30px;
}
.question { margin-bottom: 12px; }
label { margin-right: 10px; }
button {
  padding: 8px 16px;
  border: none;
  border-radius: 6px;
  background-color: #0078ff;
  color: white;
  cursor: pointer;
  margin: 5px 2px;
}
button:hover { background-color: #005ecc; }
.result {
  font-weight: bold;
  margin-top: 10px;
}
.correct { color: green; }
.wrong { color: red; }
footer {
  text-align: center;
  margin-top: 40px;
  font-size: 0.9em;
  color: #555;
}
</style>
</head>
<body>


<script>
const chapters = [
{
title: "Bài 1: Hàm số lượng giác",
questions: [
{q:"Hàm sinx và cosx đều có chu kỳ là 2π.", a:true},
{q:"Giá trị lớn nhất của cosx là 0.", a:false},
{q:"Hàm tanx xác định với mọi giá trị của x.", a:false},
{q:"sin(−x) = −sinx là tính chất hàm lẻ.", a:true},
{q:"cos(−x) = cosx là tính chất hàm chẵn.", a:true},
{q:"Hàm sinx nhận trục tung làm trục đối xứng.", a:false},
{q:"Hàm cosx nhận trục tung làm trục đối xứng.", a:true},
{q:"Tập giá trị của sinx là [−1;1].", a:true}
]
},
{
title: "Bài 2: Đồ thị hàm số lượng giác",
questions: [
{q:"Đồ thị y = sinx cắt trục hoành tại x = kπ.", a:true},
{q:"Đồ thị y = cosx đạt giá trị lớn nhất tại x = π/2.", a:false},
{q:"Đồ thị y = sinx và y = cosx có dạng sóng tuần hoàn.", a:true},
{q:"Khi a > 0, biên độ của y = a.sinx là a.", a:true},
{q:"Đồ thị y = sin(x + π/2) trùng với y = cosx.", a:true},
{q:"Tăng tần số trong y = sin(bx) làm đồ thị dãn theo trục hoành.", a:false},
{q:"Đồ thị y = 2cosx có biên độ 2.", a:true},
{q:"Đồ thị y = sinx đối xứng với y = −sinx qua trục hoành.", a:true}
]
},
{
title: "Bài 3: Phương trình lượng giác cơ bản",
questions: [
{q:"Phương trình sinx = 0 có nghiệm x = kπ.", a:true},
{q:"Phương trình cosx = 1 có nghiệm x = kπ.", a:true},
{q:"Phương trình cosx = 0 có nghiệm x = π/2 + kπ.", a:true},
{q:"Phương trình tanx = 1 có nghiệm x = π/4 + kπ.", a:true},
{q:"Phương trình sinx = 2 có nghiệm trong R.", a:false},
{q:"Phương trình cosx = −1 có nghiệm x = π + k2π.", a:false},
{q:"Phương trình cotx = 1 có nghiệm x = π/4 + kπ.", a:true},
{q:"Nếu sinx = cosx thì x = π/4 + kπ.", a:true}
]
},
{
title: "Bài 4: Công thức lượng giác",
questions: [
{q:"Công thức sin(2x) = 2sinxcosx.", a:true},
{q:"Công thức cos(2x) = cos²x + sin²x.", a:false},
{q:"Công thức sin(a + b) = sinacosb + cosasinb.", a:true},
{q:"Công thức cos(a − b) = cosacosb + sinasinb.", a:true},
{q:"Công thức tan(a + b) = (tana + tanb) / (1 − tanatanb).", a:true},
{q:"Công thức sin²x + cos²x = 1.", a:true},
{q:"Công thức 1 + tan²x = cos²x.", a:false},
{q:"Công thức cotx = 1 / tanx.", a:true}
]
},
{
title: "Bài 5: Ứng dụng lượng giác",
questions: [
{q:"Trong tam giác vuông, sinA = đối / huyền.", a:true},
{q:"Trong tam giác vuông, cosA = đối / kề.", a:false},
{q:"tanA = đối / kề và cotA = kề / đối.", a:true},
{q:"Nếu sinA = 3/5 thì cosA = 4/5 (với A nhọn).", a:true},
{q:"Công thức tính độ cao h = a.sinα.", a:true},
{q:"Công thức tính khoảng cách d = a.cosα.", a:true},
{q:"Nếu góc tăng thì sin giảm.", a:false},
{q:"sin²A + cos²A luôn bằng 1.", a:true}
]
}
];

// ===== Sinh giao diện =====
chapters.forEach((ch, ci)=>{
  const sec = document.createElement("section");
  sec.innerHTML = `<h3>${ch.title}</h3>`;
  ch.questions.forEach((ques, qi)=>{
    sec.innerHTML += `
      <div class="question">
        <b>Câu ${qi+1}:</b> ${ques.q}<br>
        <label><input type="radio" name="q${ci}_${qi}" value="true"> Đúng</label>
        <label><input type="radio" name="q${ci}_${qi}" value="false"> Sai</label>
      </div>`;
  });
  sec.innerHTML += `
    <button onclick="checkAnswers(${ci})">Kiểm tra</button>
    <button onclick="showAnswers(${ci})">Hiện đáp án</button>
    <button onclick="resetSection(${ci})">Làm lại</button>
    <div class="result" id="result${ci}"></div>`;
  document.body.appendChild(sec);
});

// ===== Xử lý =====
function checkAnswers(ci){
  const ch = chapters[ci];
  let correct = 0;
  ch.questions.forEach((ques, qi)=>{
    const radios = document.getElementsByName(`q${ci}_${qi}`);
    let chosen = null;
    radios.forEach(r=>{ if(r.checked) chosen = r.value==="true"; });
    if(chosen===ques.a){ correct++; }
  });
  document.getElementById(`result${ci}`).innerHTML =
    `✅ Bạn làm đúng ${correct}/${ch.questions.length} câu.`;
}

function showAnswers(ci){
  const ch = chapters[ci];
  ch.questions.forEach((ques, qi)=>{
    const radios = document.getElementsByName(`q${ci}_${qi}`);
    radios.forEach(r=>{
      if(r.value==="true" && ques.a===true) r.parentElement.style.color="green";
      else if(r.value==="false" && ques.a===false) r.parentElement.style.color="green";
      else r.parentElement.style.color="#999";
    });
  });
  document.getElementById(`result${ci}`).innerHTML = "📘 Đáp án đúng đã được tô xanh.";
}

function resetSection(ci){
  const ch = chapters[ci];
  ch.questions.forEach((ques, qi)=>{
    const radios = document.getElementsByName(`q${ci}_${qi}`);
    radios.forEach(r=>{
      r.checked = false;
      r.parentElement.style.color="black";
    });
  });
  document.getElementById(`result${ci}`).innerHTML = "";
}
</script>

<footer>
  © 2025 - Phiếu học tập Toán 11 | Dạng Đúng / Sai | Kết nối tri thức
</footer>
</body>
</html>



<html lang="vi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>
body {
  font-family: "Segoe UI", Arial, sans-serif;
  background-color: #f9f9f9;
  color: #222;
  margin: 20px;
  line-height: 1.6;
}
h1, h2, h3 {
  text-align: center;
  color: #004aad;
}
section {
  background: #fff;
  border-radius: 12px;
  box-shadow: 0 2px 6px rgba(0,0,0,0.1);
  padding: 20px;
  margin-bottom: 30px;
}
.question {
  margin-bottom: 10px;
}
input[type="text"] {
  width: 80%;
  padding: 6px;
  margin-top: 5px;
  border: 1px solid #ccc;
  border-radius: 6px;
}
button {
  padding: 8px 16px;
  border: none;
  border-radius: 6px;
  background-color: #0078ff;
  color: white;
  cursor: pointer;
  margin: 5px 2px;
}
button:hover { background-color: #005ecc; }
.result {
  font-weight: bold;
  color: #006600;
  margin-top: 10px;
}
.wrong { color: red; }
footer {
  text-align: center;
  margin-top: 40px;
  font-size: 0.9em;
  color: #555;
}
</style>
</head>
<body>

<script>
// ===== DỮ LIỆU CÂU HỎI =====
// Mỗi bài có 3 mức độ
const chapters = [
{
  title: "Bài 1: Hàm số lượng giác",
  questions: [
    {q:"Giá trị lớn nhất của sinx là bao nhiêu?", a:"1"},
    {q:"Giá trị nhỏ nhất của cosx là bao nhiêu?", a:"-1"},
    {q:"Hàm sinx có chu kỳ là bao nhiêu?", a:"2π"},
    {q:"Điều kiện xác định của tanx là x ≠ ?", a:"π/2 + kπ"},
    {q:"Hàm sinx là hàm chẵn hay hàm lẻ?", a:"lẻ"},
  ]
},
{
  title: "Bài 2: Đồ thị hàm số lượng giác",
  questions: [
    {q:"Đồ thị y = sinx đi qua gốc tọa độ hay không?", a:"có"},
    {q:"Biên độ của y = a.sinx là bao nhiêu?", a:"|a|"},
    {q:"Chu kỳ của y = cos(2x) là?", a:"π"},
    {q:"Giá trị lớn nhất của y = 3cosx là?", a:"3"},
    {q:"Giá trị nhỏ nhất của y = 2sinx là?", a:"-2"},
  ]
},
{
  title: "Bài 3: Phương trình lượng giác cơ bản",
  questions: [
    {q:"Phương trình sinx = 0 có nghiệm x = ?", a:"kπ"},
    {q:"Phương trình cosx = 0 có nghiệm x = ?", a:"π/2 + kπ"},
    {q:"Phương trình tanx = 0 có nghiệm x = ?", a:"kπ"},
    {q:"Phương trình cotx = 0 có nghiệm x = ?", a:"π/2 + kπ"},
  ]
},
{
  title: "Bài 4: Công thức lượng giác",
  questions: [
    {q:"Công thức sin(2x) bằng?", a:"2sinxcosx"},
    {q:"Công thức cos(2x) bằng?", a:"cos²x - sin²x"},
    {q:"Công thức tan(2x) bằng?", a:"2tanx / (1 - tan²x)"},
    {q:"Công thức sin(a ± b) bằng?", a:"sinacosb ± cosasinb"},
    {q:"Công thức cos(a ± b) bằng?", a:"cosacosb ∓ sinasinb"},
  ]
},
{
  title: "Bài 5: Ứng dụng lượng giác",
  questions: [
    {q:"Trong tam giác vuông, sinA bằng công thức nào?", a:"đối / huyền"},
    {q:"cosA bằng công thức nào?", a:"kề / huyền"},
    {q:"tanA bằng công thức nào?", a:"đối / kề"},
    {q:"cotA bằng công thức nào?", a:"kề / đối"},
    {q:"Nếu sinA = 3/5 thì cosA = ?", a:"4/5"},
  ]
}
];

// ===== SINH GIAO DIỆN =====
chapters.forEach((ch, ci)=>{
  const sec = document.createElement("section");
  sec.innerHTML = `<h3>${ch.title}</h3>`;
  ch.questions.forEach((ques, qi)=>{
    sec.innerHTML += `
      <div class="question">
        <b>Câu ${qi+1}:</b> ${ques.q}<br>
        <input type="text" id="q${ci}_${qi}" placeholder="Nhập đáp án...">
      </div>`;
  });
  sec.innerHTML += `
    <button onclick="checkAnswers(${ci})">Kiểm tra</button>
    <button onclick="showAnswers(${ci})">Hiện đáp án</button>
    <button onclick="resetSection(${ci})">Làm lại</button>
    <div class="result" id="result${ci}"></div>`;
  document.body.appendChild(sec);
});

// ===== HÀM XỬ LÝ =====
function normalize(str){ return str.toLowerCase().replace(/\s+/g,'').replace(/π/g,'pi'); }

function checkAnswers(ci){
  const ch = chapters[ci];
  let correct = 0;
  ch.questions.forEach((ques, qi)=>{
    const inp = document.getElementById(`q${ci}_${qi}`);
    if(!inp) return;
    if(normalize(inp.value)==normalize(ques.a)){
      inp.style.borderColor="green";
      correct++;
    } else {
      inp.style.borderColor="red";
    }
  });
  document.getElementById(`result${ci}`).innerHTML = 
    `✅ Bạn làm đúng ${correct}/${ch.questions.length} câu.`;
}

function showAnswers(ci){
  const ch = chapters[ci];
  ch.questions.forEach((ques, qi)=>{
    const inp = document.getElementById(`q${ci}_${qi}`);
    inp.value = ques.a;
    inp.style.borderColor="#0078ff";
  });
  document.getElementById(`result${ci}`).innerHTML = "📘 Đây là đáp án đúng.";
}

function resetSection(ci){
  const ch = chapters[ci];
  ch.questions.forEach((ques, qi)=>{
    const inp = document.getElementById(`q${ci}_${qi}`);
    inp.value = "";
    inp.style.borderColor="#ccc";
  });
  document.getElementById(`result${ci}`).innerHTML = "";
}
</script>

<footer>
  © 2025 - Phiếu học tập Toán 11 | Kết nối tri thức
</footer>
</body>
</html>



<html lang="vi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>
body {
  font-family: "Segoe UI", sans-serif;
  background-color: #f8f9fa;
  color: #222;
  margin: 0;
  padding: 0;
}
.container {
  max-width: 900px;
  margin: 30px auto;
  background: #fff;
  border-radius: 15px;
  box-shadow: 0 2px 8px rgba(0,0,0,0.1);
  padding: 20px 30px;
}
h1 {
  text-align: center;
  color: #0d6efd;
}
h2 {
  color: #0d6efd;
  margin-top: 30px;
}
textarea {
  width: 100%;
  min-height: 80px;
  margin: 8px 0 15px;
  padding: 10px;
  border-radius: 10px;
  border: 1px solid #ccc;
  font-size: 15px;
  resize: vertical;
}
button {
  background-color: #0d6efd;
  color: white;
  border: none;
  padding: 8px 18px;
  border-radius: 8px;
  cursor: pointer;
  font-size: 15px;
}
button:hover {
  background-color: #0b5ed7;
}
hr {
  margin: 20px 0;
  border: none;
  border-top: 2px solid #eee;
}
</style>
</head>
<body>
<div class="container">
  <h1>PHIẾU HỌC TẬP TƯƠNG TÁC<br>TOÁN 11 – CHƯƠNG 1 (KẾT NỐI TRI THỨC)</h1>
  <p style="text-align:center; color:#555;">Dạng: Tự luận nhiều dòng – không hiển thị đáp án</p>

  <!-- Bài 1 -->
  <h2>Bài 1: Hàm số lượng giác</h2>
  <p>1. Trình bày định nghĩa hàm số sin, cos, tan, cot.</p>
  <textarea></textarea>
  <p>2. Nêu tập xác định của các hàm số lượng giác.</p>
  <textarea></textarea>
  <p>3. Chứng minh sin²x + cos²x = 1.</p>
  <textarea></textarea>
  <p>4. Tính giá trị sin(π/6), cos(π/3), tan(π/4).</p>
  <textarea></textarea>
  <p>5. Cho biết giá trị lượng giác của các góc đặc biệt.</p>
  <textarea></textarea>
  <button onclick="resetSection(1)">Làm lại Bài 1</button>
  <hr>

  <!-- Bài 2 -->
  <h2>Bài 2: Đồ thị hàm số lượng giác</h2>
  <p>1. Mô tả hình dạng đồ thị của hàm số y = sinx.</p>
  <textarea></textarea>
  <p>2. So sánh đồ thị của y = sinx và y = cosx.</p>
  <textarea></textarea>
  <p>3. Giải thích ý nghĩa của biên độ trong đồ thị hàm số lượng giác.</p>
  <textarea></textarea>
  <p>4. Nêu chu kỳ của các hàm số lượng giác.</p>
  <textarea></textarea>
  <p>5. Vẽ phác đồ thị y = 2sinx và y = sin(2x).</p>
  <textarea></textarea>
  <button onclick="resetSection(2)">Làm lại Bài 2</button>
  <hr>

  <!-- Bài 3 -->
  <h2>Bài 3: Phương trình lượng giác cơ bản</h2>
  <p>1. Giải phương trình sinx = 0.</p>
  <textarea></textarea>
  <p>2. Giải phương trình cosx = 1/2.</p>
  <textarea></textarea>
  <p>3. Giải phương trình tanx = √3.</p>
  <textarea></textarea>
  <p>4. Giải phương trình cotx = -1.</p>
  <textarea></textarea>
  <p>5. Nêu nhận xét về nghiệm của các phương trình lượng giác cơ bản.</p>
  <textarea></textarea>
  <button onclick="resetSection(3)">Làm lại Bài 3</button>
  <hr>

  <!-- Bài 4 -->
  <h2>Bài 4: Công thức lượng giác</h2>
  <p>1. Phát biểu công thức cộng của sin(a ± b), cos(a ± b).</p>
  <textarea></textarea>
  <p>2. Chứng minh công thức nhân đôi của cos2x.</p>
  <textarea></textarea>
  <p>3. Viết công thức biến đổi tích thành tổng.</p>
  <textarea></textarea>
  <p>4. Nêu công thức hạ bậc của sin²x và cos²x.</p>
  <textarea></textarea>
  <p>5. Ứng dụng công thức cộng để tính sin75°.</p>
  <textarea></textarea>
  <button onclick="resetSection(4)">Làm lại Bài 4</button>
  <hr>

  <!-- Bài 5 -->
  <h2>Bài 5: Ứng dụng lượng giác</h2>
  <p>1. Giải thích cách sử dụng lượng giác để đo độ cao một tòa nhà.</p>
  <textarea></textarea>
  <p>2. Viết ví dụ thực tế có thể áp dụng công thức lượng giác.</p>
  <textarea></textarea>
  <p>3. Tính khoảng cách giữa hai điểm khi biết góc và cạnh.</p>
  <textarea></textarea>
  <p>4. Trình bày cách xác định độ dốc của một con đường bằng lượng giác.</p>
  <textarea></textarea>
  <p>5. Nêu ý nghĩa của các giá trị lượng giác trong đời sống thực tế.</p>
  <textarea></textarea>
  <button onclick="resetSection(5)">Làm lại Bài 5</button>
</div>

<script>
function resetSection(num) {
  const container = document.querySelectorAll('h2')[num-1].nextElementSibling;
  let next = container;
  while (next && next.tagName !== 'H2' && next.tagName !== 'HR') {
    if (next.tagName === 'TEXTAREA') next.value = '';
    next = next.nextElementSibling;
  }
  alert("Đã xóa toàn bộ nội dung của Bài " + num);
}
</script>
</body>
</html>


