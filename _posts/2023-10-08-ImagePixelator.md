---
toc: false
comments: true
layout: post
title: Image Pixelator
description: Pixelate Images!
type: hacks
courses: { compsci: {week: 1} }
---
<head>
    <style>
        /* Define styles for left and right halves */
        .container {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        .left-half, .right-half, .bottom-half{
            height: 250px;
            padding: 5px;
            color: #444444;
            font-family: 'IBM Plex Sans Hebrew', monospace;
        }
        .left-half {
            height: 170px;
            width: 575px;
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        .right-half {
            width: 425px;
            text-align: center;
            border-left: 3px solid #bde4f4;
        }
        .bottom-half {
            border-top: 3px solid #bde4f4;
            text-align: center;
            align-items: center;
            width: 100%;
        }
        .p1 {
            font-family: 'IBM Plex Sans Hebrew', monospace;
            color: #3A3B3C;
            /* src: url('fonts/fontface.css');  */
        }
        .p2 {
            font-family: 'IBM Plex Sans Hebrew', monospace;
            color: #CCCCCC;
            /* src: url('fonts/fontface.css');  */
        }
        /*@font-face {
        font-family: 'Roblox';
        src: url('.././fonts/Roblox-Font.ttf');
        } */
        .container2 {
            background-color: #444444;
            display: flex;
            flex-direction: column;
            align-items: center;
            font-family: 'IBM Plex Sans Hebrew', monospace;
            color: #CCCCCC;
            border: 5.5px solid transparent;
            animation: rgbLightEffect 7.7s linear infinite;
            overflow: break-word;
        }
        .dropbtn {
            color: black;
            padding: 16px;
            font-size: 16px;
            cursor: pointer;
        }
        .dropdown {
            position: relative;
            display: inline-block;
        }
        .dropdown-content {
            display: none;
            position: absolute;
            min-width: 160px;
            overflow: auto;
            box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
            z-index: 1;
        }
        .dropdown-content option {
            color: black;
            padding: 12px 16px;
            text-decoration: none;
            display: block;
        }
        .button {
            border-radius: 10px;
        }
        .a {
            position: relative;
            padding: 13px 24px;
            display: flex;
            justify-content: center;
            align-items: center;
            background: rgba(0, 0, 0, 0.5);
            margin: 10px;
            transition: 1s;
            text-decoration: none;
            overflow: hidden;
            -webkit-box-reflect: below 1px linear-gradient(transparent, transparent, #0004);
        }
        .a:hover {
            background: var(--clr);
            box-shadow: 0 0 10px var(--clr), 0 0 30px var(--clr);
        }
        .a::before {
            content: '';
            position: absolute;
            width: 40px;
            height: 420%;
            background: var(--clr);
            transition: 1s;
            animation: animate 2s linear infinite;
            animation-delay: calc(0.33s * var(--i));
        }
        .a:hover::before {
            width: 1200%;
        }
        @keyframes animate {
            0% {
                transform: rotate(0deg);
            }
            100% {
                transform: rotate(360deg);
            }
        }
        .a::after {
            content: '';
            position: absolute;
            inset: 4px;
            background: #011e41;
        }
        .a:hover::after {
            background: var(--clr);
        }
        .a span {
            position: relative;
            z-index: 1;
            font-size: 2em;
            color: #ffcf01;
            font-family: 'IBM Plex Sans Hebrew', monospace;
            opacity: 0.7;
            text-transform: uppercase;
            letter-spacing: 4px;
            transition: 0.5s;
        }
        .a:hover span {
            opacity: 1;
        }
        *{
            box-sizing: border-box;
        }
        .label{
            background-color: #111;
            display: flex;
            align-items: center;
            justify-content: space-between;
            position: relative;
            border-radius: 50px;
            padding: 5px;
            height: 26px;
            width: 50px;
        }
        body{
            transition: background 0.14s linear;
        }
        body.dark{
            background-color: #191d2b;
        }
        .checkbox{
            opacity: 0;
            position: absolute;
        }
        .ball{
            background-color: #ffffff;
            border-radius: 50%;
            position: absolute;
            top: 2px;
            left: 2px;
            width: 22px;
            height: 22px;
            transition: transform 0.15s linear;
        }
        .checkbox:checked + .label .ball {
            transform: translateX(24px);
        }
        .fa-moon{
            color: #f1c40f;
        }
        .fa-sun{
            color: #f39c12;
        }
        .light-text{
            color: #3A3B3C;
        }
        .dark-text{ 
            color: #CCCCCC;
        }
        .bee {
            transform: rotate(0deg); /* Initial rotation */
            transition: transform 0.2s; /* Smooth rotation transition */
        }
    </style>
</head>
<body>
    <h8 class="p1 light-text"><strong>Light Switch down below</strong></h8>
    <div>
        <input type="checkbox"
            class="checkbox" id="checkbox" >
    <label for="checkbox" class="label">
        <i class="fas fa-moon"></i>
        <i class="fas fa-sun"></i>
        <div class="ball"></div>
    </label>
    </div>
    <div class="container">
        <div class="left-half">
            <h1 class="p1"><strong>Upload an Image</strong></h1>
            <input type="file" id="imageInput" accept="image/*">
        </div>
        <div style="--clr: 	#6da7d9;--i:0;">
                <button id="manipulateButton" class="a"><a href="#"><span><strong>Pixelate!</strong></span></a></button>
            </div>
    </div>
        <div class="left-half" style="border-top: 3px solid #bde4f4; width: 419px; border-right: 3px solid #bde4f4; height: 205px;">
            <label class="p1" style="font-size: 25px; display: inline; padding-right: 4px;">Pixelation Level: </label>
            <div class="dropdown">
                <select id="pixelationLevel" class="dropbtn" style="margin-top : 4px;">
                    <option value="2">2</option>
                    <option value="4">4</option>
                    <option value="8" selected>8</option>
                    <option value="16">16</option>
                    <option value="32">32</option>
                </select>
                <br><br>
                <input type="checkbox" id="addToDatabase" name="addToDatabase">
                <label for="addToDatabase">Add to Database</label>
                <br>
                <button id="spawnBeeButton">Harmless Button</button>
                <img src="../../../images/bee.jpg" alt="Bee" class="bee" id="bee" style="position: absolute; display: none;">
            </div>
        </div>
    <div class="container">
        <div class="bottom-half">
            <h1 class="p1"><strong>Pixelated Image</strong></h1>
            <img id="uploadedImage" src="" alt="Uploaded Image" style="max-width: 100%; display: none;">
            <br>
            <button id="downloadButton" class="button">Download Pixelated Image</button>
            <br>
        </div>
    </div>
        <div>
            <h1 class="p1"><Strong>How does this work?</Strong></h1>
        </div>
        <div>
            <h4 class="p1">The above pixelate function works by downscaling the image and averaging out the RGB values over a certain box, depending on the size you specify (unfortunately not implemented yet). Then, it rescales the image up to create a pixelated image!</h4>
        </div>


<script>
    const bee = document.getElementById('bee');
    const spawnBeeButton = document.getElementById('spawnBeeButton');

    // Function to generate a random position within the screen bounds
    function getRandomPosition() {
        const maxWidth = window.innerWidth - bee.clientWidth;
        const maxHeight = window.innerHeight - bee.clientHeight;
        const randomX = Math.floor(Math.random() * maxWidth);
        const randomY = Math.floor(Math.random() * maxHeight);
        return { x: randomX, y: randomY };
    }

    // Function to calculate the rotation angle based on the direction
    function calculateRotation(currentX, currentY, destinationX, destinationY) {
        const angle = Math.atan2(destinationY - currentY, destinationX - currentX);
        return angle * (180 / Math.PI);
    }

    // Function to spawn and animate the bee
    function spawnBee() {
        alert('Oh no! You found a bug in our code! Help us get catch it!');
        bee.style.display = 'block'; // Show the bee

        // Get a random initial position for the bee
        const startPosition = getRandomPosition();
        bee.style.left = startPosition.x + 'px';
        bee.style.top = startPosition.y + 'px';

        // Animate the bee
        let destination = getRandomPosition();
        const speed = 5;

        const animationInterval = setInterval(() => {
            const currentX = parseFloat(bee.style.left);
            const currentY = parseFloat(bee.style.top);

            // Calculate the rotation angle
            const rotationAngle = calculateRotation(currentX, currentY, destination.x, destination.y);
            bee.style.transform = `rotate(${rotationAngle}deg)`; // Apply rotation

            // Calculate the direction vector
            const deltaX = destination.x - currentX;
            const deltaY = destination.y - currentY;
            const distance = Math.sqrt(deltaX * deltaX + deltaY * deltaY);

            if (distance <= speed) {
                // If the bee is close to the destination, snap to it
                bee.style.left = destination.x + 'px';
                bee.style.top = destination.y + 'px';
                destination = getRandomPosition(); // Get a new random destination
            } else {
                // Move the bee at a constant speed
                const directionX = deltaX / distance;
                const directionY = deltaY / distance;
                bee.style.left = (currentX + directionX * speed) + 'px';
                bee.style.top = (currentY + directionY * speed) + 'px';
            }
        }, 20); // Adjust the animation speed
    }

    // Add a click event listener to the button
    spawnBeeButton.addEventListener('click', spawnBee);

    // Add a click event listener to the bee (outside the function)
    document.addEventListener('click', function (event) {
        if (event.target.id === 'bee') {
            bee.style.display = 'none';
            alert('Great job! Thanks for helping us catch the bug!');
        }
    });

    const checkbox = document.getElementById('checkbox');
    const textElements = document.querySelectorAll('.p1, .p2');
    checkbox.addEventListener('change', () => {
    document.body.classList.toggle('dark');
    //change the overall theme color.
    textElements.forEach((element) => {
    element.classList.toggle('dark-text');
    element.classList.toggle('light-text');
    //change the overall text color.
    });
    });
    uploadedImageName = "";
    const resultContainer = document.getElementById("result");
    const url = "http://localhost:8017/api/pixel-partner-api";
    //const url = "https://fte.stu.nighthawkcodingsociety.com/api/pixel-partner-api";
    const test_url = url + "/test";
    const pixelate_url = url + "/pixelate/";
    const options = {
        method: 'GET', // *GET, POST, PUT, DELETE, etc.
        mode: 'cors', // no-cors, *cors, same-origin
        cache: 'default', // *default, no-cache, reload, force-cache, only-if-cached
        credentials: 'omit', // include, *same-origin, omit
        headers: {
            'Content-Type': 'application/json',
            // 'Content-Type': 'application/x-www-form-urlencoded',
        },
    };
    const post_options = {
        method: 'POST', // *GET, POST, PUT, DELETE, etc.
        mode: 'cors', // no-cors, *cors, same-origin
        cache: 'default', // *default, no-cache, reload, force-cache, only-if-cached
        credentials: 'omit', // include, *same-origin, omit
        headers: {
            'Content-Type': 'application/json',
            // 'Content-Type': 'application/x-www-form-urlencoded',
        },
    };
    // fetch the API
    fetch(test_url, options)
    // response is a RESTful "promise" on any successful fetch
    .then(response => {
        // check for response errors
        if (response.status !== 200) {
            error('GET API response failure: ' + response.status);
            return;
        }
        // valid response will have JSON data
        response.json().then(data => {
            console.log(data);
        })
    })
    // catch fetch errors (ie Nginx ACCESS to server blocked)
    .catch(err => {
    error(err + " " + test_url);
    });    
    function handleImageUpload() {
        const imageInput = document.getElementById('imageInput');
        const uploadedImage = document.getElementById('uploadedImage');
        const pixelationLevel = document.getElementById('pixelationLevel').value;
        const addToDatabaseCheckbox = document.getElementById('addToDatabase'); // Add this line
        const leftHalf = document.getElementById('left-half'); //new code

        const file = imageInput.files[0];
        if (file) {
            const reader = new FileReader();
            reader.readAsDataURL(file);

            reader.onload = function (e) {
                const base64Data = e.target.result.split(',')[1];
                const fileName = file.name;
                uploadedImageName = file.name;
                const fileExtension = fileName.split('.').pop();
                const addToDatabase = addToDatabaseCheckbox.checked;
                // Create the data object to send to the backend
                const data = {
                    "pixelate_level": pixelationLevel,
                    "addToHistory": addToDatabase,
                    "filename": fileName,
                    "base64image": base64Data,
                };
                console.log(data)
                // fetch the API
                const image_options = {...post_options, method: 'POST', body: JSON.stringify(data)};
                fetch(pixelate_url, image_options)
                .then(response => {
                    // check for response errors
                    if (response.status !== 200) {
                        error('GET API response failure: ' + response.status);
                        return;
                    }

                    // valid response will have JSON data
                    response.json().then(data => {
                        console.log(data)
                            const pixelatedImage = new Image();
                            pixelatedImage.src = 'data:image/' + fileExtension + ';base64,' + data['base64image'];

                            // Set a max-height for the image to fit within the text box
                            pixelatedImage.style.maxHeight = '100%';

                            uploadedImage.src = pixelatedImage.src;
                            uploadedImage.style.display = 'block';

                            pixelatedImage.onload = function() {
                                const parent = document.querySelector('.bottom-half');
                                const ratio = parent.clientWidth / pixelatedImage.width;

                                if (ratio < 1) {
                                    const maxHeight = ratio * pixelatedImage.height
                                    parent.style.height = (maxHeight + 175) + 'px';
                                } else {
                                    parent.style.height = (pixelatedImage.height + 175) + 'px';
                                }
                        }
                    })
                })
            };
        }
    };
    function handleDownloadClick() {
        const uploadedImage = document.getElementById('uploadedImage');
        const pixelatedImage = new Image();
        pixelatedImage.src = uploadedImage.src;

        // checking if no images is uploaded
        if (uploadedImage.width == 0) {
            //sends alert
            alert('Please upload an image before trying to download');
            return;
        }
        // Create an anchor element for downloading
        const downloadLink = document.createElement('a');
        downloadLink.href = pixelatedImage.src;
        downloadLink.download = uploadedImageName.split('.')[0] + "_pixelated." + uploadedImageName.split('.')[1];
        downloadLink.style.display = 'none';

        // Append the anchor element to the document and trigger a click event
        document.body.appendChild(downloadLink);
        downloadLink.click();

        // Remove the anchor element
        document.body.removeChild(downloadLink);

    }
    const downloadButton = document.getElementById('downloadButton');
    downloadButton.addEventListener('click', handleDownloadClick);
    const manipulateButton = document.getElementById('manipulateButton');
    manipulateButton.addEventListener('click', handleImageUpload);
</script>

</body>
<br><br>