---
toc: false
comments: true
layout: post
title: Image Manipulation Part 1
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
            height: 100vh;
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
        .left-half, .right-half {
            width: 400px;
            height: 400px;
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
            <br><br><br>
            <input type="file" id="imageInput" accept="image/*">
            <img id="uploadedImage" src="" alt="Uploaded Image" style="max-width: 100%; display: none;">
        </div>
        <div class="right-half">
            <h1 class="p1"><strong>Image Manipulation</strong></h1>
            <br><br><br>
            <button id="manipulateButton">-- -- M a n i p u l a t e !-- --</button>
        </div>
    </div>
    <div class="container2">
        <div>
            <h1 class="p1"><Strong>Wondering How This is Functioning?</Strong></h1>
        </div>
        <div>
            <h4 class="p1">Say how this code works, how it is manipulating the image to pixelated...</h4>
        </div>
    </div>

<script>
    //getting the image inputted by user
    const image = document.getElementById("imageInput");
    //add event listener for when image is uploaded and declare function on the spot
    image.addEventListener("change", function(){
        //taking the first part of object FileList
        const file = image.files[0];
        //creates new instance of the FileReader object
        var reader = new FileReader;

        //listens for when the file is fully read
        reader.addEventListener("load", function() {
            console.log(reader.result);
        })

        //initiates the reading process and reads the file as a data URL
        reader.readAsDataURL(file);
});
</script>

</body>
<br><br><br>