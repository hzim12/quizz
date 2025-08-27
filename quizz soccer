<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Quiz do Boleiro</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>

    <div class="quiz-container">
        <h1>Quiz do Boleiro</h1>
        <div id="quiz-question"></div>
        <div id="quiz-options" class="options-container"></div>
        <div class="controls">
            <button id="next-button">Próxima</button>
            <button id="restart-button" style="display:none;">Reiniciar</button>
        </div>
        <div id="quiz-score"></div>
    </div>

    <script src="script.js"></script>
</body>
</html>
body {
    font-family: Arial, sans-serif;
    background-color: #f0f2f5;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
}

.quiz-container {
    background-color: #fff;
    padding: 30px;
    border-radius: 10px;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
    width: 90%;
    max-width: 600px;
    text-align: center;
}

h1 {
    color: #333;
    margin-bottom: 20px;
}

#quiz-question {
    font-size: 1.5rem;
    color: #555;
    margin-bottom: 20px;
}

.options-container {
    display: flex;
    flex-direction: column;
    gap: 10px;
}

.option-button {
    background-color: #e0e0e0;
    color: #333;
    border: none;
    padding: 15px;
    border-radius: 8px;
    font-size: 1rem;
    cursor: pointer;
    transition: background-color 0.3s;
}

.option-button:hover {
    background-color: #d0d0d0;
}

.option-button.correct {
    background-color: #4CAF50;
    color: white;
}

.option-button.wrong {
    background-color: #F44336;
    color: white;
}

.controls {
    margin-top: 20px;
}

#next-button, #restart-button {
    background-color: #007BFF;
    color: white;
    border: none;
    padding: 12px 25px;
    border-radius: 8px;
    font-size: 1rem;
    cursor: pointer;
    transition: background-color 0.3s;
}

#next-button:hover, #restart-button:hover {
    background-color: #0056b3;
}

#quiz-score {
    font-size: 1.2rem;
    margin-top: 20px;
    color: #555;
}
const questions = [
    {
        question: "Quem é o maior artilheiro da história da Copa do Mundo?",
        options: ["Pelé", "Ronaldo Fenômeno", "Miroslav Klose", "Lionel Messi"],
        answer: "Miroslav Klose"
    },
    {
        question: "Qual seleção foi campeã da Copa do Mundo de 2014?",
        options: ["Brasil", "Alemanha", "Argentina", "Espanha"],
        answer: "Alemanha"
    },
    {
        question: "Em que ano foi realizada a primeira Copa do Mundo?",
        options: ["1930", "1950", "1938", "1926"],
        answer: "1930"
    },
    {
        question: "Qual jogador é conhecido como 'Rei do Futebol'?",
        options: ["Zico", "Cruyff", "Pelé", "Maradona"],
        answer: "Pelé"
    },
    {
        question: "Qual clube brasileiro tem mais títulos da Copa Libertadores da América?",
        options: ["São Paulo", "Palmeiras", "Santos", "Grêmio"],
        answer: "São Paulo"
    },
    {
        question: "Quem ganhou a Bola de Ouro de 2023?",
        options: ["Erling Haaland", "Kylian Mbappé", "Lionel Messi", "Vinícius Júnior"],
        answer: "Lionel Messi"
    },
    {
        question: "Qual país sediou a Copa do Mundo de 2022?",
        options: ["Catar", "Brasil", "Rússia", "África do Sul"],
        answer: "Catar"
    }
];

let currentQuestionIndex = 0;
let score = 0;

const questionElement = document.getElementById("quiz-question");
const optionsElement = document.getElementById("quiz-options");
const nextButton = document.getElementById("next-button");
const restartButton = document.getElementById("restart-button");
const scoreElement = document.getElementById("quiz-score");

function startQuiz() {
    currentQuestionIndex = 0;
    score = 0;
    nextButton.style.display = "block";
    restartButton.style.display = "none";
    scoreElement.textContent = "";
    showQuestion();
}

function showQuestion() {
    const currentQuestion = questions[currentQuestionIndex];
    questionElement.textContent = currentQuestion.question;
    optionsElement.innerHTML = "";

    currentQuestion.options.forEach(option => {
        const button = document.createElement("button");
        button.textContent = option;
        button.classList.add("option-button");
        button.addEventListener("click", () => selectOption(option, currentQuestion.answer, button));
        optionsElement.appendChild(button);
    });

    nextButton.style.display = "none";
}

function selectOption(selectedOption, correctAnswer, button) {
    if (selectedOption === correctAnswer) {
        score++;
        button.classList.add("correct");
    } else {
        button.classList.add("wrong");
        // Encontra e destaca a resposta correta
        const allButtons = document.querySelectorAll(".option-button");
        allButtons.forEach(btn => {
            if (btn.textContent === correctAnswer) {
                btn.classList.add("correct");
            }
        });
    }

    // Desabilita todos os botões após a seleção
    const allButtons = document.querySelectorAll(".option-button");
    allButtons.forEach(btn => btn.disabled = true);

    nextButton.style.display = "block";
}

function handleNextButton() {
    currentQuestionIndex++;
    if (currentQuestionIndex < questions.length) {
        showQuestion();
    } else {
        showScore();
    }
}

function showScore() {
    questionElement.textContent = "Quiz finalizado!";
    optionsElement.innerHTML = "";
    scoreElement.textContent = `Você acertou ${score} de ${questions.length} perguntas.`;
    nextButton.style.display = "none";
    restartButton.style.display = "block";
}

nextButton.addEventListener("click", handleNextButton);
restartButton.addEventListener("click", startQuiz);

startQuiz();
