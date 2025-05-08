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
<script>
  const dictionary = {
    "qalam": ["pen", "pencil", "stylus"],
    "kitob": ["book", "volume", "publication"],
    "stol": ["table", "desk"],
    "ko'z": ["eye", "sight", "vision"],
    "yorug'lik": ["light", "brightness", "illumination"],
    "daraxt": ["tree", "plant"],
    "uy": ["house", "home", "residence"],
    "telefon": ["phone", "mobile", "cellphone"],
    "maktab": ["school", "academy", "institution"],
    "daryo": ["river", "stream", "waterway"]
  };

  document.getElementById("translate-btn").addEventListener("click", function () {
    const word = document.getElementById("input-word").value.trim().toLowerCase();
    const translations = dictionary[word];
    const resultElement = document.getElementById("result");

    if (translations) {
      resultElement.innerHTML = `<strong>Tarjimalar:</strong> ${translations.join(", ")}`;
    } else {
      let suggestions = Object.keys(dictionary).filter(k => k.startsWith(word.slice(0, 2)));
      if (suggestions.length > 0) {
        resultElement.innerHTML = `Bu so‘z uchun tarjima topilmadi.<br><em>Shu so‘zlar nazarda tutilganmi?</em><br>${suggestions.join(", ")}`;
      } else {
        resultElement.textContent = "Bu so‘z lug‘atda topilmadi.";
      }
    }
  });
</script>
<!DOCTYPE html>
<html lang="uz">
<head>
  <meta charset="UTF-8">
  <title>Diyas Tarjimon</title>
  <style>
    body {
      font-family: sans-serif;
      background: linear-gradient(to right, #00c6ff, #0072ff);
      color: white;
      text-align: center;
      padding: 30px;
    }
    input {
      padding: 10px;
      width: 300px;
      font-size: 16px;
    }
    button {
      padding: 10px 20px;
      font-size: 16px;
      margin-left: 10px;
    }
  </style>
</head>
<body>
  <h1>Diyas Tarjimon</h1>
  <input type="text" id="text" placeholder="So‘z yoki jumla kiriting">
  <button onclick="translate()">Tarjima</button>

  <script>
    function translate() {
      const text = document.getElementById('text').value.trim();
      const url = "https://translate.google.com/?sl=auto&tl=en&text=" + encodeURIComponent(text) + "&op=translate";
      window.open(url, "_blank");
    }
  </script>
</body>
</html>
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Diyas Tarjimon</title>
</head>
<body>
  <h2>So‘zni tarjima qiling</h2>
  <input type="text" id="word" placeholder="So‘z kiriting">
  <button onclick="translate()">Tarjima</button>
  <p id="output"></p>

  <script>
    async function translate() {
      const text = document.getElementById('word').value;
      const response = await fetch("https://libretranslate.de/translate", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({
          q: text,
          source: "uz",
          target: "en", // kerakli til (masalan: 'ar' arabcha, 'ru' ruscha)
          format: "text"
        })
      });

      const data = await response.json();
      document.getElementById('output').innerText = "Tarjima: " + data.translatedText;
    }
  </script>
</body>
</html>
