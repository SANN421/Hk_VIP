# Hk_VIP
vipserveruser
<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <title>Hacker Togel Generator</title>
  <style>
    body {
      background-color: #000;
      color: #00ff00;
      font-family: 'Courier New', Courier, monospace;
      text-align: center;
      padding: 50px;
    }

    h1 {
      font-size: 36px;
      margin-bottom: 40px;
    }

    .result {
      font-size: 28px;
      margin: 20px 0;
    }

    button {
      background-color: #001100;
      color: #00ff00;
      border: 2px solid #00ff00;
      padding: 12px 30px;
      font-size: 18px;
      cursor: pointer;
      border-radius: 8px;
      transition: background 0.3s, color 0.3s;
    }

    button:hover:enabled {
      background-color: #003300;
    }

    button:disabled {
      opacity: 0.5;
      cursor: not-allowed;
    }

    #cooldownMsg {
      margin-top: 20px;
      font-size: 16px;
      color: #ff4444;
    }
  </style>
</head>
<body>
  <h1>SERVER HK NOMOR TOGEL REGION ASIA</h1>
  <button id="generateBtn" onclick="generateNumbers()">Generate Nomor</button>

  <div class="result" id="result2D"></div>
  <div class="result" id="result3D"></div>
  <div class="result" id="result4D"></div>
  <div id="cooldownMsg"></div>

  <script>
    const cooldownHours = 12;
    const cooldownKey = 'lastGenerateTime';

    function padNumber(num, length) {
      return num.toString().padStart(length, '0');
    }

    function generateNumbers() {
      const now = Date.now();
      localStorage.setItem(cooldownKey, now.toString());

      const angka2D = padNumber(Math.floor(Math.random() * 100), 2);
      const angka3D = padNumber(Math.floor(Math.random() * 1000), 3);
      const angka4D = padNumber(Math.floor(Math.random() * 10000), 4);

      document.getElementById('result2D').textContent = "Angka 2D: " + angka2D;
      document.getElementById('result3D').textContent = "Angka 3D: " + angka3D;
      document.getElementById('result4D').textContent = "Angka 4D: " + angka4D;

      updateCooldownUI();
    }

    function updateCooldownUI() {
      const btn = document.getElementById('generateBtn');
      const cooldownMsg = document.getElementById('cooldownMsg');
      const lastTime = parseInt(localStorage.getItem(cooldownKey));
      const now = Date.now();

      if (!isNaN(lastTime)) {
        const diff = now - lastTime;
        const cooldown = cooldownHours * 60 * 60 * 1000;

        if (diff < cooldown) {
          const remaining = cooldown - diff;
          btn.disabled = true;
          const hours = Math.floor(remaining / (60 * 60 * 1000));
          const minutes = Math.floor((remaining % (60 * 60 * 1000)) / (60 * 1000));
          cooldownMsg.textContent = `Cooldown aktif. Coba lagi dalam ${hours} jam ${minutes} menit.`;

          setTimeout(updateCooldownUI, 60000); // Perbarui setiap 1 menit
          return;
        }
      }

      btn.disabled = false;
      cooldownMsg.textContent = "";
    }

    updateCooldownUI();
  </script>
</body>
</html>
