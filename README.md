<!DOCTYPE html>
<html lang="it">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Quiz Cinema & Musica 🎬🎶</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #1a1a2e;
      color: #ffffff;
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
      margin: 0;
      padding: 20px;
    }
    .quiz-card {
      background-color: #16213e;
      border: 2px solid #e94560;
      border-radius: 12px;
      padding: 25px;
      max-width: 500px;
      width: 100%;
      text-align: center;
      box-shadow: 0 8px 16px rgba(0,0,0,0.4);
    }
    h1 {
      color: #e94560;
      font-size: 24px;
      margin-bottom: 20px;
    }
    .question {
      font-size: 18px;
      margin-bottom: 20px;
    }
    .btn {
      background-color: #0f3460;
      color: white;
      border: 1px solid #e94560;
      padding: 12px 15px;
      margin: 8px 0;
      width: 100%;
      border-radius: 6px;
      font-size: 16px;
      cursor: pointer;
      text-align: left;
    }
    .btn:hover {
      background-color: #e94560;
    }
    .result {
      font-size: 20px;
      font-weight: bold;
      color: #4eef90;
      margin-top: 20px;
    }
    .restart-btn {
      background-color: #e94560;
      color: white;
      border: none;
      padding: 10px 20px;
      border-radius: 6px;
      font-size: 16px;
      cursor: pointer;
      margin-top: 15px;
    }
  </style>
</head>
<body>

  <div class="quiz-card">
    <h1>🎬 Quiz Cinema & Musica 🎶</h1>
    <div id="quiz-box">
      <div id="question" class="question">Caricamento...</div>
      <div id="answers"></div>
    </div>
    <div id="result" class="result"></div>
  </div>

  <script>
    const questions = [
      {
        q: "1. Nel film 'Il Re Leone', come si chiama il fideno bucero consigliere del re?",
        options: ["A) Zazu", "B) Iago", "C) Rafiki"],
        correct: 0
      },
      {
        q: "2. Chi è conosciuto in tutto il mondo come il 'Re del Pop'?",
        options: ["A) Elvis Presley", "B) Michael Jackson", "C) Prince"],
        correct: 1
      },
      {
        q: "3. Chi interpreta Rose nel celebre film 'Titanic' (1997)?",
        options: ["A) Kate Winslet", "B) Julia Roberts", "C) Nicole Kidman"],
        correct: 0
      }
    ];

    let current = 0;
    let score = 0;

    function loadQuestion() {
      const q = questions[current];
      document.getElementById("question").innerText = q.q;
      const answersDiv = document.getElementById("answers");
      answersDiv.innerHTML = "";

      q.options.forEach((opt, index) => {
        const btn = document.createElement("button");
        btn.className = "btn";
        btn.innerText = opt;
        btn.onclick = () => checkAnswer(index);
        answersDiv.appendChild(btn);
      });
    }

    function checkAnswer(index) {
      if (index === questions[current].correct) {
        score++;
      }
      current++;
      if (current < questions.length) {
        loadQuestion();
      } else {
        showResult();
      }
    }

    function showResult() {
      document.getElementById("quiz-box").style.display = "none";
      document.getElementById("result").innerHTML = 
        `Hai completato il quiz!<br><br>Punteggio: <strong>${score} su ${questions.length}</strong><br><br>` +
        `<button class="restart-btn" onclick="restart()">Rigioca 🔄</button>`;
    }

    function restart() {
      current = 0;
      score = 0;
      document.getElementById("quiz-box").style.display = "block";
      document.getElementById("result").innerHTML = "";
      loadQuestion();
    }

    loadQuestion();
  </script>

</body>
</html>
