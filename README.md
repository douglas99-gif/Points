<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Site Acessível</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            max-width: 600px;
            margin: auto;
            padding: 20px;
            line-height: 1.6;
        }
        button {
            margin: 10px;
            padding: 10px;
            font-size: 16px;
            cursor: pointer;
        }
    </style>
</head>
<body>

    <h1 id="titulo">Bem-vindo ao Site Acessível</h1>
    <p id="descricao">Este site oferece suporte para Libras, pessoas idosas e cegas.</p>

    <button onclick="aumentarFonte()">Aumentar Fonte</button>
    <button onclick="lerTexto()">Ativar Leitor de Tela</button>
    <button onclick="abrirVLibras()">Ativar Libras</button>

    <script>
        // Aumentar fonte
        function aumentarFonte() {
            document.body.style.fontSize = "20px";
        }

        // Leitor de tela
        function lerTexto() {
            let texto = document.getElementById('titulo').innerText + ". " + 
                        document.getElementById('descricao').innerText;
            let msg = new SpeechSynthesisUtterance(texto);
            msg.lang = 'pt-BR';
            window.speechSynthesis.speak(msg);
        }

        // Suporte a Libras
        function abrirVLibras() {
            let script = document.createElement('script');
            script.src = "https://vlibras.gov.br/app/vlibras-plugin.js";
            script.onload = function() {
                new window.VLibras.Widget('https://vlibras.gov.br/app');
            };
            document.body.appendChild(script);
        }
    </script>

</body>
</html>
