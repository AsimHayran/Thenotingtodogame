#Hi there is noting here 
<!DOCTYPE html>
<html>
<head>
  <style>
    body {
      margin: 0;
      height: 100vh;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      background: linear-gradient(45deg, #ff6b6b, #4ecdc4);
      font-family: Arial, sans-serif;
      overflow: hidden;
    }

    .container {
      text-align: center;
      padding: 20px;
      background: rgba(255, 255, 255, 0.1);
      border-radius: 15px;
      backdrop-filter: blur(5px);
      position: relative;
      z-index: 1;
    }

    h1 {
      color: white;
      font-size: 2.5em;
      text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
      margin-bottom: 20px;
      transition: transform 0.3s;
      cursor: pointer;
    }

    h1:hover {
      transform: rotateZ(3deg);
    }

    .button {
      padding: 15px 30px;
      font-size: 1.2em;
      margin: 10px;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      transition: transform 0.3s;
      background: white;
    }

    .button:hover {
      transform: scale(1.1);
    }

    #runaway-btn {
      position: fixed;
      padding: 15px 30px;
      font-size: 1.2em;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      background: #ff4757;
      color: white;
      transition: all 0.2s ease;
      z-index: 1000;
    }

    #runaway-btn:hover {
      background: #ff6b81;
    }

    #counter {
      font-size: 3em;
      color: white;
      margin: 20px;
    }

    .floating {
      position: fixed;
      font-size: 2em;
      pointer-events: none;
      user-select: none;
      z-index: 2;
    }

    #message {
      color: white;
      font-size: 1.2em;
      margin-top: 20px;
      min-height: 1.2em;
    }

    #loading-bar {
      width: 200px;
      height: 20px;
      background: #ddd;
      border-radius: 10px;
      margin: 20px auto;
      overflow: hidden;
    }

    #loading-progress {
      width: 0%;
      height: 100%;
      background: linear-gradient(90deg, #ff0080, #ff8c00, #40e0d0);
      transition: width 0.3s;
    }

    #meaningless-text {
      color: white;
      font-size: 1em;
      margin: 10px;
      font-style: italic;
    }

    .wiggle {
      animation: wiggle 0.5s infinite;
    }

    @keyframes wiggle {
      0% { transform: rotate(0deg); }
      25% { transform: rotate(-5deg); }
      75% { transform: rotate(5deg); }
      100% { transform: rotate(0deg); }
    }

    #color-box {
      width: 50px;
      height: 50px;
      background: white;
      margin: 10px auto;
      border-radius: 5px;
      cursor: pointer;
    }

    #pet-text {
      font-size: 1.2em;
      color: white;
      margin: 10px;
      cursor: pointer;
      user-select: none;
    }
  </style>
</head>
<body>
  <button id="runaway-btn">Try to Click Me!</button>
  <div class="container">
    <h1 id="title">The Most Useless Website Ever</h1>
    <div id="counter">0</div>
    <div id="loading-bar">
      <div id="loading-progress"></div>
    </div>
    <div id="meaningless-text">Loading nothing...</div>
    <button class="button" id="pointless-button">Click for No Reason</button>
    <button class="button" id="emoji-button">Spawn Random Emoji</button>
    <button class="button" id="loading-button">Load Nothing</button>
    <button class="button" id="wiggle-button">Wiggle Everything</button>
    <div id="color-box"></div>
    <div id="pet-text">Pet me: 0 pets</div>
    <div id="message"></div>
  </div>

  <script>
    // Initialize variables
    let count = 0;
    let petCount = 0;
    let failedAttempts = 0;

    // Messages arrays
    const messages = [
      "Wow, you're really doing this?",
      "Don't you have anything better to do?",
      "Each click wastes approximately 2.3 seconds of your life",
      "This button literally does nothing important",
      "Still clicking? Impressive dedication!",
      "Fun fact: This website serves no purpose",
      "Your clicks power absolutely nothing",
      "Achievement unlocked: Maximum Pointlessness",
      "This is peak productivity right here",
      "Your manager would be so proud",
      "Clicking this counts as exercise, right?",
      "Warning: Excessive clicking may cause existential crisis"
    ];

    const loadingMessages = [
      "Loading void...",
      "Generating meaninglessness...",
      "Computing nothing...",
      "Calculating emptiness...",
      "Processing pointlessness...",
      "Optimizing uselessness...",
      "Downloading empty bytes...",
      "Installing nothing..."
    ];

    const emojis = ["🦄", "🌈", "🍕", "🎨", "🎭", "🎪", "🎡", "🎢", "🎠", "🦕", "🦖", "🦚", "🦩", "🌮", "🎪", "🎭", "🎨"];

    // Pointless counter button
    document.getElementById("pointless-button").addEventListener("click", () => {
      count++;
      document.getElementById("counter").textContent = count;
      document.getElementById("message").textContent = 
        messages[Math.floor(Math.random() * messages.length)];
    });

    // Emoji button
    document.getElementById("emoji-button").addEventListener("click", () => {
      const emoji = document.createElement("div");
      emoji.className = "floating";
      emoji.textContent = emojis[Math.floor(Math.random() * emojis.length)];
      
      emoji.style.left = Math.random() * window.innerWidth + "px";
      emoji.style.top = Math.random() * window.innerHeight + "px";
      
      document.body.appendChild(emoji);
      
      let angle = 0;
      let radius = Math.random() * 100 + 50;
      let speed = Math.random() * 2 + 1;
      
      const animate = () => {
        angle += speed;
        emoji.style.transform = `translate(${Math.cos(angle * Math.PI / 180) * radius}px, 
                                        ${Math.sin(angle * Math.PI / 180) * radius}px)`;
        
        if (angle < 720) {
          requestAnimationFrame(animate);
        } else {
          emoji.remove();
        }
      };
      
      animate();
    });

    // Loading button
    document.getElementById("loading-button").addEventListener("click", () => {
      const progress = document.getElementById("loading-progress");
      const text = document.getElementById("meaningless-text");
      progress.style.width = "0%";
      
      let width = 0;
      const interval = setInterval(() => {
        if (width >= 100) {
          clearInterval(interval);
          text.textContent = "Successfully loaded nothing!";
          setTimeout(() => {
            progress.style.width = "0%";
            text.textContent = "Loading nothing...";
          }, 1000);
        } else {
          width += 2;
          progress.style.width = width + "%";
          if (width % 20 === 0) {
            text.textContent = loadingMessages[Math.floor(Math.random() * loadingMessages.length)];
          }
        }
      }, 50);
    });

    // Wiggle button
    document.getElementById("wiggle-button").addEventListener("click", () => {
      const elements = document.querySelectorAll('.button, #counter, #message, #meaningless-text, #color-box, #pet-text');
      elements.forEach(element => {
        element.classList.add('wiggle');
        setTimeout(() => {
          element.classList.remove('wiggle');
        }, 500);
      });
    });

    // Color box
    document.getElementById("color-box").addEventListener("click", () => {
      const randomColor = '#' + Math.floor(Math.random()*16777215).toString(16);
      document.getElementById("color-box").style.backgroundColor = randomColor;
    });

    // Pet text
    document.getElementById("pet-text").addEventListener("click", (event) => {
      petCount++;
      document.getElementById("pet-text").textContent = `Pet me: ${petCount} pets`;
      
      const heart = document.createElement("div");
      heart.textContent = "💖";
      heart.style.position = "fixed";
      heart.style.left = (event.clientX - 10) + "px";
      heart.style.top = (event.clientY - 10) + "px";
      heart.style.pointerEvents = "none";
      document.body.appendChild(heart);

      let moveUp = 0;
      const animate = () => {
        moveUp += 1;
        heart.style.transform = `translateY(-${moveUp}px)`;
        heart.style.opacity = 1 - (moveUp / 100);
        
        if (moveUp < 100) {
          requestAnimationFrame(animate);
        } else {
          heart.remove();
        }
      };
      animate();
    });

    // Title color change
    document.getElementById("title").addEventListener("click", () => {
      const colors = ['#ff6b6b', '#4ecdc4', '#ffbe0b', '#ff006e', '#8338ec'];
      document.getElementById("title").style.color = colors[Math.floor(Math.random() * colors.length)];
    });

    // Runaway button
    const runawayBtn = document.getElementById('runaway-btn');

    function setRandomPosition() {
      const maxX = window.innerWidth - runawayBtn.offsetWidth;
      const maxY = window.innerHeight - runawayBtn.offsetHeight;
      const newX = Math.random() * maxX;
      const newY = Math.random() * maxY;
      runawayBtn.style.left = newX + 'px';
      runawayBtn.style.top = newY + 'px';
    }

    setRandomPosition();

    document.addEventListener('mousemove', (e) => {
      const rect = runawayBtn.getBoundingClientRect();
      const buttonCenter = {
        x: rect.left + rect.width / 2,
        y: rect.top + rect.height / 2
      };

      const mousePos = {
        x: e.clientX,
        y: e.clientY
      };

      const distance = Math.hypot(
        mousePos.x - buttonCenter.x,
        mousePos.y - buttonCenter.y
      );

      if (distance < 100) {
        setRandomPosition();
        failedAttempts++;
        runawayBtn.textContent = `Failed Attempts: ${failedAttempts}`;
      }
    });

    runawayBtn.addEventListener('click', () => {
      alert("Wow, you actually caught me! But... nothing happens. 🎉");
      setRandomPosition();
    });
  </script>
</body>
</html>
