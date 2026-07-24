<!DOCTYPE html>  
<html>  
<head>  
<title>Kindergarten Sight Word Practice</title>  
  
<style>  
body{  
font-family: Arial;  
text-align:center;  
background:#f0f8ff;  
}  
  
button{  
font-size:20px;  
padding:10px 20px;  
margin:10px;  
cursor:pointer;  
}  
  
.wordButton{  
display:block;  
margin:10px auto;  
width:200px;  
}  
  
#result{  
font-size:24px;  
margin-top:20px;  
}  
</style>  
  
</head>  
  
<body>  
  
<h1>Sight Word Practice</h1>  
  
<button onclick="speakWord()">🔊 Say Word</button>  
<button onclick="speakWord()">🔁 Repeat Word</button>  
  
<div id="choices"></div>  
  
<div id="result"></div>  
  
<script>  
  
const words = ["the","and","you","it","is","go","see","we","me","my"];  
  
let currentWord = "";  
  
function newRound(){  
  
currentWord = words[Math.floor(Math.random()*words.length)];  
  
let shuffled = [...words].sort(()=>0.5-Math.random()).slice(0,3);  
  
if(!shuffled.includes(currentWord)){  
shuffled[Math.floor(Math.random()*3)] = currentWord;  
}  
  
const choicesDiv = document.getElementById("choices");  
choicesDiv.innerHTML="";  
  
shuffled.forEach(word=>{  
let btn = document.createElement("button");  
btn.className="wordButton";  
btn.innerText = word;  
btn.onclick = ()=>checkAnswer(word);  
choicesDiv.appendChild(btn);  
});  
  
speakWord();  
}  
  
function speakWord(){  
let speech = new SpeechSynthesisUtterance(currentWord);  
speech.rate = 0.8;  
speech.pitch = 1.2;  
speechSynthesis.speak(speech);  
}  
  
function checkAnswer(choice){  
if(choice === currentWord){  
document.getElementById("result").innerText="✅ Correct!";  
setTimeout(newRound,1500);  
}  
else{  
document.getElementById("result").innerText="❌ Try again!";  
}  
}  
  
newRound();  
  
</script>  
  
</body>  
</html>  
