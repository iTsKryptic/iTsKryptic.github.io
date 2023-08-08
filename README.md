<!DOCTYPE html>
<html>
<head>
    <title>Scavenger Hunt</title>
</head>
<body>
    <div id="container">
        <h1>Scavenger Hunt</h1>
        <div id="hint-container">
            <p id="hint">Welcome to the scavenger hunt! Your adventure starts here.</p>
            <input type="text" id="answer" placeholder="Enter your answer">
            <button id="submit">Submit</button>
        </div>
    </div>

    <script>
        const hints = [
            { text: "Great job! Your next hint is: Roses are red, violets are blue, I'm a fruit, and you'll find me in a bowl.", answer: "apple" },
            { text: "You're on fire! Here's your next hint: I have keys but open no locks. I have space but no room. You can enter but not go outside. What am I?", answer: "keyboard" },
            // Add more hints and answers as needed
        ];

        let currentHintIndex = 0;
        const hintElement = document.getElementById("hint");
        const answerInput = document.getElementById("answer");
        const submitButton = document.getElementById("submit");

        function displayHint(index) {
            hintElement.textContent = hints[index].text;
            answerInput.value = "";
        }

        function checkAnswer(answer) {
            return answer.toLowerCase() === hints[currentHintIndex].answer;
        }

        function goToNextHint() {
            currentHintIndex++;
            if (currentHintIndex < hints.length) {
                displayHint(currentHintIndex);
            } else {
                hintElement.textContent = "Congratulations, you've completed the scavenger hunt!";
                answerInput.style.display = "none";
                submitButton.style.display = "none";
            }
        }

        submitButton.addEventListener("click", function () {
            const userAnswer = answerInput.value;
            if (checkAnswer(userAnswer)) {
                goToNextHint();
            } else {
                alert("Incorrect answer. Try again.");
            }
        });

        // Initialize the scavenger hunt
        displayHint(currentHintIndex);
    </script>
</body>
</html>
