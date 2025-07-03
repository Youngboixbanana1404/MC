<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>METEV Configurator Mockup</title>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;700&display=swap" rel="stylesheet">
  <style>
    body {
      margin: 0;
      font-family: 'Poppins', sans-serif;
      background-color: #fff;
      color: #000;
    }
    header {
      background-color: #d7f010;
      color: #161616;
      padding: 20px;
      text-align: center;
      font-size: 2em;
      font-weight: bold;
    }
    .main {
      display: flex;
      flex-direction: row;
      height: calc(100vh - 80px);
    }
    .preview {
      flex: 2;
      background-color: #fff;
      display: flex;
      align-items: center;
      justify-content: center;
      box-shadow: inset -15px 0 20px rgba(0, 0, 0, 0.15);
    }
    .preview img {
      width: 100%;
      max-width: 900px;
      height: auto;
    }
    .config {
      flex: 1;
      background-color: #fff;
      padding: 30px;
      display: flex;
      flex-direction: column;
      gap: 20px;
      box-shadow: -10px 0 30px rgba(0, 0, 0, 0.15);
    }
    .section-title {
      font-weight: bold;
      font-size: 1.1em;
      margin-bottom: 8px;
    }
    .options {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 10px;
    }
    .color-option {
      width: 40px;
      height: 40px;
      border-radius: 4px;
      border: 2px solid transparent;
      cursor: pointer;
    }
    .pattern-option {
      width: 60px;
      height: 60px;
      border-radius: 6px;
      background-size: cover;
      background-position: center;
      cursor: pointer;
    }
    .info-box {
      background: #f4f4f4;
      padding: 20px;
      border-radius: 10px;
    }
    .price {
      font-size: 1.3em;
      font-weight: bold;
      margin-bottom: 10px;
    }
    .button {
      padding: 15px;
      background-color: #d7f010;
      color: #161616;
      border: none;
      font-weight: bold;
      font-size: 1em;
      cursor: pointer;
      border-radius: 5px;
    }
    .toggle-group {
      display: flex;
      gap: 12px;
    }
    .toggle-btn {
      flex: 1;
      padding: 12px;
      background-color: #f4f4f4;
      color: black;
      border: 2px solid #ccc;
      text-align: center;
      cursor: pointer;
      border-radius: 30px;
      font-weight: 500;
    }
    .toggle-btn.active {
      background-color: #d7f010;
      color: #000;
      border-color: #d7f010;
    }
    .modal-overlay {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0,0,0,0.8);
      display: flex;
      align-items: center;
      justify-content: center;
      z-index: 1000;
    }
    .modal {
      background: white;
      padding: 30px;
      text-align: center;
      border-radius: 10px;
      color: black;
    }
    .modal h2 {
      font-size: 1.2em;
      color: #7fc14e;
      font-weight: bold;
    }
    .modal input[type="text"] {
      margin-top: 15px;
      padding: 10px;
      width: 80%;
      max-width: 300px;
      border: 1px solid #ccc;
      border-radius: 5px;
    }
    .arrow-btn {
      margin-top: 20px;
      background: #d7f010;
      border: none;
      padding: 10px 20px;
      font-weight: bold;
      cursor: pointer;
      border-radius: 5px;
    }
    .user-title {
      font-size: 1.1em;
      font-weight: bold;
      margin-bottom: 10px;
    }
  </style>
</head>
<body>
  <div class="modal-overlay" id="nameModal">
    <div class="modal">
      <h2>Welcome to METEV world!</h2>
      <p>What’s your name?</p>
      <input type="text" id="userNameInput" placeholder="Enter your name">
      <br>
      <button class="arrow-btn" onclick="submitName()">Start</button>
    </div>
  </div>

  <header>METEV – Build Your E-Bike</header>
  <div class="main">
    <div class="preview">
      <img id="bikeImage" src="https://i.postimg.cc/Fsn3x0J2/bike-orange-png.png" alt="Bike">
    </div>
    <div class="config">
      <div id="userMB1" class="user-title">YOUR MB1</div>

  <div class="section-title">Select a starting point</div>
      <div class="toggle-group">
        <div class="toggle-btn active" id="btnPreset" onclick="showSection('preset')">Start from Our Design Kit</div>
        <div class="toggle-btn" id="btnUpload" onclick="showSection('upload')">Start with Your Design</div>
      </div>

  <div id="presetSection">
        <p id="presetMsg" style="font-size: 0.9em; font-style: italic; color: #666;">You are customizing with basic pattern and green color.</p>
        <div class="section-title">Select Exterior Color</div>
        <div class="options" id="colorOptions"></div>

   <div class="section-title">Select Pattern</div>
        <div class="options">
          <div class="pattern-option" style="background-image: url('pattern1.png');"></div>
          <div class="pattern-option" style="background-image: url('pattern2.png');"></div>
        </div>
      </div>

  <div id="uploadSection" style="display:none;">
        <div class="section-title">Upload Your Design</div>
        <p style="font-size: 0.85em;">Accepted formats: PNG, AI, PDF (max 10MB)<br>
          Download template: <a href="#" style="color: #7fc14e; text-decoration: underline;">Click here</a></p>
        <input type="file">
        <textarea rows="3" placeholder="Any notes for our team..." style="width: 100%; margin-top: 10px;"></textarea>
        <input type="email" placeholder="Your email" style="width: 100%; margin-top: 10px;">
      </div>

  <div class="info-box">
        <div style="color: #111111; font-weight: bold; margin-bottom: 6px;">Promotion Price Until End 2025!</div>
        <div class="price">
          <span style="color: #ff0000; font-weight: bold; font-size: 1.3em;">19,000,000 VND</span>
          <span style="text-decoration: line-through; color: gray; font-size: 0.9em; margin-left: 10px;">25,000,000 VND</span>
          <span style="color: red; font-size: 0.9em; margin-left: 6px;">-24%</span>
        </div>
      </div>

  <button class="button">Add to cart</button>
  </div>
  </div>

  <script>
    const COLORS = [
      { code: '#ddf23c', name: 'green', image: 'https://i.postimg.cc/DZKqXFb0/bike-green-png.png' },
      { code: '#545454', name: 'grey', image: 'https://i.postimg.cc/J0rZpqxW/bike-grey-png.png' },
      { code: '#28bca9', name: 'mint', image: 'https://i.postimg.cc/NGD153GG/bike-mint-png.png' },
      { code: '#ff6300', name: 'orange', image: 'https://i.postimg.cc/Fsn3x0J2/bike-orange-png.png' },
      { code: '#bb99ff', name: 'purple', image: 'https://i.postimg.cc/7ZG7tb3b/bike-purple-png.png' },
      { code: '#e13800', name: 'red', image: 'https://i.postimg.cc/L8cPcRDD/bike-red-png.png' },
      { code: '#f4f6f8', name: 'white', image: 'https://i.postimg.cc/bNv1bmdx/bike-white-png.png' },
      { code: '#ffc845', name: 'yellow', image: 'https://i.postimg.cc/VNXt1TH8/bike-yellow-png.png' }
    ];

    function submitName() {
      const name = document.getElementById('userNameInput').value.trim();
      if (name) {
        document.getElementById('userMB1').textContent = `${name.toUpperCase()}'S MB1`;
        document.getElementById('nameModal').style.display = 'none';
      }
    }

    function showSection(type) {
      const presetSection = document.getElementById('presetSection');
      const uploadSection = document.getElementById('uploadSection');
      const btnPreset = document.getElementById('btnPreset');
      const btnUpload = document.getElementById('btnUpload');

      if (type === 'preset') {
        presetSection.style.display = 'block';
        uploadSection.style.display = 'none';
        btnPreset.classList.add('active');
        btnUpload.classList.remove('active');
      } else {
        presetSection.style.display = 'none';
        uploadSection.style.display = 'block';
        btnUpload.classList.add('active');
        btnPreset.classList.remove('active');
      }
    }

    const colorContainer = document.getElementById('colorOptions');
    const priceBox = document.querySelector('.price');

    COLORS.forEach(color => {
      const swatch = document.createElement('div');
      swatch.className = 'color-option';
      swatch.style.backgroundColor = color.code;
      swatch.title = color.name.charAt(0).toUpperCase() + color.name.slice(1);
      swatch.onclick = () => {
        document.getElementById('bikeImage').src = color.image;
        document.getElementById('presetMsg').textContent = `You are customizing with basic pattern and ${color.name} color.`;

        let basePrice = 21000000;
        let originalPrice = 27000000;
        if (color.code.toLowerCase() === '#ff6300') {
          basePrice = 19000000;
          originalPrice = 25000000;
        }

        const formattedBasePrice = basePrice.toLocaleString('vi-VN') + ' VND';
        const formattedOriginalPrice = originalPrice.toLocaleString('vi-VN') + ' VND';
        const discountPercent = '-' + Math.round(((originalPrice - basePrice) / originalPrice) * 100) + '%';

        priceBox.innerHTML = `
          <span style="color: #ff0000; font-weight: bold; font-size: 1.3em;">${formattedBasePrice}</span>
          <span style="text-decoration: line-through; color: gray; font-size: 0.9em; margin-left: 10px;">${formattedOriginalPrice}</span>
          <span style="color: red; font-size: 0.9em; margin-left: 6px;">${discountPercent}</span>
        `;
      };
      colorContainer.appendChild(swatch);
    });
  </script>
</body>
</html>
