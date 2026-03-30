<!DOCTYPE html>
<html lang="kk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AI & Эпигенетика: Биологиялық жасты болжау</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            background-color: #f0f4f8;
            margin: 0;
            padding: 20px;
            color: #333;
        }
        .container {
            max-width: 800px;
            margin: auto;
            background: #fff;
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }
        h1, h2 {
            color: #2c3e50;
            text-align: center;
        }
        .header-img {
            width: 100%;
            height: 300px;
            object-fit: cover;
            border-radius: 10px;
            margin-bottom: 20px;
        }
        .quiz-section {
            margin-top: 30px;
        }
        .question {
            margin-bottom: 20px;
            padding: 15px;
            border-left: 5px solid #3498db;
            background: #f9f9f9;
        }
        .options label {
            display: block;
            margin: 10px 0;
            cursor: pointer;
        }
        button {
            display: block;
            width: 100%;
            padding: 15px;
            background-color: #3498db;
            color: white;
            border: none;
            border-radius: 5px;
            font-size: 18px;
            cursor: pointer;
            transition: background 0.3s;
        }
        button:hover {
            background-color: #2980b9;
        }
        #result {
            display: none;
            margin-top: 30px;
            padding: 20px;
            background: #e8f6f3;
            border-radius: 10px;
            border: 2px solid #27ae60;
        }
        .advice {
            font-weight: bold;
            color: #27ae60;
        }
    </style>
</head>
<body>

<div class="container">
    <h1>Жасанды интеллект және Эпигенетика</h1>
    <p>Ағзаның биологиялық жасын және қартаю процесін AI арқылы болжау жүйесіне қош келдіңіз.</p>
    
    <img src="https://images.unsplash.com/photo-1507413245164-6160d8298b31?auto=format&fit=crop&w=800&q=80" alt="DNA and Technology" class="header-img">

    <div class="quiz-section" id="quiz-container">
        <h2>Биологиялық жасты анықтау сауалнамасы</h2>
        
        <form id="quizForm">
            <div class="question">
                <p>1. Тәулігіне орташа есеппен неше сағат ұйықтайсыз?</p>
                <div class="options">
                    <label><input type="radio" name="q1" value="0" required> 7-8 сағат (Норма)</label>
                    <label><input type="radio" name="q1" value="2"> 5 сағаттан аз (Төмен)</label>
                    <label><input type="radio" name="q1" value="1"> 9 сағаттан көп (Артық)</label>
                </div>
            </div>

            <div class="question">
                <p>2. Күнделікті рационыңызда көкөністер мен жемістердің мөлшері қандай?</p>
                <div class="options">
                    <label><input type="radio" name="q2" value="0"> Әр тамақтанған сайын</label>
                    <label><input type="radio" name="q2" value="1"> Күніне бір рет</label>
                    <label><input type="radio" name="q2" value="2"> Өте сирек</label>
                </div>
            </div>

            <div class="question">
                <p>3. Физикалық белсенділік (спорт) жиілігі:</p>
                <div class="options">
                    <label><input type="radio" name="q3" value="0"> Аптасына 3-5 рет</label>
                    <label><input type="radio" name="q3" value="1"> Тек жаяу жүру</label>
                    <label><input type="radio" name="q3" value="2"> Мүлдем жоқ</label>
                </div>
            </div>

            <div class="question">
                <p>4. Күйзеліс (стресс) деңгейіңізді қалай бағалайсыз?</p>
                <div class="options">
                    <label><input type="radio" name="q4" value="2"> Үнемі күйзелістемін</label>
                    <label><input type="radio" name="q4" value="1"> Орташа</label>
                    <label><input type="radio" name="q4" value="0"> Сабырлымын</label>
                </div>
            </div>

            <div class="question">
                <p>5. Экологиялық таза аймақта тұрасыз ба?</p>
                <div class="options">
                    <label><input type="radio" name="q5" value="0"> Иә</label>
                    <label><input type="radio" name="q5" value="1"> Орташа (қалалық жер)</label>
                    <label><input type="radio" name="q5" value="2"> Өндірістік аймақ</label>
                </div>
            </div>

            <button type="button" onclick="calculateResult()">AI талдауын бастау</button>
        </form>
    </div>

    <div id="result">
        <h2>Талдау нәтижесі (AI Болжамы):</h2>
        <p id="statusText"></p>
        <p class="advice" id="adviceText"></p>
        <button onclick="location.reload()" style="margin-top:20px; background:#95a5a6;">Қайта тапсыру</button>
    </div>
</div>

<script>
    function calculateResult() {
        const form = document.getElementById('quizForm');
        const formData = new FormData(form);
        let score = 0;
        let answeredQuestions = 0;

        for (let value of formData.values()) {
            score += parseInt(value);
            answeredQuestions++;
        }

        if (answeredQuestions < 5) {
            alert("Барлық сұраққа жауап беріңіз!");
            return;
        }

        document.getElementById('quiz-container').style.display = 'none';
        const resultDiv = document.getElementById('result');
        const statusText = document.getElementById('statusText');
        const adviceText = document.getElementById('adviceText');
        
        resultDiv.style.display = 'block';

        if (score <= 2) {
            statusText.innerHTML = "🎯 <b>Биологиялық жасыңыз паспортыңыздан кіші болуы мүмкін.</b> Сіздің эпигенетикалық маркерлеріңіз баяу қартаю процесін көрсетеді.";
            adviceText.innerText = "Кеңес: Қазіргі өмір салтыңызды сақтаңыз. Антиоксиданттарға бай тағамдарды тұтынуды жалғастырыңыз.";
        } else if (score <= 6) {
            statusText.innerHTML = "⚖️ <b>Биологиялық жасыңыз қалыпты деңгейде.</b> Ағзаңыз өз жасына сай қартаюда.";
            adviceText.innerText = "Кеңес: Ұйқы режимін жақсартып, күйзелісті азайтуға тырысыңыз. Бұл ДНҚ метилдену процесін оңтайландырады.";
        } else {
            statusText.innerHTML = "⚠️ <b>Қартаю процесі жеделдеген.</b> Эпигенетикалық факторлар ағзаңыздың биологиялық тозуы жоғары екенін меңзейді.";
            adviceText.innerText = "Кеңес: Шұғыл түрде физикалық белсенділікті арттырып, рационыңызды қайта қараңыз. AI жүйесі медициналық тексеруден өтуді ұсынады.";
        }
    }
</script>

</body>
</html>
