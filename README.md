<html><head><base href="https://camiloduvane.github.io/Matlhemele2024/ ">
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Mundo Cristão</title>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">
  <style>
    body {
      font-family: 'Poppins', sans-serif;
      background-color: #e8f4f8;
      margin: 0;
      padding: 0;
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
      color: #333;
    }
    .container {
      background-color: #ffffff;
      padding: 2.5rem;
      border-radius: 20px;
      box-shadow: 0 15px 30px rgba(0,0,0,0.1);
      max-width: 500px;
      width: 100%;
    }
    h1, h2 {
      text-align: center;
      color: #2c3e50;
      text-shadow: 1px 1px 2px rgba(0,0,0,0.1);
      font-weight: 600;
    }
    form {
      display: flex;
      flex-direction: column;
    }
    input, button, select {
      margin: 0.5rem 0;
      padding: 0.75rem;
      font-size: 1rem;
      border: 1px solid #bdc3c7;
      border-radius: 5px;
      font-family: 'Poppins', sans-serif;
    }
    button {
      background-color: #2980b9;
      color: white;
      border: none;
      cursor: pointer;
      transition: background-color 0.3s;
      font-weight: 600;
    }
    button:hover {
      background-color: #3498db;
    }
    .hidden {
      display: none;
    }
    #registrationForm {
      display: block;
    }
    #gameInterface {
      display: none;
    }
    .error-message {
      color: #e74c3c;
      font-size: 0.9rem;
      margin-top: 0.5rem;
    }
    #playerRegistration {
      display: flex;
      flex-direction: column;
      gap: 1rem;
    }
    #gameInterface {
      display: flex;
      flex-direction: column;
      align-items: center;
      background-color: #f9f9f9;
      border-radius: 15px;
      padding: 2rem;
    }
    #menu {
      display: flex;
      justify-content: space-between;
      align-items: center;
      width: 100%;
      margin-bottom: 1.5rem;
      background-color: #3498db;
      padding: 1rem;
      border-radius: 10px;
      color: white;
    }
    #fullscreenToggle {
      background-color: #2980b9;
      color: white;
      border: none;
      padding: 0.5rem 1rem;
      border-radius: 5px;
      cursor: pointer;
      transition: background-color 0.3s;
      font-weight: 600;
    }
    #fullscreenToggle:hover {
      background-color: #3498db;
    }
    #playerName {
      font-weight: 600;
    }
    #currentDateTime {
      font-size: 0.9rem;
    }
    #gameContent {
      text-align: center;
      margin-top: 2rem;
    }
    #question {
      font-size: 1.3rem;
      margin-bottom: 1.5rem;
      color: #2c3e50;
    }
    #answerOptions {
      display: flex;
      flex-direction: column;
      align-items: center;
    }
    .answerOption {
      margin: 0.5rem 0;
      padding: 0.75rem;
      width: 100%;
      max-width: 300px;
      background-color: #ecf0f1;
      color: #2c3e50;
      border: 2px solid #bdc3c7;
      border-radius: 5px;
      cursor: pointer;
      transition: all 0.3s ease;
    }
    .answerOption:hover {
      background-color: #3498db;
      color: white;
      transform: translateY(-2px);
    }
    #score, #timer {
      font-weight: 600;
      color: #2c3e50;
      margin-top: 1.5rem;
      font-size: 1.1rem;
    }
    #gameSetup {
      text-align: center;
      margin-top: 2rem;
    }
    #summaryTable {
      width: 100%;
      border-collapse: collapse;
      margin-top: 1rem;
    }
    #summaryTable th, #summaryTable td {
      border: 1px solid #bdc3c7;
      padding: 0.5rem;
      text-align: center;
    }
    #summaryTable th {
      background-color: #2c3e50;
      color: white;
    }
    #summaryTable td {
      color: #2c3e50;
    }
    footer {
      text-align: center;
      margin-top: 2rem;
      color: #777;
      font-size: 0.9rem;
    }
    #orderSelection {
      display: flex;
      gap: 0.5rem;
      margin-bottom: 1rem;
    }
    #orderCode {
      width: 120px;
    }
    #questionOrder {
      flex: 1;
    }
    input:disabled, select:disabled {
      background-color: #f5f5f5;
      cursor: not-allowed;
    }
  </style>
</head>
<body>
  <div class="container">
    <div id="registrationForm">
      <h1>Cadastro</h1>
      <form id="playerRegistration">
        <input type="text" id="registerName" placeholder="Nome">
        <button type="submit">Começar</button>
      </form>
    </div>
    <div id="gameInterface">
      <div id="menu">
        <span id="playerName"></span>
        <span id="currentDateTime"></span>
        <button id="fullscreenToggle">Tela Cheia</button>
      </div>
      <div id="gameSetup" class="hidden">
        <h2>Mundo Cristão</h2>
        <p>Selecione o tipo de jogo para começar</p>
        <div id="orderSelection" style="margin-bottom: 1rem;">
          <input type="password" id="orderCode" placeholder="Código de acesso" maxlength="4">
          <select id="questionOrder" disabled>
            <option value="random">Perguntas Aleatórias</option>
            <option value="sequential">Perguntas em Ordem</option>
          </select>
        </div>
        <select id="gameType">
          <option value="">Tipo de jogo</option>
          <option value="infinite">Infinito</option>
          <option value="timed">Com tempo</option>
        </select>
        <div id="timerSetup" class="hidden">
          <input type="number" id="gameMinutes" placeholder="Minutos" min="0" max="59" value="5">
          <input type="number" id="gameSeconds" placeholder="Segundos" min="0" max="59" value="0">
        </div>
        <button id="startGameBtn" class="hidden">Iniciar</button>
      </div>
      <div id="gameContent" class="hidden">
        <p id="question"></p>
        <div id="answerOptions"></div>
        <p id="result"></p>
        <p id="score">Pontuação: 0/60</p>
        <p id="timer" class="hidden"></p>
        <button id="stopGameBtn" class="hidden">Parar Jogo</button>
      </div>
      <div id="gameSummary" class="hidden">
        <h2>Resumo</h2>
        <table id="summaryTable">
          <thead>
            <tr>
              <th>Nome</th>
              <th>Acertos</th>
              <th>Erros</th>
              <th>Total de Perguntas</th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td id="summaryName"></td>
              <td id="summaryCorrect"></td>
              <td id="summaryIncorrect"></td>
              <td id="summaryTotal"></td>
            </tr>
          </tbody>
        </table>
        <button id="playAgainBtn">Jogar Novamente</button>
      </div>
    </div>
    <footer>@CWD2024</footer>
  </div>

  <script>
    const randomNames = [
      "João", "Maria", "Pedro", "Ana", "Lucas", "Julia", 
      "Gabriel", "Sofia", "Miguel", "Isabella", "Arthur", "Helena",
      "Davi", "Alice", "Bernardo", "Laura", "Heitor", "Valentina"
    ];

    let score = 0;
    let questionIndex = 0;
    let timerInterval;
    let gameType = '';
    let incorrectAnswers = 0;
    const questions = [
       {
        question: "O que é a Bíblia?", 
        options: ["É conjunto de livros que contam histórias", "É um livro que serve para ser usar nos Domingos", "É um Conjunto de 66 Livros canônicos sagrado", "É um livro usado na Escola"], 
        correctAnswer: 2
      }, 
      {
        question: "Em quantas partes está agrupada a Bíblia?", 
        options: ["3", "2", "1", "0"],
        correctAnswer: 1
      },
      {
        question: "Como estão agrupados os livros da Bíblia? ",
        options: ["Antigo Testamento e Novo Testemunha", "Velho Testamento e Nova Testemunha", "Velho Testemunho e Novo Testamento", "Antigo Testamento e Novo Testamento"], 
        correctAnswer: 3
       }, 
      {
        question: "Quantos livros tem a Bíblia? ",
        options: ["66", "64", "62", "60"], 
        correctAnswer: 0
       }, 

      {
        question: "Quantos livros tem o Antigo Testamento? ",
        options: ["30", "24", "39", "37"], 
        correctAnswer: 2
       }, 

      {
        question: "Quantos livros tem o Novo Testamento? ",
        options: ["27", "23", "32", "20"], 
        correctAnswer: 0
       }, 

      {
       question: "O Antigo Testamento está subdividido em quantos grupos? ",
        options: ["2", "3", "4", "5"], 
        correctAnswer: 3
       }, 
      {
       question: "Qual desses grupos de livros fazem parte do Antigo Testamento?",
        options: ["Livros Evagelicos, Livros Históricos, Livros Poéticos, Livros dos Profetas Maiores e Livros dos poetas Menores", "Livros Patateus, Livros Históricos, Livros Poéticos, Livros dos Profetas", "Livros Patateus, Livros Históricos, Livros Poéticos, Livros dos Profetas Maiores e Livros dos Profetas Menores", "Genises, Deternomio, Josué, Ester, Jô, cântaro de Salomão, Isaías, Daniel, Oseias e Malaquias"], 
        correctAnswer: 2
       }, 

      {
        question: "Qual desses grupos de livros fazem parte do Antigo Testamento?",
        options: ["Livros Evangélicos, Livros Históricos, Livros Epístolas / Cartas Paulina, Livros Epístolas / Cartas Gerais, Livros Proféticos / Revelações", "Livros Históricos, Livros Epístolas / Cartas Paulina, Livros Epístolas / Cartas Gerais, Livros Proféticos", "Livros Evangélicos, Livros Históricos, Livros Epístolas, Livros Proféticos / Revelações", "Livros Evangélicos, Livros Históricos, Livros Epístolas, Livros de Revelações"], 
        correctAnswer: 0
      },

      {
       question: "Das opções as seguir qual os Sistemas de Abreviação dos livros da Bíblia que aprendeste? ",
        options: ["Sistema Antigo e Sistema Novo", "Sistema Velho e Sistema Actualizado", "Sistema Clássico e Sistema Actualizado", "Sistema Clássico e Sistema Moderno"], 
        correctAnswer: 3
       },
      {
      question: "No sistema Moderno o que acontece com todos os livros que os nomes vão até 05 letras? ",
      options: ["Não se abrevia", "Se abrevia", "Usamos as Consoantes do nome", "Usamos a primeira Consoante e o primeira vogal"], 
      correctAnswer: 0
      },

      {
      question: "Em que dia da semana da criação *Deus fez a Luz*? ",
      options: ["2° dia", "4° dia", "1° dia", "3° dia"], 
      correctAnswer: 2
      },

      {
      question: "Em que dia da semana da criação *Separação entre a Água e Água, Surgimento do Céu*? ",
      options: ["2° dia", "4° dia", "1° dia", "3° dia"], 
      correctAnswer: 0
      },

      {
      question: "Em que dia da semana da criação *Deus fez terra seca e vegetação*? ",
      options: ["2° dia", "4° dia", "1° dia", "3° dia"], 
      correctAnswer: 3
      },


      {
      question: "Em que dia da semana da criação *Deus criou luminares, a Lua e as estrelas*? ",
      options: ["2° dia", "4° dia", "1° dia", "3° dia"], 
      correctAnswer: 1
      },


      {
      question: "Em que dia da semana da criação *Deus fez todo Reptil e toda ave*? ",
      options: ["6° dia", "4° dia", "7° dia", "5° dia"], 
      correctAnswer: 3
      },

      {
      question: "Em que dia da semana da criação *Deus fez animais terrestres e o Homem*? ",
      options: ["6° dia", "4° dia", "7° dia", "5° dia"], 
      correctAnswer: 0
      },

      {
      question: "Em que dia da semana da criação *Deus descansou*?",
      options: ["6° dia", "4° dia", "7° dia", "5° dia"], 
      correctAnswer: 2
      },

      {
      question: "Que Criatura, para ser feito foi preciso um Soleno Conselho Divino?",
      options: ["Elefante", "Leão", "Mulher", "Homem"], 
      correctAnswer: 3
      },

      {
      question: "Qual Das alternativas descreve a criação do Homem segundo a Bíblia? ",
      options: ["Do pó da terra", "Feito da luz do sol", "Formado da água do mar", "Criado a partir de estrelas"], 
      correctAnswer: 0
      },

      {
      question: "Qual é a técnica cirúrgica inovadora usada por Deus, segundo o livro de Gênesis, para virar a primeira Mulher? ",
      options: ["Fez um clone direto do pó da terra", "Transformou água em ossos e carne", "Utilizou uma costela do Homem como bese", "Misturou pó da terra com luz do sol"], 
      correctAnswer: 2
      },

       {
      question: "Deus fez o Homem dotado de pleno poder para governar, e em paralelo uma ordem proibitiva.",
      options: ["Falso", "Verdade"], 
      correctAnswer: 1
      },

{
      question: "Qual era o tipo de arvore Proibida?",
      options: ["Macaneira", "a", "Verdade", "Verdade"], 
      correctAnswer: 1
      }
    ];

    function shuffleArray(array) {
      for (let i = array.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));
        [array[i], array[j]] = [array[j], array[i]];
      }
    }

    function requestFullscreen() {
      if (!document.fullscreenElement) {
        document.documentElement.requestFullscreen().catch(err => {
          console.error(`Error attempting to enable full-screen mode: ${err.message} (${err.name})`);
        });
      }
    }

    document.getElementById('playerRegistration').addEventListener('submit', function(e) {
      e.preventDefault();
      
      let playerName = document.getElementById('registerName').value.trim();
      if (!playerName) {
        playerName = randomNames[Math.floor(Math.random() * randomNames.length)];
      }
      
      localStorage.setItem('playerName', playerName);
      
      document.getElementById('registrationForm').style.display = 'none';
      document.getElementById('gameInterface').style.display = 'block';
      document.getElementById('playerName').textContent = playerName;

      if (document.documentElement.requestFullscreen) {
        document.documentElement.requestFullscreen();
      }

      showGameInterface();
    });

    function showGameInterface() {
      document.getElementById('gameSetup').classList.remove('hidden');
      const playerName = localStorage.getItem('playerName');
      document.getElementById('playerName').textContent = playerName;
      updateDateTime();
      setInterval(updateDateTime, 1000);
    }

    window.addEventListener('load', function() {
      if (document.fullscreenEnabled) {
        document.documentElement.requestFullscreen().catch(err => {
          console.log('Error attempting to enable fullscreen:', err);
        });
      }
    });

    document.getElementById('orderCode').addEventListener('input', function() {
      const code = this.value;
      const orderSelect = document.getElementById('questionOrder');
      
      if (code === '6363') {
        orderSelect.disabled = false;
        this.style.borderColor = '#2ecc71';
      } else {
        orderSelect.disabled = true;
        orderSelect.value = 'random';
        this.style.borderColor = '#e74c3c';
      }
    });

    document.getElementById('gameType').addEventListener('change', function() {
      gameType = this.value;
      const timerSetup = document.getElementById('timerSetup');
      const startGameBtn = document.getElementById('startGameBtn');
      if (gameType === 'timed') {
        timerSetup.classList.remove('hidden');
      } else {
        timerSetup.classList.add('hidden');
      }
      startGameBtn.classList.remove('hidden');
    });

    document.getElementById('startGameBtn').addEventListener('click', startGame);

    function startGame() {
      const orderType = document.getElementById('questionOrder').value;
      if (orderType === 'random') {
        shuffleArray(questions);
      }
      document.getElementById('gameSetup').classList.add('hidden');
      document.getElementById('gameContent').classList.remove('hidden');
      if (gameType === 'timed') {
        const minutes = parseInt(document.getElementById('gameMinutes').value);
        const seconds = parseInt(document.getElementById('gameSeconds').value);
        const duration = minutes * 60 + seconds;
        startTimer(duration);
        document.getElementById('timer').classList.remove('hidden');
      } else {
        document.getElementById('stopGameBtn').classList.remove('hidden');
      }
      nextQuestion();
    }

    function nextQuestion() {
      if (questionIndex < questions.length) {
        const currentQuestion = questions[questionIndex];
        document.getElementById('question').textContent = currentQuestion.question;
        const answerOptionsDiv = document.getElementById('answerOptions');
        answerOptionsDiv.innerHTML = '';
        currentQuestion.options.forEach((option, index) => {
          const button = document.createElement('button');
          button.textContent = option;
          button.classList.add('answerOption');
          button.addEventListener('click', () => checkAnswer(index));
          answerOptionsDiv.appendChild(button);
        });
        document.getElementById('result').textContent = '';
      } else {
        endGame();
      }
    }

    function checkAnswer(selectedIndex) {
      const currentQuestion = questions[questionIndex];
      if (selectedIndex === currentQuestion.correctAnswer) {
        score++;
        document.getElementById('result').textContent = 'Correto!';
      } else {
        incorrectAnswers++;
        document.getElementById('result').textContent = 'Incorreto. A resposta certa era: ' + currentQuestion.options[currentQuestion.correctAnswer];
      }
      questionIndex++;
      document.getElementById('score').textContent = `Pontuação: ${score}/${questionIndex}`;
      setTimeout(nextQuestion, 1500);
    }

    function startTimer(duration) {
      let timer = duration;
      timerInterval = setInterval(function() {
        const minutes = parseInt(timer / 60, 10);
        const seconds = parseInt(timer % 60, 10);
        document.getElementById('timer').textContent = `Tempo: ${minutes}:${seconds < 10 ? '0' : ''}${seconds}`;
        if (--timer < 0) {
          clearInterval(timerInterval);
          endGame();
        }
      }, 1000);
    }

    document.getElementById('stopGameBtn').addEventListener('click', endGame);

    function endGame() {
      clearInterval(timerInterval);
      document.getElementById('gameContent').classList.add('hidden');
      document.getElementById('gameSummary').classList.remove('hidden');
      document.getElementById('summaryName').textContent = localStorage.getItem('playerName');
      document.getElementById('summaryCorrect').textContent = score;
      document.getElementById('summaryIncorrect').textContent = incorrectAnswers;
      document.getElementById('summaryTotal').textContent = questionIndex;
    }

    document.getElementById('playAgainBtn').addEventListener('click', function() {
      score = 0;
      questionIndex = 0;
      incorrectAnswers = 0;
      document.getElementById('gameSummary').classList.add('hidden');
      document.getElementById('gameSetup').classList.remove('hidden');
      document.getElementById('gameType').value = '';
      document.getElementById('gameMinutes').value = '10';
      document.getElementById('gameSeconds').value = '0';
      document.getElementById('timerSetup').classList.add('hidden');
      document.getElementById('startGameBtn').classList.add('hidden');
      document.getElementById('score').textContent = 'Pontuação: 0/50';
    });

    function toggleFullscreen() {
      if (!document.fullscreenElement) {
        document.documentElement.requestFullscreen().catch(err => {
          alert(`Error attempting to enable full-screen mode: ${err.message} (${err.name})`);
        });
      } else {
        if (document.exitFullscreen) {
          document.exitFullscreen();
        }
      }
    }

    function updateFullscreenButtonText() {
      const fullscreenButton = document.getElementById('fullscreenToggle');
      if (document.fullscreenElement) {
        fullscreenButton.textContent = 'Tela Cheia';
      } else {
        fullscreenButton.textContent = 'Tela Cheia';
      }
    }

    document.getElementById('fullscreenToggle').addEventListener('click', toggleFullscreen);
    document.addEventListener('fullscreenchange', updateFullscreenButtonText);
  </script>
</body>
</html>
