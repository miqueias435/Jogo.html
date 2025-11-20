# Jogo.html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta-name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Quiz Interativo - Cultura Pop</title>

    <!-- Bootstrap CSS -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet">

    <style>
        body {
            background: #f5f5f5;
        }
        header, footer {
            background: #0d6efd;
            color: white;
            padding: 15px;
            text-align: center;
        }
        .quiz-container {
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
        }
    </style>
</head>
<body>

<header>
    <h1>🎮 Quiz Interativo - Cultura Pop</h1>
</header>

<main class="container my-4">
    <section class="quiz-container">
        <h3>Responda o quiz abaixo:</h3>

        <!-- FORMULÁRIO DO QUIZ -->
        <form id="quizForm">

            <!-- PERGUNTA 1 -->
            <div class="mb-3">
                <label class="form-label"><strong>1) Quem é o protagonista de Dragon Ball?</strong></label>
                <div class="form-check">
                    <input class="form-check-input" type="radio" name="q1" value="Goku"> Goku
                </div>
                <div class="form-check">
                    <input class="form-check-input" type="radio" name="q1" value="Naruto"> Naruto
                </div>
                <div class="form-check">
                    <input class="form-check-input" type="radio" name="q1" value="Luffy"> Luffy
                </div>
            </div>

            <!-- PERGUNTA 2 -->
            <div class="mb-3">
                <label class="form-label"><strong>2) Quais desses são Vingadores?</strong></label>
                <div class="form-check">
                    <input class="form-check-input" type="checkbox" name="q2" value="Thor"> Thor
                </div>
                <div class="form-check">
                    <input class="form-check-input" type="checkbox" name="q2" value="Homem de Ferro"> Homem de Ferro
                </div>
                <div class="form-check">
                    <input class="form-check-input" type="checkbox" name="q2" value="Batman"> Batman
                </div>
            </div>

            <!-- PERGUNTA 3 -->
            <div class="mb-3">
                <label class="form-label"><strong>3) Em que ano lançou o primeiro filme dos Vingadores?</strong></label>
                <input type="number" class="form-control" name="q3" placeholder="Digite o ano">
            </div>

            <button type="submit" class="btn btn-primary w-100">Enviar Respostas</button>
        </form>

        <div id="resultado" class="mt-4"></div>

    </section>
</main>

<footer>
    Desenvolvido para atividade escolar • 2025
</footer>

<script>
    document.getElementById("quizForm").addEventListener("submit", function(event) {
        event.preventDefault();

        let pontos = 0;
        let mensagens = "";

        const q1 = document.querySelector("input[name='q1']:checked");
        if (q1 && q1.value === "Goku") {
            pontos++;
            mensagens += "<p>✔ Pergunta 1 correta!</p>";
        } else {
            mensagens += "<p>❌ Pergunta 1 incorreta.</p>";
        }

        const q2 = document.querySelectorAll("input[name='q2']:checked");
        let respostasQ2 = Array.from(q2).map(op => op.value);

        if (respostasQ2.includes("Thor") && respostasQ2.includes("Homem de Ferro") && !respostasQ2.includes("Batman")) {
            pontos++;
            mensagens += "<p>✔ Pergunta 2 correta!</p>";
        } else {
            mensagens += "<p>❌ Pergunta 2 incorreta.</p>";
        }

        const q3 = document.querySelector("input[name='q3']").value;

        if (q3 == 2012) {
            pontos++;
            mensagens += "<p>✔ Pergunta 3 correta!</p>";
        } else {
            mensagens += "<p>❌ Pergunta 3 incorreta.</p>";
        }

        document.getElementById("resultado").innerHTML = `
            <div class="alert alert-info">
                <h4>Resultado Final:</h4>
                <p><strong>Pontuação: ${pontos}/3</strong></p>
                ${mensagens}
            </div>
        `;

        if (pontos === 3) {
            const bonus = document.createElement("p");
            bonus.textContent = "🎉 Parabéns! Você acertou tudo!";
            bonus.classList.add("text-success", "fw-bold");
            document.getElementById("resultado").appendChild(bonus);
        }
    });
</script>

</body>
</html>
