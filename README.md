# babyname.in
Baby name suggestions
<!DOCTYPE html>
<html>
<head>
  <title>Object Breaker Game</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 20px;
      background: linear-gradient(135deg, #e0f7fa, #b3e5fc, #bbdefb);
      min-height: 100vh;
      text-align: center;
    }
    
    h1 {
      color: #303f9f;
      margin-bottom: 10px;
    }
    
    .subtitle {
      color: #455a64;
      margin-bottom: 30px;
    }
    
    .stats-container {
      display: flex;
      justify-content: center;
      margin-bottom: 20px;
      flex-wrap: wrap;
    }
    
    .stat-box {
      background-color: rgba(255, 255, 255, 0.7);
      border-radius: 10px;
      padding: 10px 20px;
      margin: 0 10px 10px 10px;
      box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
    }
    
    .stat-label {
      font-size: 14px;
      color: #455a64;
    }
    
    .stat-value {
      font-size: 20px;
      font-weight: bold;
      color: #303f9f;
    }
    
    .message-box {
      background-color: rgba(255, 255, 255, 0.7);
      border-radius: 10px;
      padding: 15px;
      margin-bottom: 20px;
      box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
      font-size: 18px;
      color: #303f9f;
    }
    
    .objects-container {
      display: flex;
      justify-content: center;
      flex-wrap: wrap;
      margin-bottom: 20px;
    }
    
    .object-card {
      background-color: rgba(255, 255, 255, 0.7);
      border-radius: 10px;
      padding: 15px;
      margin: 10px;
      width: 200px;
      box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
    }
    
    .object-title {
      font-size: 18px;
      color: #303f9f;
      margin-bottom: 10px;
    }
    
    .object {
      width: 120px;
      height: 120px;
      margin: 0 auto 15px auto;
      cursor: pointer;
      transition: transform 0.1s;
    }
    
    .object:hover {
      transform: scale(1.05);
    }
    
    .object:active {
      transform: scale(0.95);
    }
    
    .building {
      background-color: #90a4ae;
      border: 2px solid #546e7a;
      border-radius: 5px;
      position: relative;
    }
    
    .building:before {
      content: '';
      position: absolute;
      top: -20px;
      left: 0;
      width: 100%;
      height: 20px;
      background-color: #ef5350;
      border-radius: 5px 5px 0 0;
    }
    
    .building-window {
      position: absolute;
      width: 20px;
      height: 20px;
      background-color: #bbdefb;
      border: 1px solid #1565c0;
    }
    
    .window1 { top: 15px; left: 15px; }
    .window2 { top: 15px; right: 15px; }
    .window3 { top: 45px; left: 15px; }
    .window4 { top: 45px; right: 15px; }
    .window5 { top: 75px; left: 15px; }
    .window6 { top: 75px; right: 15px; }
    
    .building-door {
      position: absolute;
      bottom: 0;
      left: 50%;
      transform: translateX(-50%);
      width: 30px;
      height: 40px;
      background-color: #795548;
      border-radius: 5px 5px 0 0;
    }
    
    .egg {
      background-color: #f5f5f5;
      border: 2px solid #e0e0e0;
      border-radius: 50% 50% 50% 50% / 60% 60% 40% 40%;
      position: relative;
    }
    
    .egg:before {
      content: '';
      position: absolute;
      top: 20px;
      left: 20px;
      width: 30px;
      height: 20px;
      background-color: rgba(255, 255, 255, 0.5);
      border-radius: 50%;
    }
    
    .jar {
      background-color: rgba(187, 222, 251, 0.5);
      border: 2px solid #90caf9;
      border-radius: 5px 5px 20px 20px;
      position: relative;
    }
    
    .jar:before {
      content: '';
      position: absolute;
      top: -10px;
      left: 0;
      width: 100%;
      height: 15px;
      background-color: #78909c;
      border-radius: 5px 5px 0 0;
    }
    
    .progress-container {
      width: 100%;
      height: 20px;
      background-color: #e0e0e0;
      border-radius: 10px;
      margin-bottom: 10px;
      overflow: hidden;
    }
    
    .progress-bar {
      height: 100%;
      width: 0%;
      background-color: #303f9f;
      transition: width 0.3s;
    }
    
    .click-counter {
      font-size: 14px;
      color: #455a64;
    }
    
    /* Broken states */
    .broken-building {
      background-color: #607d8b;
      transform: rotate(5deg);
    }
    
    .broken-building .building-window {
      opacity: 0.5;
    }
    
    .broken-building .window2, .broken-building .window5 {
      opacity: 0;
    }
    
    .broken-building .building-door {
      transform: translateX(-50%) rotate(15deg);
    }
    
    .broken-egg {
      background-color: #e0e0e0;
      border-top: 2px solid #e0e0e0;
      border-radius: 50% 50% 10% 10% / 60% 60% 10% 10%;
      overflow: visible;
    }
    
    .broken-egg:after {
      content: '';
      position: absolute;
      bottom: -15px;
      left: 25px;
      width: 70px;
      height: 25px;
      background-color: #fff59d;
      border-radius: 50%;
      z-index: -1;
    }
    
    .broken-jar {
      background-color: transparent;
      border: none;
      position: relative;
    }
    
    .broken-jar:after {
      content: '';
      position: absolute;
      bottom: 0;
      left: 20px;
      width: 80px;
      height: 10px;
      background-color: rgba(187, 222, 251, 0.3);
      border-radius: 50%;
    }
    
    .jar-piece {
      position: absolute;
      background-color: rgba(187, 222, 251, 0.5);
      border: 1px solid #90caf9;
    }
    
    .jar-piece1 {
      width: 40px;
      height: 30px;
      bottom: 10px;
      left: 10px;
      transform: rotate(-30deg);
      clip-path: polygon(0 0, 100% 0, 70% 100%, 30% 100%);
    }
    
    .jar-piece2 {
      width: 50px;
      height: 40px;
      bottom: 20px;
      right: 10px;
      transform: rotate(40deg);
      clip-path: polygon(0 0, 100% 0, 100% 70%, 0 100%);
    }
    
    button {
      background-color: #303f9f;
      color: white;
      border: none;
      padding: 10px 20px;
      border-radius: 5px;
      font-size: 16px;
      cursor: pointer;
      margin: 10px;
      box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
    }
    
    button:hover {
      background-color: #3949ab;
    }
    
    .footer-message {
      margin-top: 30px;
      background-color: rgba(255, 255, 255, 0.7);
      border-radius: 10px;
      padding: 15px;
      box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
    }
    
    .highlight {
      font-weight: bold;
      font-size: 18px;
      color: #303f9f;
    }
    
    .confetti {
      position: fixed;
      width: 10px;
      height: 10px;
      background-color: #f00;
      animation: fall 3s linear forwards;
    }
    
    @keyframes fall {
      to {
        transform: translateY(100vh) rotate(720deg);
      }
    }
  </style>
</head>
<body>
  <h1>Object Breaker Game</h1>
  <div class="subtitle">Click each object 100 times to break it!</div>
  
  <div class="stats-container">
    <div class="stat-box">
      <div class="stat-label">Total Clicks</div>
      <div id="total-clicks" class="stat-value">0</div>
    </div>
    <div class="stat-box">
      <div class="stat-label">Objects Broken</div>
      <div id="broken-count" class="stat-value">0/3</div>
    </div>
    <div class="stat-box">
      <div class="stat-label">Time Played</div>
      <div id="time-played" class="stat-value">00:00</div>
    </div>
  </div>
  
  <div id="message" class="message-box">
    Click each object 100 times to break it! Break all three to win!
  </div>
  
  <div class="objects-container">
    <div class="object-card">
      <div class="object-title">Building</div>
      <div id="building" class="object building">
        <div class="building-window window1"></div>
        <div class="building-window window2"></div>
        <div class="building-window window3"></div>
        <div class="building-window window4"></div>
        <div class="building-window window5"></div>
        <div class="building-window window6"></div>
        <div class="building-door"></div>
      </div>
      <div class="progress-container">
        <div id="building-progress" class="progress-bar"></div>
      </div>
      <div id="building-clicks" class="click-counter">0/100</div>
    </div>
    
    <div class="object-card">
      <div class="object-title">Egg</div>
      <div id="egg" class="object egg"></div>
      <div class="progress-container">
        <div id="egg-progress" class="progress-bar"></div>
      </div>
      <div id="egg-clicks" class="click-counter">0/100</div>
    </div>
    
    <div class="object-card">
      <div class="object-title">Glass Jar</div>
      <div id="jar" class="object jar">
        <div id="jar-piece1" class="jar-piece jar-piece1" style="display: none;"></div>
        <div id="jar-piece2" class="jar-piece jar-piece2" style="display: none;"></div>
      </div>
      <div class="progress-container">
        <div id="jar-progress" class="progress-bar"></div>
      </div>
      <div id="jar-clicks" class="click-counter">0/100</div>
    </div>
  </div>
  
  <button id="reset-button" style="display: none;">Reset Game</button>
  
  <div class="footer-message">
    <p class="highlight">Spend your time wisely!</p>
    <p id="click-count-message">You've made 0 clicks so far.</p>
    <p style="font-size: 14px; color: #546e7a;">Could have spent that time learning something new...</p>
  </div>

  <script>
    // Game variables
    let buildingClicks = 0;
    let eggClicks = 0;
    let jarClicks = 0;
    let totalClicks = 0;
    let brokenCount = 0;
    let gameStarted = false;
    let startTime;
    let timerInterval;
    
    // DOM elements
    const building = document.getElementById('building');
    const egg = document.getElementById('egg');
    const jar = document.getElementById('jar');
    const jarPiece1 = document.getElementById('jar-piece1');
    const jarPiece2 = document.getElementById('jar-piece2');
    const buildingProgress = document.getElementById('building-progress');
    const eggProgress = document.getElementById('egg-progress');
    const jarProgress = document.getElementById('jar-progress');
    const buildingClicksText = document.getElementById('building-clicks');
    const eggClicksText = document.getElementById('egg-clicks');
    const jarClicksText = document.getElementById('jar-clicks');
    const totalClicksText = document.getElementById('total-clicks');
    const brokenCountText = document.getElementById('broken-count');
    const messageBox = document.getElementById('message');
    const resetButton = document.getElementById('reset-button');
    const timePlayed = document.getElementById('time-played');
    const clickCountMessage = document.getElementById('click-count-message');
    
    // Start game timer
    function startGame() {
      if (!gameStarted) {
        gameStarted = true;
        startTime = new Date();
        timerInterval = setInterval(updateTimer, 1000);
      }
    }
    
    // Update timer display
    function updateTimer() {
      const now = new Date();
      const diff = Math.floor((now - startTime) / 1000);
      const minutes = Math.floor(diff / 60);
      const seconds = diff % 60;
      timePlayed.textContent = (minutes < 10 ? '0' + minutes : minutes) + ':' + 
                             (seconds < 10 ? '0' + seconds : seconds);
    }
    
    // Create confetti effect
    function createConfetti() {
      const colors = ['#f44336', '#2196f3', '#ffeb3b', '#4caf50', '#9c27b0'];
      
      for (let i = 0; i < 100; i++) {
        setTimeout(() => {
          const confetti = document.createElement('div');
          confetti.className = 'confetti';
          confetti.style.left = Math.random() * window.innerWidth + 'px';
          confetti.style.backgroundColor = colors[Math.floor(Math.random() * colors.length)];
          confetti.style.width = Math.random() * 10 + 5 + 'px';
          confetti.style.height = Math.random() * 10 + 5 + 'px';
          document.body.appendChild(confetti);
          
          // Remove confetti after animation
          setTimeout(() => {
            confetti.remove();
          }, 3000);
        }, i * 20);
      }
    }
    
    // Building click handler
    building.addEventListener('click', function() {
      startGame();
      
      if (buildingClicks < 100) {
        buildingClicks++;
        totalClicks++;
        
        // Update UI
        buildingProgress.style.width = buildingClicks + '%';
        buildingClicksText.textContent = buildingClicks + '/100';
        totalClicksText.textContent = totalClicks;
        clickCountMessage.textContent = 'You\'ve made ' + totalClicks + ' clicks so far.';
        
        // Check if building is broken
        if (buildingClicks >= 100 && !building.classList.contains('broken-building')) {
          building.classList.add('broken-building');
          brokenCount++;
          brokenCountText.textContent = brokenCount + '/3';
          updateMessage();
          checkGameComplete();
        }
      }
    });
    
    // Egg click handler
    egg.addEventListener('click', function() {
      startGame();
      
      if (eggClicks < 100) {
        eggClicks++;
        totalClicks++;
        
        // Update UI
        eggProgress.style.width = eggClicks + '%';
        eggClicksText.textContent = eggClicks + '/100';
        totalClicksText.textContent = totalClicks;
        clickCountMessage.textContent = 'You\'ve made ' + totalClicks + ' clicks so far.';
        
        // Check if egg is broken
        if (eggClicks >= 100 && !egg.classList.contains('broken-egg')) {
          egg.classList.add('broken-egg');
          brokenCount++;
          brokenCountText.textContent = brokenCount + '/3';
          updateMessage();
          checkGameComplete();
        }
      }
    });
    
    // Jar click handler
    jar.addEventListener('click', function() {
      startGame();
      
      if (jarClicks < 100) {
        jarClicks++;
        totalClicks++;
        
        // Update UI
        jarProgress.style.width = jarClicks + '%';
        jarClicksText.textContent = jarClicks + '/100';
        totalClicksText.textContent = totalClicks;
        clickCountMessage.textContent = 'You\'ve made ' + totalClicks + ' clicks so far.';
        
        // Check if jar is broken
        if (jarClicks >= 100 && !jar.classList.contains('broken-jar')) {
          jar.classList.add('broken-jar');
          jarPiece1.style.display = 'block';
          jarPiece2.style.display = 'block';
          brokenCount++;
          brokenCountText.textContent = brokenCount + '/3';
          updateMessage();
          checkGameComplete();
        }
      }
    });
    
    // Check if all objects are broken
    function checkGameComplete() {
      if (brokenCount === 3) {
        resetButton.style.display = 'block';
        clearInterval(timerInterval);
        messageBox.textContent = 'Congratulations! You broke all objects in ' + timePlayed.textContent + '!';
        createConfetti();
      }
    }
    
    // Update message based on game state
    function updateMessage() {
      if (brokenCount === 1) {
        messageBox.textContent = 'One down, two more to go!';
      } else if (brokenCount === 2) {
        messageBox.textContent = 'Almost there! Just one more to break!';
      }
    }
    
    // Reset button handler
    resetButton.addEventListener('click', function() {
      // Reset object clicks
      buildingClicks = 0;
      eggClicks = 0;
      jarClicks = 0;
      
      // Reset progress bars
      buildingProgress.style.width = '0%';
      eggProgress.style.width = '0%';
      jarProgress.style.width = '0%';
      
      // Reset click counters
      buildingClicksText.textContent = '0/100';
      eggClicksText.textContent = '0/100';
      jarClicksText.textContent = '0/100';
      
      // Reset broken states
      building.classList.remove('broken-building');
      egg.classList.remove('broken-egg');
      jar.classList.remove('broken-jar');
      jarPiece1.style.display = 'none';
      jarPiece2.style.display = 'none';
      
      // Reset game state
      brokenCount = 0;
      brokenCountText.textContent = '0/3';
      messageBox.textContent = 'Click each object 100 times to break it! Break all three to win!';
      resetButton.style.display = 'none';
      
      // Reset timer
      clearInterval(timerInterval);
      gameStarted = false;
      timePlayed.textContent = '00:00';
    });
  </script>
</body>
</html>
