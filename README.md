# js-stopwatch

## Hosted link :- https://rohitdhawale07.github.io/js-stopwatch/

This is the projetc of creating a stopwatch by using javascript.
HTML file containes div tag and two buttons.
## HTML code 
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Stopwatch</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>

    <div id="timer">
        00:00:00</div>
    <div id="buttons">
        <button id="start">Start</button>
        <button id="stop">Stop</button>
        <button id="reset">Reset</button>
    </div>
    <script src="index.js"></script>
</body>
</html>
```
## CSS code
```
body {
    background-color: #c7c5c5;
    display: flex;
    flex-direction: column;
    justify-content: center;
    min-height: 100vh;
    overflow: hidden;
    align-items: center;
  }
  
  #timer {
    font-size:5rem;
    font-weight: 700;
    color: #0d2c03;
    width: 600px;
    text-align: center;
    margin: 40px auto;
  }
  
  #buttons {
    display: flex;
    justify-content: center;
  }
  
  button {
    background-color: #353809;
    color: white;
    border: none;
    font-size: 1.5rem;
    font-weight: bold;
    padding: 1.5rem 3rem;
    margin: 1rem;
    border-radius: 20px;
    cursor: pointer;
    box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.3);
  }
  
  button:hover {
    background-color: #aff390;
    color: black;
  }
 ```
## JAVASCRIPT code
```
const timer = document.getElementById("timer");
const startButton = document.getElementById("start");
const stopButton = document.getElementById("stop");
const resetButton = document.getElementById("reset");

let startTime = 0;
let elapsedTime = 0;
let timerInterval;

function startTimer() {
  startTime = Date.now() - elapsedTime;

  timerInterval = setInterval(() => {
    elapsedTime = Date.now() - startTime;
    timer.textContent = formatTime(elapsedTime);
  }, 10);

  startButton.disabled = true;
  stopButton.disabled = false;
}

function formatTime(elapsedTime) {
  const milliseconds = Math.floor((elapsedTime % 1000) / 10);
  const seconds = Math.floor((elapsedTime % (1000 * 60)) / 1000);
  const minutes = Math.floor((elapsedTime % (1000 * 60 * 60)) / (1000 * 60));
  const hours = Math.floor(elapsedTime / (1000 * 60 * 60));
  return (
    (hours ? (hours > 9 ? hours : "0" + hours) : "00") +
    ":" +
    (minutes ? (minutes > 9 ? minutes : "0" + minutes) : "00") +
    ":" +
    (seconds ? (seconds > 9 ? seconds : "0" + seconds) : "00") +
    "." +
    (milliseconds > 9 ? milliseconds : "0" + milliseconds)
  );
}
function stopTimer() {
  clearInterval(timerInterval);
  startButton.disabled = false;
  stopButton.disabled = true;
}
function resetTimer() {
  clearInterval(timerInterval);

  elapsedTime = 0;
  timer.textContent = "00:00:00";

  startButton.disabled = false;
  stopButton.disabled = true;
}

startButton.addEventListener("click", startTimer);
stopButton.addEventListener("click", stopTimer);
resetButton
.addEventListener("click", resetTimer);
```
