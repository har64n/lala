<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>For Layba ❤️</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Georgia', serif;
            height: 100vh;
            overflow: hidden;
            background: linear-gradient(135deg, #ffd6e8 0%, #ff69b4 100%);
            position: relative;
            touch-action: manipulation;
        }

        #canvas {
            width: 100vw;
            height: 100vh;
            position: relative;
            overflow: hidden;
        }

        .star {
            position: absolute;
            border-radius: 50%;
            animation: twinkle 2s infinite alternate;
        }

        @keyframes twinkle {
            0% { opacity: 0.3; }
            100% { opacity: 1; }
        }

        .heart {
            position: absolute;
            color: #ff69b4;
            font-size: 20px;
            animation: float 4s infinite linear;
        }

        @keyframes float {
            0% {
                transform: translateY(0) translateX(0);
                opacity: 1;
            }
            100% {
                transform: translateY(-100vh) translateX(20px);
                opacity: 0;
            }
        }

        .envelope {
            position: absolute;
            left: 50%;
            top: 50%;
            transform: translate(-50%, -50%);
            width: 300px;
            height: 160px;
            cursor: pointer;
            z-index: 10;
        }

        .envelope-back {
            width: 100%;
            height: 100%;
            background: #ff9fcf;
            border-radius: 20px;
            position: absolute;
        }

        .envelope-flap {
            position: absolute;
            top: -50px;
            left: 50%;
            transform: translateX(-50%);
            width: 0;
            height: 0;
            border-left: 150px solid transparent;
            border-right: 150px solid transparent;
            border-bottom: 70px solid #ff6fb1;
            transition: transform 0.8s ease;
        }

        .envelope-front {
            position: absolute;
            bottom: 0;
            left: 50%;
            transform: translateX(-50%);
            width: 0;
            height: 0;
            border-left: 150px solid transparent;
            border-right: 150px solid transparent;
            border-top: 80px solid #ff85c2;
        }

        .envelope-seal {
            position: absolute;
            top: -40px;
            left: 50%;
            transform: translateX(-50%);
            width: 30px;
            height: 30px;
            background: #ff4da1;
            border-radius: 50%;
            border: 2px solid #ff69b4;
            transition: transform 0.8s ease;
        }

        .envelope.opened .envelope-flap,
        .envelope.opened .envelope-seal {
            transform: translateX(-50%) translateY(-60px);
        }

        .prompt {
            position: absolute;
            bottom: -80px;
            left: 50%;
            transform: translateX(-50%);
            background: #ff85c2;
            color: white;
            padding: 15px 30px;
            border-radius: 18px;
            font-weight: bold;
            font-size: 12px;
            animation: pulse 1.6s infinite;
        }

        @keyframes pulse {
            0%, 100% { background: #ff85c2; }
            50% { background: #ff6fb1; }
        }

        .letter {
            position: absolute;
            left: 50%;
            top: 150%;
            transform: translateX(-50%);
            width: 90vw;
            max-width: 500px;
            height: 80vh;
            background: white;
            border-radius: 22px;
            border: 3px solid #ff85c2;
            box-shadow: 5px 5px 15px rgba(0,0,0,0.1);
            padding: 40px 30px;
            text-align: center;
            transition: top 3s ease;
            overflow-y: auto;
            z-index: 5;
        }

        .letter.show {
            top: 10%;
        }

        .letter-text {
            font-size: 14px;
            line-height: 1.8;
            color: #4b0033;
            margin-bottom: 30px;
        }

        .choice-buttons {
            display: none;
            gap: 20px;
            justify-content: center;
            margin-top: 20px;
        }

        .choice-buttons.show {
            display: flex;
        }

        .btn {
            padding: 15px 30px;
            border-radius: 18px;
            border: 2px solid white;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .yes-btn {
            background: #ff69b4;
            color: white;
        }

        .no-btn {
            background: #cfcfcf;
            color: white;
            transition: all 0.3s ease;
        }

        .countdown {
            position: absolute;
            left: 50%;
            top: 50%;
            transform: translate(-50%, -50%);
            text-align: center;
            font-size: 20px;
            color: #ff1493;
            font-weight: bold;
            z-index: 20;
            display: none;
        }

        .countdown.show {
            display: block;
        }

        .photo-container {
            position: absolute;
            left: 50%;
            top: 50%;
            transform: translate(-50%, -50%);
            display: none;
            text-align: center;
            z-index: 15;
        }

        .photo-container.show {
            display: block;
        }

        .photo {
            max-width: 70vw;
            max-height: 60vh;
            border-radius: 15px;
            border: 10px solid white;
            box-shadow: 0 0 20px rgba(255, 105, 180, 0.5);
        }

        .final-message {
            margin-top: 20px;
            font-size: 18px;
            color: #ff1493;
            font-weight: bold;
        }

        .fade-out {
            animation: fadeOut 1s ease forwards;
        }

        @keyframes fadeOut {
            to { opacity: 0; }
        }

        /* Mobile optimizations */
        @media (max-width: 768px) {
            .envelope {
                width: 250px;
                height: 140px;
            }
            
            .letter {
                width: 95vw;
                padding: 30px 20px;
            }
            
            .letter-text {
                font-size: 13px;
            }
            
            .choice-buttons {
                flex-direction: column;
                align-items: center;
            }
            
            .btn {
                width: 120px;
            }
        }
    </style>
</head>
<body>
    <div id="canvas">
        <!-- Stars will be added by JavaScript -->
        
        <!-- Hearts will be added by JavaScript -->
        
        <!-- Envelope -->
        <div class="envelope" id="envelope">
            <div class="envelope-back"></div>
            <div class="envelope-flap"></div>
            <div class="envelope-front"></div>
            <div class="envelope-seal"></div>
            <div class="prompt">✨ CLICK ON THE ENVELOPE TO OPEN ✨</div>
        </div>

        <!-- Letter -->
        <div class="letter" id="letter">
            <div class="letter-text" id="letterText"></div>
            <div class="choice-buttons" id="choiceButtons">
                <div class="btn yes-btn" id="yesBtn">YES ❤️</div>
                <div class="btn no-btn" id="noBtn">NO 💔</div>
            </div>
        </div>

        <!-- Countdown -->
        <div class="countdown" id="countdown"></div>

        <!-- Photo -->
        <div class="photo-container" id="photoContainer">
            <img class="photo" id="photo" alt="Our Love" style="display: none;">
            <div class="final-message">💕 You are my world, Layba 💕</div>
        </div>
    </div>

    <!-- Audio -->
    <audio id="backgroundMusic" loop>
        <source src="haule_haule.mp3" type="audio/mpeg">
    </audio>

    <script>
        let opened = false;
        let countdownStarted = false;

        // Create twinkling stars
        function createStars() {
            for (let i = 0; i < 50; i++) {
                const star = document.createElement('div');
                star.className = 'star';
                star.style.left = Math.random() * 100 + 'vw';
                star.style.top = Math.random() * 100 + 'vh';
                star.style.width = Math.random() * 3 + 1 + 'px';
                star.style.height = star.style.width;
                star.style.backgroundColor = ['#fff', '#ffb6c1', '#ffc0cb'][Math.floor(Math.random() * 3)];
                star.style.animationDelay = Math.random() * 2 + 's';
                document.getElementById('canvas').appendChild(star);
            }
        }

        // Create floating hearts
        function createHeart() {
            const heart = document.createElement('div');
            heart.className = 'heart';
            heart.innerHTML = '💖';
            heart.style.left = Math.random() * 90 + 'vw';
            heart.style.top = '100vh';
            heart.style.animationDuration = (Math.random() * 3 + 4) + 's';
            document.getElementById('canvas').appendChild(heart);

            setTimeout(() => {
                if (heart.parentNode) {
                    heart.parentNode.removeChild(heart);
                }
            }, 7000);
        }

        // Create hearts periodically
        function startHeartAnimation() {
            createHeart();
            setTimeout(startHeartAnimation, Math.random() * 2000 + 1000);
        }

        // Love letter text
        const loveText = `💕 Hey meri pyari si jaan 💕

I love you and I miss you so much.

I hope this little surprise makes you smile i guess.

I know we are not talking but still I love you no matter what.

I'm sorry for the times I hurt you.

You are my heart, my peace, my forever.

Ap meri zindagi hai, mera ishq hai.

Would you be my valentine? ❤️`;

        // Type text animation
        function typeText(text, element, speed = 50) {
            let i = 0;
            element.innerHTML = '';
            
            function type() {
                if (i < text.length) {
                    element.innerHTML += text.charAt(i);
                    i++;
                    setTimeout(type, speed);
                } else {
                    setTimeout(() => {
                        document.getElementById('choiceButtons').classList.add('show');
                    }, 1000);
                }
            }
            type();
        }

        // Open envelope
        function openEnvelope() {
            if (opened) return;
            opened = true;

            const envelope = document.getElementById('envelope');
            const letter = document.getElementById('letter');
            const music = document.getElementById('backgroundMusic');

            envelope.classList.add('opened');
            
            // Try to play music (user interaction required)
            music.play().catch(e => console.log('Audio autoplay prevented'));

            setTimeout(() => {
                letter.classList.add('show');
                setTimeout(() => {
                    typeText(loveText, document.getElementById('letterText'));
                }, 1000);
            }, 1500);
        }

        // Move No button on hover/click
        function moveNoButton() {
            const noBtn = document.getElementById('noBtn');
            const maxX = window.innerWidth - 120;
            const maxY = window.innerHeight - 50;
            
            const newX = Math.random() * maxX;
            const newY = Math.random() * (maxY - 100) + 100;
            
            noBtn.style.position = 'fixed';
            noBtn.style.left = newX + 'px';
            noBtn.style.top = newY + 'px';
        }

        // Yes button clicked
        function yesClicked() {
            const letter = document.getElementById('letter');
            const countdown = document.getElementById('countdown');
            
            // Hide letter
            letter.classList.add('fade-out');
            
            setTimeout(() => {
                letter.style.display = 'none';
                countdown.classList.add('show');
                startCountdown();
            }, 1000);

            // Create celebration hearts
            for (let i = 0; i < 20; i++) {
                setTimeout(createHeart, i * 100);
            }
        }

        // Countdown
        function startCountdown() {
            const loveQuotes = [
                "💕 You are my everything 💕",
                "🌹 Meri pyari si jaan 🌹",
                "✨ You light up my world ✨",
                "💖 Forever and always 💖",
                "🦋 You make me complete 🦋",
                "🌟 My beautiful angel 🌟",
                "💝 Ready for your surprise? 💝"
            ];

            let count = 7;
            const countdownEl = document.getElementById('countdown');

            function updateCountdown() {
                if (count > 0) {
                    const quote = loveQuotes[7 - count];
                    countdownEl.innerHTML = `${quote}<br><br><span style="font-size: 40px;">${count}</span>`;
                    count--;
                    setTimeout(updateCountdown, 1000);
                } else {
                    countdownEl.classList.remove('show');
                    showPhoto();
                }
            }
            updateCountdown();
        }

        // Show photo
        function showPhoto() {
            const photoContainer = document.getElementById('photoContainer');
            const photo = document.getElementById('photo');
            
            // Try to load the image
            photo.src = 'mylove.JPG';
            photo.onload = function() {
                photo.style.display = 'block';
            };
            photo.onerror = function() {
                // If image fails to load, show fallback message
                photoContainer.innerHTML = `
                    <div style="font-size: 20px; color: #ff1493; text-align: center;">
                        💕 Image not found but I still love you 💕<br><br>
                        <small>Make sure 'mylove.JPG' is uploaded</small>
                    </div>
                `;
            };
            
            photoContainer.classList.add('show');
            
            // Create more celebration hearts
            for (let i = 0; i < 30; i++) {
                setTimeout(createHeart, i * 200);
            }
        }

        // Event listeners
        document.getElementById('envelope').addEventListener('click', openEnvelope);
        document.getElementById('yesBtn').addEventListener('click', yesClicked);
        document.getElementById('noBtn').addEventListener('click', moveNoButton);
        document.getElementById('noBtn').addEventListener('mouseenter', moveNoButton);
        document.getElementById('noBtn').addEventListener('touchstart', moveNoButton);

        // Initialize
        createStars();
        startHeartAnimation();

        // Handle music with user interaction
        document.addEventListener('click', function() {
            const music = document.getElementById('backgroundMusic');
            if (opened && music.paused) {
                music.play().catch(e => console.log('Audio play failed'));
            }
        }, { once: true });

        // Prevent zoom on double tap (iOS)
        document.addEventListener('touchend', function(event) {
            event.preventDefault();
        });
    </script>
</body>
</html>
