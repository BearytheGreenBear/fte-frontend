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
            height: 60vh;
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
            padding: 20px;
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

<script>
    function handleImageUpload() {
        const imageInput = document.getElementById('imageInput');
        const uploadedImage = document.getElementById('uploadedImage');
        const leftHalf = document.getElementById('left-half'); //new code

        const file = imageInput.files[0];
        if (file) {
            const reader = new FileReader();
            reader.readAsDataURL(file);

            reader.onload = function (e) {
                uploadedImage.src = e.target.result;
                uploadedImage.style.display = 'block';
                    const base64Data = e.target.result.split(',')[1];
                    console.log(base64Data);

                    const img = new Image(); //new codes STARTS HERE
                    img.src = e.target.result;
                    img.onload = function() {
                        const parent = document.querySelector('.bottom-half'); // Get the parent element with class 'left-half'
                        parent.style.height = img.height + 'px';
                    }; //new codes added END HERE
                };
            }
        };

    const manipulateButton = document.getElementById('manipulateButton');
    manipulateButton.addEventListener('click', handleImageUpload);
</script>

</body>
<br><br><br>