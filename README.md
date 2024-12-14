# Stopwatch<!DOCTYPE html>
Make a stopwatch using HTML
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Stopwatch</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background-color: #f4f4f9;
        }
        .stopwatch {
            text-align: center;
            background: #fff;
            padding: 20px;
            border: 2px solid #ccc;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        .time {
            font-size: 2rem;
            margin-bottom: 20px;
        }
        .buttons button {
            font-size: 1rem;
            padding: 10px 15px;
            margin: 0 5px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            background-color: #007BFF;
            color: white;
            transition: background 0.3s;
        }
        .buttons button:hover {
            background-color: #0056b3;
        }
        .buttons button:disabled {
            background-color: #ccc;
            cursor: not-allowed;
        }
    </style>
</head>
<body>
    <div class="stopwatch">
        <div class="time">00:00:00</div>
        <div class="buttons">
            <button id="start">Start</button>
            <button id="stop" disabled>Stop</button>
            <button id="reset" disabled>Reset</button>
        </div>
    </div>
    <script>
        let timer;
        let seconds = 0;
        const timeDisplay = document.querySelector('.time');
        const startButton = document.getElementById('start');
        const stopButton = document.getElementById('stop');
        const resetButton = document.getElementById('reset');
        function formatTime(seconds) {
            const hrs = String(Math.floor(seconds / 3600)).padStart(2, '0');
            const mins = String(Math.floor((seconds % 3600) / 60)).padStart(2, '0');
            const secs = String(seconds % 60).padStart(2, '0');
            return `${hrs}:${mins}:${secs}`;
        }
        function startTimer() {
            timer = setInterval(() => {
                seconds++;
                timeDisplay.textContent = formatTime(seconds);
            }, 1000);
            startButton.disabled = true;
            stopButton.disabled = false;
            resetButton.disabled = false;
        }
        function stopTimer() {
            clearInterval(timer);
            startButton.disabled = false;
            stopButton.disabled = true;
        }
        function resetTimer() {
            clearInterval(timer);
            seconds = 0;
            timeDisplay.textContent = "00:00:00";
            startButton.disabled = false;
            stopButton.disabled = true;
            resetButton.disabled = true;
        }
        startButton.addEventListener('click', startTimer);
        stopButton.addEventListener('click', stopTimer);
        resetButton.addEventListener('click', resetTimer);
    </script>
</body>
</html>

