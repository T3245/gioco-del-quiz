<!DOCTYPE html>
<html lang="it">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Quiz Cinema & Musica 🎬🎶</title>
  <style>
    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background: linear-gradient(135deg, #1e1e2f, #2a2a40);
      color: #fff;
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
      margin: 0;
    }
    .quiz-container {
      background: #252538;
      padding: 30px;
      border-radius: 15px;
      box-shadow: 0 10px 25px rgba(0, 0, 0, 0.5);
      max-width: 500px;
      width: 90%;
      text-align: center;
    }
    h1 { color: #ff4757; margin-bottom: 20px; }
    .btn-container { display: flex; flex-direction: column; gap: 12px; margin-top: 20px; }
    button {
      background: #3742fa;
      color: white;
      border: none;
      padding: 12px 20px;
      font-size: 16px;
      border-radius: 8px;
      cursor: pointer;
      transition: background 0.3s;
    }
    button:hover { background: #5352ed; }
    .score { font-size: 20px; font-weight: bold; color: #2ed573; margin-top: 20px; }
  </style>
</head>
<body>

  <div class="quiz-container">
    <h1>Quiz Cinema & Musica 🎬🎶</h1>
    <div id="quiz">
      <h2 id="question">Caricamento domanda...</h2>
      <div id="answer-buttons" class="btn-container"></div>
    </div>
    <div id="score-container" class="score"></div>
  </div>

  <script>
    const questions = [
      {
        question: "1. Nel Re Leone, come si chiama il fedele bucero consigliere del re?",
        answers: [
          { text: "A) Zazu", correct: true },
          { text: "B) Iago", correct: false },
          { text: "C) Rafiki", correct: false }
        ]
      },
      {
        question: "2. Chi è conosciuto in tutto il mondo come il 'Re del Pop'?",
        answers: [
          { text: "A) Elvis Presley", correct: false },
          { text: "B) Michael Jackson", correct: true },
          { text: "C) Prince", correct: false }
        ]
      },
      {
        question: "3. Chi interpreta Rose nel film Titanic (1997)?",
        answers: [
          { text: "A) Kate Winslet", correct: true },
          { text: "B) Julia Roberts", correct: false },
          { text: "C) Nicole Kidman", correct: false }
        ]
      }
    ];

    let currentQuestionIndex = 0;
    let score = 0;

    function startQuiz() {
      currentQuestionIndex = 0;
      score = 0;
      showQuestion();
    }

    function showQuestion() {
      resetState();
      let currentQuestion = questions[currentQuestionIndex];
      document.getElementById("question").innerText = currentQuestion.question;

      currentQuestion.answers.forEach(answer => {
        const button = document.createElement("button");
        button.innerText = answer.text;
        button.addEventListener("click", () => selectAnswer(answer.correct));
        document.getElementById("answer-buttons").appendChild(button);
      });
    }

    function resetState() {
      document.getElementById("answer-buttons").innerHTML = "";
    }

    function selectAnswer(isCorrect) {
      if (isCorrect) score++;
      currentQuestionIndex++;
      if (currentQuestionIndex < questions.length) {
        showQuestion();
      } else {
        showScore();
      }
    }

    function showScore() {
      resetState();
      document.getElementById("question").innerText = "Quiz Completato!";
      document.getElementById("score-container").innerText = `Il tuo punteggio finale è: ${score} su ${questions.length}! 🎉`;
    }

    startQuiz();
  </script>
</body>
</html>
