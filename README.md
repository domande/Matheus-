<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Sala do Futuro - Matific JS</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #e0f7fa;
      text-align: center;
      padding: 50px;
    }

    .card {
      background-color: white;
      padding: 30px;
      border-radius: 10px;
      display: inline-block;
      box-shadow: 0 4px 8px rgba(0,0,0,0.2);
    }

    input {
      font-size: 20px;
      padding: 5px;
      width: 100px;
      text-align: center;
    }

    button {
      font-size: 18px;
      margin-top: 10px;
      padding: 10px 20px;
    }

    #resultado {
      margin-top: 20px;
      font-size: 18px;
    }
  </style>
</head>
<body>

<div class="card">
  <h1>🧠 Sala do Futuro - Matific JS</h1>
  <p><strong>Resolva o problema:</strong></p>
  <h2 id="pergunta"></h2>
  <input type="number" id="resposta" placeholder="Digite a resposta" />
  <br />
  <button onclick="verificarResposta()">Verificar</button>

  <div id="resultado"></div>
  <p>Pontuação: <span id="pontos">0</span></p>
</div>

<script>
let numero1, numero2, operacao;
let pontuacao = 0;

function gerarPergunta() {
  numero1 = Math.floor(Math.random() * 10) + 1;
  numero2 = Math.floor(Math.random() * 10) + 1;
  const operacoes = ["+", "-", "×"];
  operacao = operacoes[Math.floor(Math.random() * operacoes.length)];

  document.getElementById("pergunta").innerText = `${numero1} ${operacao} ${numero2}`;
  document.getElementById("resposta").value = "";
  document.getElementById("resultado").innerText = "";
}

function verificarResposta() {
  const respostaUsuario = parseInt(document.getElementById("resposta").value);
  let resultadoCorreto;

  switch (operacao) {
    case "+":
      resultadoCorreto = numero1 + numero2;
      break;
    case "-":
      resultadoCorreto = numero1 - numero2;
      break;
    case "×":
      resultadoCorreto = numero1 * numero2;
      break;
  }

  if (respostaUsuario === resultadoCorreto) {
    document.getElementById("resultado").innerText = "✅ Correto! Muito bem!";
    pontuacao += 1;
  } else {
    document.getElementById("resultado").innerText = `❌ Errado! A resposta certa era ${resultadoCorreto}.`;
  }

  document.getElementById("pontos").innerText = pontuacao;
  setTimeout(gerarPergunta, 2000); // Nova pergunta após 2 segundos
}

// Iniciar com uma pergunta
gerarPergunta();
</script>

</body>
</html>
