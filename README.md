<html><head><base>

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
        <p id="score">Pontuação: 0/51</p>
        <p id="timer" class="hidden"></p>
        <button id="stopGameBtn" class="hidden">Finalizar</button>
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
    <footer>@CWD2025</footer>
  </div>

  <script>
    const randomNames = [
      "Camilo Duvane", "Maria Langa"
    ];

    let score = 0;
    let questionIndex = 0;
    let timerInterval;
    let gameType = '';
    let incorrectAnswers = 0;
    const questions = [


      
      {
      question: "O que é a Bíblia?", 
      options: ["É um conjunto de livros que contam histórias", "É um livro que serve para ser usado nos Domingos", "É um Conjunto de 66 Livros canônicos sagrado", "É um livro Escolar"], 
      correctAnswer: 2
      }, 
      {
      question: "Em quantas partes está agrupada a Bíblia?", 
      options: ["3", "2", "1", "0"],
      correctAnswer: 1
      },
      {
      question: "Como estão agrupados os livros da Bíblia? ",
      options: ["Antigo Testamento e Novo Testemunho", "Velho Testamento e Nova Testemunha", "Velho Testemunho e Novo Testamento", "Antigo Testamento e Novo Testamento"], 
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
      question: "O Antigo Testamento está sub dividido enquantos grupos? ",
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
      options: ["Livros Evangélicos, Livros Históricos, Livros Epístolas - Cartas Paulina, Livros Epístolas - Cartas Gerais, Livros Proféticos - Revelações", "Livros Históricos, Livros Epístolas - Cartas Paulina, Livros Epístolas - Cartas Gerais, Livros Proféticos", "Livros Evangélicos, Livros Históricos, Livros Epístolas, Livros Proféticos - Revelações", "Livros Evangélicos, Livros Históricos, Livros Epístolas, Livros de Revelações"], 
      correctAnswer: 0
      },
      {
      question: "Das opções a seguir, qual é o Sistema de Abreviação dos livros da Bíblia que aprendeste? ",
      options: ["Sistema Antigo e Sistema Novo", "Sistema Velho e Sistema Actualizado", "Sistema Clássico e Sistema Actualizado", "Sistema Clássico e Sistema Moderno"], 
      correctAnswer: 3
      },
      {
      question: "No sistema Moderno o que acontece com todos os livros que os nomes têm 05 letras? ",
      options: ["Não se abrevia", "Se abrevia", "Usamos as Consoantes do nome", "Usamos a primeira Consoante e o primeira vogal"], 
      correctAnswer: 0
      },



      
      {
      question: "Em que dia da semana Deus fez a Luz? ",
      options: ["2° dia", "4° dia", "1° dia", "3° dia"], 
      correctAnswer: 2
      },
      {
      question: "Em que dia da semana Deus fez a Separação entre a Água e Água, Surgimento do Céu? ",
      options: ["2° dia", "4° dia", "1° dia", "3° dia"], 
      correctAnswer: 0
      },
      {
      question: "Em que dia da semana Deus fez terra seca e vegetação? ",
      options: ["2° dia", "4° dia", "1° dia", "3° dia"], 
      correctAnswer: 3
      },
      {
      question: "Em que dia da semana Deus criou luminares, a Lua e as estrelas? ",
      options: ["2° dia", "4° dia", "1° dia", "3° dia"], 
      correctAnswer: 1
      },
      {
      question: "Em que dia da semana Deus fez todo Reptil e toda ave? ",
      options: ["6° dia", "4° dia", "7° dia", "5° dia"], 
      correctAnswer: 3
      },
      {
      question: "Em que dia da semana Deus fez animais terrestres e o Homem? ",
      options: ["6° dia", "4° dia", "7° dia", "5° dia"], 
      correctAnswer: 0
      },
      {
      question: "Em que dia da semana Deus descansou?",
      options: ["6° dia", "4° dia", "7° dia", "5° dia"], 
      correctAnswer: 2
      },




      
      {
      question: "Que Criatura, para ser feito foi preciso um Soleno Conselho Divino?",
      options: ["O Elefante", "O Leão", "A Mulher", "O Homem"], 
      correctAnswer: 3
      },
      {
      question: "Qual Das alternativas descreve a criação do Homem segundo a Bíblia? ",
      options: ["Do pó da terra", "Da luz do sol", "Da água do mar", "Criado a partir das estrelas cósmicas"], 
      correctAnswer: 0
      },
      {
      question: "Qual é a técnica cirúrgica inovadora usada por Deus, segundo o livro de Gênesis, para fazer a primeira Mulher? ",
      options: ["Fez um clone direto do pó da terra", "Transformou água em ossos e carne", "Utilizou uma costela do Homem como base", "Misturou pó da terra com luz do sol"], 
      correctAnswer: 2
      },
      {
      question: "Deus fez o Homem dotado de pleno poder para governar, e em paralelo uma ordem proibitiva.",
      options: ["Falso", "Verdade"], 
      correctAnswer: 1
      },
      {
      question: "E importante saber o nome da árvore Proibida?",
      options: ["Sim", "Talvez", "Não"], 
      correctAnswer: 2
      },
      {
      question: "Será que Deus sabia que o Homem iria pecar?",
      options: ["Sim", "Talvez", "Não"], 
      correctAnswer: 0
      },
      {
      question: "Das opções abaixo quais são os intervenientes envolvidos na queda do Homem?",
      options: ["A Mulher, a Serpente e o Homem", "A Mulher, A serpente e a Maça", "A Mulher, o Homem e a Árvore da Vida", "A Mulher, O Homem e Deus"], 
      correctAnswer: 0
      },
      {
      question: "Quem lhe foi aumentado a dor do parto?",
      options: ["O homem", "A mulher", "A árvore da Vida", "A serpente"], 
      correctAnswer: 1
      },
      {
      question: "A quem lhe foi decretado uma vida amaldiçoada, condenada a andar sobre o seu proprio ventre e comer o pó da Terra?",
      options: ["O homem", "A Mulher", "A árvore da Vida", "A serpente"], 
      correctAnswer: 3
      },
      {
      question: "Quem lhe foi senteciado a sofrer para poder viver do seu suor?",
      options: ["O homem", "A mulher", "A árvore da Vida", "Deus"], 
      correctAnswer: 0
      },
      {
      question: "Com a queda do Homem o Relacionamento entre o Homem e Deus foi Prejudicado. Qual e o tipo de Consequências?",
      options: ["Consequência Física", "Consequência Espiritual"], 
      correctAnswer: 1
      },
      {
      question: "Com a queda do Homem, o homem passou a ficar Doente. Qual e o tipo de Consequências?",
      options: ["Consequência Fisica", "Consequência Espiritual"], 
      correctAnswer: 0
      },






      
      {
      question: "Quem e Pecador?",
      options: ["O Homem", "A Mulher", "A Serpente", "Deus", "Todos os Homens"], 
      correctAnswer: 4
      },
      {
      question: "Segundo a Bíblia, quem foi a primeira pessoa a pecar?",
      options: ["Caim", "Adão e Eva", "Moisés", "Judas Iscariotes"],
      correctAnswer: 1
      },
      {
      question: "O que é considerado pecado, de acordo com 1 João 3:4?",
      options: ["Não ir à igreja", "Não dar dízimos", "A transgressão da lei", "Falar mal de outras pessoas"],
      correctAnswer: 2
      },
      {
      question: "Qual é a consequência do pecado, segundo Romanos 6:23?",
      options: ["A pobreza", "A morte", "A doença", "A tristeza"],
      correctAnswer: 1
      },
      {
      question: "Quem nos liberta do pecado, de acordo com a Bíblia?",
      options: ["Os profetas", "Moisés", "Jesus Cristo", "O Espírito Santo"],
      correctAnswer: 2
      },
      {
      question: "O que devemos fazer para sermos perdoados por nossos pecados, segundo 1 João 1:9?",
      options: ["Fazer sacrifícios", "Confessar os pecados", "Ajudar os pobres", "Fazer boas obras"],
      correctAnswer: 1
      },






      
      {
      question: "O que significa ser salvo na Bíblia?",  
      options: ["Ser protegido de perigos físicos", "Tornar-se um líder religioso", "Receber bênçãos materiais", "Ser liberto do pecado e da condenação eterna"],
      correctAnswer: 3
      },
      {
      question: "Quem é o único mediador entre Deus e os homens, segundo 1 Timóteo 2:5?",
      options: ["Moisés", "O Espírito Santo", "Jesus Cristo", "Os apóstolos"],
      correctAnswer: 2
      },
      {
      question: "De acordo com João 3:16, o que Deus fez para nos dar a salvação?",
      options: ["Deu Seu Filho unigênito", "Enviou anjos para nos proteger", "Prometeu riquezas aos que crerem", "Destruiu o pecado de forma instantânea"],
      correctAnswer: 0
      },
      {
      question: "O que é necessário para receber a salvação, segundo Romanos 10:9?",
      options: ["Fazer boas obras", "Confessar com a boca que Jesus é o Senhor e crer no coração que Deus o ressuscitou", "Frequentar a igreja regularmente", "Cumprir todos os mandamentos da lei de Moisés"],
      correctAnswer: 1
      },
      {
      question: "A salvação é algo que podemos conquistar por nossos próprios esforços?",
      options: ["Sim, através de boas obras", "Sim, obedecendo à lei de Moisés", "Não, é um presente de Deus pela graça, mediante a fé", "Depende da igreja que você frequenta"],
      correctAnswer: 2
      },
      {
      question: "Após receber a salvação, como devemos viver, segundo 2 Coríntios 5:17?",
      options: ["Viver como novas criaturas, com mudança de vida", "Continuar como antes", "Seguir os costumes religiosos do passado", "Viver sem preocupações, pois já estamos salvos"],
      correctAnswer: 0
      },






      


      
      {
      question: "Quem recebeu de Deus as tábuas da Lei no Monte Sinai?",
      options: ["Abraão", "Moisés", "Davi", "Noé"],
      correctAnswer: 1
      },
      {
      question: "Quantos mandamentos Deus deu nas tábuas da Lei?",
      options: ["5", "7", "10", "12"],
      correctAnswer: 2
      },
      {
      question: "Para que serviam os sacrifícios de animais na lei do Antigo Testamento?",
      options: ["Para alimentar os sacerdotes", "Para enriquecer o templo", "Para mostrar poder sobre os povos vizinhos", "Para simbolizar a expiação dos pecados"],
      correctAnswer: 3
      },
      {
      question: "Qual era o animal mais comumente usado no sacrifício pelos pecados no Antigo Testamento?",
      options: ["Cordeiro", "Pomba", "Cabra", "Boi"],
      correctAnswer: 0
      },
      {
      question: "Quem é chamado de Cordeiro de Deus que tira o pecado do mundo?",
      options: ["Moisés", "João Batista", "Jesus Cristo", "Paulo"],
      correctAnswer: 2
      },
      {
      question: "Qual foi o propósito principal das leis dadas por Deus no Antigo Testamento?",
      options: ["Enriquecer o povo de Israel", "Tornar Israel mais poderoso militarmente", "Afastar Israel dos povos vizinhos", "Demonstrar a necessidade de obediência e santidade"],
      correctAnswer: 2
      },
      {
      question: "Segundo Hebreus 10:4, por que os sacrifícios de animais não eram suficientes para tirar os pecados completamente?",
      options: ["Porque eram feitos por sacerdotes imperfeitos", "Porque o sangue de animais não podia remover pecados", "Porque eram repetidos muitas vezes", "Porque Deus rejeitou esses sacrifícios"],
      correctAnswer: 1
      },
      {
      question: "Como Jesus cumpriu a lei e os sacrifícios do Antigo Testamento?",
      options: ["Oferecendo-se como sacrifício perfeito",, "Abolindo completamente a lei", "Tornando os sacrifícios de animais permanentes", "Introduzindo novas leis para substituir as antigas"],
      correctAnswer: 0
      },









      
      
      {
      question: "Segundo a Bíblia, o que é oração?",
      options: ["Uma forma de meditação silenciosa", "Uma conversa com Deus", "Um ritual obrigatório", "Um pedido de bênçãos aos santos"],
      correctAnswer: 1
      },
      {
      question: "Qual é o modelo de oração ensinado por Jesus?",
      options: ["A oração de Davi", "A oração de Elias", "O Pai Nosso", "O Credo Apostólico"],
      correctAnswer: 2
      },
      {
      question: "Segundo 1 Tessalonicenses 5:17, como devemos orar?",
      options: ["Apenas ao amanhecer", "Apenas em momentos de necessidade", "Sem cessar", "Uma vez por semana"],
      correctAnswer: 2
      },
      {
      question: "Qual é a atitude correta durante a oração, de acordo com Mateus 6:5-6?",
      options: ["Orar em secreto, para o Pai que vê em oculto", "Orar em público para que todos vejam", "Repetir muitas palavras para convencer Deus", "Permanecer em silêncio total"],
      correctAnswer: 0
      },
      {
      question: "Quem intercede por nós em oração, segundo Romanos 8:26?",
      options: ["Os anjos", "Os apóstolos", "O Espírito Santo", "Os profetas"],
      correctAnswer: 2
      },
      {
      question: "De acordo com Tiago 5:16, qual é o poder da oração do justo?",
      options: ["Fazer chover no deserto", "Resolver todos os problemas imediatamente", "Garantir riquezas", "Curar os doentes e ser eficaz"],
      correctAnswer: 3
      },
      {
      question: "Por que Jesus orava frequentemente, mesmo sendo o Filho de Deus?",
      options: ["Para mostrar um exemplo aos discípulos", "Para demonstrar humildade e dependência de Deus", "Para buscar força e comunhão com o Pai", "Todas as alternativas acima"],
      correctAnswer: 3
      },
      {
      question: "Qual oração Jesus fez por seus inimigos enquanto estava na cruz?",
      options: ["Perdoa-lhes, pois não sabem o que fazem", "Que sejam amaldiçoados", "Por que me abandonaste?", "Venha o teu Reino"],
      correctAnswer: 0
      },






      
      {
      question: "O que é jejum, segundo a Bíblia?",
      options: ["Uma forma de purificação física", "Abstenção de alimentos para buscar a Deus", "Um ritual obrigatório para todos os crentes", "Uma forma de disciplina física para perder peso"],
      correctAnswer: 1
      },
      {
      question: "Qual foi o propósito do jejum de Jesus no deserto?",
      options: ["Ganhar força física", "Cumprir um ritual judaico", "Mostrar ao diabo seu poder", "Buscar poder espiritual e resistir à tentação"],
      correctAnswer: 3
      },
      {
      question: "Como devemos jejuar, de acordo com Mateus 6:16-18?",
      options: ["Tornando nosso jejum visível para todos", "Reclamando sobre a fome para demonstrar sacrifício", "Com uma aparência alegre e sem alarde", "Apenas quando estamos em situações de emergência"],
      correctAnswer: 2
      },
      {
      question: "Por quanto tempo Moisés jejuou no Monte Sinai enquanto recebia a Lei de Deus?",
      options: ["3 dias e 3 noites", "21 dias e 21 noite", "40 dias e 40 noites", "7 dias e 7 noites"],
      correctAnswer: 2
      },
      {
      question: "Qual foi o jejum realizado por Ester e o povo judeu?",
      options: ["3 dias e 3 noites sem comer nem beber", "7 dias comendo apenas pão e água", "40 dias de abstenção parcial", "Apenas durante o período da manhã"],
      correctAnswer: 0
      },
      {
      question: "De acordo com Isaías 58:6, qual é o propósito do jejum que agrada a Deus?",
      options: ["Libertar os oprimidos, quebrar jugos e praticar justiça", "Demonstrar superioridade espiritual", "Reforçar a tradição religiosa", "Mostrar arrependimento ao público"],
      correctAnswer: 0
      },
      {
      question: "Quem declarou um jejum coletivo para buscar a proteção de Deus antes de enfrentar uma grande batalha?",
      options: ["Josué", "Neemias", "Jeosafá", "Gideão"],
      correctAnswer: 2
      },
      {
      question: "Qual foi o jejum realizado por Daniel?",
      options: ["Abstinência total de alimentos por 40 dias", "Consumo apenas de legumes, frutas e água", "Jejum de pão e carne por 7 dias", "Apenas abstinência de água"],
      correctAnswer: 1
      },
      {
      question: "Segundo Joel 2:12, o jejum deve ser acompanhado de qual atitude?",
      options: ["Arrependimento sincero e busca por Deus de todo o coração", "Alegria e celebração", "Uma oferta especial no templo", "Reuniões públicas de oração"],
      correctAnswer: 0
      },






      
      {
      question: "O que Jesus ensinou sobre quantas vezes devemos perdoar alguém?",
      options: ["Sete vezes", "Setenta vezes sete", "Apenas uma vez", "Depende da gravidade do erro"],
      correctAnswer: 1
      },
      {
      question: "De acordo com Mateus 6:14-15, qual é a condição para que Deus nos perdoe?",
      options: ["Fazer boas obras", "d) Não cometer mais pecados", "Jejuar regularmente", "Perdoar aqueles que nos ofendem"],
      correctAnswer: 3
      },
      {
      question: "Quem disse: Pai, perdoa-lhes, pois não sabem o que fazem?",
      options: ["Estêvão", "Pedro", "Paulo", "Jesus"],
      correctAnswer: 3
      },
      {
      question: "De acordo com 1 João 1:9, o que Deus faz quando confessamos nossos pecados?",
      options: ["Nos ignora", "Nos condena", "Nos perdoa e nos purifica de toda injustiça", "Nos dá uma segunda chance apenas se mudarmos"],
      correctAnswer: 2
      },
      {
      question: "Na parábola do servo impiedoso (Mateus 18:23-35), o que o rei fez ao servo que lhe devia muito?",
      options: ["Mandou-o para a prisão", "Perdoou toda a dívida", "Deu-lhe mais tempo para pagar", "Cobrou juros altos"],
      correctAnswer: 1
      },
      {
      question: "Qual atitude é essencial para buscar o perdão de Deus, segundo Salmos 51:17?",
      options: ["Um espírito quebrantado e um coração contrito", "Uma oferta generosa", "Realizar um jejum prolongado", "Orar publicamente"],
      correctAnswer: 0
      },
      {
      question: "O que Jesus disse sobre quem não perdoa os outros?",
      options: ["Será abençoado de outra forma", "Também não será perdoado por Deus", "Será punido diretamente", "Não enfrentará consequências"],
      correctAnswer: 1
      },
      {
      question: "Segundo Colossenses 3:13, como devemos perdoar uns aos outros?",
      options: ["Baseados no exemplo de Cristo", "Somente se houver arrependimento", "De maneira parcial" "Apenas quando somos solicitados"],
      correctAnswer: 0
      },
      {
      question: "Na história de José e seus irmãos (Gênesis 50:15-21), como José demonstrou perdão?",
      options: ["Pagou-lhes na mesma moeda", "Esqueceu o que haviam feito", "Tratou-os com bondade e viu o plano de Deus em tudo", "Recusou-se a falar com eles"],
      correctAnswer: 2
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
      
      if (code === '1234') {
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
      document.getElementById('score').textContent = 'Pontuação: 0/32';
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
