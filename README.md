# simle-javascript

<body id="page">
    <div id="header">
        <h1>Guess the Number</h1>
    </div>
    <div id="content">
        <div>
            <h1 id="answer">?</h1>
        </div>
        <div>
            <button id="startButton" onclick='
                var randomDecimalNumber = Math.random() * 100;
                var randomWholeNumber = Math.floor(randomDecimalNumber) + 1; // Ensure it’s between 1 and 100
                var correctAnswer = randomWholeNumber;
                console.log("Correct Answer: " + correctAnswer); // Part 1: Log the correct answer
                var playerGuess;

                // Part 3: Game loop
                while (true) {
                    playerGuess = prompt("Enter your guess (between 1 and 100):");
                    console.log("Player Guess: " + playerGuess);
                    playerGuess = parseInt(playerGuess); // Convert the guess into a number
                    
                    if (playerGuess === correctAnswer) {
                        alert("You got it!");
                        document.getElementById("answer").innerText = correctAnswer; // Part 4: Update the page with the winning answer
                        document.getElementById("startButton").innerText = "Play again"; // Part 4: Change button text

                        // Stretch: Celebration
                        var bodyHTML = document.body;
                        var bodyStyle = bodyHTML.style;
                        bodyStyle.animation = "celebration 1s";
                        break; // Exit the loop as the player guessed correctly
                    } else if (playerGuess > correctAnswer) {
                        alert("Too high");
                    } else if (playerGuess < correctAnswer) {
                        alert("Too low");
                    }
                }
            '>Start</button>
        </div>
    </div>