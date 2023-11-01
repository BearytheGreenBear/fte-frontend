---
toc: false
comments: true
layout: post
title: Image Grayscale
description: Grayscale your images!
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
            height: 200px;
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
            <br>
            <input type="checkbox" id="addToDatabase" name="addToDatabase">
            <label for="addToDatabase">Add to Database</label>
        </div>
        <div style="--clr: 	#6da7d9;--i:0;">
                <button id="manipulateButton" class="a"><a href="#"><span><strong>Grayscale!</strong></span></a></button>
            </div>
    </div>
    <div class="container">
        <div class="bottom-half">
            <h1 class="p1"><strong>Grayscaled Images</strong></h1>
            <img id="uploadedImage" src="" alt="Uploaded Image" style="max-width: 100%; display: none;">
            <br>
            <button id="downloadButton" class="button">Download Grayscaled Image</button>
            <br>
        </div>
    </div>
        <div>
            <h1 class="p2"><Strong>How does this work?</Strong></h1>
        </div>
        <div>
            <h4 class="p2">This works by averaging out the RGB values in each pixel in the image, then changes all the RGB values in that pixel to the average, turing the pixel gray. It then recombines all the pixels to form a grayscale image!</h4>
        </div>


<script>
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
    // const url = "http://localhost:8017/api/pixel-partner-api";
    const url = "https://fte.stu.nighthawkcodingsociety.com/api/pixel-partner-api";
    const test_url = url + "/test";
    const pixelate_url = url + "/pixelate/";
    const grayscale_url = url + "/grayscale";
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
                    "addToHistory": addToDatabase,
                    "filename": fileName,
                    "base64image": base64Data,
                };
                console.log(data)
                // fetch the API
                const image_options = {...post_options, method: 'POST', body: JSON.stringify(data)};
                fetch(grayscale_url, image_options)
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
        downloadLink.download = uploadedImageName.split('.')[0] + "_grayscaled." + uploadedImageName.split('.')[1];
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