## Hi there 👋

<!--
**Raul-loja/raul-loja** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Minha Loja - Pagamento via Pix</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>

<header>
    <h1>Minha Loja</h1>
</header>

<section class="produtos">
    <h2>Produtos à Venda</h2>

    <div class="grid">
        <div class="produto">
            <img src="https://via.placeholder.com/200" alt="Produto 1">
            <h3>Produto 1</h3>
            <p class="preco">R$ 49,90</p>
            <button onclick="abrirPagamento('Produto 1', 49.90)">Comprar com Pix</button>
        </div>

        <div class="produto">
            <img src="https://via.placeholder.com/200" alt="Produto 2">
            <h3>Produto 2</h3>
            <p class="preco">R$ 89,90</p>
            <button onclick="abrirPagamento('Produto 2', 89.90)">Comprar com Pix</button>
        </div>
    </div>
</section>

<!-- Modal PIX -->
<div id="modal" class="modal">
    <div class="modal-content">
        <span onclick="fecharModal()" class="close">&times;</span>
        <h3 id="produtoTitulo"></h3>
        <p><strong>Total:</strong> R$ <span id="preco"></span></p>

        <h4>Pagamento via Pix</h4>
        <p>Use a chave Pix abaixo:</p>
        <div class="pix-box">
            <p id="chavePix">cristinaelizabeth113@gmail.com</p>
        </div>

        <p>Ou escaneie o QR Code:</p>
        <img id="qrCodePix" src="https://api.qrserver.com/v1/create-qr-code/?size=200x200&data=cristinaelizabeth113@gmail.com" alt="QR Code Pix">

        <a id="btnWhats" target="_blank" class="btn">
            Enviar comprovante no WhatsApp
        </a>
    </div>
</div>

<script src="script.js"></script>

</body>
</html>
function abrirPagamento(produto, preco) {
    document.getElementById("produtoTitulo").innerText = produto;
    document.getElementById("preco").innerText = preco.toFixed(2);

    let chave = "cristinaelizabeth113@gmail.com"; 
    document.getElementById("chavePix").innerText = chave;

    document.getElementById("qrCodePix").src =
        "https://api.qrserver.com/v1/create-qr-code/?size=200x200&data=" + chave;

    document.getElementById("btnWhats").href =
        "https://wa.me/5513997254251?text=" +
        encodeURIComponent(`Olá! Fiz o pagamento via Pix do produto: ${produto}.`);

    document.getElementById("modal").style.display = "block";
}

function fecharModal() {
    document.getElementById("modal").style.display = "none";
}
body {
    margin: 0;
    font-family: Arial, sans-serif;
    background: #f3f3f3;
}
header {
    background: #111;
    color: #fff;
    padding: 20px;
    text-align: center;
}
.produtos {
    padding: 30px;
    text-align: center;
}
.grid {
    display: flex;
    justify-content: center;
    gap: 20px;
    flex-wrap: wrap;
}
.produto {
    background: white;
    padding: 20px;
    width: 230px;
    border-radius: 10px;
    box-shadow: 0 0 10px #bbb;
}
button {
    background: #0f8f2f;
    color: white;
    padding: 10px;
    width: 100%;
    border: none;
    border-radius: 8px;
    cursor: pointer;
}
button:hover {
    background: #0c6f25;
}
.modal {
    display: none;
    position: fixed;
    z-index: 999;
    left: 0;
    top: 0;
    height: 100%;
    width: 100%;
    background: rgba(0,0,0,0.7);
}
.modal-content {
    background: white;
    margin: 10% auto;
    padding: 20px;
    width: 350px;
    border-radius: 10px;
}
.close {
    float: right;
    cursor: pointer;
    font-size: 22px;
}
.pix-box {
    background: #eee;
    padding: 10px;
    border-radius: 5px;
}
.btn {
    display: inline-block;
    background: #25d366;
    color: white;
    padding: 12px;
    text-align: center;
    border-radius: 8px;
    text-decoration: none;
    margin-top: 10px;
}
