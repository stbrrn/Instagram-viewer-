<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Instagram Data Viewer</title>
  <style>
    body {
      background: #0d1117;
      color: #e6edf3;
      font-family: 'Consolas', monospace;
      margin: 0;
      padding: 20px;
    }
    h1 {
      text-align: center;
      color: #58a6ff;
    }
    input, button {
      background: #161b22;
      color: #e6edf3;
      border: 1px solid #30363d;
      border-radius: 5px;
      padding: 8px;
      font-size: 14px;
    }
    button {
      cursor: pointer;
      margin-left: 5px;
    }
    pre {
      background: #161b22;
      padding: 10px;
      border-radius: 5px;
      white-space: pre-wrap;
      word-break: break-all;
      margin-top: 15px;
      font-size: 13px;
    }
  </style>
</head>
<body>
  <h1>📁 Instagram Data Viewer</h1>
  <p>Pilih file JSON hasil download data Instagram kamu:</p>
  <input type="file" id="fileInput" accept=".json">
  <button onclick="loadJSON()">Tampilkan</button>
  <pre id="output">Menunggu file...</pre>

  <script>
    function loadJSON() {
      const file = document.getElementById('fileInput').files[0];
      if (!file) return alert('Pilih file JSON dulu bro 😎');

      const reader = new FileReader();
      reader.onload = e => {
        try {
          const json = JSON.parse(e.target.result);
          document.getElementById('output').textContent =
            JSON.stringify(json, null, 2);
        } catch (err) {
          document.getElementById('output').textContent =
            '⚠️ File bukan JSON valid bro.';
        }
      };
      reader.readAsText(file);
    }
  </script>
</body>
</html>
