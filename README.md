<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Avaliar paises</title>
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet" />
  <style>
    body {
      background-color: #f4f4f4;
      padding: 30px;
    }

    .container {
      max-width: 800px;
      margin: auto;
      background: #fff;
      padding: 20px;
      border-radius: 8px;
    }

    .comentario {
      background-color: #eaeaea;
      padding: 10px;
      margin-top: 10px;
      border-radius: 4px;
      position: relative;
    }

    .botoes {
      margin-top: 5px;
    }

    .menu {
      margin-bottom: 20px;
    }

    .conteudo img {
      max-width: 100%;
      border-radius: 8px;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1 class="text-center">Avaliar Paises</h1>

    <div class="menu d-flex justify-content-center gap-3">
      <button class="btn btn-primary" onclick="mudarConteudo(1)">Canadá</button>
      <button class="btn btn-success" onclick="mudarConteudo(2)">Noruega</button>
      <button class="btn btn-warning" onclick="mudarConteudo(3)">Suiça</button>
    </div>

    <!-- Container de conteúdo dinâmico -->
    <div class="conteudo text-center mb-4" id="conteudoContainer">
      <h2>Bem-vindo!</h2>
      <p>Escolha uma opção no menu para ver o conteúdo.</p>
      <img src="https://forbes.com.br/forbeslife/2024/03/6-tendencias-de-viagem-mais-surpreendentes-para-2024/" alt="Imagem padrão">
    </div>

    <input type="text" class="form-control" id="comentarioInput" placeholder="Digite sua avaliação..." />
    <button class="btn btn-dark mt-2" onclick="adicionarComentario()">Adicionar avalição</button>

    <div id="listaComentarios"></div>
  </div>

  <script>
    function adicionarComentario() {
      const input = document.getElementById("comentarioInput");
      const texto = input.value.trim();

      if (texto === "") {
        alert("Digite um comentário!");
        return;
      }

      const comentarioDiv = document.createElement("div");
      comentarioDiv.className = "comentario";

      const textoComentario = document.createElement("p");
      textoComentario.textContent = texto;

      const botoesDiv = document.createElement("div");
      botoesDiv.className = "botoes";

      const botaoEditar = document.createElement("button");
      botaoEditar.className = "btn btn-sm btn-outline-primary me-2";
      botaoEditar.textContent = "Editar";
      botaoEditar.onclick = function () {
        const novoTexto = prompt("Editar comentário:", textoComentario.textContent);
        if (novoTexto !== null && novoTexto.trim() !== "") {
          textoComentario.textContent = novoTexto.trim();
        }
      };

      const botaoRemover = document.createElement("button");
      botaoRemover.className = "btn btn-sm btn-outline-danger";
      botaoRemover.textContent = "Remover";
      botaoRemover.onclick = function () {
        comentarioDiv.remove();
      };

      botoesDiv.appendChild(botaoEditar);
      botoesDiv.appendChild(botaoRemover);

      comentarioDiv.appendChild(textoComentario);
      comentarioDiv.appendChild(botoesDiv);

      document.getElementById("listaComentarios").appendChild(comentarioDiv);

      input.value = "";
    }

    function mudarConteudo(opcao) {
      const container = document.getElementById("conteudoContainer");

      let titulo = "";
      let texto = "";
      let imagem = "";

      switch (opcao) {
        case 1:
          titulo = "Canadá";
          texto = "Esse é o melhor amigo do programador!";
          imagem = "https://imaginanaviagem.com/o-que-fazer-no-canada/";
          break;
        case 2:
          titulo = "Noruega";
          texto = "Nada como programar com essa vista...";
          imagem = "https://turismo.eurodicas.com.br/roteiro-noruega/";
          break;
        case 3:
          titulo = "Suiça";
          texto = "Hora de subir ao topo do código!";
          imagem = "https://www.dicasdeviagem.com/o-que-fazer-na-suica/";
          break;
      }

      container.innerHTML = `
        <h2>${titulo}</h2>
        <p>${texto}</p>
        <img src="${imagem}" alt="${titulo}">
      `;
    }
  </script>
</body>
</html>
