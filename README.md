#simple-javascript
Here's a simple implementation of the random name picker as per the requirements of your challenge. Below are the HTML and JavaScript code snippets. You can create two files named `index.html` and `script.js`, and copy the respective code into them.

### index.html
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Random Name Picker</title>
</head>
<body>
    <h1>Random Name Picker</h1>
    <div id="nameList"></div>
    <div>
        <input type="number" id="guessInput" min="0" max="6" placeholder="Enter a number (0-6)" />
        <button id="submitGuess">Submit</button>
    </div>
    <script src="script.js"></script>
</body>
</html>
```

### script.js
```javascript
// Check if user data is already in localStorage
let userData = JSON.parse(localStorage.getItem('userData')) || {};

// Prompt for user's name
if (!userData.name) {
    const userName = prompt("Please enter your name:");
    userData.name = userName;
    userData.first = 0; // to track first correct guesses
    userData.wrongs = 0; // to track wrong guesses
    localStorage.setItem('userData', JSON.stringify(userData));
}

// Prompt for 7 names
const names = [];
for (let i = 0; i < 7; i++) {
    const name = prompt(`Enter name ${i + 1}:`);
    names.push(name);
}

// Generate a random number
const randomIndex = Math.floor(Math.random() * 7);
console.log(`Random Index: ${randomIndex}`); // Log for debugging

// Display names and input form
const nameListDiv = document.getElementById('nameList');
nameListDiv.innerHTML = names.map((name, index) => `<p>${index}: ${name}</p>`).join('');

document.getElementById('submitGuess').addEventListener('click', function(event) {
    event.preventDefault(); // Prevent page refresh
    
    const guessInput = document.getElementById('guessInput').value;
    
    if (guessInput === '') {
        alert('Please enter a number.');
        return;
    }
    
    const guessedNumber = parseInt(guessInput);

    // Check the user's guess
    if (guessedNumber === randomIndex) {
        alert(`Congratulations ${userData.name}! You guessed correctly.`);
        userData.first += 1; // Track first guesses
    } else {
        alert(`Sorry ${userData.name}, that's not correct. Try again!`);
        userData.wrongs += 1; // Track wrong guesses
    }
    
    localStorage.setItem('userData', JSON.stringify(userData)); // Update localStorage
    
    console.log(`User Data:`, userData); // Log for debugging
});
```

### Explanation of the Code

1. **HTML Structure**:
   - We have a header, a div to show the names, an input field for the user's guess, and a submit button.

2. **JavaScript Logic**:
   - The script checks local storage for existing user data.
   - It prompts the user for their name if not already stored and initializes tracking variables (`first` and `wrongs`).
   - It prompts the user for 7 names, which are stored in an array.
   - A random index for the names is generated.
   - Names are displayed on the page, and an event listener is attached to the submit button to handle guesses without refreshing the page.
   - The script checks if the guess matches the random index and updates the user's data in local storage accordingly.

### Usage
- Save the provided code into appropriate `.html` and `.js` files.
- Open `index.html` in a browser to run the random name picker functionality. The local storage will track user data across page refreshes.

This basic implementation covers all the requirements laid out in the task description. Feel free to enhance or modify the UI or functionality as you see fit!