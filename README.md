<!DOCTYPE html>
<html lang="pt">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Para Má</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            background-color: #000;
            color: #fff;
            text-align: center;
            padding: 50px;
            overflow-x: hidden;
            position: relative;
        }
        h1 {
            font-size: 2.5em;
            margin-bottom: 10px;
        }
        p {
            font-size: 1.2em;
            max-width: 600px;
            margin: 0 auto 20px;
            line-height: 1.6;
        }
        .hidden {
            display: none;
        }
        .button {
            background: #6200ea;
            color: #fff;
            border: none;
            padding: 15px 30px;
            font-size: 1.2em;
            cursor: pointer;
            border-radius: 5px;
            transition: 0.3s;
            margin: 10px;
            position: relative;
        }
        .button:hover {
            background: #3700b3;
        }
        .container {
            max-width: 800px;
            margin: auto;
            position: relative;
        }
        .section {
            margin-bottom: 50px;
            position: relative;
        }
        canvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            pointer-events: none;
        }
        .emoji {
            font-size: 2em;
            margin-bottom: 20px;
        }
        .hashtag {
            font-size: 1.5em;
            margin-top: 10px;
            color: #add8e6; /* Cor do azul claro */
        }
        .photos {
            margin-top: 30px;
        }
    </style>
</head>
<body>

    <canvas id="fireworksCanvas"></canvas>

    <div class="container">

        <!-- Perguntas antes do pedido de namoro -->
        <div class="section" id="question1">
            <div class="emoji">🤔</div>
            <h1>Má 🫶🏻, você acredita que o tempo é o maior indicador de felicidade ou os momentos vividos que realmente importam?</h1>
            <button class="button" onclick="nextQuestion('question2')">O tempo é o maior indicador</button>
            <button class="button" onclick="nextQuestion('question2')">Momentos vividos são o que importa</button>
        </div>

        <div class="section hidden" id="question2">
            <div class="emoji">💭</div>
            <h1>Qual é a sua opinião sobre o equilíbrio entre lógica e emoção na tomada de decisões?</h1>
            <button class="button" onclick="nextQuestion('question3')">Lógica deve prevalecer</button>
            <button class="button" onclick="nextQuestion('question3')">Emoção deve ser priorizada</button>
        </div>

        <div class="section hidden" id="question3">
            <div class="emoji">🔍</div>
            <h1>Você acredita que as nossas escolhas determinam o nosso destino, ou estamos apenas sendo guiados pelo acaso?</h1>
            <button class="button" onclick="nextQuestion('question4')">Escolhas determinam o destino</button>
            <button class="button" onclick="nextQuestion('question4')">O acaso é quem nos guia</button>
        </div>

        <div class="section hidden" id="question4">
            <div class="emoji">😌</div>
            <h1>Má 🫶🏻, você já se perguntou como seria sua vida sem medo das decisões que precisa tomar?</h1>
            <button class="button" onclick="nextQuestion('question5')">Sim, muitas vezes</button>
            <button class="button" onclick="nextQuestion('question5')">Não, prefiro viver com os medos</button>
        </div>

        <!-- Pergunta do Benji -->
        <div class="section hidden" id="question5">
            <div class="emoji">❓</div>
            <h1>Má 🫶🏻, o Benji já aprovou o Andy como novo membro, isso é verdade ou mentira?</h1>
            <button class="button" onclick="nextQuestion('question6')">Verdade</button>
            <button class="button" onclick="nextQuestion('question6')">Mentira</button>
        </div>

        <!-- Pergunta de suspense -->
        <div class="section hidden" id="question6">
            <div class="emoji">⏳</div>
            <h1>Preparado para a última pergunta?</h1>
            <button class="button" onclick="startSuspense()">Sim</button>
            <button class="button" onclick="startSuspense()">Claro</button>
        </div>

        <!-- Pergunta final -->
        <div class="section hidden" id="final">
            <div class="emoji">💙</div> <!-- Substituí o coração roxo por um coração azul claro -->
            <h1>Má 🫶🏻, você aceita viver uma nova história ao meu lado, deixando para trás qualquer dúvida e abraçando a felicidade?</h1>
            <button class="button" onclick="showFireworks()">Sim</button>
            <button class="button" id="noButton" onclick="moveButton()">Não</button>
        </div>

        <!-- Mensagem final -->
        <div class="section hidden" id="finalMessage">
            <h1>Então é hora de me beijar e viver os melhores momentos da vida juntos! 💙</h1> <!-- Cor do coração azul claro -->
            <div class="hashtag">#SeFudeuAgoraVoceNamora</div> <!-- A hashtag foi adicionada abaixo -->
            <div class="emoji">🎉🥳🎊💃🕺🎉🥂🎈💥🔥🤯😱😜💖</div>
            <div class="emoji">🎉🥳🎊💃🕺🎉🥂🎈💥🔥🤯😱😜💖</div>
            <div class="emoji">🎉🥳🎊💃🕺🎉🥂🎈💥🔥🤯😱😜💖</div>
        </div>

    </div>

    <script>
        function nextQuestion(nextId) {
            document.querySelector('.section:not(.hidden)').classList.add('hidden');
            document.getElementById(nextId).classList.remove('hidden');
            document.getElementById(nextId).scrollIntoView({ behavior: "smooth" });  // Rola suavemente para a nova pergunta
        }

        function startSuspense() {
            nextQuestion('final');
        }

        function showFireworks() {
            startFireworks();
            document.getElementById('finalMessage').classList.remove('hidden');
            document.getElementById('finalMessage').scrollIntoView({ behavior: "smooth" });
        }

        function moveButton() {
            let button = document.getElementById("noButton");
            let maxX = window.innerWidth - button.clientWidth - 20;
            let maxY = window.innerHeight - button.clientHeight - 20;
            let randomX = Math.floor(Math.random() * maxX);
            let randomY = Math.floor(Math.random() * maxY);
            button.style.position = "absolute";
            button.style.left = `${randomX}px`;
            button.style.top = `${randomY}px`;
        }

        const canvas = document.getElementById("fireworksCanvas");
        const ctx = canvas.getContext("2d");
        let fireworks = [];

        function resizeCanvas() {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        }

        window.addEventListener("resize", resizeCanvas);
        resizeCanvas();

        function startFireworks() {
            for (let i = 0; i < 80; i++) { // Mais fogos de artifício
                fireworks.push({
                    x: Math.random() * canvas.width,
                    y: Math.random() * canvas.height - canvas.height,
                    size: Math.random() * 5 + 3,
                    speed: Math.random() * 4 + 2,
                    color: `hsl(${Math.random() * 360}, 100%, 50%)`,
                    spread: Math.random() * 3 + 1,
                    lifetime: Math.random() * 50 + 30
                });
            }
            animateFireworks();
        }

        function animateFireworks() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            fireworks.forEach((f, i) => {
                f.y += f.speed;
                f.x += Math.sin(f.spread) * f.speed;
                f.lifetime -= 0.1;

                if (f.lifetime <= 0) {
                    fireworks.splice(i, 1);
                }

                ctx.fillStyle = f.color;
                ctx.beginPath();
                ctx.arc(f.x, f.y, f.size, 0, Math.PI * 2);
                ctx.fill();
            });
            requestAnimationFrame(animateFireworks);
        }
    </script>

</body>
</html>
