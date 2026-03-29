<!DOCTYPE html>
<html>
<head>
  <title>Edu AI Chat</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>

<div class="app">
  <h2>📚 Edu AI Chat</h2>

  <div id="chat-box"></div>

  <div class="input-area">
    <input type="text" id="userInput" placeholder="Ask educational question...">
    <button onclick="sendMessage()">Send</button>
  </div>
</div>

<script src="script.js"></script>
</body>
</html>

body {
  font-family: Arial;
  background: #e3f2fd;
}

.app {
  max-width: 400px;
  margin: auto;
  background: white;
  padding: 10px;
  border-radius: 10px;
}

#chat-box {
  height: 400px;
  overflow-y: scroll;
  border: 1px solid #ccc;
  padding: 5px;
}

.user { color: blue; text-align: right; }
.bot { color: green; text-align: left; }

.input-area {
  display: flex;
}

input {
  flex: 1;
  padding: 8px;
}

button {
  padding: 8px;
}
function sendMessage() {
  let input = document.getElementById("userInput");
  let msg = input.value;

  if(msg === "") return;

  addMessage("You: " + msg, "user");

  let reply = getAnswer(msg);

  setTimeout(() => {
    addMessage("AI: " + reply, "bot");
  }, 500);

  input.value = "";
}

function addMessage(text, cls) {
  let chat = document.getElementById("chat-box");
  let div = document.createElement("div");
  div.className = cls;
  div.innerText = text;
  chat.appendChild(div);
  chat.scrollTop = chat.scrollHeight;
}

function getAnswer(q) {
  q = q.toLowerCase();

  if(q.includes("math")) return "Math studies numbers and calculations.";
  if(q.includes("science")) return "Science studies nature and universe.";
  if(q.includes("history")) return "History is about past events.";

  return "Only educational questions allowed 📚";
}
