<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Mundo Cristão - Jogo</title>
  <script src="https://www.gstatic.com/firebasejs/9.x.x/firebase-app.js"></script>
  <script src="https://www.gstatic.com/firebasejs/9.x.x/firebase-firestore.js"></script>
</head>
<body>
  <!-- Interface do jogo -->
  <script>
    // Configuração Firebase
    const firebaseConfig = {
      apiKey: "AIzaSyAJzL6sk0pDZtC-jtbpLNNR1dlQ94D9ccA",
      authDomain: "mea2024-d8f25.firebaseapp.com",
      projectId: "mea2024-d8f25",
      storageBucket: "mea2024-d8f25.appspot.com",
      messagingSenderId: "770842232248",
      appId: "1:770842232248:web:3b549761e40a0df3fbfb4d",
      measurementId: "G-EBEJ2WM5S1"
    };

    const app = firebase.initializeApp(firebaseConfig);
    const db = firebase.firestore(app);

    let gameStartTime;
    let userAnswers = [];
    let score = 0;
    let incorrectAnswers = 0;
    let questionIndex = 0;
    const questions = [
      // Perguntas do jogo...
    ];

    function startGame() {
      gameStartTime = new Date(); // Registra o início do jogo
      userAnswers = [];
      questionIndex = 0;
      score = 0;
      incorrectAnswers = 0;
      nextQuestion();
    }

    function nextQuestion() {
      if (questionIndex < questions.length) {
        // Mostra próxima pergunta...
      } else {
        endGame();
      }
    }

    function checkAnswer(selectedIndex) {
      const currentQuestion = questions[questionIndex];
      const wasCorrect = selectedIndex === currentQuestion.correctAnswer;

      userAnswers.push({
        question: currentQuestion.question,
        userAnswer: currentQuestion.options[selectedIndex],
        correctAnswer: currentQuestion.options[currentQuestion.correctAnswer],
        wasCorrect: wasCorrect
      });

      if (wasCorrect) {
        score++;
      } else {
        incorrectAnswers++;
      }

      questionIndex++;
      nextQuestion();
    }

    async function endGame() {
      const gameEndTime = new Date();
      const totalTime = Math.round((gameEndTime - gameStartTime) / 1000); // Tempo em segundos

      const gameData = {
        playerName: localStorage.getItem('playerName'),
        gameType: "Normal", // Ajustar se necessário
        score: score,
        incorrectAnswers: incorrectAnswers,
        totalQuestions: questions.length,
        totalTime: totalTime,
        questionHistory: userAnswers,
        timestamp: firebase.firestore.FieldValue.serverTimestamp()
      };

      try {
        const docRef = await db.collection("gameResults").add(gameData);
        console.log("Resultados salvos com ID:", docRef.id);
      } catch (error) {
        console.error("Erro ao salvar resultados:", error);
      }
    }
  </script>
</body>
</html>

