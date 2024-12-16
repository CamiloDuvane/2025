<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Exibição de Resultados</title>
  <script src="https://www.gstatic.com/firebasejs/9.x.x/firebase-app.js"></script>
  <script src="https://www.gstatic.com/firebasejs/9.x.x/firebase-firestore.js"></script>
</head>
<body>
  <h1>Resultados do Jogo</h1>
  <table border="1">
    <thead>
      <tr>
        <th>Jogador</th>
        <th>Tipo de Jogo</th>
        <th>Pontuação</th>
        <th>Tempo Total (s)</th>
        <th>Perguntas Respondidas</th>
      </tr>
    </thead>
    <tbody id="resultsTableBody"></tbody>
  </table>

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

    // Inicializar Firebase
    const app = firebase.initializeApp(firebaseConfig);
    const db = firebase.firestore(app);

    // Função para carregar dados do Firestore e exibir na tabela
    async function loadGameResults() {
      const tableBody = document.getElementById('resultsTableBody');
      tableBody.innerHTML = ''; // Limpar conteúdo existente

      try {
        const querySnapshot = await db.collection('gameResults').get();
        querySnapshot.forEach(doc => {
          const data = doc.data();

          // Criar uma linha na tabela para cada documento
          const row = document.createElement('tr');
          row.innerHTML = `
            <td>${data.playerName || 'Desconhecido'}</td>
            <td>${data.gameType || 'N/A'}</td>
            <td>${data.score || 0}/${data.totalQuestions || 0}</td>
            <td>${data.totalTime || 0}</td>
            <td>${data.totalQuestions || 0}</td>
          `;
          tableBody.appendChild(row);
        });
      } catch (error) {
        console.error('Erro ao carregar resultados:', error);
      }
    }

    // Chamar a função para carregar os dados ao carregar a página
    loadGameResults();
  </script>
</body>
</html>
