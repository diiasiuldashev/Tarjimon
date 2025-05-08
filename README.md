<!DOCTYPE html>
<html lang="uz">
<head>
  <meta charset="UTF-8">
  <title>Diyas Tarjimon</title>
  <style>
    body {
      font-family: sans-serif;
      background: linear-gradient(to right, #f5af19, #f12711);
      color: white;
      text-align: center;
      padding: 50px;
    }
    input {
      padding: 10px;
      width: 200px;
    }
    button {
      padding: 10px 20px;
      margin-left: 10px;
      cursor: pointer;
    }
    .result {
      margin-top: 20px;
      font-size: 18px;
    }
  </style>
</head>
<body>
  <h1>Diyas Tarjimon</h1>
  <input type="text" id="input-word" placeholder="So‘z kiriting...">
  <button id="translate-btn">Tarjima qil</button>
  <div class="result" id="result"></div>

  <script>
    const dictionary = {
      "qalam": ["pen", "pencil", "stylus"],
      "kitob": ["book", "volume", "publication"],
      "stol": ["table", "desk"],
      "ko'z": ["eye", "sight", "vision"],
      "yorug'lik": ["light", "brightness", "illumination"]
    };

    document.getElementById("translate-btn").addEventListener("click", function () {
      const word = document.getElementById("input-word").value.trim().toLowerCase();
      const translations = dictionary[word];
      const resultElement = document.getElementById("result");

      if (translations) {
        resultElement.innerHTML = `<strong>Tarjimalar:</strong> ${translations.join(", ")}`;
      } else {
        resultElement.textContent = "Bu so‘z uchun tarjima topilmadi.";
      }
    });
  </script>
</body>
</html>
