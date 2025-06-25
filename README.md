<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Brechó Oonlinet - Atacado de Roupas</title>
  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }
    body {
      font-family: 'Arial', sans-serif;
      background-color: #fdfdfd;
      color: #333;
    }
    header {
      background-color: #111;
      color: #fff;
      padding: 20px;
      text-align: center;
    }
    nav {
      background-color: #000;
      display: flex;
      justify-content: center;
      gap: 20px;
      padding: 10px 0;
      position: sticky;
      top: 0;
      z-index: 1000;
    }
    nav a {
      color: #fff;
      text-decoration: none;
      font-weight: bold;
      text-transform: uppercase;
    }
    .hero {
      background: url('https://via.placeholder.com/1200x400') center/cover no-repeat;
      color: #fff;
      text-align: center;
      padding: 80px 20px;
    }
    .hero h1 {
      font-size: 3em;
      margin-bottom: 10px;
    }
    .hero p {
      font-size: 1.2em;
    }
    .section {
      padding: 40px 20px;
      max-width: 1200px;
      margin: auto;
    }
    .section h2 {
      margin-bottom: 20px;
      text-align: center;
    }
    .produtos {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
      gap: 20px;
    }
    .produto {
      border: 1px solid #ddd;
      padding: 15px;
      border-radius: 10px;
      background: #fff;
      text-align: center;
    }
    .produto img {
      width: 100%;
      border-radius: 10px;
    }
    .btn {
      display: inline-block;
      margin-top: 10px;
      padding: 10px 20px;
      background-color: #000;
      color: white;
      text-decoration: none;
      border-radius: 5px;
      cursor: pointer;
    }
    footer {
      background-color: #111;
      color: #fff;
      text-align: center;
      padding: 20px;
      margin-top: 40px;
    }
    #carrinho {
      position: fixed;
      bottom: 20px;
      right: 20px;
      background-color: #000;
      color: white;
      padding: 15px;
      border-radius: 50px;
      cursor: pointer;
      z-index: 999;
    }
    #lista-carrinho {
      margin-top: 20px;
      background-color: #fff;
      padding: 20px;
      border: 1px solid #ccc;
      border-radius: 10px;
    }
  </style>
</head>
<body>

  <header>
    <h1>Brechó Oonlinet</h1>
    <p>Atacado de Roupas Vintage e Exclusivas</p>
    <p>Vendedor: Flávio</p>
  </header>

  <nav>
    <a href="#catalogo">Catálogo</a>
    <a href="#como-comprar">Como Comprar</a>
    <a href="#contato">Contato</a>
  </nav>

  <section class="hero">
    <h1>Estilo retrô com preço de atacado</h1>
    <p>Garanta peças únicas para revenda com qualidade e personalidade</p>
  </section>

  <section class="section" id="catalogo">
    <h2>Catálogo</h2>
    <div class="produtos">
      <div class="produto">
        <img src="https://via.placeholder.com/300x300" alt="Jaqueta Vintage" />
        <h3>Jaqueta Nike Vintage</h3>
        <p>R$ 39,90 (mínimo 10 peças)</p>
        <button class="btn" onclick="adicionarCarrinho('Jaqueta Nike Vintage - R$ 39,90')">Adicionar ao Pedido</button>
      </div>
      <div class="produto">
        <img src="https://via.placeholder.com/300x300" alt="Camiseta Retro" />
        <h3>Camiseta Retrô</h3>
        <p>R$ 19,90 por unidade</p>
        <button class="btn" onclick="adicionarCarrinho('Camiseta Retrô - R$ 19,90')">Adicionar ao Pedido</button>
      </div>
      <div class="produto">
        <img src="https://static.champssports.com/is/image/ChampsSports/X0755001_SKP?$pdpflexf2$" alt="Air Max TN" />
        <h3>Tênis Air Max TN</h3>
        <p><s>R$ 328,00</s> <strong>R$ 150,00</strong> (promoção por unidade no atacado)</p>
        <button class="btn" onclick="adicionarCarrinho('Tênis Air Max TN - R$ 150,00')">Adicionar ao Pedido</button>
      </div>
    </div>
  </section>

  <section class="section" id="como-comprar">
    <h2>Como Comprar</h2>
    <ol>
      <li>Escolha os produtos no catálogo.</li>
      <li>Clique em "Adicionar ao Pedido".</li>
      <li>Clique no ícone de carrinho para revisar e enviar o pedido.</li>
      <li>Pagamento via Pix, Boleto ou Cartão.</li>
      <li>Envio rápido para todo o Brasil.</li>
    </ol>
  </section>

  <section class="section" id="contato">
    <h2>Contato</h2>
    <p>📱 WhatsApp: <a href="https://wa.me/5551991215716">(51) 99121-5716</a></p>
    <p>📸 Instagram: @brechooonlinet</p>
    <p>📍 São Paulo - SP</p>
  </section>

  <div id="carrinho" onclick="mostrarCarrinho()">🛒 Ver Pedido</div>
  <div class="section" id="lista-carrinho" style="display:none">
    <h2>Seu Pedido</h2>
    <ul id="itens-carrinho"></ul>
    <a class="btn" id="btn-finalizar" href="#">Finalizar Pedido via WhatsApp</a>
  </div>

  <footer>
    <p>&copy; 2025 Brechó Oonlinet - Todos os direitos reservados.</p>
  </footer>

  <script>
    let carrinho = [];
    function adicionarCarrinho(item) {
      carrinho.push(item);
      alert(item + " adicionado ao pedido!");
    }

    function mostrarCarrinho() {
      const lista = document.getElementById("itens-carrinho");
      lista.innerHTML = "";
      carrinho.forEach(item => {
        const li = document.createElement("li");
        li.textContent = item;
        lista.appendChild(li);
      });
      document.getElementById("lista-carrinho").style.display = "block";

      const textoPedido = encodeURIComponent("Olá Flávio, gostaria de fazer o seguinte pedido:\n" + carrinho.join("\n"));
      document.getElementById("btn-finalizar").href = `https://wa.me/5551991215716?text=${textoPedido}`;
    }
  </script>

</body>
</html>

