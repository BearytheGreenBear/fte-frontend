---
toc: false
comments: true
layout: post
title: Image Manipulation
description: Upload an image
type: hacks
courses: { compsci: {week: 1} }
---

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        /* Define styles for left and right halves */
        .container {
            display: flex;
            justify-content: space-between;
            align-items: center;
            height: 80vh;
        }
        @keyframes rgbLightEffect {
            0% {
               border-color: red;
            }
            10% {
                border-color: yellow;
            }
            20% {
                border-color: lime;
            }
            30% {
                border-color: aqua;
            }
            40% {
                border-color: blue;
            }
            50% {
                border-color: fuchsia;
            }
            60% {
                border-color: blue;
            }
            70% {
                border-color: aqua;
            }
            80% {
                border-color: lime;
            }
            90% {
                border-color: yellow;
            }
            100% {
                border-color: red;
            }
        }
        .left-half, .right-half, .bottom-half{
            width: 500px;
            height: 300px;
            padding: 10px;
            box-sizing: border-box;
            color: black;
            border: 5.5px solid transparent;
            animation: rgbLightEffect 7.7s linear infinite;
        }
        .left-half {
            background-color: #333333;
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        .right-half {
            background-color: #444444;
            text-align: center;
        }
        .bottom-half {
            background-color: #555555;
            text-align: center;
            align-items: center;
            width: 100%;
        }
        .p1 {
            font-family: 'Verdana', sans-serif;
            color: #CCCCCC;
            /* src: url('fonts/fontface.css'); */
        }
        /* @font-face {
        font-family: 'Roblox';
        src: url('Roblox-Font-Bold.ttf');
        } */
        .container2 {
            background-color: #444444;
            display: flex;
            flex-direction: column;
            align-items: center;
            font-family: 'Verdana', sans-serif;
            color: #CCCCCC;
            border: 5.5px solid transparent;
            animation: rgbLightEffect 7.7s linear infinite;
            overflow: break-word;
        }
        .container3 {
            background-color: #444444;
            display: flex;
            flex-direction: column;
            align-items: center;
            font-family: 'Verdana', sans-serif;
            color: #CCCCCC;
            border: 5.5px solid transparent;
            border-color: #234823;
        }
    </style>



</head>



<body>
    <div class="container">
        <div class="left-half">
            <h1 class="p1"><strong>Upload an Image</strong></h1>
            <input type="file" id="imageInput" accept="image/*">
        </div>
        <div class="right-half">
            <h1 class="p1"><strong>Image Manipulation</strong></h1>
            <button id="manipulateButton">-- -- M a n i p u l a t e !-- --</button>
        </div>
    </div>
    <div class="container">
        <div class="bottom-half">
            <h1 class="p1"><strong>Uploaded Image</strong></h1>
            <img id="uploadedImage" src="" alt="Uploaded Image" style="max-width: 100%; display: none;">
        </div>
    </div>
    <div class="container2">
        <div>
            <h1 class="p1"><Strong>How does this work?</Strong></h1>
        </div>
        <div>
            <h4 class="p1">The above pixelate function works by downscaling the image and averaging out the RGB values over a certain box, depending on the size you specify (unfortunately not implemented yet). Then, it rescales the image up to create a pixelated image!</h4>
        </div>
    </div>
    <div class="container3">
        <div>
            <h1 class="p1"><Strong>JPG file type needed!</Strong></h1>
        </div>
    </div>

<script>
    const resultContainer = document.getElementById("result");
    const url = "http://127.0.0.1:8017/api/pixel-partner-api";
    const test_url = url + "/test";
    const pixelate_url = url + "/pixelate/";
    const options = {
        method: 'GET', // *GET, POST, PUT, DELETE, etc.
        mode: 'cors', // no-cors, *cors, same-origin
        cache: 'default', // *default, no-cache, reload, force-cache, only-if-cached
        credentials: 'omit', // include, *same-origin, omit
        headers: {
            'Content-Type': 'application/json'
            // 'Content-Type': 'application/x-www-form-urlencoded',
        },
    };
    const post_options = {
        method: 'POST', // *GET, POST, PUT, DELETE, etc.
        mode: 'cors', // no-cors, *cors, same-origin
        cache: 'default', // *default, no-cache, reload, force-cache, only-if-cached
        credentials: 'omit', // include, *same-origin, omit
        headers: {
            'Content-Type': 'application/json'
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
        const leftHalf = document.getElementById('left-half'); //new code

        const file = imageInput.files[0];
        if (file) {
            const reader = new FileReader();
            reader.readAsDataURL(file);

            reader.onload = function (e) {
                const base64Data = e.target.result.split(',')[1];
                // fetch the API
                // add option to change pixelate level
                data = {"pixelate_level": "8", "base64image": base64Data}
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
                        pixelatedImage.src = 'data:image/jpg;base64,' + data['base64image'];
                        uploadedImage.src = pixelatedImage.src;
                        uploadedImage.style.display = 'block';
                        pixelatedImage.onload = function() {
                            const parent = document.querySelector('.bottom-half'); // Get the parent element with class 'left-half'  
                            ratio = parent.clientWidth / pixelatedImage.width
                            height = ratio * pixelatedImage.height + 150         
                            parent.style.height = height + 'px';
                        }
                    })
                })
            };
        }
    };

    const manipulateButton = document.getElementById('manipulateButton');
    manipulateButton.addEventListener('click', handleImageUpload);
</script>

</body>
<br><br>