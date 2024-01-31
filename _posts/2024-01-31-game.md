<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        body {
            margin: 0;
            overflow: hidden;
            background-color: #87CEEB; /* Sky Blue */
        }

        #hamster {
            position: absolute;
            bottom: 10px;
            left: 50%;
            transform: translateX(-50%);
            transition: transform 0.2s ease-out;
            font-size: 40px; /* Adjust the font size to make the hamster bigger */
        }

        #score {
            position: absolute;
            bottom: 10px;
            right: 10px;
            font-size: 24px;
            color: white;
        }

        .falling-item {
            position: absolute;
            width: 30px;
            height: 30px;
            background-color: #FFA500; /* Orange */
            border-radius: 50%;
            animation: fall 2s linear infinite;
        }

        .carrot {
            font-size: 30px; /* Adjust the font size to make the carrot bigger */
        }

        @keyframes fall {
            to {
                transform: translateY(100vh);
            }
        }
    </style>
</head>
<body>
    <div id="hamster">
        🐹
    </div>

    <div id="score">Score: 0</div>

    <script>
        const hamster = document.getElementById('hamster');
        const scoreElement = document.getElementById('score');
        let hamsterPosition = 50;
        let score = 0;

        window.addEventListener('keydown', (event) => {
            if (event.key === 'ArrowLeft') {
                moveHamster('left');
            } else if (event.key === 'ArrowRight') {
                moveHamster('right');
            }
        });

        function moveHamster(direction) {
            const step = 20; // Increase the step for faster movement
            if (direction === 'left') {
                hamsterPosition = Math.max(hamsterPosition - step, 0);
            } else if (direction === 'right') {
                hamsterPosition = Math.min(hamsterPosition + step, 100);
            }

            hamster.style.transform = `translateX(${hamsterPosition}%)`;
        }

        function createFallingItem() {
            const fallingItem = document.createElement('div');
            fallingItem.classList.add('falling-item', 'carrot');
            fallingItem.style.left = `${Math.random() * 90 + 5}vw`;

            document.body.appendChild(fallingItem);

            fallingItem.addEventListener('animationend', () => {
                fallingItem.remove();
            });

            checkCollision(fallingItem);
        }

        function checkCollision(fallingItem) {
            const hamsterRect = hamster.getBoundingClientRect();
            const itemRect = fallingItem.getBoundingClientRect();

            if (
                itemRect.bottom >= hamsterRect.top &&
                itemRect.top <= hamsterRect.bottom &&
                itemRect.right >= hamsterRect.left &&
                itemRect.left <= hamsterRect.right
            ) {
                fallingItem.remove();
                score++;
                scoreElement.textContent = `Score: ${score}`;
            }
        }

        setInterval(createFallingItem, 3000); // Create falling items every 3 seconds
        setInterval(() => {
            document.querySelectorAll('.falling-item').forEach((item) => {
                checkCollision(item);
            });
        }, 100); // Check collisions every 100 milliseconds
    </script>
</body>
</html>
