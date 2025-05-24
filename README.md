# Kundan ka hai 

<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Cute Timer</title>
  <style>
    body {
      font-family: 'Comic Sans MS', cursive, sans-serif;
      background: linear-gradient(to bottom right, #ffe3ec, #d0f0fd);
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
      margin: 0;
      transition: background 0.3s;
    }
    h1 {
      color: #ff6f91;
      font-size: 2.5rem;
      margin-bottom: 20px;
    }
    #timer {
      font-size: 3rem;
      margin: 20px;
      color: #444;
    }
    button {
      background: #ffc2d1;
      border: none;
      padding: 12px 20px;
      margin: 5px;
      border-radius: 12px;
      font-size: 1rem;
      cursor: pointer;
      box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
      transition: all 0.2s;
    }
    button:hover {
      transform: scale(1.05);
      background: #ffb3c6;
    }
    .dark-mode {
      background: #222;
      color: white;
    }
    .dark-mode #timer {
      color: #fefefe;
    }
    .dark-mode button {
      background: #444;
      color: white;
    }
  </style>
</head>
<body>
  <h1>Cute Timer</h1>
  <div id="timer">00:00</div>
  <button onclick="startTimer()">Start</button>
  <button onclick="pauseTimer()">Pause</button>
  <button onclick="resetTimer()">Reset</button>
  <button onclick="toggleDarkMode()">Toggle Dark Mode</button><audio id="beep" src="https://actions.google.com/sounds/v1/alarms/alarm_clock.ogg"></audio>

  <script>
    let seconds = 0;
    let timer;
    let running = false;

    function updateDisplay() {
      const min = String(Math.floor(seconds / 60)).padStart(2, '0');
      const sec = String(seconds % 60).padStart(2, '0');
      document.getElementById('timer').textContent = `${min}:${sec}`;
    }

    function startTimer() {
      if (!running) {
        running = true;
        timer = setInterval(() => {
          seconds++;
          updateDisplay();
        }, 1000);
      }
    }

    function pauseTimer() {
      running = false;
      clearInterval(timer);
    }

    function resetTimer() {
      running = false;
      clearInterval(timer);
      seconds = 0;
      updateDisplay();
    }

    function toggleDarkMode() {
      document.body.classList.toggle('dark-mode');
    }

    // Optional: Beep at 60s mark
    setInterval(() => {
      if (seconds !== 0 && seconds % 60 === 0) {
        document.getElementById('beep').play();
      }
    }, 1000);
  </script></body>
</html>
