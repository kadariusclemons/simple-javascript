#simple-javascript
### Folder Structure:
```
/FLO-FanPage
|-- index.html
|-- about.html
|-- contact.html
|-- css
|   |-- styles.css
|-- js
|   |-- script.js
|-- images
|   |-- banner.jpg
|   |-- team.jpg
```

### HTML Files

**1. index.html (Landing Page)**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="css/styles.css">
    <title>FLO Fan Page</title>
</head>
<body>
    <header>
        <h1>FLO Fan Page</h1>
        <nav>
            <ul>
                <li><a href="index.html">Home</a></li>
                <li><a href="about.html">About</a></li>
                <li><a href="contact.html">Contact</a></li>
            </ul>
        </nav>
    </header>

    <main>
        <img src="images/banner.jpg" alt="FLO Banner" class="banner">
        <h2>Discover FLO: Fresh, Unique, Fun</h2>
        <p>Welcome to the official fan page for FLO, an incredible British girl group. Dive into their music, explore their journey, and connect with fellow fans!</p>
        <div id="greeting"></div>
    </main>

    <footer>
        <p>&copy; 2023 FLO Fan Page | Designed by Kadarius Clemons</p>
    </footer>

    <script src="js/script.js"></script>
</body>
</html>
```

**2. about.html (About Page)**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="css/styles.css">
    <title>About FLO</title>
</head>
<body>
    <header>
        <h1>FLO Fan Page</h1>
        <nav>
            <ul>
                <li><a href="index.html">Home</a></li>
                <li><a href="about.html">About</a></li>
                <li><a href="contact.html">Contact</a></li>
            </ul>
        </nav>
    </header>

    <main>
        <h2>About FLO</h2>
        <p>FLO is a dynamic girl group hailing from the UK, known for their stunning vocal harmonies and infectious energy. Their unique blend of pop and R&B has captured the hearts of fans worldwide.</p>
        <p>With their debut single topping charts, FLO is redefining the modern girl group experience. Join us on their journey as they continue to create magic in the music industry!</p>
        <img src="images/team.jpg" alt="FLO Team" class="team-image">
    </main>

    <footer>
        <p>&copy; 2023 FLO Fan Page | Designed by Kadarius Clemons</p>
    </footer>

    <script src="js/script.js"></script>
</body>
</html>
```

**3. contact.html (Contact Page)**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="css/styles.css">
    <title>Contact FLO</title>
</head>
<body>
    <header>
        <h1>FLO Fan Page</h1>
        <nav>
            <ul>
                <li><a href="index.html">Home</a></li>
                <li><a href="about.html">About</a></li>
                <li><a href="contact.html">Contact</a></li>
            </ul>
        </nav>
    </header>

    <main>
        <h2>Contact Us</h2>
        <form id="contactForm">
            <label for="email">Your Email:</label>
            <input type="email" id="email" required>

            <label for="message">Message:</label>
            <textarea id="message" required></textarea>

            <label for="item">Select an item:</label>
            <select id="item">
                <option value="">Select...</option>
                <option value="sticker">Sticker</option>
                <option value="poster">Poster</option>
            </select>

            <button type="submit">Send Message</button>
            <div id="formMessage" class="error"></div>
        </form>
        <div id="successMessage" style="display:none;"></div>
    </main>

    <footer>
        <p>&copy; 2023 FLO Fan Page | Designed by Kadarius Clemons</p>
    </footer>

    <script src="js/script.js"></script>
</body>
</html>
```

### CSS File (css/styles.css)

```css
body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
}

header {
    background-color: #f4f4f4;
    padding: 10px;
    text-align: center;
}

nav ul {
    list-style: none;
    padding: 0;
}

nav ul li {
    display: inline;
    margin: 0 15px;
}

.banner {
    width: 100%;
    height: auto;
}

.team-image {
    max-width: 100%;
    height: auto;
}

main {
    padding: 20px;
}

#error {
    color: red;
}

footer {
    background-color: #f4f4f4;
    text-align: center;
    padding: 10px;
    position: relative;
    bottom: 0;
    width: 100%;
}
```

### JavaScript File (js/script.js)

```javascript
// greeting prompt for landing page
window.onload = function() {
    let name = prompt("Please enter your name:");
    if (name) {
        document.getElementById("greeting").innerText = 'Welcome, ' + name + '!';
    }
};

// Contact Form Submission
document.getElementById("contactForm").onsubmit = function(event) {
    event.preventDefault(); // Prevent form submission

    let email = document.getElementById("email").value;
    let message = document.getElementById("message").value;
    let item = document.getElementById("item").value;

    if (!email || !message) {
        document.getElementById("formMessage").innerText = "Please fill all required fields.";
        return;
    } else {
        document.getElementById("formMessage").innerText = "";
    }

    // Simulate sending an email
    var randomNum = Math.floor(Math.random() * 10000);
    let subject = `Message to FLO Fan Page #${randomNum}`;
    let mailtoLink = `mailto:imaginarybusiness@example.com?cc=your-email@example.com&subject=${encodeURIComponent(subject)}&body=${encodeURIComponent('From: ' + email + '\nMessage: ' + message + '\nItem: ' + item)}`;

    // show success message
    document.getElementById("contactForm").style.display = 'none';
    document.getElementById("successMessage").style.display = 'block';
    document.getElementById("successMessage").innerHTML = `Thank you for your message! You will be redirected to the homepage shortly.`;
    
    setTimeout(() => {
        window.location.href = "index.html";  // Redirect after 5 seconds
    }, 5000);
    
    window.location.href = mailtoLink; // Open the email client
};
```

### Instructions for usage:
1. Create the files and folders as per the structure mentioned.
2. Copy the HTML code into the respective HTML files, the CSS into the `styles.css`, and the JavaScript code into `script.js`.
3. Add your images to the `images` folder and ensure their names match those specified in the code.
4. Open the `index.html` file in a web browser to see your fan page in action.