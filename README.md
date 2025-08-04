body {
  font-family: Arial, sans-serif;
  padding: 30px;
  background-color: #f7f7f7;
  text-align: center;
}
h1 {
  color: #333;
}
#test-text {
  font-size: 18px;
  padding: 20px;
  margin: 20px auto;
  background-color: #fff;
  max-width: 600px;
  border: 1px solid #ccc;
  border-radius: 10px;
}
#input-box {
  width: 90%;
  max-width: 600px;
  padding: 12px;
  font-size: 16px;
  margin-top: 20px;
}
#result {
  font-size: 20px;
  color: green;
  margin-top: 20px;
}
#timer {
  font-size: 18px;
  color: #d9534f;
}
#message {
  font-size: 18px;
  color: #555;
  margin-top: 15px;
  font-style: italic;
}
button {
  padding: 10px 20px;
  margin-top: 20px;
  font-size: 16px;
  cursor: pointer;
  border: none;
  background-color: #007bff;
  color: white;
  border-radius: 5px;
}

const testSentences = {
  english: [
    "Practice makes a man perfect.",
    "Typing fast needs accuracy and patience.",
    "Keep your eyes on the screen.",
    "Stay calm and focus on each word."
  ],
  hindi: [
    "अभ्यास इंसान को परिपूर्ण बनाता है।",
    "तेजी से टाइप करने के लिए सटीकता चाहिए।",
    "स्क्रीन पर नजर रखें और ध्यान केंद्रित करें।",
    "धैर्य रखो और शब्दों पर ध्यान दो।"
  ],
  marathi: [
    "सराव माणसाला परिपूर्ण बनवतो.",
    "जलद टायपिंगसाठी अचूकता आवश्यक आहे.",
    "स्क्रीनकडे पाहा आणि लक्ष केंद्रित ठेवा.",
    "धैर्य ठेवा आणि प्रत्येक शब्दावर लक्ष द्या."
  ]
};

const motivationalMessages = [
  "Great job! Keep improving every day!",
  "You're getting better — one word at a time!",
  "Progress is progress, no matter how small.",
  "Awesome effort! Keep typing and growing!",
  "Mistakes mean you're trying. Well done!"
];

let timer;
let timeLeft = 60;
let currentText = "";
let language = "english";

function startTest() {
  clearInterval(timer);
  timeLeft = 60;
  document.getElementById("result").innerText = "";
  document.getElementById("message").innerText = "";
  document.getElementById("input-box").value = "";
  const sentences = testSentences[language];
  currentText = sentences[Math.floor(Math.random() * sentences.length)];
  document.getElementById("test-text").innerText = currentText;
  document.getElementById("timer").innerText = `Time Left: ${timeLeft}s`;

  timer = setInterval(() => {
    timeLeft--;
    document.getElementById("timer").innerText = `Time Left: ${timeLeft}s`;
    if (timeLeft <= 0) {
      clearInterval(timer);
      checkResult();
    }
  }, 1000);
}

function checkResult() {
  const typed = document.getElementById("input-box").value.trim();
  const wordsTyped = typed.split(" ").filter(word => word !== "").length;
  const wpm = wordsTyped;
  const accuracy = Math.floor((compareText(typed, currentText) / currentText.length) * 100);
  const randomMsg = motivationalMessages[Math.floor(Math.random() * motivationalMessages.length)];
  document.getElementById("result").innerText = `WPM: ${wpm} | Accuracy: ${accuracy}%`;
  document.getElementById("message").innerText = randomMsg;
}

function compareText(input, original) {
  let match = 0;
  for (let i = 0; i < input.length && i < original.length; i++) {
    if (input[i] === original[i]) {
      match++;
    }
  }
  return match;
}

window.onload = startTest;

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Typing Test</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>

  <h1>Typing Speed Test</h1>
  <div id="timer">Time Left: 60s</div>
  <div id="test-text"></div>
  <textarea id="input-box" placeholder="Start typing here..."></textarea>
  <div id="result"></div>
  <div id="message"></div>
  <button onclick="startTest()">Restart</button>

  <script src="script.js"></script>
</body>
</html>

const testSentences = {
  english: [
    "Practice makes a man perfect.",
    "Typing fast needs accuracy and patience.",
    "Keep your eyes on the screen.",
    "Stay calm and focus on each word."
  ],
  hindi: [
    "अभ्यास इंसान को परिपूर्ण बनाता है।",
    "तेजी से टाइप करने के लिए सटीकता चाहिए।",
    "स्क्रीन पर नजर रखें और ध्यान केंद्रित करें।",
    "धैर्य रखो और शब्दों पर ध्यान दो।"
  ],
  marathi: [
    "सराव माणसाला परिपूर्ण बनवतो.",
    "जलद टायपिंगसाठी अचूकता आवश्यक आहे.",
    "स्क्रीनकडे पाहा आणि लक्ष केंद्रित ठेवा.",
    "धैर्य ठेवा आणि प्रत्येक शब्दावर लक्ष द्या."
  ]
};

const motivationalMessages = [
  "Great job! Keep improving every day!",
  "You're getting better — one word at a time!",
  "Progress is progress, no matter how small.",
  "Awesome effort! Keep typing and growing!",
  "Mistakes mean you're trying. Well done!"
];

let timer;
let timeLeft = 60;
let currentText = "";
let language = "english";

function startTest() {
  clearInterval(timer);
  timeLeft = 60;
  document.getElementById("result").innerText = "";
  document.getElementById("message").innerText = "";
  document.getElementById("input-box").value = "";
  const sentences = testSentences[language];
  currentText = sentences[Math.floor(Math.random() * sentences.length)];
  document.getElementById("test-text").innerText = currentText;
  document.getElementById("timer").innerText = `Time Left: ${timeLeft}s`;

  timer = setInterval(() => {
    timeLeft--;
    document.getElementById("timer").innerText = `Time Left: ${timeLeft}s`;
    if (timeLeft <= 0) {
      clearInterval(timer);
      checkResult();
    }
  }, 1000);
}

function checkResult() {
  const typed = document.getElementById("input-box").value.trim();
  const wordsTyped = typed.split(" ").filter(word => word !== "").length;
  const wpm = wordsTyped;
  const accuracy = Math.floor((compareText(typed, currentText) / currentText.length) * 100);
  const randomMsg = motivationalMessages[Math.floor(Math.random() * motivationalMessages.length)];
  document.getElementById("result").innerText = `WPM: ${wpm} | Accuracy: ${accuracy}%`;
  document.getElementById("message").innerText = randomMsg;
}

function compareText(input, original) {
  let match = 0;
  for (let i = 0; i < input.length && i < original.length; i++) {
    if (input[i] === original[i]) {
      match++;
    }
  }
  return match;
}

window.onload = startTest;

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Typing Test</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>

  <h1>Typing Speed Test</h1>
  <div id="timer">Time Left: 60s</div>
  <div id="test-text"></div>
  <textarea id="input-box" placeholder="Start typing here..."></textarea>
  <div id="result"></div>
  <div id="message"></div>
  <button onclick="startTest()">Restart</button>

  <script src="script.js"></script>
</body>
</html>

body {
  font-family: Arial, sans-serif;
  padding: 30px;
  background-color: #f7f7f7;
  text-align: center;
}
h1 {
  color: #333;
}
#test-text {
  font-size: 18px;
  padding: 20px;
  margin: 20px auto;
  background-color: #fff;
  max-width: 600px;
  border: 1px solid #ccc;
  border-radius: 10px;
}
#input-box {
  width: 90%;
  max-width: 600px;
  padding: 12px;
  font-size: 16px;
  margin-top: 20px;
}
#result {
  font-size: 20px;
  color: green;
  margin-top: 20px;
}
#timer {
  font-size: 18px;
  color: #d9534f;
}
#message {
  font-size: 18px;
  color: #555;
  margin-top: 15px;
  font-style: italic;
}
button {
  padding: 10px 20px;
  margin-top: 20px;
  font-size: 16px;
  cursor: pointer;
  border: none;
  background-color: #007bff;
  color: white;
  border-radius: 5px;
}
