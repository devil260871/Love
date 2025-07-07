<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Be My Valentine</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            touch-action: manipulation;
        }
        
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #ffafbd, #ffc3a0);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow: hidden;
            position: relative;
            padding: 15px;
        }
        
        .container {
            background: rgba(255, 255, 255, 0.95);
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
            padding: 30px 20px;
            text-align: center;
            width: 100%;
            max-width: 500px;
            position: relative;
            z-index: 10;
            border: 6px solid #e91e63;
            animation: pulse 2s infinite;
        }
        
        h1 {
            color: #e91e63;
            font-size: clamp(1.8rem, 6vw, 2.8rem);
            margin: 10px 0 20px;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.1);
            line-height: 1.3;
        }
        
        .message {
            color: #d81b60;
            font-size: clamp(1rem, 4vw, 1.3rem);
            margin-bottom: 25px;
            line-height: 1.6;
            padding: 0 10px;
        }
        
        .buttons-container {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 20px;
            margin: 30px 0 20px;
            position: relative;
            min-height: 70px;
        }
        
        .btn {
            padding: clamp(12px, 4vw, 15px) clamp(30px, 10vw, 40px);
            font-size: clamp(1.1rem, 4vw, 1.3rem);
            border: none;
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.3s ease;
            font-weight: bold;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
            min-width: 120px;
            z-index: 20;
        }
        
        .btn-yes {
            background: linear-gradient(to right, #4CAF50, #2E7D32);
            color: white;
            position: static;
        }
        
        .btn-no {
            background: linear-gradient(to right, #f44336, #c62828);
            color: white;
            position: absolute;
            transition: left 0.5s ease, top 0.5s ease;
        }
        
        .btn:hover, .btn:active {
            transform: translateY(-3px);
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.3);
        }
        
        .btn:active {
            transform: scale(0.98);
        }
        
        /* Decorative elements */
        .heart {
            position: absolute;
            font-size: clamp(1.5rem, 5vw, 2rem);
            color: #e91e63;
            animation: float 8s infinite ease-in-out;
            z-index: 1;
            pointer-events: none;
        }
        
        .balloon {
            position: absolute;
            width: clamp(40px, 10vw, 50px);
            height: clamp(50px, 12vw, 60px);
            border-radius: 50%;
            animation: float 10s infinite ease-in-out;
            z-index: 1;
            pointer-events: none;
        }
        
        .balloon:after {
            content: "";
            position: absolute;
            bottom: -15px;
            left: 50%;
            transform: translateX(-50%);
            height: 25px;
            width: 2px;
            background-color: rgba(255, 255, 255, 0.7);
        }
        
        .balloon.red { background: radial-gradient(circle at 30% 30%, #ff5252, #d32f2f); }
        .balloon.pink { background: radial-gradient(circle at 30% 30%, #f48fb1, #d81b60); }
        .balloon.purple { background: radial-gradient(circle at 30% 30%, #e1bee7, #7b1fa2); }
        
        /* Animations */
        @keyframes float {
            0% { transform: translateY(0) rotate(0deg); }
            50% { transform: translateY(-20px) rotate(5deg); }
            100% { transform: translateY(0) rotate(0deg); }
        }
        
        @keyframes pulse {
            0% { box-shadow: 0 0 0 0 rgba(233, 30, 99, 0.7); }
            70% { box-shadow: 0 0 0 12px rgba(233, 30, 99, 0); }
            100% { box-shadow: 0 0 0 0 rgba(233, 30, 99, 0); }
        }
        
        .confetti {
            position: absolute;
            width: 8px;
            height: 8px;
            background-color: #f44336;
            border-radius: 50%;
            animation: confetti-fall 5s linear infinite;
            z-index: 0;
            pointer-events: none;
        }
        
        @keyframes confetti-fall {
            0% { transform: translateY(-100px) rotate(0deg); }
            100% { transform: translateY(100vh) rotate(360deg); }
        }
        
        .footer {
            margin-top: 20px;
            color: #d81b60;
            font-size: clamp(0.9rem, 3.5vw, 1.1rem);
            padding: 0 10px;
        }
        
        /* Mobile-specific optimizations */
        @media (max-width: 600px) {
            .container {
                padding: 25px 15px;
                border-width: 4px;
            }
            
            .buttons-container {
                gap: 15px;
                margin: 25px 0 15px;
                min-height: 60px;
            }
            
            .btn {
                min-width: 100px;
                padding: 12px 25px;
            }
            
            .heart {
                font-size: 1.8rem;
            }
            
            .balloon {
                width: 35px;
                height: 45px;
            }
        }
        
        @media (max-width: 400px) {
            .buttons-container {
                flex-direction: column;
                align-items: center;
                min-height: 140px;
            }
            
            .btn-no {
                position: relative;
                margin-top: 10px;
            }
        }
        
        /* Touch optimization */
        .no-touch .btn-no {
            transition: none;
        }
    </style>
</head>
<body>
    <!-- Decorative elements -->
    <div class="heart" style="top: 5%; left: 5%;">❤️</div>
    <div class="heart" style="top: 15%; right: 8%;">❤️</div>
    <div class="heart" style="bottom: 12%; left: 10%;">❤️</div>
    <div class="heart" style="bottom: 20%; right: 7%;">❤️</div>
    
    <div class="balloon red" style="top: 3%; left: 3%;"></div>
    <div class="balloon pink" style="top: 10%; right: 5%;"></div>
    <div class="balloon purple" style="bottom: 8%; left: 12%;"></div>
    
    <!-- Confetti -->
    <div class="confetti" style="left: 5%; animation-delay: 0s;"></div>
    <div class="confetti" style="left: 15%; animation-delay: 1s; background-color: #e91e63;"></div>
    <div class="confetti" style="left: 25%; animation-delay: 2s; background-color: #ff9800;"></div>
    <div class="confetti" style="left: 35%; animation-delay: 3s; background-color: #4CAF50;"></div>
    <div class="confetti" style="left: 45%; animation-delay: 4s; background-color: #2196F3;"></div>
    <div class="confetti" style="left: 55%; animation-delay: 0.5s; background-color: #9C27B0;"></div>
    <div class="confetti" style="left: 65%; animation-delay: 1.5s; background-color: #FFEB3B;"></div>
    <div class="confetti" style="left: 75%; animation-delay: 2.5s; background-color: #00BCD4;"></div>
    <div class="confetti" style="left: 85%; animation-delay: 3.5s; background-color: #795548;"></div>
    <div class="confetti" style="left: 95%; animation-delay: 4.5s; background-color: #607D8B;"></div>
    
    <!-- Content container -->
    <div class="container">
        <h1>💝 Will You Be My Valentine? 💝</h1>
        
        <p class="message">
            My heart beats only for you! I cherish every moment we spend together. 
            You make my world brighter and my life more meaningful. 
        </p>
        
        <p class="message">
            Will you make me the happiest person and be my Valentine?
        </p>
        
        <div class="buttons-container">
            <button class="btn btn-yes" id="yesBtn">Yes!</button>
            <button class="btn btn-no" id="noBtn">No</button>
        </div>
        
        <p class="footer">
            You can't escape by clicking "No"! Try to catch it if you can 😉
        </p>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            const noBtn = document.getElementById('noBtn');
            const yesBtn = document.getElementById('yesBtn');
            const container = document.querySelector('.container');
            const buttonsContainer = document.querySelector('.buttons-container');
            
            // Detect touch devices
            const isTouchDevice = 'ontouchstart' in window || navigator.maxTouchPoints;
            if (!isTouchDevice) {
                document.body.classList.add('no-touch');
            }
            
            // Function to generate random position within the container
            function getRandomPosition() {
                const containerRect = buttonsContainer.getBoundingClientRect();
                const btnRect = noBtn.getBoundingClientRect();
                
                const maxX = containerRect.width - btnRect.width;
                const maxY = containerRect.height - btnRect.height;
                
                // Ensure we stay within container boundaries
                const randomX = Math.max(0, Math.min(maxX, Math.random() * maxX));
                const randomY = Math.max(0, Math.min(maxY, Math.random() * maxY));
                
                return { x: randomX, y: randomY };
            }
            
            // Move the No button
            function moveButton() {
                const newPos = getRandomPosition();
                noBtn.style.left = newPos.x + 'px';
                noBtn.style.top = newPos.y + 'px';
                
                // Add a fun effect
                noBtn.style.transform = 'scale(1.1) rotate(5deg)';
                setTimeout(() => {
                    noBtn.style.transform = '';
                }, 300);
            }
            
            // Event listeners for different device types
            if (isTouchDevice) {
                // For touch devices
                noBtn.addEventListener('touchstart', function(e) {
                    e.preventDefault();
                    moveButton();
                });
            } else {
                // For desktop devices
                noBtn.addEventListener('mouseover', function() {
                    moveButton();
                });
            }
            
            // Make the Yes button do something special
            yesBtn.addEventListener('click', function() {
                // Create hearts animation
                for (let i = 0; i < 50; i++) {
                    createFloatingHeart();
                }
                
                // Show a message
                showMessage('💖 You made my day! I love you! 💖');
            });
            
            // Function to create floating hearts
            function createFloatingHeart() {
                const heart = document.createElement('div');
                heart.innerHTML = '❤️';
                heart.classList.add('heart');
                heart.style.position = 'fixed';
                heart.style.left = Math.random() * 100 + 'vw';
                heart.style.top = '100vh';
                heart.style.fontSize = (Math.random() * 30 + 20) + 'px';
                heart.style.animation = `float ${Math.random() * 3 + 2}s ease-in forwards`;
                document.body.appendChild(heart);
                
                // Remove hearts after animation
                setTimeout(() => {
                    heart.remove();
                }, 5000);
            }
            
            // Function to show message
            function showMessage(text) {
                const message = document.createElement('div');
                message.innerHTML = text;
                message.style.position = 'fixed';
                message.style.top = '50%';
                message.style.left = '50%';
                message.style.transform = 'translate(-50%, -50%)';
                message.style.fontSize = 'clamp(1.5rem, 5vw, 2.2rem)';
                message.style.color = '#e91e63';
                message.style.backgroundColor = 'rgba(255, 255, 255, 0.95)';
                message.style.padding = '20px 30px';
                message.style.borderRadius = '15px';
                message.style.zIndex = '100';
                message.style.textAlign = 'center';
                message.style.boxShadow = '0 0 30px rgba(0, 0, 0, 0.3)';
                message.style.fontWeight = 'bold';
                message.style.border = '3px solid #e91e63';
                message.style.maxWidth = '90%';
                document.body.appendChild(message);
                
                // Remove message after 3 seconds
                setTimeout(() => {
                    message.style.transition = 'opacity 1s';
                    message.style.opacity = '0';
                    setTimeout(() => {
                        message.remove();
                    }, 1000);
                }, 3000);
            }
        });
    </script>
</body>
</html>
