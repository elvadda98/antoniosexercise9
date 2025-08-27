<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Vocabulary Exercise: Everyday Life & Transportation</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #43cea2 0%, #185a9d 100%);
            min-height: 100vh;
            padding: 20px;
            color: #333;
        }

        .container {
            max-width: 1000px;
            margin: 0 auto;
            background: white;
            border-radius: 20px;
            box-shadow: 0 15px 35px rgba(0,0,0,0.2);
            overflow: hidden;
        }

        .header {
            background: linear-gradient(135deg, #43cea2, #185a9d);
            color: white;
            padding: 30px;
            text-align: center;
            position: relative;
        }

        .header::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"><circle cx="20" cy="20" r="2" fill="rgba(255,255,255,0.1)"/><circle cx="80" cy="30" r="1.5" fill="rgba(255,255,255,0.1)"/><circle cx="40" cy="70" r="1" fill="rgba(255,255,255,0.1)"/><circle cx="90" cy="80" r="2.5" fill="rgba(255,255,255,0.1)"/></svg>');
        }

        .header h1 {
            font-size: 2.5em;
            margin-bottom: 10px;
            position: relative;
            z-index: 1;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.2);
        }

        .header p {
            font-size: 1.2em;
            opacity: 0.9;
            position: relative;
            z-index: 1;
        }

        .nav-buttons {
            display: flex;
            justify-content: center;
            gap: 10px;
            padding: 20px;
            background: #f8f9fa;
            flex-wrap: wrap;
        }

        .nav-btn {
            padding: 12px 24px;
            border: none;
            border-radius: 25px;
            cursor: pointer;
            font-size: 16px;
            font-weight: bold;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(0,0,0,0.1);
        }

        .nav-btn.active {
            background: linear-gradient(135deg, #43cea2, #185a9d);
            color: white;
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(67,206,162,0.4);
        }

        .nav-btn:not(.active) {
            background: white;
            color: #666;
        }

        .nav-btn:hover:not(.active) {
            background: #e9ecef;
            transform: translateY(-1px);
        }

        .game-section {
            display: none;
            padding: 30px;
            min-height: 400px;
        }

        .game-section.active {
            display: block;
            animation: fadeIn 0.5s ease-in;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .word-bank {
            background: linear-gradient(135deg, #f5f7fa, #e0faf4);
            padding: 25px;
            border-radius: 15px;
            margin-bottom: 25px;
            border: 2px solid #43cea2;
            box-shadow: 0 4px 15px rgba(67,206,162,0.2);
        }

        .word-bank h3 {
            color: #2c3e50;
            margin-bottom: 15px;
            text-align: center;
            font-size: 1.4em;
        }

        .word-options {
            display: flex;
            flex-wrap: wrap;
            gap: 12px;
            justify-content: center;
        }

        .word-option {
            background: linear-gradient(135deg, #43cea2, #185a9d);
            color: white;
            padding: 10px 18px;
            border-radius: 20px;
            font-weight: bold;
            font-size: 16px;
            box-shadow: 0 3px 10px rgba(67,206,162,0.3);
            transition: all 0.3s ease;
            cursor: default;
        }

        .word-option:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(67,206,162,0.4);
        }

        .question {
            background: #f8f9fa;
            padding: 25px;
            border-radius: 15px;
            margin-bottom: 20px;
            border-left: 5px solid #43cea2;
            box-shadow: 0 4px 15px rgba(0,0,0,0.05);
        }

        .question h3 {
            color: #2c3e50;
            margin-bottom: 15px;
            font-size: 1.3em;
        }

        .fill-blank {
            background: #fff;
            border: 2px solid #ddd;
            border-radius: 8px;
            padding: 8px 12px;
            font-size: 16px;
            margin: 0 5px;
            min-width: 120px;
            transition: border-color 0.3s ease;
        }

        .fill-blank.correct {
            border-color: #4CAF50;
            background: #e8f5e8;
        }

        .fill-blank.incorrect {
            border-color: #f44336;
            background: #ffeaea;
        }

        .options {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 15px;
            margin-top: 15px;
        }

        .option {
            padding: 15px 20px;
            border: 2px solid #ddd;
            border-radius: 10px;
            cursor: pointer;
            transition: all 0.3s ease;
            background: white;
            text-align: center;
            font-weight: 500;
        }

        .option:hover {
            border-color: #43cea2;
            transform: translateY(-2px);
            box-shadow: 0 4px 15px rgba(67,206,162,0.2);
        }

        .option.selected {
            background: #43cea2;
            color: white;
            border-color: #43cea2;
        }

        .option.correct {
            background: #4CAF50;
            color: white;
            border-color: #4CAF50;
        }

        .option.incorrect {
            background: #f44336;
            color: white;
            border-color: #f44336;
        }

        .matching-container {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 30px;
            margin-top: 20px;
        }

        .match-column h4 {
            text-align: center;
            margin-bottom: 15px;
            color: #2c3e50;
            font-size: 1.2em;
        }

        .match-item {
            padding: 15px;
            margin: 8px 0;
            border: 2px solid #ddd;
            border-radius: 10px;
            cursor: pointer;
            transition: all 0.3s ease;
            background: white;
            text-align: center;
            font-weight: 500;
        }

        .match-item:hover {
            border-color: #43cea2;
            transform: translateY(-1px);
            box-shadow: 0 4px 15px rgba(67,206,162,0.2);
        }

        .match-item.selected {
            background: #e0faf4;
            border-color: #43cea2;
        }

        .match-item.matched {
            background: #4CAF50;
            color: white;
            border-color: #4CAF50;
            cursor: default;
        }

        .check-btn {
            background: linear-gradient(135deg, #43cea2, #185a9d);
            color: white;
            border: none;
            padding: 15px 30px;
            border-radius: 25px;
            cursor: pointer;
            font-size: 16px;
            font-weight: bold;
            margin: 20px auto;
            display: block;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(67,206,162,0.3);
        }

        .check-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(67,206,162,0.4);
        }

        .feedback {
            margin-top: 15px;
            padding: 15px;
            border-radius: 10px;
            font-weight: bold;
            text-align: center;
            animation: slideIn 0.3s ease;
        }

        @keyframes slideIn {
            from { transform: translateX(-20px); opacity: 0; }
            to { transform: translateX(0); opacity: 1; }
        }

        .feedback.correct {
            background: #d4edda;
            color: #155724;
            border: 1px solid #c3e6cb;
        }

        .feedback.incorrect {
            background: #f8d7da;
            color: #721c24;
            border: 1px solid #f5c6cb;
        }

        .score {
            position: fixed;
            top: 20px;
            right: 20px;
            background: linear-gradient(135deg, #43cea2, #185a9d);
            color: white;
            padding: 15px 20px;
            border-radius: 25px;
            font-weight: bold;
            box-shadow: 0 4px 15px rgba(67,206,162,0.3);
            z-index: 1000;
        }

        @media (max-width: 768px) {
            .matching-container {
                grid-template-columns: 1fr;
                gap: 20px;
            }
            
            .nav-buttons {
                flex-direction: column;
                align-items: center;
            }
            
            .nav-btn {
                width: 200px;
            }
            
            .score {
                position: static;
                margin: 20px auto;
                display: block;
                width: fit-content;
            }
        }
    </style>
</head>
<body>
    <div class="score">Score: <span id="score">0</span>/20</div>
    
    <div class="container">
        <div class="header">
            <h1>📱 Everyday Life & Transportation Vocabulary</h1>
            <p>Practice and master these useful English words!</p>
        </div>

        <div class="nav-buttons">
            <button class="nav-btn active" onclick="showSection('fill-gaps')">Fill in the Gaps</button>
            <button class="nav-btn" onclick="showSection('matching')">Match Meanings</button>
            <button class="nav-btn" onclick="showSection('multiple-choice')">Multiple Choice</button>
        </div>

        <!-- Fill in the Gaps Section -->
        <div id="fill-gaps" class="game-section active">
            <div class="word-bank">
                <h3>📝 Word Bank - Choose from these words:</h3>
                <div class="word-options">
                    <span class="word-option">quick</span>
                    <span class="word-option">screen</span>
                    <span class="word-option">middle</span>
                    <span class="word-option">replacement</span>
                    <span class="word-option">improvement</span>
                    <span class="word-option">busy</span>
                    <span class="word-option">keep</span>
                    <span class="word-option">usual</span>
                    <span class="word-option">staff</span>
                    <span class="word-option">find</span>
                    <span class="word-option">basically</span>
                    <span class="word-option">break up</span>
                </div>
            </div>

            <div class="question">
                <h3>Question 1:</h3>
                <p>I can't <input type="text" class="fill-blank" data-answer="find" placeholder="answer"> my keys anywhere; I think I might have left them at the office.</p>
                <div class="feedback" id="feedback-1" style="display: none;"></div>
            </div>

            <div class="question">
                <h3>Question 2:</h3>
                <p>The new software update is a significant <input type="text" class="fill-blank" data-answer="improvement" placeholder="answer"> over the previous version.</p>
                <div class="feedback" id="feedback-2" style="display: none;"></div>
            </div>

            <div class="question">
                <h3>Question 3:</h3>
                <p>My <input type="text" class="fill-blank" data-answer="usual" placeholder="answer"> order is a black coffee and a croissant.</p>
                <div class="feedback" id="feedback-3" style="display: none;"></div>
            </div>

            <div class="question">
                <h3>Question 4:</h3>
                <p>I need a <input type="text" class="fill-blank" data-answer="quick" placeholder="answer"> solution to this problem before the meeting starts.</p>
                <div class="feedback" id="feedback-4" style="display: none;"></div>
            </div>

            <div class="question">
                <h3>Question 5:</h3>
                <p>The committee decided to <input type="text" class="fill-blank" data-answer="break up" placeholder="answer"> the large project into smaller, more manageable tasks.</p>
                <div class="feedback" id="feedback-5" style="display: none;"></div>
            </div>

            <div class="question">
                <h3>Question 6:</h3>
                <p>We need to find a <input type="text" class="fill-blank" data-answer="replacement" placeholder="answer"> for Sarah while she's on maternity leave.</p>
                <div class="feedback" id="feedback-6" style="display: none;"></div>
            </div>

            <div class="question">
                <h3>Question 7:</h3>
                <p>I'm too <input type="text" class="fill-blank" data-answer="busy" placeholder="answer"> to meet for lunch today; maybe we can schedule for next week.</p>
                <div class="feedback" id="feedback-7" style="display: none;"></div>
            </div>

            <div class="question">
                <h3>Question 8:</h3>
                <p>The hotel <input type="text" class="fill-blank" data-answer="staff" placeholder="answer"> were very helpful when I needed directions.</p>
                <div class="feedback" id="feedback-8" style="display: none;"></div>
            </div>

            <div class="question">
                <h3>Question 9:</h3>
                <p>The phone's <input type="text" class="fill-blank" data-answer="screen" placeholder="answer"> cracked when I dropped it, so I need to get it fixed.</p>
                <div class="feedback" id="feedback-9" style="display: none;"></div>
            </div>

            <div class="question">
                <h3>Question 10:</h3>
                <p>Please <input type="text" class="fill-blank" data-answer="keep" placeholder="answer"> this information confidential until the official announcement.</p>
                <div class="feedback" id="feedback-10" style="display: none;"></div>
            </div>

            <div class="question">
                <h3>Question 11:</h3>
                <p>My seat was in the <input type="text" class="fill-blank" data-answer="middle" placeholder="answer"> of the row, so I had to ask people to move when I needed to leave.</p>
                <div class="feedback" id="feedback-11" style="display: none;"></div>
            </div>

            <div class="question">
                <h3>Question 12:</h3>
                <p><input type="text" class="fill-blank" data-answer="basically" placeholder="answer">, the plan is to meet at the station and take the train together.</p>
                <div class="feedback" id="feedback-12" style="display: none;"></div>
            </div>

            <button class="check-btn" onclick="checkFillBlanks()">Check Answers</button>
        </div>

        <!-- Matching Section -->
        <div id="matching" class="game-section">
            <h2 style="text-align: center; margin-bottom: 20px; color: #2c3e50;">Match the words with their meanings</h2>
            <div class="matching-container">
                <div class="match-column">
                    <h4>Words</h4>
                    <div class="match-item" data-word="quick" onclick="selectMatch(this)">quick</div>
                    <div class="match-item" data-word="screen" onclick="selectMatch(this)">screen</div>
                    <div class="match-item" data-word="middle" onclick="selectMatch(this)">middle</div>
                    <div class="match-item" data-word="replacement" onclick="selectMatch(this)">replacement</div>
                    <div class="match-item" data-word="improvement" onclick="selectMatch(this)">improvement</div>
                    <div class="match-item" data-word="busy" onclick="selectMatch(this)">busy</div>
                    <div class="match-item" data-word="keep" onclick="selectMatch(this)">keep</div>
                    <div class="match-item" data-word="usual" onclick="selectMatch(this)">usual</div>
                    <div class="match-item" data-word="staff" onclick="selectMatch(this)">staff</div>
                    <div class="match-item" data-word="find" onclick="selectMatch(this)">find</div>
                    <div class="match-item" data-word="basically" onclick="selectMatch(this)">basically</div>
                    <div class="match-item" data-word="break up" onclick="selectMatch(this)">break up</div>
                </div>
                <div class="match-column">
                    <h4>Meanings</h4>
                    <div class="match-item" data-meaning="screen" onclick="selectMatch(this)">the display surface of an electronic device</div>
                    <div class="match-item" data-meaning="quick" onclick="selectMatch(this)">done with speed; taking little time</div>
                    <div class="match-item" data-meaning="replacement" onclick="selectMatch(this)">a person or thing that takes the place of another</div>
                    <div class="match-item" data-meaning="improvement" onclick="selectMatch(this)">the act of making something better</div>
                    <div class="match-item" data-meaning="busy" onclick="selectMatch(this)">having a great deal to do; occupied</div>
                    <div class="match-item" data-meaning="keep" onclick="selectMatch(this)">to retain possession of; to continue in a specified condition</div>
                    <div class="match-item" data-meaning="usual" onclick="selectMatch(this)">habitually or typically occurring or done; customary</div>
                    <div class="match-item" data-meaning="staff" onclick="selectMatch(this)">all the people employed by a particular organization</div>
                    <div class="match-item" data-meaning="find" onclick="selectMatch(this)">to discover or locate something</div>
                    <div class="match-item" data-meaning="basically" onclick="selectMatch(this)">in the most essential respects; fundamentally</div>
                    <div class="match-item" data-meaning="break up" onclick="selectMatch(this)">to separate into smaller pieces; to disperse</div>
                    <div class="match-item" data-meaning="middle" onclick="selectMatch(this)">the central point or part; equidistant from the ends</div>
                </div>
            </div>
            <div class="feedback" id="matching-feedback" style="display: none;"></div>
        </div>

        <!-- Multiple Choice Section -->
        <div id="multiple-choice" class="game-section">
            <div class="question">
                <h3>Question 1: What does "quick" mean?</h3>
                <div class="options">
                    <div class="option" onclick="selectOption(this, false)">Slow and careful</div>
                    <div class="option" onclick="selectOption(this, true)">Done with speed; taking little time</div>
                    <div class="option" onclick="selectOption(this, false)">Complicated and difficult</div>
                    <div class="option" onclick="selectOption(this, false)">Expensive and luxurious</div>
                </div>
                <div class="feedback" id="mc-feedback-1" style="display: none;"></div>
            </div>

            <div class="question">
                <h3>Question 2: Which word means "the display surface of an electronic device"?</h3>
                <div class="options">
                    <div class="option" onclick="selectOption(this, false)">middle</div>
                    <div class="option" onclick="selectOption(this, false)">replacement</div>
                    <div class="option" onclick="selectOption(this, true)">screen</div>
                    <div class="option" onclick="selectOption(this, false)">improvement</div>
                </div>
                <div class="feedback" id="mc-feedback-2" style="display: none;"></div>
            </div>

            <div class="question">
                <h3>Question 3: "Break up" means:</h3>
                <div class="options">
                    <div class="option" onclick="selectOption(this, false)">To repair something</div>
                    <div class="option" onclick="selectOption(this, false)">To celebrate an event</div>
                    <div class="option" onclick="selectOption(this, true)">To separate into smaller pieces</div>
                    <div class="option" onclick="selectOption(this, false)">To build something new</div>
                </div>
                <div class="feedback" id="mc-feedback-3" style="display: none;"></div>
            </div>

            <div class="question">
                <h3>Question 4: Which word describes something that is "habitually or typically occurring"?</h3>
                <div class="options">
                    <div class="option" onclick="selectOption(this, false)">quick</div>
                    <div class="option" onclick="selectOption(this, true)">usual</div>
                    <div class="option" onclick="selectOption(this, false)">busy</div>
                    <div class="option" onclick="selectOption(this, false)">middle</div>
                </div>
                <div class="feedback" id="mc-feedback-4" style="display: none;"></div>
            </div>

            <div class="question">
                <h3>Question 5: What is an "improvement"?</h3>
                <div class="options">
                    <div class="option" onclick="selectOption(this, false)">Something that makes things worse</div>
                    <div class="option" onclick="selectOption(this, false)">A replacement part</div>
                    <div class="option" onclick="selectOption(this, true)">The act of making something better</div>
                    <div class="option" onclick="selectOption(this, false)">A busy schedule</div>
                </div>
                <div class="feedback" id="mc-feedback-5" style="display: none;"></div>
            </div>

            <div class="question">
                <h3>Question 6: Which word means "to retain possession of"?</h3>
                <div class="options">
                    <div class="option" onclick="selectOption(this, false)">find</div>
                    <div class="option" onclick="selectOption(this, true)">keep</div>
                    <div class="option" onclick="selectOption(this, false)">break up</div>
                    <div class="option" onclick="selectOption(this, false)">screen</div>
                </div>
                <div class="feedback" id="mc-feedback-6" style="display: none;"></div>
            </div>
        </div>
    </div>

    <script>
        let score = 0;
        let selectedWord = null;
        let selectedMeaning = null;
        let matchedPairs = [];

        function showSection(sectionId) {
            // Hide all sections
            document.querySelectorAll('.game-section').forEach(section => {
                section.classList.remove('active');
            });
            
            // Remove active class from all buttons
            document.querySelectorAll('.nav-btn').forEach(btn => {
                btn.classList.remove('active');
            });
            
            // Show selected section
            document.getElementById(sectionId).classList.add('active');
            
            // Add active class to clicked button
            event.target.classList.add('active');
        }

        function checkFillBlanks() {
            const blanks = document.querySelectorAll('.fill-blank');
            let correctCount = 0;
            
            blanks.forEach((blank, index) => {
                const userAnswer = blank.value.toLowerCase().trim();
                const correctAnswer = blank.dataset.answer.toLowerCase();
                
                if (userAnswer === correctAnswer) {
                    blank.classList.remove('incorrect');
                    blank.classList.add('correct');
                    correctCount++;
                } else {
                    blank.classList.remove('correct');
                    blank.classList.add('incorrect');
                }
            });
            
            // Show feedback for each question
            for (let i = 1; i <= 12; i++) {
                const feedback = document.getElementById(`feedback-${i}`);
                const blank = document.querySelectorAll('.fill-blank')[i - 1];
                
                if (blank.classList.contains('correct')) {
                    feedback.textContent = '✅ Correct!';
                    feedback.className = 'feedback correct';
                } else {
                    feedback.textContent = `❌ Incorrect. The correct answer is: "${blank.dataset.answer}"`;
                    feedback.className = 'feedback incorrect';
                }
                feedback.style.display = 'block';
            }
            
            updateScore();
        }

        function selectMatch(element) {
            if (element.classList.contains('matched')) return;
            
            if (element.dataset.word) {
                // Word selected
                if (selectedWord) selectedWord.classList.remove('selected');
                selectedWord = element;
                element.classList.add('selected');
            } else {
                // Meaning selected
                if (selectedMeaning) selectedMeaning.classList.remove('selected');
                selectedMeaning = element;
                element.classList.add('selected');
            }
            
            // Check if we have both word and meaning selected
            if (selectedWord && selectedMeaning) {
                checkMatch();
            }
        }

        function checkMatch() {
            const feedback = document.getElementById('matching-feedback');
            
            if (selectedWord.dataset.word === selectedMeaning.dataset.meaning) {
                // Correct match
                selectedWord.classList.remove('selected');
                selectedWord.classList.add('matched');
                selectedMeaning.classList.remove('selected');
                selectedMeaning.classList.add('matched');
                
                matchedPairs.push(selectedWord.dataset.word);
                
                feedback.textContent = '✅ Correct match!';
                feedback.className = 'feedback correct';
                
                // Check if all matches are complete
                if (matchedPairs.length === 12) {
                    feedback.textContent = '🎉 Congratulations! You matched all terms correctly!';
                }
            } else {
                // Incorrect match
                feedback.textContent = '❌ Incorrect match. Try again.';
                feedback.className = 'feedback incorrect';
            }
            
            feedback.style.display = 'block';
            selectedWord = null;
            selectedMeaning = null;
            
            updateScore();
        }

        function selectOption(element, isCorrect) {
            // Remove selection from all options in this question
            const options = element.parentElement.querySelectorAll('.option');
            options.forEach(opt => {
                opt.classList.remove('selected');
            });
            
            // Mark the selected option
            element.classList.add('selected');
            
            const questionNumber = element.closest('.question').querySelector('h3').textContent.match(/\d+/)[0];
            const feedback = document.getElementById(`mc-feedback-${questionNumber}`);
            
            if (isCorrect) {
                element.classList.add('correct');
                feedback.textContent = '✅ Correct!';
                feedback.className = 'feedback correct';
            } else {
                element.classList.add('incorrect');
                feedback.textContent = '❌ Incorrect. Try again.';
                feedback.className = 'feedback incorrect';
                
                // Show the correct answer
                options.forEach(opt => {
                    if (opt.onclick.toString().includes('true')) {
                        opt.classList.add('correct');
                    }
                });
            }
            
            feedback.style.display = 'block';
            updateScore();
        }

        function updateScore() {
            // Calculate score for fill-in-the-blank
            let fillScore = 0;
            document.querySelectorAll('.fill-blank.correct').forEach(blank => {
                if (!blank.classList.contains('counted')) {
                    fillScore++;
                    blank.classList.add('counted');
                }
            });
            
            // Calculate score for matching (each pair is 1 point)
            const matchScore = matchedPairs.length;
            
            // Calculate score for multiple choice (each correct is 1 point)
            let mcScore = 0;
            document.querySelectorAll('.option.correct.selected').forEach(opt => {
                mcScore++;
            });
            
            // Total score
            score = fillScore + matchScore + mcScore;
            document.getElementById('score').textContent = score;
        }
    </script>
</body>
</html>
