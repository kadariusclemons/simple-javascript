#simple-javascript

HTML: `index.html`
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="styles.css">
    <title>Image Gallery</title>
</head>
<body>
    <div class="gallery">
        <img id="main-image" src="image1.jpg" alt="Main image" />
        <div class="thumbnails">
            <img class="thumbnail" src="thumb1.jpg" alt="Thumbnail 1" data-large="image1.jpg">
            <img class="thumbnail" src="thumb2.jpg" alt="Thumbnail 2" data-large="image2.jpg">
            <img class="thumbnail" src="thumb3.jpg" alt="Thumbnail 3" data-large="image3.jpg">
        </div>
        <div id="score">Score: 0</div>
    </div>
    <script src="script.js"></script>
</body>
</html>
```

### JavaScript: `script.js`
```javascript
let score = 0;

const mainImage = document.getElementById('main-image');
const thumbnails = document.querySelectorAll('.thumbnail');
const scoreDisplay = document.getElementById('score');

thumbnails.forEach(thumbnail => {
    thumbnail.addEventListener('click', function() {
        const largeImageSrc = this.getAttribute('data-large');
        mainImage.src = largeImageSrc;
        
        // Change score and style based on score
        score++;
        scoreDisplay.textContent = `Score: ${score}`;
        document.body.style.backgroundColor = score % 2 === 0 ? 'lightblue' : 'lightgreen';
    });
});
```

### CSS: `styles.css`
```css
body {
    font-family: Arial, sans-serif;
}

.gallery {
    text-align: center;
}

#main-image {
    width: 600px;
    height: auto;
    border: 2px solid #ccc;
    margin-bottom: 20px;
}

.thumbnails {
    display: flex;
    justify-content: center;
}

.thumbnail {
    width: 100px;
    height: auto;
    margin: 0 10px;
    cursor: pointer;
    border: 2px solid #ccc;
    transition: transform 0.2s;
}

.thumbnail:hover {
    transform: scale(1.1);
}

#score {
    font-size: 20px;
    margin-top: 20px;
}