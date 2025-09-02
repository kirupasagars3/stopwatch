# stopwatch
NAME-KIRUPASAGAR S
REGISTER NUMBER-212224230126
# PROGRAM
```
# INDEX.HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Stopwatch Application</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="stopwatch-container">
        <h1 class="title">⏱️ Stopwatch</h1>
        <div class="time-display" id="timeDisplay">00 : 00 : 00</div>
        <div class="controls">
            <button class="btn start-btn" id="startBtn" onclick="startStopwatch()">Start</button>
            <button class="btn pause-btn" id="pauseBtn" onclick="pauseStopwatch()">Pause</button>
            <button class="btn reset-btn" id="resetBtn" onclick="resetStopwatch()">Reset</button>
        </div>
        <div class="status stopped" id="status">Ready to start</div>
    </div>
    <script src="script.js"></script>
</body>
</html>

# STYLE.CSS
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 20px;
}
.stopwatch-container {
    background: rgba(255, 255, 255, 0.95);
    backdrop-filter: blur(10px);
    border-radius: 20px;
    padding: 40px;
    box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
    text-align: center;
    min-width: 350px;
}
.title {
    font-size: 2rem;
    color: #333;
    margin-bottom: 30px;
    font-weight: 600;
}
.time-display {
    font-size: 3.5rem;
    font-weight: 700;
    color: #2c3e50;
    background: #f8f9fa;
    padding: 20px;
    border-radius: 15px;
    margin-bottom: 30px;
    font-family: 'Courier New', monospace;
    letter-spacing: 2px;
    border: 3px solid #e9ecef;
}
.controls {
    display: flex;
    gap: 15px;
    justify-content: center;
    flex-wrap: wrap;
}
.btn {
    padding: 12px 24px;
    font-size: 1.1rem;
    font-weight: 600;
    border: none;
    border-radius: 10px;
    cursor: pointer;
    transition: all 0.3s ease;
    min-width: 100px;
    text-transform: uppercase;
    letter-spacing: 1px;
}
.btn:hover {
    transform: translateY(-2px);
    box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
}
.btn:active {
    transform: translateY(0);
}
.start-btn {
    background: linear-gradient(45deg, #28a745, #20c997);
    color: white;
}
.start-btn:hover {
    background: linear-gradient(45deg, #218838, #1ba085);
}
.pause-btn {
    background: linear-gradient(45deg, #ffc107, #fd7e14);
    color: white;
}
.pause-btn:hover {
    background: linear-gradient(45deg, #e0a800, #e8630a);
}
.reset-btn {
    background: linear-gradient(45deg, #dc3545, #e83e8c);
    color: white;
}
.reset-btn:hover {
    background: linear-gradient(45deg, #c82333, #d91a72);
}
.status {
    margin-top: 20px;
    font-size: 1.1rem;
    color: #6c757d;
    font-weight: 500;
}
.running {
    color: #28a745;
}
.paused {
    color: #ffc107;
}
.stopped {
    color: #dc3545;
}
@media (max-width: 480px) {
    .stopwatch-container {
        padding: 30px 20px;
        min-width: 300px;
    }
    .time-display {
        font-size: 2.5rem;
        padding: 15px;
    }
    .controls {
        flex-direction: column;
        align-items: center;
    }
    .btn {
        width: 100%;
        max-width: 200px;
    }
}

# SCRIPT.JS
let startTime = 0
let elapsedTime = 0
let timerInterval = null
let isRunning = false

const timeDisplay = document.getElementById('timeDisplay')
const startBtn = document.getElementById('startBtn')
const pauseBtn = document.getElementById('pauseBtn')
const resetBtn = document.getElementById('resetBtn')
const status = document.getElementById('status')

function formatTime(milliseconds) {
    const totalMs = Math.floor(milliseconds / 10)
    const minutes = Math.floor(totalMs / 6000)
    const seconds = Math.floor((totalMs % 6000) / 100)
    const ms = totalMs % 100
    return `${minutes.toString().padStart(2, '0')} : ${seconds.toString().padStart(2, '0')} : ${ms.toString().padStart(2, '0')}`
}

function updateDisplay() {
    const currentTime = Date.now()
    elapsedTime = currentTime - startTime
    timeDisplay.textContent = formatTime(elapsedTime)
}

function startStopwatch() {
    if (!isRunning) {
        startTime = Date.now() - elapsedTime
        timerInterval = setInterval(updateDisplay, 10)
        isRunning = true
        startBtn.textContent = 'Running'
        startBtn.disabled = true
        status.textContent = 'Running...'
        status.className = 'status running'
    }
}

function pauseStopwatch() {
    if (isRunning) {
        clearInterval(timerInterval)
        isRunning = false
        startBtn.textContent = 'Resume'
        startBtn.disabled = false
        status.textContent = 'Paused'
        status.className = 'status paused'
    }
}

function resetStopwatch() {
    clearInterval(timerInterval)
    isRunning = false
    elapsedTime = 0
    timeDisplay.textContent = '00 : 00 : 00'
    startBtn.textContent = 'Start'
    startBtn.disabled = false
    status.textContent = 'Ready to start'
    status.className = 'status stopped'
}

timeDisplay.textContent = formatTime(0)
```

# OUTPUT
<img width="1919" height="1198" alt="Screenshot 2025-09-02 164153" src="https://github.com/user-attachments/assets/42d4df59-b82e-4fda-9642-f0aa5f30d9d7" />
<img width="1919" height="1199" alt="Screenshot 2025-09-02 164204" src="https://github.com/user-attachments/assets/aaa468fb-f599-4a95-a28f-c9bdf87a076f" />
<img width="1919" height="1199" alt="Screenshot 2025-09-02 164212" src="https://github.com/user-attachments/assets/3d9c9ad1-0a66-4dd5-8a37-0c7ab43c9a65" />

