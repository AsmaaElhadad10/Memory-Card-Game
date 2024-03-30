<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Memory Game</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f0f0f0;
        }
        .memory-card {
            width: 100px;
            height: 100px;
            background-color: #fff;
            border: 2px solid #ccc;
            margin: 10px;
            display: inline-block;
            cursor: pointer;
        }
        .memory-card img {
            max-width: 100%;
            max-height: 100%;
            display: none;
        }
        .memory-card.flipped img {
            display: block;
        }
    </style>
</head>
<body>
    <div class="memory-card">
        <img src="image1.jpg" alt="Card 1">
    </div>
    <div class="memory-card">
        <img src="image2.jpg" alt="Card 2">
    </div>
    <!-- Add more cards here -->

    <script>
        const cards = document.querySelectorAll('.memory-card');
        let flippedCards = [];

        cards.forEach(card => {
            card.addEventListener('click', () => {
                card.classList.add('flipped');
                flippedCards.push(card);

                if (flippedCards.length === 2) {
                    // Check if cards match
                    if (flippedCards[0].innerHTML === flippedCards[1].innerHTML) {
                        // Cards match, keep them flipped
                        flippedCards = [];
                    } else {
                        // Cards don't match, flip them back after a second
                        setTimeout(() => {
                            flippedCards.forEach(card => card.classList.remove('flipped'));
                            flippedCards = [];
                        }, 1000);
                    }
                }
            });
        });
    </script>
</body>
</html>
