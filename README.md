<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happy Birthday Pandy!</title>
    <style>
        body {
            margin: 0;
            overflow: hidden;
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background: linear-gradient(to bottom, #87ceeb, #f0f8ff); /* Sky-like background */
        }

        .message {
            position: absolute;
            color: white;
            font-size: 3em;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
            padding: 20px;
            background: rgba(0, 0, 0, 0.3);
            border-radius: 10px;
            z-index: 2;
        }

        .balloon {
            position: absolute;
            width: 30px;
            height: 40px;
            background: red;
            border-radius: 50%;
            bottom: -60px;
            animation: floatUp 6s linear infinite, pop 6s linear infinite;
        }

        .balloon::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
            width: 2px;
            height: 30px;
            background: red;
        }

        @keyframes floatUp {
            0% { transform: translateY(0); }
            100% { transform: translateY(-100vh); }
        }

        @keyframes pop {
            90% { transform: scale(1); }
            100% { transform: scale(0); opacity: 0; }
        }
    </style>
</head>
<body>
    <div class="message">🎉 Happy Birthday Pandy! 🎉</div>

    <audio id="popSound" src="https://www.soundjay.com/button/beep-07.mp3" preload="auto"></audio> <!-- Sound effect for popping -->

    <script>
        function createBalloons(count) {
            for (let i = 0; i < count; i++) {
                const balloon = document.createElement('div');
                balloon.className = 'balloon';
                balloon.style.left = Math.random() * 100 + 'vw';
                balloon.style.animationDuration = Math.random() * 3 + 4 + 's'; // Random float speed
                document.body.appendChild(balloon);

                // Play pop sound when the balloon reaches the top and is removed
                balloon.addEventListener('animationend', () => {
                    const popSound = document.getElementById('popSound');
                    popSound.play();
                    balloon.remove();
                });
            }
        }

        // Create 20 balloons initially
        createBalloons(20);

        // Continuously generate balloons every 2 seconds
        setInterval(() => {
            createBalloons(5);
        }, 2000);
    </script>
</body>
</html>
          
