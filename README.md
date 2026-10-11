<!DOCTYPE html>
<html lang="it">
<head>
  <meta charset="UTF-8">
  <title>Quiz Cinema e Musica</title>
  <style>
    body {
      font-family: sans-serif;
      background-color: #1a1a2e;
      color: #ffffff;
      text-align: center;
      padding: 40px;
    }
    .card {
      background-color: #16213e;
      border: 2px solid #e94560;
      border-radius: 10px;
      padding: 20px;
      max-width: 400px;
      margin: 0 auto;
    }
    button {
      background-color: #0f3460;
      color: white;
      border: 1px solid #e94560;
      padding: 10px;
      margin: 5px 0;
      width: 100%;
      border-radius: 5px;
      font-size: 16px;
      cursor: pointer;
    }
    button:hover { background-color: #e94560; }
  </style>
</head>
<body>

  <div class="card">
    <h1>🎬 Quiz Cinema & Musica 🎶</h1>
    <h3 id="domanda">Caricamento...</h3>
    <div id="opzioni"></div>
    <p id="risultato" style="font-weight: bold; color: #4eef90;"></p>
  </div>

  <script>
    const domande = [
      {
        q: "1. Nel Re Leone, come si chiama il consigliere del re?",
        opzioni: ["A) Zazu", "B) Iago", "C) Rafiki"],
        esatta: 0
      },
      {
        q: "2. Chi è conosciuto come il 'Re del Pop'?",
        opzioni: ["A) Elvis Presley", "B) Michael Jackson", "C) Prince"],
        esatta: 1
      },
      {
        q: "3. Chi interpreta Rose in 'Titanic' (1997)?",
        opzioni: ["A) Kate Winslet", "B) Julia Roberts", "C) Nicole Kidman"],
        esatta: 0
      }
    ];

    let indice = 0;
    let punti = 0;

    function mostraDomanda() {
      const d = domande[indice];
      document.getElementById("domanda").innerText = d.q;
      const box = document.getElementById("opzioni");
      box.innerHTML = "";

      d.opzioni.forEach((opt, i) => {
        const btn = document.createElement("button");
        btn.innerText = opt;
        btn.onclick = () => rispondi(i);
        box.appendChild(btn);
      });
    }

    function rispondi(i) {
      if (i === domande[indice].esatta) punti++;
      indice++;
      if (indice < domande.length) {
        mostraDomanda();
      } else {
        document.getElementById("domanda").innerText = "Quiz Completato!";
        document.getElementById("opzioni").innerHTML = "";
        document.getElementById("risultato").innerText = "Punteggio: " + punti + " su " + domande.length + "! 🎉";
      }
    }

    mostraDomanda();
  </script>
</body>
</html>
