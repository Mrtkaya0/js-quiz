// Quiz Uygulaması
// Quiz sorularını ve cevaplarını içeren bir dizi oluşturun
const questions = [
    {
        question: "Başkentleri neresi olan ülke hangisidir?",
        options: ["Türkiye", "İngiltere", "İtalya", "Fransa"],
        answer: "Türkiye"
    },
    {
        question: "Hangi gezegen Güneş Sistemi'ndeki en büyük gezegendir?",
        options: ["Mars", "Jüpiter", "Venüs", "Satürn"],
        answer: "Jüpiter"
    },
    {
        question: "Hangi renkler bir regenbogen'da bulunur?",
        options: ["Mavi ve Sarı", "Siyah ve Beyaz", "Kırmızı ve Yeşil", "Pembe ve Mor"],
        answer: "Kırmızı ve Yeşil"
    }
];
// Quiz uygulaması için başlangıç değişkenleri
let currentQuestion = 0;
let score = 0;
// HTML öğelerini seçme
const questionElement = document.getElementById("question");
const optionsElement = document.getElementById("options");
const scoreElement = document.getElementById("score");
// Quiz sorularını ve seçeneklerini gösterme
function showQuestion() {
    const question = questions[currentQuestion];
    questionElement.textContent = question.question;

    optionsElement.innerHTML = "";
    question.options.forEach((option) => {
        const button = document.createElement("button");
        button.textContent = option;
        button.addEventListener("click", checkAnswer);
        optionsElement.appendChild(button);
    });
}
// Cevap kontrolü
function checkAnswer(event) {
    const selectedOption = event.target.textContent;
    const correctAnswer = questions[currentQuestion].answer;

    if (selectedOption === correctAnswer) {
        score++;
    }

    currentQuestion++;

    if (currentQuestion < questions.length) {
        showQuestion();
    } else {
        showResult();
    }
}
// Sonucu gösterme
function showResult() {
    questionElement.textContent = "Quiz Tamamlandı!";
    optionsElement.innerHTML = `Puanınız: ${score} / ${questions.length}`;
}
// Quiz'i başlatma
showQuestion();
