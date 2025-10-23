
<html lang="vi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Phiếu học tập tự luận - Toán 11 Chương 1</title>
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
